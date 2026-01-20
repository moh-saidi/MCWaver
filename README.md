# AI-Powered Mod Generator

> Transform natural language descriptions into working Minecraft mods using constraint-validated LLM code generation

[![Minecraft](https://img.shields.io/badge/Minecraft-1.21.11-green.svg)](https://fabricmc.net/)
[![Fabric](https://img.shields.io/badge/Fabric-API-orange.svg)](https://fabricmc.net/)
[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Ollama](https://img.shields.io/badge/Ollama-Qwen%202.5-red.svg)](https://ollama.ai/)

An end-to-end AI code generation system that converts natural language into compiled Minecraft Fabric mods. Features constraint-based validation, structured output parsing, and automated compilation to ensure reliable LLM-generated code.

## Key Features

- **Fast Generation** - Complete mods in 3-5 seconds using local LLM (Qwen 2.5 0.5B)
- **Constraint Validation** - Multi-stage validation prevents AI hallucination
- **Zero Manual Work** - Fully automated from prompt to executable JAR
- **Game-Balanced** - Automatic value clamping for nutrition, saturation, and effects
- **Error Recovery** - Graceful fallbacks at every pipeline stage
- **Complete Output** - Generates source code, resources, recipes, and assets

## System Architecture

<div align="center">
  <img src="https://github.com/user-attachments/assets/3ea8bac1-b21c-4f52-8603-310ff12435ca" alt="System Architecture Diagram" width="700" />
</div>

### Pipeline Overview

The system implements a **5-layer pipeline** with comprehensive error recovery:

| Layer | Function | Error Handling |
|-------|----------|----------------|
| **Input** | Structured prompt generation with constraints | Format validation |
| **AI Processing** | Ollama + Qwen 2.5 (0.5B) inference | Timeout & retry |
| **Validation** | API whitelist, value clamping, ingredient filtering | Default fallbacks |
| **Code Generation** | Parallel Java/JSON/recipe output | Syntax validation |
| **Build** | Gradle compilation to JAR | Detailed error logs |

## Quick Start

### Prerequisites

- Google Colab account (free tier supported)
- Minecraft Fabric mod template for 1.21.11 (zip file)
- Item texture image (16x16 PNG recommended)

### Installation & Usage

**1. Open in Google Colab with GPU runtime** (T4 recommended)

**2. Install dependencies and setup Ollama**
```python
# Run setup cells in notebook
!pip install ollama
!curl -fsSL https://ollama.com/install.sh | sh
!ollama pull qwen2.5:0.5b
```

**3. Upload your mod template**
```python
from google.colab import files
uploaded = files.upload()
agent.setup_project(list(uploaded.keys()))
```

**4. Generate your mod**
```python
description = "A golden apple that gives Speed and Jump Boost for 30 seconds"
item_id = "super_apple"
item_name = "Super Apple"

# AI generates balanced game logic
logic = agent.get_balanced_logic(description)

# Creates complete mod structure
agent.create_food(item_id, item_name, logic)
```

**5. Compile and download**
```python
agent.finish()  # Produces working JAR file
```

## Example Output

```
Generating logic for: "A golden apple that gives Speed and Jump Boost for 30 seconds"

Extracted Logic:
{
  'nutrition': 6,
  'saturation': 0.8,
  'effects': [
    {'effect_id': 'MobEffects.SPEED', 'duration': 600, 'amplifier': 0},
    {'effect_id': 'MobEffects.JUMP_BOOST', 'duration': 600, 'amplifier': 0}
  ],
  'recipe_ingredients': ['minecraft:golden_apple', 'minecraft:sugar']
}

Validation passed: All effects recognized
Values clamped: nutrition=6, saturation=0.8
Recipe validated: 2 valid ingredients

Generated files:
   - ModItems.java
   - super_apple.json (model)
   - super_apple.json (recipe)
   - en_us.json (translations)

Building mod...
Build Successful!
Mod file: super_apple-1.0.0.jar (compiled in 18s)
```

## Technical Deep Dive

### Input Processing: Structured Prompting

The prompt builder injects explicit constraints into the LLM context:

- Whitelisted Minecraft effect IDs (30+ vanilla effects)
- Value bounds (nutrition: 1-12, saturation: 0.1-1.2)
- Valid crafting ingredients
- API endpoint specifications
- Output format requirements

### Validation Pipeline

**Stage 1: API Whitelist Check**
```python
VALID_EFFECTS = ['MobEffects.SPEED', 'MobEffects.REGENERATION', ...]
filtered_effects = [e for e in ai_effects if e['effect_id'] in VALID_EFFECTS]
```

**Stage 2: Value Clamping**
```python
nutrition = clamp(ai_nutrition, min=1, max=12)
saturation = clamp(ai_saturation, min=0.1, max=1.2)
duration = clamp(ai_duration, min=20, max=6000)
```

**Stage 3: Ingredient Filtering**
```python
valid_ingredients = [i for i in ai_ingredients if is_minecraft_item(i)]
unique_ingredients = list(set(valid_ingredients))[:9]  # Max 9 slots
```

### Code Generation: Parallel Artifact Creation

The system generates **4 synchronized outputs**:

```
mod_project/
├── src/main/java/[package]/
│   ├── ModItems.java           # AI-generated food logic
│   └── [MainClass].java        # Auto-injected initialization
└── src/main/resources/
    ├── assets/[mod_id]/
    │   ├── textures/item/       # Uploaded texture
    │   ├── models/item/         # Generated model JSON
    │   ├── items/               # Item definition JSON
    │   └── lang/en_us.json      # Translations
    └── data/[mod_id]/recipe/    # Crafting recipe JSON
```

### Error Recovery Strategy

```
AI Response → Parse → Validate → Generate Code → Compile
     ↓          ↓         ↓            ↓           ↓
  Timeout   Defaults  Fallbacks    Retry      Error Log
```

Every stage includes fallback mechanisms:
- **Parse failures** → Use default values
- **Invalid effects** → Filter and continue
- **Build errors** → Log detailed diagnostics
- **Timeouts** → Single retry with extended timeout

## Performance Metrics

| Metric | Value | Notes |
|--------|-------|-------|
| **AI Inference** | ~3 seconds | Qwen 2.5 (0.5B) on T4 GPU |
| **Total Generation** | 3-5 seconds | Per item (excluding build) |
| **First Build** | 1-2 minutes | Gradle dependency download |
| **Subsequent Builds** | 15-30 seconds | Cached dependencies |
| **Success Rate** | >95% | With validation enabled |
| **Model Size** | 0.5B parameters | Optimized for speed |
| **GPU Requirement** | T4 | Colab free tier sufficient |

## Technical Stack

**Core Technologies**
- Python 3.10+ (automation & orchestration)
- Ollama (local LLM inference)
- Qwen 2.5 (0.5B) (lightweight language model)

**Minecraft Modding**
- Minecraft 1.21.11
- Fabric API & Loader
- Java 21 (mod compilation)
- Gradle 8.x (build automation)

**Validation & Parsing**
- Regex-based structured output parsing
- Domain-specific constraint validation
- Multi-stage error recovery

## Supported Features

**Generated Items**
- Custom food items with configurable nutrition
- Multiple potion effects per item
- Customizable effect durations and amplifiers
- Crafting recipes with vanilla ingredients

**Validation Constraints**
- 30+ whitelisted vanilla potion effects
- Nutrition: 1-12 (half drumsticks to 6 drumsticks)
- Saturation: 0.1-1.2 (realistic hunger mechanics)
- Effect duration: 20-6000 ticks (1s to 5min)
- Recipe ingredients: Max 9 unique items

## Architecture Highlights

### Hallucination Prevention
- **Pre-validated API whitelist** prevents non-existent effect references
- **Item ID validation** ensures all ingredients exist in vanilla Minecraft
- **Recipe deduplication** removes redundant ingredients
- **Bounds enforcement** prevents impossible game values

### Reliability Engineering
- Graceful degradation with default fallbacks
- Connection timeout handling (30s with retry)
- Build failure detection with detailed diagnostics
- Structured logging at every pipeline stage

### Generalizability
While built for Minecraft, the architecture is transferable to any code generation domain:
- Constraint-based validation framework
- Structured output parsing pipeline
- Multi-stage error recovery
- Automated build integration

## Contributing

This project is part of a personal portfolio and is **not accepting contributions**. Feel free to fork for personal, non-commercial use.

## Resources

- [Fabric Mod Documentation](https://fabricmc.net/wiki/tutorial:introduction)
- [Ollama Documentation](https://ollama.ai/docs)
- [Minecraft Modding Wiki](https://minecraft.wiki/)
- [Qwen 2.5 Model Card](https://huggingface.co/Qwen/Qwen2.5-0.5B)

## License

Educational/portfolio project. See repository for license details.

---

**Built to demonstrate:** Production LLM constraint systems • Automated code generation • Structured output parsing • Build automation integration • Reliability engineering

**Domain:** Minecraft Fabric 1.21.11 | **Architecture:** Generalizable to any code generation target

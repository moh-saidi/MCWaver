# AI-Powered Minecraft Mod Generator

An AI code generation system that converts natural language descriptions into working Minecraft Fabric mods. Implements constraint-based validation, structured output parsing, and automated compilation to ensure reliable LLM code generation.

## System Architecture

![AI Code Generation System Architecture]<img width="800" height="1400" alt="mc (1)" src="https://github.com/user-attachments/assets/4eebc629-cdf7-48ef-ae4d-6dec28bf6632" />

The system implements a **5-layer pipeline** with comprehensive error recovery:

1. **Input Layer** - Converts natural language to structured prompts with constraint enforcement
2. **AI Processing Layer** - Ollama + Qwen 2.5 (0.5B) generates code in ~3 seconds
3. **Validation Layer** - 3-stage validation (API whitelist, value clamping, ingredient filtering)
4. **Code Generation Layer** - Parallel output of Java source, JSON resources, recipes, and assets
5. **Build Layer** - Gradle compilation produces executable JAR files

**Error Recovery**: Automatic fallbacks at every stage prevent failures from invalid AI outputs.

## Features

- **Local LLM Integration** - Uses Ollama with Qwen 2.5 (0.5B) for fast inference (<3 seconds)
- **Constraint Validation System** - Prevents hallucination with API whitelisting and regex validation
- **Automatic Value Clamping** - Enforces domain-specific bounds (nutrition 1-12, saturation 0.1-1.2)
- **Multi-Stage Error Recovery** - Fallback defaults when AI outputs invalid data
- **Complete Build Pipeline** - Generates source code, resources, and compiles to executable JAR files
- **Zero Manual Intervention** - End-to-end automation from prompt to working mod

## Quick Start

### Prerequisites
- Google Colab account (free tier works)
- Minecraft Fabric mod template for 1.21.11 (zip file)
- Item texture (16x16 PNG recommended)

### Usage

1. **Open the notebook** in Google Colab with GPU runtime (T4 recommended)

2. **Run the setup cells** to install Ollama and dependencies

3. **Upload your mod template**
```python
uploaded = files.upload()
agent.setup_project(list(uploaded.keys()))
```

4. **Generate your mod**
```python
description = "A golden apple that gives Speed and Jump Boost for 30 seconds"
item_id = "super_apple"
item_name = "Super Apple"

logic = agent.get_balanced_logic(description)
agent.create_food(item_id, item_name, logic)
```

5. **Compile the mod** (produces working JAR file)
```python
agent.finish()  # Downloads compiled mod
```

## Technical Stack

- **Python** - Core automation and code generation
- **Ollama** - Local LLM inference engine  
- **Qwen 2.5 (0.5B)** - Lightweight language model optimized for speed
- **Regex-based parsing** - Robust extraction from unstructured AI output
- **Minecraft Fabric API** - Modding framework (1.21.11)
- **Gradle** - Build automation and dependency management
- **Java 21** - Mod compilation environment

## Architecture Deep Dive

### Input Processing
**Structured Prompting** enforces explicit format rules and validation requirements. The prompt builder injects constraint rules, vanilla effects lists, value bounds, and API endpoints directly into the LLM context.

### AI Processing
**Multi-Pattern Parsing** uses regex to extract structured data from AI responses:
- `nutrition=X` - Food restoration value
- `effect_id=Y` - Potion effect identifiers  
- `ingredients=[Z]` - Crafting recipe components

### Validation Pipeline

#### Stage 1: API Whitelist Check
Validates all effect IDs against 30+ known Minecraft effects (e.g., `MobEffects.SPEED`, `MobEffects.REGENERATION`). Unknown effects are filtered out.

#### Stage 2: Value Clamping
Enforces game balance constraints:
- **Nutrition**: 1-12 (prevents overpowered food)
- **Saturation**: 0.1-1.2 (realistic hunger mechanics)
- **Duration**: Bounded to reasonable gameplay values

#### Stage 3: Ingredient Filtering
- Removes invalid item IDs
- Deduplicates recipe ingredients
- Ensures all items exist in vanilla Minecraft

### Code Generation
Parallel output produces **4 synchronized artifacts**:

1. **ModItems.java** - Food properties, effect instances, registration logic
2. **JSON Resources** - Item models, translations, asset definitions
3. **Recipe Files** - Crafting recipes with validated ingredients
4. **Asset Integration** - Texture placement and main class injection

### Build & Error Recovery
- **Success Path**: Gradle compiles to JAR → Downloads artifact
- **Failure Path**: Logs detailed errors → Reports to user
- **Timeout Handling**: 30-second limit with single retry
- **Parse Failures**: Graceful degradation to default values

## Reliability Features

### Hallucination Prevention
- Pre-validated API endpoint whitelist (30+ Minecraft effects)
- Item ID validation and deduplication
- Recipe ingredient filtering (removes invalid items)
- Effect duration bounds enforcement

### Error Recovery
- Default fallbacks for all parsed values
- Connection timeout handling (30s max)
- Build failure detection with detailed logging
- Graceful degradation when AI outputs invalid data

## Generated Output

The system creates complete mod structure:
```
mod_project/
├── src/main/java/[package]/
│   ├── ModItems.java (AI-generated food items)
│   └── [MainClass].java (auto-injected initialization)
└── src/main/resources/
    ├── assets/[mod_id]/
    │   ├── textures/item/[item_id].png
    │   ├── models/item/[item_id].json
    │   ├── items/[item_id].json
    │   └── lang/en_us.json
    └── data/[mod_id]/recipe/[item_id].json
```

## Example Output

```
📊 Extracted Logic:
{
  'nutrition': 6,
  'saturation': 0.8,
  'effects': [
    {'effect_id': 'MobEffects.SPEED', 'duration': 600},
    {'effect_id': 'MobEffects.JUMP_BOOST', 'duration': 600}
  ],
  'recipe_ingredients': ['minecraft:golden_apple', 'minecraft:sugar']
}

✅ Build Successful!
📦 Found Mod File: super_apple-1.0.0.jar
```

## Performance Metrics

| Metric | Value |
|--------|-------|
| **AI Response Time** | ~3 seconds |
| **Total Generation Time** | 3-5 seconds per item |
| **First Build Time** | 1-2 minutes (dependency download) |
| **Subsequent Builds** | 15-30 seconds |
| **Success Rate** | >95% with validation layer |
| **Model Size** | 0.5B parameters |
| **GPU Requirement** | T4 (Colab free tier) |

## Contributing

This project is currently **not accepting contributions** as it's part of a personal portfolio. Feel free to fork for your own non-commercial use.

## Technical Notes

- First Gradle build downloads dependencies (~1-2 minutes)
- Colab's free T4 GPU sufficient for 0.5B parameter model
- System operates fully offline after initial model download
- Average generation time: 3-5 seconds per item
- Compatible with Minecraft 1.21.11 Fabric mods
- Architecture is generalizable to other code generation targets

## About

Built as part of an AI & Data Science engineering curriculum, demonstrating:
- Production LLM constraint systems
- Automated code generation pipelines
- Structured output parsing from language models
- Build automation integration
- Error handling and reliability engineering

## Links

- [Fabric Mod Documentation](https://fabricmc.net/wiki/tutorial:introduction)
- [Ollama Documentation](https://ollama.ai/docs)
- [Minecraft Modding Wiki](https://minecraft.wiki/)

---

**Target Domain:** Minecraft Fabric 1.21.11 | **Architecture:** Transferable to any code generation application

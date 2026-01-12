# AI-Powered Minecraft Mod Generator

An AI code generation system that converts natural language descriptions into working Minecraft Fabric mods. Implements constraint-based validation, structured output parsing, and automated compilation to ensure reliable LLM code generation.

## System Architecture

![AI Code Generation System Architecture](<svg viewBox="0 0 800 1400" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="blueGrad" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#3b82f6;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#1e40af;stop-opacity:1" />
    </linearGradient>
    <linearGradient id="purpleGrad" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#a855f7;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#7e22ce;stop-opacity:1" />
    </linearGradient>
    <linearGradient id="greenGrad" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#10b981;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#047857;stop-opacity:1" />
    </linearGradient>
    <linearGradient id="cyanGrad" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#06b6d4;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#0e7490;stop-opacity:1" />
    </linearGradient>
    <linearGradient id="amberGrad" x1="0%" y1="0%" x2="0%" y2="100%">
      <stop offset="0%" style="stop-color:#f59e0b;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#d97706;stop-opacity:1" />
    </linearGradient>
  </defs>
  
  <!-- Background -->
  <rect width="800" height="1400" fill="#0f172a"/>
  
  <!-- Title -->
  <rect x="50" y="20" width="700" height="60" rx="8" fill="url(#purpleGrad)"/>
  <text x="400" y="52" font-family="Arial, sans-serif" font-size="24" font-weight="bold" fill="white" text-anchor="middle">AI CODE GENERATION SYSTEM</text>
  <text x="400" y="70" font-family="Arial, sans-serif" font-size="12" fill="#e0e7ff" text-anchor="middle">Architecture Flow</text>
  
  <!-- INPUT LAYER -->
  <rect x="50" y="100" width="700" height="30" rx="5" fill="url(#blueGrad)"/>
  <text x="400" y="120" font-family="Arial, sans-serif" font-size="16" font-weight="bold" fill="white" text-anchor="middle">INPUT LAYER</text>
  
  <rect x="200" y="145" width="400" height="50" rx="5" fill="#1e3a8a" stroke="#3b82f6" stroke-width="2"/>
  <text x="400" y="165" font-family="Arial, sans-serif" font-size="13" font-weight="bold" fill="#93c5fd" text-anchor="middle">User Natural Language</text>
  <text x="400" y="185" font-family="Arial, sans-serif" font-size="11" fill="#dbeafe" text-anchor="middle" font-style="italic">"healing food with fire resistance"</text>
  
  <path d="M 400 195 L 400 215" stroke="#64748b" stroke-width="3" marker-end="url(#arrowhead)"/>
  
  <rect x="150" y="220" width="500" height="80" rx="5" fill="#1e3a8a" stroke="#3b82f6" stroke-width="2"/>
  <text x="400" y="240" font-family="Arial, sans-serif" font-size="13" font-weight="bold" fill="#93c5fd" text-anchor="middle">Structured Prompt Builder</text>
  <text x="250" y="260" font-family="Arial, sans-serif" font-size="10" fill="#dbeafe" text-anchor="start">• Format enforcement</text>
  <text x="250" y="275" font-family="Arial, sans-serif" font-size="10" fill="#dbeafe" text-anchor="start">• Validation rules</text>
  <text x="250" y="290" font-family="Arial, sans-serif" font-size="10" fill="#dbeafe" text-anchor="start">• Output schema</text>
  <text x="480" y="260" font-family="Arial, sans-serif" font-size="10" fill="#dbeafe" text-anchor="start">• Constraint Rules</text>
  <text x="480" y="275" font-family="Arial, sans-serif" font-size="10" fill="#dbeafe" text-anchor="start">• Vanilla effects list</text>
  <text x="480" y="290" font-family="Arial, sans-serif" font-size="10" fill="#dbeafe" text-anchor="start">• Value bounds</text>
  
  <!-- AI PROCESSING LAYER -->
  <path d="M 400 300 L 400 325" stroke="#64748b" stroke-width="3" marker-end="url(#arrowhead)"/>
  
  <rect x="50" y="330" width="700" height="30" rx="5" fill="url(#purpleGrad)"/>
  <text x="400" y="350" font-family="Arial, sans-serif" font-size="16" font-weight="bold" fill="white" text-anchor="middle">AI PROCESSING LAYER</text>
  
  <rect x="200" y="375" width="400" height="60" rx="5" fill="#581c87" stroke="#a855f7" stroke-width="2"/>
  <text x="400" y="395" font-family="Arial, sans-serif" font-size="13" font-weight="bold" fill="#e9d5ff" text-anchor="middle">Ollama LLM ⚡</text>
  <text x="400" y="412" font-family="Arial, sans-serif" font-size="11" fill="#f3e8ff" text-anchor="middle">Qwen 2.5 (0.5B)</text>
  <text x="400" y="428" font-family="Arial, sans-serif" font-size="11" fill="#86efac" text-anchor="middle">~3 second response</text>
  
  <path d="M 400 435 L 400 455" stroke="#64748b" stroke-width="3" marker-end="url(#arrowhead)"/>
  
  <rect x="200" y="460" width="400" height="60" rx="5" fill="#581c87" stroke="#a855f7" stroke-width="2"/>
  <text x="400" y="480" font-family="Arial, sans-serif" font-size="13" font-weight="bold" fill="#e9d5ff" text-anchor="middle">Multi-Pattern Regex Parser</text>
  <text x="400" y="497" font-family="Courier, monospace" font-size="10" fill="#f3e8ff" text-anchor="middle">nutrition=X</text>
  <text x="400" y="510" font-family="Courier, monospace" font-size="10" fill="#f3e8ff" text-anchor="middle">effect_id=Y  •  ingredients=[Z]</text>
  
  <!-- VALIDATION LAYER -->
  <path d="M 400 520 L 400 545" stroke="#64748b" stroke-width="3" marker-end="url(#arrowhead)"/>
  
  <rect x="50" y="550" width="700" height="30" rx="5" fill="url(#greenGrad)"/>
  <text x="400" y="570" font-family="Arial, sans-serif" font-size="16" font-weight="bold" fill="white" text-anchor="middle">VALIDATION LAYER</text>
  
  <rect x="150" y="595" width="500" height="140" rx="5" fill="#064e3b" stroke="#10b981" stroke-width="2"/>
  <text x="400" y="615" font-family="Arial, sans-serif" font-size="13" font-weight="bold" fill="#6ee7b7" text-anchor="middle">Constraint Validator</text>
  
  <rect x="170" y="625" width="460" height="25" rx="3" fill="#1e293b"/>
  <circle cx="185" cy="637.5" r="8" fill="#10b981"/>
  <text x="195" y="640" font-family="Arial, sans-serif" font-size="10" font-weight="bold" fill="#6ee7b7" text-anchor="start">1. API Whitelist Check</text>
  <text x="350" y="640" font-family="Arial, sans-serif" font-size="9" fill="#d1fae5" text-anchor="start">30+ valid effects only</text>
  
  <rect x="170" y="655" width="460" height="35" rx="3" fill="#1e293b"/>
  <circle cx="185" cy="667" r="8" fill="#10b981"/>
  <text x="195" y="670" font-family="Arial, sans-serif" font-size="10" font-weight="bold" fill="#6ee7b7" text-anchor="start">2. Value Clamping</text>
  <text x="195" y="683" font-family="Courier, monospace" font-size="8" fill="#d1fae5" text-anchor="start">nutrition: 1-12  •  saturation: 0.1-1.2</text>
  
  <rect x="170" y="695" width="460" height="35" rx="3" fill="#1e293b"/>
  <circle cx="185" cy="707" r="8" fill="#10b981"/>
  <text x="195" y="710" font-family="Arial, sans-serif" font-size="10" font-weight="bold" fill="#6ee7b7" text-anchor="start">3. Ingredient Filtering</text>
  <text x="195" y="723" font-family="Arial, sans-serif" font-size="8" fill="#d1fae5" text-anchor="start">Remove invalid items • Deduplicate entries</text>
  
  <path d="M 400 735 L 300 760" stroke="#64748b" stroke-width="2" marker-end="url(#arrowhead)"/>
  <path d="M 400 735 L 500 760" stroke="#64748b" stroke-width="2" marker-end="url(#arrowhead)"/>
  
  <rect x="200" y="765" width="120" height="40" rx="5" fill="#064e3b" stroke="#10b981" stroke-width="2"/>
  <text x="260" y="785" font-family="Arial, sans-serif" font-size="12" font-weight="bold" fill="#6ee7b7" text-anchor="middle">✓ VALID</text>
  <text x="260" y="798" font-family="Arial, sans-serif" font-size="9" fill="#86efac" text-anchor="middle">Continue</text>
  
  <rect x="480" y="765" width="120" height="40" rx="5" fill="#7f1d1d" stroke="#ef4444" stroke-width="2"/>
  <text x="540" y="785" font-family="Arial, sans-serif" font-size="12" font-weight="bold" fill="#fca5a5" text-anchor="middle">✗ INVALID</text>
  <text x="540" y="798" font-family="Arial, sans-serif" font-size="9" fill="#fecaca" text-anchor="middle">Fallback</text>
  
  <path d="M 260 805 L 260 820 L 400 820" stroke="#64748b" stroke-width="2"/>
  <path d="M 540 805 L 540 820 L 400 820" stroke="#64748b" stroke-width="2"/>
  <path d="M 400 820 L 400 840" stroke="#64748b" stroke-width="3" marker-end="url(#arrowhead)"/>
  
  <!-- CODE GENERATION LAYER -->
  <rect x="50" y="845" width="700" height="30" rx="5" fill="url(#cyanGrad)"/>
  <text x="400" y="865" font-family="Arial, sans-serif" font-size="16" font-weight="bold" fill="white" text-anchor="middle">CODE GENERATION LAYER</text>
  
  <rect x="100" y="890" width="600" height="150" rx="5" fill="#164e63" stroke="#06b6d4" stroke-width="2"/>
  <text x="400" y="910" font-family="Arial, sans-serif" font-size="13" font-weight="bold" fill="#a5f3fc" text-anchor="middle">Code Generator - Parallel Output:</text>
  
  <rect x="120" y="920" width="140" height="105" rx="3" fill="#0e293b" stroke="#22d3ee" stroke-width="1"/>
  <text x="190" y="935" font-family="Arial, sans-serif" font-size="10" font-weight="bold" fill="#67e8f9" text-anchor="middle">ModItems.java</text>
  <text x="125" y="950" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• Food properties</text>
  <text x="125" y="963" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• Effect instances</text>
  <text x="125" y="976" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• Registration</text>
  
  <rect x="270" y="920" width="140" height="105" rx="3" fill="#0e293b" stroke="#22d3ee" stroke-width="1"/>
  <text x="340" y="935" font-family="Arial, sans-serif" font-size="10" font-weight="bold" fill="#67e8f9" text-anchor="middle">JSON Resources</text>
  <text x="275" y="950" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• models/item/*.json</text>
  <text x="275" y="963" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• items/*.json</text>
  <text x="275" y="976" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• lang/en_us.json</text>
  
  <rect x="420" y="920" width="140" height="50" rx="3" fill="#0e293b" stroke="#22d3ee" stroke-width="1"/>
  <text x="490" y="935" font-family="Arial, sans-serif" font-size="10" font-weight="bold" fill="#67e8f9" text-anchor="middle">Recipe Files</text>
  <text x="425" y="950" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• Crafting recipe</text>
  <text x="425" y="963" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• Ingredient list</text>
  
  <rect x="420" y="975" width="140" height="50" rx="3" fill="#0e293b" stroke="#22d3ee" stroke-width="1"/>
  <text x="490" y="990" font-family="Arial, sans-serif" font-size="10" font-weight="bold" fill="#67e8f9" text-anchor="middle">Asset Integration</text>
  <text x="425" y="1005" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• Texture placement</text>
  <text x="425" y="1018" font-family="Arial, sans-serif" font-size="8" fill="#cffafe" text-anchor="start">• Main class inject</text>
  
  <!-- BUILD LAYER -->
  <path d="M 400 1040 L 400 1065" stroke="#64748b" stroke-width="3" marker-end="url(#arrowhead)"/>
  
  <rect x="50" y="1070" width="700" height="30" rx="5" fill="url(#amberGrad)"/>
  <text x="400" y="1090" font-family="Arial, sans-serif" font-size="16" font-weight="bold" fill="white" text-anchor="middle">BUILD LAYER</text>
  
  <rect x="200" y="1115" width="400" height="60" rx="5" fill="#78350f" stroke="#f59e0b" stroke-width="2"/>
  <text x="400" y="1135" font-family="Arial, sans-serif" font-size="13" font-weight="bold" fill="#fde68a" text-anchor="middle">Gradle Build System</text>
  <text x="400" y="1152" font-family="Arial, sans-serif" font-size="10" fill="#fef3c7" text-anchor="middle">• Dependency resolve  • Java 21 compile</text>
  <text x="400" y="1167" font-family="Arial, sans-serif" font-size="10" fill="#fef3c7" text-anchor="middle">• JAR packaging</text>
  
  <path d="M 400 1175 L 300 1200" stroke="#64748b" stroke-width="2" marker-end="url(#arrowhead)"/>
  <path d="M 400 1175 L 500 1200" stroke="#64748b" stroke-width="2" marker-end="url(#arrowhead)"/>
  
  <rect x="180" y="1205" width="140" height="50" rx="5" fill="#064e3b" stroke="#10b981" stroke-width="3"/>
  <text x="250" y="1227" font-family="Arial, sans-serif" font-size="14" font-weight="bold" fill="#6ee7b7" text-anchor="middle">SUCCESS ✓</text>
  <text x="250" y="1244" font-family="Arial, sans-serif" font-size="10" fill="#86efac" text-anchor="middle">Download JAR</text>
  
  <rect x="480" y="1205" width="140" height="50" rx="5" fill="#7f1d1d" stroke="#ef4444" stroke-width="3"/>
  <text x="550" y="1227" font-family="Arial, sans-serif" font-size="14" font-weight="bold" fill="#fca5a5" text-anchor="middle">FAIL ✗</text>
  <text x="550" y="1244" font-family="Arial, sans-serif" font-size="10" fill="#fecaca" text-anchor="middle">Error Logs</text>
  
  <!-- ERROR RECOVERY -->
  <rect x="50" y="1280" width="700" height="30" rx="5" fill="#991b1b"/>
  <text x="400" y="1300" font-family="Arial, sans-serif" font-size="16" font-weight="bold" fill="white" text-anchor="middle">ERROR RECOVERY FLOWS</text>
  
  <rect x="80" y="1320" width="640" height="20" rx="3" fill="#450a0a" stroke="#7f1d1d" stroke-width="1"/>
  <text x="90" y="1333" font-family="Courier, monospace" font-size="9" fill="#fca5a5" text-anchor="start">Timeout (30s) → Retry once → Fail safe</text>
  
  <rect x="80" y="1345" width="640" height="20" rx="3" fill="#450a0a" stroke="#7f1d1d" stroke-width="1"/>
  <text x="90" y="1358" font-family="Courier, monospace" font-size="9" fill="#fca5a5" text-anchor="start">Parse fail → Default values → Build</text>
  
  <rect x="80" y="1370" width="640" height="20" rx="3" fill="#450a0a" stroke="#7f1d1d" stroke-width="1"/>
  <text x="90" y="1383" font-family="Courier, monospace" font-size="9" fill="#fca5a5" text-anchor="start">Invalid effect → Filter out → Continue</text>
  
  <!-- Arrow marker definition -->
  <defs>
    <marker id="arrowhead" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <polygon points="0 0, 10 3, 0 6" fill="#64748b"/>
    </marker>
  </defs>
</svg>![mc](https://github.com/user-attachments/assets/fd57c18a-81c4-402d-a840-56fb9e75cf0c)
)

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

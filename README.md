# AI-Powered Code Generation System

A constraint-based LLM system that converts natural language descriptions into production-ready compiled code. Implements structured output parsing, API validation, and automated build pipelines to ensure reliable code generation.

## Features

- **Local LLM Integration** - Uses Ollama with Qwen 2.5 (0.5B) for fast inference (<3 seconds)
- **Constraint Validation System** - Prevents hallucination with API whitelisting and regex validation
- **Automatic Value Clamping** - Enforces domain-specific bounds (nutrition 1-12, saturation 0.1-1.2)
- **Multi-Stage Error Recovery** - Fallback defaults when AI outputs invalid data
- **Complete Build Pipeline** - Generates source code, resources, and compiles to executable artifacts
- **Zero Manual Intervention** - End-to-end automation from prompt to compiled output

## Quick Start

### Prerequisites
- Google Colab account (free tier works)
- Project template (zip file)
- Any required assets (textures, configs, etc.)

### Usage

1. **Open the notebook** in Google Colab with GPU runtime (T4 recommended)

2. **Run the setup cells** to install Ollama and dependencies

3. **Upload your template**
```python
uploaded = files.upload()
agent.setup_project(list(uploaded.keys()))
```

4. **Generate code**
```python
description = "A healing item that restores health over time"
item_id = "healing_potion"
item_name = "Healing Potion"

logic = agent.get_balanced_logic(description)
agent.create_food(item_id, item_name, logic)
```

5. **Compile** (produces working executable)
```python
agent.finish()  # Downloads compiled artifact
```

## Technical Stack

- **Python** - Core automation and code generation
- **Ollama** - Local LLM inference engine  
- **Qwen 2.5 (0.5B)** - Lightweight language model optimized for speed
- **Regex-based parsing** - Robust extraction from unstructured AI output
- **Gradle** - Build automation and dependency management
- **Java 21** - Target compilation environment

## System Architecture

1. **Structured Prompting** - Constrains LLM output with explicit format rules and validation requirements
2. **Multi-Pattern Parsing** - Regex extraction handles variations in AI response format
3. **Validation Layer** - Checks all generated identifiers against whitelist of 30+ valid API endpoints
4. **Value Clamping** - Enforces numeric bounds to prevent unrealistic outputs
5. **Code Injection** - Inserts generated logic into template structure with proper imports
6. **Automated Compilation** - Gradle build produces tested, executable artifacts

## Reliability Features

### Hallucination Prevention
- Pre-validated API endpoint whitelist
- Effect ID validation (30+ vanilla options)
- Ingredient deduplication and filtering
- Invalid item rejection system

### Error Recovery
- Default fallbacks for all parsed values
- Connection timeout handling (30s max)
- Build failure detection with detailed logging
- Graceful degradation when AI fails

## License

**Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)**

- Use, modify, and share for non-commercial purposes
- Commercial use prohibited without permission

## Contributing

This project is currently **not accepting contributions** as it's part of a personal portfolio. Feel free to fork for your own non-commercial use.

## Technical Notes

- First build downloads dependencies (~1-2 minutes)
- Colab's free T4 GPU sufficient for 0.5B parameter model
- System operates fully offline after initial setup
- Average generation time: 3-5 seconds per item
- Target domain: Fabric API (Minecraft 1.21.1) - architecture is domain-agnostic

## About

Built as part of an AI & Data Science engineering curriculum, demonstrating:
- Production LLM constraint systems
- Automated code generation pipelines
- Structured output parsing from language models
- Build automation integration
- Error handling and reliability engineering

## Links
- [Ollama Documentation](https://ollama.ai/docs)
- [Fabric API Docs](https://fabricmc.net/wiki/tutorial:introduction)

---

**Domain application:** Minecraft Fabric mods | **Architecture:** Generalizable to any code generation target

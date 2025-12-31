# AI-Powered Minecraft Fabric Mod Generator 🎮🤖

An intelligent system that generates balanced Minecraft food items with status effects using local LLMs. Upload a mod template, describe your item, and get a fully compiled Minecraft 1.21.1 Fabric mod in minutes.

## ✨ Features

- 🧠 **Local LLM Integration** - Uses Ollama with Qwen 2.5 Coder (1.5B) for intelligent game balance
- ⚖️ **Automatic Balance System** - Smart value clamping ensures nutrition (1-12) and saturation (0.1-1.2) stay realistic
- 🎯 **Robust Parsing** - Brute-force regex extraction handles unpredictable AI responses with fallback defaults
- 🏗️ **Complete Mod Generation** - Generates textures, JSON resources, Java code, and Creative Tab integration
- 📦 **One-Click Compilation** - Automatic Gradle build produces ready-to-use JAR files
- 🎨 **Minecraft 1.21.1 Compatible** - Uses proper Mojang mappings and dual JSON resource format

## 🚀 Quick Start

### Prerequisites
- Google Colab account (free tier works)
- Minecraft Fabric mod template for 1.21.1 (zip file)
- Texture file (16x16 PNG recommended)

### Usage

1. **Open the notebook** in Google Colab with GPU runtime (T4 recommended)

2. **Run the setup cells** to install Ollama and dependencies

3. **Upload your mod template**

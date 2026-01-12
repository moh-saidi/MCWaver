
# AI-Powered Minecraft Fabric Mod Generator 🎮🤖

An intelligent system that generates balanced Minecraft food items with status effects using local LLMs. Upload a mod template, describe your item, and get a fully compiled Minecraft 1.21.1 Fabric mod in minutes.

**🌐 [Try it online at modweaver.netlify.app](https://modweaver.netlify.app/)**

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
uploaded = files.upload()
agent.setup_project(list(uploaded.keys()))

text

4. **Define your food item**
description = "A spicy taco that gives Fire Resistance for 30 seconds"
item_id = "spicy_taco"
item_name = "Spicy Taco"

text

5. **Generate and build**
logic = agent.get_balanced_logic(description)
agent.create_mod_files(item_id, item_name, logic)
agent.finish()

text

6. **Compile the mod** (optional - produces working JAR)
- Run the Java 21 installation cell
- Execute the Gradle build cell
- Download your compiled mod!

## 🎯 Example Output

📊 Extracted Logic: {
'nutrition': 6,
'saturation': 0.8,
'effect_id': 'MobEffects.FIRE_RESISTANCE',
'duration': 600,
'amplifier': 0
}
✅ Build Successful!
📦 Found Mod File: taco-1.0.0.jar

text

## 🛠️ Technical Stack

- **Python** - Core automation and file generation
- **Ollama** - Local LLM inference engine
- **Qwen 2.5 Coder (1.5B)** - Lightweight code generation model
- **Minecraft Fabric API** - Mod framework for 1.21.1
- **Gradle** - Build automation
- **Java 21** - Minecraft mod compilation
- **PIL** - Texture processing

## 📋 How It Works

1. **Project Setup** - Extracts mod template, parses `fabric.mod.json` for mod ID and structure
2. **AI Balance Generation** - Queries local LLM for appropriate nutrition, saturation, and effects
3. **Robust Parsing** - Uses regex to extract values regardless of AI response format
4. **Resource Generation** - Creates JSON models, item definitions, and language files for 1.21.1
5. **Java Code Injection** - Generates `ModItems.java` with proper Mojang mappings and Creative Tab registration
6. **Gradle Compilation** - Builds the mod into a distributable JAR file

## 🎨 Generated Files Structure

mod_project/
├── src/main/java/[package]/
│ ├── ModItems.java (AI-generated with balanced values)
│ └── [MainClass].java (auto-injected initialization)
└── src/main/resources/
└── assets/[mod_id]/
├── textures/item/[item_id].png
├── models/item/[item_id].json
├── items/[item_id].json
└── lang/en_us.json

text

## 🔒 License

**Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)**

- ✅ Use, modify, and share for non-commercial purposes

## 🤝 Contributing

This project is currently **not accepting contributions** as it's part of a personal portfolio. However, feel free to fork for your own non-commercial use!

## ☕ Support

If you find this project helpful, consider buying me a coffee!

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-Support-yellow?style=for-the-badge&logo=buy-me-a-coffee)](https://buymeacoffee.com/spaghettios)

## 📝 Notes

- First Gradle build may take 1-2 minutes to download dependencies
- Colab's free tier T4 GPU is sufficient for the 1.5B parameter model
- The system works offline after initial Ollama model download
- Tested with Minecraft 1.21.1 Fabric mods

## 🎓 About

Created as part of an AI & Data Science engineering curriculum project, demonstrating practical applications of:
- Local LLM integration
- Automated code generation
- Game balance systems
- Full-stack mod development pipeline

## 🔗 Links

- **[ModWeaver Web App](https://modweaver.netlify.app/)** - Try the online version
- [Fabric Mod Development](https://fabricmc.net/wiki/tutorial:introduction)
- [Ollama Documentation](https://ollama.ai/docs)
- [Minecraft Modding Resources](https://minecraft.wiki/)

---

**Made with ❤️ for the Minecraft modding community**

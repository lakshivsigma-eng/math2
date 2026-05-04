# Kumon Worksheet Generator

Generate custom Kumon-style math worksheets for any level and topic! This tool uses AI to generate problems and creates professionally formatted worksheets with front and back pages that match Kumon's design style.

Todo:
add these data sources
| Source           | Nature              | Best For                                      |
| ---------------- | ------------------- | --------------------------------------------- |
| MathGenerator    | Algorithmic         | Endless, randomized, rapid-fire speed drills. |
| DeepMind Dataset | Massive Static Bank | Diverse, curriculum-aligned problems (2M+).   |
| OpenSAT/GSM8K    | Human-Authored      | Realistic standardized test patterns.         |

## Features

- 🎯 **All Kumon Levels**: Support for Levels 6A through O
- 📚 **Topic Selection**: Choose from specific topics within each level
- 🤖 **AI Problem Generation**: Automatically generates problems using OpenAI or OpenRouter.io
- 📄 **Professional Layout**: Adaptive layouts that match Kumon's style (Level B vs Level H differences)
- 🔄 **Front & Back Pages**: Automatically splits problems across front and back
- 📥 **PDF Export**: Download worksheets as PDF files

## Quick Start

**Fastest way to get started:**

```bash
make install  # Install dependencies
make setup    # Create .env file
# Edit .env and add your OPENAI_API_KEY
make run      # Start the app
```

Visit **http://localhost:5000** and start generating worksheets!

📖 **For detailed instructions:** See [QUICKSTART.md](QUICKSTART.md)

## Setup

### Using Makefile (Recommended)

1. **Clone the repository**:
   ```bash
   git clone https://github.com/tejvirmann/kumon-worksheet-generator.git
   cd kumon-worksheet-generator
   ```

2. **Install dependencies**:
   ```bash
   make install
   ```

3. **Set up environment**:
   ```bash
   make setup
   ```

4. **Edit `.env` file** and configure your AI provider:
   
   **For OpenRouter.io (Recommended):**
   ```
   AI_PROVIDER=openrouter
   OPENROUTER_API_KEY=your-openrouter-api-key-here
   OPENAI_MODEL=openai/gpt-4
   ```
   
   **For OpenAI Direct:**
   ```
   AI_PROVIDER=openai
   OPENAI_API_KEY=your-openai-api-key-here
   OPENAI_MODEL=gpt-4
   ```
   
   See [OPENROUTER_SETUP.md](OPENROUTER_SETUP.md) for details.

5. **Run the application**:
   ```bash
   make run
   # OR for development mode with auto-reload:
   make dev
   ```

6. **Open in browser**:
   Navigate to `http://localhost:5000`

### Manual Setup

1. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Create `.env` file**:
   ```
   OPENAI_API_KEY=your_key_here
   ```

3. **Run the application**:
   ```bash
   python app.py
   ```

## Usage

1. Select a Kumon level from the dropdown (e.g., Level B, Level H, Level K)
2. Choose a topic within that level
3. Specify the number of problems (default: 10)
4. Click "Generate Worksheet"
5. Download the generated PDF

## AI Model Configuration

**Current Model:** GPT-4 (configurable)

- **Local:** Uses model specified in `.env` (defaults to `gpt-4`)
- **Deployment:** Same model, controlled by environment variable `OPENAI_MODEL`

To change the model, add to your `.env`:
```
OPENAI_MODEL=gpt-3.5-turbo  # or gpt-4, gpt-4-turbo
```

See [DEPLOYMENT.md](DEPLOYMENT.md) for more details.

## Deployment

This is a Flask web application that can be deployed to:

- **Render** (Recommended - Easy setup, free tier)
- **Railway** (Simple, $5/month credit)
- **Fly.io** (Global distribution, free tier)
- **Vercel** (Serverless, requires adaptation)
- **Heroku** ($7/month minimum)

📖 **Full deployment guide:** See [DEPLOYMENT.md](DEPLOYMENT.md)

**Note:** PyPI is for publishing Python packages, not for deploying web applications. Use one of the platforms above for web deployment.

## Project Structure

```
kumon-worksheet-generator/
├── app.py                  # Flask web application
├── problem_generator.py    # AI problem generation
├── worksheet_generator.py  # PDF worksheet creation
├── kumon_levels.json       # Level and topic data
├── templates/
│   └── index.html         # Web interface
├── output/                # Generated PDFs (created automatically)
└── requirements.txt       # Python dependencies
```

## Image Analysis Complete ✅

The worksheet generator has been fully updated to match actual Kumon worksheet styling based on analysis of real Kumon worksheets (Levels H and K):

- **Header Design**: KUMON logo, level identifier, centered title, student info fields, performance tracking table
- **Typography**: Clean sans-serif fonts with proper sizing (Level H: 11pt, Level K: 10pt)
- **Layout Adaptation**: 
  - Level H and simpler levels: Single column layout with generous spacing
  - Level K and advanced levels: Two-column layout with compact spacing
- **Footer**: Copyright notice in vertical text along left margin
- **Problem Formatting**: Problems numbered with parentheses: (1), (2), etc.
- **Colors**: Dark purple (#4B2E83) for headers, black for content, gray for footer

## Mathematical Notation

The generator currently renders problems as plain text. For advanced mathematical expressions (fractions, exponents, etc.), you may want to enhance the problem generator to output LaTeX or MathML format, which can be rendered using additional libraries like `matplotlib` or `sympy`.

## License

MIT License

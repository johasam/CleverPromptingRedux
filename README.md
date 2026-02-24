# Clever Prompting

Interactive Jupyter notebooks demonstrating advanced LLM prompting techniques using the OpenAI API.

## Live Site

The notebooks are hosted as a JupyterLite site on GitHub Pages:

**https://johasam.github.io/CleverPromptingRedux/**

## Notebooks

| # | Notebook | Topic |
|---|----------|-------|
| 01 | Basic Calls | Simple API calls and structured output with Pydantic |
| 02 | Self-Consistency | Running the same prompt N times and aggregating results |
| 03 | LLM Judges | Using an LLM to score summary quality against a reference |
| 04 | Token Probability | Inspecting token-level log probabilities and alternatives |
| 05 | Function Calling | Multi-step tool use with a calculator function |

## Project Structure

```
clever-prompting/
├── .gitlab-ci.yml              # CI/CD pipeline: build JupyterLite & deploy to GitHub Pages
├── jupyter_lite_config.json    # JupyterLite build configuration
├── requirements-build.txt      # Build dependencies (jupyterlite-core, pyodide kernel)
├── content/                    # Jupyter notebooks served by JupyterLite
│   ├── 01_basic_calls.ipynb
│   ├── 02_self_consistency.ipynb
│   ├── 03_llm_judges.ipynb
│   ├── 04_token_probability.ipynb
│   └── 05_function_calling.ipynb
├── clever_prompting/           # Original Python modules
├── prompting_through_code/     # Original Python scripts
└── README.md
```

## Deployment

The site is automatically deployed via GitLab CI/CD:

1. **Build stage**: Installs `jupyterlite-core` and builds the static site from `content/`
2. **Deploy stage**: Pushes the built site to the `gh-pages` branch of the GitHub repository using an SSH deploy key

### Setup Requirements

1. **GitLab CI/CD Variable**: Add the SSH private key as a CI/CD variable named `GITHUB_DEPLOY_KEY` (type: File or Variable, protected, masked).

2. **GitHub Deploy Key**: Add the corresponding public key as a deploy key on the GitHub repository (`Settings > Deploy keys`) with **write access** enabled.

3. **GitHub Pages**: Configure the repository to serve GitHub Pages from the `gh-pages` branch.

## Local Build

```bash
pip install -r requirements-build.txt
jupyter lite build --config jupyter_lite_config.json
# Open _output/index.html in a browser
```

<div align="center">
  <br />
    <a href="https://www.librai.tech">
      <img alt="LibrAI Logo" src="./fig/librai_librai.png" alt="LibrAI Logo" width="50%" height="auto">
    </a>
  <br />
</div>

# Loki: An Open-source Tool for Fact Verification

## Overview
Loki is our open-source solution designed to automate the process of verifying factuality. It provides a comprehensive pipeline for dissecting long texts into individual claims, assessing their worthiness for verification, generating queries for evidence search, crawling for evidence, and ultimately verifying the claims. This tool is especially useful for journalists, researchers, and anyone interested in the factuality of information. To stay updated, please subscribe to our newsletter at [our website](https://www.librai.tech/) or join us on [Discord](https://discord.gg/NRge6RS7)!

## Components
- **Decomposer:** Breaks down extensive texts into digestible, independent claims, setting the stage for detailed analysis.
- **Checkworthy:** Assesses each claim's potential significance, filtering out vague or ambiguous statements to focus on those that truly matter. For example, vague claims like "MBZUAI has a vast campus" are considered unworthy because of the ambiguous nature of "vast."
- **Query Generator:** Transforms check-worthy claims into precise queries, ready to navigate the vast expanse of the internet in search of truth.
- **Evidence Crawler:** Ventures into the digital realm, retrieving relevant evidence that forms the foundation of informed verification.
- **ClaimVerify:** Examines the gathered evidence, determining the veracity of each claim to uphold the integrity of information.

## Quick Start

### Clone the repository and navigate to the project directory
```bash
git clone https://github.com/Libr-AI/OpenFactVerification.git
cd OpenFactVerification
```

### Installation with poetry (option 1)
1. Install Poetry by following it [installation guideline](https://python-poetry.org/docs/).
2. Install all dependencies by running:
```bash
poetry install
```

### Installation with pip (option 2)
1. Create a Python environment at version 3.9 or newer and activate it.

2. Navigate to the project directory and install the required packages:
```bash
pip install -r requirements.txt
```

### Configure API keys

You can choose to export essential api key to the environment

- Example: Export essential api key to the environment
```bash
export SERPER_API_KEY=... # this is required in evidence retrieval if serper being used
export OPENAI_API_KEY=... # this is required in all tasks
export ANTHROPIC_API_KEY=... # this is required only if you want to replace openai with anthropic
export LOCAL_API_KEY=... # this is required only if you want to use local LLM
export LOCAL_API_URL=... # this is required only if you want to use local LLM
```

Alternatively, you can save the api information in a yaml file with the same key names as the environment variables and pass the path to the yaml file as an argument to the `check_response` method.

See `demo_data\api_config.yaml` as an example of the api configuration file.
- Example: Pass the path to the api configuration file
```bash
python -m factcheck --modal string --input "MBZUAI is the first AI university in the world" --api_config demo_data/api_config.yaml
```

### Test

<p align="center"><img src="./fig/cmd_example.gif"/></p>

To test the project, you can run the `factcheck.py` script:
```bash
# String
python -m factcheck --modal string --input "MBZUAI is the first AI university in the world"
# Text
python -m factcheck --modal text --input demo_data/text.txt
# Speech
python -m factcheck --modal speech --input demo_data/speech.mp3
# Image
python -m factcheck --modal image --input demo_data/image.webp
# Video
python -m factcheck --modal video --input demo_data/video.m4v
```

## Usage

The main interface of the Fact-check Pipeline is located in `factcheck/core/FactCheck.py`, which contains the `check_response` method. This method integrates the complete pipeline, where each functionality is encapsulated in its class as described in the Features section.

Example usage:
```python
from factcheck import FactCheck

factcheck_instance = FactCheck()

# Example text
text = "Your text here"

# Run the fact-check pipeline
results = factcheck_instance.check_response(text)
print(results)
```

Web app usage:
```bash
python webapp.py --api_config demo_data/api_config.yaml
```
<p align="center"><img src="./fig/web_input.png"/></p>
<p align="center"><img src="./fig/web_result.png"/></p>


## Contributing
We welcome contributions from the community! If you'd like to contribute, please follow these steps:
1. Fork the repository.
2. Create a new branch for your feature (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the branch (`git push origin feature/AmazingFeature`).
5. Open a pull request.


## Customize Your Experience

### Custom Models
```bash
python -m factcheck --modal string --input "MBZUAI is the first AI university in the world" --api_config demo_data/api_config.yaml --model claude-3-opus-20240229 --prompt claude_prompt
```

### Custom Evidence Retrieval
```bash
python -m factcheck --modal string --input "MBZUAI is the first AI university in the world" --api_config demo_data/test_api_config.yaml --retriever google
```

### Custom Prompts
```bash
python -m factcheck --modal string --input "MBZUAI is the first AI university in the world" --api_config demo_data/test_api_config.yaml --prompt demo_data/sample_prompt.yaml
```

## Ready for More?

💪 **Join Our Journey to Innovation with the Supporter Edition**

As we continue to evolve and enhance our fact-checking solution, we're excited to invite you to become an integral part of our journey. By registering for our Supporter Edition, you're not just unlocking a suite of advanced features and benefits; you're also fueling the future of trustworthy information.

Your support enables us to:

🚀 Innovate continuously: Develop new, cutting-edge features that keep you ahead in the fight against misinformation.

💡 Improve and refine: Enhance the user experience, making our app not just powerful, but also a joy to use.

🌱 Grow our community: Invest in the resources and tools our community needs to thrive and expand.

🎁 And as a token of our gratitude, registering now grants you **complimentary token credits**—a little thank you from us to you, for believing in our mission and supporting our growth!


<div align="center">


| Feature                                | Open-Source Edition | Supporter Edition |
|----------------------------------------|:-------------------:|:------------------:|
| Trustworthy Verification Results       | ✅                   | ✅                  |
| Diverse Evidence from the Open Web     | ✅                   | ✅                  |
| Automated Correction of Misinformation | ✅                   | ✅                  |
| Privacy and Data Security              | ✅                   | ✅                  |
| Multimodal Input                       | ✅                   | ✅                  |
| One-Stop Custom Solution               | ❌                   | ✅                  |
| Customizable Verification Data Sources | ❌                   | ✅                  |
| Enhanced User Experience               | ❌                   | ✅                  |
| Faster Efficiency and Higher Accuracy  | ❌                   | ✅                  |


</div>

[TRY NOW!](https://aip.librai.tech/login)


## Stay Connected and Informed


Don’t miss out on the latest updates, feature releases, and community insights! We invite you to subscribe to our newsletter and become a part of our growing community.

💌 Subscribe now at [our website](https://www.librai.tech/)!


## Change Log

1. **API Key Handling:** Transitioned from creating key files via copying to dynamically reading all API keys from a YAML file, streamlining configuration processes.
2. **Unified Configuration Dictionary:** Replaced platform-specific dictionaries with a unified dictionary that aligns with environmental variable naming conventions, enhancing consistency and maintainability.
3. **Model Switching:** Introduced a `--model` parameter that allows switching between different models, currently supporting OpenAI and Anthropic.
4. **Modular Architecture:** Restructured the codebase into one Base class file and individual class files for each model, enhancing modularity and clarity.
5. **Base Class Redefinition:** Redefined the Base class to abstract asynchronous operations and other functionalities. Users customizing models need only override three functions.
6. **Prompt Switching:** Added a `--prompt` parameter for switching between predefined prompts, initially supporting prompts for OpenAI and Anthropic.
7. **Prompt Definitions via YAML and JSON:** Enabled prompt definitions using YAML and JSON, allowing prompts to be automatically read from corresponding YAML or JSON files when the prompt parameter ends with `.yaml` or `.json`.
8. **Search Engine Switching:** Introduced a `--retriever` parameter to switch between different search engines, currently supporting Serper and Google.
9. **Webapp Frontend Optimization:** Optimized the web application frontend to prevent duplicate requests during processing, including disabling the submit button after a click and displaying a timer during processing.
10. **Client Switching:** introduce a --client parameter that allows switching between different client (chat API), currently support OpenAI compatible API (for local model and official model), and Anthropic chat API client.

## Development Plan

As Loki continues to evolve, our development plan focuses on broadening capabilities and enhancing flexibility to meet the diverse needs of our users. Here are the key areas we are working on:

## 1. Support for Multiple Models
- **Broader Model Compatibility:**
  - Integration with leading AI models besides ChatGPT and Claude to diversify fact-checking capabilities, including Command R and Gemini.
  - Implementation of self-hosted model options for enhanced privacy and control, e.g., FastChat, TGI, and vLLM.

## 2. Model-specific Prompt Engineering
- **Unit Testing for Prompts:**
  - Develop robust unit tests for each step to ensure prompt reliability and accuracy across different scenarios.

## 3. Expanded Search Engine Support
- **Diverse Search Engines:**
  - Incorporate a variety of search engines including Bing, scraperapi to broaden search capabilities.
  - Integration with [Searxng](https://github.com/searxng/searxng), an open-source metasearch engine.
  - Support for specialized indexes like LlamaIndex and Langchain, and the ability to search local documents.

## 4. Deployment and Scalability
- **Dockerization:**
  - Packaging Loki into Docker containers to simplify deployment and scale-up operations, ensuring Loki can be easily set up and maintained across different environments.

We are committed to these enhancements to make Loki not just more powerful, but also more adaptable to the needs of a global user base. Stay tuned as we roll out these exciting developments!


## License
This project is licensed under the [MIT license](LICENSE.md) - see the LICENSE file for details.

## Acknowledgments
- Special thanks to all contributors who have helped in shaping this project.

<!---
add slack channel here
-->

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=Libr-AI/OpenFactVerification&type=Date)](https://star-history.com/#Libr-AI/OpenFactVerification&Date)

## Cite as
```
@misc{Loki,
  author = {Wang, Hao and Wang, Yuxia and Wang, Minghan and Geng, Yilin and Zhao, Zhen and Zhai, Zenan and Nakov, Preslav and Baldwin, Timothy and Han, Xudong and Li, Haonan},
  title = {Loki: An Open-source Tool for Fact Verification},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/Libr-AI/Loki}},
}
```

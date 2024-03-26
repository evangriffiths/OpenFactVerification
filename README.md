<div align="center">
  <br />
    <a href="https://www.librai.tech">
      <img alt="LibrAI Logo" src="./fig/librai_librai.png" alt="LibrAI Logo" width="50%" height="auto">
    </a>
  <br />
</div>

# OpenFactVerification: An Open-source Tool for Fact Verification

## Overview
OpenFactChecking is a simplified open-source version of our online fact-checking tool designed to automate the process of verifying factuality. It provides a comprehensive pipeline for dissecting long texts into individual claims, assessing their worthiness for verification, generating queries for evidence search, crawling for evidence, and ultimately verifying the claims. This tool is especially useful for journalists, researchers, and anyone interested in the factuality of information. To stay updated, please subscribe to our newsletter at [our website](https://www.librai.tech/) or join our [slack channel](to_be_added)!

## Components
- **Decomposer:** Splits a long text into several independent claims for further processing.
- **Checkworthy:** Evaluates each claim to determine if it's worth checking. For example, vague claims like "MBZUAI has a vast campus" are considered unworthy because of the ambiguous nature of "vast."
- **Query Generator:** For each check-worthy claim, generates queries to search for evidence on search engines, aiding in the validation of the claim's authenticity.
- **Evidence Crawler:** Uses search engines to find evidence based on the queries generated, collecting results for analysis.
- **ClaimVerify:** Analyzes the search results to ascertain the accuracy of the claims.

## Quick Start
### Prerequisites
- Python 3.9 or newer
- Required Python packages are listed in `requirements.txt`

### Installation
1. Clone the repository:
```bash
git clone https://github.com/Libr-AI/factcheckservice.git
```
2. Navigate to the project directory and install the required packages:
```bash
cd factcheckservice
pip install -r requirements.txt
```

3. Configure api keys

You can choose to export essential api key to the environment, or configure it in `factcheck/config/secret_dict.py`.

- Example: Export essential api key to the environment
```bash
export SERPER_API_KEY=... # this is required in evidence retrieval if serper being used
export OPENAI_API_KEY=... # this is required in all tasks
export ANTHROPIC_API_KEY=... # this is required only if you want to replace openai with anthropic
```

### Test

<p align="center"><img src="./fig/cmd_example.gif"/></p>

To test the project, you can run the `factcheck.py` script:
```bash
# String
python factcheck.py --modal string --input "MBZUAI is the first AI university in the world"
# Text
python factcheck.py --modal text --input demo_data/text.txt
# Speech
python factcheck.py --modal speech --input demo_data/speech.mp3
# Image
python factcheck.py --modal image --input demo_data/image.webp
# Video
python factcheck.py --modal video --input demo_data/video.m4v
```

## Usage

The main interface of the Fact-check Pipeline is located in `factcheck/core/FactCheck.py`, which contains the `check_response` method. This method integrates the complete pipeline, where each functionality is encapsulated in its class as described in the Features section.

Example usage:
```python
from factcheck.core.FactCheck import check_response

# Example text
text = "Your text here"

# Run the fact-check pipeline
results = check_response(text)
print(results)
```

Web app usage:
```bash
python webapp.py
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
| Multimodal Input                       | ❌                   | ✅                  |
| One-Stop Custom Solution               | ❌                   | ✅                  |
| Customizable Verification Data Sources | ❌                   | ✅                  |
| Enhanced User Experience               | ❌                   | ✅                  |
| Faster Efficiency and Higher Accuracy  | ❌                   | ✅                  |


</div>

[TRY NOW!](https://aip.librai.tech/login)


## Stay Connected and Informed


Don’t miss out on the latest updates, feature releases, and community insights! We invite you to subscribe to our newsletter and become a part of our growing community.

💌 Subscribe now at [our website](https://www.librai.tech/)!



## License
This project is licensed under the [MIT license](LICENSE.md) - see the LICENSE file for details.

## Acknowledgments
- Special thanks to all contributors who have helped in shaping this project.

<!---
add slack channel here
-->


## Cite as
```
@misc{openfactverification,
  author = {LibrAI},
  title = {OpenFactVerification: An Open-source Tool for Fact Verification},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/Libr-AI/OpenFactVerification}},
}
```
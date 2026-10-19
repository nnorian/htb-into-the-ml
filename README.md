# HTB AI Red Teamer — Lab Work

Completed exercises from the [Hack The Box Academy](https://academy.hackthebox.com/) **AI Red Teamer** career path. This module covers offensive security techniques targeting machine learning systems — from poisoning training data to evading deployed classifiers and exploiting ML infrastructure vulnerabilities. Each notebook is a hands-on lab where the attack is implemented, tested against a live HTB target, and verified.

## Techniques

- **Label flipping attacks** using [scikit-learn's LogisticRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) to demonstrate how flipping a fraction of training labels degrades classifier accuracy on targeted classes
- **Clean label poisoning** — crafting poisoned samples that look correctly labeled but shift the model's decision boundary, evaluated with [matplotlib](https://matplotlib.org/) visualizations
- **Trojan insertion into CNNs** — embedding a backdoor trigger pattern into an [MNIST](http://yann.lecun.com/exdb/mnist/) classifier built with [PyTorch](https://pytorch.org/), so the model behaves normally except on inputs containing the trigger
- **Pickle deserialization attacks** — exploiting Python's [pickle](https://docs.python.org/3/library/pickle.html) module to embed arbitrary code execution payloads inside serialized PyTorch model files (`.pth`)
- **FGSM (Fast Gradient Sign Method)** — generating adversarial examples by perturbing inputs along the gradient of the loss function, causing misclassification while keeping changes imperceptible
- **DeepFool** — computing minimal perturbations that cross the nearest decision boundary, a more precise evasion method than FGSM
- **Model reverse engineering** — querying a black-box classifier API to reconstruct a surrogate model using [joblib](https://joblib.readthedocs.io/)-serialized pipelines and [pandas](https://pandas.pydata.org/) for data handling
- **MCP server exploitation** — using [FastMCP](https://github.com/jlowin/fastmcp) to enumerate and exploit vulnerabilities in Model Context Protocol servers, including resource enumeration and prompt injection
- **Network anomaly detection** — building a [Random Forest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) classifier on the KDD dataset to detect network intrusions
- **SMS spam detection** — training a text classifier on the [UCI SMS Spam Collection](https://archive.ics.uci.edu/dataset/228/sms+spam+collection)

## Libraries and Tools

| Library | Purpose |
|---------|---------|
| [PyTorch](https://pytorch.org/) | CNN training, adversarial example generation, model trojan insertion |
| [torchvision](https://pytorch.org/vision/stable/index.html) | MNIST dataset loading and image transforms |
| [scikit-learn](https://scikit-learn.org/) | Logistic regression, random forest, preprocessing pipelines |
| [NumPy](https://numpy.org/) | Array manipulation for dataset poisoning and perturbation math |
| [matplotlib](https://matplotlib.org/) | Plotting adversarial examples, decision boundaries, confusion matrices |
| [pandas](https://pandas.pydata.org/) | Data wrangling for network and tabular datasets |
| [seaborn](https://seaborn.pydata.org/) | Statistical visualizations and heatmaps |
| [FastMCP](https://github.com/jlowin/fastmcp) | MCP server client for resource enumeration and exploitation |
| [Pillow](https://python-pillow.org/) | Image encoding/decoding for adversarial image payloads |
| [joblib](https://joblib.readthedocs.io/) | Model serialization for surrogate model persistence |

## Project Structure

```
├── Introduction-to-Red-Teaming-AI/
│   ├── network-anomalies-detector/
│   ├── SPAM-detection/
│   ├── the-small-natwork-model/
│   └── redteam_code/
├── AI-Data-Attacks/
│   ├── label-flipping/
│   ├── evaluating-targeted-label-attack/
│   ├── evaluating-the-clean-label-atack/
│   ├── pickles-n-steganography/
│   ├── trojan-attack/
│   └── skill-assesment/
├── AI-Evasion-II/
└── Attacking-AI/
    └── vulnerable-MCP-servers/
```

- [Introduction-to-Red-Teaming-AI/](Introduction-to-Red-Teaming-AI/) — Foundational ML security: building classifiers (network anomaly detection, spam filtering) and understanding what makes them vulnerable
- [AI-Data-Attacks/](AI-Data-Attacks/) — Training data poisoning: label flipping, clean label attacks, trojan backdoors in neural networks, and pickle deserialization exploits
- [AI-Evasion-II/](AI-Evasion-II/) — Evasion attacks against deployed models: FGSM and DeepFool adversarial example generation
- [Attacking-AI/](Attacking-AI/) — Application-layer attacks: reverse engineering black-box models via API queries and exploiting MCP server vulnerabilities

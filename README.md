[manuscript.md](https://github.com/user-attachments/files/27108966/manuscript.md)
PC-STNO: Physics-Constrained Spatiotemporal Neural Operator

📖 Overview

PC-STNO is a deep learning framework designed for high-resolution meteorological downscaling, specifically targeting Surface Solar Radiation (SSR). By integrating physical constraints into a spatiotemporal neural operator architecture, PC-STNO effectively bridges the gap between coarse-resolution reanalysis data (like ERA5) and the high-fidelity irradiance fields required for precision energy planning.

The framework is built to capture large-scale atmospheric dynamics while respecting localized topographical modulations, providing a robust tool for reducing uncertainties in day-ahead photovoltaic (PV) forecasting.

✨ Key Features

Physics-Constrained Architecture: Embeds physical boundaries and radiative transfer priors into the learning process to ensure meteorologically consistent outputs.

Neural Operator Backbone: Leverages the power of Neural Operators (NOs) for resolution-invariant mapping, allowing for flexible downscaling across various spatial scales.

Spatiotemporal Modeling: Simultaneously accounts for temporal evolution and spatial dependencies in cloud advection and solar irradiance.

Energy-Focused: Specifically optimized for downstream integration into power grid dispatch simulators and renewable energy management systems.

🛠️ Installation

Prerequisites

Python 3.8 or higher

NVIDIA GPU + CUDA (Recommended)

Setup

Clone the repository:

git clone [https://github.com/your-username/PC-STNO.git](https://github.com/your-username/PC-STNO.git)
cd PC-STNO


Install dependencies:

pip install -r requirements.txt


Note: Ensure torch and torchvision are installed with the version matching your CUDA toolkit.

🚀 Quick Start

1. Data Preparation

Store your input datasets (e.g., ERA5 boundary conditions) and target data (high-resolution SSR) in the data/ folder.

data/
├── raw/
├── processed/
└── metadata/ (e.g., elevation, land mask)


2. Training

Configure your hyperparameters in configs/train_config.yaml and run:

python train.py --config configs/train_config.yaml


3. Inference

To generate downscaled fields using a pre-trained model:

python inference.py --checkpoint checkpoints/pcstno_v1.pth --input data/test_input.nc


📂 Project Structure

PC-STNO/
├── configs/            # Training and model configurations
├── data/               # Data storage and preprocessing scripts
├── models/             # PC-STNO architecture and physics-loss layers
│   ├── layers.py       # Spectral convolutions and operator blocks
│   └── physics.py      # Radiative constraint definitions
├── utils/              # Visualization and evaluation metrics
├── train.py            # Main training entry point
├── evaluate.py         # Performance validation scripts
└── README.md           # Documentation


🔮 Future Work & Roadmap

To advance the current modeling framework, future research must first address the fundamental uncertainties of coarse-resolution reanalysis data (e.g., ERA5) by fusing higher-resolution remote sensing products with dense ground-based observations. By constructing these high-quality, multimodal training datasets, we aim to pre-calibrate the driving data and mitigate systematic biases at the source. Building upon these refined meteorological inputs, subsequent efforts will transition towards practical engineering applications by integrating the model-derived, high-resolution irradiance fields into grid dispatch simulators. Consequently, this integration will allow for a direct, quantitative assessment of the model's economic viability, specifically demonstrating how enhanced day-ahead photovoltaic (PV) forecasting can reduce reserve capacity requirements and curtailment costs. Beyond these regional economic impacts, the ultimate objective is to validate the framework's global applicability. Therefore, it is imperative to expand the evaluation domains from currently restricted climatological regimes to more complex environments, such as hyper-arid deserts and high-latitude cryospheric domains. Through the implementation of cross-climate transfer learning mechanisms, the model's generalizability and robustness will be significantly enhanced, thereby ensuring reliable support for climate-resilient energy system planning on a global scale.

📝 Citation

If you use PC-STNO in your research, please cite our work:

@article{author2024pcstno,
  title={Physics-Constrained Spatiotemporal Neural Operator for High-Resolution Solar Radiation Downscaling},
  author={Your Name, Co-authors},
  journal={Your Target Journal},
  year={2024},
  url={[https://github.com/your-username/PC-STNO](https://github.com/your-username/PC-STNO)}
}


📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

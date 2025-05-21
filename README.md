# Smart Home AutoML Test Generator

This project demonstrates how to apply Automated Machine Learning (AutoML) to generate test cases for smart home systems based on behavioral data. The goal is to simulate real-world device usage, train a machine learning model to predict synchronization failures, and generate Python test functions for high-risk scenarios automatically.

## 🔍 Project Objective

- Simulate smart home device interactions (e.g., turning on lights, unlocking doors)
- Train an AutoML model to detect patterns that lead to failures (e.g., due to latency or concurrency)
- Automatically generate test case functions in Python for scenarios likely to fail
- Enable integration into CI/CD pipelines for dynamic, risk-based testing

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/your-username/smart-home-automl-testgen.git
cd smart-home-automl-testgen
```

### 2. Create a virtual environment (optional but recommended)

```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

Dependencies include:
- h2o
- pandas
- numpy
- scikit-learn

> Note: The first time H2O runs, it may take a few seconds to initialize the local cluster.
> Note2: Please make sure you are running JDK 64bits.

## ▶️ How to Run

Simply execute the main script:

```bash
python main.py
```

This will:

- Simulate 2500 smart home interactions with random latency and concurrency
- Train a classifier using H2O AutoML
- Predict which scenarios are most likely to fail
- Generate Python test functions for the riskiest cases
- Save the generated functions to a file called `generated_tests.py`

## 📄 Expected Results

After running the script, you should see:

- Console output showing AutoML training progress
- Summary of how many high-risk test cases were identified
- A new file: `generated_tests.py`

Example output in `generated_tests.py`:

```python
def test_generated_case_1242():
    # Predicted failure probability: 0.91
    send_command('unlock_door')
    simulate_network_latency(342)
    assert_device_sync(timeout=3000)
```

These tests simulate real usage conditions where the system is likely to experience synchronization failures.

## ✅ Applications

- Smart home system testing
- Risk-based test generation
- Continuous testing in CI/CD pipelines
- AutoML-driven quality assurance

## 📬 Feedback

Pull requests and suggestions are welcome! Feel free to fork the project and adapt it to your own smart system use cases.

# Startup Health Scoring Model

Project submission for the ScaleDux Artificial Intelligence Intern role (Task 1).

This repository contains a Python-based model designed to evaluate and rank 100 startups based on key business indicators from the provided dataset.

### Project Objective

The primary goal of this project is to develop a "Startup Health Score," a composite metric designed to provide a quick and data-driven assessment of a startup's potential. This score facilitates the identification and ranking of the most promising companies within the dataset.

### Methodology

**1. Data Preprocessing**

Effective data preprocessing was crucial for creating a fair comparison between startups.

* **Normalization:** To standardize the features, which were on vastly different scales, Min-Max normalization was applied. This technique scales each feature to a 0-1 range, ensuring that all metrics contribute equitably to the final score.

* **Inverse Metric Handling:** The `monthly_burn_rate_inr` is an inverse metric, where a lower value is preferable. To properly incorporate this into the scoring system, the normalized value was inverted (as `1 - normalized_score`) to create a `burn_efficiency_score`. Consequently, startups with higher capital efficiency receive a higher score.

**2. Scoring Formula**

The core of the evaluation is a weighted formula that reflects the strategic importance of each business metric. The weights were assigned based on the following rationale:

| Feature                   | Weight | Rationale                                                                                                                   |
| ------------------------- | :----: | --------------------------------------------------------------------------------------------------------------------------- |
| **Monthly Active Users** |  25%   | Assigned the highest weight as it is a direct indicator of product-market fit and current customer traction.                  |
| **Team Experience** |  20%   | Weighted heavily as the execution capability and domain expertise of the founding team are critical predictors of success.    |
| **Burn Efficiency Score** |  15%   | Represents financial discipline and sustainability. A startup that manages its capital efficiently has a longer runway.      |
| **Market Size (TAM)** |  15%   | A large Total Addressable Market is essential for scalability and significant long-term growth potential.                     |
| **Valuation** |  15%   | Serves as a strong signal of external investor confidence and the perceived future value of the company.                       |
| **Funds Raised** |  10%   | While an important milestone, it is considered a lagging indicator compared to active user engagement and team strength.      |

**3. Key Findings**

The model's output provided a clear differentiation between high and low-potential startups. Analysis of the rankings revealed that top-performing companies consistently excelled in metrics with the highest weights, particularly `monthly_active_users` and `team_experience`. Conversely, lower-ranked startups typically showed significant weaknesses in these same areas, validating the model's logic. The generated visualizations, available in the `/outputs` directory, further illustrate these trends.

### How to Run This Project

To replicate the analysis, please follow these steps:

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/SrihariRamesh/ScaleDux_Task1.git](https://github.com/SrihariRamesh/ScaleDux_Task1.git)
    ```

2.  **Install Dependencies:** The project requirements are listed in the `requirements.txt` file. You can install them using pip:
    ```bash
    pip install -r requirements.txt
    ```

3.  **Execute the Notebook:** The complete analysis is contained within the `notebooks/ScaleDux_Task1_.ipynb` file. It is designed to be run sequentially in a Jupyter environment like Google Colab or JupyterLab.

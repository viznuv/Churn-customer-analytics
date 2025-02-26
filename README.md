# Customer Churn Simulation and Analysis

This repository contains Python code for simulating customer churn and performing various churn analyses, including survival analysis and cohort analysis.

## Overview

The core of the project is the `simulate_churn` function, which models customer acquisition and churn over a specified time horizon.  It allows for flexible configuration, including:

*   **Customizable Acquisition Rates:** Define how new customers are acquired over time using functions (e.g., linear growth, Poisson processes).
*   **Base Churn Rate:** Set the baseline probability of a customer churning.
*   **Churn Modifiers:**  Apply multiplicative factors to the churn rate based on customer attributes and behavior.  These modifiers can be defined using:
    *   **Conditions:**  Functions that evaluate customer data and determine whether a modifier applies.
    *   **Feature-Based Effects:**  Specify how specific feature values (e.g., "usage_frequency=low") affect the churn rate.
*   **Customer Features:**  Generate random customer attributes (e.g., usage frequency, plan type, age) using probability distributions.

The simulation generates a Pandas DataFrame containing customer histories, which is then used for various churn analyses:

*   **Kaplan-Meier Survival Analysis:**  Estimate and visualize survival curves, both overall and for different customer segments.  Calculate median survival time.
*   **Cox Proportional Hazards Regression:**  Identify the factors that significantly influence churn and quantify their effects (hazard ratios).
*   **Churn Rate Over Time:**  Track the overall churn rate throughout the simulation period.
*   **Cohort Analysis:**  Analyze customer retention rates based on their acquisition date (cohort).  Visualize retention patterns using a heatmap.

## Getting Started

### Prerequisites

*   Python 3.7+
*   Required Libraries (install using `pip`):
    ```bash
    pip install pandas numpy lifelines matplotlib scipy seaborn
    ```

### Running the Simulation and Analysis

1.  **Clone the repository:**

    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

2.  **Run the Python script:**

    ```bash
    python churn_simulation.py
    ```

    This will execute the example simulation and analysis code, generating plots and printing results to the console.

## Code Structure

*   **`simulate_churn(n_customers, time_horizon, acquisition_rate_func, base_churn_rate, churn_rate_modifiers, start_date, features=None, feature_churn_effects=None, random_seed=42, age_groups=None)`:**  The main function for simulating customer churn.  See the function docstring for detailed parameter descriptions.
*   **`plot_km_curve(df, duration_col, event_col, label=None)`:**  Generates a Kaplan-Meier survival curve plot.
*   **`perform_cox_regression(df, duration_col, event_col, covariates)`:**  Performs Cox Proportional Hazards regression.
*   **`calculate_median_survival_time(kmf)`:** Calculates median survival times
*   **Example Usage (`if __name__ == "__main__":`)**:  Contains example code demonstrating how to define simulation parameters, run the simulation, and perform the analyses.  You should modify this section to customize the simulation to your specific needs.

## Customization

The example usage section provides a starting point.  You can customize the simulation by:

*   **Modifying `acquisition_rate_func`:** Change how new customers are added.
*   **Adjusting `base_churn_rate`:** Set the baseline churn probability.
*   **Defining `churn_rate_modifiers`:** Add conditions and factors that influence churn.
*   **Specifying `features` and `feature_churn_effects`:** Create customer attributes and define how they impact churn.
*   **Changing `time_horizon` and `start_date`:** Adjust the simulation's duration and starting point.
*   **Setting the `random_seed`:**  Ensure reproducibility of the simulation.

## Output

The script generates the following outputs:

*   **Console Output:**  Prints the head of the simulated DataFrame, median survival time, and the Cox regression summary.
*   **Plots:**
    *   Kaplan-Meier Survival Curve (overall and segmented by plan type, usage frequency, and age group).
    *   Cox Regression Coefficients Plot.
    *   Churn Rate Over Time Plot.
    *   Cohort Retention Matrix Heatmap.

## Contributing

Contributions are welcome!  Please feel free to submit pull requests or open issues to suggest improvements or report bugs.

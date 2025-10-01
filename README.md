# MLflow Quickstart: Experiment Tracking and Model Management

## Problem Statement and Goal of Project

This project serves as a practical demonstration of leveraging **MLflow** for robust machine learning experiment tracking, model logging, and management. The primary goal is to showcase a complete MLOps workflow, from training and comparing multiple models to registering and versioning them in the MLflow Model Registry. The focus is on demonstrating the process and tooling rather than achieving state-of-the-art model accuracy.

## Solution Approach

The project uses the classic Iris dataset to train and evaluate a **Logistic Regression** classifier. The core of the solution involves the following steps:

1.  **Experimentation:** Two separate models are trained with different hyperparameters (`solver`, `random_state`, etc.).
2.  **MLflow Tracking:** For each training run, MLflow is used to log:
      * **Parameters:** The hyperparameters used for the model.
      * **Metrics:** The accuracy score of the trained model.
      * **Tags:** Descriptive tags for easy identification.
      * **Models:** The trained scikit-learn model itself, along with its signature and an input example.
3.  **Model Registration:** The trained models are registered under the name `tracking_quick_start` in the MLflow Model Registry, creating new versions for each run. This demonstrates an understanding of model versioning and lineage.
4.  **Inference & Validation:** The logged models are loaded back from the registry using their URI to perform predictions on a test set, validating that the models can be successfully retrieved and used for inference.

An important aspect of this project was encountering and solving a common MLOps challenge: MLflow's automatic dependency inference failed, issuing a `WARNING`. This was intentionally addressed by demonstrating how to manage dependencies explicitly, a critical skill for creating reproducible and deployable models.

## Technologies & Libraries

The project is built using the following core technologies:

  * [cite\_start]**MLflow:** Version 2.16.2 [cite: 1]
  * [cite\_start]**Scikit-learn:** For model training and evaluation [cite: 1]
  * [cite\_start]**Pandas & NumPy:** For data manipulation [cite: 1]
  * [cite\_start]**UV:** As the environment manager for model validation [cite: 1]
  * [cite\_start]**Matplotlib:** For plotting (included in requirements) [cite: 1]
  * [cite\_start]**IPykernel:** For running the Jupyter Notebook [cite: 1]

## Description about Dataset

The project utilizes the well-known **Iris dataset**, available directly through the `scikit-learn` library. This dataset contains 150 samples of iris flowers, each with four features:

  * Sepal Length (cm)
  * Sepal Width (cm)
  * Petal Length (cm)
  * Petal Width (cm)

The goal is to classify each flower into one of three species: Setosa, Versicolour, or Virginica.

## Installation & Execution Guide

To replicate this project, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone <your-repository-url>
    cd <repository-directory>
    ```
2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```
3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Start the MLflow Tracking Server:**
    Open a separate terminal and run the following command to start the MLflow UI.
    ```bash
    mlflow ui
    ```
    The UI will be accessible at `http://127.0.0.1:5000`.
5.  **Run the Jupyter Notebook:**
    Launch the `project.ipynb` notebook and execute the cells sequentially to train the models and log the results to your MLflow server.

## Key Results / Performance

The project successfully demonstrates the end-to-end tracking of multiple model training runs. The key outcome is not the model's accuracy but the structured logging of all relevant artifacts in MLflow.

  * **Run 1 Accuracy:** The first model achieved a specific accuracy score, which was logged as a metric.
  * **Run 2 Accuracy:** The second model, with different hyperparameters, achieved another accuracy score.
  * **Model Versions:** The notebook created versions 3 and 4 of the `tracking_quick_start` model in the Model Registry.

These results are visible and comparable in the MLflow UI, showcasing the ability to track model performance over time and across different experiments.

## Sample Output

Here is a sample DataFrame generated at the end of the notebook, comparing the model's predictions against the actual test data. This demonstrates the successful loading of a tracked model from MLflow and its use for inference.

```
    sepal length (cm)  sepal width (cm)  petal length (cm)  petal width (cm)  actual data  predict data
0                 6.1               2.9                4.7               1.4            1             1
1                 5.7               3.0                4.2               1.2            1             1
2                 5.7               4.4                1.5               0.4            0             0
3                 5.1               3.8                1.6               0.2            0             0
4                 5.0               2.3                3.3               1.0            1             1
```

## Additional Learnings / Reflections

This project was a valuable exercise in understanding the practical challenges of MLOps. A key takeaway was observing the `WARNING` message during model logging, where MLflow's automatic environment capture failed. This highlights a critical real-world scenario: **automatic dependency inference is not always reliable**. The best practice, and the one I would implement in a production setting, is to explicitly define dependencies in a `requirements.txt` file and pass it during model logging to ensure 100% reproducibility. This project solidified my understanding of why explicit dependency management is non-negotiable for building robust and deployable machine learning systems.

💡 *Some interactive outputs (e.g., plots, widgets) may not display correctly on GitHub. If so, please view this notebook via [nbviewer.org](https://nbviewer.org) for full rendering.*

## 👤 Author

## Mehran Asgari

## **Email:** [imehranasgari@gmail.com](mailto:imehranasgari@gmail.com).

## **GitHub:** [https://github.com/imehranasgari](https://github.com/imehranasgari).

-----

## 📄 License

This project is licensed under the Apache 2.0 License – see the `LICENSE` file for details.
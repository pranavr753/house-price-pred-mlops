### House Price Prediction using ZenML

This project demonstrates a robust and modular **Machine Learning Pipeline** for predicting house prices using ZenML. It employs industry-standard practices for reproducibility, scalability, and maintainability of ML workflows. Designed with the principles of clean architecture and modern design patterns, this project exemplifies how pipelines can be seamlessly integrated with tools like MLflow for experiment tracking and deployment.

---

### Features
1. **End-to-End Pipeline**:
   - Data ingestion, cleaning, and preprocessing.
   - Feature engineering with transformations, outlier detection, and scaling.
   - Model training, evaluation, and deployment using **ZenML Pipelines**.

2. **Pipeline Steps**:
   - **Data Ingestion**: Automated handling of multiple data formats and ingestion strategies.
   - **Handling Missing Values**: Implemented custom strategies such as dropping or imputing missing values.
   - **Feature Engineering**: Incorporated log transformations, scaling, and one-hot encoding for preprocessing.
   - **Outlier Detection**: Utilized Z-score and IQR methods to detect and handle outliers effectively.
   - **Model Training and Evaluation**: Built scalable models using linear regression, tracked with **MLflow** for experiment comparison.

3. **Continuous Deployment**:
   - Leveraged **ZenML's integration with MLflow** for automating deployment pipelines.
   - Enabled real-time inference using a deployed model served via MLflow's REST APIs.

4. **Integration of Design Patterns**:
   - **Factory Pattern**: Dynamically instantiated data ingestion and handling classes.
   - **Strategy Pattern**: Used for encapsulating multiple strategies like missing value imputation and outlier detection.
   - **Pipeline Abstraction**: Designed reusable pipelines to ensure modular and extendable architecture.

5. **Experiment Tracking and Visualization**:
   - Enabled tracking of experiments using **MLflow** to compare model performance metrics.
   - Visualized the entire pipeline and step dependencies on the ZenML dashboard.

---

### Installation Guide
Follow the steps below to set up and execute the project:

1. **Install ZenML**  
   Refer to the [ZenML installation guide](https://docs.zenml.io/getting-started/installation) for installation.

2. **Set up a Virtual Environment**  
   Download the source code and create a virtual environment. Follow this [YouTube guide](https://youtu.be/GZbeL5AcTgw?si=uj7B8-10kbyEytKo) if you need assistance.

3. **Install Required Python Packages**  
   Activate the virtual environment and run:
   ```bash
   pip install -r requirements.txt
   ```

4. **Install ZenML Integrations**  
   For running deployment pipelines:
   ```bash
   zenml integration install mlflow -y
   ```

5. **Set Up the ZenML Stack**  
   The project requires an MLflow experiment tracker and model deployer. Configure your stack as follows:
   ```bash
   zenml experiment-tracker register mlflow_tracker --flavor=mlflow
   zenml model-deployer register mlflow --flavor=mlflow
   zenml stack register local-mlflow-stack -a default -o default -d mlflow -e mlflow_tracker --set
   ```

---

### Execution Steps
To execute the pipeline:
1. Run the training pipeline:
   ```bash
   python run_pipeline.py
   ```

2. Deploy the model:
   ```bash
   python run_deployment.py
   ```

3. Make batch predictions using the deployed model:
   ```bash
   python batch_prediction.py
   ```

---

### Insights from the Project
- **ZenML's Modularity**: Using ZenML pipelines allows for highly modular workflows, where individual steps like ingestion, feature engineering, and deployment can be isolated and optimized independently.
- **Scalability**: The integration with MLflow ensures that the project is deployable across distributed systems, with scalability and monitoring capabilities.
- **Reusability**: With design patterns like Strategy and Factory, this project can be easily extended to new datasets or ML algorithms.

---

### Visualization of the Pipeline
<img width="1715" alt="image" src="https://github.com/user-attachments/assets/6d141f2d-b6a7-4e22-b301-a50fbd3ea94d" />


The pipeline dashboard offers a detailed view of every pipeline step, its outputs, and its runtime configuration, making debugging and optimization intuitive.

---

Feel free to explore, modify, and enhance the pipeline to fit your use case. For any queries or issues, check out the [ZenML documentation](https://docs.zenml.io)

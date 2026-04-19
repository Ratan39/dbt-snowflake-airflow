# Modern Data Stack: Airflow + dbt + Snowflake Pipeline

This project demonstrates a production-grade data engineering workflow using the **Astro CLI**. It orchestrates **dbt** transformations within **Apache Airflow** using the **Cosmos** library, targeting a **Snowflake** data warehouse.

## Project Architecture
The pipeline automates the transformation of raw data into analytics-ready datasets. By using **Astronomer Cosmos**, the project dynamically generates Airflow DAGs directly from dbt models, reducing boilerplate code and ensuring that the orchestration layer always matches the transformation logic.

### Key Technical Highlights:
* **Orchestration:** Apache Airflow running on the Astronomer platform.
* **Transformation:** dbt (Data Build Tool) utilizing a modular **Marts** layer.
* **Storage:** Snowflake Cloud Data Warehouse.
* **Dynamic DAGs:** Automatic dbt-to-Airflow task mapping via the `DbtDag` class.
* **Dependency Isolation:** dbt runs in a dedicated Python virtual environment (`dbt_venv`) to prevent library conflicts.
* **Integrity Testing:** A custom Pytest suite with monkeypatching validates DAG parsing and Snowflake connection logic without requiring live credentials during CI.


Deploy Your Project Locally
===========================

Start Airflow on your local machine by running 'astro dev start'.

This command will spin up five Docker containers on your machine, each for a different Airflow component:

- Postgres: Airflow's Metadata Database
- Scheduler: The Airflow component responsible for monitoring and triggering tasks
- DAG Processor: The Airflow component responsible for parsing DAGs
- API Server: The Airflow component responsible for serving the Airflow UI and API
- Triggerer: The Airflow component responsible for triggering deferred tasks

When all five containers are ready the command will open the browser to the Airflow UI at http://localhost:8080/. You should also be able to access your Postgres Database at 'localhost:5432/postgres' with username 'postgres' and password 'postgres'.

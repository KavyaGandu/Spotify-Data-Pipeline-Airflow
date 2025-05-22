# Spotify Airflow Data Pipeline

This project implements a scalable and automated Spotify data pipeline using Apache Airflow, AWS S3, Lambda, and optionally AWS Glue for transformations.

---

## Overview

- Extracts Spotify playlist data using the Spotify API via Lambda functions.
- Stores raw data in AWS S3 (`raw_data/to_processed` folder).
- Uses Airflow DAGs to orchestrate the full ETL workflow.
- Transforms data using Python in Airflow tasks or AWS Glue jobs.
- Moves processed data into organized S3 folders for analytics.

---

## Setup Instructions

1. **Spotify API Credentials**  
   - Create a Spotify app on [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/applications).  
   - Obtain `Client ID` and `Client Secret`.  
   - Add these as Airflow Variables (`spotify_client_id`, `spotify_secret_id`).

2. **AWS Setup**  
   - Create an S3 bucket to store raw and processed data.  
   - Create an IAM user with permissions for S3, Lambda, and Glue as needed.  
   - Add AWS credentials as Airflow Connection (`aws_s3_spotify` or your custom name).

3. **Airflow Environment**  
   - Install required Python packages via `requirements.txt` (e.g., `spotipy`, `apache-airflow-providers-amazon`).  
   - Deploy DAG files in Airflow’s DAG folder.

4. **Running the Pipeline**  
   - Trigger the Airflow DAG manually or schedule it daily.  
   - Monitor DAG runs and task logs via Airflow UI.  
   - Verify data in S3 bucket folders.

---

## Project Structure

- `dags/spotify_airflow_pipeline.py` - Main Airflow DAG for extraction, processing, and storage.  
- `dags/spotify_trigger_external.py` - (Optional) DAG to orchestrate Lambda and Glue workflows.  
- `requirements.txt` - Python dependencies.  
- `docker-compose.yml` - Docker environment setup (if applicable).

---

## Key Components

- **Airflow Variables:** Store API keys securely, accessible via `Variable.get()`.  
- **Python Operators:** Run custom Python functions for data processing.  
- **S3 Operators and Hooks:** Upload/download data from AWS S3.  
- **Lambda Operators:** Invoke AWS Lambda functions for extraction or transformation.  
- **Glue Operators:** Trigger AWS Glue jobs for scalable transformations (optional).

---

## License

MIT License

---

Feel free to open issues or pull requests for improvements!

---

# Contact

Kavya Gandu - [LinkedIn](https://linkedin.com/in/yourprofile) - kavyag.py@gmail.com

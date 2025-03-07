# airflow-from-scratch
An Airflow Installation From Scratch

## Installation
- Create new virtual environment
- Run 'pip install -r requirements.txt'

## Create PostgreSQL Database
`CREATE DATABASE airflow_db;
CREATE USER airflow_user WITH PASSWORD 'airflow_pass';
GRANT ALL PRIVILEGES ON DATABASE airflow_db TO airflow_user;
-- PostgreSQL 15 requires additional privileges:
GRANT ALL ON SCHEMA public TO airflow_user;
ALTER USER airflow_user SET search_path = public;
ALTER SCHEMA public OWNER TO airflow_user;`


## Initialize the database
export AIRFLOW__DATABASE__SQL_ALCHEMY_CONN="postgresql+psycopg2://airflow_user:airflow_pass@localhost:5432/airflow_db"
export AIRFLOW__DATABASE__SQL_ALCHEMY_SCHEMA="public"
airflow db migrate

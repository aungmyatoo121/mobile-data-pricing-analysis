# Start the Docker container
docker start myproject 

# Access the container
docker exec -it myproject /bin/bash

# Connect to PostgreSQL
psql -U postgres

# Create a new database
CREATE DATABASE my_portfolio_internet_pricing;

# Create a new user with a password
CREATE USER my_portfolio_internet_pricing WITH PASSWORD '12345';

# Verify database creation
SELECT datname FROM pg_database;

# Connect to the newly created database
\c my_portfolio_internet_pricing postgres

# Grant all privileges on the public schema to the user
GRANT ALL ON SCHEMA public TO my_portfolio;

# Install the required package
pip install xlsx2csv

# Convert Excel file to CSV
xlsx2csv "Data pricing.xlsx" "Data pricing_formatted.csv"

# ETL Server Access Log Processing DAG

This Airflow Directed Acyclic Graph (DAG) processes server access logs using an Extract-Transform-Load (ETL) pipeline. The pipeline downloads a server access log file, extracts relevant data, transforms it, and then loads the transformed data into a zip file.

## Overview

This DAG consists of four tasks: `download`, `extract`, `transform`, and `load`. Each task performs a specific step in the ETL process.

## DAG Configuration

The DAG is configured with the following properties:

- **Owner**: Selase Perry
- **Start Date**: The DAG's start date is set to the current date.
- **Email**: Email notifications are sent to `psterlings@gmail.com` on task failure.
- **Retries**: The DAG retries a failed task once.
- **Retry Delay**: The delay between task retries is set to 5 minutes.

## Task Details

### `download`

This task downloads the server access log file from the specified URL.

### `extract`

This task extracts relevant data from the downloaded log file and saves it to a new file (`extracted.txt`).

### `transform`

This task transforms the extracted data by converting lowercase letters to uppercase and saves the transformed data to another file (`capitalized.txt`).

### `load`

This task compresses the transformed data file (`capitalized.txt`) into a zip file (`log.zip`).

## Task Dependencies

The tasks are connected in a linear dependency chain, where each task depends on the successful completion of the preceding task:


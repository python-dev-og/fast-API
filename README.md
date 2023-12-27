![Python Version](https://img.shields.io/pypi/pyversions/fastapi)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?&style=for-the-badge&logo=docker&logoColor=white)


# FastAPI Customer and Invoice Management System

This FastAPI application provides a RESTful API for managing customers and their invoices. It uses Pydantic for data validation and includes endpoints for creating and retrieving customers and invoices.

## Features

- **Customer Management**: Add new customers and retrieve customer details.
- **Invoice Management**: Create invoices for customers and retrieve invoice details.

## Installation

Before running the application, ensure you have FastAPI and Uvicorn installed. You can install them using pip:

```bash
pip install fastapi uvicorn
```

## Usage

Run the application using Uvicorn:

```bash
uvicorn main:app --reload
```

The application will be available at `http://127.0.0.1:8000`.

## Endpoints

### General

- `GET /`: Returns a welcome message.

### Customer Endpoints

- `POST /customer`: Create a new customer.
- `GET /customer/{customer_id}`: Retrieve a customer by their ID.

### Invoice Endpoints

- `POST /customer/{customer_id}/invoice`: Create a new invoice for a customer.
- `GET /customer/{customer_id}/invoice`: Retrieve all invoices for a specific customer.
- `GET /invoice/{invoice_no}`: Retrieve a specific invoice by its number.
- `GET /invoice/{invoice_no}/{stockcode}/`: Retrieve a specific stock code on an invoice.
- `POST /invoice/{invoice_no}/{stockcode}/`: Add a stock code to an invoice.

## Models

### Customer

- `customer_id`: The unique identifier for the customer.
- `country`: The country of the customer.

### URLLink

- `url`: Optional URL link.

### Invoice

- `invoice_no`: The invoice number.
- `invoice_date`: The date of the invoice.
- `customer`: Optional link to the customer.

## Data Storage

This application uses a simple in-memory dictionary (`fakeInvoiceTable`) to store invoices. In a production environment, this should be replaced with a database system.

Certainly! Here's an updated section of your `README.md` to include information about the Docker setup for your FastAPI application:

---

## Docker Support

This application is Docker-ready. A Dockerfile is included for easy deployment.

### Dockerfile

The Dockerfile uses `tiangolo/uvicorn-gunicorn-fastapi:python3.11` as the base image, which is optimized for FastAPI applications.

```Dockerfile
FROM tiangolo/uvicorn-gunicorn-fastapi:python3.11

COPY ./app /app
```

### Building the Docker Image

To build the Docker image for this application, navigate to the directory containing the Dockerfile and run:

```bash
docker build -t your-app-name .
```

Replace `your-app-name` with the desired name for your Docker image.

### Running the Application with Docker

After building the image, you can run the application using the following command:

```bash
docker run -d --name your-container-name -p 80:80 your-app-name
```
To view the API on swagger when the container is up and running 

```commandline
http://localhost/docs
```


This will start a container named `your-container-name` and expose the application on port 80.


## Error Handling

The application handles errors and returns appropriate HTTP status codes. For instance, if a customer is not found, it returns a 404 status code.

## Contribution

Contributions to improve this application are welcome. Please ensure to follow the best practices in coding and documentation.

![Screenshot 2023-12-27 at 4.08.14 PM.png](images%2FScreenshot%202023-12-27%20at%204.08.14%E2%80%AFPM.png)
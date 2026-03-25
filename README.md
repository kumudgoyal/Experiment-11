# Experiment-11: Microservices Lab

## Aim
Create 2 backend services in Python (Flask).
- **Customer Service**: Create API to fetch customer orders
- **Order Service**: Create API to update order status

## Learning Outcomes
By completing this experiment, you will learn:
- **Microservices Architecture**: Understand the principles of building distributed systems with independent services
- **RESTful API Development**: Design and implement REST APIs using Flask framework
- **Service Communication**: Implement HTTP-based communication between microservices
- **Data Aggregation**: Combine data from multiple services to provide unified responses
- **Error Handling**: Handle service unavailability and network errors gracefully
- **API Testing**: Test microservices endpoints using curl or other HTTP clients
- **Python Flask Framework**: Gain proficiency in building web applications with Flask
- **Dependency Management**: Use virtual environments and manage Python packages

## Overview
This experiment demonstrates a simple microservices architecture using Flask in Python. It consists of two independent services: a Customer Service and an Order Service that communicate via HTTP requests. The Customer Service retrieves customer information and fetches associated orders from the Order Service.

## Services

### Customer Service
- **Port**: 5001
- **Purpose**: Manages customer data and aggregates order information
- **Endpoints**:
  - `GET /`: Service health check
  - `GET /customers/<user_id>/orders`: Returns customer details with their orders

### Order Service
- **Port**: 5002
- **Purpose**: Manages order data
- **Endpoints**:
  - `GET /orders/user/<user_id>`: Returns orders for a specific user
  - `PUT /orders/<order_id>/status`: Updates order status

## Prerequisites
- Python 3.7+
- Virtual environment (recommended)
- 
## Running the Services

### Start Order Service
```bash
python micro-services-lab/order-service/order_app.py
```

### Start Customer Service
In a new terminal:
```bash
python micro-services-lab/customer-service/customer_app.py
```

## Testing the API

### Get customer with orders
```bash
curl http://localhost:5001/customers/101/orders
```

### Get orders for a user
```bash
curl http://localhost:5002/orders/user/101
```

### Update order status
```bash
curl -X PUT http://localhost:5002/orders/1/status -H "Content-Type: application/json" -d '{"order_status": "Delivered"}'
```

## Dependencies
- Flask==3.1.3
- requests
- gunicorn (for production deployment)

## Architecture
The services demonstrate:
- Service-to-service communication
- RESTful API design
- Data aggregation across services
- Error handling for service unavailability

## Notes
- Both services run in debug mode for development
- The Customer Service calls the Order Service synchronously
- Sample data is hardcoded for demonstration purposes

# Project Overview

This project sets up a local development environment for working with Kafka, Zookeeper, PostgreSQL, and Debezium. The setup includes multiple services, each with a specific role in the data pipeline. Below is an overview of each service and its purpose.

## Services

### 1. Zookeeper
- **Purpose**: Zookeeper is used to manage and coordinate the Kafka brokers. It maintains configuration information, tracks the status of Kafka nodes, and provides synchronization services for distributed systems.
- **Port**: `2181`

### 2. Kafka
- **Purpose**: Kafka is a distributed event streaming platform that allows you to publish and subscribe to streams of records. It acts as a broker for messages between producers and consumers.
- **Port**: `9092`
- **Depends on**: Zookeeper

### 3. PostgreSQL
- **Purpose**: PostgreSQL is a relational database management system. In this setup, it is used to store data that will be captured and streamed using Debezium.
- **Port**: `5432`
- **Credentials**:
  - Database: `mydb`
  - User: `myuser`
  - Password: `mypassword`

### 4. Debezium
- **Purpose**: Debezium is a CDC (Change Data Capture) tool that monitors your PostgreSQL database for changes and streams those changes into Kafka topics. It allows you to capture and stream data changes in real-time.
- **Port**: `8083`
- **Depends on**: Kafka and PostgreSQL

### 5. Kafka Consumer (Custom TypeScript Service)
- **Purpose**: This is a custom-built service written in TypeScript that consumes messages from a Kafka topic. The service listens for changes to a specific Kafka topic (linked to your PostgreSQL database table) and processes these changes.
- **Port**: `3000`
- **Depends on**: Kafka

## How to Use

1. **Start the services**: Run `docker-compose up` in the root directory to start all the services.
2. **Accessing the services**:
   - Zookeeper: Port `2181`
   - Kafka: Port `9092`
   - PostgreSQL: Port `5432`
   - Debezium: Port `8083`
   - Kafka Consumer: Port `3000`
3. **Stop the services**: Use `docker-compose down` to stop and remove all containers.

## Summary

This setup provides a complete environment for streaming data from a PostgreSQL database to Kafka using Debezium and then consuming that data with a custom TypeScript service.

📌 Project Overview

Trail Explorer is a microservices-based web application built as a student project for the Service-Oriented Architectures course.
The system demonstrates a complete service-oriented platform containing independently deployable services, containerization, event-driven communication, and advanced architectural concepts such as API Gateway, SAGA pattern, gRPC, NoSQL databases, and distributed monitoring/tracing.

The platform supports three roles: Administrator, Guide, and Tourist, and provides features such as user management, blog creation, tour creation, tour purchasing, following users, map interaction, and real-time tour execution tracking.

The project was developed through multiple coursework milestones, each introducing additional architectural challenges and requirements.

📌 System Architecture (Short Summary)

The application consists of several independent microservices:

Stakeholders Service – user registration, profiles, roles, administration (C#)

Blog Service – blogs, comments, likes, markdown-based content (Go)

Followers Service – user following system using Neo4j graph database (Go)

Tour Service – tour creation, map points, difficulty, tags, geospatial logic (C#)

Payment Service – shopping cart, checkout, tour tokens (C#)

Gateway Service – central API gateway routing all client requests (Go)

Each service maintains its own SQL or NoSQL database, runs independently, and communicates using REST, gRPC, or asynchronous event-based communication depending on the module.

All services are fully containerized with Docker, and the entire system is orchestrated via Docker Compose, which coordinates services, databases, and inter-service networking.

📌 My Contribution

I contributed to both functional features and key technical infrastructure across several services. My work includes:

🔹 User & Account Features

Implemented admin user blocking functionality

Developed user profile viewing (name, surname, profile image, biography, motto)

Implemented profile editing, including validation and image updates

🔹 Position Simulator

Built an interactive, map-based simulator for setting a tourist’s current location

Integrated simulated coordinates with the TourExecution module for real-time tracking

🔹 Tour Execution

Implemented the full tour session lifecycle: start, activity tracking, completion/abandoning

Added periodic proximity checks for completing key points during the tour

Supported execution of published and archived tours, enforcing purchase requirements

🔹 Technical Contributions

Dockerized multiple services and contributed to the Docker Compose environment

Migrated two REST endpoints to gRPC

Implemented a SAGA pattern using NATS for distributed workflow coordination

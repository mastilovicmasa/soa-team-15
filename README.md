# 📌 Project Overview

**Explorer** is a microservices-based web application built as a **student project** for the *Service-Oriented Architectures* course.  
The system demonstrates a complete service-oriented platform containing independently deployable services, containerization, event-driven communication, and advanced architectural concepts such as **API Gateway**, **SAGA pattern**, **gRPC**, **NoSQL databases**, and **distributed monitoring/tracing**.

The platform supports three roles: **Administrator**, **Guide**, and **Tourist**, and provides functionalities such as user management, blog creation, tour creation, tour purchasing, following users, map interaction, and real-time tour execution tracking.

The project was developed through multiple coursework milestones, each introducing new architectural requirements and complexity. It was created as a team project involving four students, with each team member responsible for implementing a distinct subset of functionalities and microservices.



# 📌 System Architecture (Short Summary)

The application consists of several independent microservices:

- **Stakeholders Service** – user registration, profiles, roles, administration (C#)  
- **Blog Service** – blogs, comments, likes, markdown-based content (Go)  
- **Followers Service** – user following system using a Neo4j graph database (Go)  
- **Tour Service** – tour creation, map points, difficulty, tags, geospatial logic (C#)  
- **Payment Service** – shopping cart, checkout, tour tokens (C#)  
- **Gateway Service** – central API gateway routing all client requests (Go)

Each service maintains its own **SQL or NoSQL database**, runs independently, and communicates using REST, gRPC, or asynchronous event-based communication depending on the module.

All services are fully **containerized with Docker**, and the entire system is orchestrated through **Docker Compose**, which coordinates services, databases, and inter-service networking.
<img width="1600" height="900" alt="docker_containers_running" src="https://github.com/user-attachments/assets/08bf80e4-c62b-42d4-80ee-4d46d5197add" />



# 📌 My Contribution

I contributed to both functional features and technical infrastructure across several services. My work includes:


## 🔹 User & Account Features
- Implemented **admin user blocking** functionality  
- Developed user **profile viewing** (name, surname, profile image, biography, motto)  
- Implemented **profile editing**, including validation and image updates  
<img width="1920" height="896" alt="user_profile" src="https://github.com/user-attachments/assets/73b50870-9a14-487b-bd2b-e57460a7d76a" />


## 🔹 Position Simulator
- Built an interactive **map-based simulator** for setting and updating the tourist’s current location  
- Integrated simulated coordinates with the **TourExecution** module for real-time tracking  


## 🔹 Tour Execution
- Implemented the full **tour session lifecycle**: start, activity tracking, completion/abandoning  
- Added periodic **proximity checks** for completing key points during the tour  
- Supported execution of **published and archived tours**, enforcing purchase requirements
<img width="1600" height="900" alt="tour_execution_in_positon_simulator" src="https://github.com/user-attachments/assets/cc749df8-efd3-468b-b9a6-8a4aab384c31" />






## 🔹 Technical Contributions
- **Dockerized** multiple services and contributed to the Docker Compose environment  
- Migrated two REST endpoints to **gRPC**  
- Implemented a **SAGA pattern** using **NATS** for distributed workflow coordination

# 📌 How to Run

To run the entire microservices system locally, follow the steps below.

1️⃣ Start All Services

First, start the full system using the main Docker Compose configuration:
docker-compose up --build

2️⃣ Execute migrations

Wait for all microservices, databases, message broker (NATS), and the API Gateway to fully start. Then run the database migrations required for the C# services:
docker-compose -f docker-compose-migration.yml up


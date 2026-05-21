# Voting Survey

## Overview
The **Voting Survey** project provides a RESTful API for managing user registrations, logins, constituencies, and administrative functionalities. It allows users to register, log in, and manage voting-related data efficiently.



2️⃣ **User Dashboard:**  
   - **User Details Section:** Displays the voter’s profile and constituency.  
   - **Candidates List:** Shows all election candidates in the user's constituency when the election is live.  
   - **Search Bar:** Allows users to search previous election results and other constituency details.  

3️⃣ **Voting Process:**  
   - Users can vote for any candidate **only during active elections**.  
   - Once a vote is cast, the **Vote button is disabled** to prevent multiple voting.  
   - In future elections, users can log in and vote again.  

4️⃣ **Real-Time Election Results:**  
   - Votes are updated **instantly** as users vote.  
   - The **party with the most votes is automatically ranked first**.  
   - Results are visible to everyone, ensuring transparency.  

---

### **🔴 Admin Functionalities**
1️⃣ **Admin Login:**  
   - Admins log in to access the election management panel.  

2️⃣ **Election Management:**  
   - **Register new candidates** for elections.  
   - **Add constituencies** and assign candidates.  
   - **Start or close elections** at any time.  

3️⃣ **Candidate & Party Management:**  
   - Admins can **delete candidates or parties** if needed.  

4️⃣ **Monitoring Election Activities:**  
   - Admins can **track votes in real-time**, view **which users have voted**, and monitor **total votes per candidate**.  
   - Admins can access a **list of all constituencies** and their assigned candidates.  

---

## API Endpoints

### Admin Endpoints

| S.No | Endpoint                          | Method | Description          |
|------|----------------------------------|--------|----------------------|
| 1    | `http://localhost:8090/api/admin/auth` | POST   | Admin login        |
| 2    | `http://localhost:8090/api/admin/{id}` | GET    | Get admin by ID    |

**Request Body for Admin Login:**
```json
{
    "id": 123,
    "password": "admin123",
   
}
```

### User Endpoints

| S.No | Endpoint                          | Method | Description                                  |
|------|----------------------------------|--------|----------------------------------------------|
| 1    | `http://localhost:8090/api/user/register` | POST   | Register a new user                         |
| 2    | `http://localhost:8090/api/user/login`    | POST   | User login                                  |
| 3    | `http://localhost:8090/api/user`          | GET    | Retrieve all users                          |
| 4    | `http://localhost:8090/api/user/{id}`     | GET    | Get user by ID                             |
| 5    | `http://localhost:8090/api/user/{id}`     | DELETE | Delete user by ID                          |
| 6    | `http://localhost:8090/api/user/{id}`     | PUT    | Update user details                        |
| 7    | `http://localhost:8090/api/user/voterId/{voterId}` | GET | Get user by voter ID                      |
| 8    | `http://localhost:8090/api/user/email/{email}` | GET | Get user by email                         |
| 9    | `http://localhost:8090/api/user/constituency/{name}` | GET | Get users by constituency name           |
| 10   | `http://localhost:8090/api/user/constituency/{state}/vote-status/{status}` | PUT | Update voting status for users in state |
| 11   | `http://localhost:8090/api/user/reset-votes/{constituencyNumber}` | PUT | Reset votes by constituency number      |
| 12   | `http://localhost:8090/api/user/voterId/{voterId}/vote-status/{status}` | PUT | Update voting status by voter ID       |

**Request Body for User Registration:**
```json
{
  "voterId": 99887766554433,
  "name": "Avneet Singh",
  "email": "akas@example.com",
  "password": "akas123",
  "age": 22,
  "gender": "Male",
  "address": "greater noida",
  "constituency": "surajpur greater noida",
  "constituencyNumber":1
}
```

### Constituency Endpoints

| S.No | Endpoint                          | Method | Description                      |
|------|----------------------------------|--------|----------------------------------|
| 1    | `http://localhost:8090/api/constituency` | POST   | Save constituency               |
| 2    | `http://localhost:8090/api/constituency` | GET    | Get all constituencies          |
| 3    | `http://localhost:8090/api/constituency/{id}` | GET    | Get constituency by ID          |
| 4    | `http://localhost:8090/api/constituency/state/{state}` | GET | Get constituency by state      |
| 5    | `http://localhost:8090/api/constituency/active` | GET | Get active constituencies      |
| 6    | `http://localhost:8090/api/constituency/allConstituencyByIdOrName?name={name}` | GET | Get constituency by name or ID |
| 7    | `http://localhost:8090/api/constituency/all` | POST  | Save multiple constituencies   |

**Request Body for Saving a Constituency:**
```json
{
  "id": 1,
  "name": "North Delhi",
  "state": "Delhi",
  "electionActive": true,
  "dOLS": "2024-02-15"
}
```

## Usage
- Ensure the backend server is running on `localhost:8090`.
- Use API testing tools like Postman or cURL to interact with the endpoints.

## Technologies Used
- Java (Spring Boot)
- REST API
- MySQL (Database)
- Hibernate (ORM)
- Maven (Build Tool)
- Spring Data JPA
- Lombok (Simplified Java Code)
- H2 Database (In-memory testing)

## Installation & Setup
1. Fork the repository from GitHub.
2. Clone your forked repository:
   ```sh
   git clone https://github.com/avneet23/Election-Survey-Spring-Boot-Backend-Project
   ```
3. Navigate to the project directory:
   ```sh
   cd voting-survey
   ```
4. Build the project using Maven:
   ```sh
   mvn clean install
   ```
5. Run the Spring Boot application:
   ```sh
   mvn spring-boot:run
   ```

## Project Structure
```
/votingsurvey
│── src/main/java/com/jspider/votingsurvey
│   │── VotingsurveyApplication.java
│   │── controller
│   │   ├── AdminController.java
│   │   ├── ConstituencyController.java
│   │   └── UserController.java
│   │── dao
│   │   ├── ConstituencyDao.java
│   │   ├── UsersDao.java
│   │   └── dashboard
│   │       ├── AdminDao.java
│   │       └── AdminImpDao.java
│   │── entity
│   │   ├── Admin.java
│   │   ├── Constituency.java
│   │   ├── Party.java
│   │   └── User.java
│   │── repository
│   │   ├── AdminRepository.java
│   │   ├── ConstituencyRepository.java
│   │   └── UserRepository.java
│   │── services
│── src/main/resources
│   │── application.properties
│── src/test/java
│── target/
│── pom.xml
│── README.md
```


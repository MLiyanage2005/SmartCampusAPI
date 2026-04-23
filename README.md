# SmartCampus API

## Overview
The SmartCampus API is a RESTful web service developed as part of the coursework for the CSA module. It simulates a smart campus environment by managing rooms, sensors, and sensor readings.

The system supports resource creation, retrieval, and validation, while enforcing business rules such as preventing deletion of rooms with active sensors and restricting readings from sensors under maintenance.

---

## Technologies Used
- Java (JAX-RS - javax.ws.rs)
- Jersey (REST implementation)
- Apache Tomcat 9 (Web Server)
- Maven (Build tool)
- JSON (Data format)

---

## Deployment Instructions

### Prerequisites
- Java JDK 8 or higher
- Apache NetBeans IDE
- Apache Tomcat 9

### Steps to Run
1. Clone the repository
   
2. Open the project in NetBeans.

3. Ensure Apache Tomcat 9 is configured in NetBeans.

4. Right-click the project and select
   
5. Run the project.

6. Access the API at:
   http://localhost:8080/SmartCampus_API/api/

---

## API Endpoints

### Base Endpoint
- `GET /api/`
- Returns API metadata and available resources

---

### Room Management

- `GET /api/rooms`
- Retrieve all rooms

- `POST /api/rooms`
- Create a new room

- `GET /api/rooms/{id}`
- Retrieve a specific room

- `DELETE /api/rooms/{id}`
- Delete a room (only if no sensors are assigned)

---

### Sensor Management

- `POST /api/sensors`
- Create a sensor (must belong to an existing room)

- `GET /api/sensors`
- Retrieve all sensors

- `GET /api/sensors?type={type}`
- Filter sensors by type

---

### Sensor Readings

- `GET /api/sensors/{id}/readings`
- Retrieve readings for a sensor

- `POST /api/sensors/{id}/readings`
- Add a new reading to a sensor

---

## Business Rules

- A sensor must be linked to an existing room.
- A room cannot be deleted if it contains sensors.
- Sensor readings cannot be added when the sensor is in "MAINTENANCE" status.

---

## Error Handling

The application implements custom exception handling using ExceptionMapper:

- 422 Unprocessable Entity  
- Returned when linked resources do not exist

- 409 Conflict  
- Returned when attempting to delete a room with sensors

- 403 Forbidden  
- Returned when adding readings to a sensor under maintenance

- 500 Internal Server Error  
- Returned for unexpected system errors

---

## Logging

A logging filter is implemented to log:
- Incoming HTTP requests
- Response status codes

---

## Notes

- The application uses `javax.ws.rs` as it is deployed on Apache Tomcat 9.
- The project follows REST principles including resource-based URIs and appropriate HTTP status codes.
- All data is stored in-memory using Java collections.

---

## Author
[Maneth Liyanage]

---

## License
This project is developed for academic purposes only.
   

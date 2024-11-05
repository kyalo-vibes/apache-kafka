 WikiMedia Project
=====================================

This project is a part of the WikiMedia organization and consists of two main components: Producer and Consumer.

 Producer
------------

The Producer is responsible for generating and publishing data to a Kafka topic. It uses the Wikimedia REST API to fetch data and then transforms it into a JSON format before publishing it to the Kafka topic. The Producer is written in Java and uses Spring Boot for building the application.

### API Documentation

#### Kafka API

The Producer uses the Kafka API to publish data to a Kafka topic. The API is documented below:

##### Produce Message

* **Endpoint:** `POST /topics/{topicName}`
* **Request Body:** `application/json`
* **Request Parameters:**
	+ `topicName`: The name of the Kafka topic to produce to.
	+ `message`: The message to produce to the topic.
* **Response:** `201 Created`

Example Request:
```bash
curl -X POST \
  http://localhost:8080/topics/my-topic \
  -H 'Content-Type: application/json' \
  -d '{"message": "Hello, World!"}'
```

#### Consume Message

* **Endpoint:** `GET /topics/{topicName}`
* **Request Parameters:**
    + `topicName`: The name of the Kafka topic to consume from.
* **Response:** `200 OK`

Example Request:
```bash
curl -X GET \
  http://localhost:8080/topics/my-topic
```

## Consumer

The Consumer is responsible for consuming data from a Kafka topic and performing certain operations on it. It uses Spring Boot and Spring Kafka for building the application. The Consumer also uses Apache Kafka for message brokering.

### API Documentation

#### Kafka API

The Consumer uses the Kafka API to consume data from a Kafka topic. The API is documented below:

##### Consume Message

* **Endpoint:** `GET /topics/{topicName}`
* **Request Parameters:**
    + `topicName`: The name of the Kafka topic to consume from.
* **Response:** `200 OK`

Example Request:
```bash
curl -X GET \
  http://localhost:8080/topics/my-topic
```

## Setup and Running

To setup and run the project, follow these steps:

1. Clone the repository: `git clone https://github.com/your-username/wikimedia-project.git`
2. Change into the project directory: `cd wikimedia-project`
3. Build the project: `./mvnw clean install`
4. Start the Kafka broker: `docker-compose up -d`
5. Start the Producer: `./producer/mvnw spring-boot:run`
6. Start the Consumer: `./consumer/mvnw spring-boot:run`

## Configuration

The project uses the following configuration files:

* `producer/src/main/resources/application.properties`: Configuration for the Producer.
* `consumer/src/main/resources/application.properties`: Configuration for the Consumer.
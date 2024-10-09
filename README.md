# Kafka-PySpark Real-Time Data Processing Project

This project allows real-time data input, processing with PySpark, and output via Kafka in a Dockerized environment. The producer sends real-time data to Kafka, PySpark processes it by adding 1 to the ASCII value of each character, and the consumer reads and displays the processed data.

## Prerequisites

- Docker and Docker Compose must be installed.
- Ensure that `/opt/kafka` and `/opt/spark` are present on your system.

## Setup and Running

1. **Clone the repository**:
   ```bash
   git clone https://github.com/EdIrfan/kafka-pyspark-real-time-project.git
   cd kafka-pyspark-real-time-project
   ```

2. **Build and Run Docker Containers**:
   ```bash
   docker-compose up --build
   ```

3. **Run the Producer**:
   - Open a new terminal and run the producer to send real-time input to Kafka:
     ```bash
     docker exec -it pyspark_container bash
     python3 kafka_producer.py
     ```

4. **Run the PySpark Transformation**:
   - In another terminal, run:
     ```bash
     docker exec -it pyspark_container bash
     spark-submit pyspark_transform.py
     ```

5. **Run the Consumer**:
   - Finally, run the consumer to receive and display the processed data:
     ```bash
     docker exec -it pyspark_container bash
     python3 kafka_consumer.py
     ```

6. **Real-Time Input**:
   - When the producer asks for input, type your data in real time. The processed data will appear in the consumer terminal.

## Spark UI

You can access the **Spark UI** to monitor the jobs at:
[http://localhost:8080](http://localhost:8080).

## Handling External Managed Environments

If you encounter issues with external environment management (common on Debian systems), you can create a virtual environment to isolate the Python dependencies:

1. **Create Virtual Environment**:
   ```bash
   python3 -m venv kafka-pyspark-env
   ```

2. **Activate the Virtual Environment**:
   ```bash
   source kafka-pyspark-env/bin/activate
   ```

3. **Install Requirements**:
   ```bash
   pip install -r requirements.txt
   ```

## Future Enhancements

- Planning to add Apache Hudi for data management.
- Planning to deploy the project on AWS and run producer node in local machine whereas consumer node will be a free tier instance in AWS EC2.
- Planning to add database functionality with the project running producer node on AWS and local system will be consumer node. 

## License

This project is licensed under the MIT License - see the LICENSE file for details.
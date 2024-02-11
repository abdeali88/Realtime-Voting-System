Realtime Election Voting System
===============================

The system is built using Python, Kafka, Spark Streaming, Postgres and Streamlit. The system is built using Docker Compose to easily spin up the required services in Docker containers.

## System Architecture
![system_architecture.jpg](images%2Fsystem_architecture.jpg)

## System Flow
![system_flow.jpg](images%2Fsystem_flow.jpg)

## System Components
- **main.py**: This is the main Python script that creates the required tables on postgres (`candidates`, `voters` and `votes`), it also creates the Kafka topic and creates a copy of the `votes` table in the Kafka topic. It also contains the logic to consume the votes from the Kafka topic and produce data to `voters_topic` on Kafka.
- **voting.py**: This is the Python script that contains the logic to consume the votes from the Kafka topic (`voters_topic`), generate voting data and produce data to `votes_topic` on Kafka.
- **spark-streaming.py**: This is the Python script that contains the logic to consume the votes from the Kafka topic (`votes_topic`), enrich the data from postgres and aggregate the votes and produce data to specific topics on Kafka.
- **streamlit-app.py**: This is the Python script that contains the logic to consume the aggregated voting data from the Kafka topic as well as postgres and display the voting data in realtime using Streamlit.

## Setting up the System
This Docker Compose file allows you to easily spin up Zookkeeper, Kafka and Postgres application in Docker containers. 


## Screenshots
### Candidates and Parties information
![candidates_and_party.png](images/candidates_and_party.png)
### Voters
![voters.png](images%2Fvoters.png)

### Voting
![voting.png](images%2Fvoting.png)

### Dashboard
![dashboard_image.png](images%2Fdashboard_image.png)


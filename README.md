# Kafka Data Streaming Application

## Project Description
This project demonstrates a simple data streaming application using Apache Kafka. The system consists of a producer that generates numerical data and a consumer that processes this data stream. The primary purpose is to showcase real-time data processing capabilities using Kafka's publish-subscribe pattern.

## Architecture & Flow Process

### Overall Flow
1. The producer generates a string of numbers ("1 2 3 4 5 6") every 2 seconds
2. This data is published to the Kafka topic named 'variance'
3. The consumer subscribes to the 'variance' topic and processes the incoming messages
4. The received messages are displayed in the console

```
┌──────────────┐     ┌───────────────────┐     ┌──────────────┐
│              │     │                   │     │              │
│   Producer   │────▶│  Kafka Broker(s)  │────▶│   Consumer   │
│              │     │   Topic: variance │     │              │
└──────────────┘     └───────────────────┘     └──────────────┘
```

## Implementation Details

### Producer (producer_variance.py)
- Connects to a Kafka broker running on localhost:9092
- Continuously generates a message containing "1 2 3 4 5 6"
- Publishes messages to the 'variance' topic
- Uses UTF-8 encoding for message serialization
- Waits 2 seconds between message publications

### Consumer (consumer_variance.py)
- Connects to the same Kafka broker
- Subscribes to the 'variance' topic
- Configured to start reading from the earliest available message
- Auto-commits offsets after processing
- Deserializes messages using UTF-8 decoding
- Simply prints the received messages to the console

## Tech Stack
- **Apache Kafka**: Distributed event streaming platform
- **Python 3**: Programming language used for implementation
- **kafka-python**: Python client library for Apache Kafka
  
## Prerequisites
- Python 3.x
- Apache Kafka (running on localhost:9092)
- kafka-python library (`pip install kafka-python`)

## Running the Application

1. Ensure Kafka is running on localhost:9092
2. Start the consumer:
   ```
   python consumer_variance.py
   ```
3. Start the producer in a separate terminal:
   ```
   python producer_variance.py
   ```

## Future Enhancements
- Implement actual calculation of variance from the numeric data
- Add error handling and recovery mechanisms
- Develop a web interface to visualize the data stream
- Scale to multiple consumers for parallel processing 
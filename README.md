# Kafka async messaging POC

This project objective is to create a prove of concept for a small consumer/producer asynchronous event-driven comunication using Kafka as a message broker. Kafka pusblishes events in collections where all of them are persisted and prepared to be consumed by services in a decoupled, escalable, reliable and resilient way (Service-Oriented Architecture).

Brief introduction of Kafka and their benefits: https://youtu.be/FKgi3n-FyNU

## Installation and setup process

In order to run this POC it's required to have Python3.7 runtime installed. Also is required to have docker installed to run kafka broker locally for testing purposes.

1. `py -m pip install -r requirements.txt`
2. `docker-compose up` 
3. `py consumer.py`
4. `py producer.py` 
    
At this point you should be seeing messages handled by the consumer.

## POC implementation details

In this example we use the default topic that Kafka brings by itself for simplicity (which is `default_ksql_processing_log`)

## Next steps

Endpoint configuration in the end should be moved to a EndpointFactory, where the implementation details of routing an event to a topic is hidden (a topic is designed to be one for each type of event so it follows SRP and have several benefits, for example, each topic could scale out independently). 

The aim of this is to have in the service DownloadRequestService, message bus should be injected, so it can be called with the event to raise, so it is put on the topic to be consumed by other services. Ideally MessageBus should be an interface so it can be easily and elegantly testable.

No worries, no rush for premature optimization on that, let's be pragmatic :)

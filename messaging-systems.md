***Notes about Messaging Systems I have worked with in different projects:***

**Goal**:
Enabling communication between producers and consumers using message-based topics. 

**Example**:
Commuincation between micro-services or different parts in the application. 

**General Terminologies**:

>> **Message Broker**:

![vmware-message-broker-publish](https://github.com/RadwaSaleh/miscellaneous/assets/33086179/d404c2f2-4c19-42d6-a698-6845a48a9eba)

 >> **Message Producer** 

 >> **Message Consumer** 

**Messaging Patterns:**

- **Point to Point**:
>> * Messages are persisted in a queue
>> * A message can be consumed by a maximum of one consumer only
>> * Message disappears from the queue once consumed 


- **Publish-Subscribe**
>> * Messages are persisted in a topic 
>> * Message Consumers/Subscribers subscribe to one or more topic and consume all the messages in that topic


---


**My Own Experience:**
- AWS Redis:

- Kafka: 

Kafka Broker: persists and replicates data.

Kafka Producer API: permits an application to push the message into the message container (one or more) called the Kafka Topic.

Kafka Consumer API: pulls the message from the Kafka Topic by subscribing to one or more topic.

Message: A stream of records.

Kafka Streams API: gives applications permissions to publish output stream, consume input stream 

Kafka Connector API: allows building and running reusable producers or consumers that connect Kafka topics to existing applications or data systems to push or capture every change.

![image](https://github.com/RadwaSaleh/miscellaneous/assets/33086179/75956cb4-b2ff-4b1e-acae-f26df3042419)

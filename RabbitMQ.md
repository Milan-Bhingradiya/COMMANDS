# RabbitMQ - Message Queue Basics & Using with Node.js (ES6)

## What is RabbitMQ?
RabbitMQ is an open-source message broker that enables applications to communicate asynchronously. It implements the Advanced Message Queuing Protocol (AMQP) and is widely used for distributed systems.

---

## Installing RabbitMQ

### Linux (Ubuntu/Debian)
```sh
sudo apt update
sudo apt install rabbitmq-server
sudo systemctl enable rabbitmq-server
sudo systemctl start rabbitmq-server
```

### macOS (Using Homebrew)
```sh
brew install rabbitmq
brew services start rabbitmq
```

### Windows (Using Chocolatey)
```sh
choco install rabbitmq
rabbitmq-server start
```

---

## Enabling RabbitMQ Management Plugin
```sh
rabbitmq-plugins enable rabbitmq_management
```

Access the dashboard at: [http://localhost:15672](http://localhost:15672)

Default login credentials:
- Username: `guest`
- Password: `guest`

---

## Using RabbitMQ with Node.js (ES6)

### Install Dependencies
```sh
npm install amqplib
```

### Producer (Sending Messages)
```js
import amqp from 'amqplib';

const sendMessage = async () => {
    const connection = await amqp.connect('amqp://localhost');
    const channel = await connection.createChannel();
    const queue = 'task_queue';
    const message = 'Hello, RabbitMQ!';

    await channel.assertQueue(queue, { durable: true });
    channel.sendToQueue(queue, Buffer.from(message));

    console.log(`Sent: ${message}`);
    await channel.close();
    await connection.close();
};

sendMessage();
```

### Consumer (Receiving Messages)
```js
import amqp from 'amqplib';

const receiveMessage = async () => {
    const connection = await amqp.connect('amqp://localhost');
    const channel = await connection.createChannel();
    const queue = 'task_queue';

    await channel.assertQueue(queue, { durable: true });
    console.log(`Waiting for messages in ${queue}`);

    channel.consume(queue, (msg) => {
        if (msg !== null) {
            console.log(`Received: ${msg.content.toString()}`);
            channel.ack(msg);
        }
    });
};

receiveMessage();
```

---

## RabbitMQ Commands

### List Queues
```sh
rabbitmqctl list_queues
```

### Check Server Status
```sh
rabbitmqctl status
```

### Restart RabbitMQ
```sh
sudo systemctl restart rabbitmq-server
```

---

## Conclusion
RabbitMQ is a powerful message broker that helps in building scalable, event-driven architectures. Using ES6 syntax with `amqplib`, we can implement efficient producer-consumer patterns in Node.js.


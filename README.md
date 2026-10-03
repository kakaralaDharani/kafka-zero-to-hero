# Kafka Zero to Hero — Hands-On Demo

A hands-on Apache Kafka project demonstrating event streaming using **Kafka, Python, Docker Compose, and Kafka UI**.

## 🛠️ Technologies

* Apache Kafka 3.8.0
* Python
* Docker & Docker Compose
* Kafka UI
* Bash/Shell scripting
* Git & GitHub

## 🏗️ What I Implemented

* Set up a single-node Kafka cluster using **KRaft mode**.
* Used Docker Compose to run Kafka and Kafka UI.
* Automated Kafka startup using a **shell script**.
* Created Kafka topics programmatically using Python.
* Implemented a Python Kafka producer for publishing events.
* Implemented a Python Kafka consumer for consuming events.
* Worked with:

  * Topics
  * Partitions
  * Consumer Groups
  * Offsets
  * `earliest` / `latest` offset behavior
* Used Kafka UI to monitor topics and messages.
* Added Kafka broker health checks.
* Configured separate internal and external Kafka listeners.

## 🔄 Data Flow

```text
Python Producer
      ↓
Kafka Topic
      ↓
Partitions
      ↓
Python Consumer
      ↓
Processed Event
```

## 🚀 Setup

### 1. Clone the repository

```bash
git clone https://github.com/kakaralaDharani/kafka-zero-to-hero.git
cd kafka-zero-to-hero
```

### 2. Create Python virtual environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install the project

```bash
pip install -e .
```

### 4.0 Start Kafka

Kafka and Kafka UI are started through the project's shell script:

```bash
./scripts/start-kafka.sh
```

The script starts Docker Compose and verifies the running containers.

### 4.1 Access Kafka
Kafka broker: localhost:9092
Kafka UI: http://localhost:8080
Python producer and consumer connected to Kafka using localhost:9092.
Kafka UI was used to view topics, partitions, messages, and consumer activity.

### 4.2 Check Kafka Containers
docker compose ps

This was used to verify that Kafka and Kafka UI were running.

### 5. Create the topic

```bash
python examples/live_topic_setup.py --topic order-events-live
```

### 6. Start the producer

```bash
python examples/live_producer.py --topic order-events-live --interval 1
```

### 7. Start the consumer

```bash
python examples/live_consumer.py --topic order-events-live
```

Use `--from-beginning` when you want the consumer to read existing messages from the beginning.

### 8.Stop Kafka
Kafka was stopped using the project's shell script:

```bash
./scripts/stop-kafka.sh
```
The script stops the Docker Compose services cleanly.

## 🖥️ Four-Terminal Workflow

| Terminal | Activity                           |
| -------- | ---------------------------------- |
| 1        | Start Kafka using the shell script |
| 2        | Create Kafka topic                 |
| 3        | Run producer                       |
| 4        | Run consumer                       |

## 🔧 Issues Faced & Fixes

### Python project not found

**Issue:** `pip install -e .` failed because it was executed outside the project directory.

**Fix:** Changed to the project root and ran:

```bash
pip install -e .
```

### Python module not found

**Issue:** `ModuleNotFoundError: No module named 'kafka_zero_to_hero'`

**Fix:** Installed the project in editable mode from the project root:

```bash
pip install -e .
```

### Docker daemon not running

**Issue:** Kafka containers could not start because Docker was not running.

**Fix:** Started Docker Desktop and verified Docker with:

```bash
docker info
```



## 🎯 Key Learning

This project gave me hands-on experience with **Kafka event streaming, Docker-based infrastructure, Python Kafka clients, consumer groups, partitions, offsets, health checks, and container networking**.

## 🎥 Demo Videos

### Kafka Demo

Complete hands-on Kafka demo covering Kafka setup, topic creation, producer, consumer, Kafka UI, and stopping Kafka.

[Watch Kafka Demo](docs/videos/kafka-demo.mp4)

### Git & GitHub Demo

Demonstration of the Git workflow used to add, commit, and push this project to GitHub.

[Watch Git & GitHub Demo](docs/videos/git-demo.mp4)


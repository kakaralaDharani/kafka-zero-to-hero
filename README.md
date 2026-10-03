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
git clone <your-repository-url>
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

### 4. Start Kafka

Kafka and Kafka UI are started through the project's shell script:

```bash
./<your-startup-script>
```

The script starts Docker Compose and verifies the running containers.

### 5. Create the topic

```bash
python examples/live_topic_setup.py --topic order-events-live
```

### 6. Start the producer

Run the project's producer command/script to publish order events.

### 7. Start the consumer

```bash
python examples/live_consumer.py --topic order-events-live
```

Use `--from-beginning` when you want the consumer to read existing messages from the beginning.

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

## 📸 Screenshots

Add screenshots showing:

1. Kafka containers running
2. Kafka UI
3. Topic creation
4. Producer messages
5. Consumer output
6. Kafka messages/partitions in Kafka UI

## 🎯 Key Learning

This project gave me hands-on experience with **Kafka event streaming, Docker-based infrastructure, Python Kafka clients, consumer groups, partitions, offsets, health checks, and container networking**.

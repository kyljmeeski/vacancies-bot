**Vacancies Bot** is a Telegram bot designed to notify subscribers of new job vacancies using a microservices architecture. The application is composed of several components, each running in a Docker container and communicating through RabbitMQ message broker.

## Components

1. [Scheduler](https://github.com/kyljmeeski/vacancies-bot-scheduler) - Responsible for scheduling job parsing tasks to fetch new vacancies from devkg.com.
2. [Importer](https://github.com/kyljmeeski/vacancies-bot-importer) - Parses job listings from devkg.com and forwards them to the Saver component for saving.
3. [Saver](https://github.com/kyljmeeski/vacancies-bot-saver) - Receives parsed vacancies from the Importer, filters out new vacancies, and saves them into MongoDB.
4. [Notifier](https://github.com/kyljmeeski/vacancies-bot-notifier) - Retrieves newly saved vacancies from MongoDB, matches them with subscribed users from PostgreSQL, and sends notifications to the Telegram bot.
5. [Telegram Bot](https://github.com/kyljmeeski/vacancies-bot-telegram-bot) - Manages user registration and sends notifications of new vacancies to subscribed users.

## Technology Stack
1. MongoDB - Used to store job vacancies due to their varied structures.
2. PostgreSQL - Stores user data and subscription information.
3. RabbitMQ - Message broker facilitating communication between application components.

This command starts all components in detached mode for seamless integration.

## Getting Started

1. Clone this repository:
```shell
git clone https://github.com/kyljmeeski/vacancies-bot.git
cd vacancies-bot
```
2. Modify environment variables in the docker-compose.yml file as needed.
3. Deploy the application using Docker Compose:
```shell
docker-compose up -d
```


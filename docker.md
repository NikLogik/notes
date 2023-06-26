---
id: hkew03pdh672q5rxmjd3t7v
title: Docker
desc: ""
updated: 1684828059929
created: 1684331173747
---

## Dockerfile

Dockerfile подходит для создания образа из которого будет вдальнейшем запускаться контейнер

Пример минимально достаточно Dockerfile для сборки образа Java приложения

```Dockerfile
FROM openjdk:8-jdk-alpine
COPY target/docker-message-server-1.0.0.jar message-server-1.0.0.jar
ENTRYPOINT ["java","-jar","/backend-1.0.0.jar"]
```

Команды Docker:

- FROM — задаёт базовый (родительский) образ.
- LABEL — описывает метаданные. Например — сведения о том, кто создал и поддерживает образ.
- ENV — устанавливает постоянные переменные среды.
- RUN — выполняет команду и создаёт слой образа. Используется для установки в контейнер пакетов.
- COPY — копирует в контейнер файлы и папки.
- ADD — копирует файлы и папки в контейнер, может распаковывать локальные .tar-файлы.
- CMD — описывает команду с аргументами, которую нужно выполнить когда контейнер будет запущен. Аргументы могут быть переопределены при запуске контейнера. В файле может присутствовать лишь одна инструкция CMD.
- WORKDIR — задаёт рабочую директорию для следующей инструкции.
- ARG — задаёт переменные для передачи Docker во время сборки образа.
- ENTRYPOINT — предоставляет команду с аргументами для вызова во время выполнения контейнера. Аргументы не переопределяются.
- EXPOSE — указывает на необходимость открыть порт.
- VOLUME — создаёт точку монтирования для работы с постоянным хранилищем.

Команды **RUN, COPY, ADD** создают новые слои, в том время как другие инструкции являются промежуточными и не влияют на размер создаваемого Image.

## Docker compose

Позволяет объединять в себе конфигурацию сразу для нескольких сервисов.

Также через запуск docker-compose можно регулировать масштабирование (репликацию) отдельных сервисов.

```sh
$> docker-compose --file docker-compose-scale.yml up -d --build --scale postgres=1 backend=2
```

Пример файла docker-compose.yml

```yml
version: "3.8"
services:
  postgres:
    image: postgres:14.5-alpine
    container_name: "postgres"
    healthcheck:
      test:
        [
          "CMD-SHELL",
          "pg_isready -U postgres && psql -U postgres -lqt | cut -d \\| -f 1 | grep -qw omnichat && psql -U postgres -lqt | cut -d \\| -f 1 | grep -qw webchat",
        ]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 10s
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_HOST_AUTH_METHOD=trust
    volumes:
      - ./init-migrations:/docker-entrypoint-initdb.d/
      - "db-data:/var/lib/postgresql/data"
    networks:
      backend: { aliases: [postgres.backend] }

  rabbitmq:
    image: 2chat/rabbitmq:1.2
    restart: on-failure
    healthcheck:
      test: ["CMD", "nc", "-z", "localhost", "5672"]
      interval: 10s
      timeout: 15s
      retries: 3
    environment:
      - "RABBITMQ_DEFAULT_USER=admin"
      - "RABBITMQ_DEFAULT_PASS=x3%u*n_WvzE"
    networks:
      backend: { aliases: [rabbitmq.backend] }

  app:
    build:
      context: ./
      dockerfile: Dockerfile
    command: java -jar ./gamification.jar
    environment:
      - SPRING_DATASOURCE_URL=jdbc:postgresql://postgres.backend:5432/gamification_db
      - SPRING_DATASOURCE_DRIVER=org.postgresql.Driver
      - SPRING_DATASOURCE_USERNAME=postgres
      - SPRING_DATASOURCE_PASSWORD=postgres
      - POSTGRES_HOST_AUTH_METHOD=trust
      - SERVER_PORT=8095
      - RABBIT_USER=admin
      - RABBIT_PASSWORD=x3%u*n_WvzE
      - RABBIT_HOST=rabbitmq.backend
      - NOTIFY_URL=http://localhost:9009
    ports:
      - 8095:8095
    depends_on:
      - postgres
      - rabbitmq
    networks:
      backend: { aliases: [app.backend] }
networks:
  backend:
    driver: bridge
volumes:
  db-data:
```

## Разница с Virtual Machine

![Docker-VS-VirtualMachine](assets/images/Docker-vs-VM.png)

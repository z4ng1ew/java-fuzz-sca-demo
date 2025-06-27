> **`JavaFuzzTrack: SCA & Fuzz Testing Integration`**

## 📜 Краткое описание на 280 символов

### 🇷🇺 Русский:

Pet-проект, объединяющий фаззинг-функцию на Java, систему анализа зависимостей Dependency-Track (SCA) и Docker-инфраструктуру. Используется PostgreSQL, Maven и OWASP BOM для анализа. Полностью совместимо с DevSecOps подходом.

### 🇺🇸 English:

A pet project combining Java fuzz testing, SCA analysis via Dependency-Track, and Docker infrastructure. Uses PostgreSQL, Maven, and OWASP BOM generation. Perfect for DevSecOps enthusiasts to explore dependency risk and dynamic testing in one setup.

---

## 📘 README.md (весь файл)

```markdown
# 🔒 JavaFuzzTrack: SCA + Fuzz Testing + Docker

Этот pet-проект демонстрирует сочетание:
- Java-приложения с функцией, уязвимой к фаззингу
- Анализа зависимостей с помощью [Dependency-Track](https://dependencytrack.org/)
- Docker-инфраструктуры для быстрого развёртывания
- Импорта BOM-файла (Bill of Materials) в систему безопасности

## ⚙️ Стек технологий

- ☕ Java 17 (Maven)
- 🐘 PostgreSQL 15 (alpine)
- 🛠️ Dependency-Track (API + Frontend)
- 🐳 Docker Compose
- 🧪 Fuzz-тесты (JUnit + случайные входные данные)
- 📦 CycloneDX (OWASP BOM)

## 📂 Структура проекта

```

.
├── demo-app/               # Java-приложение
│   ├── src/                # Исходный код и тесты
│   ├── pom.xml             # Maven зависимости + генерация BOM
│   └── target/             # Скомпилированные артефакты (в т.ч. bom.xml/json)
├── docker-compose.yml      # Инфраструктура
└── README.md

````

## 🔍 Цель

Объединить фаззинг и SCA-анализ в одном окружении:

- 📈 Проверить, как фаззинг может выявить баги в пользовательских функциях
- 🛡️ Проверить зависимости на наличие уязвимостей через Dependency-Track
- 🔄 Автоматизировать импорт BOM-файла из Maven в Dependency-Track

## 🚀 Быстрый старт

### 📦 1. Сборка Java-проекта и BOM

```bash
cd demo-app
mvn clean package org.cyclonedx:cyclonedx-maven-plugin:makeAggregateBom
````

Это сгенерирует `bom.xml` и `bom.json` в `target/`.

### 🐳 2. Запуск Dependency-Track в Docker

```bash
cd ..
docker-compose up -d
```

* API-сервер: [http://localhost:8080](http://localhost:8080)
* Frontend UI: [http://localhost:8081](http://localhost:8081)

### 🧪 3. Добавление BOM в систему

После запуска Dependency-Track, зайди в веб-интерфейс и:

* Создай проект
* Загрузи `bom.xml` в проект

### 🤖 4. Запуск fuzz-тестов

Пример теста с JUnit + рандомным входом находится в `AppTest.java`.

```bash
mvn test
```

Можно заменить тест на fuzz-фреймворки типа [jazzer](https://github.com/CodeIntelligenceTesting/jazzer), если нужен coverage-guided fuzzing.

---

## 🧠 Почему это полезно?

✔ Учишься анализировать зависимости через CycloneDX и D-Track
✔ Практикуешь фаззинг, усиливая безопасную разработку
✔ Показываешь рекрутёру знание DevSecOps-инфраструктуры

---

## 🛠 Переменные подключения

```env
POSTGRES_USER=dependencytrack
POSTGRES_PASSWORD=dependencytrack
POSTGRES_DB=dependencytrack
```

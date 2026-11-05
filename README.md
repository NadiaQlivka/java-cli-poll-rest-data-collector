# REST API Data Collector

Консольное приложение на Java для автоматизированного сбора данных из внешних REST API с сохранением результатов в JSON или CSV.

## Технологии

Java 17, Java HttpClient, Maven, Gson, Apache Commons CSV, JUnit 5, Mockito, JaCoCo.

## Возможности

- Сбор данных из **RandomUser**, **EmojiHub** и **Agent Nexus**.
- Параллельный и периодический опрос API с настраиваемым числом потоков и интервалом запросов.
- Потокобезопасная запись результатов в JSON/CSV, поддержка добавления данных в существующий файл.
- Интерактивный режим и автоматический запуск с параметрами командной строки.
- Модульные тесты с Mockito, контроль покрытия кода через JaCoCo (порог — 70% строк).

## Запуск

**Требования:** Java 17+, Maven и интернет-соединение.

Интерактивный режим:

```bash
mvn compile exec:java -Dexec.mainClass="com.voronina.course.Main"
```

Автоматический сбор (все API, по 10 объектов на источник, 2 потока):

```bash
mvn compile exec:java -Dexec.mainClass="com.voronina.course.Main" -Dexec.args="--auto --format=json --output=result --count=10 --threads=2 --interval=1"
```

Для сохранения в CSV замените `--format=json` на `--format=csv`. Флаг `--append` добавляет новые данные к существующим.

## Тестирование

```bash
mvn test
mvn verify
```

Отчёт JaCoCo: `target/site/jacoco/index.html`.

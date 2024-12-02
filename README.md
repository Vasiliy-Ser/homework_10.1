# Домашнее задание к занятию 3 "`«Базы данных, их типы»`" - `Падеев Василий`


   
### Задание 1

![task1](https://github.com/Vasiliy-Ser/homework_10.1/blob/6a707e50a0b48d7102fa40e0cc454dd6a931fb80/file/task10.1.1.png)

Решения...
1.1 Для крупной строительной компании оптимальной будет комбинация PostgreSQL или Microsoft SQL Server для оперативной работы с данными и Snowflake или ClickHouse для аналитической обработки. 
Это обеспечит как надежное управление финансовыми данными, так и возможность масштабируемой аналитики.
1.1* AWS Key Management Service (KMS): Предоставляет API для выполнения криптографических операций, включая хеширование.
Google Cloud Key Management: Быстрые операции хеширования через облако.
Для ускорения хеширования можно использовать специализированные библиотеки, такие как OpenSSL или Libsodium, а также оптимизировать алгоритмы, переключившись на менее ресурсоемкие, если безопасность не является критической задачей.
1.2 Лендинги: MongoDB или Redis (для быстрой записи данных форм).
CRM: Основной СУБД: PostgreSQL для хранения ключевых данных. Дополнительно: MongoDB для хранения гибких атрибутов клиентов и сделок.
1.2* Можно закрыть задачу одной СУБД, и оптимальным выбором будет PostgreSQL. Эта СУБД обеспечивает:
- Высокую производительность для лендингов (через JSONB).
- Четкую структуру и транзакционность для CRM (через реляционные таблицы).
- Возможности масштабирования и аналитики. 
1.3 Для такой задачи оптимальным выбором будет реляционная СУБД с возможностью работы с документами и метаданными.
Для базы отдела контроля качества наиболее подходящим вариантом будет PostgreSQL как универсальная, простая и мощная СУБД, обеспечивающая:
- Четкую структуру.
- Поддержку полуструктурированных данных через JSON.
- Встроенный полнотекстовый поиск для быстрого доступа к информации.
Если акцент на документах, можно использовать MongoDB или дополнить PostgreSQL системой поиска вроде Elasticsearch.
1.3* Да, для описанной задачи можно использовать одну из уже предложенных СУБД, так как все они достаточно универсальны и масштабируемы. Это позволит избежать необходимости внедрения новой системы и упростит интеграцию. 
PostgreSQL, рекомендованная ранее для задач CRM и лендингов, прекрасно подойдет и для базы данных отдела контроля качества. Это связано с ее гибкостью, поддержкой реляционных данных и JSON-структур, а также встроенным полнотекстовым поиском.
Если в задаче лендингов использовалась MongoDB, ее также можно адаптировать для отдела контроля качества, особенно если корпоративные нормы представлены в виде документов, разнообразных форматов, видео и т. д.
1.4 Для задач департамента логистики, включающих формирование маршрутов доставки материалов и распределение курьеров, важными являются:
- Эффективная работа с графами – маршруты доставки и связи между точками можно представить в виде графов.
- Высокая производительность – нужно быстро рассчитывать оптимальные маршруты и распределять ресурсы.
- Гибкость – система должна масштабироваться и работать с динамическими данными (например, изменениями маршрутов, новых точек доставки).

Если требуется сосредоточиться на быстром и удобном решении графовых задач, лучше всего выбрать Neo4j или ArangoDB. Если компания уже использует PostgreSQL, то добавление pgRouting и PostGIS будет оптимальным и менее затратным решением.


`При необходимости прикрепитe сюда скриншоты



---

### Задание 2

![task2](https://github.com/Vasiliy-Ser/homework_10.1/blob/6a707e50a0b48d7102fa40e0cc454dd6a931fb80/file/task10.1.2.png)


Решения...

2.1 
1. Инициация платежа пользователем
Пользователь выбирает способ пополнения баланса (например, через терминал, мобильное приложение, интернет-банкинг или кассу).
Указывает номер телефона, сумму пополнения и подтверждает платеж.
2. Передача данных в платежную систему
Система, через которую пользователь инициировал пополнение, передает данные о номере телефона, сумме и идентификаторе платежа в платежный шлюз или процессинговый центр.
Проверяется корректность введенных данных (например, правильность формата номера телефона).
3. Авторизация платежа
Платежная система инициирует запрос в банк или иную финансовую организацию для списания указанной суммы со счета пользователя.
Происходит проверка доступности средств на счету пользователя.
При успешной авторизации средства резервируются или списываются.
4. Подтверждение транзакции
После успешного списания средств платежная система возвращает подтверждение в исходную систему (например, приложение или терминал).
Если списание средств не удалось (например, недостаточно денег на счету), пользователю отправляется уведомление об ошибке.
5. Перевод средств на счет оператора связи
Платежная система направляет запрос оператору связи о пополнении указанного телефонного номера на указанную сумму.
Оператор связи подтверждает зачисление средств.
6. Уведомление о завершении транзакции
Пользователь получает уведомление (например, SMS, push-уведомление или электронное письмо) о зачислении средств на счет телефона.
Баланс телефона обновляется в реальном времени.

2.2
1. Настройка автоплатежа
Пользователь заранее активирует автоплатёж в банковском приложении, у оператора связи или в платежной системе.
Указываются условия автоплатежа:
Номер телефона для пополнения.
Сумма пополнения.
Порог баланса, при котором срабатывает автоплатёж.
Источник списания (счёт, карта).
2. Мониторинг баланса оператора связи
Система (например, у оператора связи) отслеживает баланс телефона.
Когда баланс падает ниже заданного порога, инициируется автоплатёж.
3. Инициация автоплатежа
Система отправляет запрос в платежный шлюз или банк на автоматическое списание средств.
Передаются данные: номер телефона, сумма, реквизиты источника средств.
4. Авторизация списания средств
Банк или финансовая система проверяет параметры автоплатежа:
Достаточность средств на счёте/карте пользователя.
Валидность настроек автоплатежа.
Если все условия выполнены, средства резервируются или списываются.
5. Пополнение счёта телефона
Средства перечисляются оператору связи.
Оператор обновляет баланс телефона пользователя.
6. Уведомление пользователя
Пользователь получает уведомление о выполнении автоплатежа (SMS, push-уведомление, email).
Уведомление включает сумму, дату, источник списания и текущий баланс телефона.

`При необходимости прикрепитe сюда скриншоты


---

### Задание 3

![task3](https://github.com/Vasiliy-Ser/homework_10.1/blob/6a707e50a0b48d7102fa40e0cc454dd6a931fb80/file/task10.1.3.png)



Решения...

3.1 пять ключевых преимуществ SQL-систем
1. Строгая структура данных и гарантии целостности
SQL-системы используют схемы, которые определяют строгую структуру данных. Это обеспечивает:
- Ясность данных: каждая таблица имеет четко определенные столбцы с типами данных.
- Целостность данных: механизмы, такие как внешние ключи и ограничения, гарантируют, что данные остаются согласованными.

2. Поддержка сложных запросов
SQL предоставляет мощный и стандартизированный язык запросов, который позволяет:
- Выполнять сложные операции, включая соединения (JOIN), вложенные запросы и агрегации.
- Анализировать большие объемы данных с использованием встроенных функций.

3. Соответствие ACID-принципам
Реляционные базы данных поддерживают транзакции с соблюдением ACID-принципов (атомарность, согласованность, изолированность, долговечность). Это гарантирует:
- Надежность операций (даже при сбоях).
- Отсутствие противоречий в данных, что особенно важно для финансовых и критически важных приложений.

4. Стандарты и совместимость
SQL — это хорошо стандартизированный язык, поддерживаемый большинством реляционных баз данных. Это дает:
- Возможность легко переключаться между разными системами (например, MySQL, PostgreSQL, SQL Server).
- Упрощение интеграции с различными инструментами и технологиями.

5. Широкая поддержка аналитических инструментов и экосистемы
Большинство бизнес-аналитических инструментов и фреймворков, таких как Tableau, Power BI, Apache Spark, ориентированы на SQL. Это обеспечивает:
- Простую интеграцию для отчетности и анализа.
- Быстрое внедрение в существующие бизнес-процессы.

3.2 Преимущества NewSQL перед SQL и NoSQL:

1. Баланс между производительностью и функциональностью
NewSQL предлагает высокую производительность и масштабируемость, сопоставимую с NoSQL, без отказа от реляционной модели и ACID-принципов.

2. Интеграция с современными технологиями
Большинство NewSQL систем разработаны с учетом интеграции с облачными средами, микросервисной архитектурой и потребностями потоковой обработки данных.

3. Гибкость и адаптивность
NewSQL объединяет лучшие аспекты SQL и NoSQL, предоставляя универсальную платформу для широкого спектра задач: от OLTP (операционная обработка транзакций) до OLAP (аналитическая обработка). 


`При необходимости прикрепитe сюда скриншоты



### Задание 4

![task4](https://github.com/Vasiliy-Ser/homework_10.1/blob/6a707e50a0b48d7102fa40e0cc454dd6a931fb80/file/task10.1.4.png)


Решения...
4.1 Если преобладает аналитика (OLAP): Используем Spark + Druid или Spark + Hive для обработки и ClickHouse для аналитики.
Если задачи реального времени (Stream Processing): Kafka + Flink для стриминга данных.
Если нужны сложные транзакции (OLTP): CockroachDB или YugabyteDB с поддержкой горизонтального масштабирования.
Для комбинации задач:
Apache Spark как универсальный инструмент.
HDFS или объектное хранилище (S3) для хранения данных.
Совместимость с NoSQL или SQL базами для гибкости.

`При необходимости прикрепитe сюда скриншоты




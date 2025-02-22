Сервис Cloud Queues от VK Cloud совместим с Amazon SQS API. Для работы с сервисом можно пользоваться инструментом [AWS CLI](https://aws.amazon.com/ru/cli/), чтобы выполнять команды с использованием оболочки командной строки.

С помощью AWS CLI, вы можете выполнять следующие действия:

- Удаление очередей сообщений;
- Отправка, просмотр и удаление сообщений в очередях;
- Редактирование атрибутов сообщений и очередей;
- Изменение прав пользователей, имеющих доступ к редактированию очередей.

На этой странице вы узнаете:

- Как начать работу с Cloud Queues в AWS CLI.
- Как формировать команды в AWS CLI.
- Примеры команд.

Перед началом работы с сервисом Cloud Queues, ознакомьтесь с ограничениями сервиса в разделе [Ограничения](../../limitations/).

## Подготовительные шаги

1. [Установите AWS CLI](../../../tools-for-using-services/aws-cli/).
1. Создайте ключи доступа для получения доступа к AWS CLI. Ключи доступа состоят из идентификатора ключа доступа и секретного ключа доступа, которые используются для подписи программных запросов, отправляемых в VK Cloud. Ключи доступа можно создать в панели VK Cloud в меню **Ключи доступа** сервиса **Очереди сообщений**.

Единственный раз, когда можно просмотреть или загрузить секретный ключ доступа, – когда ключи создаются. Восстановить их позже будет невозможно. Однако создать новые ключи доступа можно в любое время.

## Настройка CLI

Самый быстрый способ настроить установку AWS CLI – с помощью команды

```
aws configure
```

При вводе этой команды интерфейс командной строки AWS запрашивает четыре части информации:

- **Идентификатор ключа доступа** – используются полученные данные идентификатора ключа при добавлении аккаунта;
- **Секретный ключ доступа** – используются полученные данные секретного ключа при добавлении аккаунта;
- **AWS регион** – регион размещения сервиса Cloud Storage, по умолчанию это `ru-msk`;
- **Выходной формат** – определяет как отформатировать вывод используемой команды. Если не будет указан выходной формат, будет использовать json по умолчанию. Доступные варианты: json, yaml, текст и таблица.

Пример команды настройки AWS CLI выглядит вот так:

```
aws configure
AWS Access Key ID [****************rtP7]: <идентификатор ключа доступа>
AWS Secret Access Key [****************F2OP]: <секретный ключ доступа>
Default region name [eu-west-1]: ru-msk
Default output format [None]:
```

Интерфейс командной строки AWS хранит эту информацию в профиле (наборе настроек), названном **default** в файле **credentials**. По умолчанию информация в этом профиле используется, когда запускается команда интерфейса командной строки AWS, в которой явно не указывается используемый профиль.

## Использование команд AWS CLI с Cloud Queues

В AWS CLI используется составной синтаксис для формирования команд:

```
aws sqs --endpoint-url https://sqs.mcs.mail.ru <имя команды> [опции и параметры]
```

- `aws sqs` – вызов сервиса Cloud Queues;

- `<имя команды>` – название выполняемой операции;

- `--endpoint-url https://sqs.mcs.mail.ru` – для всех команд необходимо указывать параметр `--endpoint-url` со значением `https://sqs.mcs.mail.ru` для нормальной работы сервиса;

- `[опции и параметры]` – дополнительные параметры выполняемой операции.

Вы можете использовать команду `aws sqs help` для вызова справки по доступным командам.

Полный список всех команд, доступных в AWS CLI для работы с Cloud Queues также можно увидеть на [сайте Amazon](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/sqs/index.html#available-commands).

## Примеры команд

### Создание сообщения в очереди

Следующая команда создаст сообщение в очереди сообщений `test-queue`:

```
aws sqs send-message --endpoint-url https://sqs.mcs.mail.ru --queue-url sqs.mcs.mail.ru/mcsprojectid/test-queue --message-body "test message body"
```

### Получение сообщений в очереди

Следующая команда вернет текст сообщений в очереди `test-queue`:

```
aws sqs receive-message --endpoint-url https://sqs.mcs.mail.ru --queue-url sqs.mcs.mail.ru/mcsprojectid/test-queue
```

### Удаление сообщения в очереди

Следующая команда удалит сообщение c параметром `Receipt-handle AQEB6nR4...HzlvZQ==` в очереди `test-queue`:

```
aws sqs delete-message --endpoint-url https://sqs.mcs.mail.ru --queue-url sqs.mcs.mail.ru/mcsprojectid/test-queue --receipt-handle AQEB6nR4...HzlvZQ==
```

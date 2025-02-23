Сервис Cloud Networks позволяет работать с несколькими типами сетей.

## Стандартная сеть

Стандартная сеть предоставляет доступ к подсетям с приватными IP-адресами и существует в рамках одного проекта.

[Управлять](../../operations/) стандартной сетью, ее подсетями и портами можно через личный кабинет, OpenStack CLI или Terraform.

## Общая сеть

Общая сеть (shared network) тоже предоставляет доступ к подсетям с приватными IP-адресами, но существует в рамках нескольких проектов. Подключить такую сеть могут пользователи, чья облачная инфраструктура распределена между двумя и более проектами.

Сначала в проекте-владельце (owner) создается стандартная сеть. По [запросу в техническую поддержку](/ru/contacts) такую сеть можно сделать общей и предоставить к ней доступ из одного или нескольких зависимых проектов.

В проекте-владельце [управлять](../../operations/) общей сетью, ее подсетями и портами можно через личный кабинет, OpenStack CLI или Terraform. Удалить общую сеть можно только через [запрос в техническую поддержку](/ru/contacts).

В зависимых проектах общая сеть доступна для просмотра, например, из личного кабинета, но разрешено только [управлять портами](../../operations/manage-ports) такой сети с помощью OpenStack CLI. Также в зависимых проектах нельзя подключать к общей сети инстансы БД и кластеры Kubernetes.

## Внешняя сеть

Внешняя сеть (`ext-net`) предоставляет доступ к подсетям с публичными IP-адресами. Такая сеть существует во всех проектах и используется для предоставления доступа из интернета к сервисам. Подробнее в разделе [Сетевая адресация и доступ в интернет](../ips-and-inet).

Изменять или удалять подсети такой сети нельзя. Доступны следующие операции из личного кабинета, OpenStack CLI или Terraform:

- назначение этой сети виртуальной машине;
- назначение этой сети в качестве внешней для маршрутизатора.

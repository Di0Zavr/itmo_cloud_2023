# Аналитическая работа 2

## Цель работы

Знакомство с облачными сервисами.
Понимание уровней абстракции над инфраструктурой в облаке.
Формирование понимания типов потребления сервисов в сервисной-модели.
Сопоставление сервисов между разными провайдерами.
Оценка возможностей миграции на отечественные сервисы.

### Ход работы

Мы выделили сервисы, которые нам встретились.
Ниже будет представлено их описание.

### Биллинг


### Список сервисов и их описание

1. ***Azure Data Factory***:
   - Назначение: ETL-сервис (Extract, Transform, Load) для интеграции и оркестровки данных.
   - Функциональные возможности: Всасывает, преобразует и перемещает данные из различных источников в такие места назначения, как Azure SQL Database, Azure Blob Storage и т. д.

2. ***Azure Database for PostgreSQL***:
   - Назначение: управляемая служба базы данных PostgreSQL.
   - Функциональные возможности: Предоставляет полностью управляемую, масштабируемую и безопасную базу данных PostgreSQL в Azure.

3. ***Azure Databricks***:
   - Назначение: унифицированная аналитическая платформа для больших данных и машинного обучения.
   - Функциональные возможности: Рабочее пространство для совместной работы над задачами инженерии данных, науки о данных и машинного обучения.

4. ***Redis Cache***:
   - Назначение: In-memory хранилище данных для кэширования.
   - Функциональные возможности: Повышает производительность приложений за счет хранения часто используемых данных в памяти.

5. ***Content Delivery Network (CDN)***:
   - Назначение: Распространяет контент по всему миру с низкой задержкой.
   - Функциональность: Кэширование и доставка статического и динамического контента (изображений, видео и т. д.) с пограничных серверов, расположенных вблизи конечных пользователей.

6. ***Content Delivery Network***:
   - Назначение: Легкое, бессерверное развертывание контейнеров.
   - Функциональность: Запуск контейнеров без управления базовой инфраструктурой.

7. ***Machine Learning Studio***:
   - Назначение: Визуальный интерфейс для построения, развертывания и управления моделями машинного обучения.
   - Функциональные возможности: Упрощает разработку и развертывание ML-моделей.
8. ***Bandwith***:
   - Назначение: измеряет скорость передачи данных.
   - Функциональные возможности: Определяет, сколько данных может быть передано по сетевому соединению.

9. ***VPN-gateway***:
   - Назначение: безопасное подключение локальных сетей к Azure.
   - Функциональные возможности: Создает зашифрованные коммуникационные туннели для удаленного доступа или соединения между объектами.

10. ***Traffic Manager***:
    - Назначение: распределяет входящий трафик между несколькими конечными точками.
    - Функциональные возможности: Повышает доступность, отзывчивость и масштабируемость приложений.

11. ***Azure Firewall***:
    - Назначение: управляемая служба сетевой безопасности.
    - Функциональные возможности: Фильтрует и контролирует сетевой трафик между ресурсами Azure и внешними сетями.

12. ***Notification Hub***:
    - Назначение: служба Push-уведомлений.
    - Функциональные возможности: Отправка целевых уведомлений на мобильные устройства, веб-приложения и т. д.

13. ***Power BI***:
    - Назначение: инструмент бизнес-аналитики и визуализации данных.
    - Функциональные возможности: Создание интерактивных отчетов и информационных панелей на основе различных источников данных.

14. ***Power BI Embedded***:
    - Назначение: Встраивание отчетов Power BI в пользовательские приложения.
    - Функциональность: Позволяет пользователям просматривать отчеты и взаимодействовать с ними в других приложениях.

### Сопоставление сервисов между разными провайдерами

В таблице ниже представлено сопоставление сервисов между разными провайдерами.

| Meter Category                | Meter Sub-Category  | Meter Name                   | Consumed Service                  | [AdditionalInfo] | Аналоговые сервисы                                          |
| ----------------------------- | ------------------- | ---------------------------- | --------------------------------- | ---------------- |-------------------------------------------------------------|
| Azure Data Factory            | v2                  | Data Movement Self Hosted IR | Microsoft.DataFactory             |                  | Yandex Data Transfer                                        |
| Azure Data Factory            | v2                  | Orchestration Self Hosted IR | Microsoft.DataFactory             |                  | \-                                                          |
| Azure Data Factory            | v2                  | %                            | Microsoft.DataFactory             |                  | \-                                                          |
| Azure Data Factory            | v2                  | Data Movement Cloud IR       | Microsoft.DataFactory             |                  | Yandex Data Transfer                                        |
| Azure Data Factory            | v2                  | Orchestration Cloud IR       | Microsoft.DataFactory             |                  | \-                                                          |
| Azure Data Factory            | v2                  | SSIS STD D4 v2               | Microsoft.DataFactory             |                  | \-                                                          |
| Azure Database for PostgreSQL |                     |                              | Microsoft.DBforMyQL               |                  | Yandex Managed Service for PostgreSQL                       |
| Azure Database for PostgreSQL |                     |                              | Microsoft.DBforPostgreSQL         |                  | Yandex Managed Service for PostgreSQL                       |
| Azure Databricks              |                     | %Data Analytics%             | Microsoft.Databricks              |                  | Yandex DataSphere                                           |
| Azure Databricks              |                     | %Data Engineering%           | Microsoft.Databricks              |                  | Yandex DataSphere                                           |
| Cache                         | Azure Redis Cache   |                              | Microsoft.Cache                   |                  | Yandex Managed Service for Redis                            |
| Redis Cache                   |                     | C%                           | Microsoft.Cache                   |                  | Yandex Managed Service for Redis                            |
| Redis Cache                   |                     | ___C%                        | Microsoft.Cache                   |                  | Yandex Managed Service for Redis                            |
| CDN                           | CDN                 | Standard CDN Data Transfer%  | Microsoft.Cdn                     |                  | Yandex Data Transfer                                        |
| Content Delivery Network      | Azure CDN%          | %Data Transfer               | Microsoft.Cdn                     |                  | Yandex Data Transfer                                        |
| Container Instances           | Container Instances | Core Duration                | Microsoft.ContainerInstance       |                  | Yandex Serverless Containers                                |
| Container Instances           | Container Instances | Duration                     | Microsoft.ContainerInstance       |                  | Yandex Serverless Containers                                |
| Container Instances           | Container Instances | Executions                   | Microsoft.ContainerInstance       |                  | Yandex Serverless Containers                                |
| Container Instances           |                     | Memory Duration              | Microsoft.ContainerInstance       |                  | Yandex Serverless Containers                                |
| Container Instances           |                     | vCPU Duration                | Microsoft.ContainerInstance       |                  | Yandex Serverless Containers                                |
| Machine Learning Studio       | Production Web API  |                              | Microsoft.MachineLearning         |                  | Yandex DataSphere                                           |
| Bandwidth                     |                     | %Data Transfer%              | Microsoft.MachineLearningServices |                  | Yandex Data Transfer                                        |
| Bandwidth                     |                     | %Data Transfer%              | Microsoft.Search                  |                  | Yandex Data Transfer                                        |
| VPN Gateway                   |                     | %Gateway%                    | Microsoft.Network                 |                  | \-                                                          |
| VPN Gateway                   |                     | %Gw%                         | Microsoft.Network                 |                  | \-                                                          |
| VPN Gateway                   |                     | %Data Transfer%              | Microsoft.Network                 |                  | \-                                                          |
| Traffic Manager               |                     | %Azure Endpoint%             | Microsoft.Network                 |                  | Yandex Network Load Balancer                                |
| Traffic Manager               |                     | %Service Endpoint%           | Microsoft.Network                 |                  | Yandex Network Load Balancer                                |
| Traffic Manager               |                     | %DNS Queries%                | Microsoft.Network                 |                  | Yandex Network Load Balancer                                |
| Traffic Manager               |                     | %Real User Measurements      | Microsoft.Network                 |                  | Yandex Network Load Balancer                                |
| Traffic Manager               |                     | %Traffic View%               | Microsoft.Network                 |                  | Yandex Network Load Balancer                                |
| Azure Firewall                |                     | Deployment                   | Microsoft.Network                 |                  | [cloud.ru](http://cloud.ru/) Web Application Firewall (WAF) |
| Azure Firewall                |                     | Data Processed               | Microsoft.Network                 |                  | [cloud.ru](http://cloud.ru/) Web Application Firewall (WAF) |
| Notification Hubs             |                     |                              | Microsoft.NotificationHubs        |                  | Битрикс24 NotiSend                                          |
| Power BI                      | Embedded            |                              | Microsoft.PowerBI                 |                  | Yandex DataLens                                             |
| Power BI Embedded             | Power BI Embedded   | A1 Node                      | Microsoft.PowerBIDedicated        |                  | Yandex DataLens                                             |
| Power BI Embedded             |                     | A1                           | Microsoft.PowerBIDedicated        |                  | Yandex DataLens                                             |

### Вывод

В ходе выполнения данной работы мы познакомились с обилием облачных сервисов Azure.
Также мы сопоставили сервисы Azure с сервисами Yandex Cloud.
Для большинства сервисов удалось найти аналоги в Yandex Cloud, некоторые - Cloud.ru или Битрикс24.
Поэтому можно сделать вывод, что возможно мигрировать на отечественные сервисы.

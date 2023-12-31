# Аналитическая работа 1

## Состав команды
`Федорин Кирилл K3240` - капитан 

`Яковенко Ксения K3240`

`Сергеев Виктор K3241`


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

![image](https://github.com/Di0Zavr/itmo_cloud_2023/blob/main/CloudLabs/lab1/aws%20table.png?raw=true)

### Список сервисов и их описание

1. ***AmazonCloudWatch*** -
   сервис мониторинга и управления ресурсами в среде AWS.
   Он следит за состоянием различных ресурсов в реальном времени; собирать, хранить и агрегировать данные о разных метриках;
   возможно настроить оповещения, создавать графики и дэшборды для визуализации данных.

2. ***AWSBudgets*** -
   сервис управления бюджетами, который помогает контролировать расходы в облаке AWS.
   Он позволяет отлеживать ресурсы, устанавливать бюджеты на ресурсы и прогнозировать будущих расходов.
3. ***AWSDeviceFarm*** -
   сервис тестирования мобильных приложений на реальных устройствах, предоставляемых в облаке.
   Позволяет тестировать мобильные приложения на более чем 2000 устройствах,
   генерирует отчёты о тестах, предоставляет инструменты для ручного и автоматического тестирования
4. ***AWSLambda*** -
   менеджер для выполнения кода в облаке без необходимости управления инфраструктурой.
   Запускает функции в ответ на различные триггеры, позволяет масштабировать выполнение функции и сосредоточить внимание разраба только на коде, а не поддержку инфраструктуры
5. ***ElasticMapReduce*** -
   управляемый сервис для обработки и анализа больших объемов данных, используя фреймворки, такие, как Apache Hadoop, Apache Spark, Apache Hive и другие.
   Легко интегрируется с другими сервисами AWS и обеспечивает управление жизненным циклом кластер.
6. ***AmazonEC2***
   предоставляет виртуальные серверы в облаке, что позволяет пользователям запускать приложения и обрабатывать данные в облачной среде.
7. ***AmazonWorkMail*** -
   управляемый сервис электронной почты и календаря в облаке для бизнес-организаций.
   Включает полнофункциональные почтовые ящики с интегрированным календарем, синхронизацию электронной почты и календаря с различными устройствами.
8. ***AmazonWorkSpaces*** -
   виртуальные рабочие столы в облаке, которые пользователи могут запускать и использовать для доступа к своим приложениям и данным из любого места.
   Предоставляет настраиваемые сетевые параметры, включая использование виртуальных частных облаков.
9. ***A4B*** -
   управляемый сервис для интеграции с интеллектуальным помощником Alexa для улучшения рабочих процессов и увеличения производительности.
   Позволяет интегрировать Alexa с устройствами рабочего пространства и выполнять операции с помощью голосовых команд.
10. ***AmazonDetective*** -
   управляемый сервис для анализа данных о безопасности и выявления аномалий в облачной среде AWS.
   В автоматическом режиме анализирует логи, используется машинное обучение для выявления аномалий и потенциальных угроз.
   Можно делать графические отчёты для визуализации отношений между ресурсами и событиями.
11. ***AmazonInspector*** -
   управляемый сервис для автоматизации оценки безопасности приложений, развернутых в среде AWS.
   Автоматически оценивает безопасность приложений на предмет уязвимостей и позволяется настраивать параметры сканирования.
12. ***AmazonMacie***
   предоставляет управляемый сервис для обнаружения, классификации и защиты конфиденциальных данных в облачной среде AWS.
   Использует машинное обучение для обнаружения конфиденциальных данных и отслеживает подозрительную активность в облаке.
13. ***AmazonPinpoint*** -
   сервис для управления и взаимодействия с конечными пользователями через различные каналы связи.
   Позволяет отправлять персонализированные сообщения (в зависимости от профиля и поведения) конечным пользователям через различные каналы,
   а также анализировать взаимодействие.
### Итоговая таблица
![image](https://github.com/Di0Zavr/itmo_cloud_2023/blob/main/CloudLabs/lab1/end%20aws%20table.png?raw=true)
### Сопоставление сервисов между разными провайдерами

В таблице ниже представлено сопоставление сервисов между разными российскими провайдерами.

| Meter Category    | Аналоговые сервисы                                        |
|-------------------|-----------------------------------------------------------|
| AmazonCloudWatch  | Yandex Monitoring                                         |
| AWSBudgets        | \-                                                        |
| AWSDeviceFarm     | \-                                                        |
| AWSLambda         | Yandex Cloud Functions                                    |
| ElasticMapReduce  | [cloud.ru](http://cloud.ru/) MapReduce Service (MRS)      |
| AmazonEC2         | Yandex Instance Groups                                    |
| AmazonWorkMail    | Yandex360                                                 |
| AmazonWorkSpaces  | Yandex Cloud Desktop                                      |
| A4B               | \-                                                        |
| AmazonDetective   | \-                                                        |
| AmazonInspector   | [cloud.ru](http://cloud.ru/)  Host Security Service (HSS) |
| AmazonMacie       | -                                                         |
| AmazonPinpoint    | amoCRM                                                    |

### Вывод

В ходе выполнения данной работы мы познакомились с обилием облачных сервисов AmazonWebServices.
Также мы сопоставили сервисы AWS с сервисами Yandex Cloud.
Для большинства сервисов удалось найти аналоги в Yandex Cloud, некоторые на других платформах.
Поэтому можно сделать вывод, что большую часть инфраструктуры можно мигрировать на отечественные сервисы.

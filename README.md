# schEDUler

Базовый репозиторий для выполнения практического задания по написанию библиотеки с учётом управления зависимостями, и кода, использующего эту библиотеку с подключенным [PHP-DI](http://php-di.org).

Задача:

* Шедулер (/src/Scheduler) должен предоставлять:
    * интерфейс для добавления заданий в расписание;
    * интерфейс для получения заданий из расписания для выполнения;
    * интерфейсы для добавления и получения заданий из очереди;
    * интерфейс для фабрики обработчиков заданий;
    * интерфейс для обработчика задания;
    * базовую реализацию воркера для выборки заданий из расписания и добавления их в очередь;
    * базовую реализацию воркера для получения задания из очереди, поиска обработчика для неё и запуска этого обработчика.
* Шедулер должен запускаться по крону раз в минуту, выбирать из расписания задания, которые нужно выполнить и добавлять их очередь на выполнения.
* Базовые реализации интерфейсов должны быть покрыты тестами.
* Основной код (/src/Topface) должен предоставлять:
    * возможность запуска крона через run.php;
    * возможность запуска обработчиков очереди через run.php;
    * возможность добавлять два-три типа задания в расписание;
    * реализации необходимых для работы библиотеки интерфейсов;
    * обработчики заданий расписания.
* Способ просмотра результатов работы заданий можно выбрать самим (логи, ES и т.п.). 
* Для хранения расписания, заданий и очереди использовать Redis.
* Опционально:
    * Добавить логирование действия через PSR-3 интерфейс.
    * Добавить сбор статистических метрик работы шедулера.

Для упрощения работы добавлены:
* [интерфейс](/src/Scheduler/Task/SchedulerTaskInterface.php) и [реализация](/src/Scheduler/Task/SchedulerTask.php) для сущности "Задание";
* [интерфейс](/src/Scheduler/SchedulerInterface.php) и [простой вариант реализации](/src/Scheduler/Scheduler.php) логики хранения расписания.

Для запуска кода и тестов советуется использовать докер-образ hub.core.tf/topface-ci:1.4.
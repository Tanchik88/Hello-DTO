DTO классы, нормализация БД, логгирование
=========================================

## Что такое DTO (Data Transfer Object)?

Зачастую, в клиент-серверных приложениях, данные на клиенте (слой представления) и на сервере (слой предметной области) структурируются по-разному. На стороне сервера это дает нам возможность комфортно хранить данные в базе данных или оптимизировать использование данных в угоду производительности, в то же время заниматься “user-friendly” отображением данных на клиенте, и, для серверной части, нужно найти способ как переводить данные из одного формата в другой. Конечно, существуют и другие архитектуры приложений, но мы остановимся на текущей в качестве упрощения. DTO-подобные объекты могут использоваться между любыми двумя слоями представления данных.

Подробнее: статья [Переосмысление DTO в Java](https://habr.com/ru/articles/513072/)

## Нормализация БД

Нормализация — это процесс организации данных в базе данных, Она включает в себя создание таблиц и установление связей между ними в соответствии с правилами, разработанными как для защиты данных, так и для повышения гибкости базы данных, устраняя избыточность и несогласованную зависимость.

Избыточность данных приводит к непродуктивному расходованию свободного места на диске и затрудняет обслуживание баз данных. Например, если данные, хранящиеся в нескольких местах, потребуется изменить, в них придется внести одни и те же изменения во всех этих местах. Изменение адреса клиента проще реализовать, если эти данные хранятся только в таблице Customers и нигде в базе данных.

Что такое «несогласованные зависимости»? Хотя пользователю интуитивно понятно искать в таблице Клиенты адрес конкретного клиента, возможно, не имеет смысла искать там зарплату сотрудника, который обращается к данному клиенту. Зарплата сотрудника связана с сотрудником (зависит от него), поэтому эти сведения следует хранить в таблице Employees (сотрудники). Несогласованные зависимости могут затруднять доступ к данным, так как путь к данным при этом может отсутствовать или быть неправильным.

Существует несколько правил нормализации баз данных. Каждое правило называется "обычной формой". Если соблюдается первое правило, база данных, как говорят, находится в "первой нормальной форме". При соблюдении первых трех правил база данных считается в "третьей нормальной форме". Хотя и другие уровни нормализации возможны, третья нормальная форма считается самым высоким уровнем, необходимым для большинства приложений.

Подробнее: статья [Описание основных приемов нормализации базы данных](https://learn.microsoft.com/ru-ru/office/troubleshoot/access/database-normalization-description)

## Логгирование (журналирование)

Ведение журнала (лога) или журналирование (логгирование) является важной частью всех приложений и приносит пользу не только нам, разработчикам, но и пользователям системы, а также сопровождающим ее. Приложения Spring Boot должны собирать соответствующие данные журнала, чтобы помочь нам диагностировать и устранять проблемы и измерять бизнес-показатели.

Фреймворк Spring Boot предварительно настроен с использованием Logback в качестве реализации по умолчанию в его "компетентном" подходе к Spring Framework. В статье рассматриваются различные способы настройки ведения журнала в Spring Boot.

Подробнее: статья [Ведение журнала в Spring Boot](https://habr.com/ru/articles/521950/)

---
Owner: Nikita Vdovin
tags:
  - TM
---
# ГПЭБ Task Mining

## Расчет потребленной электроэнергии

Для того, чтобы рассчитать объем потребленной электроэнергии сотруднику необходимо обратиться за сведениями к некоторым “бзам данных”. Например, к тем, которые клиенты хранят в Excel.

В самой Excel сотрудники с помощью поиска выбирают нужную запись. Нужная запись при этом хранится в системе 1С.  
После этого, сотрудник, по всей видимости, формирует отчет в Excel, и печатает его.  

При этом, только на этом фрагменте операции мы видим неоптимальности, которые уже сейчас можно оптимизировать. Например:  
Вести базу данных по отчетам потребителей не в Excel, так как это ненадежно, небезопасно и долго, но вести базу знаний в спезиализированной БД, в которой также будут храниться ключевые данные по клиентам. При этом в такой БД (  
_MySQL, PostgreSQL, Oracle_) можно будет настроить прямую интеграцию с 1С.  
При этом скорость работы также возрастет из-за особенностей работы СУБД.  

## Рабочий стол специалиста (1С > Outlook)

Рабочий стол специалиста, это, судя по всему, ключевое рабочее место, или ключевая транзакция сотрудников — специалистов. С рабочего стола специалиста сотрудники могут начать выполнять те или иные типы задач.

### Начало работы специалиста

Одной из типовых задач специалиста является работа с почтой Outlook. В ней пользователь отвечает на сообщения, высылает отчеты и выполняет довольно большой пулл действий, однако все это можно также оптимизировать.

К примеру, мы видим как рабочий процесс специалиста начинается с того, как он открывает все необходимые для работы файлы и вложения напрямую с почтового клиента. При этом почтовый клиент используется, как своеобразная база заний, или каьталог шаблонов.

Мы видим, как сотрудники открывают программы для чтония PDF файлов, и, судя по всему, используют их как “визуальный эталон”. То есть смотрян на содержимое открытого файла, на структуру, и делают по аналогии свою работу в 1С.

При всем при этом 1С — довольно гибкая и настраиваемая среда. Она вполне позволяет создавать шалоны, готовые решения, автозаполнения и пр.

### Ручная отправка отчетов

К примеру, на данном участке операции видно, как специались создает сообщение для того, чтобы выслать отчет, либо как-то зафиксировать обращение. Но 1С позволяет настроить интеграцию с почтовым клиентом Outlook, чтобы при этом текст письма, адресаты, тема — все это формировалось автоматически.

## Итог

Наш отчет по Task Mining — весьма гибкий отчет, который позволяет найти вседи цепочек протекания операции даже самые мельчайшие неоптимальности, что позволит вам принять рациональное решение по поиску пути к оптимизации.
---
id: cpfmd5f1o8e12tv18ijrwgm
title: RPC
desc: ""
updated: 1684219745981
created: 1684218670836
---

## Идея RPC

Основная идея RPC состоит в том, что выполнение сетевого запроса к удаленному сервису должно выглядеть как вызов локальной функции или метода в пределах одного процесса.

**AKA 'location transparency'** - независимость от расположения.

## Отличия RPC и локального вызова функции (ЛФ):

1. ЛФ присуща предсказуемость. Он либо завершается, либо нет.  
   Сетевой запрос может потеряться из-за различных инфраструктурных причин (сетевой сбой, медленная удаленная машина).

2. ЛФ всегда возвращает результат, или геренирует исключение, или ничего не возвращает.  
   Сетевой запрос же может еще вернуться, но без результата (например таймаут соединения). В следствие чего невозможно узнать, был ли выполнен/доставлен запрос.

3. Повторные неудавшиеся вызовы на самом деле могут выполняться. Требуется реализовывать механизм дедупликации (**AKA идемпотентность**).

4. Скорость выполения ЛФ +/- предсказуема и постоянна.  
   Сетевой же запрос может выполняться с различными таймингами.

5. ЛФ может принимать указатели на объекты в общей локальной памяти.  
   Сетевой запрос требует передачу всех необходимых для успешного выполнения данных.

6. Реализация клиента/сервера на разных языках может привести к ошибкам в преобразовании некоторых типов данных.

## Форматы сериализации данных

- Apache Avro (+ RPC поддержка)
- Apache Thrift (+ RPC поддержка)
- Protocol Buffers (Protobuf). Используется в gRPC.

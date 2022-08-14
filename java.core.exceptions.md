---
id: yarvu4gfm1zazi71a8o2tt0
title: Exceptions
desc: ''
updated: 1660502569833
created: 1659561906622
---

## Иерархия

Все ошибки делятся на две группы:
  - checked
  - unchecked  

!["Иерархия ошибок"](assets/images/exceptions_hierarchy.png)

## Errors

Error — это критическая ошибка во время исполнения программы, связанная с работой виртуальной машины Java. В большинстве случаев Error не нужно обрабатывать, поскольку она свидетельствует о каких-то серьезных недоработках в коде.

### java.lang.OutOfMemoryError
&nbsp;
Создается, если в системе недостаточно ресурсов для создания потока. Для появления этого сообщения есть три причины:

  - Недостаточно ресурсов для пользователя или приложения.
  - Системе не хватает собственной памяти для нового потока. Для потоков требуется собственная память для внутренних структур JVM, стека Java и собственного стека.
  - Работает слишком много потоков, и системе не хватает внутренних ресурсов для создания потоков.
   
### java.lang.StackOverflowError
&nbsp;
У каждого потока, создаваемого в программе Java или в JVM, есть собственное пространство стека, которое не зависит от кучи Java. Общий размер стека, доступный приложению, задается во время запуска, и это значение определяет число возможных потоков; превышение его приведет к ошибке java.lang.StackOverflowError

Во избежание этой ошибки увеличьте размер стека, доступный приложению.

### java.lang.AssertionError
&nbsp;
Выбрасывается если в выражении 
```java
assert BoolExpression : "Some message"
```
BoolExpression возвращает false.
Режим assertions работает только при запуске программы с флагом '-ea' (enable assertions)


## Exceptions

### java.lang.Exception
Базовый класс для checked ошибок, все наследуемые ошибки так же unchecked, кроме RuntimeException.
Примеры классов:  
  - IOException
  - FileNotFoundException

### java.lang.RuntimeException
Базовый класс для unchecked ошибок.
Примеры классов:
  - IllegalStateException
  - IllegalArgumantException
  - NullPointerException
  - IndexOutOfBoundsException
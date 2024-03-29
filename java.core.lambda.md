---
id: 01qhpq4ekspyrw4qccsnozf
title: Lambda
desc: ""
updated: 1684842572120
created: 1684321581580
---

Лямбда-выражения являются анонимными классами, реализующими метод функционального интерфейса.

## Функциональные интерфейсы

Если интерфейс в Java содержит один и только один абстрактный метод, то он называется функциональным.

Функциональные интерфейсы рассматривались как Single Abstract Methods (SAM).

Например:

```java
@FunctionalInterface
public interface Runnable {
  void run();
}
```

## Стандартные интерфейсы Java

1. Predicate (Bi-)
2. Function (Bi-)
3. Supplier
4. Consumer (Bi-)
5. BinaryOperator
6. ... и т.д.

## Ссылки на методы

Ссылка на метод - это сокращенный синтаксис выражения лямбда, который выполняет только один метод. Это позволяет нам ссылаться на конструкторы или методы, не выполняя их. Ссылки на методы и Lambda аналогичны тем, что они оба требуют целевого типа, который состоит из совместимого функционального интерфейса.

## Отличия от Анонимномых классов

1. Lambda-expression не могут выбрасывать проверяемые исключения, только unchecked.
2. Lambda-expression может ссылаться только на внешние final (effectively final) переменные (неизменяемые после объявления).
3. Анонимный класс создает свой собственный scope. При наличии переменной с одинаковым именем за пределами АК, произойдет shadowing (сокрытие).  
   Lambda-expression работает в скоупе, где объявлена. Невозможно объявить переменную с тем же именем внутри тела Lambda-expression.
4. АК имеет собственные поля и может хранить состояние между вызовами. Lambda-expression доступен только захват скоупа в момент вызова и использование effectively final переменных.
5. Для АК создается отдельный .class файл. А Lambda-expression генерируется в рантайме через LambdaMetaFactory. Поэтому лямбды обычно работают быстрее.
6. Lambda-expression реализуют только функицональне интерфейсы. АК могут реализовывать интерфейсы/расширять классы с любым количеством абстрактных методов.

---
id: nza11e7ebwgeec2reuj2zcn
title: Features JDK-17
desc: ""
updated: 1684660936728
created: 1684659518398
---

## Текстовые блоки

До появления текстовых блоков обычно мы определяли подобные строки следующим образом:

```java
String text = "{\n" +
                  "  \"name\": \"Капитан Джек Воробей\",\n" +
                  "  \"age\": 45,\n" +
                  "  \"address\": \"г. Сочи, ул. Пиратская, д. 7, кв. 777\"\n" +
                  "}";
    System.out.println(text);
```

С использование текстового блока:

```java
String text = """
            {
              "name": "Капитан Джек Воробей",
              "age": 45,
              "address": "г. Сочи, ул. Пиратская, д. 7, кв. 777"
            }
            """;
System.out.println(text);
```

## Оператор switch

switch можно использовать в качестве аргумента для метода:

```java
System.out.println(
      switch (month) {
      case DECEMBER, JANUARY, FEBRUARY -> "Зима";
      case MARCH, APRIL, MAY -> "Весна";
      default -> "Не зима и не весна";
});
```

Что если нам необходимо не просто возвратить значение, но при это еще выполнить одно или более действий?  
На помощь приходит ключевое слово **yield**.

Рассмотрим пример:

```java
String text = switch (month) {
        case DECEMBER, JANUARY, FEBRUARY -> {
            System.out.println("выбранный месяц: " + month);
            yield "Зима";
        }
        case MARCH, APRIL, MAY -> "Весна";
        default -> "Не зима и не весна";
    };
System.out.println(text);
```

## Records

Неизменяемые структуры данных.

```java
public record GrapeRecord(Color color, int nbrOfPits) {
}
```

Также возможно добавление валидации параметров конструкторв:

```java
record GrapeRecord(Color color, int nbrOfPits) {
        GrapeRecord {
            if (color == null) {
                throw new IllegalArgumentException("Color may not be null");
            }
        }
    }
```

## Sealed-классы

```java
public abstract sealed class FruitSealed permits AppleSealed, PearSealed {
}
public non-sealed class AppleSealed extends FruitSealed {
}
public final class PearSealed extends FruitSealed {
}
```

Использование sealed класса накладывает три важных ограничения на его разрешенных наследников:

- Все разрешенные наследники должны принадлежать к тому же модулю, что и запечатанный родительский класс.

- Каждый разрешенный наследник должен явно наследоваться от запечатанного класса-родителя.

- Каждый разрешенный наследник должен сопровождаться одним из трех модификаторов: final, sealed или non-sealed.

## Pattern matching

```java
private static void patternMatching() {
     Object o = new PhoneClass (Color.BLUE, 32);
     if (o instanceof PhoneClass phone) {
        System.out.println("У этого телефона " + phone.getRamSize() + " Гб ОЗУ.");
     }
}
```

---
id: e9otxuunkc40hblugvj0zft
title: Stream
desc: ""
updated: 1684336441847
created: 1684328132810
---

Стримы предназначены для параллельных и последовательных агрегаций, выполняемых через цепочку операций.

## Виды операций

Операции бывают Intermediate/Terminate, Stateless/Stateful

### Intermediate

| Операция   | Stateful | Описание                                                |
| ---------- | -------- | ------------------------------------------------------- |
| peek()     |          | Аналог forEach(), только промежуточный (нетерминальный) |
| map()      |          | Преобразовать данные из одного типа в другой            |
| filter()   |          | Отфильтровать элементы                                  |
| distinct() | +        | Удалить дублирующиеся элементы                          |
| sorted()   | +        | Сортировка и обратная сортировка элементов              |
| limit()    | +        | Лимит количества элементов                              |
| skip()     | +        | Пропустить первые элементы                              |
| flatMap()  |          | Сопоставить поток с развернутым потоком                 |

### Terminate

| Операция                            | Описание                                                  |
| ----------------------------------- | --------------------------------------------------------- |
| collect()                           | Преобразовать поток в List toList(), для String joining() |
| forEach()                           | Итерация по каждому элементу                              |
| count()                             | Узнать количество элементов стрима                        |
| min(), max()                        | Найти минимальное и максимальное значение                 |
| findFirst(), findAny()              | Найти элемент в стриме                                    |
| allMatch(), noneMatch(), anyMatch() | Соответствие элементов условию                            |
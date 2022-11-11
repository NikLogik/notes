---
id: iukmod8sf806y5l5xbt4keo
title: Garbage Collection
desc: ''
updated: 1668198675747
created: 1659518499428
---

## GC Roots


* Class: Классы, загруженные системными ClassLoaders, включая статичные
* Stack Local: Локальные переменные и параметры методов хранимые на стеке
* Active Java Threads: Все активные Java потоки
* References: JNI (Java Native Interface) Native code Java objects created for JNI calls; contains local variables, parameters to JNI methods, and global JNI references
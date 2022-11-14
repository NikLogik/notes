---
id: zs584s3c0v13qr07sy1ltnd
title: 'Core'
desc: ''
updated: 1668372660635
created: 1668290871247
---

## ApplicationContext

Типы ApplicationContext:
* ClassPath*
* Xml*
* WebXml*
* Annotation*
* Groove*

___

## ApplicationContext initialization stages   

![Context flow](assets/images/spring-core-app-context-flow.jpeg)

___

## ApplicationContextEvents

* **ContextRefreshedEvent** - публикуется, когда ApplicationContext инициализирован или обновлен, например, при использовании метода AbstractApplicationContext#refresh()
* **ContextStartedEvent** - публикуется, когда ApplicationContext запущен методом ConfigurableApplicationContext#start()
* **ContextStoppedEvent** - публикуется, когда ApplicationContext остановлен методом ConfigurableApplicationContext#stop()
* **ContextClosedEvent** - публикуется, когда ApplicationContext закрыт методом ConfigurableApplicationContext#close()
* **RequestHandledEvent** - web-событие, которое оповещает о том, что все бины из HTTP запроса были обработаны. Применимо только для web-приложений с использованием Spring DispatcherServlet
--
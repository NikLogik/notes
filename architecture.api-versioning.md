---
id: n1rdfitssl6u8ggtq67isgg
title: API Versioning
desc: ''
updated: 1668501409998
created: 1668501226290
---

## API Versioning

Подходы к версионированию:

* URI Path - изменение маршрутов для отдельных версий (удобно для версионирования группы маршрутов)
* Query Parameters - указание желаемой версии через параметры запроса
* Headers - указание версии через заголовки (Accept-*)
* MIME Types - использования собственных типов данных (Accept-* => Content-Type: application/vnd.version.v1+json)
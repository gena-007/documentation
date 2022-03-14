# Edengine

## Общие положения, описание архитектуры

Edengine - платформа для быстрого запуска образовательных программ в любой сфере (создание  и продажа онлайн-курсов)

Проект состоит из 2-х платформ, завязанных на 1 backend сервис
   * app.edengine.ru - плаформа для авторов, размещающих курсы
   * edstore.io  - маркетплейс: покупка курсов студентами






ект имеет микросервисную архитектуру. Каждый сервис запускается под своим пользователем и работает на определенном порту (имя сервиса соответствует имени пользователя)
> bslpln_auth_service - port 23181  
> bslpln_account_service - port 23281  
> bslpln_project_service - port 23381   
> bslpln_sync_service - port 23481

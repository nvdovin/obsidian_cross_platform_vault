---
Owner: Nikita Vdovin
---
# Последовательный запуск скриптов (GraphQL)

1. Создать ключ API со стандартным режимом аутэнтификации
2. У ключа должен быть доступ на изменение пространства. Выбираем то пространство, которое собираемся изменять.  
    Копируем ключ.  
    
3. Берем блок “Отправить запрос”.
    
    1. В URL указываем адрес системы с параметром api_key=<ключ>
    2. Метод - пост
    3. Заголовок лучше указывать,
        
        ```JavaScript
        Content-Type
        ```
        
        ```JavaScript
        application/json; charset=utf8
        ```
        
    4. Тело запроса:
    
    ```JavaScript
                                {’query’: ‘mutation{automation{script{execute(id: ???){id, is_running}}}}}
    ```
    
    Чтобы узнать GUID используем в GraphQL заполс
    
    `query{automation{script{script_general(id: 1024){id guid workspace{id}}}}}`
    
    Чтобы запустить скрипт
    
    `mutation{automation{script{execute_by_guid(guid: "82a554c4-6bfb-4c72-9912-3dd8a7c91557"){guid}}}}`
    
    И есть также опциональный аргумент data
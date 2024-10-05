---
Owner: Nikita Vdovin
---
**.Блок "JavaScript" varchive**

**Общее описание**

Блок "JavaScript" служит для обработки данных посредством Js кода.

Блок может выполнять множественные/связанные HTTP запросы.

Блок может выгружать/загружать файлы с помощью HTTP запросов.

Блок позволяет совершать математические действия над данными(переменными). Блок позволяет парсить строки в JSON, фильтровать значения.

|   |   |   |
|---|---|---|
|**Имя блока в JSON(Импорт/Экспорт)**|**Макет**|**JIRA**|
|"javascript"|||

**Входные поля**

|   |   |   |
|---|---|---|
|**Входные поля**|**Описание**|**Валидация**|
|**Javascript**|JS код, задающий логику работы блока.  <br>Для корректной работы, должен быть соблюден ожидаемый формат кода.|Обязательное поле.  <br>  <br>**Доступные значения:** не пустрока.|

**Структура базы данных**

Реализация блока "JavaScript" не предполагает изменение существующей структуры базы данных.

**Описание реализации**

В основе работы блока, лежит подключение движка JavaScript V8. Библиотека J2V8 предоставляет Java коду доступ к api V8.

Принцип работы:

1.Из входных полей (Fields) извлекается JS код.

2.В JS коде производится поиск переменных и замена из формата

**${a5.my_variable_name}** в формат **bundle.inputData.my_variable_name**.

3.Создается экземпляр V8 и на его основе, создаются объекты **bundle** и **Z** объект.

4.Создается _ComplexIterator_ на основе полученных имен переменных. _ComplexIterator_ находит значения переменных.

5.При обходе записей _ComplexIterator_ на каждой итерации, в объект **bundle** инжектируются значения переменных.

6.Объект **bundle** заново инжектируется в общую среду выполнения V8.

7.В выходном результате работы V8, ищется и запускается функция **output**. Если функция отсутствует, система выдаст ошибку.

8.Из имен и значений результата выполнения **output**, формируются выходные записи. Выходные записи складываются в _List<Record> records_.

9.Работа блока завершается формированием выходного итератора на основе собранной коллекции записей (_List<Record> records_).

10.Завершается работа движка V8 и освобождаются ресурсы библиотеки.

**Примеры JavaScript кода для настройки блока**

Импорт нового скрипта

```js
const apiKey = '776f7da1626543e4be2407f70b13942f';
var resp1 = z.request(
	{
		url: 'http://localhost:8010/graphql?api_key=' + apiKey, method: 'POST',
		headers: {
			["Content-Type"]: 'my custom value'
		},
		multipartBody: [
				{
					key: 'operationName',
					textValue: 'ImportScript'
				}, 
			{
				key: 'variables',
				textValue: '{"workspace_id":1}'
			}, 
			{
				key: 'query',
				textValue: 'mutation ImportScript($workspace_id: Long!){automation{script{import_new_script(workspace_id: $workspace_id){script{name}}}}}'
			}, 
			{
				key: '0',
				fileValue: ${a5.file_content},
				fileName: 'newSuperGigaBlocks.zip',
				contentType: 'application/x-zip-compressed' 
			}
		]
	}
);
const app = {
output: () => (
	{
		f1: 'FAKE DATA',
		f2: 1234,
		resp_1_body: JSON.stringify(resp1.response), resp_1_header: JSON.stringify(resp1.headers), resp_1_status: resp1.status,
		["var-with-hard-name-1"]: resp1.headers.date, ["var-with-hard-name-2"]: resp1.headers["cache-co content_type: resp1.headers["content-type"], content_length: resp1.headers["content-length"])
}
```

Старт скрипта по GUID

```JavaScript
const apiKey = '776f7da1626543e4be2407f70b13942f';
const scriptGuid = '28703685-eade-4173-a73c-b15b83604279';
const workspaceId = 1;
var resp1 = z.request(
	{
		url: 'http://localhost:8010/graphql?api_key=' + apiKey, 
		method: 'POST',
		jsonBody: '{"query":"mutation{automation{script{execute_b scriptGuid + '\\", 
		workspace_id:' + workspaceId + '){guid}}}} 
	}
);
const app = {
	output: () => (
		{
			resp_1_body: JSON.stringify(resp1.response), 
			resp_1_header: JSON.stringify(resp1.headers), 
			resp_1_status: resp1.status,
			["var-with-hard-name-1"]: resp1.headers.date, 
			["var-with-hard-name-2"]: resp1.headers["cache-co content_type: resp1.headers["content-type"], 
			content_length: resp1.headers["content-length"] 
		}
	)
}
```

|   |   |
|---|---|
|||
|Получения файла с сервиса Jira|const login = 'test@infomaximum.com';  <br>  <br>const password = 'JfCi!$gJRQB$QK5x';  <br>  <br>const auth = z.base64Encode(login + ':' + password);  <br>var resp1 = z.request({  <br>  <br>url:  <br>  <br>'https://jira.office.infomaximum.com/secure/attachment/76158/ method: 'GET',  <br>  <br>headers: {  <br>  <br>Authorization: 'Basic ' + auth  <br>  <br>}  <br>  <br>});  <br>const app = {  <br>  <br>output: () => ({  <br>  <br>resp_1_body: JSON.stringify(resp1.response), resp_1_header: JSON.stringify(resp1.headers), resp_1_status: resp1.status,  <br>  <br>file_content: resp1.response,  <br>  <br>["var-with-hard-name-1"]: resp1.headers.date, ["var-with-hard-name-2"]: resp1.headers["cache-co content_type: resp1.headers["content-type"], content_length: resp1.headers["content-length"] }  <br>  <br>)  <br>  <br>}|

|   |   |
|---|---|
|Добавление объекта методом PUT  <br>  <br>на сервисе  <br>https://petstore.swagger.io|const body = '{"id": 0, "category": {"id": 0, "name": "string "doggie", "photoUrls": ["string"], "tags": [{"id": 0, "name": "status": "available"}';  <br>var resp1 = z.request({  <br>  <br>url: 'https://petstore.swagger.io/v2/pet', method: 'PUT',  <br>  <br>jsonBody: body  <br>  <br>});  <br>const app = {  <br>  <br>output: () => ({  <br>  <br>resp_1_body: JSON.stringify(resp1.response), resp_1_header: JSON.stringify(resp1.headers), resp_1_status: resp1.status  <br>  <br>}  <br>  <br>)  <br>  <br>}|

|   |   |
|---|---|
|Создание 3х объектов методом POST  <br>  <br>и удаление объекта с id =3  <br>  <br>на сервисе  <br>https://petstore.swagger.io|var resp1 = z.request({  <br>  <br>url: 'https://petstore.swagger.io/v2/store/order', method: 'POST',  <br>  <br>jsonBody: '{"id": 1, "petId": 1, "quantity": 0, "shipDate 06T10:23:02.332Z", "status": "placed", "complete": true}' });  <br>var resp2 = z.request({  <br>  <br>url: 'https://petstore.swagger.io/v2/store/order', method: 'POST',  <br>  <br>jsonBody: '{"id": 2, "petId": 2, "quantity": 0, "shipDate 06T10:23:02.332Z", "status": "placed", "complete": true}' });  <br>var resp3 = z.request({  <br>  <br>url: 'https://petstore.swagger.io/v2/store/order', method: 'POST',  <br>  <br>jsonBody: '{"id": 3, "petId": 3, "quantity": 0, "shipDate 06T10:23:02.332Z", "status": "placed", "complete": true}' });  <br>var resp4 = z.request({  <br>  <br>url: 'https://petstore.swagger.io/v2/store/order/3', method: 'DELETE'  <br>  <br>});  <br>var resp5 = z.request({  <br>  <br>url: 'https://petstore.swagger.io/v2/store/order/3', method: 'DELETE'  <br>  <br>});  <br>const app = {  <br>  <br>output: () => ({  <br>  <br>resp_1_body: JSON.stringify(resp1.response), resp_1_status: resp1.status,  <br>  <br>resp_2_body: JSON.stringify(resp2.response), resp_2_status: resp2.status,  <br>  <br>resp_3_body: JSON.stringify(resp3.response), resp_3_status: resp3.status,  <br>  <br>resp_4_body: JSON.stringify(resp4.response), resp_4_status: resp4.status,  <br>  <br>resp_5_body: JSON.stringify(resp5.response), resp_5_status: resp5.status  <br>  <br>}  <br>  <br>)  <br>  <br>}|

|   |   |
|---|---|
|Данные по задаче taskID из Jira|const login = 'test@infomaximum.com';  <br>  <br>const password = 'JfCi!$gJRQB$QK5x';  <br>  <br>const taskID = 'AU-6505';  <br>  <br>const baseURL = 'https://jira.office.infomaximum.com/rest/api  <br>var resp1 = z.request({  <br>  <br>url: baseURL + 'issue/' + taskID + '?expand=changelog', method: 'GET',  <br>  <br>headers: {  <br>  <br>Authorization: 'Basic ' + z.base64Encode(login + ':' }  <br>  <br>});  <br>const app = {  <br>  <br>output: () => ({  <br>  <br>// resp_1_body: JSON.stringify(resp1.response), // resp_1_changelog: JSON.stringify(resp1.respons resp_1_displayName_0:  <br>  <br>JSON.stringify(resp1.response.changelog.histories[0].author.d resp_1_displayName_1:  <br>  <br>JSON.stringify(resp1.response.changelog.histories[1].author.d resp_1_displayName_2:  <br>  <br>JSON.stringify(resp1.response.changelog.histories[2].author.d resp_1_status: resp1.status  <br>  <br>}  <br>  <br>)  <br>  <br>}|

|   |   |
|---|---|
|Комплексный тест с  <br>  <br>последовательностью  <br>  <br>GET, PUT, POST, DELETE запросов  <br>  <br>на сервисе  <br>https://petstore.swagger.io|resp_2_status: resp2.status,  <br>  <br>resp_3_new_pet_name: resp3.response.name,  <br>  <br>resp_3_status: resp3.status,  <br>  <br>test_status: resp1.response.name != resp3.respons resp_4_body: JSON.stringify(resp4.response), resp_4_status: resp4.status,  <br>  <br>resp_5_body: JSON.stringify(resp5.response), resp_5_status: resp5.status,  <br>  <br>absolute_test_status: resp5.status == 404  <br>  <br>}  <br>  <br>)  <br>  <br>}|

|   |   |
|---|---|
|Создание задачи в Jira и прикрепление вложения|const login = 'test@infomaximum.com';  <br>  <br>const password = 'JfCi!$gJRQB$QK5x';  <br>  <br>const auth = z.base64Encode(login + ':' + password);  <br>var resp0 = z.request({  <br>  <br>url: 'https://jira.office.infomaximum.com/rest/api/2/issu method: 'POST',  <br>  <br>headers: {  <br>  <br>Authorization: 'Basic ' + auth  <br>  <br>},  <br>  <br>jsonBody: '{"fields": {"project": {"key": "AU"},"summary" (если не закрыто - закрыть)","description": "Тестовая задача закрыть)","issuetype": {"name": "Задача"},"fixVersions": [{"nвыпуска","archived": false,"released": false}]}}'  <br>  <br>});  <br>var resp1 = z.request({  <br>  <br>url: 'https://jira.office.infomaximum.com/rest/api/2/issu resp0.response.key + '/attachments',  <br>  <br>method: 'POST',  <br>  <br>headers: {  <br>  <br>Authorization: 'Basic ' + auth,  <br>  <br>["X-Atlassian-Token"]: 'nocheck'  <br>  <br>},  <br>  <br>multipartBody: [  <br>  <br>{ key: 'file',  <br>  <br>fileValue: ${a3.file_content},  <br>  <br>fileName: ${a3.file_name},  <br>  <br>contentType: 'application/octet-stream'  <br>  <br>}  <br>  <br>]  <br>  <br>});  <br>const app = {  <br>  <br>output: () => ({  <br>  <br>resp_0_body: JSON.stringify(resp0.response), resp_0_header: JSON.stringify(resp0.headers), resp_0_status: resp0.status,  <br>  <br>file_content_0: resp0.response,  <br>  <br>issue_key: resp0.response.key,  <br>  <br>resp_1_body: JSON.stringify(resp1.response), resp_1_header: JSON.stringify(resp1.headers), resp_1_status: resp1.status  <br>  <br>}  <br>  <br>)  <br>  <br>}|

|   |   |
|---|---|
|Создание таблицы в ClickHouse|const user = 'writeUser';  <br>  <br>const password = 'write';  <br>const port = '8125';  <br>  <br>const baseURL = 'http://localhost:' + port + '/';  <br>  <br>const query = 'create table IF NOT EXISTS test_table (c1 Null Nullable(String), c3 Nullable(bool))engine = Memory';  <br>var resp1 = z.request({  <br>  <br>url: baseURL + encodeURI('?query=' + query), method: 'POST',  <br>  <br>headers: {  <br>  <br>["X-ClickHouse-User"]: user,  <br>  <br>["X-ClickHouse-Key"]: password  <br>  <br>},  <br>  <br>jsonBody: ''  <br>  <br>});  <br>const app = {  <br>  <br>output: () => ({  <br>  <br>resp_1_body: resp1.response.split('\n'), resp_1_status: resp1.status  <br>  <br>}  <br>  <br>)  <br>  <br>}|

|   |   |
|---|---|
|Получение колонок таблицы в ClickHouse|const user = 'writeUser';  <br>  <br>const password = 'write';  <br>const port = '8125';  <br>  <br>const baseURL = 'http://localhost:' + port + '/'; const query = 'DESCRIBE TABLE test_db.test_table';  <br>var resp1 = z.request({  <br>  <br>url: baseURL + encodeURI('?query=' + query), method: 'GET',  <br>  <br>headers: {  <br>  <br>["X-ClickHouse-User"]: user,  <br>  <br>["X-ClickHouse-Key"]: password  <br>  <br>},  <br>  <br>});  <br>var types = new Array();  <br>  <br>var columns = new Array();  <br>  <br>resp1.response.split('\t\t\t\t\t').forEach((item, i, arr) =>{ const clmn = item.split('\t');  <br>  <br>if(clmn.length == 2){  <br>  <br>columns.push(clmn[0]);  <br>  <br>types.push(clmn[1]);  <br>  <br>}  <br>  <br>});  <br>const app = {  <br>  <br>output: () => ({  <br>  <br>columns: columns,  <br>  <br>types: types,  <br>  <br>resp_1_status: resp1.status }  <br>  <br>)  <br>  <br>}|
|Группировка входных  <br>  <br>значений в массивы, по 10 значений.|const outer = function () {  <br>  <br>var arr = [${a3.table_name}];  <br>  <br>var count = 9;  <br>  <br>var indexer = 1;  <br>  <br>while(z.hasNext() && count > 0){ z.next();  <br>  <br>arr[indexer++] = ${a3.table_name} count--;  <br>  <br>}  <br>  <br>return arr;  <br>  <br>};  <br>const app = {  <br>  <br>output: () => ({  <br>  <br>arrr_1: outer()  <br>  <br>}  <br>  <br>)  <br>  <br>}|

**Z объект**

Предоставляет методы для выполнения в JS среде.

|   |   |
|---|---|
|**Метод**|**Описание**|
|z.base64Encode()|Производит base64 кодирование входной строки.  <br>  <br>**Пример**  <br>  <br>const auth = z.base64Encode(login + ':' + password);|
|z.base64Decode()|Производит base64 декодирование входной строки.  <br>  <br>**Пример**  <br>  <br>const originalText = z.base64Decode(encodedText);|
|z.request()|Выполняет HTTP запрос.  <br>Ожидает на вход объект с конфигурацией запроса.  <br>**ПараметрОписание**urlОбязательный параметр.  <br>URL куда будет отправлен запрос,methodНеобязательный параметр. По умолчанию GET.  <br>Доступные значения: GET, POST, DELETE, PUTheadersНеобязательный параметр.  <br>Список заголовков HTTP запроса.jsonBody/multipartBodyОбязательный параметр для POST и PUT методов.  <br>Тело запроса.|
|z.hasNext()|Возвращает true или false в зависимости от того, есть ли еще элементы в входном итераторе блока.|
|z.next()|Если есть следующий элемент в итераторе, вызов этого метода  <br>обновит все значения тегов маппинга  <br>  <br>на значения соответствующие следующему элементу итератора.  <br>Вызов этого метода, автоматически сокращает количество элементов в выходном итераторе.|
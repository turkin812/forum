# Test case

## Тест-кейс №1.
|  |  |
| ------ | ------ |
| Заголовок | Добавление темы |
| Предусловие | Запустить сервер, введя команду в консоли: **node server.js** |

| Шаг | Ожидаемый результат |
| ------ | ------ |
| Окрыть сниффер Fiddler, ввести адрес: http://localhost:8000/topic, выставить **POST**-запрос, заполнить тело запроса в соответствии с **apiDocumentation.json** и нажать **Execute**  | Отправился запрос на сервер вследствие чего добавилась тема|

## Тест-кейс №2.
|  |  |
| ------ | ------ |
| Заголовок | Вывод всех тем |
| Предусловие | Выполнить Тест-кейс №1 |

| Шаг | Ожидаемый результат |
| ------ | ------ |
| Окрыть браузер и ввести адрес: http://localhost:8000/topic | Открылась страница с текстом в виде формата JSON со всеми темами вид которых представлен в файле **apiDocumentation.json**, в соответствии с адресом http://localhost:8000/topic и методом **GET**-запроса |

## Тест-кейс №3.
|  |  |
| ------ | ------ |
| Заголовок | Вывод одной темы |
| Предусловие | Выполнить Тест-кейс №2 |

| Шаг | Ожидаемый результат |
| ------ | ------ |
|Ввести запрос в браузере http://localhost:8000/topicone?id={topicId}, где topicId - индетификатор темы| Открылась страница с текстом в виде формата JSON с темой, соответствующая индетификатору из запроса, вид которого представлен в файле **apiDocumentation.json**|

## Тест-кейс №4.
|  |  |
| ------ | ------ |
| Заголовок | Изменение темы |
| Предусловие | Выполнить Тест-кейс №2 |

| Шаг | Ожидаемый результат |
| ------ | ------ |
|Окрыть сниффер Fiddler, ввести адрес: http://localhost:8000/topic/{topicId}, где topicId - индетификатор темы, которую вы хотите изменить, выставить **PUT**-запрос, заполнить тело запроса в соответствии с **apiDocumentation.json** и нажать **Execute**  | Изменяется тема в соответствии |

## Тест-кейс №5.
|  |  |
| ------ | ------ |
| Заголовок | Удаление темы |
| Предусловие | Выполнить Тест-кейс №2 |

| Шаг | Ожидаемый результат |
| ------ | ------ |
|Окрыть сниффер Fiddler, ввести адрес: http://localhost:8000/topic/{topicId}, где topicId - индетификатор темы, которую вы хотите изменить, выставить **DELETE**-запрос и нажать **Execute**  | Удаляется тема с введённым индетификатором |

## Тест-кейс №6.
|  |  |
| ------ | ------ |
| Заголовок | Добавление комментария |
| Предусловие | Выполнить Тест-кейс №3 |

| Шаг | Ожидаемый результат |
| ------ | ------ |
|Окрыть сниффер Fiddler, ввести адрес: http://localhost:8000/topic/{topicId}/comment, где topicId - индетификатор темы, к которой вы хотите добавить комментарий, выставить **POST**-запрос и нажать **Execute**  | Добавляется комментарий к теме, соответсвующей индетификатору из запроса |

## Тест-кейс №7.
|  |  |
| ------ | ------ |
| Заголовок | Редактирование комментария |
| Предусловие | Выполнить Тест-кейс №6 |

| Шаг | Ожидаемый результат |
| ------ | ------ |
|Окрыть сниффер Fiddler, ввести адрес: http://localhost:8000/topic/{topicId}/{commentId}, где topicId - индетификатор темы, в которой находится наш добавленный комментарий, commentId - индетификатор комментария, который мы хотим изменить, выставить **PUT**-запрос, заполнить тело запроса в соответствии с **apiDocumentation.json** и нажать **Execute**  | Изменяется комментарий |

## Тест-кейс №8.
|  |  |
| ------ | ------ |
| Заголовок | Удаление комментария |
| Предусловие | Выполнить Тест-кейс №6 |

| Шаг | Ожидаемый результат |
| ------ | ------ |
|Окрыть сниффер Fiddler, ввести адрес: http://localhost:8000/topic/{topicId}/{commentId}, где topicId - индетификатор темы, в которой находится наш добавленный комментарий, commentId - индетификатор комментария, который мы хотим удалить, выставить **DELETE**-запрос и нажать **Execute**  | Удаляется комментарий |

## Тест-кейс №9.
|  |  |
| ------ | ------ |
| Заголовок | Вывод всех тем, с помощью длинного запроса |
| Предусловие | Выполнить Тест-кейс №1 |

| Шаг | Ожидаемый результат |
| ------ | ------ |
| Окрыть браузер и ввести адрес: http://localhost:8000/topic?version={version}&timeWait={timeWait}, где version - версия тем, выведенная на предыдущем шаге, timeWait - время ожидания длинного запроса в секундах | Спустя timeWait выводится список всех тем |
|Окрыть сниффер Fiddler, ввести адрес: http://localhost:8000/topic?version={version}&timeWait={timeWait}, где version - версия тем, выведенная на предыдущем шаге, timeWait - время ожидания длинного запроса в секундах, выставить **GET**-запрос и нажать **Execute**  | Открывается соединение по данному запросу|
|Ввести адрес в Fiddler: ввести адрес:http://localhost:8000/topic], выставить **POST**-запрос, заполнить тело запроса в соответствии с **apiDocumentation.json** и нажать **Execute**  | Добавляется тема, а так же меняется их версия и вследствие закрывается соединение по запросу из предыдущего шага, если данный шаг был сделан в течение времени длинного запроса и выведит все темы |
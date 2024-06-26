# shmr-android-2024

### Домашнее задание
<details>
  <summary>Развернуть</summary>

Вводные:
Как было написано в начале, мы не предоставляем доступ к реальному бэкенду. У вас есть несколько вариантов, как дальше работать над приложением:
- Хранить все данные локально и не работать с бэкендом вообще.
- Подменить реальный бэкенд на замоканные данные. Можно работать с сетью как обычно, но использовать [MockWebServer](https://github.com/square/okhttp/tree/master/mockwebserver), чтобы подменять реальный ответ на бэкенда на .json-файлики, которые вы подготовили и положили в проект. Пример того, какие у бэкенда могут быть эндпоинты и формат, можно посмотреть в отдельном документе https://disk.yandex.ru/i/FtN5cexuoHlv-A

Общие требования:
- Добавить авторизационный токен в запросы (например, через Interceptor). Токен сгенерировать самостоятельно в виде любой строки, так как используется не реальный бэкенд.
- Получать список задач от сервера.
- Отправлять данные о добавлении/удалении/изменении задач с сервером.
- Обработка ошибок от сервера:
   - В случае ошибки с возможностью ретрая попытаться повторить запрос в заданном интервале.
   - Ошибка при получении данных: отобразить (*понятную пользователю*) ошибку на экране и кнопку "Повторить", по кнопке делать запрос на сервер. Если вы уже поддержали кэширование данных локально (например, в бд), то отобразить закэшированные данные, но показать пользователю, что они неактуальны (например, с помощью снекбара). Можно добавить обновление по кнопке или через жест pull-to-refresh.
   - Ошибка при добавлении/удалении/изменении задач: отобразить snackbar с текстом ошибки (*понятной пользователю*).
- Предусмотреть автоматическую загрузку данных при появлении интернета. (Если пользователь перешел из состояния "нет интернета" в состояние "есть интернет", мы должны автоматически отправить запрос на получение данных).
- Реализовать периодическое обновление данных в фоне (раз в 8 часов). (Если вы пока не делали хранение данных в базе, можно просто выполнять запрос без сохранения данных).

Если вы уже реализовали хранение данных:
Если вы уже храните все дела в локальной базе данных (например, с помощью Room), то можно сразу делать домашнее задание с будущей лекции про хранение данных (или позже после лекции про домашнее задание).

Краткое описание того, что надо сделать:
- Приложение должно работать без интернета (отображать задачи, добавлять, удалять и тд).
- Синхронизация данных. Если пользователь внес изменения в офлайн режиме, при появлении интернета мы должны синхронизировать данные с сервером. Учесть момент, что пользователь может менять список с нескольких устройств.
- Реализовать периодическое обновление данных в фоне (раз в 8 часов) с обновлением локальных данных.

Внимание: Все I/O операции (походы в сеть или базу данных) должны выполняться в фоновом потоке.

Дополнительное задание:
- Добавить авторизацию через Я.Паспорт
- попробовать Cronet (со звёздочкой)

</details>

### Ссылки
[OkHttp](https://github.com/square/okhttp) и [Retrofit](https://github.com/square/retrofit)  
[Пример Cronet+Ktor (HTTP/3, GET, POST)](https://github.com/rugged-bl/ktor-client-cronet)  

[O'Reilly / High Performance Browser Networking](https://hpbn.co/)  
[The Cloudflare Blog / The Road to QUIC](https://blog.cloudflare.com/the-road-to-quic/)  
[Android Developers / Perform network operations using Cronet](https://developer.android.com/develop/connectivity/cronet)  
[Use Cronet with other libraries](https://developer.android.com/develop/connectivity/cronet/integration#okhttp)

[Usage statistics of HTTP/2 for websites](https://w3techs.com/technologies/details/ce-http2)  
[Usage statistics of HTTP/3 for websites](https://w3techs.com/technologies/details/ce-http3)  
[Cloudflare Radar / Adoption & Usage](https://radar.cloudflare.com/adoption-and-usage)  

# Yandex_airport_board

# Тестовое задание

## Входные данние

Табло аэропорта

Разработайте клиентское приложение (сайт), где будет табло аэропорта. У табло должны быть следующие функции:
1. просмотр только вылетающий рейсов
2. просмотр только прилетающих рейсов
3. просмотр задержанных рейсов
4. поиск по номеру рейса

В качестве примера можно посмотреть на http://www.svo.aero/. Ограничений на использование шаблонизаторов и библиотек нет. Плюсом будет, если данные для табло вы получите из публичных api. Если решите их не использовать, то положите данные в отдельный файл в репозитории.

## Результат

Реализованные функции:
1. просмотр только вылетающий рейсов
2. просмотр только прилетающих рейсов
3. просмотр задержанных рейсов
4. поиск по номеру рейса

Запустить приложение:

```
npm install
npm start
```
## Ticker

Почему this.\_i не увеличивается. Как исправить?

## Ответ

this.\_i не увеличивается из-за строки ```setInterval(ticker.tick, 1000)``` , т.к. теряется контекст. 

Причина ошибки в нашем примере в том,что в функции ```setTimeout``` значение ```this``` является глобальный объект `window` (который не имеем свойства _i ), поэтому результат `undefined`+1 = `NaN`.

Исправить ситуацию можно следующим способом:

```javascript
function Ticker() {
 this._i = 0;
}
Ticker.prototype = {
 tick: function() {
   console.log(this._i++);
 }
};
var ticker = new Ticker();
setInterval(function() {
 ticker.tick();
}, 1000);
```

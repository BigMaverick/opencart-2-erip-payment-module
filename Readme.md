## Модуль оплаты через систему Расчёт (ЕРИП) для OpenCart 2

Данный модуль обеспечивает информационное взаимодействие между вашим интернет-магазином, системой Расчёт (ЕРИП) и сервисом платежей [bePaid.by](https://bepaid.by)

### Установка

* Создайте резервную копию вашего магазина и базы данных
* Загрузите файл модуля [opencart-erip-payment-module.ocmod.zip](https://github.com/beGateway/opencart-2-erip-payment-module/raw/opencart-2.0/opencart-erip-payment-module.ocmod.zip) с помощью _Модули_ -> _Установка расширений_
* Загрузите содержимое архива в вашу установленную копию OpenCart
* Задайте в настройках модуля Расчёт (ЕРИП):
  * Id магазина
  * Ключ магазина
  * Домен API
  * Код услуги ЕРИП
  * Статус заказа в случае успешной оплаты
  * Включите модуль
  * Опционально задайте идентификатор модуля для сортировки его в списке способов оплаты. Меньшее значени подымает модуль в вверх списка

### Статус заказа после оплаты не меняется

Если после оплаты статус заказа не меняется, то вероятно проблема в конфигурации PHP на вашем сервере.

Попробуйте добавить в `.htaccess` файл, находящийся в корневой директории вашего OpenCart, следующий код

```
RewriteEngine on
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization},L]
```
и протестируйте еще раз оплату через ЕРИП с тестовым кодом услуги.

### Примечания

Разработано и протестировано с OpenCart v.2.0.1.1

Требуется PHP 5+

### Проблемы при установке

Если ваша хостинговая компания не предоставляет FTP доступ, то вам будет необходимо установить
[этот модуль](http://www.opencart.com/index.php?route=extension/extension/info&extension_id=18892) прежде чем устанавливать данный модуль оплаты.

Другой вариант - это закачать на сервер содержимое папки _upload_ в корень директoрии, где устанвлена OpenCart

### Тестовые данные

Вы можете использовать следующие данные, чтобы настроить способ оплаты в
тестовом режиме:

  * Идентификационный номер магазина __363__
  * Секретный ключ магазина __4f585d2709776e53d080f36872fd1b63b700733e7624dfcadd057296daa37df6__
  * Домен API __api.bepaid.by__
  * Код услуги ЕРИП __99999999__

В случае успешного взаимодействия интернет-магазина и bePaid.by покупателю будет показана инструкция как оплатить заказ через систему Расчёт (ЕРИП) и bePaid.by через 10 секунд пришлёт подтверждение об успешной оплате и OpenCart переведёт заказ в заданный статус успешного платежа.

## Нашли ошибку или у вас есть предложение по улучшению модуля?

Создайте [запрос](https://github.com/beGateway/opencart-erip-payment-module/issues/new)

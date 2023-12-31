# 1. Описание
План тестирования веб-сервиса, который предлагает купить тур по определённой цене двумя способами:
1. Обычная оплата по дебетовой карте.
2. Уникальная технология: выдача кредита по данным банковской карты.
# 2. Тестовые сценарии
## Сценарии тестирования кнопок переключения форм оплаты
* __Test Case 0:__ Успешная смена форм оплаты с помощью соответствующих кнопок
## Положительные сценарии тестирования UI - Оплата дебетовой картой
* __Test Case 1:__ Успешная покупка тура с помощью действительной дебетовой карты
## Негативные сценарии тестирования UI - Оплата дебетовой картой
* __Test Case 2:__ Неудачная покупка тура с неверным номером дебетовой карты
* __Test Case 3:__ Неудачная покупка тура с просроченной дебетовой картой
* __Test Case 4:__ Неудачная покупка тура с неправильным именем владельца
* __Test Case 5:__ Неудачная покупка тура с неправильным CVV
## Положительные сценарии тестирования UI - Оплата кредитной картой
* __Test Case 6:__ Успешная покупка тура с помощью действительной кредитной карты
## Негативные сценарии тестирования UI - Оплата кредитной картой
* __Test Case 7:__ Неудачная покупка тура с неверным номером кредитной карты
* __Test Case 8:__ Неудачная покупка тура с просроченной кредитной картой
* __Test Case 9:__ Неудачная покупка тура с неправильным именем владельца
* __Test Case 10:__ Неудачная покупка тура с неправильным CVV
## Тестовые сценарии проверки базы данных
* __Test Case 11:__ Проверка данных об успешной покупке тура в базе данных
* __Test Case 12:__ Проверка отсутствия неверных данных в базе данных
# 3. Перечень используемых инструментов
1. __Selenium WebDriver:__ Используется для автоматизации тестов пользовательского интерфейса для взаимодействия с веб-страницами приложения, заполнения форм и проверки элементов.
2. __Selenide:__ это лаконичная и удобная в использовании платформа автоматизации тестирования веб-интерфейса, построенная на Selenium WebDriver, предлагающая свободный API, неявные ожидания, простые средства определения местоположения и встроенные утверждения.
3. __Java:__ язык программирования для написания тестовых сценариев благодаря его широкой поддержке и объектно-ориентированным возможностям.
4. __Gradle:__ Инструмент автоматизации сборки для управления зависимостями проекта и выполнения тестов.
5. __MySQL:__ Для настройки тестовой базы данных мы будем использовать MySQL, который широко используется, прост в управлении и широко поддерживается.
# 4. Возможные риски при автоматизации
1. __Изменения в приложении:__ Если приложение претерпевает значительные изменения, это может привести к сбоям скрипта, и потребуется поддержка тестирования.
2. __Изменения пользовательского интерфейса:__ Любые изменения в пользовательском интерфейсе, такие как указатели элементов или структура, могут нарушить тесты пользовательского интерфейса.
3. __Подключение к базе данных:__ Если учетные данные базы данных или URL-адрес в файле application.properties неверны, тесты, связанные с базой данных, завершатся неудачей.
4. __Зависимость от внешнего сервиса:__ Приложение зависит от внешних сервисов, таких как credit gate и payment gate. Если эти службы не работают или меняют свои URL-адреса, это может привести к сбоям тестирования.
5. __Управление тестовыми данными:__ С тестовыми данными следует обращаться осторожно, чтобы обеспечить согласованность и надежность результатов тестирования.
6. __Общие возможные проблемы:__ Тесты пользовательского интерфейса могут не проходить из-за проблем с сетью, несоответствий в браузере или проблем с производительностью приложений.
# 5. Тестирование базы данных
- После каждого позитивного сценария (Test Case 1 и Test Case 6) проверяем запись о покупке в базе данных MySQL
- Для сценариев с негативными сценариями UI (Test Case 2-5 и Test Case 7-10) убеждаемся, что в базе данных не хранятся неверные данные.
- Очищаем тестовые данные, чтобы убедиться, что база данных остается согласованной для последующих запусков тестов.
# 6. План выполнения
1. Расставить приоритеты в Test Case на основе критических функциональных возможностей и потенциальных рисков
2. Настроить тестовые среды для тестирования пользовательского интерфейса
3. Провести тестирование в соответствие с планом
4. Сделать автоматизацию тестовых сценариев для одной из форм
5. Создать и проанализировать отчеты о тестировании, создать issue с выявленными багами
6. Сделать выводы о проведенном тестировании, его автоматизации, дать общие рекомендации по работе веб-сервиса
### Дополнительно
Сервис обрабатывает только специальные номера карт, которые даны для тестирования:
APPROVED карта — 1111 2222 3333 4444;
DECLINED карта — 5555 6666 7777 8888.
Остальные данные карт могут быть любыми, но учитывайте, что год не должен быть прошлым, CVC состоит из трёх цифр и т. д.

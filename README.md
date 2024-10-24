# Задача построения карты маршрутов грузовых перевозок

Для большой компании, занимающейся грузоперевозками, необходимо разработать консольное приложение, которое сможет рассчитать самый длинный/короткий маршрут среди имеющихся, найти все маршруты для конкретного водителя.

В качестве входных данных выступают записи всех перевозок, осуществляемые водителями между городами.
Каждая запись соответствует одной поездке водителя из точки A в точку B.

---

### Входные условия
 
#### 1. Данные

Каждая запись представлена набором полей

    TripID;VehicleID;DriverID;Departure;Destination;Distance;ScheduledDate
Данные о всех маршрутах представлены в файле **_all-routes.csv_**.

#### 2. Описание данных

**TripID** - идентификатор поездки между точкой A и B. Тип данных - GUID. Всегда заполнено.

**VehicleID** - идентификатор транспортного средства. Всего в компании насчитывается 300 машин. Идентиифкатор лежит в диапазоне от 1 до 300. Всегда заполнено.

**DriverID** - идентификатор водителя. Всего в компании 250 водителей. Идентификатор лежит в диапазоне 1-250. Всегда заполнено.

**Departure** - точка отправления A. Точка представлена названием города, откуда осуществлялась поездка. Поле может быть не заполнено (сбой в данных).

**Destination** - точка назначения B. Точка представлена названием города, где поездка была завершена. Поле может быть не заполнено (сбой в данных).

**Distance** - дистанция между точкой отправления A и точкой назначения B. Представлена целым числом от 100 км до 1000 км. Может иметь отрицательные значения (сбой в данных).

**ScheduledDate** - дата поездки. Представлена в формате 'yyyy-MM-dd'. Всегда заполнено.

#### 3. Планируемое поведение консольного приложения

При запуске приложения все записи должны быть провалидированы и ошибочные данные записаны построчно в файл **_routes-error.csv_**.

При запуске приложения в терминал должно быть выведено приветствие:

    Добрый день! В период с <Дата самого первого маршрута (dd.MM.yyyy)> по <Дата самого последнего маршрута (dd.MM.yyyy)> было осуществлено маршрутов: <Количество маршрутов>.
    Выберите необходимое действие:
    1 - Расчет пробега выбранного транспортного средства.
    2 - Вывод всех поездок, совершенных за определенный период.
    3 - Ожидаемое расстояние между точкой А и точкой B.
    4 - Выход

##### Опция 1.
    
Необходимо ввести идентификатор транспортного средства, после этого в терминале должен отобразиться пробег выбранного транспортного средства в километрах:

    Траспортное средство с идентификатором <VehicleId> совершило <Количество поездок> с общим расстоянием <Расстояние> км.

##### Опция 2.

При выборе второго варианта пользователю предлагается ввести диапазон дат в формате 'dd.MM.yyyy-dd.MM.yyyy'.

**Важно!** При вводе неправильного диапазона (дата окончания > дата начала или введенный формат отличается от требуемого) необходимо вывести сообщение:

    Преиод введен неправильно. Пожалуйста, введите период в формате 'dd.MM.yyyy-dd.MM.yyyy'.

После правильно введенного периода в ответ пользователю выводятся все поездки в формате:

    TripID;VehicleID;DriverID;Departure;Destination;Distance;ScheduledDate

##### Опция 3.

При выборе данной опции пользователю предлагается ввести точки отправления A и точку назначения B в формате 'New York;Atlanta'.

    Введите точку отправления А и точку назначения в формате 'New York: Atlanta'

После успешного ввода, пользователю выводится сообщение с рассчитанным расстоянием между выбранными точками:

    Расстояние между точкой отправления New York и точкой назначения Atlanta составляет <Расстояние между точками> км.

**Важно!** Расстояние должно выводится между **_любыми_** двумя точками, которые представлены в данных и между ними есть свзяь. Если же связи в данных между точками нет, или _точка отправления_ == _точке назначения_ то выводить цифру 0 км.

##### Опция 4.

Пользователь, выбрав 4-ую оцпию завершает работу с приложением. Приложение останавливается.
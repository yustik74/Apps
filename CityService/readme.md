<br />
<p align="center">
  <a href="https://www.tk-nav.ru/">
    <img src="img/logo_TK_big_ru.png" alt="Logo" width="133" height="29">
  </a>

<h3 align="center">Приложение для отображения городской коммунальной техники</h3>


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Содержание</h2></summary>
  <ol>
    <li>
      <a href="#о-проекте">О проекте</a>
    </li>
    <li>
      <a href="#перед-началом">Перед началом</a>
      <ul>
        <li><a href="#установка">Установка</a></li>
      </ul>
    </li>
    <li><a href="#использование">Использование</a></li>
    <li><a href="#контакты">Контакты</a></li>
  </ol>
</details>

## О проекте

![Скриншот](img/screen.png)

Данное приложение позволяет в онлайн-режиме наблюдать за группами транспорта на карте.

## Перед началом

Для работы примера нужен доступ к АвтоГРАФ.Web под учетной записью администратора.

### Установка

1. Скопируйте папку с App в AppTemplates

2. Откройте модуль **Apps**

   ![Apps windows](img/menu-apps.png)

2. Добавьте новый App, выбрав шаблон **CityService** (Шаблон - название директории, в которой находится приложение).
   Если требуется, добавьте параметры. Все недобавленные параметры будут использоваться со значением по умолчанию.
   Описание возможных параметров:
    * **LogoUrl**
   > путь к логотипу компании
    * **RefreshTime**
   > интервал обновления положения автомобилей в секундах
    * **ClusterSize**
   > размер зоны в пикселях для группировки автомобилей
    * **OutdatedTimeout**
   > время в минутах, по истечению которого автомобиль считается **offline** и пропадает из отображения
    * **DefaultCoordinates**
   > координаты карты по умолчанию в формате [xx.xxx, yy.yyy]
    * **HideForm**
   > флаг отображения информационной формы, может принимать значения **true**(не отображать) или **false**(отображать форму)
    * **HideOrgs**
   > флаг отображения полей выбора организации, может принимать значения **true**(не отображать) или **false**(отображать)
    * **HideStats**
   > флаг отображения полей статистики, может принимать значения **true**(не отображать) или **false**(отображать)
    * **DrawLabel**
   > флаг для включения или отключения строки с информацией об автомобиле, может принимать значения **true**(не отображать) или **false**(отображать)
    * **CursorBackgroundPath**
   > путь к вращаемой подложке курсора, кроме ссылки на файл может принимать значения **none**(не отображать), **auto**(по умолчанию)
    * **CursorIconPath**
   > путь к иконке курсора, кроме ссылки на файл может принимать значения **none**(не отображать), **auto**(по умолчанию)
    * **IconBackgroundPath**
   > путь к подложке иконки, кроме ссылки на файл может принимать значения **none**(не отображать), **auto**(по умолчанию)
    * **IconPath**
   > путь к иконке, кроме ссылки на файл может принимать значения **none**(не отображать), **auto**(по умолчанию)

![Меню](img/adding-app.png)

4. Перезагрузите страницу и включите App в меню

   ![App в меню](img/app-in-menu.png)

   или на панели инструментов.

   ![App на панели инструментов](img/app-on-panel.png)

5. Для того, чтобы указать, какие объекты должны отображаться на карте, а какие - нет, предусмотрен параметр
   **AppCityServiceVisible** типа bool (**true**/**false**). Объекты со значение параметра **AppCityServiceVisible**
   = **true** - будут отображаться на карте. Если параметр **AppCityServiceVisible** у объекта отсутствует - объект
   будет всегда отображаться на карте. Вы можете сконструировать любое требуемое выражение для параметра **
   AppCityServiceVisible** в дизайнере параметров или в реестре параметров схемы.

   Пример:
   Требуется задать список геозон, при нахождении которых нужно исключить автомобиль из показа на карте (например,
   гараж, база, ремонтная мастерская и т.п.).

   Зайдите в дизайнер параметров объекта, создайте новый слой геозон и выберите из списка все необходимые геозоны для
   исключения.

   ![Добавление слоя Геозона](img/add-geofences.png)

   Перейдите на закладку "Список параметров", добавьте новый параметр с именем **AppCityServiceVisible**, значением
   колонки Список "Финальные" и выражением вида **OutOfGFx**, где **x** - порядковый номер слоя. В указанном примере
   слой "Геозона простоя" второй по счету, поэтому используется выражение OutOfGF2.

   ![Добавление параметра "В геозоне"](img/boolean-parameter.png)

   Вы можете задать любое выражение в параметре **AppCityServiceVisible**, используя произвольные условия для
   выставления флага отображения автомобиля.

В случае отсутствия параметра **AppCityServiceVisible** автомобиль будет отображаться в любой геозоне.

6. Для интеграции на сайт воспользуйтесь <a href="integration/readme.md">инструкцией</a>.

<!-- USAGE EXAMPLES -->

## Использование

Выберите группу (организацию) и подгруппу (подразделение) автомобилей, все активные автомобили из группы будут
отображены на карте.

<!-- CONTACT -->

## Контакты

E-mail: <a href="mailto:mail@tk-chel.ru">mail@tk-chel.ru</a>
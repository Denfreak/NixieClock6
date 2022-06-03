Видео
<a href="https://youtu.be/4lqGsXRB4vA" target="_blank"><img src="https://sun9-29.userapi.com/impg/cvYoLpUpgVMc0LABgj05KSxFlFYCi1RnLahJSg/aorpCGpu2Qs.jpg?size=1521x889&quality=96&proxy=1&sign=aeabadccb992afac0decc25e86ff368e" alt="Видео"></a>

![PROJECT_PHOTO](https://sun9-21.userapi.com/bWwjce5PnHbB8VanPXkxXA7Pkjoxh6WSA_MJUg/TnIqux89CcI.jpg)
# Часы на газоразрядных индикаторах "ИН" и Arduino
 Здесь Вы можете скачать прошивку и Gerber-файлы для заказа плат.
 Также Вы найдете описание проекта, фотографии, видео, инструкции и контакты для покупки печатных плат.
 Плата электроники (нижняя) общая для проекта COVID-19
 Плата для ламп (верхняя) на выбор:
 Вариант А. 6шт ИН-14;
 Вариант B. 6шт ИН-12;
 Вариант C. 4шт ИН-14 + 2шт ИН-16 (секунды);
 Вариант D. 4шт ИН-12 + 2шт ИН-2 (секунды);
 Вариант E. 6шт ИН-14 + ИН-19А
 Вариант F. 4шт ИН-14 + ИН-19А + 2шт ИН-16 (секунды)
* [Описание проекта](#chapter-0)
* [Что здесь добавлено](#chapter-1)
* [Папки проекта](#chapter-2)
* [Схемы подключения](#chapter-3)
* [Радиодетали](#chapter-4)
* [Как скачать и прошить](#chapter-5)
* [Настройки в коде](#chapter-6)
* [FAQ от AlexGyver](#chapter-7)
* [ОЧЕНЬ ВАЖНАЯ информация!](#chapter-8)
* [Часы "ЛАДУШКИ"v2 на 4 лампах](#chapter-9)
* [Купить](#chapter-10)
* [Фотографии](#chapter-11)
* [Работа над ошибками](#chapter-12)

[![AlexGyver YouTube](http://alexgyver.ru/git_banner.jpg)](https://www.youtube.com/channel/UCgtAOyEQdAyjvm9ATCi_Aig?sub_confirmation=1)

<a id="chapter-0"></a>
## Описание проекта
Часы на советских газоразрядных индикаторах под управлением платформы Arduino. 
Модифицированно на базе проекта AlexGyver
Страница исходного проекта AlexGyver на сайте: https://alexgyver.ru/nixieclock_v2/
  
Дополненные часы имеют две дополнительные лампы секунд, RGB подсветку, датичик температуры, давления, влажности и будильник. 
- Управление:
  - При отображении часов:
    - М (двойной клик) - войти в режим настроек времени;
    - М (удержание) - войти в режим настроек будильника;
    - "минус" (кратко) - переключает режимы подсветки ламп;
    - "минус" (удержание) - включает/отключает "глюки";
    - "плюс" (кратко) - переключает режимы перелистывания цифр;
    - сенсор (кратко) - показать температуру, давление, влажность, установленное время будильника
              (только если будильник включен) и вернуться в режим отображения часов;
    - (удержание) - то же, что (кратко).
    
  - При срабатывании будильника (играет мелодия):
    - сенсор  (кратко) - сброс сигнала, будильник остаётся включенным;
    - сенсор  (удержание) - сброс сигнала, будильник остаётся включенным.
    
  - При демонстрации температуры, влажности, давлении, времени будильника:
    - сенсор  (кратко) - переключиться на следующий параметр (давление, влажность, установленное
              время будильника, отображение часов);
    - (удержание) - вернуться в режим отображения часов;
    - М (удержание) - зафиксировать отображение выбранного показания (значения будут изменяться)
    
  - При настройке времени:
    - М (кратко) - переключение между установкой часов и минут;
    - (удержание) - сброс текущей группы разрядов в 00;
    - "минус" (кратко) - уменьшение значения;
    - (удержание) - уменьшение значения на 5;
    - "плюс"  (кратко) - увеличение значения;
    - (удержание) - уведичение значения на 5;
    - сенсор  (кратко) - выход с сохранением установок;
    - сенсор  (удержание) - выход с возвратом к прежнему значению.
    
  - При настройке будильника:
    - М (кратко) - переключение между установкой часов и минут;
    - М (удержание) - сброс текущей группы разрядов в 00;
    - "минус" (кратко) - уменьшение значения;
    - "минус" (удержание) - уменьшение значения на 5;
    - "плюс"  (кратко) - увеличение значения;
    - "плюс"  (удержание) - уведичение значения на 5;
    - сенсор  (кратко) - выход с сохранением установок;
    - сенсор  (удержание) - включение/выключение будильника.
    
  - Эффекты В РЕЖИМЕ ЧАСОВ:
    - Подсветка (циклически изменяется цвет: красный,  зелёный, синий):
      - Дыхание;
      - Постоянное свечение;
      - Отключена.
    - Смена цифр (при смене на короткое время отображается номер эффекта во всех разрядах):
      - (0) Без эффекта;
      - (1) Плавное угасание;
      - (2) Перемотка по порядку числа;
      - (3) Перемотка по катодам;
      - (4) Поезд;
      - (5) Резинка.
    - Поведение секундной точки зависит от того, включен ли будильник? устанавливается параметрами:
      - DOT_IN_TIME - когда будильник выключен;
      - DOT_IN_ALARM - когда будильник включен.
      Выбор поведения точки можно осуществлять из следующих величин:
      - DM_NULL, (0) точка постоянно выключена;
      - DM_ONCE, (1) точка моргает один раз в секунду (штатно);
      - DM_HALF, (2) точка изменяет яркость раз в секунду;
      - DM_TWICE,(3) точка моргает два раза в секунду;
      - DM_THREE,(4) точка моргает три раза в секунду;
      - DM_FULL, (5) точка постоянно включена 

<a id="chapter-1"></a>
## Что здесь добавлено
Мы подписчики AlexGyver, я Евгений "adm503" и Владислав "poty"
совместно внесли изменения в проект AlexGyver  NixieClock_v2.
Задачи которые мы преследовали:
1. 6 ламп - часы, минуты, секунды.
2. Возможность устанавливать верхнюю плату от прокта AlexGyver NixieClock_v2.
Да, это чистой воды прихоть. Зато я могу перекрестно тестировать платы разных проектов.
3. Сделать нижнюю плату той-же ширины что и верхняя.
4. Добавить датчик температуры, влажности и давления BME280.
5. Постоянная синхронизация тактов времени с модуля RTC.
6. Допилить будильник.
7. Сделать плату универсальной, пригодной и для светодиодной мерцающей разделительной точки и для неоновой.
8. Добавить сенсорную кнопку для выключения будильника.
9. Контроль высокого напряжения и самостабилизация.
10. Ну и конечно же, самореализация. Ах какое удовольствие делать что-то прекрасное.
Особенно в этот сумасшедший 2020 год. Пускай версия нашей платы 2020 года, на память об этом безумии, будет называться "COVID 2019".
Будем смотреть и вздрагивать.<br>

В программе:
 - добавлены секунды;
  - тактирование переведено на SQW-выход DS3231 (с прерыванием), прерывание таймера оригинального скетча (таймер 2) не используется;
  - таймер 0 и таймер 2 используются на одинаковых частотах = таймер 0, для управления тремя линиями светодиодов (PWM);
  - таймер 1 используется на частоте 32кГц для PWM генератора DC/DC и яркости неонки;
  - контроль выходного высокого напряжения через делитель на вывод А6;
  - подключен будильник, добавлено меню установки будильника и режим просмотра установки будильника;
  - мелодия будильника реализована на программной реализации мелодии в прерывании SQW;
  - индикация включения будильника реализована через разные режимы моргания секундной точки;
  - часть эффектов переключения цифр срабатывает только при смене минут;
  - исправлен показ номера эффекта при переключении;
  - подключение BME-280, три режима для отображения результатов измерений.

<a id="chapter-2"></a>
## Папки
- **libraries** - библиотеки проекта. Заменить имеющиеся версии (в этом проекте внешних библиотек нет)
- **firmware** - прошивки для Arduino
	- NixieClock_PE_v2.0.17 - версия без поддержки платы "Ладушки"
	- NixieClock_PE_v2.1.0 - версия для плат "COVID-19" и "Ладушки"
	- NixieClock_PE_A_v2.0.1 - версия для <a href="https://youtu.be/yetfYi0qS0o" target="_blank">платы "COVID-19" с 7-ю лампами (+ ИН-19А)</a>
- **schemes** - схемы подключения компонентов

<a id="chapter-3"></a>
## Схемы
- ВНИМАНИЕ! В модуле RTC DS3231S mini Pi ОБЯЗАТЕЛЬНО соединить 3 контакт микросхемы с NC пином модуля
- COVID 2019 v2 - плата под ИН-14/ИН-16 + ИН-12/ИН-2 с RGB подсветкй
- COVID 2019 v2 x6 - плата под ИН-14 6шт + ИН-12 6шт с RGB подсветкй (По личной просьбе nick_e)
- COVID 2019 v2 WS - плата под ИН-14/ИН-16 + ИН-12/ИН-2 с подсветкой на светодиодной ленте WS2812B  

<a id="chapter-4"></a>
## Радиодетали
- <a href="https://aliexpress.ru/item/4000587268145.html?spm=a2g2w.detail.0.0.67115eefC6kyzz" target="_blank">Arduino NANO 328p</a> -1шт. (200р.)
- <a href="https://aliexpress.ru/item/1005003264838795.html?algo_expid=1027afeb-6834-477a-88e4-04eca2f8b2bc-14&algo_pvid=1027afeb-6834-477a-88e4-04eca2f8b2bc&btsid=0b8b034e16353107493278362e9a7c&sku_id=12000024921801089&spm=a2g0o.productlist.0.0.6ead418bjhlCO9&ws_ab_test=searchweb0_0%2Csearchweb201602_%2Csearchweb201603_" target="_blank">DS3231S</a> микро -1шт. (120р.) Осторожно: DS3231M не подходит!
- <a href="https://aliexpress.ru/item/32849462236.html?ad_pvid=202110262204485391989560616350003230505_2&algo_expid=6af418a2-1f95-4f11-978e-f0a60f22e8d3-1&algo_pvid=6af418a2-1f95-4f11-978e-f0a60f22e8d3&btsid=0b8b158f16353110882768522ea6c3&item_id=32849462236&s=p&sku_id=10000005620984903&spm=a2g0o.productlist.0.0.2af95bafmZa1Ov&ws_ab_test=searchweb0_0%2Csearchweb201602_%2Csearchweb201603_" target="_blank">BME280</a> цифровой датчик температуры, влажности и атмосферного давления. -1шт. (650р.) Рекомендуется вынести на гибком шлейфе на край корпуса для точных измерений температуры.
- Гнёзда на плату PBS-40 (DS1023-1x40) -1шт.
- Рейка штыревая PLS-40 (DS1021-1x40) -1шт.
- Конденсатор электролитический 470мкФ 6.3V -2шт.
- Конденсатор электролитический 4,7 мкФ 350V -1шт.
- Конденсатор 0.1 мкФ 400в.
- Индуктивность 220 мкГн (uH) -1шт.
- Диод HER106 (BYV26C) -1шт.
- Параллельно резистору 100 Ом в затворе поставить импульсный диод катодом в сторону Ардуино (например кд521)
- Транзистор IRF840PBF -1шт.
- Оптопара TLP627(F) DIP-4 -7шт.
- Дешифратор К155ИД1 -1шт.
- RGB cветодиоды 5 мм (общий катод) -6шт.
- Резисторы 0.25 Вт для версии с неоновыми точками:
	- 51 Ом - 1шт.; 100 Ом - 3шт.; 470 Ом - 1шт; 1к - 1шт.; 5,1к - 2шт.; 10к - 3шт.; 680к - 1шт.; 3к - 1шт.; 33к - 1шт.
	- 330к - 2шт.
- Резисторы 0.25 Вт для версии со светодиодными точками:
	- 51 Ом - 1шт.; 100 Ом - 3шт.; 470 Ом - 1шт; 1к - 1шт.; 5,1к - 2шт.; 10к - 3шт.; 680к - 1шт.; 3к - 1шт.; 33к - 1шт.
	- 150 Ом -2шт.
- Транзистор (для звука) любой n-p-n -1шт.
- Разъем питания -1шт.<br>
В проекте заложена возможность установки на плату USB разъема (5 вариантов на выбор) или гнезда питания с понижающем модулем
	 - <a href="https://ae01.alicdn.com/kf/Hb0bd5728c4684785a299a9bf75fee4547.jpg" target="_blank">USB: Type C 3,1 SMD DIP 6pin</a>; <a href="https://lcsc.com/product-detail/USB-Connectors_Jing-Extension-of-the-Electronic-Co-C46391_C46391.html" target="_blank">Mini USB 5pin</a>; <a href="https://lcsc.com/product-detail/USB-Connectors_SHOU-HAN-MICRO5-9mmusb_C393940.html" target="_blank">Micro USB Type B SMD DIP</a>; <a href="https://ae01.alicdn.com/kf/HTB1Gz1yacvrK1Rjy0Feq6ATmVXaK.jpg" target="_blank"> USB 2,0 4PIN Type A</a> Гнездовой разъем G54; <a href="https://ae01.alicdn.com/kf/HTB1cX7MX8Cw3KVjSZR0q6zcUpXae.jpg" target="_blank"> USB 2,0 Type A</a> Гнездовой разъем 5PIN DIP вертикальный.
	 - <a href="https://ae01.alicdn.com/kf/H2726b55fa9f34ed6b13cb8acaa94c2cfi.jpg" target="_blank">QS-1205CME-3A</a> Понижающий модуль (DC-DC 12-24 В до 5 В 3A)
- Кнопки тактовые 6х6 боковые (1-1825027-7; 1825027-5; 1-1825027-1; 1825027-5; 1825027-5; KLS7-TS6606-5.0-180) -3шт.
- <a href="https://aliexpress.ru/item/1005001989233616.html?sku_id=12000018329752752&spm=a2g2w.productlist.0.0.6cee5831rX1xuO" target="_blank">TTP223</a> модуль сенсорной кнопки -1шт. (90р.\10шт.)

<a id="chapter-5"></a>
## Как скачать и прошить
* [Первые шаги с Arduino](http://alexgyver.ru/arduino-first/) - ультра подробная статья по началу работы с Ардуино, ознакомиться первым делом!
* Скачать архив с проектом
> На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Code**, вот её жми, там будет **Download ZIP**
* Установить библиотеки в  
`C:\Program Files (x86)\Arduino\libraries\` (Windows x64)  
`C:\Program Files\Arduino\libraries\` (Windows x86)
* **Подключить внешнее питание 5 Вольт**
* Подключить Ардуино к компьютеру
* Запустить файл прошивки (который имеет расширение .ino)
* Настроить IDE (COM порт, модель Arduino, как в статье выше)
* Настроить что нужно по проекту
* Нажать загрузить
* Пользоваться (вздрагивать) 

<a id="chapter-6"></a>
## Настройки в коде
    // ************************** НАСТРОЙКИ **************************
    #define BOARD_TYPE 4 (Поменяйте цифру в зависимости от версии часов)
    // тип платы часов:
    // 0 - IN-12 turned (индикаторы стоят правильно)
    // 1 - IN-12 (индикаторы перевёрнуты)
    // 2 - IN-14 (обычная и neon dot)
    // 3 - COVID 2019 (проект ADM503 и poty)
    // 4 - "Ладушки" ИН-12
    // 5 - "Ладушки" ИН-14
    
    // ************************** НАСТРОЙКИ **************************
    BRIGHT 100          // яркость цифр дневная, %
    BRIGHT_N 20         // яркость ночная, %
    NIGHT_START 23      // час перехода на ночную подсветку (BRIGHT_N)
    NIGHT_END 7         // час перехода на дневную подсветку (BRIGHT)
    FREQ 900            // частота писка будильника

    CLOCK_TIME 10       // время (с), которое отображаются часы
    TEMP_TIME 5         // время (с), которое отображается температура и влажность
    ALM_TIMEOUT 30      // таймаут будильника

    // *********************** ДЛЯ РАЗРАБОТЧИКОВ ***********************
    BURN_TIME 200       // период обхода в режиме очистки
    REDRAW_TIME 3000    // время цикла одной цифры, мс
    ON_TIME 2200        // время включенности одной цифры, мс
    
*Настройки высокого напряжения во вкладке data (для опытных)
	
<a id="chapter-7"></a>
## FAQ от AlexGyver
### Основные вопросы
В: Как скачать с этого грёбаного сайта?  
О: На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Code**, вот её жми, там будет **Download ZIP**

В: Скачался какой то файл .zip, куда его теперь?  
О: Это архив. Можно открыть стандартными средствами Windows, но думаю у всех на компьютере установлен WinRAR, архив нужно правой кнопкой и извлечь.

В: Я совсем новичок! Что мне делать с Ардуиной, где взять все программы?  
О: Читай и смотри видос http://alexgyver.ru/arduino-first/

В: Вылетает ошибка загрузки / компиляции!
О: Читай тут: https://alexgyver.ru/arduino-first/#step-5

<a id="chapter-8"></a>
## ОЧЕНЬ ВАЖНАЯ информация!
ВНИМАНИЕ!<br> 
1. В модуле RTC DS3231S mini Pi обязательно соединить 3 контакт микросхемы с NC пином модуля.<br>
![PROJECT_PHOTO](https://sun9-61.userapi.com/impg/DjIXvA39iBTszeVjRUofA8XiRuRAfazwt0DAWQ/rRwPlqKjQL0.jpg?size=138x121&quality=96&sign=6da09cbc0506c29aee459f97345ee8fc&type=album)<br>
Без перемычки не будет высокого напряжения.<br>
2. Модуль RTC DS3231M не подходит! Нужно ставить DS3231S. А лучше ставить модуль RTC DS3231SN.<br>
Если у вас горит всего одна лампа, например пятая, а через некоторое время пятая погасает и зажигается шестая, значит у вас стоит модуль RTC DS3231M не зависимо от той маркировки что нанесли на микросхему "добрые" китайцы. <br>

Если у Вас не появилось высокое напряжение на конденсаторе или горит только одна лампа, значит скорее всего Вы не выполнили эти требования.
<a id="chapter-9"></a>
## P.S. А вот вам часы "ЛАДУШКИ"v2 на 4 лампах под прошивку poty
Видео
<a href="https://youtu.be/8mwN5G242v4" target="_blank"><img src="https://sun9-7.userapi.com/impg/7Xobo-Spw0Qx71dley2CyZFXO8aHlWC12OrtKA/k3jESm_vkdA.jpg?size=967x797&quality=96&sign=f16734e38cd9f70bf9c18e252f35e872&type=album" alt="Видео"></a><br>
В этих часах всё как в больших, но без секундных ламп.<br>
Размеры плат как у Алекса, по разъемам совместимы.<br>
Прошивка подходит начиная с NixieClock_PE_v2.1.0

<a id="chapter-10"></a>
## Купить
Если Вы желаете приеобрести готовые платы, комплекты "плата+детали+лампы" или готовые часы, пишите в телеграм @adm503

<a id="chapter-11"></a>
## Фотографии
<a href="https://github.com/adm503/images/blob/main/README.md"> Фотографии тут</a>

<a id="chapter-12"></a>
## Работа над ошибками
Частенько со мной связываются по телеграму (@adm503) люди и просят помочь с проблемами, возникшеми при пусконаладке наших часов.<br>
Даже говорили что эти часы сложно запускать. На самом деле, у меня накопилась статистика. Ничего сложного нет, их влёгкую собирают люди еле умеющие паять. <br>
Слухи пошли из-за того что иногда китайцы продают модуль точного времени DS3231M с маркировкой DS3231S, а в наших часах это кретично. Вторая проблема возникла у покупетелей плат "Ладушки" в Киеве летом 2021 года. Человек заказал у китайцев платы "Ладушки" в момент когда я проводил правки. Приношу свои извинения, я не знал что мои платы так популярны и правил прямо в открытом проекте. В итоге вышли в продажу (штучно) платы "Ладушки" v2 с двума КЗ. Ошибки исправлены в версии "Ладушки" v2.1.<br>
Далее буду рассказывать о том с чем сталкивались люди и как проблемы решились:<br>
1. "Ладушки" v2. На сколько мне известно, таких плат выпущено всего 10шт. Ошибка оперативно исправлена.<br>
Проблема1: Не горит первая лампа потому что с D8 сигнал не доходит до оптопары А1 из-за КЗ на землю металлизированным отверстием.<br>
![PROJECT_PHOTO](https://github.com/adm503/images/blob/main/NixieClock/%D0%9B%D0%B0%D0%B4%D1%83%D1%88%D0%BA%D0%B8%20v2/%D0%9A%D0%97%20D8.jpg)<br>
Решение: Удаляем метализацию из отверстия<br>
Проблема2: Не работают две кнопки управления из-за КЗ А7 с D9. <br>
![PROJECT_PHOTO](https://github.com/adm503/images/blob/main/NixieClock/%D0%9B%D0%B0%D0%B4%D1%83%D1%88%D0%BA%D0%B8%20v2/%D0%907%20%D0%BA%D0%BE%D1%80%D0%BE%D1%82%D0%B8%D1%82%20%D1%81%20D9.jpg)<br>
Решение: Режем дорожки<br>
![PROJECT_PHOTO](https://github.com/adm503/images/blob/main/NixieClock/%D0%9B%D0%B0%D0%B4%D1%83%D1%88%D0%BA%D0%B8%20v2/%D1%80%D0%B5%D0%B6%D0%B5%D0%BC%20%D0%907%20-%20D9.jpg)<br>
![PROJECT_PHOTO](https://github.com/adm503/images/blob/main/NixieClock/%D0%9B%D0%B0%D0%B4%D1%83%D1%88%D0%BA%D0%B8%20v2/%D1%80%D0%B5%D0%B6%D0%B5%D0%BC%20%D0%907%20-%20D9_.jpg)<br>
Дублируем дорожку проводом<br>
![PROJECT_PHOTO](https://github.com/adm503/images/blob/main/NixieClock/%D0%9B%D0%B0%D0%B4%D1%83%D1%88%D0%BA%D0%B8%20v2/%D0%9C%D0%93%D0%A2%D0%A4%20%D0%BD%D0%B0%20%D0%907%20%D1%81%20D9.jpg)<br>
2. Проблема: Свечение лампы ярче чем у остальных и одновременно светятся 3-4 цифры.<br>
![PROJECT_PHOTO](https://github.com/adm503/images/blob/main/NixieClock/%D0%9E%D0%BF%D1%82%D0%BE%D0%BF%D0%B0%D1%80%D0%B0/IMG_20211009_125916.jpg)<br>
![PROJECT_PHOTO](https://github.com/adm503/images/blob/main/NixieClock/%D0%9E%D0%BF%D1%82%D0%BE%D0%BF%D0%B0%D1%80%D0%B0/IMG_20211009_130046.jpg)<br>
Решение: Замените оптопару на этой лампе.<br>
3. Вопрос: Возле ДС3231 нарисован проводочек со спиралькой уходящий в бесконечность отверстие посажено на 5В это для чего? (Плата COVID 2019)<br>
![PROJECT_PHOTO](https://github.com/adm503/images/blob/main/NixieClock/%D0%92%D0%BE%D0%BF%D1%80%D0%BE%D1%81%D1%8B/%D0%B4%D1%80%D0%BE%D1%81%D0%B5%D0%BB%D1%8C.jpg)<br>
Ответ: Это для дросселей разной конструкции. Для радиальных выводов - два отверстия рядом, для аксиальных - два разнесённых по плате.<br>

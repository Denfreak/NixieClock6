<a href="https://youtu.be/4lqGsXRB4vA"  target="_blank"><img src="https://sun9-29.userapi.com/impg/cvYoLpUpgVMc0LABgj05KSxFlFYCi1RnLahJSg/aorpCGpu2Qs.jpg?size=1521x889&quality=96&proxy=1&sign=aeabadccb992afac0decc25e86ff368e" alt="Видео"></a>

![PROJECT_PHOTO](https://sun9-21.userapi.com/bWwjce5PnHbB8VanPXkxXA7Pkjoxh6WSA_MJUg/TnIqux89CcI.jpg)
# Часы на газоразрядных индикаторах и Arduino
* [Описание проекта](#chapter-0)
* [Что здесь добавлено](#chapter-1)
* [Папки проекта](#chapter-2)
* [Схемы подключения](#chapter-3)
* [Радиодетали](#chapter-4)
* [Как скачать и прошить](#chapter-5)
* [FAQ](#chapter-6)

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
Будем смотреть и вздрагивать.
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
**ВНИМАНИЕ! Если это твой первый опыт работы с Arduino, читай [инструкцию](#chapter-4)**
- **libraries** - библиотеки проекта. Заменить имеющиеся версии (в этом проекте внешних библиотек нет)
- **firmware** - прошивки для Arduino
- **schemes** - схемы подключения компонентов

<a id="chapter-3"></a>
## Схемы
- Схемы на EasyEDA: https://easyeda.com/adm503/nixieclock-covid-2019-v2
- COVID 2019 v2 - плата под ИН-14/ИН-16 + ИН-12/ИН-2 с RGB подсветкй
- COVID 2019 v2 x6 - плата под ИН-14 6шт + ИН-12 6шт с RGB подсветкй (По личной просьбе nick_e)
- COVID 2019 v2 WS - плата под ИН-14/ИН-16 + ИН-12/ИН-2 с подсветкой на светодиодной ленте WS2812B  

<a id="chapter-4"></a>
## Радиодетали
- Arduino NANO 328p -1шт.
- DS3231 микро -1шт.
- BME280 цифровой датчик температуры, влажности и атмосферного давления. -1шт.
- Гнёзда на плату PBS-40 (DS1023-1x40) -1шт.
- Рейка штыревая PLS-40 (DS1021-1x40) -1шт.
- Конденсатор электролитический 4,7 мкФ 350V -1шт.
- Индуктивность 220 мкГн (uH) -1шт.
- Диод HER106 (BYV26C) -1шт.
- Параллельно резистору 100 Ом в затворе поставить импульсный диод катодом в сторону Ардуино
- Транзистор IRF840PBF -1шт.
- Оптопара TLP627(F) DIP-4 -7шт.
- Дешифратор К155ИД1 -1шт.
- RGB cветодиоды 5 мм (общий катод) -6шт.
- Резисторы 0.25 Вт для версии с неоновыми точками:
	- 100 Ом -3шт.; 470 Ом -1шт; 1к - 1шт.; 5,1к - 3шт.; 10к - 2шт.; 360к -1шт.; 3к -1шт.; 33к -1шт.
	- 330к -2шт.
- Резисторы 0.25 Вт для версии со светодиодными точками:
	- 100 Ом -3шт.; 470 Ом -1шт; 1к - 1шт.; 5,1к - 3шт.; 10к - 2шт.; 360к -1шт.; 3к -1шт.; 33к -1шт.
	- 150 Ом -2шт.
- Транзистор (для звука) любой n-p-n -1шт.
- Разъем питания -1шт.<br>
В проекте заложена возможность установки на плату USB разъема (5 вариантов на выбор) или гнезда питания с понижающем модулем
	 - <a href="https://ae01.alicdn.com/kf/Hb0bd5728c4684785a299a9bf75fee4547.jpg" target="_blank">USB: Type C 3,1 SMD DIP 6pin</a>; <a href="https://lcsc.com/product-detail/USB-Connectors_Jing-Extension-of-the-Electronic-Co-C46391_C46391.html" target="_blank">Mini USB 5pin</a>; <a href="https://lcsc.com/product-detail/USB-Connectors_SHOU-HAN-MICRO5-9mmusb_C393940.html" target="_blank">Micro USB Type B SMD DIP</a>; USB 2,0 4PIN Type A, гнездовой разъем G54; <a href="https://ae01.alicdn.com/kf/HTB1cX7MX8Cw3KVjSZR0q6zcUpXae.jpg" target="_blank"> USB 2,0 Type A гнездовой разъем 5PIN DIP вертикальный</a>.
	 - <a href="https://ae01.alicdn.com/kf/H2726b55fa9f34ed6b13cb8acaa94c2cfi.jpg" target="_blank">Понижающий модуль QS-1205CME-3A (DC-DC 12-24 В до 5 В 3A)</a>
- Кнопки тактовые 6х6 боковые (1-1825027-7; 1825027-5; 1-1825027-1; 1825027-5; 1825027-5; KLS7-TS6606-5.0-180) -3шт.
- Модуль сенсорной кнопки TTP223 -1шт.

<a id="chapter-5"></a>
## Как скачать и прошить
* [Первые шаги с Arduino](http://alexgyver.ru/arduino-first/) - ультра подробная статья по началу работы с Ардуино, ознакомиться первым делом!
* Скачать архив с проектом
> На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**
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

## Настройки в коде
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
	
<a id="chapter-6"></a>
## FAQ от AlexGyver
### Основные вопросы
В: Как скачать с этого грёбаного сайта?  
О: На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**

В: Скачался какой то файл .zip, куда его теперь?  
О: Это архив. Можно открыть стандартными средствами Windows, но думаю у всех на компьютере установлен WinRAR, архив нужно правой кнопкой и извлечь.

В: Я совсем новичок! Что мне делать с Ардуиной, где взять все программы?  
О: Читай и смотри видос http://alexgyver.ru/arduino-first/

В: Вылетает ошибка загрузки / компиляции!
О: Читай тут: https://alexgyver.ru/arduino-first/#step-5

В: Сколько стоит?  
О: Ничего не продаю.
## P.S. А вот вам часы "ЛАДУШКИ" на 4 лампах под прошивку poty
![PROJECT_PHOTO](https://sun9-45.userapi.com/impg/U2N5A5BCOv4Uk9iz5iBQKQDSGAvVGMM1ixtdlA/X3CdfCGLBJY.jpg?size=821x677&quality=96&proxy=1&sign=29db8821801edc9f435bd4a1a7e6703b)
- Схемы на EasyEDA: https://oshwlab.com/adm503/ladushki
- В этих часах всё как в больших, но без секундных ламп.
Размеры плат как у Алекса, по разъемам совместимы.

# MusicToColor

Основные принципы работы данной ЦМУ:

— Полосовая фильтрация звука и управление выбором цветомузыкальных программ выполняется программой "CMU.EXE" для ПК.

— Формирование цветомузыкальных программ выполняется модулями Arduino.

— Управление светодиодной лентой осуществляет модуль Arduino в соответствии с выбранной программой.

— Для воспроизведения музыки может использоваться любой программный плеер, например WinAmp, AIMP, ITUNES, Windows Media и т.п. или аппаратный плеер имеющий линейный выход.


Сборка цветомузыки.

  Для сборки минимального комплекта ЦМУ, с непосредственным подключением к USB ПК, нужна лишь светодиодная лента с WS2812B, arduino nano (или аналогичная), три проводника и мини USB кабель для подключения платы Arduino к одному из USB портов ПК. В данном варианте количество активных светодиодов ограничено 20 по одному на каждую цветовую полосу программы ЦМУ. Ограничение введено для предотвращения перегрузки USB порта.
  
  Простая схема включения с большим количеством светодиодов показана на рисунке "sch.jpg". Количество светодиодов при данной схеме включения ограничено мощьностью вашего источника питания, но не может превышать 256. Для снятия ограничения в 256 светодиодов вам нужно поменять в скетчах типы переменных отвечающих за количество светодиодов с uint8_t на uint16_t.
  
  Для сборки беспроводного варианта, дополнительно потребуется ещё одна плата Arduino, два радио модуля nRF24L01 с платами адаптеров, блок питания 5В на мощность соответствующую вашей ленте. Оба модуля nRF24L01 подключаются к платам Arduino идентично. Подключение осуществляется по типовой схеме к цифровым выводам D9,D10,D11,D12,D13 или другим при соответствующем изменении заголовков конфигурации в скетчах. Типовые схемы включения nRF24L01 есть в интернете. Вход управления светодиодной лентой Din (Din на ленте) заведён на цифровой выход D2 платы arduino и может быть изменён при внесении соответствующих изменений в скетч.

Условия использования.

Программа "CMU.EXE" поставляется как есть для свободного использования.
Скетчи поставляются в виде исходников и доступны для редактирования и модернизации.

Руководство пользователя.

  1. Программа "CMU.EXE" не требует специальной установки. Создайте папку с любым именем которое у вас ассоциируется с цветомузыкой и скопируйте в неё файл "CMU.EXE". Программа готова к запуску.
  2. Установите среду Arduino IDE. Скачайте и установите библиотеки Adafruit_Neopixel, RF24 и IRremote. Установка библиотек в Arduino IDE описана в интернете и не представляет сложности.
  3. Внесите изменения в скетчи под вашу ленту и вариант подключения.
  
      3.1 Установите количество светодиодов в вашей ленте
      
              #define stripLed 120 // количество светодиодов в ленте
              
      3.2 Установите номер вывода к которому подключена светодиодная лента
      
              #define stripPin 2   // выход управления светодиодной лентой
              
      3.3 Установите номера выводов к которым подключён модуль nRF24L01
      
              RF24  radio(9, 10);  // создаём объект radio для работы с библиотекой RF24, указывая номера выводов nRF24L01+ (CE, CSN)
              
  4. Собираем проект и заливаем в плату или платы в зависимости от варианта.
  5. Подключаем ленту, запускаем программу.
  6. Настройка программы.
  
      6.1 Установите последовательный COM порт к которому подключён модуль Arduino.
      
      6.2 Выберите аудио устройство с выхода которого аудио поток будет подаваться на вход цветомузыкальной программы. Для получения аудио потока с программного плеера используйте "Руководство по выбору аудио источника" из файла audioConnect.doc.
      
      6.3 Выберите одну из программ цветомузыкальной или динамической визуализации.

Руководство по модернизации скетчей



  



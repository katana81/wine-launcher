## Что это за проект?

**Wine Launcher** - Контейнер для Windows приложения на основе Wine.  

[Видео инструкция](https://www.youtube.com/watch?v=GRlebaAVWn8)  

<details>
<summary><b>Основные идеи</b></summary>
<br>

- Изолированность от системы  
- Независимость от системы  
- Для каждой игры отдельный набор из Wine и Prefix-а  

<br>
</details>

<details>
<summary><b>Возможности</b></summary>
<br>

- Отдельный **Wine\Prefix**
- Сжатие **Wine\Data** в **squash** образы для экономия места
- Обновление **Wine**
- Интеграция с **DXVK**, **MangoHud**, **VkBasalt**
- Поддержка нескольких приложений в одном порте
- Генерация патчей для префикса
- Диагностика

<br>
</details>

## Установка

1. Скачайте актуальный файл `start` (x86_64 only) со страницы [релизов](https://github.com/hitman249/wine-launcher/releases).
2. В любом месте создайте пустую директорию и переместите файл туда.
3. Сделайте файл исполняемым и запустите
   ```bash
   chmod +x ./start && ./start
   ```
4. Дождитесь инициализации.
5. Закройте лаунчер и переместите файл `start` в появившуюся папку `bin`.
6. Готово.

> В один Wine Launcher рекомендуется устанавливать только одну игру. Тогда вам будет удобней её сжимать для экономии
> места в разделе `Инструменты > Упаковка`


<details>
<summary><b>Как установить игру?</b></summary>
<br>

1. Перед установкой игры необходимо создать новый патч.  
2. Дайте патчу осмысленное имя т.к. этим словом будет называться папка в которой хранится патч.  
3. После установки игры не забудьте сохранить патч. Это пригодится вам для обновления **Wine** в будущем, чтобы 
пересоздать префикс.
4. Если необходимо установить ещё что либо повторите шаги 1-3.

> Игру нужно **обязательно** устанавливать в папку `C:\Games` ! Если требуется другая папка, её нужно переназначить в 
> настройках префикса, после чего его пересоздать.

<br>
</details>


#### Игры

Реализован простой запуск игр, но расширенный дополнительными возможностями, такими как расширенное логирование и
отображение счетчика FPS.

![Main](main.gif)


<details>
<summary><b>Обновление Wine</b></summary>
<br>

Удобный GUI для обновления Wine включает 6 репозиториев

![Main](wine.gif)

<br>
</details>

<details>
<summary><b>Настройка Prefix</b></summary>
<br>

* В настройках prefix-а присутствует автоматическая установка DXVK, MangoHud, VkBasalt.  
* Восстановление разрешения активного монитора после выхода из игры.  

![Main](prefix.gif)

<br>
</details>

<details>
<summary><b>Настройки игр</b></summary>
<br>

* Все игры должны устанавливаться в папку по умолчанию, которая задана в настройках prefix-а по умолчанию `Games`.  
* В самих играх можно задать оформление из **иконки** и **фона**.
* В настройках игр путь указывается относительно папки `Games`. Будьте внимательны!
  Пример, если путь до исполняемого файла - `C:/Games/The super game/bin/game.exe`, то в настройку игры нужно писать
    - В поле **Путь до папки**: `The super game/bin`
    - В поле **Имя файла**: `game.exe`

![Main](games.gif)

<br>
</details>

<details>
<summary><b>Патчи</b></summary>
<br>

* Всё что находится в **prefix**-е, оформляется в виде **патчей**.
* Если вы используете сторонние патчи, то чтобы их применить необходимо пересоздать **prefix**.
* Другими словами **prefix** не долгоживущая структура, пересоздавать его нужно при каждом изменении версии **wine** 
  или для накатывания сторонних патчей.

![Main](patches.gif)

<br>
</details>

<details>
<summary><b>Создание нового патча</b></summary>
<br>

При создании патча вам доступны следующие возможности:  
Перед началом обязательно прочтите **Настройки игр**  ^

  * Установка приложения(игры)
  * Установка приложения(игры) из образа диска
  * Регистрация `dll`, `ocx` библиотек
  * **Winetricks**, доступен из коробки
  * Wine Config
  * Wine File Manager
  * Wine Regedit

![Main](patch.gif)

<br>
</details>

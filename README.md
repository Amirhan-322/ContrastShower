# Contrast Shower Companion

Contrast Shower Companion – это приложение на Flutter, созданное для сопровождения процедур контрастного душа. Приложение помогает пользователю начать сеанс, отслеживать его ход, настраивать параметры сеанса и сохранять историю для последующего анализа. Проект реализован в рамках учебного задания и демонстрирует работу с кастомными анимациями, управлением состоянием через Riverpod, локальным хранением данных, а также интеграцию с аудио уведомлениями.

## Особенности

- **Анимация волн и кастомные рендер-объекты:**  
  Приложение использует виджет с кастомной анимацией волн для визуализации переходов температур (холод/горячее) и сегментированную линию для отображения параметров сеанса.  
  :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

- **Главный экран и история сеансов:**  
  Экран (homescreen.dart) показывает список ранее завершённых сеансов. Пользователь может очистить историю или запустить новый сеанс.  
  :contentReference[oaicite:2]{index=2}

- **Экран настроек:**  
  Файл *settingsscreen.dart* предоставляет пользователю возможность задать параметры предстоящего сеанса – длительность интервалов, количество интервалов, а также выбор, с какого режима (горячий или холодный) начинать. Настройки визуально подтверждаются через анимированную сегментированную линию и смену цветовой гаммы.

- **Экран активного сеанса:**  
  Файл *sessionscreen.dart* отвечает за ведение активного сеанса. Здесь реализованы:
  - Таймер с обратным отсчетом общего времени сеанса и оставшимся временем текущего интервала.
  - Плавное переключение между фазами (горячая/холодная) с визуальными переходами посредством цветовых tween-анимаций.
  - Аудио уведомления: проигрывание звуков при переключении фаз и по окончании сеанса.
  - Возможность завершения сеанса с последующим запросом оценки (рейтинг в звёздах) и сохранением истории.
  
- **Сохранение истории:**  
  Сеансы сохраняются в локальное хранилище (SharedPreferences) в виде JSON. Это позволяет восстанавливать историю даже в офлайн-режиме.  
  :contentReference[oaicite:3]{index=3}

- **Плавные переходы между экранами:**  
  Реализована навигация с использованием анимационных контроллеров (main.dart и main copy.dart) для обеспечения приятного и интуитивно понятного пользовательского опыта.  
  :contentReference[oaicite:4]{index=4} :contentReference[oaicite:5]{index=5}

## Структура проекта

- **main.dart / main copy.dart:**  
  Точка входа в приложение. Настраивается ProviderScope для управления состоянием через Riverpod, а также реализуются анимационные переходы между экранами (Home, Settings, Session).

- **custom_animation.dart:**  
  Содержит реализацию кастомной анимации волн, используемой для создания визуального эффекта перехода температур.

- **homescreen.dart:**  
  Главный экран, отображающий историю сеансов и предоставляющий возможность очистки истории или запуска нового сеанса.

- **linepainter.dart:**  
  Реализует кастомный рендер-объект для отрисовки сегментированной линии, отражающей параметры сеанса (например, начало с горячей или холодной воды).

- **storage.dart:**  
  Логика работы с локальным хранилищем: сохранение, удаление и получение сеансов, а также отображение карточек сеансов (SessionCard).

- **sessionscreen.dart:**  
  Экран активного сеанса, где реализован обратный отсчет времени, смена фаз с помощью анимаций и аудио уведомлений, а также сохранение завершённого сеанса с последующей оценкой.

- **settingsscreen.dart:**  
  Экран настроек, позволяющий пользователю задать параметры будущего сеанса (выбор начального режима, длительность интервалов, их количество). Настройки подтверждаются анимацией и визуальными эффектами.

- **Прочие файлы (например, notifier.dart):**  
  Файлы для управления состоянием и навигацией, расширяющие функциональность приложения.

## Зависимости

Проект использует следующие основные пакеты:

- [flutter_riverpod](https://pub.dev/packages/flutter_riverpod) – управление состоянием.
- [shared_preferences](https://pub.dev/packages/shared_preferences) – локальное хранение данных.
- [intl](https://pub.dev/packages/intl) – форматирование дат и времени.
- [audioplayers](https://pub.dev/packages/audioplayers) – воспроизведение аудио уведомлений.
- Flutter SDK и стандартные библиотеки Dart.

## Установка и запуск
### 1.Установить и запустить полный Flutter проект
1.1: **Клонируйте репозиторий:**

   ```bash
   git clone <URL_вашего_репозитория>
   cd <название_проекта>

1.2: **Установите зависимости:**
    ```bash
    flutter pub get

1.3: **Запустите приложение:**
    ```bash
    flutter run

### 2.Запустить .exe файл
Вы можете найти и запустить файл ".exe" на вашей машине по адресу:
"build\windows\x64\runner\Release\shower_companion.exe"


.. _installation:

Установка
------------

Введение
~~~~~~~~~~~~

Selenium Python bindings предоставляют простое API для разработки функциональных и приёмочных
тестов с использованием WebDriver Selenium. С помощью Python API для Selenium вы можете
получить доступ ко всем функциям WebDriver Selenium интуитивно понятным образом.

Selenium Python bindings предоставляют удобный API для обращения к таким WebDriver-ам Selenium
как Firefox, Internet Explorer, Chrome, Remote и т.д. Текущая поддерживаемая версия Python -
3.5 и выше.

В этой документации описана работа с API WebDriver для Selenium 2 (API Selenium 1 или Selenium RC не описаны).


Скачивание Python bindings для Selenium
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Используйте команду `pip <https://pip.pypa.io/en/latest/installing/>`_ для установки пакета selenium.
В Python 3.6 `pip` доступен в `стандартной библиотеке
<https://docs.python.org/3.6/installing/index.html>`_.  С помощью `pip` вы можете установить selenium:

  pip install selenium

Кроме того, можно использовать команду `virtualenv <http://www.virtualenv.org>`_ для создания
изолированного виртуального окружения Python. В Python 3 вы можете использовать команду `venv
<https://docs.python.org/3/library/venv.html>`_, которая практически эквивалентна
virtualenv.

Python bindings for Selenium можно скачать отсюда: `PyPI page for
selenium package <https://pypi.python.org/pypi/selenium>`_. и установить вручную.

Drivers
~~~~~~~

Для работы Selenium необходим интерфейс к выбранному браузеру. Например для Firefox требуется `geckodriver
<https://github.com/mozilla/geckodriver/releases>`_, который нужно установить
до запуска приведённых ниже примеров. Также удостоверьтесь, что путь к драйверу есть в переменной окружения `PATH`,
например в `/usr/bin` или `/usr/local/bin`.

Пропустив этот шаг вы получите ошибку:
`selenium.common.exceptions.WebDriverException: Message: 'geckodriver'
executable needs to be in PATH.`

У остальных поддерживаемых браузеров есть собственные драйверы. Ниже приведены ссылки на драйверы наиболее
популярных браузеров:

+--------------+-----------------------------------------------------------------------+
| **Chrome**:  | https://sites.google.com/a/chromium.org/chromedriver/downloads        |
+--------------+-----------------------------------------------------------------------+
| **Edge**:    | https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/ |
+--------------+-----------------------------------------------------------------------+
| **Firefox**: | https://github.com/mozilla/geckodriver/releases                       |
+--------------+-----------------------------------------------------------------------+
| **Safari**:  | https://webkit.org/blog/6900/webdriver-support-in-safari-10/          |
+--------------+-----------------------------------------------------------------------+

Для подробной информации об установке драйверов обратитесь к `официальной
документации
<https://www.selenium.dev/documentation/en/webdriver/driver_requirements/>`_.

Инструкции для пользователей Windows
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Note::

  Для установки требуется соединение с интернетом.

1. Установите Python 3.6 или старше, используя `файл MSI, доступный на странице download сайта python.org
   <http://www.python.org/download>`_.

2. Запустите командную строку (``cmd.exe``) и используйте команду ``pip``
   для установки `selenium` как показано ниже.

   ::
   
     C:\Python35\Scripts\pip.exe install selenium

Теперь вы можете запускать тестовые скрипты на Python. Например, если у вас есть скрипт Selenium,
расположенный в ``C:\my_selenium_script.py``, вы можете запустить его следующим образом:

   ::

    C:\Python35\python.exe C:\my_selenium_script.py


Скачивание сервера Selenium
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::

  **Selenium server необходим только если вы хотите использовать удалённый
  WebDriver**.  См. раздел :ref:`selenium-remote-webdriver` для более подробной информации.
  Если вы начинающий в Selenium, вы можете пропустить этот раздел и перейти к следующей части.

Selenium server - это программа на Java. Для запуска Selenium server рекомендуется использовать
 Java Runtime Environment (JRE) версии 1.6 или более новой.

Скачать Selenium server 2.x можно `на странице download сайта selenium
<http://seleniumhq.org/download/>`_.  Имя файла должно быть вида: ``selenium-server-standalone-2.x.x.jar``.
Вы всегда можете скачать последнюю версию Selenium server 2.x.

Если Java Runtime Environment (JRE) не установлена на вашем компьютере, вы можете скачать её
на сайте `JRE от Oracle
<http://www.oracle.com/technetwork/java/javase/downloads/index.html>`_.  Если вы используете GNU/Linux,
и у вас есть root-доступ к системе, используйте инструкции ОС для установки JRE.

Если команда `java` доступна в переменной окружения PATH, вы можете запустить Selenium server командой::

  java -jar selenium-server-standalone-2.x.x.jar

Замените `2.x.x` на номер версии Selenium server, которую вы скачали.

Если JRE установлена не-root пользователем и/или если она недостуна в переменной окружения PATH,
вы можете написать относительный или абсолютный путь к команде `java`.
Аналогично, вы можете указать относительный или абсолютный путь к jar-файлу Selenium server.
В этом случае команда будет выглядеть как-то так::

  /path/to/java -jar /path/to/selenium-server-standalone-2.x.x.jar


Установка из исходников в Git
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Чтобы собрать Selenium Python из исходников, нужно клонировать `официальный репозиторий
<https://github.com/SeleniumHQ/selenium.git>`_.  Он содержит исходники всех официальных Selenium,
 таких как Python, Java, Ruby и других.  Код на Python находится в директории ``/py``.
 Для сборки вам также потребуется сборщик `Bazel <https://www.bazel.build>`_.

.. note::

  Сейчас, когда Selenium подбирается к релизу 4.0.0, он требует Bazel 3.2.0
  (`Инструкции по установке
  <https://docs.bazel.build/versions/3.2.0/install.html>`_) несмотря на то, что версия 3.3.0
  уже доступна.

Чтобы собрать Wheel из исходников, запустите следующую команду в корне репозитория::

  bazel //py:selenium-wheel

Эта команда подготовит исходный код с некоторыми предобработанными файлами JS, которые нужны некоторым модулям
 webdriver, и соберёт пакет ``.whl`` в директории ``./bazel-bin/py/``.
 После этого вы можете использовать ``pip`` для установки.

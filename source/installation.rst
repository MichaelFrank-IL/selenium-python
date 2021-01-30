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

  **The Selenium server is only required if you want to use the remote
  WebDriver**.  See the :ref:`selenium-remote-webdriver` section for more
  details.  If you are a beginner learning Selenium, you can skip this section
  and proceed with next chapter.

Selenium server is a Java program.  Java Runtime Environment (JRE) 1.6 or newer
version is recommended to run Selenium server.

You can download Selenium server 2.x from the `download page of selenium website
<http://seleniumhq.org/download/>`_.  The file name should be something like
this: ``selenium-server-standalone-2.x.x.jar``.  You can always download the
latest 2.x version of Selenium server.

If Java Runtime Environment (JRE) is not installed in your system, you can
download the `JRE from the Oracle website
<http://www.oracle.com/technetwork/java/javase/downloads/index.html>`_.  If you
are using a GNU/Linux system and have root access in your system, you can also
use your operating system instructions to install JRE.

If `java` command is available in the PATH (environment variable), you can start
the Selenium server using this command::

  java -jar selenium-server-standalone-2.x.x.jar

Replace `2.x.x` with the actual version of Selenium server you downloaded from
the site.

If JRE is installed as a non-root user and/or if it is not available in the PATH
(environment variable), you can type the relative or absolute path to the `java`
command.  Similarly, you can provide a relative or absolute path to Selenium
server jar file.  Then, the command will look something like this::

  /path/to/java -jar /path/to/selenium-server-standalone-2.x.x.jar


Installing from Git sources
~~~~~~~~~~~~~~~~~~~~~~~~~~~

To build Selenium Python from the source code, clone `the official repository
<https://github.com/SeleniumHQ/selenium.git>`_.  It contains the source code for
all official Selenium flavors, like Python, Java, Ruby and others.  The Python
code resides in the ``/py`` directory.  To build, you will also need the `Bazel
<https://www.bazel.build>`_ build system.

.. note::

  Currently, as Selenium gets near to the 4.0.0 release, it requires Bazel 3.2.0
  (`Install instructions
  <https://docs.bazel.build/versions/3.2.0/install.html>`_), even though 3.3.0
  is already available.

To build a Wheel from the sources, run the following command from the repository
root::

  bazel //py:selenium-wheel

This command will prepare the source code with some preprocessed JS files needed
by some webdriver modules and build the ``.whl`` package inside the
``./bazel-bin/py/`` directory.  Afterwards, you can use ``pip`` to install it.

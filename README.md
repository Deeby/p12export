What is this?
---------------------
**p12export** - это утилита для экспортирования закрытых ключей и сертификатов
из Windows ГОСТ CSP в файл формата PKCS12. Тестировалась работа утилиты с CSP
КриптоПро версий 4.0 и 5.0 с контейнерами ключей, использующих алгоритмы ГОСТ
2001 и 2012 с длиной ключей 256 и 512 бит. Тестирование с другими ГОСТ CSP не
проводилось.

**p12info** - это утилита для получения информации о файле в формате PKCS12.

Installation
------------
Утилиты p12export и p12info не требуют установки и могут использоваться
из командной строки.

Usage
-----
**p12export** [-d|-D]

Ключ -d предназначен для отладки и получения дополнительной информации
о процессе чтения ключа из контейнера CSP.

**p12info** [container] [password]

container - имя PKCS12 файла

password - пароль

Building
--------
Для сборки под Windows нужны

1. Platform SDK (7, 8.1, или 10.0) и Visual Studio 2015

1. openssl-1.1.1d в ./openssl_1_1_1d/*

    git clone --single-branch --branch OpenSSL_1_1_1d https://github.com/openssl/openssl.git openssl_1_1_1d

1. gost-engine в ./engine/*

    git clone https://github.com/gost-engine/engine.git

**p12export**

Сначала нужно собрать openssl выполнив build_openssl.bat (требует Strawberry Perl для
выполнения configure), затем выполняется build_export.bat для сборки p12export.exe.

**p12info**

Для сборки для Windows gost-engine не обязателен, но крайне рекомендуется, так как
gost-engine необходим для получения информации о блобах PKCS12, использующих ГОСТ
алгоритмы. Для сборки нужно выполнить build_export.bat. p12info можно компилировать
для Linux, для этого предназначен Makefile.

Precompiled binaries
--------------------
Для удобства в составе проекта поставляются уже собранные p12export.exe и p12info.exe.
Так как линковка с gost-engine и openssl статическая, то никаких дополнительных DLL
для работы не требуется, кроме 32-битной библиотеки msvcr100.dll:
http://www.microsoft.com/ru-RU/download/details.aspx?id=8328


Bugs
----
Авторы будут очень признательны за любые отзывы, советы и замечания.
Пишите на support@etersoft.ru.

Contributing
------------
Патчи с исправлениями найденных ошибок или с добавлением новой функциональности
приветствуются.

---
name: RoninDojo

description: Установка и использование вашего Bitcoin-нода RoninDojo.
---
***ВНИМАНИЕ:** После ареста основателей кошелька Samourai и изъятия их серверов 24 апреля, некоторые функции RoninDojo, такие как Whirlpool, больше не работают. Тем не менее, возможно, что эти инструменты могут быть восстановлены или запущены по-новому в ближайшие недели. К тому же, поскольку код RoninDojo был размещен на GitLab Samourai, который также был изъят, в настоящее время невозможно удаленно загрузить код. Вероятно, команды RoninDojo работают над повторной публикацией кода.*

_Мы тщательно следим за развитием этого дела, а также за развитием связанных инструментов. Будьте уверены, что мы обновим этот учебник, как только появится новая информация._

_Этот учебник предоставляется только для образовательных и информационных целей. Мы не поддерживаем и не поощряем использование этих инструментов в преступных целях. Каждый пользователь несет ответственность за соблюдение законов в своей юрисдикции._

_Этот учебник посвящен установке RoninDojo v1. Чтобы воспользоваться последними улучшениями и функциями, я настоятельно рекомендую ознакомиться с нашим учебником, посвященным прямой установке RoninDojo v2 на ваш Raspberry Pi:_ [https://planb.network/tutorials/node/ronin-dojo-v2](https://planb.network/tutorials/node/ronin-dojo-v2)

---

Запуск и использование собственного нода является существенным для полноценного участия в сети Bitcoin. Хотя запуск Bitcoin-нода не приносит пользователю финансовых выгод, это позволяет ему сохранять свою конфиденциальность, действовать независимо и контролировать свое доверие к сети.

В этой статье мы подробно рассмотрим RoninDojo, отличное решение для запуска собственного Bitcoin-нода.

### Содержание:

- Что такое RoninDojo?
- Какое оборудование выбрать?
- Как установить RoninDojo?
- Как использовать RoninDojo?
- Заключение

Если вы не знакомы с тем, как работает Bitcoin-нод и его роль, я рекомендую начать с чтения этой статьи: Bitcoin-нод - Часть 1/2: Технические концепции.

![Samourai](assets/1.webp)

## Что такое RoninDojo?

Dojo - это полноценный сервер Bitcoin-нода, разработанный командой кошелька Samourai. Вы можете свободно установить его на любую машину.

RoninDojo - это помощник по установке и инструмент управления для Dojo и различных других инструментов. RoninDojo берет оригинальную реализацию Dojo и добавляет к ней множество других инструментов, одновременно упрощая установку и управление.

Они также предлагают "plug-and-play" оборудование, RoninDojo Tanto, с предустановленным RoninDojo на машине, собранной их командой. Tanto - это платное решение, подходящее для тех, кто не хочет заморачиваться с установкой.

Код RoninDojo открыт, так что его также можно установить на собственное оборудование. Этот вариант экономичен, но требует немного больше манипуляций, что и будет рассмотрено в этой статье.

RoninDojo является Dojo, поэтому он позволяет легко интегрировать Whirlpool CLI в ваш Bitcoin-нод для наилучшего возможного опыта CoinJoin. С Whirlpool CLI вы не только можете позволить вашим биткойнам ремиксироваться 24/7, не требуя постоянной работы вашего персонального компьютера, но и значительно улучшить вашу конфиденциальность.
RoninDojo интегрирует множество других инструментов, которые зависят от вашего Dojo, таких как калькулятор Boltzmann, определяющий уровень конфиденциальности транзакции, сервер Electrum для подключения ваших различных биткойн-кошельков к вашему узлу, или сервер Mempool для приватного наблюдения за вашими транзакциями. В сравнении с другим решением для узла, таким как Umbrel, о котором я рассказал вам в этой статье, RoninDojo глубоко сосредоточен на решениях и инструментах "On Chain", оптимизирующих конфиденциальность пользователя. Поэтому RoninDojo не позволяет взаимодействовать с сетью Lightning.

RoninDojo предлагает меньше инструментов по сравнению с Umbrel, но несколько ключевых функций для биткойнера, присутствующих на Ronin, невероятно стабильны.

Так что, если вам не нужны все функции сервера Umbrel и вы хотите только простой и стабильный узел с несколькими ключевыми инструментами, такими как Whirlpool или Mempool, тогда RoninDojo, вероятно, хорошее решение для вас.

На мой взгляд, разработка Umbrel сильно сосредоточена на сети Lightning и универсальных инструментах. Это все еще узел биткойна, но цель состоит в том, чтобы сделать его многофункциональным мини-сервером. В отличие от этого, фокус разработки RoninDojo больше совпадает с командами Samourai Wallet и сосредоточен на ключевых инструментах для биткойнера, позволяя полностью независимо и оптимизированно управлять конфиденциальностью в биткойне.

Обратите внимание, что настройка узла RoninDojo немного сложнее, чем узла Umbrel.

Теперь, когда мы смогли дать представление о RoninDojo, давайте посмотрим, как настроить этот узел вместе.

## Какое оборудование выбрать?

Чтобы выбрать машину, которая будет хостить и запускать RoninDojo, у вас есть несколько вариантов.

Как было сказано ранее, самым простым выбором является заказ Tanto, машины plug-and-play, специально предназначенной для этой цели. Чтобы заказать свою, перейдите сюда: [ссылка](https://shop.ronindojo.io/product-category/nodes/).

Поскольку команды RoninDojo производят открытый код, также возможно реализовать RoninDojo на других машинах. Вы можете найти последние версии мастера установки на этой странице: [ссылка](https://ronindojo.io/en/downloads.html), и последние версии кода на этой странице: [ссылка](https://code.samourai.io/ronindojo/RoninDojo).

Лично я установил его на Raspberry Pi 4 8GB и все работает идеально.

Однако обратите внимание, что команды RoninDojo указывают, что часто возникают проблемы с корпусом и адаптером SSD. Поэтому не рекомендуется использовать корпус с кабелем для SSD вашей машины. Вместо этого предпочтительнее использовать карту расширения памяти, специально предназначенную для вашей материнской платы, например, такую: Карта расширения памяти Raspberry Pi 4.

Вот пример того, как настроить свой собственный узел RoninDojo:

- Raspberry Pi 4.
- Корпус с вентилятором.
- Совместимая карта расширения памяти.
- Кабель питания.
- Промышленная микро SD карта на 16 ГБ или больше.
- SSD на 1 ТБ или больше.
- Кабель Ethernet RJ45, рекомендуется категория 8.

## Как установить RoninDojo?

### Шаг 1: Подготовьте загрузочную микро SD карту.

После сборки вашей машины вы можете начать установку RoninDojo. Для этого начните с создания загрузочной микро SD карты, записав на нее соответствующий образ диска.

Вставьте вашу микро SD карту в ваш личный компьютер, затем перейдите на официальный сайт RoninDojo, чтобы скачать образ диска RoninOS: https://ronindojo.io/en/downloads.html.
Загрузите образ диска, соответствующий вашему оборудованию. В моем случае я загрузил образ "MANJARO-ARM-RONINOS-RPI4-22.03.IMG.XZ":
![Загрузка образа диска RoninOS](assets/2.webp)

После загрузки образа проверьте его целостность с помощью соответствующего файла .SHA256. Я подробно опишу, как это сделать, в этой статье: Как проверить целостность программного обеспечения Bitcoin на Windows?

Конкретные инструкции по проверке целостности RoninOS также доступны на этой странице: https://wiki.ronindojo.io/en/extras/verify.

Чтобы записать этот образ на вашу micro SD карту, вы можете использовать такое программное обеспечение, как Balena Etcher, которое можно загрузить здесь: https://www.balena.io/etcher/.

Для этого выберите образ в Etcher и запишите его на micro SD карту:

![Запись образа диска с помощью Etcher](assets/3.webp)

После завершения операции вы можете вставить загрузочную micro SD карту в Raspberry Pi и включить устройство.

### Шаг 2: Настройка RoninOS.

RoninOS — это операционная система вашего узла RoninDojo. Это модифицированная версия Manjaro, дистрибутива Linux. После запуска вашего устройства и ожидания нескольких минут, вы можете начать его настройку.

Для удаленного подключения к нему вам нужно будет найти IP-адрес вашего устройства RoninDojo. Для этого вы можете, например, подключиться к панели управления вашего интернет-модема, или также можно загрузить программное обеспечение, такое как https://angryip.org/, для сканирования вашей локальной сети и поиска IP-адреса устройства.

После того как вы нашли IP, вы можете взять управление вашим устройством с другого компьютера, подключенного к той же локальной сети, используя SSH.

С компьютера на macOS или Linux просто откройте терминал. С компьютера на Windows вы можете использовать специализированный инструмент, такой как Putty, или напрямую использовать Windows PowerShell.

После открытия терминала введите следующую команду:

> ssh root@192.168.?.?

Просто замените два вопросительных знака на IP вашего ранее найденного RoninDojo.
Совет: В Shell щелкните правой кнопкой мыши, чтобы вставить элемент.

Далее вы попадете в панель управления Manjaro. Выберите правильную раскладку клавиатуры, используя стрелки для изменения цели в выпадающем списке.

![Настройка клавиатуры Manjaro](assets/4.webp)

Выберите имя пользователя и пароль для вашей сессии. Используйте надежный пароль и сделайте безопасную резервную копию. При желании вы можете использовать слабый пароль во время установки, а позже легко изменить его, "скопировав и вставив" его в RoninUI. Это позволит вам использовать очень надежный пароль, не тратя слишком много времени на его ручной ввод во время настройки Manjaro.

![Настройка имени пользователя Manjaro](assets/5.webp)

Далее вам также будет предложено выбрать пароль root. Для пароля root введите надежный пароль напрямую. Вы не сможете изменить его из RoninUI. Также не забудьте надежно сохранить этот пароль root.

Затем введите ваше местоположение и часовой пояс.

![Настройка часового пояса Manjaro](assets/6.webp)

![Настройка местоположения Manjaro](assets/7.webp)

Далее выберите имя хоста.

![Настройка имени хоста Manjaro](assets/8.webp)

Наконец, проверьте информацию о настройке Manjaro и подтвердите.

![Проверка информации о настройке ManjaroOS](assets/9.webp)

### Шаг 3: Загрузка RoninDojo.
Начальная конфигурация RoninOS будет выполнена. После завершения, как показано на скриншоте выше, машина перезагрузится. Подождите несколько моментов, затем введите следующую команду, чтобы снова подключиться к вашей машине RoninDojo:
> ssh username@192.168.?.?

Просто замените "username" на имя пользователя, которое вы выбрали ранее, и замените вопросительные знаки на IP вашего RoninDojo.

Затем введите пароль пользователя.

В терминале это будет выглядеть так:

![SSH Connection to RoninOS](assets/10.webp)

Теперь вы подключены к вашей машине, на которой в настоящее время установлена только RoninOS. Теперь вам нужно установить на нее RoninDojo.

Скачайте последнюю версию RoninDojo, введя следующую команду:

> git clone https://code.samourai.io/ronindojo/RoninDojo

Скачивание будет быстрым. В терминале вы увидите это:

![Cloning RoninDojo](assets/11.webp)

Дождитесь окончания скачивания, затем установите и получите доступ к пользовательскому интерфейсу RoninDojo, используя следующую команду:

> ~/RoninDojo/ronin

Вам будет предложено ввести пароль пользователя:

![Bitcoin Node Password Verification](assets/12.webp)

Эта команда необходима только при первом доступе к вашему RoninDojo. После этого, чтобы получить доступ к RoninCLI через SSH, вам просто нужно будет ввести команду [SSH username@192.168.?.?], заменив "username" на ваше имя пользователя и введя IP-адрес вашего узла. Вас попросят ввести пароль пользователя.

Далее вы увидите эту великолепную анимацию:

![RoninCLI launch animation](assets/13.webp)

Затем вы наконец попадете в пользовательский интерфейс RoninDojo CLI.

### Шаг 4: Установка RoninDojo.

Из главного меню перейдите в меню "System" с помощью стрелок на клавиатуре. Нажмите клавишу ввода, чтобы подтвердить ваш выбор.

![RoninCLI navigation menu to System](assets/14.webp)

Затем перейдите в меню "System Setup & Install".

![RoninCLI navigation menu to RoninDojo system installation](assets/15.webp)

Наконец, отметьте "System Setup" и "Install RoninDojo" с помощью пробела, затем выберите "Accept", чтобы начать установку.

![RoninDojo installation confirmation](assets/16.webp)

Позвольте установке спокойно продолжаться. В моем случае это заняло около 2 часов. Держите терминал открытым во время процесса.

Иногда проверяйте ваш терминал, так как вас будут просить нажать клавишу на определенных этапах установки, как здесь, например:

![RoninDojo installation in progress](assets/17.webp)

В конце установки вы увидите запуск различных контейнеров:

![Node container startup](assets/18.webp)

Затем ваш узел перезагрузится. Снова подключитесь к RoninCLI для следующего шага.

![Bitcoin node restart](assets/19.webp)

### Шаг 5: Скачивание цепочки proof-of-work и доступ к RoninUI.

После завершения установки ваш узел начнет скачивание цепочки Bitcoin proof-of-work. Это называется начальной загрузкой блоков (IBD). Обычно это занимает от 2 до 14 дней в зависимости от вашего интернет-соединения и устройства.

Вы можете отслеживать прогресс скачивания цепочки, получив доступ к веб-интерфейсу RoninUI.

Чтобы получить к нему доступ из локальной сети, введите следующее в адресную строку вашего браузера:

- Либо напрямую введите IP-адрес вашей машины (192.168.?.?)

- Либо введите: ronindojo.local
Не забудьте отключить ваш VPN, если вы его используете.
### Возможная проблема

Если у вас не получается подключиться к RoninUI через ваш браузер, проверьте корректную работу приложения через Терминал, подключенный к вашему узлу через SSH. Подключитесь к главному меню, следуя предыдущим шагам:

- Введите: SSH username@192.168.?.?, заменив на ваши учетные данные.

- Введите пароль пользователя.

После перехода в главное меню перейдите к:

> RoninUI > Перезапустить

Если приложение перезапускается корректно, проблема с подключением через ваш браузер. Убедитесь, что вы не используете VPN и подключены к той же сети, что и ваш узел.

Если при перезапуске возникает ошибка, попробуйте обновить операционную систему, а затем переустановить RoninUI. Для обновления ОС:

> Система > Обновления ПО > Обновить операционную систему

После обновления и перезапуска снова подключитесь к вашему узлу через SSH и переустановите RoninUI:

> RoninUI > Переустановить

После повторной загрузки RoninUI попробуйте подключиться к RoninUI через ваш браузер.

> Совет: Если вы случайно вышли из RoninCLI и оказались в терминале Manjaro, просто введите команду "ronin", чтобы вернуться непосредственно в главное меню RoninCLI.

### Вход в веб-интерфейс

Вы также можете войти в веб-интерфейс RoninUI с любой сети, используя Tor. Для этого извлеките Tor-адрес вашего RoninUI из RoninCLI:

> Учетные данные > Ronin UI

Извлеките Tor-адрес, заканчивающийся на .onion, затем войдите в Ronin UI, введя этот адрес в вашем Tor-браузере. Будьте осторожны, чтобы не раскрыть ваши различные учетные данные, так как это конфиденциальная информация.

![Интерфейс входа в веб RoninUI](assets/20.webp)

После входа в систему вам будет запрошен пароль пользователя. Это тот же пароль, который вы используете для входа через SSH.

![Панель управления веб-интерфейса RoninUI](assets/21.webp)

Здесь мы можем видеть прогресс IBD (Initial Block Download). Будьте терпеливы, вы извлекаете все транзакции, совершенные в Bitcoin с 3 января 2009 года.

После загрузки всего блокчейна индексатор сжимает базу данных. Эта операция занимает около 12 часов. Вы также можете отслеживать его прогресс в разделе "Индексатор" в RoninUI.

Ваш узел RoninDojo будет полностью функциональным после этого:

![Индексатор синхронизирован на 100% функциональный узел](assets/22.webp)

Если вы хотите изменить пароль пользователя на более сложный, вы можете сделать это сейчас во вкладке "Настройки". В RoninDojo нет дополнительного уровня безопасности, поэтому я рекомендую выбрать действительно сложный пароль и позаботиться о его резервном копировании.

## Как использовать RoninDojo?

После загрузки и сжатия цепочки вы можете начать пользоваться услугами, предлагаемыми вашим новым узлом RoninDojo. Давайте посмотрим, как их использовать.

### Подключение программного обеспечения кошелька к electrs.

Первое применение вашего недавно установленного и синхронизированного узла будет в том, чтобы транслировать ваши транзакции в сеть Bitcoin. Поэтому вы, вероятно, захотите подключить к нему ваше различное программное обеспечение для управления кошельками.

Вы можете сделать это, используя Electrum Rust Server (electrs). Приложение обычно предустановлено на вашем узле RoninDojo. Если нет, вы можете вручную установить его из интерфейса RoninCLI.

Просто перейдите к:

> Приложения > Управление приложениями > Установить Electrum Server

Чтобы получить Tor-адрес вашего Electrum Server, из меню RoninCLI перейдите к:

> Учетные данные > Electrs
Вам просто нужно ввести ссылку .onion в программное обеспечение вашего кошелька. Например, в Sparrow Wallet перейдите на вкладку:
> Файл > Настройки > Сервер

В типе сервера выберите "Private Electrum", затем введите Tor-адрес вашего Electrum Server в соответствующее поле. Наконец, нажмите на "Тестировать соединение", чтобы проверить и сохранить ваше соединение.

![Интерфейс подключения Sparrow Wallet к electrs](assets/23.webp)

### Подключение программного обеспечения кошелька к Samourai Dojo.

Вместо использования Electrs, вы также можете использовать Samourai Dojo для подключения вашего совместимого программного кошелька к вашему узлу RoninDojo. Например, Samourai Wallet предлагает эту опцию.

Для этого просто отсканируйте QR-код подключения вашего Dojo. Чтобы получить к нему доступ из RoninUI, нажмите на вкладку "Панель управления", а затем на кнопку "Управление" в окне вашего Dojo. Затем вы сможете увидеть QR-коды подключения для вашего Dojo и BTC-RPC Explorer. Чтобы отобразить их, нажмите на "Показать значения".

![Получение QR-кода подключения к Dojo](assets/24.webp)

Для подключения вашего Samourai Wallet к вашему Dojo вам нужно будет отсканировать этот QR-код во время установки приложения:

![Подключение к Dojo из приложения Samourai Wallet](assets/25.webp)

### Использование собственного Mempool Explorer.

Незаменимый инструмент для пользователей Bitcoin, эксплорер позволяет проверять различную информацию о цепочке Bitcoin. С помощью Mempool, например, вы можете в реальном времени проверять комиссии, применяемые другими пользователями, чтобы соответственно скорректировать свои. Вы также можете проверить статус подтверждения одной из ваших транзакций или просмотреть баланс адреса.

Эти инструменты эксплорера могут подвергать вас рискам конфиденциальности и требуют доверия к базе данных третьей стороны. Когда вы используете этот онлайн-инструмент, не проходя через свой собственный узел:

- Вы рискуете утечкой информации о вашем кошельке.

- Вы доверяете управляющему веб-сайта за цепочку доказательства работы, которую они хостят.

Чтобы избежать этих рисков, вы можете использовать свой собственный экземпляр Mempool на вашем узле через сеть Tor. С этим решением вы не только сохраняете свою конфиденциальность при использовании сервиса, но и больше не нуждаетесь в доверии к провайдеру, поскольку вы запрашиваете данные из своей собственной базы данных.

Для этого начните с установки Mempool Space Visualizer из RoninCLI:

> Приложения > Управление приложениями > Установить Mempool Space Visualizer

После установки получите ссылку на ваш Mempool. Tor-адрес позволит вам получить к нему доступ из любой сети. Аналогично, мы получаем эту ссылку через RoninCLI:

> Учетные данные > Mempool

![Получение Tor-адреса Mempool](assets/26.webp)

Просто введите ваш Tor-адрес Mempool в браузер Tor, чтобы насладиться вашим собственным экземпляром Mempool, основанным на ваших собственных данных. Я рекомендую добавить этот Tor-адрес в избранное для более быстрого доступа. Вы также можете создать ярлык на вашем рабочем столе.

![Интерфейс Mempool Space](assets/27.webp)

Если у вас еще нет браузера Tor, вы можете скачать его здесь: https://www.torproject.org/download/

Вы также можете получить к нему доступ с вашего смартфона, установив браузер Tor и введя тот же адрес. Откуда угодно вы можете просматривать состояние цепочки Bitcoin, используя ваш собственный узел.

### Использование Whirlpool CLI.

Ваш узел RoninDojo также включает WhirlpoolCLI, удаленный интерфейс командной строки для автоматизации смешивания в Whirlpool.
Когда вы выполняете CoinJoin с использованием реализации Whirlpool, приложение, которое вы используете, должно оставаться открытым, чтобы выполнять смешивания и повторные смешивания. Этот процесс может быть утомительным для пользователей, которые хотят иметь высокие анонимные наборы, поскольку устройство, на котором размещено приложение с Whirlpool, должно постоянно оставаться включенным. На практике это означает, что если вы хотите вовлекать ваши UTXO в круглосуточные повторные смешивания, вам нужно будет постоянно держать ваш личный компьютер или телефон включенным с открытым приложением.
Одним из решений этой проблемы является использование WhirlpoolCLI на машине, которая предназначена для постоянной работы, например, на Bitcoin-ноде. С его помощью наши UTXO могут быть пересмешаны 24/7 без необходимости держать включенной другую машину, кроме нашей Bitcoin-ноды.
WhirlpoolCLI используется с WhirlpoolGUI, графическим интерфейсом, который устанавливается на личный компьютер для удобного управления Coinjoin. В этой статье я подробно объясню, как настроить Whirlpool CLI со своим собственным dojo: [ссылка](https://www.pandul.fr/post/comprendre-et-utiliser-le-coinjoin-sur-bitcoin#:~:text=dans%20cette%20partie.-,Tutoriel%20%3A%20Whirpool%20CLI%20sur%20Dojo%20et%20Whirlpool%20GUI.,-Si%20vous%20souhaitez).

Чтобы узнать больше о Coinjoin в целом, я объясняю все в этой статье: [ссылка](https://www.pandul.fr/post/comprendre-et-utiliser-le-coinjoin-sur-bitcoin).

### Использование инструмента Whirlpool Stat Tool.

После выполнения CoinJoins с Whirlpool вы можете захотеть узнать фактический уровень конфиденциальности ваших смешанных UTXO. Инструмент Whirlpool Stat Tool позволяет вам легко это сделать. С помощью этого инструмента вы можете рассчитать перспективный и ретроспективный баллы ваших смешанных UTXO. Чтобы узнать больше о расчете этих анонимных наборов и о том, как они работают, я рекомендую прочитать этот раздел: [ссылка](https://www.pandul.fr/post/comprendre-et-utiliser-le-coinjoin-sur-bitcoin#:~:text=perdre%20en%20confidentialit%C3%A9.-,Anon%20Sets.,-Comme%20expliqu%C3%A9%20pr%C3%A9c%C3%A9demment).

Инструмент предустановлен на вашем RoninDojo. Пока он доступен только из RoninCLI. Чтобы запустить его из главного меню, перейдите к:

> Samourai Toolkit > Whirlpool Stat Tool

Появятся инструкции по использованию. После завершения нажмите любую клавишу, чтобы получить доступ к командной строке:

![Домашняя страница программного обеспечения Whirlpool Stats Tool](assets/28.webp)

Будет отображен терминал:

> wst#/tmp>

Чтобы выйти из этого интерфейса и вернуться в меню RoninCLI, просто введите команду:

> quit

Для начала мы установим прокси на Tor, чтобы извлекать данные OXT с полной конфиденциальностью. Введите команду:

> socks5 127.0.0.1:9050

Затем загрузите данные из пула, который содержит вашу транзакцию:

> download 0001
>
> Замените 0001 на код номинала пула, который вас интересует.

Коды номиналов на WST следующие:

- Пул 0.5 биткоинов: 05

- Пул 0.05 биткоинов: 005

- Пул 0.01 биткоинов: 001

- Пул 0.001 биткоинов: 0001
![Загрузка данных из пула 0001 с OXT](assets/29.webp)
После того как данные будут загружены, загрузите их с помощью команды:

> load 0001
>
> Замените 0001 на код интересующего вас пула.

![Загрузка данных из пула 0001](assets/30.webp)
Позвольте процессу загрузки завершиться, это может занять несколько минут. После загрузки данных введите команду score, за которой следует ваш TXID (идентификатор транзакции), чтобы получить его Anon Sets:

> score TXID
>
> Замените TXID на идентификатор вашей транзакции.

![Вывод проспективного и ретроспективного рейтингов для данного TXID](assets/31.webp)

Затем WST отобразит ретроспективный рейтинг (метрики, оглядывающиеся назад) за которым следует проспективный рейтинг (метрики, смотрящие вперед). Помимо рейтингов Anon Sets, WST также предоставляет вам информацию о скорости распространения вашего вывода в пуле на основе anon set.

Обратите внимание, что проспективный рейтинг вашего UTXO рассчитывается на основе TXID вашего первоначального микса, а не вашего последнего микса. В свою очередь, ретроспективный рейтинг UTXO рассчитывается на основе TXID последнего цикла.

Еще раз, если вы не понимаете эти концепции Anon Sets, я рекомендую прочитать эту часть моей статьи о Coinjoin, где я объясняю все подробно с диаграммами: [https://www.pandul.fr/post/comprendre-et-utiliser-le-coinjoin-sur-bitcoin#:~:text=perdre%20en%20confidentialit%C3%A9.-,Anon%20Sets.,-Comme%20expliqu%C3%A9%20pr%C3%A9c%C3%A9demment](https://www.pandul.fr/post/comprendre-et-utiliser-le-coinjoin-sur-bitcoin#:~:text=perdre%20en%20confidentialit%C3%A9.-,Anon%20Sets.,-Comme%20expliqu%C3%A9%20pr%C3%A9c%C3%A9demment)

### Использование калькулятора Больцмана.

Калькулятор Больцмана - это инструмент, который позволяет легко рассчитать различные продвинутые метрики для биткойн-транзакции, включая ее уровень энтропии. Все эти данные помогут вам оценить уровень конфиденциальности транзакции и обнаружить любые потенциальные ошибки. Этот инструмент предустановлен на вашем узле RoninDojo.

Чтобы получить к нему доступ из RoninCLI, подключитесь через SSH, затем перейдите в меню:

> Samourai Toolkit > Boltzmann Calculator

Прежде чем объяснять, как его использовать на RoninDojo, я расскажу, что представляют собой эти метрики, как они рассчитываются и для чего они используются.

Эти индикаторы могут быть использованы для любой биткойн-транзакции, но они особенно интересны для изучения качества транзакции Coinjoin.

1. Первый индикатор, рассчитываемый этим программным обеспечением, - это количество возможных комбинаций. В калькуляторе он обозначен как "nb combinations". Учитывая значения UTXO, этот индикатор представляет собой количество возможных соответствий между входами и выходами.

> Если вы не знакомы с термином "UTXO", я рекомендую прочитать эту короткую статью: Механизм биткойн-транзакции: UTXO, входы и выходы.

Другими словами, этот индикатор представляет количество возможных интерпретаций для данной транзакции. Например, структура Coinjoin Whirlpool 5x5 будет иметь количество возможных комбинаций, равное 1496:

![Схема транзакции Coinjoin на kycp.org](assets/32.webp)

Кредит: KYCP
2. Второй рассчитываемый показатель - это энтропия транзакции. Поскольку количество возможных комбинаций для транзакции может быть очень велико, вместо этого можно использовать энтропию. Энтропия представляет собой двоичный логарифм количества возможных комбинаций. Ее формула следующая:
- E: энтропия транзакции.
- C: количество возможных комбинаций для транзакции.

> E = log2(C)

В математике двоичный логарифм (по основанию 2) является обратной функцией функции степени двойки. Другими словами, двоичный логарифм от x - это степень, до которой число 2 должно быть возведено, чтобы получить значение x.

Таким образом:

> E = log2(C)
> C = 2^E

Этот показатель выражается в битах. Например, вот расчет энтропии транзакции Whirlpool 5x5 Coinjoin, с ранее упомянутым количеством возможных комбинаций, равным 1496:

> C = 1496
>
> E = log2(1496)
>
> E = 10.5469 бит

Следовательно, эта транзакция Coinjoin имеет энтропию 10.5469 бит, что очень хорошо.

Чем выше этот показатель, тем больше различных интерпретаций транзакции существует, и, следовательно, тем более конфиденциальной является транзакция.

Давайте рассмотрим другой пример. Вот "классическая" транзакция, которая имеет один вход и два выхода:

![Схема биткойн-транзакции на oxt.me](assets/34.webp)

Автор: OXT

Эта транзакция имеет только одну возможную интерпретацию:

> [(inp 0) > (Outp 0 ; Outp 1)]

Так что ее энтропия будет равна 0:

> C = 1
>
> E = log2(C)
>
> E = 0

3. Третий показатель, возвращаемый калькулятором Boltzmann, - это эффективность транзакции, называемая "Эффективность кошелька". Этот показатель просто позволяет сравнить входящую транзакцию с лучшей возможной транзакцией в той же конфигурации.

Теперь мы введем понятие максимальной энтропии, которое представляет собой наивысшую достижимую энтропию для данной структуры транзакции. Например, структура Whirlpool 5x5 Coinjoin будет иметь максимальную энтропию 10.5469. Показатель эффективности сравнивает эту максимальную энтропию с фактической энтропией входящей транзакции. Его формула следующая:

- ER: Фактическая энтропия, выраженная в битах.
- EM: Максимальная энтропия с той же структурой, выраженная в битах.
- Ef: Эффективность, выраженная в битах.

> Ef = ER - EM
>
> Ef = 10.5469 - 10.5469
>
> Ef = 0 бит

Этот показатель также выражается в процентах, поэтому формула становится следующей:

- CR: Фактическое количество возможных комбинаций.
- CM: Максимальное количество возможных комбинаций с той же структурой.
- Ef: Эффективность, выраженная в процентах.

> Ef = CR/CM
>
> Ef = 1496/1496
>
> Ef = 100%

Эффективность 100% означает, что эта транзакция имеет наивысшую возможную конфиденциальность относительно своей структуры.

4. Четвертый рассчитываемый показатель - это плотность энтропии. Он позволяет связать энтропию с каждым входом или выходом. Этот показатель можно использовать для сравнения эффективности между транзакциями разного размера.

Его расчет очень прост: мы делим энтропию транзакции на количество присутствующих входов и выходов. Например, для Whirlpool 5x5 Coinjoin, у нас было бы:

    ED: Плотность энтропии, выраженная в битах.
    E: Энтропия транзакции, выраженная в битах.
    T: Общее количество входов и выходов в транзакции.

T = 5 + 5 = 10
ED = E / TED = 10.5469 / 10
ED = 1.054 бита

Пятая часть информации, предоставляемая калькулятором Больцмана, - это таблица вероятностей связей между входами и выходами. Эта таблица просто дает вам вероятность (оценку Больцмана), что данный вход соответствует данному выходу.

Если взять наш пример с Whirlpool Coinjoin, таблица вероятностей будет выглядеть так:

| %       | Выход 0 | Выход 1 | Выход 2 | Выход 3 | Выход 4 |
|---------|---------|---------|---------|---------|---------|
| Вход 0  | 34%     | 34%     | 34%     | 34%     | 34%     |
| Вход 1  | 34%     | 34%     | 34%     | 34%     | 34%     |
| Вход 2  | 34%     | 34%     | 34%     | 34%     | 34%     |
| Вход 3  | 34%     | 34%     | 34%     | 34%     | 34%     |
| Вход 4  | 34%     | 34%     | 34%     | 34%     | 34%     |

Здесь мы видим, что каждый вход имеет равную вероятность быть связанным с каждым выходом.

Однако, если взять пример транзакции с одним входом и двумя выходами, он будет выглядеть так:

| Вход | Выход 0 | Выход 1 |
| ---- | ------- | ------- |
| 0    | 100%    | 100%    |

В этом примере мы видим, что вероятность каждого выхода, исходящего от входа 0, составляет 100%.

Чем ниже эта вероятность, тем выше уровень конфиденциальности.

6. Шестая часть информации, которая рассчитывается, - это количество детерминированных связей. Также будет предоставлено соотношение детерминированных связей. Этот показатель подчеркивает количество связей между входами и выходами данной транзакции, которые имеют вероятность 100%, то есть они неоспоримы.

Соотношение указывает количество детерминированных связей в транзакции по сравнению с общим числом связей.

Например, транзакция Coinjoin Whirlpool не имеет детерминированных связей между входами и выходами. Показатель будет равен нулю, а соотношение также будет 0%.

Однако для второй изученной транзакции (1 вход и 2 выхода) показатель составляет 2, а соотношение - 100%.

Таким образом, если этот показатель равен нулю, это указывает на хорошую конфиденциальность.

Теперь, когда мы изучили показатели, давайте посмотрим, как их рассчитать с помощью этого программного обеспечения. Из RoninCLI перейдите в меню:

> Samourai Toolkit > Boltzmann Calculator

![Домашняя страница программного обеспечения калькулятора Больцмана](assets/35.webp)

После запуска программного обеспечения введите идентификатор транзакции, который вы хотите изучить. Вы можете ввести несколько транзакций одновременно, разделив их запятой, затем нажмите Enter:

![Введите TXID для изучения в калькуляторе Больцмана](assets/36.webp)

Затем калькулятор вернет все ранее упомянутые показатели:

![Печать данных калькулятора Больцмана для этого TXID](assets/37.webp)

Введите команду "Quit" для выхода из программного обеспечения и возвращения в меню RoninCLI.

Чтобы узнать больше о калькуляторе Больцмана, рекомендую прочитать эти статьи:

- https://medium.com/@laurentmt/introducing-boltzmann-85930984a159

- https://gist.github.com/LaurentMT/e758767ca4038ac40aaf
### Подключение Bisq.
Bisq - это платформа обмена между пользователями, которая позволяет вам покупать и продавать биткойны. Она используется с настольным программным обеспечением, работающим на Tor, и позволяет обмениваться биткойнами, не требуя предоставления вашей личности.
Bisq обеспечивает обмен между пользователями через систему мультиподписи 2/2. Вы можете использовать это программное обеспечение со своим собственным узлом RoninDojo, чтобы оптимизировать конфиденциальность ваших обменов и доверять данным из блокчейна вашего собственного узла.

Чтобы скачать программное обеспечение Bisq, перейдите на их официальный сайт: https://bisq.network/

Чтобы начать работу с программным обеспечением, я рекомендую прочитать эту страницу: https://bisq.network/getting-started/

Чтобы получить ссылку для подключения от вашего RoninDojo, вам нужно будет подключиться к RoninCLI через SSH. Затем перейдите в меню:

> Приложения > Управление приложениями

Введите ваш пароль, затем отметьте поле с помощью пробела:

> [ ] Включить подключение Bisq

Подтвердите свой выбор. Позвольте вашему узлу установиться, затем извлеките адрес Tor V3 из:

> Учетные данные > Bitcoind

Скопируйте адрес под "Bitcoin Daemon".

Вы также можете извлечь ваш адрес Bitcoind Tor V3 из интерфейса RoninUI, просто нажав на "Управление" в блоке "Bitcoin Core" на "Панели управления":

![Получение адреса TorV3 Bitcoin Daemon в RoninUI](assets/38.webp)

Чтобы подключить ваш узел к Bisq, перейдите в меню:

> Настройки > Информация о сети

![Доступ к интерфейсу подключения узла из программного обеспечения Bisq](assets/39.webp)

Нажмите на пузырь "Использовать пользовательские узлы Bitcoin Core". Затем введите ваш адрес Bitcoin TorV3 в предназначенное для этого поле, с ".onion", но без "http://".

![Поле для ввода адреса TorV3 вашего узла в программном обеспечении Bisq](assets/40.webp)

Перезапустите программное обеспечение Bisq. Теперь ваш узел подключен к вашему Bisq.

### Другие функции.

Ваш узел RoninDojo также включает в себя другие базовые функции. У вас есть возможность сканировать конкретную информацию, чтобы убедиться, что она учитывается.

Например, иногда может случиться, что ваш кошелек, подключенный к вашему RoninDojo, не находит принадлежащие вам биткойны. Баланс равен 0, хотя вы уверены, что у вас есть биткойны в этом кошельке. Существует множество возможных причин, включая ошибку в путях производных, и среди них также возможно, что ваш узел не наблюдает за вашими адресами.

Чтобы исправить это, вы можете проверить, отслеживает ли ваш узел ваш xpub с помощью "инструмента xpub". Чтобы получить к нему доступ из RoninUI, перейдите в меню:

> Обслуживание > Инструмент XPUB

Введите проблемный xpub и нажмите "Проверить", чтобы проверить эту информацию.

![Инструмент XPUB из RoninUI](assets/41.webp)

Если ваш xpub отслеживается узлом, вы увидите это:

![Результат инструмента XPUB, показывающий успешный анализ](assets/42.webp)

Проверьте, правильно ли отображаются все транзакции. Также проверьте, соответствует ли тип производной тому, что используется в вашем кошельке. Здесь мы видим, что узел интерпретирует этот xpub как производную BIP44. Если этот тип производной не соответствует используемому в вашем кошельке, нажмите на кнопку "Перенабрать", затем выберите BIP44/BIP49/BIP84 в соответствии с вашим выбором:

![Изменение типа производной изучаемого xpub из RoninUI](assets/43.webp)

Если ваш xpub не отслеживается вашим узлом, вы увидите этот экран, приглашающий вас импортировать его:
![Импортируйте xpub с помощью инструмента XPUB в RoninUI](assets/44.webp)
Вы также можете использовать другие инструменты обслуживания:

- Инструмент Транзакции: Позволяет наблюдать за деталями конкретной транзакции.
- Инструмент Адреса: Позволяет проверить, отслеживается ли конкретный адрес вашим Dojo.
- Пересканирование Блоков: Принуждает ваш узел к пересканированию выбранного диапазона блоков.

Вы также найдете инструмент "Push Tx" на RoninUI. Он позволяет транслировать подписанную транзакцию в сеть Bitcoin. Она должна быть введена в шестнадцатеричном формате:

![Инструмент для трансляции подписанной транзакции из RoninUI](assets/45.webp)

## Заключение.

Мы увидели, как установить и начать работу с этим замечательным инструментом, который является RoninDojo. Это отличный выбор для запуска собственного узла Bitcoin. Это стабильное решение, которое интегрирует и обновляет все необходимые инструменты для пользователя Bitcoin.

Если использование терминала вас не пугает и если вам не нужны инструменты, связанные с сетью Lightning, тогда RoninDojo может вас заинтересовать.

Если можете, рассмотрите возможность пожертвования разработчикам, которые бесплатно создают эти программы с открытым исходным кодом для вас: https://donate.ronindojo.io/

Чтобы узнать больше о RoninDojo, рекомендую ознакомиться со ссылками в моих внешних ресурсах ниже.

### Дополнительное чтение:

- Понимание и использование CoinJoin в Bitcoin.
- Хеш-функции - выдержка из электронной книги Bitcoin Démocratisé 1.
- Все, что вам нужно знать о Bitcoin Passphrase.

### Внешние ресурсы:

- https://ronindojo.io/index.html
- https://wiki.ronindojo.io/en/home
- https://gist.github.com/LaurentMT/e758767ca4038ac40aaf
- https://medium.com/@laurentmt/introducing-boltzmann-85930984a159
- https://en.wikipedia.org/wiki/Boltzmann_formula
- https://wiki.ronindojo.io/en/setup/bisq
- https://bisq.network/
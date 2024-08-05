---
name: Добыча в Океане

description: Введение в добычу в океане
---

![signup](assets/cover.webp)

**Май 2024**

Добыча в Океане - это довольно уникальный майнинговый пул. Здесь не требуются учетные записи, адреса электронной почты, пароли. Как и в случае с Bitcoin, все прозрачно, псевдонимно, и участники могут выбирать из четырех различных шаблонов блоков.

### Система Компенсации

Система компенсации Океана называется TIDES, "Прозрачный Индекс Отдельных Расширенных Долей". Эта система записывает работу, предоставленную майнерами, известную как "доли". Пул рассчитывает процент "долей" для каждого участника, затем добавляет их Bitcoin-адрес в шаблон блока пула в качестве получателя этого процента от вознаграждения за блок.

Шаблон блока обновляется примерно каждые 10 секунд для учета наиболее выгодных новых транзакций и для изменения распределения вознаграждения за блок, если это необходимо.

![signup](assets/rem.webp)

Не имеет значения, подключены ли ваши машины в момент, когда пул добывает новый блок. Уже представленная работа сохраняется для следующих восьми блоков, найденных пулом.

Сохранение работы для восьми блоков вместо сброса счетчиков до нуля с каждым новым добытым блоком означает, что ваша компенсация будет составлять 100% только после того, как пул найдет восемь блоков после начала вашего участия. Это также означает, что вы будете продолжать получать компенсацию за восемь блоков, если прекратите участие в пуле.

Этот механизм сглаживает компенсацию и препятствует "прыжкам по пулам", которые включают регулярную смену пулов в зависимости от того, какой из них скорее всего найдет следующий блок.

### Выводы

Операция добычи в Океане позволяет ее участникам восстанавливать "чистые" биткоины, то есть биткоины, которые напрямую выпущены вознаграждением за блок.

В отличие от большинства других пулов, Океан не получает вновь добытые биткоины; адреса участников напрямую интегрируются в шаблон блока.

На данный момент минимальная сумма для реальной выгоды от чистых биткоинов составляет 1,048,576 сатоши. С каждым блоком, добытым пулом, ваша доля "долей" должна давать вам право на более чем 1,048,576 сатоши, чтобы они были напрямую выплачены вам вознаграждением за блок.
В противном случае ваши сатоши будут сохранены Океаном до тех пор, пока общая сумма ваших вознаграждений не превысит эту сумму.

Все биткоины, временно сохраненные Океаном, находятся на этом адресе: [37dvwZZoT3D7RXpTCpN2yKzMmNs2i2Fd1n, все проверяемо на TimeChain.](https://mempool.space/address/37dvwZZoT3D7RXpTCpN2yKzMmNs2i2Fd1n)
Также возможен вывод ваших сатоши через Lightning с использованием BOLT12. Мы рассмотрим, как это настроить.

### Комиссии Пула

Комиссии варьируются от 0% до 2% в зависимости от выбранного шаблона блока.

## Прозрачность Океана

### Данные Участников

![signup](assets/1.webp)

Вся информация о пуле прозрачна, включая все данные пользователей. Чтобы понять этот момент, давайте рассмотрим пример:

[На панели управления Океана](https://ocean.xyz/dashboard) вы можете найти множество информации, такой как хешрейт за последние шесть месяцев, количество участников в пуле, общее количество добытых биткоинов и т. д.

Мы сосредоточимся на разделе "Участники". Вы можете видеть список всех участников с их средним хешрейтом за последние три часа, а также процентом **"долей"** и **"хеша"** по отношению к остальной части пула.
**"Доля %"** - это процент работы, предоставленной участником за последние восемь блоков по сравнению с остальной частью пула.
**"Хэш %"** - это процент средней хэш-мощности, предоставленной участником за последние три часа по сравнению с остальной частью пула.

![signup](assets/2.webp)

Вы заметите, что "Участники" идентифицируются по адресу Bitcoin. Вы можете кликнуть по любому из этих адресов для получения дополнительной информации.

Если взять первый, тот, что с наивысшей хэш-мощностью [1GRfspGGx4Ne66YotWuosUc4WeJLfGE3dZ](https://ocean.xyz/stats/1GRfspGGx4Ne66YotWuosUc4WeJLfGE3dZ), вы можете увидеть все детали об этом пользователе: хэш-мощность, количество добытых биткоинов, с каким блоком, и даже детали каждой из их машин (ASIC). Однако они остаются анонимными, как и на Bitcoin.

### Шаблон Блока

В верхнем левом углу на панели управления у вас есть "Следующий блок". На этой странице представлены четыре различных шаблона блоков. Ocean позволяет каждому участнику выбирать шаблон блока, который они хотят поддержать. Это не имеет прямого влияния на ваше вознаграждение. Когда пул добывает блок, все участники получают вознаграждение независимо от выбранного ими шаблона. Это просто позволяет каждому "голосовать" за шаблон блока, который им подходит.

![signup](assets/3.webp)

**CORE:** Комиссия 2%, это классический шаблон Bitcoin Core без фильтра, как написано на их странице "Включает транзакции и большинство спама"

**CORE+ANTISPAM:** Комиссия 0%, Bitcoin Core с фильтром против определенных транзакций, таких как Ordinals "Включает транзакции и ограничивает спам"

**OCEAN:** Комиссия 0%, Bitcoin Knot "Включает только транзакции и разумно малые данные"

**DATA-FREE:** Комиссия 0%, Bitcoin Knot "Включает только транзакции без каких-либо произвольных данных"

### Различие между Bitcoin Core и Bitcoin Knot
Bitcoin Core - это программное обеспечение, которое позволяет около 99% узлов Bitcoin во всем мире работать. Bitcoin является протоколом, что означает, что, как и в случае с Интернетом, где существует множество браузеров, может существовать несколько различных программных продуктов, сосуществующих на одной TimeChain. Однако, из-за беспокойства о совместимости и для ограничения риска ошибок, которые оставили бы неизгладимые следы на TimeChain, почти все разработчики Bitcoin работают над Bitcoin Core. Bitcoin Knots - это форк Bitcoin Core, что означает, что он делится большинством их кода, значительно ограничивая риск ошибок. Этот форк был создан Люком Дэшджром, который хотел применить более строгие правила, чем Bitcoin Core, не создавая хардфорк. Теперь Bitcoin Core и Bitcoin Knots сосуществуют благодаря консенсусу Накамото.

## Добавление Рабочего

Чтобы добавить рабочего, начните с выбора шаблона блока. Этот выбор определит URL пула, который нужно ввести в ваш майнер (ASIC).

- **CORE**: `stratum+tcp://core.mine.ocean.xyz:3202`
- **CORE+ANTISPAM**: `stratum+tcp://ordis.mine.ocean.xyz:3303`
- **OCEAN**: `stratum+tcp://mine.ocean.xyz:3334`
- **DATA-FREE**: `stratum+tcp://datafree.mine.ocean.xyz:3404`

Далее, в поле пользователя, введите адрес Bitcoin, который вы владеете. Вот список совместимых типов адресов:
- **P2PKH** (Оригинальный тип адреса. Начинается с “1”)
- **P2SH** (Мультиподпись или P2SH-Segwit. Начинается с “3”)
- **Bech32** (Segwit. Начинается с “bc”.)
- **Bech32m** (Taproot. Начинается с “bc”. Длиннее, чем Bech32.)

Если у вас несколько майнеров, вы можете ввести один и тот же адрес для всех из них, таким образом их хешрейты будут объединены и отображены как один майнер. Вы также можете различать их, добавив уникальное имя каждому. Для этого просто добавьте “.workername” после адреса Bitcoin.

Наконец, для поля пароля используйте `x`.

**Пример:**
Если вы выбрали шаблон **OCEAN**, ваш Bitcoin адрес `bc1q2ed8zxq8njqsznkp7gj84n0xwl9dp224uha2fv` и вы хотите назвать ваш майнер “Brrrr”, тогда вам нужно будет ввести следующую информацию в интерфейс вашего майнера:

- **URL**: `stratum+tcp://mine.ocean.xyz:3334`
- **ПОЛЬЗОВАТЕЛЬ**: `bc1q2ed8zxq8njqsznkp7gj84n0xwl9dp224uha2fv.Brrrr`
- **ПАРОЛЬ**: `x`

Через несколько минут после начала майнинга, вы сможете увидеть ваши данные на сайте Ocean, выполнив поиск по вашему адресу.

### Обзор панели управления
- **Доли в окне вознаграждения**: Эти данные указывают количество долей, работу, которую вы отправили в пул в окне последних 8 блоков, добытых пулом.
- **Оценочные вознаграждения в окне**: Оценка количества сатоши, которые вы заработаете с уже выполненной работой. Это не учитывает комиссии за транзакции, а только coinbase, новые биткойны, выпущенные сетью.
- **Оценочный доход следующего блока**: Оценка количества сатоши, заработанных, если блок будет добыт сейчас. Помните, если это значение меньше 1,048,576 сатоши, вы не получите сатоши напрямую на ваш адрес. Они будут отправлены на адрес Ocean, пока ваши заработки не превысят этот порог.

Ниже вы найдете график, отображающий историю вашего хешрейта до 6 месяцев.

![signup](assets/4.webp)

Здесь вы найдете ваш средний хешрейт за разные временные промежутки, от 60 секунд до 24 часов, а также историю блоков, добытых пулом, за которые вы внесли вклад и были вознаграждены.

![signup](assets/5.webp)

У вас есть возможность экспортировать файл CSV этой истории с помощью кнопки **Скачать CSV**.

![signup](assets/6.webp)

В следующем разделе вы найдете список всех майнеров, которые вы подключили к пулу с этим адресом. У вас, конечно, есть их индивидуальный хешрейт, но также количество сатоши, которые они индивидуально получили за свою работу.

![signup](assets/7.webp)

Вы можете кликнуть на **Псевдоним** любого майнера. Затем вы получите всю информацию, которую мы только что видели, но конкретно для этого майнера.

И внизу страницы некоторая дополнительная информация, где вы можете увидеть историю платежей по вашему адресу, сатоши, которые вы добыли, но еще не получили, и общее количество сатоши, которые вы добыли.

![signup](assets/8.webp)

Здесь вы можете видеть, что в поле **Оценочное время до минимальной выплаты** написано Lightning, потому что мы настроили предложение BOLT12.

### Настройка вывода средств через Lightning
Как вы уже поняли, Ocean стремится максимизировать прозрачность и минимизировать хранение (хранение ваших сатоши от вашего имени).
Поэтому для вывода средств через Lightning необходимо использовать **предложения BOLT12**. Это новый способ совершения платежа в сети Lightning, который начинает появляться в 2024 году и позволяет делать несколько вещей:
- Это повторно используемая платежная ссылка, позволяющая автоматические платежи и, в отличие от Lightning адреса, BOLT12 не требует хранения.
- Это также способ платежа, который предоставляет доказательство того, что платеж был совершен, чего не скажешь о LNURL.
- Очень важно, его можно использовать вместе с подписью Bitcoin, чтобы доказать, что вы являетесь владельцем как BTC адреса, так и предложения BOLT12.
На сегодняшний день (май 2024 года) существует немного решений для использования этого метода. В этом примере мы будем использовать сервер Start9 с Core Lightning. Когда другие инструменты, такие как Phoenix Wallet, например, интегрируют предложения BOLT12, этот учебник останется актуальным. Убедитесь, что у вас открыты каналы с входящей ликвидностью, иначе платежи не будут работать.

Начните с перехода на вашу панель управления на сайте Ocean, введя ваш BTC адрес, затем нажмите на вкладку **Configuration**.

![signup](assets/9.webp)

Мы скопируем текст **Description**, здесь:
`OCEAN выплаты для bc1q2ed8zxq8njqsznkp7gj84n0xwl9dp224uha2fv`

Теперь перейдите в интерфейс Core Lightning на вашем сервере Start9 (или в любой кошелек, способный предоставить предложение BOLT12).

![signup](assets/10.webp)

Нажмите на **Receive**.

Выберите **Offer**, затем вставьте ранее скопированный текст в поле **Description** и оставьте поле **Amount** пустым.

![signup](assets/11.webp)

Нажмите на **Generate Offer**.

![signup](assets/12.webp)

Вы сгенерировали повторно используемую и постоянную платежную ссылку, которая не требует центрального сервера, как это бывает с Lightning адресами. Скопируйте ссылку, а затем вернитесь на страницу Ocean.

В поле **Lightning BOLT12 Offer** вставьте платежную ссылку и оставьте поле **Block Height** со значением по умолчанию. Нажмите на **GENERATE**.

![signup](assets/13.webp)

Чтобы Ocean мог убедиться, что эта платежная ссылка действительно ваша без использования системы аккаунтов, вам нужно будет подписать сообщение, которое только что было сгенерировано, вашим приватным ключом, соответствующим Bitcoin адресу, который вы используете. Существует множество решений для подписи сообщения вашим приватным ключом. В этом учебнике мы рассмотрим пример BlueWallet, но метод тот же для всех кошельков.

![signup](assets/14.webp)

Предполагая, что ваш приватный ключ находится в BlueWallet (вы можете сделать то же самое с аппаратным кошельком), нажмите на соответствующий кошелек.

![signup](assets/15.webp)

Затем на **…** в правом верхнем углу.

![signup](assets/15bis.webp)

И выберите **Sign/Verify Message**.

![signup](assets/16.webp)

В этом окне у вас есть три поля: **Address**, **Signature**, и **Message**.

В поле **Address** введите ваш Bitcoin адрес. Если вернуться к нашему примеру, это адрес: `bc1q2ed8zxq8njqsznkp7gj84n0xwl9dp224uha2fv`.

Оставьте поле **Signature** пустым.
И вставьте сгенерированное сообщение в поле **Сообщение** на странице Ocean: `{"height":845900,"lightning_bolt12":"lno1pg7y7s69g98zq5rp09hh2arnypnx7u3qvf3nzufjv4jrs7ncwyuxu6n3wdaxu6msxank5wp5dcc8samv89j8qv3jx36kscfjvempvggz84uzkn26vyzq8y2mr2s8fv0j76wesq43dz72kqrk33nl2tk9j45s"}`Нажмите на **Подписать**.

Это сгенерирует криптографическую подпись, подтверждающую, что вы являетесь владельцем адреса `bc1q2ed8zxq8njqsznkp7gj84n0xwl9dp224uha2fv`, и эта подпись уникальна благодаря сообщению, предоставленному Ocean, сгенерированному из платежной ссылки BOLT12.

![signup](assets/17.webp)

Скопируйте подпись и вставьте ее на странице Ocean, затем нажмите на **ПОДТВЕРДИТЬ**.

![signup](assets/18.webp)

Вы должны увидеть сообщение о подтверждении.

![signup](assets/19.webp)

Теперь перейдите на вкладку **Моя Статистика**. В верхней части отображается дополнительная информация с платежной ссылкой BOLT12, которую вы ранее сгенерировали с помощью Core Lightning на Start9.

![signup](assets/20.webp)
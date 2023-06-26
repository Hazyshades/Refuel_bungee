# Refuel-script
Refuel скрипт Спекуляции

# Скрипт раскидывает деньги на газ ИЗ сетей:
BSC, AVALANCHE, FANTOM, POLYGON, OPTIMISM, ARBITRUM, ETHEREUM.

# Скрипт раскидывает деньги на газ В сети:
BSC, AVALANCHE, FANTOM, POLYGON, OPTIMISM, ARBITRUM, ETHEREUM, AURORA, GNOSIS, ZKSYNC, POLYGON_ZKEVM.

Исполняемый файл - ``execute.py``, свои адреса кошельков и приватники нужно вставлять в файл data.csv, там же все настройки скрипта по тому, сколько раскидывать в другие сети в **НАТИВНОЙ МОНЕТЕ СЕТКИ ОТКУДА ВЫ РАСКИДЫВАЕТЕ!**

**Ex:** вы раскидываете из сети BSC в сеть ARB, вам нужно указывать в **BNB**!

# В файле ``config.py`` производится первичная настройка, что значат каждая из переменных:
``WAIT_MIN`` - время, сколько ждать между кошельками.
``FROM_CHAIN`` - сеть, откуда вы отправляете нативную монету. Писать с заглавной буквы, для лёгкости добавил рядов в комментариях сети.
``MAX_GAS`` - максимальный газ в нативной монете, если он будет превышать это значение, скрипт будет ждать.

# В файле ``data.csv`` производится основная настройка, что значат каждая из колонок:

1) ``DO`` - нужно ли делать этот кошелек, чтобы скрипт начал его делать, нужно поставить английскую X, без неё не важно, что написано дальше. После окончания прогона, там будет написано "Done".
2) ``Name``  - название кошелька для логов.
3) ``Wallet``  - адрес кошелька в EVM-сети.
4) ``Privat_key`` - приватный ключ от кошелька.

Дальше идут названия сетей вида ``BSC/AVALACNHE`` и ``BSC_VALUE/AVALANCHE_VALUE``, у всех у них функции работают одинаково, а именно:

1) ``NETWORK(ex. BSC)`` - название сети куда ВАМ НУЖНО ОТПРАВИТЬ НАТИВНЫЕ МОНЕТКИ. Стандартно там стоит DONE, значит скрипт не будет туда переводить деньги. Чтобы скрипт начал переводить туда монетки, нужно **УДАЛИТЬ DONE и ОСТАВИТЬ ПОЛЕ ПУСТЫМ**. 
2) ``NETWORK_VALUE(ex BSC_VALUE)`` - это количество нативной монеты сети, откуда вы отправляете. Например, вам нужно отправить 1$ из сети ARB в сеть OPT. Открываем текущий курс ETH(условно, он будет равен 2000$), и считаем. Значит нам нужно отравить 1/2000 ETH, то есть 0.0005 ETH. Кроме этого, скрипт имеет функцию "отправить все средства". Для этого в поле нужно вписать значение ``999.0``. Но у функции Refuel у bungee есть ограничения. Для корректной работы, не выствляйте значения ниже 1$ или выше 10$, во избежание ошибок.

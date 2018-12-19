### Общий класс:
* `read() write()` - используются в других функциях storage.py
* `clear()` - очищает файл от данных
* `hash_insert()` - используется в других функциях storage.py

### Блоки:
* `find_all() # из общего класса BaseDB()`

input: Инициализацию можно проводить двойным путем
    
    bcdb = BlockChainDB() #создание базы хранения блоков
    blockchain = bcdb.find_all()
    
либо
    
    blockchain = BlockChainDB().find_all()
    
output: Выведет данные - цепочку - (в виде списка) из всего документа blockchain (просто пример, что там может храниться)
    
    [{"index": 0, "timestamp": 1528972068, "tx": ["86dc2f1acfd239004b8a7b515241070204d5da0ccebf82140416623d3380766d"], "previous_block": "", "nouce": 16648, "hash": "00000fee282315563171dccc13a2eab380ee82351e7efa6ab13249754f283758"},
    {"index": 1, "timestamp": 1528972068, "tx": ["415b22b74f47513d3f82b6d4b7ff59185814011f6ae04dd364dc9ae918bc32b2"], "previous_block": "00000fee282315563171dccc13a2eab380ee82351e7efa6ab13249754f283758", "nouce": 13309, "hash": "000074b206a81fb748a382cf105692c19fd5297a7dd2f14af7747bf54067105b"},
    {и так далее, до самого последнего словаря в документе}]

* `find()`:

input: Инициализация такая же, как у предыдущего
    
    blockchain = BlockChainDB().find()

output: Выведет только тот блок (в виде словаря), чей hash ему нужен.
    
    {"index": 1, "timestamp": 1528972068, "tx": ["415b22b74f47513d3f82b6d4b7ff59185814011f6ae04dd364dc9ae918bc32b2"], "previous_block": "00000fee282315563171dccc13a2eab380ee82351e7efa6ab13249754f283758", "nouce": 13309, "hash": "000074b206a81fb748a382cf105692c19fd5297a7dd2f14af7747bf54067105b"}

* `last()`:

input: Инициализация

    last_block = BlockChainDB().last()

output: Последний блок (в виде словаря) в цепочке. Цепочка - это весь документ. 

    см. предыдущее

* `insert():`

input: Хотим сохранить данные data? Просто вставляем строку
    
    BlockChainDB().insert(data)


### Транзакции:

* `find_all() # из общего класса BaseDB()`

input: Инициализацию можно проводить двойным путем
    
    txdb = TransactionDB() #создание базы хранения транзакций
    transactions = txdb.find_all()
    
либо
    
    transactions = TransactionDB().find_all()
    
output: Выведет все данные (в виде списка) из документа transactions (просто пример, что там может храниться).
    
    [{"timestamp": 1528972068, "vin": [], "vout": [{"receiver": "1L8Q3xJyk5MnWoV1Qz6sfT57yGB6bA7DgR", "amount": 20, "hash": "1962d0500de06d90e74249659d12640b32eafbe1ba02fea578637f25464eb220"}], "hash": "86dc2f1acfd239004b8a7b515241070204d5da0ccebf82140416623d3380766d"},
    {"timestamp": 1528972068, "vin": [], "vout": [{"receiver": "1L8Q3xJyk5MnWoV1Qz6sfT57yGB6bA7DgR", "amount": 20, "hash": "2ef3d0fa1367d79a74e8e621d132448db8ec0691be9bc8fc32eea15714d1b088"}], "hash": "415b22b74f47513d3f82b6d4b7ff59185814011f6ae04dd364dc9ae918bc32b2"},
    {"timestamp": 1528972135, "vin": [{"hash": "9a9e45e69fdb8c1efa14784b996632d0fb99958ee33ef84c2bd31a8878180547", "amount": 20}], "vout": [{"receiver": "145wtdP4dwgvMkYp2Jv6GWHmRkYQCnqvuU", "amount": 10, "hash": "b9453b1f8cae8dd11214b578e56dfc37ba841eb394c837afa984aef51b699edc"}, {"receiver": "1L8Q3xJyk5MnWoV1Qz6sfT57yGB6bA7DgR", "amount": 10, "hash": "b1389953a2767abf51a0361d767bd17a33492eccebdc7daaf8f082cbb283a17d"}], "hash": "3a12a995d43eb72d12251d1e33f30c0301840a267c6b64e2a69e9adc254247a8"},
    {"timestamp": 1529034991, "vin": [], "vout": [{"receiver": "1L8Q3xJyk5MnWoV1Qz6sfT57yGB6bA7DgR", "amount": 20, "hash": "7dc0fc548ecc3a5e489e99a3fbff9436a241cf9993892d1534c4dd8f063cfbd2"}], "hash": "26ca26b3d9ab07dacec72154b2b8dea86d29cdfbac8f543f9fe393cfbd7ad116"}]

* `insert()`:

input: Хотим сохранить данные data? Просто вставляем строку
    
    TransactionDB().insert(data)


### Аккаунты:

* `get_account()`:

 input: хотим получить данные из файла account:
    
    account = AccountDB().get_account()

output: набор того (в виде словаря), что хранится в аккаунте. Например:
    
    {"pubkey": "9c18ba33bf94cc8822fa97c3d2c9425da043ca56", "address": "1L8Q3xJyk5MnWoV1Qz6sfT57yGB6bA7DgR"}, {"pubkey": "2beb7ff7f0a87082a54645df38a4d482dccafb44", "address": "1AdoyhS4Wbq26PzzevxaYnkaQU5NgyJWFr"}

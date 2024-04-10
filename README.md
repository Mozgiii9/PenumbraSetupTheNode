![image](https://github.com/Mozgiii9/PenumbraSetupTheNode/assets/74683169/6f15c932-475f-4087-a8d7-e2f423a5c549)


## Дата создания гайда: 10.04.2023


## Разбор проекта Penumbra + Инструкция по установке ноды(Ceremony Phase 2)


[Penumbra](https://penumbra.zone/) — это layer-1 блокчейн, который ставит своей целью создать платформу для безопасных и приватных транзакций, стейкинга и торговли между сетями. В разработке Penumbra используется технология криптографии с нулевым разглашением: zk-SNARK. 


Интересно, что Penumbra сможет связываться с другим блокчейнами по протоколу связи IBC (например, со всей экосистемой Cosmos), но при этом не будет строиться на Cosmos SDK. Сделано это с целью исключения из системы понятия счетов для обычных пользователей. Какие-либо долгосрочные идентификаторы будут иметь только валидаторы. Это сделает сеть Penumbra ещё более приватной. 

Проект собрал $4.75 млн. в seed-раунде с участием tier 2-3 фондов Dragonfly Capital, Lemniscap и других. 

В читателях [Twitter](https://twitter.com/penumbrazone) проекта отмечаем сбежавшихся представителей крупных фондов: [Dan Robinson](https://twitter.com/danrobinson) и [Dave White](https://twitter.com/_Dave__White_) ([Paradigm](https://twitter.com/paradigm)), [Niraj Pant](https://twitter.com/niraj) и [tekin salimi](https://twitter.com/tekinsalimi) ([Polychain](https://twitter.com/niraj)), а также экосистемных разработчиков. 

У проекта продолжается тестнет с ~марта 2022 года. Даже несмотря на то, что ранее мы не участвовали в тестнете, у нас все равно есть возможность установить ноду. Установка достаточно простая, космических наград от проекта не жду, но на анти-фомо ноду можно поставить. Тем более, что для установки нам понадобится простой по характеристикам сервер:

**CPU: 2 ядра, чем больше частота - тем лучше;**

**RAM: 4GB;**

**Storage: 100GB of storage (SSD or NVME)**

**Обратите внимание на версию Ubuntu:**

**OS: Ubuntu 22.04**

## Перейдем к установке ноды:

**1. Обновление пакетов:**

```
sudo apt update && sudo apt upgrade -y
```

*При возникновении розовых окон просто жмите ENTER.*

**2. Установка необходимого ПО:**

```
sudo apt install make clang pkg-config libssl-dev build-essential tmux -y
```

```
sudo apt-get install git-lfs
```

**3. Продолжаем установку. Выполним команды, связанные с запуском Penumbra:**

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
```

*Команда выше вставляется целиком. Обратите внимание на скрин ниже:*

![image](https://github.com/Mozgiii9/PenumbraSetupTheNode/assets/74683169/3385acb4-97c2-4522-9d77-192603f52694)

Просто нажимаем ENTER и ждем конца установки.

![image](https://github.com/Mozgiii9/PenumbraSetupTheNode/assets/74683169/51c9996d-9666-4ad1-985d-d2500fd0bb54)

*Скрин выше говорит о том, что все успешно установилось.*

**Следующая команда идет целиком. Вставляем в терминал и нажимаем ENTER:**

```
curl -sSfL -O https://github.com/penumbra-zone/penumbra/releases/download/v0.71.0/pcli-x86_64-unknown-linux-gnu.tar.xz
unxz pcli-x86_64-unknown-linux-gnu.tar.xz
tar -xf pcli-x86_64-unknown-linux-gnu.tar
sudo mv pcli-x86_64-unknown-linux-gnu/pcli /usr/local/bin/
pcli --version
```

![image](https://github.com/Mozgiii9/PenumbraSetupTheNode/assets/74683169/6c7fcbbb-8295-45ac-ac8b-751c8913260a)

*Должен появиться такой вывод.*

**4. Создаем кошелек, внимательно анализируем вывод сервера. В выводе будет Seed фраза, сохраняем ее в надежное место:**

```
pcli init soft-kms generate
```

![image](https://github.com/Mozgiii9/PenumbraSetupTheNode/assets/74683169/d6c8f65f-3cae-43c8-8b2a-4678784e33b8)


Отлично. Теперь узнаем адрес кошелька. Для этого переходим в браузер Chrome и качаем расширение [Penumbra Wallet](https://chromewebstore.google.com/detail/penumbra-wallet/lkpmkhpnhknhmibgnmmhdhgdilepfghe)

![image](https://github.com/Mozgiii9/PenumbraSetupTheNode/assets/74683169/1afd8f1a-ddcc-41aa-8deb-b1caf289380b)

![image](https://github.com/Mozgiii9/PenumbraSetupTheNode/assets/74683169/488be2e6-2e47-4009-b256-63d5a02d6ea6)

Запускаем расширение, импортируем аккаунт путем ввода Seed фразы. Появится адрес Вашего кошелька и начнется процесс синхронизации. Копируем адрес кошелька и переходим в [Discord](https://discord.com/invite/GZqQXuZVqx) проекта за тестовыми токенами в ветку "testnet-faucet". В ветке "testnet-faucet" отправляем адрес своего кошелька, в ответ бот должен ответить, что токены были успешно отправлены. 

**5. Вернемся к серверу. Выполним команду:**

```
screen -S ceremony
```

**6. Следом выполним команду участия в церемонии:**

```
pcli ceremony contribute --phase 2 --bid 60penumbra
```

Пойдут логи, чтобы выйти из окна screen можно использовать комбинацию клавиш CTRL + A + D.

**На данном этапе установка ноды подошла к концу. Проверить работоспособность ноды можно при помощи команды:**

```
screen -ls
```

![image](https://github.com/Mozgiii9/PenumbraSetupTheNode/assets/74683169/3e7dd20e-5f6e-45e0-8e1b-0a72f5132b79)


После чего нужно узнать ID сессии (первые 5 цифр перед "."). Подключаемся к окну с логами командой:

```
screen -r <ID_ОКНА> # example : screen -r 26578
```

## Официальные ссылки проекта:

- **Веб-сайт:** [перейти](https://penumbra.zone/)
- **Discord:** [перейти](https://discord.gg/GZqQXuZVqx)
- **Twitter:** [перейти](https://twitter.com/penumbrazone)
- **Github:** [перейти](https://github.com/penumbra-zone)

## Обязательно проведите собственный ресерч проектов перед тем как ставить ноду. Сообщество NodeRunner не несет ответственность за Ваши действия и средства. Помните, проводя свой ресёрч, Вы учитесь и развиваетесь.

**Связь со мной:** [Telegram(@M0zgiii)](https://t.me/m0zgiii)

**Мои соц. сети:** [Twitter](https://twitter.com/m0zgiii)


# Bot de telegram

Para poder trabajar con el bot de Telegram necesitamos las herramientas básicas, en nuestro caso:

* [Go](Lenguajes/Go)
* [Git](Herramientas/Git)

## Token de acceso

Para poder comunicarnos con el bot de Telegram necesitamos un `token` para poder identificarnos.

Para ello bastara con hablar en Telegram con **@BotFather**, ejecutar el comando **/newbot** y seguir las instrucciones. Al final del proceso veremos este mensaje:

```
Use this token to access the HTTP API:
123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11
Keep your token secure and store it safely, it can be used by anyone to control your bot.
```

## Librerías

Necesitamos instalar las siguientes librerías para poder trabajar en este proyecto

* [telegram-bot-api](https://github.com/go-telegram-bot-api/telegram-bot-api): Bindings de Go para la API de Telegram.
* [TOML](https://github.com/BurntSushi/toml): Parseador de TOML para Go.

Para instalar estas librerías ejecutaremos estos comandos.

```bash
go get -u github.com/go-telegram-bot-api/telegram-bot-api
go get github.com/BurntSushi/toml
```


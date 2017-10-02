# IONIC 3
## Como usar

```
docker run -ti --rm -p 8100:8100 -p 35729:35729 kidoncio/ionic-docker
```
Se você já possuí um projeto em andamento:

```
docker run -ti --rm -p 8100:8100 -p 35729:35729 -v /caminho/do/seu/projeto-ionic/:/myApp:rw kidoncio/ionic-docker:latest
```

### Automação
Usando como alias:

```
alias ionic="docker run -ti --rm -p 8100:8100 -p 35729:35729 --privileged -v /dev/bus/usb:/dev/bus/usb -v ~/.gradle:/root/.gradle -v /caminho/do/seu/projeto-ionic/:/myApp:rw kidoncio/ionic-docker ionic"
```

> Devido a um bug no ionic, se você quiser usar o ionic serve, você deve usar a opção --net host:
```
alias ionic="docker run -ti --rm --net host --privileged -v /dev/bus/usb:/dev/bus/usb -v ~/.gradle:/root/.gradle -v /caminho/do/seu/projeto-ionic/:/myApp:rw kidoncio/ionic-docker ionic"
```

Basta abrir o http://localhost:8100 e estará tudo supimpa.

### Tests no Android
Você pode tranquilamente testar no seu android, basta ter certeza de que o debug está habilitado nele.

```bash
cd myApp
ionic platform add android
ionic build android
ionic run android
```

## FAQ
* A aplicação não está instalada no meu equipamento
  * Tente: `docker run -ti --rm -p 8100:8100 -p 35729:35729 --privileged -v /dev/bus/usb:/dev/bus/usb -v \$PWD:/myApp:rw kidoncio/ionic-docker adb devices` e o seu aparelho deve aparecer :D
* Se você não estiver conseguindo usar o `adb devices`, isso se deve pelo fato de já estar rodando em alguma parte do seu sistema. Tente matar o processo (`adb kill-server`) e tente novamente.

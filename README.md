# Network Education CGNAT Logger

[![N|Solid](http://network.education/static/img/mvp_landing_logo.png)](http://network.education)

Daemon para logs de NAT que respeita as obrigações do Marco Civil da Internet 


# Recursos

  - Compatível com RouterOS ( Mikrotik )
  - Pasta de armazenamento configurável
  - Compatível com armazenamento na nuvem ( mega, drive, dropbox )
  - Compactação bz2 automática
  - Rotação automática de hora em hora

# Estatísticas
Consumo de recursos ( 400MB Aprox ):
  - 7% de cpu de um core de 2.8Ghz
  - 8-10Mb por arquivo por hora

# Instalação ( Ubuntu Server ):
> Recomendamos uma instalação limpa do Ubuntu Server em 64bits

### Preparando o Ambiente:

Todos os comandos devem ser executados como root e/ou sudo.

Instalação das dependências:

```sh
$ apt-get install python-pip git
$ pip install pathlib
```

Instalando o sistema...

```sh
$ cd /
$ git clone https://github.com/elizandropacheco/neteducgnatloggerd.git neteducgnatloggerd
$ cd neteducgnatloggerd
$ ./geraserial
```
 
* Enviar o serial para a network education ( caso vc tenha adiquirido licença )

A Network Education retornará a você a licença e as instruções de exportação, então:

```sh
$ touch /etc/<LICENÇA>
```

Edite as variáveis no arquivo start ( porta e local de armazenamento ) e depois, inicie o daemon:

```sh
$ vim start
$ screen -m -d sh start
```

## Comandos auxiliares
Para verificar o software rodando em tempo real:
```sh
$ screen -r
```

Para sair, aperte ESC, digite :detach e pressione ENTER




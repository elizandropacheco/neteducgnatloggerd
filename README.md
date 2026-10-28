<div align="center">

<img src=".github/assets/banner.svg" alt="NetEduc CGNAT Logger — logs de NAT via syslog para o Marco Civil da Internet" width="100%">

<br>

**Daemon para provedores que recebe os logs de NAT (CGNAT) do roteador por syslog e os guarda compactados, hora a hora, para cumprir as obrigações de guarda do Marco Civil da Internet.**

[![Licença](https://img.shields.io/github/license/elizandropacheco/neteducgnatloggerd?style=for-the-badge&label=licen%C3%A7a&color=1F232F)](LICENSE)
[![Repositório](https://img.shields.io/badge/reposit%C3%B3rio-p%C3%BAblico-2A2F3D?style=for-the-badge&logo=github)](https://github.com/elizandropacheco/neteducgnatloggerd)
[![Último commit](https://img.shields.io/github/last-commit/elizandropacheco/neteducgnatloggerd?style=for-the-badge&label=%C3%BAltimo%20commit&color=04B4EF)](https://github.com/elizandropacheco/neteducgnatloggerd/commits)
[![Estrelas](https://img.shields.io/github/stars/elizandropacheco/neteducgnatloggerd?style=for-the-badge&label=estrelas&color=A0CC3B)](https://github.com/elizandropacheco/neteducgnatloggerd/stargazers)

![Python](https://img.shields.io/badge/Python-2.7-3776AB?style=flat-square&logo=python&logoColor=white)
![Cython](https://img.shields.io/badge/Cython-bin%C3%A1rio-FFD43B?style=flat-square)
![Linux](https://img.shields.io/badge/Linux-x86--64-FCC624?style=flat-square&logo=linux&logoColor=black)
![Ubuntu](https://img.shields.io/badge/Ubuntu_Server-64_bits-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![MikroTik](https://img.shields.io/badge/RouterOS-MikroTik-293239?style=flat-square&logo=mikrotik&logoColor=white)

[Sobre](#sobre) · [Uso](#uso) · [Licença](#licença)

</div>

---

> [!WARNING]
> Projeto legado, publicado em 2017. Os executáveis foram compilados para Linux x86-64 com Python 2.7, que
> não recebe mais atualizações desde 2020. Avalie o uso em produção com cuidado.

## Sobre

O **Network Education CGNAT Logger** (`neteducgnatd`) é um daemon de logs de NAT que respeita as obrigações do
Marco Civil da Internet. Ele escuta **syslog via UDP** na porta configurada, grava as mensagens do roteador em
uma pasta de armazenamento e gera **um arquivo compactado em bz2 por hora** (nome no formato
`DD-MM-AAAA-HH.bz2`).

O daemon é licenciado por equipamento: o `geraserial` lê o serial da placa-mãe do servidor (via `dmidecode`)
e a **Network Education** devolve a licença correspondente. Sem ela, o daemon informa que o sistema não está
licenciado para o dispositivo.

### Recursos

- Compatível com RouterOS (MikroTik).
- Pasta de armazenamento configurável.
- Compatível com armazenamento na nuvem (MEGA, Drive, Dropbox).
- Compactação bz2 automática.
- Rotação automática de hora em hora.

### Consumo de recursos

Medição original do projeto:

- aprox. 400 MB;
- 7% de CPU de um núcleo de 2,8 GHz;
- 8 a 10 MB por arquivo por hora.

### Conteúdo do repositório

| Arquivo | Função |
|---|---|
| `neteducgnatd` | daemon de logs (executável Linux x86-64) |
| `geraserial` | gera o serial do servidor para o pedido de licença (executável Linux x86-64) |
| `start` | script de inicialização com a pasta de logs e a porta |

## Uso

> [!NOTE]
> Recomendamos uma instalação limpa do **Ubuntu Server 64 bits**. Todos os comandos devem ser executados como
> root ou com `sudo`.

### 1. Dependências

```bash
apt-get install python-pip git
pip install pathlib
```

### 2. Instalação

```bash
cd /
git clone https://github.com/elizandropacheco/neteducgnatloggerd.git neteducgnatloggerd
cd neteducgnatloggerd
./geraserial
```

Envie o serial gerado para a Network Education (caso você tenha adquirido a licença). A Network Education
devolve a licença e as instruções de exportação do roteador; então crie o arquivo de licença:

```bash
touch /etc/<LICENÇA>
```

### 3. Configuração e execução

Edite as variáveis do arquivo `start` (porta e local de armazenamento). Por padrão, ele usa a pasta
`/neteducgnatloggerd/logs` e a porta `666`:

```sh
PASTA="/neteducgnatloggerd/logs"
PORTA="666"
```

Depois, inicie o daemon em uma sessão `screen` destacada:

```bash
vim start
screen -m -d sh start
```

### Comandos auxiliares

Para acompanhar o software em tempo real:

```bash
screen -r
```

Para sair sem encerrar o daemon, pressione `Ctrl+A`, digite `:detach` e pressione `Enter`.

## Agradecimentos

- **Uesley Correa**: desenvolvedor e motivador do projeto (e quem pagou a cerveja).
- **Guilherme Ramires**: contribuições em firewall e lógica de captura.

## Licença

Distribuído sob a licença **MIT**. © 2017-2026 Elizandro Pacheco. Veja [LICENSE](LICENSE).

## Autor

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/elizandropacheco">
        <img src="https://github.com/elizandropacheco.png" width="100" alt="Elizandro Pacheco"><br>
        <sub><b>Elizandro Pacheco</b></sub>
      </a><br>
      <sub>Desenvolvedor e autor do projeto</sub>
    </td>
  </tr>
</table>

[![Site](https://img.shields.io/badge/elizandropacheco.io-04B4EF?style=flat-square&logo=googlechrome&logoColor=white)](https://elizandropacheco.io)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/elizandropacheco)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/elizandropacheco)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=flat-square&logo=youtube&logoColor=white)](https://www.youtube.com/@ElizandroPacheco)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=flat-square&logo=instagram&logoColor=white)](https://www.instagram.com/elizandropacheco)

<div align="center">
<sub>Feito por <a href="https://github.com/elizandropacheco">Elizandro Pacheco</a></sub>
</div>

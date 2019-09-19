## Instruções para instalação e uso do container

**1**. Primeiro, instale e configure o LXD. [Este documento](https://linuxcontainers.org/lxd/getting-started-cli/#getting-the-packages) contém pacotes para várias distros. Se você está usando ubuntu, siga os passos abaixo:

```bash
$ sudo add-apt-repository ppa:ubuntu-lxc/lxc-stable
$ sudo apt update
$ sudo apt install lxd
$ sudo lxd init   # Use as opções padrões
```  

**2**. Baixe a [imagem](https://static.pwn2win.party/pwn2win2019.tar.gz) do container LXC e importe no LXD:

```bash
$ lxc image import pwn2win2019.tar.gz --alias=pwn2win2019
```

**3**. Crie uma instância a partir da imagem:

```bash
$ lxc launch pwn2win2019 pwn2win
```
**4**. Certifique-se que está com a última versão do repositório:

```bash
$ lxc exec pwn2win -- git pull
```

**5**. Agora, **OU** você pode gerar novas chaves e [adicioná-las](https://github.com/settings/keys) no GitHub:
```bash
$ lxc exec pwn2win -- ssh-keygen -t ed25519
$ lxc exec pwn2win -- cat .ssh/id_ed25519.pub
 ```

OU ainda pode usar suas próprias chaves, da máquina host:
```bash
$ lxc file push ~/.ssh/id_* pwn2win/root/.ssh/
```


**6**. Siga as instruções do [README](https://github.com/pwn2winctf/2019/blob/master/README.pt.md) prefixando os comandos com *lxc exec pwn2win --*. Por exemplo, se você for o capitão do time, registre a equipe digitando *lxc exec pwn2win -- ./ctf init*. Se quiser spawnar uma shell, use: *lxc exec pwn2win sh*.

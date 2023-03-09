
# Guia para instalação WSL, Oh my ZSH + PowerLevel10k

Guia e tutorial para a utilização do Linux dentro do ambiente Windows com plugins e funcionalidades visando a melhor experiência para desenvolvimento.

## Sumário

- [Recomendações Iniciais](#recomendacoes-iniciais)
- [O que é WSL?](#features)
- [Por que usar WSL 2 para desenvolvimento?](#installation)
- [Instalação do WSL 2](#configuration)
- [O que é Z Shell?](#fonts)
- [Instalando ZSH](#try-it-in-docker)
- [O que é Oh My Zsh?](#license)
- [Oh My Zsh](#faq)
- [Troubleshooting](#troubleshooting)

## Recomendações Iniciais

- [Instale uma fonte adequada](#fontes)
- [Cheque se sua máquina tem os requísitos minimos](#requisitos-minimos)
## O que é WSL?

WSL significa "Windows Subsystem for Linux" e é uma camada de compatibilidade dentro do sistema operacional Windows que permite a execução de aplicativos Linux diretamente no Windows, sem a necessidade de uma máquina virtual separada. Isso permite que os usuários executem aplicativos e ferramentas Linux em seus sistemas Windows sem ter que instalar um sistema operacional Linux separado.

No ano de 2019, a Microsoft divulgou uma nova edição do WSL, conhecida como WSL 2. Essa nova versão apresentou melhorias em relação à primeira:

- Capacidade de executar o kernel completo do Linux.
- Melhoria no desempenho de acesso aos arquivos internos do Linux.
- Compatibilidade completa com as chamadas de sistema.
O lançamento oficial do WSL 2 ocorreu em 28 de maio de 2020.

Para entender as diferenças entre as versões, consulte o seguinte link: https://docs.microsoft.com/pt-br/windows/wsl/compare-versions
## Por que usar WSL 2 para desenvolvimento?

Existem várias razões pelas quais o WSL pode ser uma excelente escolha para desenvolvimento de software:

1. **Acesso a ferramentas Linux** - O WSL permite que os desenvolvedores acessem e usem as ferramentas de linha de comando do Linux, muitas das quais são amplamente utilizadas na comunidade de desenvolvimento de software, como o Git, Vim, GCC, entre outras. Isso pode ser útil para desenvolvedores que estão acostumados a trabalhar em ambientes Linux e querem continuar usando essas ferramentas no Windows.

2. **Suporte para ambientes de desenvolvimento populares do Linux** - O WSL suporta ambientes de desenvolvimento populares do Linux, como o Ruby on Rails, o Node.js e o Python. Isso significa que os desenvolvedores podem continuar usando esses ambientes de desenvolvimento populares sem ter que mudar para o Linux.

3. **Facilidade de configuração** - O WSL é fácil de configurar e usar, os desenvolvedores podem instalar rapidamente suas ferramentas de desenvolvimento favoritas, sem ter que passar por todo o processo de configuração de um ambiente Linux completo.

Em resumo, o WSL pode ser uma excelente escolha para desenvolvimento de software, permitindo que os desenvolvedores acessem ferramentas Linux, suportem ambientes de desenvolvimento populares do Linux, configurem facilmente seus ambientes de desenvolvimento e garantam a compatibilidade com o Windows.
## Instalação do WSL 2

> ## Windows 11
Para instalar o WSL no Windows 11 ou Windows 10 na versão 2004 ou superior basta abrir um PowerShell ou um Prompt de comando e executar:
```bash
 wsl --install
```
Este comando irá instalar todas as dependências do WSL instalando o Ubuntu como o Linux padrão.

Se você quiser instalar uma distribuição diferente, execute o comando `wsl -l -o` , será listado todas as versões de Linux disponíveis. Instale a versão escolhida com o comando `wsl --install -d nome-da-distribuicao`.

Recomendamos manter-se com Ubuntu por ser uma distribuição popular e que já vem com diversas ferramentas pre-instaladas.

> ## Windows 10
Caso você esteja em uma versão mais antiga do Windows 10, execute os seguintes comandos no PowerShell em modo administrador:

``` bash
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Abra o PowerShell e digite o comando `wsl`, se não funcionar reinicie sua máquina.

#### Definindo WSL 2 como sua versão padrão
Abra o Terminal/PowerShell e execute este comando:
```bash
wsl --set-default-version 2
```

***⚠️ Caso mostre que você não tenha o Kernel***<br>

Faça o download do Kernel 2 do WSL 2 nesse link: [https://docs.microsoft.com/pt-br/windows/wsl/wsl2-kernel](https://docs.microsoft.com/pt-br/windows/wsl/wsl2-kernel) e instale o pacote.

## Escolha sua distro pela Microsoft Store
Na Microsoft Store há diversas opções distribuições Linux para você baixar e utilizar.
<br><br>
![microsoft-store-print](./assets/linux-sc.png)

Ao iniciar o Linux instalado, você deverá criar um nome de usuário, que pode ser o mesmo da sua máquina, e uma senha, este será o usuário root da sua instância WSL.

<hr>
Se tudo deu certo até aqui, parabéns, seu WSL2 já está funcionando! 🥳<br><br>

## O que é Z shell?

Z Shell, também conhecido como zsh, é um interpretador de comandos de shell para sistemas Unix-like, como Linux e macOS. Ele é uma alternativa mais poderosa e avançada ao shell padrão Bash.

O Z Shell tem muitos recursos úteis, incluindo autocompletar, histórico de comandos aprimorado, substituição de nomes de arquivos com wildcards (expressões regulares), suporte a várias abas e janelas, personalização da aparência e do comportamento do shell e muito mais. Além disso, ele tem um sistema de plugin robusto que permite estender ainda mais suas funcionalidades.

Outro recurso útil do Z Shell é o seu "prompt de diretorio", que mostra o diretório atual em que o usuário está trabalhando no shell, bem como outras informações relevantes. Isso pode ajudar a evitar erros ao executar comandos em diretórios errados e a tornar o trabalho no shell mais eficiente.

O Z Shell pode ser instalado em muitas distribuições Linux e macOS por meio de gerenciadores de pacotes ou por meio de download direto do site oficial. Ele é frequentemente recomendado para usuários avançados de linha de comando que desejam uma experiência de shell mais poderosa e personalizável.

### *Por que utilizar o ZSH vai melhorar a sua experiência utilizando o terminal?*
- **Personalização**: o Z Shell é altamente personalizável e você pode ajustar muitas configurações para adaptar o shell às suas preferências. Isso pode incluir personalizar o prompt, criar aliases para comandos frequentemente usados, configurar atalhos de teclado personalizados e muito mais. Neste guia irei mostrar o **PowerLevel10k** um plugin versátil, extremamente útil que deixará está funcionalidade de customização super simples e que pode cobrir a maioria das suas necessidades.

- **Compatibilidade com Bash**: o Z Shell é compatível com a maioria dos comandos do Bash, o que significa que você pode usar scripts e comandos existentes sem precisar reescrevê-los. Além disso, o Z Shell tem recursos adicionais que o Bash não possui, portanto, você pode aproveitar o melhor dos dois mundos.
## Instalando ZSH 
Para instalar o Z Shell abra o app Terminal do Windows para acessar o seu WSL <br><br>
![windows-terminal-search](./assets/terminal-neo.gif)

No terminal, em ambiente Linux, atualize os seus pacotes e dê upgrade nos programas do seu sistema utilizando os comandos abaixo:
```bash
sudo apt update && sudo apt upgrade
```
**Ubuntu, Debian & derivatives (Windows 10 WSL | Native Linux kernel with Windows 10 build 1903)** <br>
Para instalar o zshell utilize:
```bash
sudo apt install zsh
```
Para checar se o zsh foi devidamente instalado, reinicie seu terminal e digite, zsh --version, o comando deve retornar algo como: `zsh 5.8.1` 

## O que é Oh My Zsh?
Oh My Zsh é um framework de código aberto para gerenciar sua configuração do Z Shell (zsh). Ele fornece uma maneira fácil de instalar e gerenciar temas, plugins e outras configurações do Z Shell. Com o Oh My Zsh, você pode personalizar facilmente a aparência e o comportamento do seu shell, adicionar novas funcionalidades e tornar sua experiência de linha de comando mais produtiva e agradável.

O Oh My Zsh vem com vários recursos úteis pré-instalados, como autocompletar, sugestões de comandos, substituição de nomes de arquivos com wildcards, temas de aparência atraente e muito mais. Além disso, existem centenas de plugins disponíveis para o Oh My Zsh, que podem ser facilmente adicionados e configurados para atender às suas necessidades.

Vamos utilizar o Oh My Zsh para instalar o PowerLevel10k, um plugin que vai deixar nosso terminal charmoso e intuitivo, mostrando diretorios e status do Git diretamente nas linhas de escrita do prompt.

## Oh My Zsh
> ### Pre-requisitos:

- Ter Git instalado (Por padrão o **WSL - Ubuntu** já vem com o Git instalado, mas caso queira se certificar digite `git --version` no seu terminal). 

- Ter `curl` ou `wget` instalados (Neste guia iremos utilizar curl).


⚠️ ***Caso o Git não esteja instalado no seu WSL, utilize:***
```bash
sudo apt update && sudo apt upgrade
sudo apt install git
```
## CURL
Vamos utilizar o curl, uma ferramenta de linha de comando que permite realizar transferência de dados de e para servidores por meio de vários protocolos de rede, incluindo HTTP, HTTPS, FTP, SMTP, POP3 e muitos outros, para baixar e instalar o Oh My ZSH.
<br><br>
Para instalar o curl basta somente fazer os mesmos passos feitos utilizados para a instalação do zsh:
```bash
sudo apt install curl
```
Para checar se foi devidamente instalado execute o comando: `curl --version`

## Instalando OhMyZsh
Para instalar Oh My Zsh basta digitar este comando no terminal e reinciar a janela do WSL.
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## PowerLevel10k
Antes de prosseguir com a instalação é **ideal**:
- Instalar uma fonte adequada.
- Fazer todos os passos anteriores a este.

### O que o PowerLevel10k faz?
É um tema para o ZSH, que enfatiza velocidade, flexibilidade e uma experiência fora da caixa, voltada principalmente para a customização do seu terminal.

## Instalando o PowerLevel10k
A maneira mais simples de instalar é utilizando o git, desta forma bastar executar o código no terminal e reiniciar a janela para entrar no modo de configuração.
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```
## Wizard e Customização
Após reiniciar a janela um wizard deve aparecer no seu terminal para selecionar opções de customização estéticas, a partir daqui vai a seu bom gosto e customização, caso queira repetir o processo de setup utilize:
```bash
p10k configure
```

![terminal-show-config](/assets/terminal10k.gif)

## Plugins & Adicionais
Agora que seu combo setup está pronto, WSL2 + zsh + powerlevel10k, podemos colocar a valer as ferramentas a nossa disposição. Aqui vou somente mostrar comn instalar dois plugins que são em minha opnião indispensáveis, mas vale falar que as opções de customização são praticamente ilimitadas e que você pode adicionar quantos plugins desejar.
<br><br>
> ### zsh-syntax-highlighting & zsh-autosuggestions
<br>

Execute os dois comandos abaixo para instalar o zsh-autosuggestions e o zsh-syntax-highlighting, respectivamente.
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

Depois de instalados, vá para `nano ~/.zshrc` e ache `plugins=(git)` e adicione os plugins desta forma: 

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```
- Reabra o terminal e pronto. 🥳

## Visual Studio Code
## Referências

- [Guia rápido do WSL2 + Docker](https://github.com/codeedu/wsl2-docker-quickstart)
- [WSL - Wikipedia](https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux#:~:text=WSL%202%20requires%20Windows%2011,of%20native%20Ubuntu%2020.04%20LTS.)
- [Z shell](https://en.wikipedia.org/wiki/Z_shell)
- [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh)
- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
- [Gist - Plugins zsh](https://gist.github.com/dogrocker/1efb8fd9427779c827058f873b94df95)
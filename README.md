# NLW-06-React

## Preparando o ambiente

Sem mais delongas, vamos ao conteúdo principal desse guia: configuração do seu ambiente para o NLW. Teremos três etapas principais na seção "**Instalação"**:

> [!NOTE]
> - Node + NPM;
> - Yarn;
> - Visual Studio Code e configurações.

Se você já participou de alguma das nossas outras NLWs, já deve ter tudo isso instalado, mas talvez desatualizado. Por isso, preparamos uma seção "**Atualização"** para você atualizar suas dependências caso precise, mas sugerimos dar uma olhada pelo menos no guia Visual Studio Code na seção "**Instalação"** pois o Diego deixou algumas configs especialmente para você 💜

## Windows

Para o Windows utilizaremos o gerenciador de pacotes **[Chocolatey](https://chocolatey.org/)**, porém antes dos passos de instalação vamos falar brevemente sobre qual shell você deve usar.

- **CMD**: também conhecido como **Command Prompt**, ele é um dos shells mais antigos da atualidade (foi construído para ser compatível com o **MS-DOS**) e, apesar da sua fama, hoje em dia tem sido cada vez menos utilizado.
- **Powershell**: novo shell apresentado pela Microsoft por volta de 2005, ele apresenta diversas melhorias em relação ao **CMD**, tornando-o popular atualmente.

Escolhido o shell, vamos começar a instalação:

- Busque no campo de busca do Windows por **Windows Powershell**, clique com o botão direito em cima do programa e escolha a opção **Executar como administrador**.
- O Powershell trabalha com um esquema de autorizações (conhecido como `Execution Policy`) para execução de scripts e, por isso, precisamos verificar se o presente no sistema está compatível com o que o Chocolatey precisa. Execute o seguinte comando:

```bash
Get-ExecutionPolicy
```

Caso ele retorne Restricted, execute o comando:

```bash
Set-ExecutionPolicy RemoteSigned
```

E escolha a opção [A] Sim para Todos

> [!CAUTION]
>Caso o comando acima apresente erro, tente usar:

```bash
Set-ExecutionPolicy Bypass -Scope Process
```

Verifique se alteração de permissão ocorreu com sucesso executando novamente o comando:

```bash
Get-ExecutionPolicy
```

Alterada a permissão, basta instalar o Chocolatey com o comando:

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

> [!CAUTION]
> Caso o comando acima apresente um erro, verifique se a sua máquina atende às requisições mínimas
>   Windows 7+ / Windows Server 2003+ <br />
>   PowerShell v3+ <br />
>   .NET Framework 4.5+ <br />

Caso o erro apresentado seja Exceção ao definir "SecurityProtocol": "Não é possível converter o valor "3312", siga esse [guia](https://blog.chocolatey.org/2020/01/remove-support-for-old-tls-versions/)


Após o fim da instalação, feche e abra o powershell como administrador novamente e execute:

```bash
choco -v
```

Caso ele retorne a versão do Chocolatey, a instalação foi um sucesso. Para finalizar, basta instalar a versão LTS mais recente do Node com o seguinte comando:

```bash
cinst nodejs-lts
```

E escolha a opção `[A]ll - yes to all`

Após o fim da instalação, feche e abra o powershell como administrador novamente e execute:

```bash
node -v
npm -v
```

> [!NOTE]
>Caso retorne as versões do Node e Npm, sua instalação foi um sucesso.

# Yarn 1

## Windows, Linux e macOS

Para instalar o Yarn 1 siga os seguintes passos, execute o comando no terminal:

```bash
 npm install --global yarn
```

Após a instalação finalizar, feche e abra o terminal novamente, em seguida rode o comando:

```bash
 yarn --version
```

Caso retorne a versão do Yarn (acima de 1.0 e abaixo de 2.0), a instalação ocorreu com sucesso.

### Possíveis problemas

Ao usar o Yarn no Windows para instalar as dependências nos seus projetos, atente-se para que seu nome de usuário não possua espaços, pois nesse caso, alguns erros poderão ocorrer durante esse processo, como por exemplo: com o nome "Diego Fernandes", o caminho até a pasta do projeto (supondo que estivesse na pasta *Documents*) seria algo como `C:\Users\Diego Fernandes\Documents\NLW\Projeto` e nesse caso, uma solução seria criar o projeto já na raiz do **Disco C**. Dessa forma, o caminho até a pasta não passaria pelo nome do usuário, ficando `C:\NLW\Projeto`.
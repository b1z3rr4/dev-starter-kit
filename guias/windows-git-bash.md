# 🪟 Guia: Git Bash no Windows

> Este guia é **exclusivo para usuários de Windows**. Mac e Linux já têm terminal nativo e não precisam seguir estas etapas.

O Git Bash é um terminal que permite usar comandos do Git (e outros comandos de desenvolvimento) no Windows, da mesma forma que desenvolvedores usam no Mac e Linux. Sem ele, vários comandos simplesmente não vão funcionar.

---

## Por que preciso do Git Bash?

O terminal padrão do Windows (cmd e PowerShell) tem sintaxe diferente e não funciona bem com várias ferramentas de desenvolvimento. O Git Bash instala dois recursos de uma vez:

- **Git** — o sistema de controle de versão
- **Bash** — um terminal compatível com o padrão usado em servidores e pela maioria dos tutoriais da internet

---

## 1. Baixar o Git para Windows

1. Acesse: **[git-scm.com/download/win](https://git-scm.com/download/win)**
2. O download vai começar automaticamente
3. Baixe a versão **64-bit Git for Windows Setup**

---

## 2. Instalar — siga estas opções com atenção

O instalador tem várias telas. A maioria pode deixar no padrão, mas **preste atenção nas telas abaixo**:

### Tela: "Select Components"
Deixe tudo marcado. Certifique-se de que estas opções estão ativas:
- ✅ Git Bash Here
- ✅ Git GUI Here
- ✅ Associate .git* configuration files with the default text editor
- ✅ Associate .sh files to be run with Bash

### Tela: "Choosing the default editor used by Git"
Selecione **"Use Visual Studio Code as Git's default editor"**

> Isso faz o VS Code abrir automaticamente quando o Git precisar que você escreva uma mensagem de commit ou resolva um conflito.

### Tela: "Adjusting the name of the initial branch in new repositories"
Selecione **"Override the default branch name for new repositories"** e escreva: `main`

> O padrão antigo era `master`, mas a comunidade migrou para `main`. Já configure certo desde o início.

### Tela: "Adjusting your PATH environment"
Selecione: **"Git from the command line and also from 3rd-party software"**

> Isso permite usar o Git no terminal do VS Code também.

### Tela: "Choosing the SSH executable"
Deixe: **"Use bundled OpenSSH"**

### Tela: "Choosing HTTPS transport backend"
Deixe: **"Use the OpenSSL library"**

### Tela: "Configuring the line ending conversions"
Selecione: **"Checkout Windows-style, commit Unix-style line endings"**

> Isso evita problemas de compatibilidade quando pessoas de sistemas diferentes trabalham no mesmo projeto.

### Tela: "Configuring the terminal emulator to use with Git Bash"
Selecione: **"Use MinTTY (the default terminal of MSYS2)"**

### Tela: "Choose the default behavior of 'git pull'"
Selecione: **"Default (fast-forward or merge)"**

### Demais telas
Pode deixar no padrão e clicar em **Next** até o **Install**.

---

## 3. Verificar a instalação

Após instalar, abra o **Git Bash** (procure no menu Iniciar por "Git Bash"):

```bash
git --version
```

Deve aparecer algo como:
```
git version 2.44.0.windows.1
```

Se apareceu a versão, **funcionou!** ✅

---

## 4. Configurar o Git Bash como terminal padrão no VS Code

1. Abra o VS Code
2. Pressione `Ctrl + Shift + P` para abrir a paleta de comandos
3. Digite: `Terminal: Select Default Profile`
4. Selecione **Git Bash**

Agora sempre que você abrir o terminal no VS Code (`Ctrl + '`), ele vai usar o Git Bash.

---

## 5. Confirmar que está tudo certo

Abra o terminal no VS Code com `Ctrl + '` (ou pelo menu `Terminal > New Terminal`).

Você deve ver um prompt parecido com este:

```
nome@COMPUTADOR MINGW64 ~
$
```

Se aparecer esse `$` no final, o Git Bash está funcionando dentro do VS Code. 🎉

---

## Dúvidas comuns

**O terminal ainda mostra PowerShell ou cmd, o que faço?**
Feche o terminal, pressione `Ctrl + Shift + P`, digite `Terminal: Select Default Profile`, e selecione **Git Bash**. Abra um novo terminal.

**Apareceu um erro "git is not recognized as a command"**
Feche e abra o VS Code novamente após a instalação do Git. Se persistir, reinstale o Git marcando a opção "Git from the command line and also from 3rd-party software".

**Não achei o instalador para 64-bit**
Na página do git-scm.com, role para baixo e clique em "Click here to download" — o link direto pega a versão correta automaticamente.

---

Próximo passo: [`configurar-git.md`](configurar-git.md) — configurar seu nome, email e integrar o Git ao VS Code.

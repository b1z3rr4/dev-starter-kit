# 🔑 Guia: Configurar SSH no GitHub

> SSH é a forma mais prática de conectar sua máquina ao GitHub. Com ele configurado, você nunca mais precisa digitar usuário e senha pra fazer push — o computador se autentica automaticamente.

---

## O que é SSH?

SSH (Secure Shell) funciona com um par de chaves:

- **Chave privada** — fica no seu computador, nunca sai daqui
- **Chave pública** — você cadastra no GitHub

Quando você tenta se conectar, o GitHub e seu computador se reconhecem pelas chaves. Sem senha, sem complicação.

---

## 1. Verificar se já existe uma chave SSH

Abra o terminal (`Ctrl + '` no VS Code) e rode:

```bash
ls ~/.ssh
```

Se aparecer arquivos como `id_ed25519` e `id_ed25519.pub` (ou `id_rsa` e `id_rsa.pub`), você já tem um par de chaves. Pode pular para o **passo 3**.

Se não aparecer nada ou der erro de "No such file or directory", continue no passo 2.

---

## 2. Gerar uma nova chave SSH

Rode o comando abaixo, **substituindo pelo seu e-mail do GitHub**:

```bash
ssh-keygen -t ed25519 -C "seu@email.com"
```

O terminal vai fazer algumas perguntas:

**"Enter a file in which to save the key"**
→ Pressione `Enter` para aceitar o caminho padrão

**"Enter passphrase (empty for no passphrase)"**
→ Pode deixar em branco e pressionar `Enter` duas vezes

> Usar uma passphrase adiciona uma camada de segurança, mas vai pedir essa senha toda vez que você fizer push. Para uso pessoal e de estudo, deixar em branco é ok.

Ao terminar, o terminal vai exibir algo parecido com:

```
Your identification has been saved in /home/seu-usuario/.ssh/id_ed25519
Your public key has been saved in /home/seu-usuario/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx seu@email.com
```

---

## 3. Adicionar a chave ao ssh-agent

O ssh-agent é um programa que guarda sua chave em memória enquanto o computador está ligado.

**Iniciar o agente:**

```bash
eval "$(ssh-agent -s)"
```

Deve aparecer algo como `Agent pid 12345`.

**Adicionar sua chave:**

```bash
ssh-add ~/.ssh/id_ed25519
```

> Se o seu arquivo tiver nome diferente (ex: `id_rsa`), substitua no comando acima.

---

## 4. Copiar a chave pública

Rode o comando abaixo para exibir sua chave pública:

```bash
cat ~/.ssh/id_ed25519.pub
```

Vai aparecer uma linha longa começando com `ssh-ed25519` e terminando com seu e-mail. **Selecione e copie tudo** — do `ssh-ed25519` até o final.

Exemplo (a sua vai ser diferente):

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIAbCdEfGhIjKlMnOpQrStUvWxYz1234567890abcdef seu@email.com
```

---

## 5. Cadastrar a chave no GitHub

1. Acesse **[github.com/settings/keys](https://github.com/settings/keys)** (você precisa estar logado)
2. Clique em **"New SSH key"**
3. Preencha:
   - **Title:** Um nome pra identificar este computador (ex: `Notebook Casa`, `PC Trabalho`)
   - **Key type:** Authentication Key (padrão)
   - **Key:** Cole a chave pública que você copiou
4. Clique em **"Add SSH key"**
5. O GitHub pode pedir sua senha de conta para confirmar

---

## 6. Testar a conexão

```bash
ssh -T git@github.com
```

Na primeira vez, vai aparecer uma mensagem pedindo confirmação:

```
The authenticity of host 'github.com (...)' can't be established.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Digite `yes` e pressione `Enter`.

Se tudo funcionou, a resposta será:

```
Hi seu-usuario! You've successfully authenticated, but GitHub does not provide shell access.
```

**Conectado!** ✅

---

## 7. Usar SSH ao clonar e conectar repositórios

Agora que o SSH está configurado, sempre use a **URL SSH** dos repositórios (não a HTTPS).

### Clonar um repositório

No GitHub, ao clicar em **Code**, selecione a aba **SSH** e copie a URL:

```bash
git clone git@github.com:seu-usuario/nome-do-repo.git
```

### Conectar um repositório local ao GitHub

Se você já tem uma pasta com Git iniciado e criou um repositório vazio no GitHub:

```bash
git remote add origin git@github.com:seu-usuario/nome-do-repo.git
git branch -M main
git push -u origin main
```

Após este primeiro push com `-u`, nas próximas vezes é só:

```bash
git push
```

---

## 8. Verificar se o remote está usando SSH

Para checar se um repositório já existente está usando SSH ou HTTPS:

```bash
git remote -v
```

**SSH** (correto):

```
origin  git@github.com:seu-usuario/repo.git (fetch)
origin  git@github.com:seu-usuario/repo.git (push)
```

**HTTPS** (vai pedir senha):

```
origin  https://github.com/seu-usuario/repo.git (fetch)
origin  https://github.com/seu-usuario/repo.git (push)
```

Para trocar de HTTPS para SSH num repositório existente:

```bash
git remote set-url origin git@github.com:seu-usuario/nome-do-repo.git
```

---

## Dúvidas comuns

**"Permission denied (publickey)" ao tentar fazer push**
→ A chave não foi adicionada ao ssh-agent. Rode `ssh-add ~/.ssh/id_ed25519` e tente de novo.

**Tenho mais de um computador, preciso repetir tudo?**
→ Sim. Cada máquina tem seu próprio par de chaves. Repita este processo em cada computador e cadastre cada chave pública no GitHub com um título diferente.

**Posso deletar uma chave do GitHub?**
→ Sim, a qualquer momento em [github.com/settings/keys](https://github.com/settings/keys). Útil se você trocar de computador ou perder um dispositivo.

**Estou no Windows e o `ssh-keygen` não funciona**
→ Certifique-se de estar usando o **Git Bash** (não o PowerShell ou cmd). Veja o guia [`windows-git-bash.md`](windows-git-bash.md).

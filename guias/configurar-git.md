# 🔧 Guia: Configurar Git + VS Code

> Antes de continuar, certifique-se de que o Git está instalado:
> - **Windows:** siga o guia [`windows-git-bash.md`](windows-git-bash.md) primeiro
> - **Mac/Linux:** abra o terminal e rode `git --version`. Se não retornar uma versão, instale pelo site [git-scm.com](https://git-scm.com)

---

## O que é o Git e por que usar?

Git é um sistema de controle de versão. Na prática, ele:

- Salva o histórico de tudo que você mudou no código
- Permite voltar pra uma versão anterior se algo quebrar
- Possibilita trabalhar em equipe sem sobrescrever o trabalho de ninguém
- É o padrão da indústria — toda empresa usa

Pense no Git como um "Ctrl+Z infinito e inteligente" para o seu projeto.

---

## 1. Configurar seu nome e e-mail

Abra o terminal no VS Code com `Ctrl + '` (Windows/Linux) ou `Cmd + '` (Mac).

Rode os dois comandos abaixo, **substituindo pelos seus dados**:

```bash
git config --global user.name "Seu Nome Aqui"
```

```bash
git config --global user.email "seu@email.com"
```

> **Por que isso importa?** Cada commit (salvamento) que você fizer vai ter seu nome e e-mail registrados. É como assinar seu trabalho.

### Verificar se funcionou

```bash
git config --list
```

Você deve ver suas informações na lista:
```
user.name=Seu Nome Aqui
user.email=seu@email.com
```

---

## 2. Configurar o VS Code como editor padrão do Git

Quando o Git precisar que você escreva uma mensagem (como em merges ou conflitos), ele abre um editor. Configure para abrir o VS Code:

```bash
git config --global core.editor "code --wait"
```

---

## 3. Configurar o nome padrão da branch principal

Por padrão mais antigo, o Git criava uma branch chamada `master`. A comunidade migrou para `main`. Configure isso agora para não ter surpresas:

```bash
git config --global init.defaultBranch main
```

---

## 4. Seu primeiro repositório

Um repositório (ou "repo") é uma pasta que o Git está monitorando.

### Criar e inicializar

```bash
# Crie e entre numa pasta de teste
mkdir meu-projeto
cd meu-projeto

# Inicializa o Git nessa pasta
git init
```

Você vai ver: `Initialized empty Git repository in .../meu-projeto/.git/`

Isso significa que o Git está de olho em tudo dentro dessa pasta.

### Ver o status do repositório

```bash
git status
```

No início, vai aparecer:
```
On branch main
No commits yet
nothing to commit
```

---

## 5. O ciclo básico do Git

O Git tem três etapas para salvar uma mudança:

```
Você edita → git add → git commit
```

| Etapa | O que faz |
|---|---|
| Editar o arquivo | Você faz as mudanças normalmente no VS Code |
| `git add` | Diz ao Git "quero incluir esse arquivo no próximo salvamento" |
| `git commit` | Salva de vez, com uma mensagem descrevendo o que mudou |

### Exemplo prático

Crie um arquivo dentro da pasta:

```bash
# Cria o arquivo (ou crie pelo VS Code mesmo)
echo "Olá mundo" > index.html
```

Veja o que o Git detectou:

```bash
git status
```

Vai aparecer que o arquivo está "untracked" (não rastreado ainda).

Adicione ao stage (preparar pra salvar):

```bash
git add index.html
```

Ou para adicionar todos os arquivos de uma vez:

```bash
git add .
```

Salve com uma mensagem:

```bash
git commit -m "Adiciona página inicial"
```

Veja o histórico:

```bash
git log --oneline
```

Vai aparecer algo como:
```
a3f8c21 Adiciona página inicial
```

**Parabéns — você fez seu primeiro commit!** 🎉

---

## 6. Usar o Git pela interface do VS Code

Você não precisa usar o terminal o tempo todo. O VS Code tem uma aba de controle de versão embutida.

### Acessar

Clique no **ícone de ramificação** na barra lateral esquerda (parece um grafo/Y) ou pressione `Ctrl + Shift + G`.

### O que você consegue fazer por lá

- Ver todos os arquivos modificados
- Adicionar arquivos ao stage (clicando no `+` ao lado do arquivo)
- Escrever a mensagem do commit no campo de texto
- Commitar clicando em **"Commit"** (ou `Ctrl + Enter`)
- Ver o histórico de commits com a extensão **GitLens** (fica na barra lateral também)

---

## 7. Comandos mais usados no dia a dia

```bash
# Ver o que mudou
git status

# Adicionar tudo ao stage
git add .

# Salvar com mensagem
git commit -m "Sua mensagem aqui"

# Ver histórico de commits
git log --oneline

# Ver as diferenças antes de commitar
git diff

# Desfazer mudanças num arquivo (cuidado: irreversível)
git checkout -- nome-do-arquivo.html

# Voltar para um commit anterior (modo seguro, só visualização)
git checkout abc1234
```

---

## 8. Boas práticas de commit

Mensagens de commit boas fazem diferença quando você (ou outra pessoa) precisar entender o histórico depois.

**Use verbos no imperativo, em português ou inglês:**

✅ Bom:
```
git commit -m "Adiciona formulário de contato"
git commit -m "Corrige bug no menu mobile"
git commit -m "Atualiza cores do botão principal"
```

❌ Evite:
```
git commit -m "update"
git commit -m "arrumei umas coisas"
git commit -m "asdfjkl"
```

**Commite com frequência.** Não espere terminar o projeto todo. Commit após cada funcionalidade ou correção que funcionar.

---

## Próximos passos

Quando quiser hospedar seu código online e colaborar com outras pessoas, você vai usar o **GitHub**. O fluxo é:

1. Criar uma conta em [github.com](https://github.com)
2. Criar um repositório lá
3. Conectar sua pasta local com o repositório remoto (`git remote add origin ...`)
4. Enviar seus commits com `git push`

Mas isso é assunto pra um próximo guia. Por enquanto, o mais importante é praticar o ciclo: **editar → add → commit**.

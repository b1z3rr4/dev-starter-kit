# 🚀 Dev Starter Kit — HTML, CSS & JavaScript

> Setup completo pra quem tá começando do zero. Siga essa ordem e você vai ter um ambiente profissional funcionando em menos de 1 hora.

---

## 📋 O que você vai configurar

- [x] VS Code (editor de código)
- [x] Extensões recomendadas
- [x] Configurações otimizadas pra HTML, CSS e JS
- [x] Git (controle de versão)
- [x] Git integrado ao VS Code

> **Windows?** Antes de qualquer coisa, leia o guia [`guias/windows-git-bash.md`](guias/windows-git-bash.md) para instalar o Git Bash — você vai precisar dele.

---

## 1. Instalar o VS Code

### Download

Acesse **[code.visualstudio.com](https://code.visualstudio.com)** e baixe a versão para o seu sistema:

| Sistema | Botão no site |
|---|---|
| Windows | `Download for Windows` |
| macOS | `Download for Mac` |
| Linux | Escolha `.deb` (Ubuntu/Debian) ou `.rpm` (Fedora) |

### Instalação no Windows

1. Abra o instalador `.exe` que você baixou
2. Aceite os termos de uso
3. Na tela **"Selecionar Tarefas Adicionais"**, marque **todas** as opções:
   - ✅ Adicionar ao PATH
   - ✅ Registrar código como editor para tipos de arquivo suportados
   - ✅ Adicionar a ação "Abrir com Code" no menu de contexto de arquivos
   - ✅ Adicionar a ação "Abrir com Code" no menu de contexto de diretórios
4. Clique em **Instalar** e depois em **Concluir**

### Instalação no macOS

1. Abra o `.zip` baixado — vai extrair o app `Visual Studio Code`
2. Arraste o app pra pasta **Aplicativos**
3. Abra o VS Code, pressione `Cmd + Shift + P`, digite `shell command` e clique em **"Shell Command: Install 'code' command in PATH"**
   - Isso permite abrir o VS Code pelo terminal digitando `code .`

---

## 2. Colocar o VS Code no seu idioma

O VS Code vem em inglês por padrão. Você pode usar em **português** ou manter em **inglês** — ambos funcionam bem.

### 👉 Opção A — Português (BR)

1. Pressione `Ctrl + Shift + X` (ou `Cmd + Shift + X` no Mac) para abrir as extensões
2. Pesquise: `Portuguese Brazil`
3. Instale a extensão **"Portuguese (Brazil) Language Pack for Visual Studio Code"** da Microsoft
4. Reinicie o VS Code quando solicitado

### 👉 Opção B — Inglês (padrão)

Não precisa fazer nada! O VS Code já vem em inglês.

> 💡 **Dica:** Se você pretende trabalhar com documentação técnica, tutoriais internacionais ou procurar ajuda no Stack Overflow, o inglês pode ser mais prático. Mas o português deixa tudo mais acessível pra quem tá começando. Escolha o que fizer mais sentido pra você.

---

## 3. Instalar as extensões recomendadas

Este repositório já tem uma lista de extensões configurada. Para instalar todas de uma vez:

1. Abra esta pasta no VS Code (`Arquivo > Abrir Pasta` ou `File > Open Folder`)
2. Uma notificação vai aparecer no canto inferior direito:
   > *"This workspace has extension recommendations. Do you want to install them?"*
3. Clique em **Install All** (ou **Instalar Tudo**)

### O que cada extensão faz

| Extensão | Para que serve |
|---|---|
| **Prettier** | Formata o código automaticamente ao salvar |
| **Live Server** | Abre seu HTML no navegador e atualiza em tempo real |
| **Auto Rename Tag** | Renomeia a tag de fechamento automaticamente quando você edita a de abertura |
| **CSS Peek** | Permite ir direto para a definição do CSS clicando no nome da classe |
| **Error Lens** | Mostra erros e avisos diretamente na linha do código |
| **Path Intellisense** | Autocompleta caminhos de arquivos (`src/`, `./`, etc.) |
| **Indent Rainbow** | Colore os níveis de indentação pra facilitar a leitura |
| **GitLens** | Mostra quem editou cada linha de código e quando (integração com Git) |
| **Material Icon Theme** | Ícones bonitos pra identificar tipos de arquivo na barra lateral |

---

## 4. Aplicar as configurações do VS Code

As configurações já estão prontas no arquivo `.vscode/settings.json` deste repositório. Elas serão aplicadas automaticamente quando você abrir a pasta no VS Code.

### O que está configurado

- **Formatação automática ao salvar** — o Prettier arruma o código pra você
- **Tamanho de fonte e espaçamento confortáveis** para leitura
- **Tamanho de tab = 2 espaços** (padrão do front-end)
- **Quebra de linha automática** — nada vai sumir pra fora da tela
- **Emmet ativado** — escreva `!` e pressione `Tab` num arquivo HTML para gerar o esqueleto completo
- **Auto save** — salva automaticamente quando você muda de janela

> Se quiser personalizar mais, edite o arquivo `.vscode/settings.json` diretamente.

---

## 5. Configurar o Git

O Git é o sistema que salva o histórico de tudo que você muda no seu projeto. Pense nele como um "checkpoint" do seu código.

> **Windows:** Certifique-se de ter seguido o guia [`guias/windows-git-bash.md`](guias/windows-git-bash.md) antes de continuar.

Para o guia completo de configuração do Git no VS Code, acesse: [`guias/configurar-git.md`](guias/configurar-git.md)

---

## 6. Testar se tudo funcionou

1. Crie um arquivo chamado `index.html` dentro desta pasta
2. Digite `!` e pressione `Tab` — o esqueleto HTML deve aparecer automaticamente
3. Escreva qualquer coisa dentro do `<body>`
4. Clique com o botão direito no arquivo e escolha **"Open with Live Server"**
5. O navegador deve abrir com sua página

Se abriu — **tá tudo funcionando!** 🎉

---

## Estrutura deste repositório

```
dev-starter-kit/
├── .vscode/
│   ├── extensions.json   → lista de extensões recomendadas
│   └── settings.json     → configurações do editor
├── guias/
│   ├── windows-git-bash.md  → instalar Git Bash no Windows
│   └── configurar-git.md    → configurar Git + VS Code
└── README.md             → você está aqui
```

---

## Dúvidas?

- Documentação oficial do VS Code: [code.visualstudio.com/docs](https://code.visualstudio.com/docs)
- Documentação do Git: [git-scm.com/doc](https://git-scm.com/doc)
- Busque no Google sempre em inglês pra achar mais resultados: ex. `how to center a div css`

<h1 align="center">📘 Guia Git & GitHub</h1>

### 📌 O que é Controle de Versão?

- Uma técnica que ajuda a gerenciar o código-fonte de uma aplicação;
- Registra todas as modificações do código, permitindo reverter se necessário;
- Permite criar versões diferentes de um software e alternar entre elas;
- Cada membro da equipe pode trabalhar em uma versão distinta;
- Ferramentas populares: `Git`, `SVN`.
- Controlar versões evita conflitos e facilita colaboração simultânea;
- Mantém um histórico claro do progresso e das decisões de desenvolvimento.

---

### 🔧 O que é Git?

- O sistema de controle de versão mais usado do mundo;
- Baseado em repositórios com todas as versões e cópias de desenvolvedores;
- Focado em alto desempenho;
- Utiliza criptografia para segurança;
- Projeto de código aberto.
- Git é distribuído: cada desenvolvedor possui uma cópia completa do histórico do projeto;
- Permite trabalho offline com sincronização posterior ao repositório remoto.

---

### 📂 O que é um Repositório?

- Onde o código é armazenado;
- Cada projeto normalmente tem um repositório;
- É possível criar repositórios locais e remotos (ex: GitHub);
- Todos do time podem clonar e criar versões locais do repositório.
- Pode conter diretórios, arquivos, documentação e histórico de commits;
- Um repositório remoto é geralmente compartilhado via HTTP ou SSH.

---

### 👤 Configurar nome e email do Git

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

- Essa configuração é usada para identificar o autor dos commits;
- A flag --global define os dados para todos os projetos no computador;
- Para configuração local (por projeto), remova --global e execute dentro do repositório desejado.

---

### 📦 Criando Repositórios

```bash
git init
```

- Cria os arquivos necessários e inicia o Git no projeto;
- O diretório passa a ser monitorado pelo Git;
- Os arquivos de controle ficam na pasta oculta `.git`.
- Esse comando deve ser executado uma vez ao iniciar o projeto.

---

### 🐙 O que é o GitHub?

- Plataforma para hospedagem e gerenciamento de repositórios Git;
- Muito utilizado para colaboração entre devs;
- Gratuito para projetos públicos e privados.
- Integrações com CI/CD, wikis, issues e pull requests;
- Facilita o trabalho em equipe e a revisão de código.

---

### 🚀 Enviando Repositórios para o GitHub

- Criar projeto no GitHub;
- Inicializar o Git local;
- Conectar ao repositório remoto;

```bach
git remote add origin https://github.com/usuario/repositorio.git
```

- Enviar com `git push -u origin main` (ou master, dependendo do nome do branch).
- O `-u` define `origin main` como padrão para os próximos `git push`.

---

### 🔍 Verificando mudanças no projeto

```bash
git status
```

- Mostra arquivos modificados, adicionados ou removidos;
- Usado com frequência para monitorar o estado atual do projeto.
- Indica se arquivos estão no `staging` ou aguardando `commit`.

---

### ➕ Adicionando arquivos ao projeto

```bash
git add index.js          # Um arquivo
git add .                 # Todos os arquivos modificados
git add pasta/            # Todos os arquivos da pasta
```

- Move os arquivos para o "staging area";
- Só arquivos adicionados serão salvos no commit.
- A ordem correta: `git add` → `git commit`.

---

### 💾 Salvando alterações do projeto (commit)

```bash
git commit -m "mensagem"              # Commit com mensagem
git commit -a -m "mensagem"           # Adiciona + commita arquivos modificados
```

- Registra alterações no repositório;
- Boa prática: usar mensagens claras e objetivas.
- A flag `-a` adiciona apenas arquivos modificados (não novos).

---

### ☁️ Enviando código ao repositório remoto

```bash
git push
```

- Envia os commits locais para o repositório remoto.
- Normalmente usado após commit para sincronizar com o GitHub.

---

### ⬇️ Recebendo mudanças do repositório remoto

```bash
git pull
```

- Atualiza o projeto local com alterações feitas remotamente.

---

### 📥 Clonando repositórios

```bash
git clone https://github.com/usuario/repositorio.git
```

- Cria uma cópia local do repositório remoto.

```bash
git clone https://github.com/usuario/repositorio.git .
```

- Clona o repositório remoto diretamente na pasta atual, sem criar uma subpasta com o nome do repositório. Ideal para quando você já está em uma pasta vazia preparada para receber o projeto.

```bash
git clone https://github.com/usuario/repositorio.git nome_pasta
```

- Clona o repositório remoto e define um nome personalizado para a pasta onde o projeto será armazenado localmente.

---

### ❌ Removendo arquivos do repositório

```bash
git rm arquivo.txt
```

- Remove arquivo do projeto e do controle de versão.
- Necessário fazer commit para finalizar a remoção.

---

### 🕓 Histórico de alterações

```bash
git log
```

- Lista todos os commits feitos no projeto.
- Usa `q` para sair da visualização;
- Pode ser personalizado com `git log --oneline` ou `--graph`.

---

### ✏️ Renomeando arquivos

```bash
git mv antigo.txt novo.txt
```

- Renomeia e mantém o controle de versão do arquivo.
- Equivalente a mv seguido de `git add` e `git rm`.

---

### ↩️ Desfazendo alterações

```bash
git checkout nome-do-arquivo
```

- Volta o arquivo para o estado do último commit.
- Para desfazer commits inteiros: `git reset`

---

### 🙈 Ignorando arquivos no projeto

**Criar arquivo:** `.gitignore`

```bash
# Exemplo de conteúdo:
node_modules/
dist/
.env
```

- Arquivos listados não serão versionados.
- Importante manter esse arquivo versionado no projeto.

---

### 🧹 Desfazendo todas as alterações

```bash
git reset --hard
```

- Remove todas as alterações e commits locais;
- **Cuidado:** essa ação é irreversível!

---

### 📎 Comandos rápidos

| Ação                       | Comando                       |
| -------------------------- | ----------------------------- |
| Iniciar repositório        | `git init`                    |
| Adicionar arquivo          | `git add nome-do-arquivo`     |
| Verificar alterações       | `git status`                  |
| Criar commit               | `git commit -m "mensagem"`    |
| Adicionar + commitar       | `git commit -a -m "mensagem"` |
| Enviar para repositório    | `git push`                    |
| Receber alterações remotas | `git pull`                    |
| Clonar projeto             | `git clone url`               |
| Ver histórico              | `git log`                     |
| Remover arquivo            | `git rm nome-do-arquivo`      |
| Renomear arquivo           | `git mv antigo novo`          |
| Resetar alterações         | `git reset --hard`            |

---

### 📦 Branches

### 🌿 O que é um branch?

- São ramificações do projeto;
- Permite trabalhar com versões paralelas;
- Geralmente usados para features, hotfixes, etc.

### 👀 Visualizando branches

```bash
git branch
```

### ✨ Criando branches

```bash
git branch nome-da-branch
```

### 🔁 Mudando de branch

```bash
git checkout nome-da-branch
git checkout -b nova-branch   # cria e já muda para ela
```

### 🗑️ Deletando branch

```bash
git branch -d nome-da-branch
```

### 🔀 Unindo branches

```bash
git merge nome-da-branch
```

---

### 💾 Stash

### 📥 Guardando alterações

```bash
git stash
```

### 📥 Recuperando alterações

```bash
git stash list
git stash apply stash@{0}
```

### 🧹 Limpando o stash

```bash
git stash clear
git stash drop stash@{0}
```

---

### 🏷️ Tags

### 🏷️ Criando tags

```bash
git tag -a v1.0 -m "Versão 1.0"
```

### 🔍 Verificando e alternando tags

```bash
git show v1.0
git checkout v1.0
```

### 📤 Enviando tags

```bash
git push origin v1.0
git push origin --tags
```

---

### 🔍 Encontrando novos branches remotos

```bash
git fetch
```

---

### 💡Comandos adicionais úteis

### 🌐 Ver o repositório remoto

```bash
git remote -v
```

---

### 🔄 Recebendo alterações

### 📥 `git pull`

- Recebe atualizações do repositório remoto.
- Cada branch pode ser atualizado com `git pull`.
- Usado para atualizar a branch principal (ex: `master`) ou sincronizar mudanças feitas por outros desenvolvedores.

```bash
git pull
```

---

### 📤 Enviando alterações

### 🚀 `git push`

- Envia alterações locais para o repositório remoto.
- Pode ser usado para compartilhar mudanças de um branch com outros devs.
- Utilizado ao finalizar uma tarefa para enviá-la ao repositório.

```bash
git push
```

---

### 🌐 Utilizando o remote

### 🔗 `git remote`

- Permite adicionar, visualizar ou remover repositórios remotos.
- Exemplo de adicionar um repositório remoto:

```bash
git remote add origin <link-do-repo>
```

---

### 📦 Trabalhando com submódulos

### 🧩 `git submodule`

- Submódulos permitem manter múltiplos projetos dentro de um só repositório.
- Permite adicionar uma dependência sem misturar estruturas de projeto.
- Adicionando um submódulo:

```bash
git submodule add <url-do-repo>
```

- Verificando submódulos:

```bash
git submodule
```

---

### 🔄 Atualizando submódulos

### 🔃 `git push --recurse-submodules=on-demand`

- Commit as mudanças normalmente.
- Para atualizar o repositório do submódulo:

```bash
git push --recurse-submodules=on-demand
```

---

<h1 align="center">📘 Git - Inspeções e Logs</h1>

### 📄 Exibindo informações

● O comando `git show` nos dá diversas informações úteis;

```bach
git show
```

● Ele nos dá as informações do branch atual e também seus commits;  
 ● As modificações de arquivos entre cada commit também são exibidas;  
 ● Podemos exibir as informações de tags também com: `git show <tag>`

```bach
git show <tag>
```

---

### 🧮 Exibindo diferenças

● O comando `git diff` serve para exibir as diferenças de um branch;

```bach
git diff
```

● Quando utilizado as diferenças do branch atual com o remoto serão exibidas no terminal;  
 ● Podemos também verificar a diferença entre arquivos: `git diff <arquivo> <arquivo_b>`

```bach
git diff <arquivo> <arquivo_b>
```

---

### 📊 Log resumido

● O comando `git shortlog` nos dá um log resumido do projeto;  
 ● Cada commit será unido por nome do autor;  
 ● Podemos então saber quais commits foram enviados ao projeto e por quem.

```bach
git shortlog
```

---

### 🏷️ Utilizando o describe

● Com o comando `git describe --tags` podemos verificar todas as tags do nosso projeto;

```bach
git describe --tags
```

● Com a opção `--all` recebemos também a referência das tags;

```bach
git describe --all
```

---

### 🧹 Limpando arquivos untracked

- O comando `git clean` vai verificar e limpar arquivos que não estão sendo _trackeados_;
- Ou seja, todos que você não utilizou `git add`;
- Utilizado para arquivos que são gerados automaticamente, por exemplo, e atrapalham a visualização do que é realmente importante.

```bash
git clean -n    # Mostra os arquivos que seriam removidos
git clean -f    # Remove os arquivos não trackeados
```

---

### ⚙️ Otimizando o repositório

- O comando `git gc` é uma abreviação para _garbage collector_;
- Ele identifica arquivos que não são mais necessários e os exclui;
- Isso fará com que o repositório seja otimizado em questões de performance.

```bach
git gc
```

---

### 🧪 Checando integridade de arquivos

- O comando `git fsck` é uma abreviação de _File System ChecK_;
- Esta instrução verifica a integridade de arquivos e sua conectividade;
- Verificando assim possíveis corrupções em arquivos;
- Comando de rotina, utilizado para ver se está tudo certo com nossos arquivos.

```bach
git fsck
```

---

### 📜 Reflog

- O `git reflog` vai mapear todos os seus passos no repositório, até uma mudança de branch é inserida neste log;
- Já o `git log`, que vimos anteriormente, apenas armazena os commits de um branch;
- Os _reflogs_ ficam salvos até expirar, o tempo de expiração padrão é de 30 dias.

```bach
git reflog
```

---

### ♻️ Recuperando arquivos com reflog

- Podemos avançar e também retroceder nas _hashs_ do reflog;
- Para isso utilizamos o comando `git reset --hard <hash>`;
- Caso você tenha algo que queira salvar, pode utilizar o `git stash` antes;
- Lembrando: o reflog expira com o tempo!

```bach
git stash                    # Salva alterações atuais antes de resetar
git reflog                   # Lista todas as referências do reflog
git reset --hard <hash>      # Retorna para um ponto específico
```

---

### 📦 Transformando o repo para arquivo

- Com o comando `git archive` podemos transformar o repositório em um arquivo compactado, por exemplo;
- O comando é:

```bash
git archive --format zip --output master_files.zip master
```

---

| 🌎 LinkedIn                                                              | 👨‍💻 **Autor**                                                                 |
| ------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| [LinkedIn](https://www.linkedin.com/in/albert-backend-java-spring-boot/) | [Albert Silva](https://www.linkedin.com/in/albert-backend-java-spring-boot/) |

<h1 align="center">📘 Guia Git & GitHub</h1>

### 📌 O que é Controle de Versão?
- Uma técnica que ajuda a gerenciar o código-fonte de uma aplicação;
- Registra todas as modificações do código, permitindo reverter se necessário;
- Permite criar versões diferentes de um software e alternar entre elas;
- Cada membro da equipe pode trabalhar em uma versão distinta;
- Ferramentas populares: `Git`, `SVN`.

---

### 🔧 O que é Git?
- O sistema de controle de versão mais usado do mundo;
- Baseado em repositórios com todas as versões e cópias de desenvolvedores;
- Focado em alto desempenho;
- Utiliza criptografia para segurança;
- Projeto de código aberto.

---

### 📂 O que é um Repositório?
- Onde o código é armazenado;
- Cada projeto normalmente tem um repositório;
- É possível criar repositórios locais e remotos (ex: GitHub);
- Todos do time podem clonar e criar versões locais do repositório.

---

### 👤 Configurar nome e email do Git
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

---

### 📦 Criando Repositórios
```bash
git init
```
- Cria os arquivos necessários e inicia o Git no projeto;
- O diretório passa a ser monitorado pelo Git;
- Os arquivos de controle ficam na pasta oculta `.git`.

---

### 🐙 O que é o GitHub?
- Plataforma para hospedagem e gerenciamento de repositórios Git;
- Muito utilizado para colaboração entre devs;
- Gratuito para projetos públicos e privados.

---

### 🚀 Enviando Repositórios para o GitHub
- Criar projeto no GitHub;
- Inicializar o Git local;
- Conectar ao repositório remoto;
- Enviar com `git push`.

---

### 🔍 Verificando mudanças no projeto
```bash
git status
```
- Mostra arquivos modificados, adicionados ou removidos;
- Usado com frequência para monitorar o estado atual do projeto.

---

### ➕ Adicionando arquivos ao projeto
```bash
git add index.js          # Um arquivo
git add .                 # Todos os arquivos modificados
git add pasta/            # Todos os arquivos da pasta
```
- Move os arquivos para o "staging area";
- Só arquivos adicionados serão salvos no commit.

---

### 💾 Salvando alterações do projeto (commit)
```bash
git commit -m "mensagem"              # Commit com mensagem
git commit -a -m "mensagem"           # Adiciona + commita arquivos modificados
```
- Registra alterações no repositório;
- Boa prática: usar mensagens claras e objetivas.

---

### ☁️ Enviando código ao repositório remoto
```bash
git push
```
- Envia os commits locais para o repositório remoto.

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

---

### ❌ Removendo arquivos do repositório
```bash
git rm arquivo.txt
```
- Remove arquivo do projeto e do controle de versão.

---

### 🕓 Histórico de alterações
```bash
git log
```
- Lista todos os commits feitos no projeto.

---

### ✏️ Renomeando arquivos
```bash
git mv antigo.txt novo.txt
```
- Renomeia e mantém o controle de versão do arquivo.

---

### ↩️ Desfazendo alterações
```bash
git checkout nome-do-arquivo
```
- Volta o arquivo para o estado do último commit.

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

---

### 🧹 Desfazendo todas as alterações
```bash
git reset --hard
```
- Remove todas as alterações e commits locais;
- **Cuidado:** essa ação é irreversível!

---

### 📎 Comandos rápidos
| Ação                          | Comando                              |
|------------------------------|--------------------------------------|
| Iniciar repositório          | `git init`                           |
| Adicionar arquivo            | `git add nome-do-arquivo`           |
| Verificar alterações         | `git status`                         |
| Criar commit                 | `git commit -m "mensagem"`          |
| Adicionar + commitar         | `git commit -a -m "mensagem"`       |
| Enviar para repositório      | `git push`                           |
| Receber alterações remotas   | `git pull`                           |
| Clonar projeto               | `git clone url`                      |
| Ver histórico                | `git log`                            |
| Remover arquivo              | `git rm nome-do-arquivo`            |
| Renomear arquivo             | `git mv antigo novo`                |
| Resetar alterações           | `git reset --hard`                   |

---

## 📦 Branches

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

## 💾 Stash

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

## 🏷️ Tags

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

## 🔍 Encontrando novos branches remotos
```bash
git fetch
```

---

## Comandos adicionais úteis

### 🌐 Ver o repositório remoto
```bash
git remote -v
```
---


## 🔄 Recebendo alterações

### 📥 `git pull`
- Recebe atualizações do repositório remoto.
- Cada branch pode ser atualizado com `git pull`.
- Usado para atualizar a branch principal (ex: `master`) ou sincronizar mudanças feitas por outros desenvolvedores.

```bash
git pull
```

---

## 📤 Enviando alterações

### 🚀 `git push`
- Envia alterações locais para o repositório remoto.
- Pode ser usado para compartilhar mudanças de um branch com outros devs.
- Utilizado ao finalizar uma tarefa para enviá-la ao repositório.

```bash
git push
```

---

## 🌐 Utilizando o remote

### 🔗 `git remote`
- Permite adicionar, visualizar ou remover repositórios remotos.
- Exemplo de adicionar um repositório remoto:

```bash
git remote add origin <link-do-repo>
```

---

## 📦 Trabalhando com submódulos

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

## 🔄 Atualizando submódulos

### 🔃 `git push --recurse-submodules=on-demand`
- Commit as mudanças normalmente.
- Para atualizar o repositório do submódulo:

```bash
git push --recurse-submodules=on-demand
```

---

| 🌎 LinkedIn | 👨‍💻 **Autor** |
|------------|---------------|
| [LinkedIn](https://www.linkedin.com/in/albert-backend-java-spring-boot/) | [Albert Silva](https://www.linkedin.com/in/albert-backend-java-spring-boot/) |

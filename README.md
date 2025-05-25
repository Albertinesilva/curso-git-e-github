<h1 align="center">📘 Guia Git & GitHub</h1>

🚀 **Instalação e Configuração Inicial**

💻 **Instalação Git no Windows**
- Instalar git no Windows é muito fácil!
- Acessar o site: [https://git-scm.com/downloads](https://git-scm.com/downloads)
- Fazer o download do executável;
- E seguir as instruções.

🐧 **Instalação Git no Linux**
- Instalar git no Linux também é muito fácil!
- Acessar o site: [https://git-scm.com/download/linux](https://git-scm.com/download/linux)
- Teremos que seguir as instruções dependendo da nossa distro;
- E iniciar a instalação com nosso gerenciador de pacotes.

🧰 **Instalação do VS Code**
- O VS Code é o editor que vamos utilizar no curso;
- Porém não é uma obrigatoriedade, use o de sua preferência;
- A grande jogada é que ele possui um terminal integrado, facilitando as nossas ações com o git;
- Além de ser um editor super atualizado e que aceita diversas linguagens e ferramentas de programação.
---

📌 **O que é Controle de Versão?**

- Uma técnica que ajuda a gerenciar o código-fonte de uma aplicação;
- Registra todas as modificações do código, permitindo reverter se necessário;
- Permite criar versões diferentes de um software e alternar entre elas;
- Cada membro da equipe pode trabalhar em uma versão distinta;
- Ferramentas populares: `Git`, `SVN`.
- Controlar versões evita conflitos e facilita colaboração simultânea;
- Mantém um histórico claro do progresso e das decisões de desenvolvimento.

---

🔧 **O que é Git?**

- O sistema de controle de versão mais usado do mundo;
- Baseado em repositórios com todas as versões e cópias de desenvolvedores;
- Focado em alto desempenho;
- Utiliza criptografia para segurança;
- Projeto de código aberto.
- Git é distribuído: cada desenvolvedor possui uma cópia completa do histórico do projeto;
- Permite trabalho offline com sincronização posterior ao repositório remoto.

---

📂 **O que é um Repositório?**

- Onde o código é armazenado;
- Cada projeto normalmente tem um repositório;
- É possível criar repositórios locais e remotos (ex: GitHub);
- Todos do time podem clonar e criar versões locais do repositório.
- Pode conter diretórios, arquivos, documentação e histórico de commits;
- Um repositório remoto é geralmente compartilhado via HTTP ou SSH.

---

👤 **Configurar nome e email do Git**

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

- Essa configuração é usada para identificar o autor dos commits;
- A flag --global define os dados para todos os projetos no computador;
- Para configuração local (por projeto), remova --global e execute dentro do repositório desejado.

---

📦 **Criando Repositórios**

```bash
git init
```

- Cria os arquivos necessários e inicia o Git no projeto;
- O diretório passa a ser monitorado pelo Git;
- Os arquivos de controle ficam na pasta oculta `.git`.
- Esse comando deve ser executado uma vez ao iniciar o projeto.

---

🐙 **O que é o GitHub?**

- Plataforma para hospedagem e gerenciamento de repositórios Git;
- Muito utilizado para colaboração entre devs;
- Gratuito para projetos públicos e privados.
- Integrações com CI/CD, wikis, issues e pull requests;
- Facilita o trabalho em equipe e a revisão de código.

---

🚀 **Enviando Repositórios para o GitHub**

- Criar projeto no GitHub;
- Inicializar o Git local;
- Conectar ao repositório remoto;

```bach
git remote add origin https://github.com/usuario/repositorio.git
```

- Enviar com `git push -u origin main` (ou master, dependendo do nome do branch).
- O `-u` define `origin main` como padrão para os próximos `git push`.

---

🔍 **Verificando mudanças no projeto**

```bash
git status
```

- Mostra arquivos modificados, adicionados ou removidos;
- Usado com frequência para monitorar o estado atual do projeto.
- Indica se arquivos estão no `staging` ou aguardando `commit`.
---

➕ **Adicionando arquivos ao projeto**

```bash
git add index.js          # Um arquivo
git add .                 # Todos os arquivos modificados
git add pasta/            # Todos os arquivos da pasta
```

- Move os arquivos para o "staging area";
- Só arquivos adicionados serão salvos no commit.
- A ordem correta: `git add` → `git commit`.
---

💾 **Salvando alterações do projeto (commit)**

```bash
git commit -m "mensagem"              # Commit com mensagem
git commit -a -m "mensagem"           # Adiciona + commita arquivos modificados
```

- Registra alterações no repositório;
- Boa prática: usar mensagens claras e objetivas.
- A flag `-a` adiciona apenas arquivos modificados (não novos).
---

☁️ **Enviando código ao repositório remoto**

```bash
git push
```

- Envia os commits locais para o repositório remoto.
- Normalmente usado após commit para sincronizar com o GitHub.
---

⬇️ **Recebendo mudanças do repositório remoto**

```bash
git pull
```
- Atualiza o projeto local com alterações feitas remotamente.
---

📥 **Clonando repositórios**

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

❌ **Removendo arquivos do repositório**

```bash
git rm arquivo.txt
```
- Remove arquivo do projeto e do controle de versão.
- Necessário fazer commit para finalizar a remoção.
---

🕓 **Histórico de alterações**

```bash
git log
```
- Lista todos os commits feitos no projeto.
- Usa `q` para sair da visualização;
- Pode ser personalizado com `git log --oneline` ou `--graph`.
---

✏️ **Renomeando arquivos**

```bash
git mv antigo.txt novo.txt
```
- Renomeia e mantém o controle de versão do arquivo.
- Equivalente a mv seguido de `git add` e `git rm`.
---

↩️ **Desfazendo alterações**

```bash
git checkout nome-do-arquivo
```
- Volta o arquivo para o estado do último commit.
- Para desfazer commits inteiros: `git reset`
---

🙈 **Ignorando arquivos no projeto**

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

🧹 **Desfazendo todas as alterações**

```bash
git reset --hard
```
- Remove todas as alterações e commits locais;
- **Cuidado:** essa ação é irreversível!
---

📎 **Comandos rápidos**

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

🌿 O que é um branch?

- São ramificações do projeto;
- Permite trabalhar com versões paralelas;
- Geralmente usados para features, hotfixes, etc.

👀 **Visualizando branches**

```bash
git branch
```

✨ **Criando branches**

```bash
git branch nome-da-branch
```

**Renomear localmente**
```bash
git branch -m nome-da-branch nome-da-branch-nova
```

**Enviar a nova branch para o GitHub e configurar tracking**
```bash
git push -u origin nome-da-branch
```

🔁 **Mudando de branch**

```bash
git checkout nome-da-branch
git checkout -b nova-branch   # cria e já muda para ela
```

🗑️ **Deletando branch**

```bash
git push origin --delete nome-da-branch ou git branch -d nome-da-branch
```

🔀 **Unindo branches**

```bash
git merge nome-da-branch
```
---

### 💾 Stash

📥 **Guardando alterações**

```bash
git stash
```

📥 **Recuperando alterações**

```bash
git stash list
git stash apply stash@{0}
```

🧹 **Limpando o stash**

```bash
git stash clear
git stash drop stash@{0}
```
---

### 🏷️ Tags

🏷️ **Criando tags**

```bash
git tag -a v1.0 -m "Versão 1.0"
```

🔍 **Verificando e alternando tags**

```bash
git show v1.0
git checkout v1.0
```

📤 **Enviando tags**

```bash
git push origin v1.0
git push origin --tags
```
---

🔍 **Encontrando novos branches remotos**

```bash
git fetch
```
---

💡**Comandos adicionais úteis**

🌐 **Ver o repositório remoto**

```bash
git remote -v
```
---

🔄 **Recebendo alterações**

📥 `git pull`

- Recebe atualizações do repositório remoto.
- Cada branch pode ser atualizado com `git pull`.
- Usado para atualizar a branch principal (ex: `master`) ou sincronizar mudanças feitas por outros desenvolvedores.

```bash
git pull
```
---

📤 **Enviando alterações**

🚀 `git push`

- Envia alterações locais para o repositório remoto.
- Pode ser usado para compartilhar mudanças de um branch com outros devs.
- Utilizado ao finalizar uma tarefa para enviá-la ao repositório.

```bash
git push
```
---

🌐 **Utilizando o remote**

🔗 `git remote`

- Permite adicionar, visualizar ou remover repositórios remotos.
- Exemplo de adicionar um repositório remoto:

```bash
git remote add origin <link-do-repo>
```
---

#### [➡️ Próximo](conceitos-avancados.md)

| 🌎 LinkedIn                                                              | 👨‍💻 **Autor**                                                                 |
| ------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| [LinkedIn](https://www.linkedin.com/in/albert-backend-java-spring-boot/) | [Albert Silva](https://www.linkedin.com/in/albert-backend-java-spring-boot/) |

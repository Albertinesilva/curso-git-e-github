<h1 align="center">📘Guia Git & GitHub - Parte 2</h1>

### 📦 Trabalhando com submódulos

🧩 `git submodule`

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

🔃 `git push --recurse-submodules=on-demand`

- Commit as mudanças normalmente.
- Para atualizar o repositório do submódulo:

```bash
git push --recurse-submodules=on-demand
```
---

<h2 align="center">📘 Git - Inspeções e Logs</h2>

📄 **Exibindo informações**

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

🧮 **Exibindo diferenças**

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

📊 **Log resumido**

● O comando `git shortlog` nos dá um log resumido do projeto;  
 ● Cada commit será unido por nome do autor;  
 ● Podemos então saber quais commits foram enviados ao projeto e por quem.

```bach
git shortlog
```
---

🏷️ **Utilizando o describe**

● Com o comando `git describe --tags` podemos verificar todas as tags do nosso projeto;

```bach
git describe --tags
```

● Com a opção `--all` recebemos também a referência das tags;

```bach
git describe --all
```
---

🧹 **Limpando arquivos untracked**

- O comando `git clean` vai verificar e limpar arquivos que não estão sendo _trackeados_;
- Ou seja, todos que você não utilizou `git add`;
- Utilizado para arquivos que são gerados automaticamente, por exemplo, e atrapalham a visualização do que é realmente importante.

```bash
git clean -n    # Mostra os arquivos que seriam removidos
git clean -f    # Remove os arquivos não trackeados
```
---

⚙️ **Otimizando o repositório**

- O comando `git gc` é uma abreviação para _garbage collector_;
- Ele identifica arquivos que não são mais necessários e os exclui;
- Isso fará com que o repositório seja otimizado em questões de performance.

```bach
git gc
```
---

🧪 **Checando integridade de arquivos**

- O comando `git fsck` é uma abreviação de _File System ChecK_;
- Esta instrução verifica a integridade de arquivos e sua conectividade;
- Verificando assim possíveis corrupções em arquivos;
- Comando de rotina, utilizado para ver se está tudo certo com nossos arquivos.

```bach
git fsck
```
---

📜 **Reflog**

- O `git reflog` vai mapear todos os seus passos no repositório, até uma mudança de branch é inserida neste log;
- Já o `git log`, que vimos anteriormente, apenas armazena os commits de um branch;
- Os _reflogs_ ficam salvos até expirar, o tempo de expiração padrão é de 30 dias.

```bach
git reflog
```
---

♻️ **Recuperando arquivos com reflog**

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

📦 **Transformando o repo para arquivo**

- Com o comando `git archive` podemos transformar o repositório em um arquivo compactado, por exemplo;
- O comando é:

```bash
git archive --format zip --output master_files.zip master
```
---

<h2 align="center">🛠️ Rebase interativo passo a passo</h2>

O `git rebase -i` (rebase interativo) é uma forma poderosa de reescrever o histórico de commits. Ele permite **editar mensagens, excluir, unir (squash)** ou **organizar commits** de forma limpa e controlada.

🧩 **Exemplos de comandos**

✅ **Rebase por código do commit:**

```bach
git rebase -i fc0bdae
```

- Neste exemplo, `fc0bdae` é o hash do commit anterior ao primeiro que você deseja alterar.

```bach
git rebase main minha-feature -i
```

- Esse comando reescreve o histórico da branch `minha-feature` usando a branch `main` como base. Útil ao usar branches privadas, para depois limpar os commits antes de subir ao repositório.

🔤 **Comandos no editor interativo**

```bach
pick 27354b3 Introdução com alguns Tópicos
pick 36403b9 Conceitos e Formatação do Readme.md
```

### Substitua `pick` por:

- `r` ou `reword`: altera a **mensagem** do commit;
- `e` ou `edit`: permite **editar o conteúdo** do commit;
- `s` ou `squash`: une esse commit ao anterior e mantém as mensagens;
- `f` ou `fixup`: une esse commit ao anterior e **descarta a mensagem** atual;
- `d` ou `drop`: **remove** o commit;

⌨️ **Controles no editor (modo VIM)**

- Entrar no modo edição: pressione `i`
- Sair do modo edição: pressione `ESC`
- Salvar e sair: digite `:x` e pressione `ENTER`
- Forçar saída (se necessário): `:x!`

✅ **Finalizando o rebase**

Após salvar, o Git pode pedir para:

```bach
git rebase --continue
```

- Caso haja conflitos, resolva-os, faça `git add` e continue o rebase.

🔁 **Retornando à branch original**

Se estiver em modo `detached HEAD`:

```bach
git checkout main
```

📤 **Atualizando o GitHub após rebase**

Se você alterou o histórico com `rebase`, será necessário forçar o push:

```bach
git push origin main --force
```

⚠️ Atenção: Use `--force` com cuidado para não sobrescrever o trabalho de outras pessoas.

---

✅ **Exemplos com `&&` para agilizar `comandos Git`**

O operador `&&` permite encadear vários comandos no terminal. Ele executa o próximo comando **somente se o anterior for bem-sucedido**.

🔹 1. Adicionar, comitar e fazer push de uma vez só

```bach
git add . && git commit -m "mensagem do commit" && git push
```

🔹 2. Adicionar um arquivo específico, comitar e fazer push

```bach
git add README.md && git commit -m "Atualiza README com exemplos de uso" && git push
```

🔹 3. Reverter alterações em um arquivo, adicionar e comitar

```bach
git restore nome-do-arquivo.txt && git add nome-do-arquivo.txt && git commit -m "Reverte mudanças no arquivo"
```

🔹 4. Mudar de branch, dar pull e abrir a pasta no VS Code

```bach
git checkout main && git pull && code .
```

🔹 5. Após um rebase, continuar e fazer push forçado

```bach
git rebase --continue && git push --force
```

📝 **Dica: no PowerShell (Windows), substitua && por ;:**

```bach
git add .; git commit -m "Mensagem"; git push
```
---
<h2 align="center">🧠 Boas Práticas com Commits e Branches</h2>

✅ **A importância do commit**

- O problema: commits sem sentido atrapalham o projeto;
- Precisamos padronizar os commits, para que o projeto cresça de forma saudável também no versionamento, isso ajuda em:
    - Review do Pull Request;
    - Melhoria dos logs com `git log`;
    - Manutenção do projeto (voltar código, por exemplo).

✍️ **Boas mensagens de commit**

- Separar assunto do corpo da mensagem;
- Assunto com no máximo 50 caracteres;
- Assunto com letra inicial maiúscula;
- Corpo com no máximo 72 caracteres por linha;
- Explicar por que e como o commit foi feito — e não como o código foi escrito.

🔁 **Branches com commits ruins**

- Há uma solução chamada private branches;
- Criamos branches que não serão compartilhados no repositório (podem ter qualquer commit);
- Ao fim da solução do problema, podemos fazer um rebase;
- Exemplo de comando:

```bach
git rebase <atual> <funcionalidade> -i
```
- Durante o rebase interativo:
    - Escolha os commits para excluir com `drop` ou juntar com `squash`;
    - Renomeie mensagens com `reword`.

🛠️ **Dicas práticas com git commit**

- Evite commits genéricos como `Update`, `Changes`, `Fixes`.
- Prefira algo como: `Corrige validação de e-mail no formulário de login`.
- Use `git commit -v` para revisar as alterações no editor antes de confirmar.

🌿 **Nomeação de branches**

- Use nomes descritivos para as branches:
    - `feature/adicionar-login`
    - `bugfix/erro-validacao-email`
    - `hotfix/ajuste-navbar-mobile`
- Isso ajuda na leitura e organização do repositório.
---

📝 **O que é Markdown?**

O Markdown é uma forma simples e intuitiva de adicionar estilo a textos na web, especialmente útil para documentações.

- Permite exibir: trechos de código, links, imagens e muito mais.
- Arquivos como `README.md` usam Markdown para criar uma documentação mais bonita e organizada.
- Melhora a experiência de quem acessa seu repositório no GitHub.

🖼️ **Imagens**

Você pode adicionar imagens no markdown com a seguinte sintaxe:
```bach
![Texto Alt](link-da-imagem)
```
```bach
![Logo GitHub](imag/GitHub-Mark.png)
```
- Você pode usar imagens externas ou armazenadas dentro do seu repositório.

🔗 **Links**

Markdown facilita a inserção de links:
```bach
[Texto do link](https://www.exemplo.com)
```

🏷️ **Cabeçalhos**

Usamos o símbolo `#` para criar títulos, assim como em HTML (`h1`, `h2`, `h3`...):
```bach
# Título Principal (h1)
## Subtítulo (h2)
### Título menor (h3)
```

✨ **Ênfase**

Dê estilo ao texto com os seguintes símbolos:

- Negrito: `**texto**` ou `__texto__`
- Itálico: `*texto*` ou `_texto_`
- Um texto combinado

✅ **Listas**

Listas não ordenadas:

```bach
* Item 1
* Item 2
```
Listas ordenadas:

```bach
1. Primeiro
2. Segundo
```

💻 **Código (GitHub)**

Use `crase tripla` para destacar blocos de código:

```bash
git status
git add .
git commit -m "mensagem"
```

📋 **Task list (GitHub)**

Permite criar listas de tarefas diretamente no README:

- [x] CSS do rodapé
- [ ] CSS da página de contatos
- [ ] Ajustar responsividade do layout
---

<h2 align="center">🌐 Conceitos essenciais do GitHub</h2>

📦 **Criando repositório**

- No GitHub inicializamos os repositórios, e temos algumas informações importantes para - preencher, vamos vê-las em detalhes;
- Algumas delas são: Nome do repo, descrição, licença;
- Tudo poderá ser alterado ao longo do seu projeto, mas é interessante conhecer os detalhes das informações para configurar um projeto;
- É possível também iniciar o repositório com um arquivo `README.md`, `.gitignore` e escolher a visibilidade (público ou privado).

📁 **A aba Code**

- Na aba Code teremos acesso a informações importantes, como o próprio código fonte;
- Podemos checar também uma documentação do projeto pelo `README.md`;
- E os detalhes da licença do projeto;
- Criar branches, adicionar arquivos e muito mais!
- Também é possível clonar o repositório por HTTPS, SSH ou GitHub CLI.

🐞 **A aba Issue**

- Na aba Issue podemos criar tarefas ou possíveis bugs do projeto;
- Interessante para a organização se manter ciente do que ainda precisa fazer ou corrigir;
- Normalmente há um padrão para criação de novos issues;
- Podemos utilizar o Markdown no texto também (igual o `README.md`);
- A issue deve ter uma label e também um responsável;
- É possível mencionar usuários com `@usuario` e referenciar outras issues ou pull requests com `#número`.

🔃 **A aba Pull Request**

- Na aba Pull Request é onde os colaboradores do projeto enviam código para resolver as issues ou adicionar novas funcionalidades ao projeto;
- A ideia é que o código não seja inserido direto na master e sim passe por um pull request, para ser analisado;
- O `pull request` pode ser revisado por membros da equipe antes de ser mesclado;
- É possível adicionar comentários, checklists e aprovações antes do merge.

📈 **A aba Insights**

- Na aba Insights temos informações detalhadas do projeto, como:
- Quem são os contribuidores, commits, forks e muito mais;
- Interessante para entender como o projeto está andando e a sua evolução desde o início;
- O pull request vem de um novo branch criado no projeto e enviado para o repo, com o incremento de código;
- Também é possível visualizar gráficos de contribuição e análise de linguagens usadas.

⚙️ **A aba Actions**

- Na aba Actions é onde se cria as automatizações de deploy com integração em outros serviços;
- Incluindo CI/CD (Continuous Integration / Continuous Development);
- Ou seja, podemos criar uma rotina de atualizar a master automaticamente e outros processos;
- As automações são configuradas por meio de arquivos `.yml` na pasta `.github/workflows`.

📋 **A aba Projects**

- Na aba Projects podemos criar um projeto e utilizar um quadro de tarefas;
- Este processo é conhecido como Kanban e pode ajudar a organizar seu time, criando notas que podem virar issues;
- Estrutura interessante: Backlog, Retorno de qualidade, Desenvolvimento, Teste, Finalizadas;
- A tela lembra muito o software Trello;
- Os cards do Kanban podem ser vinculados diretamente a issues e pull requests.

📚 **A aba Wiki**

- Na aba Wiki podemos criar uma documentação mais extensa para o projeto;
- Como descrever funcionalidades, bugs conhecidos e não solucionados, entre outras funções;
- A ideia é que seja um repositório de conhecimento sobre o projeto;
- A Wiki pode conter várias páginas interligadas, como um manual do projeto.

🔧 **A aba Settings**

- Na aba Settings temos acesso a diversas configurações do projeto;
- É onde podemos alterar o nome do repo ou remover/adicionar features;
- E também é nela que adicionamos colaboradores ao projeto;
- O repositório pode ser removido nesta aba;
- Também é possível configurar o GitHub Pages, personalizar branches e permissões.

✂️ **Criando um Gist**

- Gist são pequenos blocos de código que podem ser hospedado no GitHub também;
- Você pode armazenar uma solução que achou interessante para algum problema e não quer perder, por exemplo;
- E o link do Gist pode ser compartilhado;
- No fim das contas o Gist acaba sendo um repositório também;
- Gists podem conter múltiplos arquivos e são públicos ou privados.

🔎 **Encontrando repositórios**

- O GitHub não serve só para salvar os nossos projetos, podemos encontrar muitos repos interessantes;
- Podemos até aprender com isso também, olhando o código fonte de desenvolvedores experientes;
- E não para por aí: você pode dar star nos projetos que gostou ou fork nos que deseja continuar em um repo próprio;
- A aba “Explore” ajuda a encontrar repositórios populares, trending e recomendados.
---

<h2 align="center">🌐 O que é GitHub Pages</h2>

- 📄 Uma forma de criar uma página estática nos servidores do GitHub;
- 💸 Ou seja, uma alternativa gratuita para hospedar nosso portfólio;
- ⚙️ Muito simples de colocar no ar, não precisa de domínio ou servidor;
- 🏢 Muitas empresas utilizam para apresentar o seu projeto ou a própria documentação;
- 🔒 O site é servido via HTTPS e pode ser personalizado com domínio próprio, se necessário.

🚀 **Como criar a página**

Você deve seguir alguns passos simples, veja:

1. 📁 Criar um repositório com o nome nomedousuario.github.io
    - O GitHub reconhece esse padrão como um site pessoal.
2. 💻 Clonar o repositório no nosso computador
    - Usando git clone https://github.com/nomedousuario/nomedousuario.github.io.
3. 🧾 Adicionar o código do projeto na branch master
    - Para repositórios pessoais, o GitHub Pages usa a branch master ou main.
4. ⬆️ Enviar o código por meio de push
    - Usar git add ., git commit -m "initial commit" e git push origin master.
5. ✅ E pronto, você tem um site em https://nomedousuario.github.io
    - O site geralmente leva poucos minutos para entrar no ar.
---

#### [⬅️ Voltar](README.md)

| 🌎 LinkedIn                                                              | 👨‍💻 **Autor**                                                                 |
| ------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| [LinkedIn](https://www.linkedin.com/in/albert-backend-java-spring-boot/) | [Albert Silva](https://www.linkedin.com/in/albert-backend-java-spring-boot/) |

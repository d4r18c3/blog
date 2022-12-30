---
title: "Curadoria de comandos básicos para git e github"
slug: "curadoria-comandos-git-github"
date: 2022-12-30
draft: false
toc: true
thumbnail: "images/landscape.jpg"
tags:
- git
- github
categories: 
- Configurações
---



{{< figure src="/media/spf13.jpg" title="Steve Francia" >}}

{{ $readTime := mul (div (countwords .Content) 220.0) 60 }}

<p>Reading time: {{ math.Floor (div $readTime 60) }} minutes and
    {{ mod $readTime 60 }} seconds.</p>

## Primeiras configurações

### Valores globais mandatórios

**Observação: manter user.email, user.name**

> git config --global user.email "you@example.com"
> git config --global user.name "Your Name"



### Configuração de autenticação SSH

1. > $ ssh-keygen -t rsa -b 4096 -C "dc3@mailbox.org"

2. Procurar a pasta de .ssh mostrada no console

3. Abrir o arquivo pub

4. Ir até settings/ssh keys e adicionar essa chave



### Criar e vincular um repositório (pela primeira vez)

#### No Github

1. Acessar a página do github e criar o novo repositório;
2. Na opção de botão HTTPS/SSH, marcar SSH;
3. Anotar o nome do seu branch principal (master, main, etc);
4. (tem que ter executado git init no diret´)
5. Copiar a linha git remote add... (git remote add origin git@github.com:mezengasoftware/java-pills.git).

#### No Gitbash

1. git init (inicia um repositório local);
2. git add . (adiciona todo o diretório ao stage);
3. git commit -m "mensagem explicativa do commit";
4. git branch -M main (considerando que main é o nome do seu branch principal, criado anteriormente no github);
5. git remote add origin git@github.com:mezengasoftware/java-pills.git (vincula o repositório local ao repositório remoto;
6. git push -u origin main (considerando que main é seu branch principal)



### Comandos rotineiros de atualização

//Adicionar tudo ao Stagging?

git add .



//

git commit -m "Mensagem aqui!"



//Verificar alterações.

git status

git push

git log --oneline



#### Git checkout

`git checkout <código>`

ou

`git checkout HEAD~x`

`git checkout main` (para voltar ao topo. **certifique-se que não haja mudança nos arquivos!**)

**Caso eu tenha feita alguma alteração acidental:**

`git reset` (Tirar arquivos da área de stage)

`git clean -df`

`git checkout -- .` (Checkout para limpart modificações)



#### Clonar e modificar um repositório

Clonar para trazer projeto **e histórico**.

`git clone git@github.com:mezengasoftware/java-pills.git`

`git add .`

`git commit -m "mensagem"`

`code .` (Abrir VSCode no diretório de trabalho)

`git push`



### Outros comandos

`git log`

`git log --online`

`code .` (Abrir VSCode)

`ls`



## Resolvendo problemas comuns no Git

1. Como remover arquivos da área de stage?

   > Contexto: Adicionei arquivos para stage, porém me arrependi.

`git status`

`git reset`



2. Como modificar modificações não salvas? 

   > Contexto:  Volta o projeto para estado do último commit.

`git status`

`git reset`

`git clean -df`

`git checkout -- .`



3. O que fazer quando abre o editor Vim?

   > Contexto: Alguns comandos podem abrir o edito vim automaticamente. Ex. commit sem mensagem.

​	`i` (Habilita a edição)

<esc>`:wq`<enter> (Write, Quit: Salva alterações)

<esc> `:q!` <enter> (Quit, Force: Sai sem salvar alterações)



4. O que fazer quando abre o editor nano?

`ctrl o` (salvar)

`ctrl x` (sair)



5. Como desfazer o último commit?

> Quero aproveitar a maioria das alterações, mas faltou uma coisinha pra mudar. Então eu defaço o commit, mantendo as modificações anteriores, apenas adicionando a coisinha.
>

 `git status`

 `git reset --soft HEAD~1` (Soft não apaga as alterações)



6. Deletar commits e também as modificações dos arquivos?

> Volta até o commit escolhido, deletando ações de commits posteriores. **Ação destrutiva!**
>

`git status`

`git reset --hard HEAD~1` (Volta para o penúltimo commit)

ou

`git reset --hard <Código do commit>` (Código do commit)



7. Como atualizar o repositório local em relação ao remoto?

`git pull origin main`



8. Como resolver push rejeitado?

> O histórico do projeto local esta atrasado/divergente em relação ao remoto. Após git pull origin main, o editor de texto será aberto com um nome proposto de commit, afim de efetuar o merge de três vias. No nano, ctrl + o, ctrl + x salva e fecha o editor.

 `git pull origin main` 

`git push`



9. Conflito de edição de mesmo arquivo em dois locais diferentes ou por duas pessoas.

`Vou obter o erro de conflito, ao fazer o pull e usar git status, o Git me avisa do conflito. Uso code . para verificar o conflito e remover o errado.` 



10. Como sobrescrever um histórico no Github?

> Ao encontrar disparidade de commits entre repositório local e remoto, avalio a situação e percebo que posso sobrescrever o último commit remoto. Ou seja, vou ignorar a disparidade de commits e forçar um push, pois sei que no meu repositório local esta tudo certo. **Ação destrutiva!**

`git push -f`



11. Verificar qual é o repositório remoto e apontar para outro.

    > Criar outro repositório remoto. Apontar meu repositório local para este novo remoto (set-url), conservando todo o histórico! 

`git remote -v`

`git remote set-url origin git@github.com:mezengasoftware/java-pills.git`



## Reconhecer arquivos SQL

https://github.com/Thomas-George-T/HackerRank-SQL-Challenges-Solutions/issues/1

> `.gitattributes` solved this issue for me!

> after providing
>  *.sql linguist-detectable=true
>  *.sql linguist-language=sql

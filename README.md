# Git Quick Guide

## ❶ Sobre este guia
Este guia foi criado como um lembrete rápido dos pontos e comandos mais importantes do Git que merecem atenção no uso diário.
Também encaro este documento como uma forma de reafirmar que o conteúdo foi compreendido e aprendido por mim com sucesso ao longo da prática.

## ❷ Conceitos essenciais

- **Repositório (Repository)**  
  É o local onde o projeto e todo o seu histórico de alterações ficam armazenados. Pode ser local (na sua máquina) ou remoto (como no GitHub).

- **Commit**  
  É um registro de mudanças no repositório. Cada commit representa um “snapshot” do estado do projeto em um determinado momento.

- **Branch**  
  É uma linha paralela de desenvolvimento. Permite trabalhar em funcionalidades ou correções sem afetar a versão principal do projeto.

- **Working Directory**  
  É a área onde os arquivos estão sendo editados no momento. Alterações feitas aqui ainda não fazem parte de um commit.

- **Staging Area (Index)**  
  Área intermediária onde você seleciona quais mudanças irão entrar no próximo commit.

- **Remote**  
  É um repositório externo, geralmente hospedado em plataformas como GitHub, usado para compartilhar e sincronizar código.

- **HEAD**  
  Indica a posição atual no histórico do Git, normalmente apontando para o commit mais recente do branch ativo.

## ❸ Setup inicial do Git

Verifique se o Git está instalado:
```bash
git --version
```
Configure o nome de usuário:
```bash
git config --global user.name "Seu Nome"
```

Configure o email:
```bash
git config --global user.email "seu@email"
```

Verifique as configurações atuais:
```bash
git config --list
```

## ❹ Comandos essenciais

```bash
# Inicialização e configuração
git init                 # Inicializa um repositório Git
git clone URL            # Clona um repositório remoto

# Status e inspeção
git status               # Mostra o estado do repositório
git log                  # Exibe o histórico de commits
git log --oneline        # Histórico resumido
git diff                 # Mostra diferenças nos arquivos

# Staging e commits
git add .                # Adiciona todas as mudanças à staging area
git add arquivo.ext      # Adiciona um arquivo específico
git commit -m ""         # Cria um commit com mensagem
git commit --amend       # Altera o último commit

# Branches
git branch               # Lista branches
git branch nome-branch   # Cria um novo branch
git checkout nome        # Muda de branch
git switch nome          # Alternativa moderna ao checkout

# Repositório remoto
git pull                 # Atualiza o repositório local
git push                 # Envia commits para o remoto
git remote -v            # Lista repositórios remotos

# Limpeza e correção
git restore arquivo      # Descarta mudanças em um arquivo
git reset HEAD arquivo   # Remove arquivo da staging area
```
## ❺ Fluxo básico de trabalho

1. Fazer alterações nos arquivos  
   → Arquivos são editados no *Working Directory*

2. Verificar o estado do repositório  
```bash
git status
```
3. Adicionar mudanças à Staging Area
```bash
git add .
```
4. Criar um commit com as mudanças adicionadas
```bash
git commit -m "mensagem do commit"
```
5. Enviar os commits para o repositório remoto
```bash
git push
```
6. Outros importantes
```bash
ls - mostra em qual pasta está
```
## ❻ Branches (básico)

### 1. O que é uma branch

Uma branch é uma linha paralela de desenvolvimento dentro do mesmo repositório. Ela permite trabalhar em mudanças sem afetar diretamente a versão principal do projeto. Pense em ramificações, que serão (se bem sucedidas) atribuidas ao projeto principal.

---

### 2. Por que branches existem

* Permitem desenvolver funcionalidades de forma isolada
* Ajudam a testar mudanças com segurança
* Mantêm o histórico de commits mais organizado

---

### 3. Branch principal

Geralmente chamada de `main` (ou `master` em projetos antigos).

* Representa a versão mais estável do projeto
* Recebe apenas código que já foi revisado ou testado

---

### 4. Operações básicas com branches

As ações mais comuns envolvendo branches são:

* Listar branches existentes (`git branch`)
* Criar uma nova branch (`git branch nome-da-branch`)
* Trocar de branch (`git switch nome-da-branch` ou `git checkout nome-da-branch`)
* Unir branches por meio de merge (ramificações bem sucedidas lembra?)

---

### 5. Observação (muito) importante 

Branches não criam cópias físicas dos arquivos. Elas apenas apontam para commits diferentes dentro do mesmo histórico do repositório.

---

## ❼ Problemas comuns
### 1. Commits não aparecem no gráfico do GitHub

Geralmente acontece quando:

Os commits foram feitos em um repositório privado

O email configurado no Git não está associado à conta do GitHub

Os commits foram feitos em um branch diferente do main

### 2. Alterações não entram no commit

Normalmente ocorre quando os arquivos não foram adicionados à staging area antes do commit.

Verifique o estado do repositório com git status

Adicione os arquivos corretamente antes de commitar

### 3. Commit com mensagem errada

É possível corrigir o último commit antes de enviá-lo ao repositório remoto usando git commit --amend.

### 4. Commit feito no branch errado

Esse problema costuma acontecer ao esquecer de trocar de branch antes de commitar.

Sempre confirme o branch atual antes de criar um commit

Evite trabalhar diretamente na branch principal

### 5. Arquivo commitado por engano

Arquivos que não deveriam entrar no repositório devem ser ignorados usando .gitignore.

### 6. Conflitos durante merge ou pull

Conflitos surgem quando o Git não consegue resolver mudanças automaticamente.

Leia os arquivos indicados

Escolha manualmente quais alterações manter

Finalize o merge após resolver os conflitos

## ❽ Boas práticas (Pode ter certeza que te ajudarão a curto e longo prazo)
### 1. Commits pequenos e frequentes

Commits menores facilitam revisão, entendimento e correção de erros.

### 2. Mensagens de commit claras

Uma boa mensagem explica o que foi feito, não apenas que algo mudou.

### 3. Usar branches para mudanças

Evite trabalhar diretamente na branch principal sempre que possível.

### 4. Não versionar arquivos desnecessários

Use .gitignore para evitar subir arquivos temporários, dependências ou dados sensíveis.

### 5. Verificar antes de enviar

Antes de usar git push, confira:

Branch atual

Arquivos incluídos no commit

Mensagem do commit

---

## ❾ Pull Requests (básico)

### 1. O que é um Pull Request (PR)

Um Pull Request é uma solicitação para que mudanças feitas em uma branch sejam revisadas e incorporadas a outra branch, normalmente a `main`. 

---

### 2. Quando usar Pull Requests

* Ao trabalhar em equipe
* Ao querer revisar mudanças antes de integrá-las
* Ao contribuir para projetos open source

Mesmo em projetos pessoais, PRs ajudam a manter organização.

---

### 3. Relação entre branch e PR

O fluxo comum é:

* Criar uma branch para a mudança
* Fazer commits nessa branch
* Abrir um Pull Request apontando para a branch principal

O PR é o “pedido formal” de merge.

---

### 4. Vantagem principal

Pull Requests criam um ponto claro de:

* Revisão
* Discussão
* Histórico de decisões

---

## ❿ gitignore

### 1. O que é o `.gitignore`

É um arquivo que define quais arquivos ou pastas o Git deve **ignorar**, ou seja, não versionar.

---

### 2. Por que usar `.gitignore`

* Evita subir arquivos desnecessários
* Mantém o repositório limpo
* Impede versionar dados sensíveis ou temporários

---

### 3. Onde fica o `.gitignore`

* Na raiz do repositório
* Versionado junto com o projeto

---

### 4. Exemplos comuns de uso

Normalmente ignoram-se:

* Dependências
* Arquivos temporários
* Configurações locais
* Pastas de build

Cada tipo de projeto tem seu próprio padrão de `.gitignore`.

---

## ⓫ Referências rápidas

### 1. Documentação oficial

A documentação oficial do Git é a fonte mais confiável para detalhes e comandos avançados. Esse quick guide não substitui de forma alguma o documento original.

---

### 2. Cheatsheets

Cheatsheets são úteis para:

* Revisão rápida
* Consulta durante o uso
* Aprender novos comandos aos poucos

---

### 3. Aprendizado contínuo

Git é uma ferramenta ampla e muito poderosa. O uso frequente é o que consolida o aprendizado de verdade. 

---

## ⓬ Encerramento

Este guia não tem como objetivo cobrir **todos** os detalhes do Git, mas sim servir como uma **referência rápida e prática** para autodidatas e iniciantes que já entraram em contato com o tópico em questão...

Ele pode ser usado tanto como:

* Consulta no dia a dia
* Revisão de conceitos

Adendo:
Se este guia te ajudou de alguma forma, ele já cumpriu seu propósito.
Vou atualizar esse guia com o passar do tempo...
Se este projeto foi útil para você, considere deixar uma ⭐.
Sugestões e contribuições são bem-vindas.

---



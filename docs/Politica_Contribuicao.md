# Políticas de Contribuição

## 1. Introdução

Esse documento guia como devem ser feitas as contribuições no projeto para criar uma padronização e facilitar na organização do projeto.

## 2. Guia de Contribuição

Parar criar um Issue no projeto é necessário seguir os templates, de história de usuário, Bug e documentação.

Antes de abrir uma issue é importante analisar se aquele tópico já naõ foi discutido anteriormente, para evitar duplicidade.

Ao criar uma issue com algum dos templates, use as labels a seguir para melhor identificação: HOTFIX, DOCS, FEATURE, US, ARQ, DEVOPS, ANALYTICS, EASY, MEDIUM ou HARD.

### 2.1. Sugerir Melhorias

Para sugerir uma melhoria, uma issue deve ser criada seguindo o template abaixo:

```
# Nome da melhoria a ser sugerida

## Descrição

Descrever a melhoria breve e objetivamente

## Detalhamentos importantes da melhoria

Explicar de forma mais detalhada o que deve ser feito para a melhoria ser apresentada

## Contexto adicional

Adicione comentários adicionais que considerar importante

## Protótipo

Adicione um protótipo da sua melhoria, lembre de seguir o guia de estilo do projeto.
```

# 3. Política de Branches

Aqui esta uma descrição de como é o padrão de criação de branches nos repositório de código fonte e no de documentação.

## Para o repositório Doc

### Main

<p align="justify" style="text-indent: 20px">
    Branch principal do repositório, apresenta código em sua última versão e estável para o usuário final. Por isso possui as seguintes regras:
</p>

- Só existe uma main no projeto;
- Commits não são permitidos diretamente nessa branch;
- Mudanças nela só ocorrem por meio de pull requests das branches.

### Outras Branches

<p align="justify" style="text-indent: 20px">
    Essas branches tem o objetivo de resolver 1 issue, por isso o padrãod e nomeclatura é o número da issue seguido pelo nome da issue:
</p>    

- Só pode existir uma branche por issue, evitar duplicidade.

```bash
Exemplo: 113-Metodologia
```

## Para os repositórios de Desenvolvimento

### Develop

<p align="justify" style="text-indent: 20px">
    Branch principal do projeto, apresenta código em sua última versão e estável para o usuário final. Por isso possui as seguintes regras:
</p>

- Só existe uma develop no projeto;
- Commits não são permitidos diretamente nessa branch;
- Mudanças nela só ocorrem por meio de pull requests das branches release.

### Outras Branches

<p align="justify" style="text-indent: 20px">
    Branch destinada a alterações no projeto. Suas regras são:
</p>

- Deve ser derivada da develop;
- O padrão de nome delas segue o tipo da issue seguido pela nome da issue que sera resolvida.


```bash
Exemplo: feat/melhoria-perfil
```

# 4. Estrutura dos _Commits_

Aqui tem uma descrição de como é o padrão de commits realizados no projeto.

Os commits devem ser atômicos (uma contribuição pequena para resolver um problema específico) e significativos. A mensagem do commit deve conter o que foi feito de maneira sucinta e direta, além disso ela precisa estar em **português**, **começar** com um **verbo** e com a **primeira letra maiúscula**. Exemplo de como um commit deve ser feito:

```
$ git commit -m "Adiciona estrutura inicial do documento de identidade visual"
```

Caso mais de uma pessoa tenha trabalhado no commit, a funcionalidade co-autoria deve ser feita, da seguinte maneira:

```
$ git commit -m "Cria model do usuário
>
>
Co-authored-by: name <name@example.com>
Co-authored-by: another-name <another-name@example.com>"
```

# 5. Pull Request

Os Pull Request são criados seguindo o template:


1. Nome, deve ter o número e nome da issue: `# N° - Nome Issue`
2. Conteúdo, deve ser uma lista com principais modificações:

```
1. Descrição breve da issue
2. Tipo de Mudança
3. Checklist (Pré-requisitos para verificar se a tarefa foi realizada)
4. Capturas de Tela (se apropriado)
5. Como Testar
```

## 3. Versionamento do Documento

| Data | Versão | Descrição | Autor |
| :-----: | :-------------: | :---------------: | :-: |
| 26/01/2025 | 1.0 | Criando versão inicial do documento | [Artur Vinícius Dias Nunes](https://github.com/ArturVinicius) |
# Contribuindo

Este projeto é baseado na teoria de _Crowdsourcing Database_. Isto significa que
o banco de dados disponibilizado é mantido pela própria comunidade,
possibilitando que qualquer pessoa adicione ou atualize as informações aqui
presentes.

Muito obrigado pelo interesse em contribuir com este projeto. Com o esforço de
todos, podemos construir a maior e melhor base de informações de CEPs do Brasil.

## Informando um Problema

Encontrou algum problema? Você não precisa saber programar para ajudar neste
projeto. Por favor, [adicione uma nova
_issue_](https://github.com/carteiro/ceps/issues/new), informando o problema.
Adicione no conteúdo da solicitação o máximo de informações possíveis, como
número de CEP inválido, nome de arquivos com possíveis erros ou problemas na
estrutura do documento `JSON` descrito.

Caso você saiba trabalhar com Git e possui uma conta no GitHub, por favor, tenha
conhecimento da estrutura do repositório e crie um _patch request_ (PR) com suas
alterações.

## Estrutura do Repositório

Este projeto é controlado através de _tags_ no formato de versionamento
semântico, com 2 _branches_ principais: `master` e `develop`. Todas as _tags_
representam informações estáveis e a última _tag_ sempre aponta para o _branch_
`master`. Todos os _branches_ deverão ter como _fork_ o _branch_ `master` e
sofrem _merge_ no _branch_ `develop`. Quanto uma _tag_ é criada, todos os
_branches_ que não sofreram _merge_ deverão receber um _rebase_ no _branch_
`master`.

Isto quer dizer que todos os _branches_ devem sair da última versão estável e
devem receber _merge_ no _branch_ de desenvolvimento. Quanto todas as tarefas do
_milestone_ atual forem finalizadas, então o _branch_ principal será
sincronizado com o desenvolvimento, fazendo com que o _branch_ principal
represente sempre a última versão do projeto.

## Estrutura do Documento

Todos os documentos estão no formato `JSON` e disponíveis no diretório `data/`,
com O nome de cada arquivo respeitando o padrão `/^[0-9]{8}\.json$/`. Ainda,
cada documento `JSON` deve possuir todas as informações e somente as informações
a seguir.

| Atributo   | Tipo   | Descrição                            |
| ---------- | ------ | ------------------------------------ |
| \_id       | string | Código de Endereçamento Postal (CEP) |
| tipo       | string | Tipo de Logradouro                   |
| logradouro | string | Nome do Logradouro                   |
| bairro     | string | Bairro                               |
| cidade     | string | Cidade                               |
| estado     | string | Sigla do Estado                      |

O atributo `_id` deve possuir um mesmo CEP do nome do arquivo. Os valores
armazenados nos atributos `tipo` e `estado` devem ser válidos e previamente
reconhecíveis pelo projeto. Por fim, os atributos `logradouro`, `bairro` e
`cidade` não devem ser vazios.

## Patch Requests (PR)

Seguindo os padrões da estrutura do repositório, crie um _branch_ para alteração
do código a partir do _branch_ `master`, que representa a última versão estável
do projeto.

Todos os PRs serão verificados pelo [Travis
CI](https://travis-ci.org/carteiro/ceps), que efetua a leitura de toda a base de
dados cadastrada, procurando por algum erro de conteúdo e estrutura.
Basicamente, o Travis CI executa os testes unitários através da ferramenta de
linha de comando `npm`, conforme exemplo abaixo.

```bash
npm test
```

Para rodar os testes locais, já fornecemos o ambiente através do `docker`, bastando rodar o comando abaixo:

```bash
docker-compose run test /bin/sh -c "cd /src && npm install && npm test"
```

Happy Coding!

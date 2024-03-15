# @NoAds web workspace

> Workspace para os projetos webs do NoAds.

## Pre-requisitos

Antes de começar, precisamos de algumas ferramentas instaladas:

- [NodeJS](https://nodejs.org/en) na versão 20.11.1
- [pnpm](https://pnpm.io/) na versão 8.15.4

Caso você utilize o VS Code como ferramenta de desenvolvimento, será exibida uma caixa de notificação perguntando se você deseja instalar as extensões recomendadas pelo nosso projeto. Você pode instalar sem receio.

![VS Code recomendando a instalação das extensões](./.github/images/vscode-recomendacao.jpg)

É extremamente importante que às versões sejam as mesmas, pois assim, todos os contribuidores poderão reproduzir os projetos de maneira semi-identica.

> Recomendação
> Existem ferramentas que ajudam a fazer esse controle automaticamente. Para as versões de Node, existe o [Volta](https://docs.volta.sh/guide/), o [ASDF](https://asdf-vm.com/contribute/documentation.html#initial-setup), o [NVM](https://github.com/nvm-sh/nvm), e até mesmo o próprio [pnpm](https://pnpm.io/cli/env).
>
> Já para o NPM, eu sugiro fortemente a instalação do [corepack](https://github.com/nodejs/corepack), que é uma ferramenta oficial do Node que gerencia as versões dos gerenciadores de pacotes automaticamente. Aqui estão os passos de como usar:
>
> 1. Instale o corepack globalmente com npm (ou pnpm): `npm install -g corepack`
> 2. Rode o comando para "ativar" a versão do pnpm que a gente vai usar: `corepack prepare pnpm@8.15.4 --activate`
> 3. Vá na sua configuração de terminal (.bash_profile, .zshrc, etc.), e adicione o seguinte alias: `alias pnpm="corepack pnpm"`
> 4. Reinicie seu terminal.

## Começando

Primeiro, faça o clone do repositorio.

Em seguida, na raiz do projeto, rode o seguinte comando:

```bash
pnpm i
```

Feito isso, todas as dependencias de todos os projetos vão ser instaladas.

Como este projeto é um monorepo, ele segue a seguinte estrutura:

- root (`./`): é o ponto de partida do projeto. Aqui a gente vai ter o package.json central que vão ter dependencias para manutenção do repositorio. Nenhuma dependencia especifica de projeto deve ser instalada aqui.
- packages (`./packages/*`): a pasta onde packages que pode ser reutilizadas em outros projetos vai ficar.
- apps (`./apps/*`): a pasta dos projetos em si.

## Rodando um projeto

Imagine que você queira rodar o comando `dev` do projeto chamado `@noads/webapp`. Em um monorepo, há duas maneiras de rodar um comando de um projeto.

A primeira é na raiz do projeto. Abra o terminal e rode o comando

```bash
pnpm --filter @noads/webapp run dev
```

A flag --filter pode ser usada para qualquer comando pnpm, inclusive no `add`:

```bash
pnpm --filter @noads/webapp add -E lodash-es
```

Ou então, você pode navegar até o projeto e rodar o comando dentro de seu diretório:

```bash
cd ./apps/webapp && pnpm run dev
```

Caso queira rodar algum comando através do Turbo (que vai rodar todos as dependencias em cascata), é a quase a mesma coisa. A única diferença é que agora você precisa passar `turbo`:

```bash
pnpm turbo --filter @noads/webapp run dev
```

> [!Note]
> Vale ressaltar que o comando só vai funcionar se ele estiver listado dentro do `./turbo.json[pipelines]`.

## Ferramentas do projeto

Esse projeto foi configurado com às seguintes ferramentas:

- pnpm: gerenciamento de dependencias e controle do workspace entre as packages e apps;
- biome: substituto do ESLINT e Prettier, mas escrito em Rust. Ele já tem suporte pra TypeScript nativamente e roda extremamente rapido.
- turbo: o motor do monorepo. Com essa ferramenta é possível rodar comandos em ordem de importancia entre as packages e os projetos. Também faz um trabalho de cachear os processos que já foram executados, evitando rodar comandos desnecessariamente.

## Criando uma nova package

<!-- TODO -->

## Criando um novo projeto

<!-- TODO -->

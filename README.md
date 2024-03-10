# @NoAds web workspace

> Workspace para os projetos webs do NoAds.

## Pre-requisitos

Antes de começar, precisamos de algumas ferramentas instaladas:

- [Volta](https://docs.volta.sh/guide/getting-started) - Volta é uma ferramenta que garante que todos os usuarios do repositorio, vão utilizar a mesma versão de NodeJS e a mesma versão do pnpm.

O suporte pra pnpm no Volta ainda é experimental, apesar de funcionar muito bem. Você vai precisar adicionar no seu profile do terminal (.bash_profile, .zshrc, etc.) a seguinte variável de ambiente:

```bash
export VOLTA_FEATURE_PNPM=1
```

## Começando

Primeiro, faça o clone do repositorio.

Em seguida, na raiz do projeto, rode o seguinte comando:

```bash
pnpm i
```

Feito isso, todas as dependencias de todos os projetos vão ser instaladas.

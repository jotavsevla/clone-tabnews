# Clone TabNews — laboratório full-stack

Projeto de estudo inspirado no fluxo do [curso.dev](https://curso.dev), usado para praticar integração incremental de frontend, backend, banco de dados, testes e infraestrutura.

## Estado

**Scaffold inicial.** A branch principal auditada contém uma página Next.js simples e arquivos reservados para banco, conteúdo, usuário e senha. Os módulos de domínio ainda estão vazios. A evolução local com `GET /api/v1/status` e seu primeiro teste foi publicada separadamente no [PR #14](https://github.com/jotavsevla/clone-tabnews/pull/14).

O README descreve somente o que está verificável no código atual; “clone do TabNews” é a direção do estudo, não uma funcionalidade pronta.

## Stack atual

- Node.js LTS Hydrogen (`.nvmrc`);
- Next.js 13 e React 18;
- Jest configurado como dependência;
- Prettier.

## Estrutura

```text
clone-tabnews/
├── pages/index.js       # única interface implementada
├── infra/database.js    # placeholder vazio
├── models/content.js    # placeholder vazio
├── models/password.js   # placeholder vazio
├── models/user.js       # placeholder vazio
└── package.json
```

## Executar

```bash
nvm use
npm install
npm run dev
```

Acesse `http://localhost:3000`.

## Auditoria técnica

- a auditoria encontrou uma chave `test` duplicada no `package.json`; o [PR #14](https://github.com/jotavsevla/clone-tabnews/pull/14) remove a duplicidade;
- o mesmo PR adiciona o primeiro teste de integração, que pressupõe um servidor em `localhost:3000`;
- não há script `build` no `package.json`; `npx next build` foi executado diretamente e concluiu com sucesso na auditoria.
- não há alocação manual nem estrutura dinâmica própria. A memória é gerenciada pelo runtime, mas futuras conexões de banco precisarão de pool singleton e encerramento/liberação explícitos.
- não há `.env.example`, migration, schema, validação de entrada ou política de autenticação implementados.
- Next.js 13 e Node 18 são escolhas históricas; uma atualização de dependências deve ser feita como tarefa separada, com build e testes, e não apenas por alteração de versão.

## Roadmap sugerido

1. mesclar e evoluir o endpoint/teste do PR #14;
2. adicionar CI que suba o servidor antes dos testes de integração;
3. definir banco, migrations e variáveis de ambiente;
4. implementar modelos com contratos e validação;
5. criar API de status antes dos recursos de conteúdo/usuário;
6. documentar decisões e diferenças em relação ao TabNews original.

## Relação com o portfólio

Este repositório é um laboratório de aprendizado e não está entre os cases principais do [portfólio](https://portfolio.jvapa.com.br/). Ele pode ser promovido quando houver domínio, testes e infraestrutura verificáveis.

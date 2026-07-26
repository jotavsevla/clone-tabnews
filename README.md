# Clone TabNews — laboratório full-stack

Projeto de estudo inspirado no fluxo do [curso.dev](https://curso.dev), usado para praticar integração incremental de frontend, backend, banco de dados, testes e infraestrutura.

## Estado

**Scaffold inicial.** A branch principal contém uma página Next.js simples e arquivos reservados para banco, conteúdo, usuário e senha. Os módulos de domínio ainda estão vazios, não existe API implementada e não há testes versionados.

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

- `package.json` declara a chave `test` duas vezes. JSON aceita apenas um valor efetivo; o último (`jest`) sobrescreve silenciosamente o script de erro criado pelo `npm init`.
- `npm test` encontra zero testes e termina com erro. Crie o primeiro teste antes de considerar CI funcional.
- não há script `build` no `package.json`; `npx next build` foi executado diretamente e concluiu com sucesso na auditoria.
- não há alocação manual nem estrutura dinâmica própria. A memória é gerenciada pelo runtime, mas futuras conexões de banco precisarão de pool singleton e encerramento/liberação explícitos.
- não há `.env.example`, migration, schema, validação de entrada ou política de autenticação implementados.
- Next.js 13 e Node 18 são escolhas históricas; uma atualização de dependências deve ser feita como tarefa separada, com build e testes, e não apenas por alteração de versão.

## Roadmap sugerido

1. remover a chave duplicada de `scripts`;
2. adicionar teste mínimo e CI;
3. definir banco, migrations e variáveis de ambiente;
4. implementar modelos com contratos e validação;
5. criar API de status antes dos recursos de conteúdo/usuário;
6. documentar decisões e diferenças em relação ao TabNews original.

## Relação com o portfólio

Este repositório é um laboratório de aprendizado e não está entre os cases principais do [portfólio](https://portfolio.jvapa.com.br/). Ele pode ser promovido quando houver domínio, testes e infraestrutura verificáveis.

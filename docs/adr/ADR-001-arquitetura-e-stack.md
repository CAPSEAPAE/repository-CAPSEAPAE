# ADR-001 — Adoção da arquitetura e stack do repositório Connexa

- **Situação:** aceita
- **Data:** 2026-11-15
- **Participantes:** Gustavo Barone, Gustavo Pereira, David Perrota, Arthur Alberto e Gustavo Pimentel

## Contexto

Para iniciar a Sprint 1, a equipe precisa definir a arquitetura, a stack e os processos de desenvolvimento que serão usados na aplicação Connexa. O repositório já fornece uma estrutura funcional alinhada às necessidades do projeto e às orientações da disciplina. A equipe decidiu manter essa base, sem introduzir alterações de arquitetura, ferramentas ou processos.

## Decisão

Adotamos a arquitetura, a stack e os processos descritos no `README.md` do repositório. O back-end será um monólito modular organizado em fatias verticais, e o front-end será uma SPA. Manteremos as ferramentas e os fluxos de desenvolvimento já configurados, sem adicionar ou substituir dependências.

| Área | Adoção |
|---|---|
| Back-end | Java 21, Spring Boot 4.1, Spring Modulith 2.1, Spring Data JPA, Flyway e springdoc-openapi |
| Banco de dados | PostgreSQL 17, com schema próprio por módulo |
| Front-end | React 19, TypeScript, Vite, React Router, TanStack Query, React Hook Form e Zod |
| Testes | JUnit 5 e MockMvc no back-end; Vitest e Testing Library no front-end; verificações de fronteiras entre módulos |
| Integração e ambiente | GitHub Actions, GitHub Codespaces ou ambiente local com Docker Compose |
| Processo | Tasks do Azure Boards como especificação; implementação por fatias verticais; pull requests vinculados aos work items; validação pelo comando `./verificar` e CI |

As fronteiras entre módulos, os schemas, os contratos da API e as convenções do front-end continuarão seguindo as regras documentadas no `README.md` e em `AGENTS.md`.

## Alternativas consideradas

| Alternativa | Por que não foi escolhida |
|---|---|
| Alterar ou substituir agora a arquitetura, a stack ou os processos do repositório | A equipe não identificou uma necessidade que justifique divergir da base fornecida. A alteração acrescentaria trabalho e risco antes do início das funcionalidades da Sprint 1. |
| Separar o back-end em microsserviços | O monólito modular já atende à organização por módulos e mantém a implantação mais simples para o escopo do projeto. |
| Substituir a SPA e as ferramentas de front-end configuradas | O React e as ferramentas existentes atendem à interface prevista e já estão integrados à verificação do projeto. |

## Consequências

- **Positivas:** a equipe inicia a Sprint 1 sobre uma base pronta e consistente; preserva a integração entre back-end, front-end, testes, CI e Azure Boards; evita dependências e configurações adicionais.
- **Negativas:** a equipe mantém as convenções e limitações da arquitetura e das ferramentas escolhidas no modelo. Mudanças futuras de stack ou de fronteiras poderão exigir migração e deverão ser registradas em novos ADRs.
- **Como verificar:** executar `./verificar`; manter verdes os checks de back-end, front-end e sincronização das instruções no CI; preservar as verificações de fronteiras dos módulos, schemas do banco e fronteiras entre features.

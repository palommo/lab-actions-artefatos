# lab-actions-artefatos

Desafio prático de GitHub Actions: controle de fluxos (triggers) e sobrevivência de arquivos (artefatos).

## Estrutura

```
/src
  /codigo/script.js
  /docs/manual.md
/testes
  suite.test.js
/.github/workflows/pipeline-inteligente.yml
```

## Workflow

O workflow `pipeline-inteligente.yml` é disparado por:

- **Manual**: botão `workflow_dispatch` na aba Actions.
- **Agendado**: todo dia às 02:00 (cron `0 2 * * *`).
- **Push**: apenas em branches `feature/**`, monitorando `src/**` mas ignorando `src/docs/**`.

### Jobs

1. `job_gerador` — gera `saida_build/relatorio1.txt` e `relatorio2.txt` e faz upload como artefato `meus-relatorios-oficiais`.
2. `job_auditoria` — depende do `job_gerador`, baixa o artefato e exibe seu conteúdo.

<!-- Teste 1: push em main não deve disparar workflow -->

# Dossiê do Incidente #INC-2026-01 (Sistema de Matrículas)

## Contexto
Às **19h10** de ontem, o time de desenvolvimento subiu a versão `v2.3.0` adicionando um campo opcional `"nome_social"` no cadastro de alunos.

## Linha do Tempo Bruta (Logs & Chamados)
- **19:10** — Deploy da `v2.3.0` concluído em produção (sem rodar testes de integração no banco).
- **19:14** — Primeiro chamado no WhatsApp do suporte: *"Tentei matricular um aluno novo e deu Erro Interno 500!"*
- **19:18** — 14 novos chamados idênticos no Help Desk. Secretaria acadêmica parada.
- **19:22** — Log do servidor mostra: `SQLITE_ERROR: table alunos has no column named nome_social`.
- **19:25** — Dev de plantão percebe que esqueceu de rodar a *migration* do banco de dados em produção antes do deploy do código.
- **19:32** — Migration aplicada manualmente em produção.
- **19:35** — Sistema volta ao normal. Total de **25 minutos** fora do ar para novas matrículas (aprox. 42 matrículas impactadas).

## Missão do Squad
1. Redigir **1 comunicado para a Diretoria/Secretaria** (linguagem acessível, impacto, solução e próxima etapa).
2. Redigir **1 comunicado técnico para o time de Dev**.
3. Preencher o **Blameless Postmortem** usando `template-postmortem.md` e a técnica dos **5 Porquês**.

# Cronograma por valor para o farmacêutico

**Fluxo básico → RAG → validações automatizadas → decisão e documentos → consolidação.**

Início: 13/11/2026. Implementação nominal: 12/02/2027. Entrega: 19/02/2027. Capacidade proposta: quatro HUs por semana.

## Premissas e critérios de liberação

- Prioridade aprovada pelo usuário: fluxo básico primeiro, validações automatizadas em seguida e RAG antecipado para a semana 3.
- Início em 13/11/2026, quatro HUs por semana como hipótese de capacidade. Implementação nominal 12/02/2027 e entrega 19/02/2027. Datas não descontam feriados ou recesso.
- As primeiras semanas entregam fatias integradas das HUs. Introdução não equivale a aceite integral: predecessoras ainda incompletas são registradas na coluna de pendências e no JSON. Não contar a mesma HU novamente ao integrar seus complementos.
- Desde a semana 1 incluir como tarefas das entregas: minimização de dados, persistência protegida, eventos básicos de auditoria, acessibilidade e contratos de identificação. Até conta/permissões e política institucional validadas, demonstrações apenas com dados fictícios; não liberar dados reais por antecipação de fluxo.
- US-047, US-048 e US-049 na semana 11 consolidam gestão, auditoria completa e acessibilidade transversal. Não postergar seus controles mínimos até essa semana. US-045/046 têm fontes e precedência mínimas aprovadas antes de qualquer resposta RAG ou regra clínica.
- US-044 deve implementar RAG com indexação de documentos aprovados, recuperação, resposta com fonte/versão, abstenção sem evidência e testes de fidelidade. Não tratar uma conversa genérica com LLM como cumprimento dessa HU. Respostas consultivas não acionam dispensação ou alteram prescrição.
- Exames continuam opcionais. As regras automatizadas só executam análises sustentadas pelos dados, com limites de cobertura explícitos.
- Recomendação pediátrica encurtada permanece desabilitada até US-015 na semana 12; sua integração condicional com o resumo deve ser testada no aceite.
- A semana 13 tem uma HU e espaço para integrações pendentes; a semana 14 é de estabilização/homologação. A cadência precisa ser validada com esforço real, principalmente no RAG e nas HUs de consolidação.

## Ordem das HUs e deadlines

O acumulado conta HUs introduzidas; não representa aceite integral quando há pendências. A ordem dentro da semana é de execução.

| Semana | Deadline | HUs em ordem | Pendências para aceite integral |
|---|---|---|---|
| 1 | **20/11/2026** | US-002 — Início do atendimento; US-005 — Dados mínimos do paciente; US-003 — Checklist de documentos; US-012 — Revisão da prescrição | US-002: US-001, US-048 |
| 2 | **27/11/2026** | US-006 — Diagnóstico e fase; US-008 — Medicamentos concomitantes; US-004 — Correção de respostas; US-001 — Acesso profissional | US-004: US-048; US-001: US-047 |
| 3 | **04/12/2026** | US-045 — Versões de regras e fontes; US-046 — Precedência de fontes; US-044 — Consulta clínica com fontes; US-019 — Limites de atuação profissional | — |
| 4 | **11/12/2026** | US-013 — Adequação do esquema; US-014 — Dose e apresentação; US-021 — Aprovação das interações; US-020 — Verificação de interações | — |
| 5 | **18/12/2026** | US-007 — Condições especiais; US-023 — Reações adversas; US-022 — Destaque de interações relevantes; US-009 — Barreiras de adesão | — |
| 6 | **25/12/2026** | US-010 — Exames opcionais; US-017 — Avaliação hepática e renal; US-024 — Toxicidade hepática e renal; US-011 — HIV e notificação | — |
| 7 | **01/01/2027** | US-025 — Alergias e fatores de risco; US-016 — Formas especiais e encaminhamento; US-026 — Avaliação da resposta; US-027 — Adesão e interrupções | — |
| 8 | **08/01/2027** | US-032 — Resumo dos PRMs; US-033 — Revisão das condutas; US-034 — Decisão de dispensação; US-035 — Quantidade e cobertura | — |
| 9 | **15/01/2027** | US-041 — Transmissão e contatos; US-037 — Evolução para prontuário; US-038 — Carta ao profissional; US-039 — Orientações personalizadas | — |
| 10 | **22/01/2027** | US-040 — Agenda de medicamentos; US-042 — Aprovação e exportação; US-018 — Acesso e duplicidade terapêutica; US-036 — Comunicações e encaminhamentos | — |
| 11 | **29/01/2027** | US-047 — Privacidade e proteção de dados; US-048 — Auditoria do atendimento; US-049 — Acessibilidade e uso móvel; US-029 — Acompanhamento longitudinal | — |
| 12 | **05/02/2027** | US-030 — Programação dos retornos; US-028 — Registro de TDO; US-043 — Desfecho do tratamento; US-015 — Regime pediátrico encurtado | — |
| 13 | **12/02/2027** | US-031 — Projeto Terapêutico Singular | — |
| 14 | **19/02/2027** | Estabilização e homologação | — |

## Marcos

- **20/11/2026 — Fluxo básico utilizável em demonstração:** Abrir atendimento, dados mínimos, checklist e prescrição; dados fictícios e decisão manual.
- **04/12/2026 — RAG com fontes:** Consulta documental recuperada e citada, com abstenção e limites explícitos.
- **11/12/2026 — Validações de esquema, dose e interações:** Ferramentas determinísticas aprovadas como apoio ao farmacêutico.
- **08/01/2027 — Condutas e dispensação:** Resumo dos PRMs, confirmação profissional e cobertura.
- **22/01/2027 — Documentos e exportação:** Evolução, carta, orientações e agenda revisadas antes de exportar.
- **29/01/2027 — Consolidação transversal:** Revisão de privacidade, auditoria e acessibilidade; decisão de liberação institucional.
- **19/02/2027 — Entrega:** Estabilização, regressão e homologação.

## Relação com o planejamento anterior

Este documento substitui a ordem do cronograma anterior. O grafo de dependências integrais continua como referência de aceite; não foi alterado artificialmente para afirmar que protótipos cumprem histórias completas. O cronograma antecipa capacidades através de contratos e controles mínimos incorporados ao trabalho semanal. Revalidar os aceites de US-001, US-002, US-004 e US-045 após completar suas predecessoras; integração e testes fazem parte das entregas, sem criar novas HUs contabilizadas.

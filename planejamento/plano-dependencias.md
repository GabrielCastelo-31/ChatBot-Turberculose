> Ordem vigente por valor: consulte `cronograma-semanal.md`. As semanas indicam introdução de capacidades; as setas do grafo representam dependências para aceite integral.

# Dependências e ordem de implementação do chatbot de tuberculose

Proposta de planejamento inferida dos critérios; dependências não foram declaradas formalmente pelo cliente. Validar no refinamento.

Base: versão 0.2 dos requisitos. Os 49 IDs e suas prioridades MoSCoW foram mantidos. A semana indica a introdução proposta no cronograma, não o aceite integral nem uma estimativa de esforço.

## Como interpretar o grafo

- Necessária: capacidade predecessora para integrar a funcionalidade descrita. Para planejar a conclusão, usar as predecessoras da matriz. Contratos de interface permitem desenvolvimento em paralelo; uma seta não proíbe começar código ou testes antes.
- Condicional: torna-se obrigatória quando o perfil correspondente é habilitado. US-015 → US-032 se o produto incluir recomendação pediátrica encurtada. Antecipar toda a fatia pediátrica nesse caso.
- Complementar: integra informação adicional; não deve ser cadastrada como bloqueio no cronograma.
- Transversal: US-047, US-048 e US-049 começam com a primeira entrega e são ampliadas e verificadas a cada funcionalidade. Não esperar um grande módulo de segurança, auditoria ou acessibilidade terminar para começar tudo, nem declarar essas histórias definitivamente concluídas na primeira entrega.
- O grafo visual reduz relações transitivas para evitar excesso de setas. A matriz CSV preserva todas as predecessoras explicitadas. Complementos estão na matriz e no explorador, fora do grafo principal para não criar ciclos falsos.
- Implementar a interface de exames (US-010) não exige obter resultados reais nem construir integração laboratorial. Nenhuma etapa depende de exame efetivamente disponível.

## Ordem atual e primeira fatia

A ordem por valor, os marcos e as pendências estão em `cronograma-semanal.md`. A primeira demonstração reúne abertura de atendimento, dados mínimos, checklist e prescrição, com dados fictícios e decisão manual. RAG é introduzido na semana 3, seguido das validações de esquema, dose e interações. A geração e a aprovação completas de documentos seguem as semanas 9 e 10; não há fatias US-037a/US-042a adicionais contabilizadas antecipadamente.

Privacidade, auditoria e acessibilidade têm controles mínimos desde a primeira fatia e consolidação posterior. A introdução antecipada de uma HU não remove as dependências necessárias ao seu aceite integral. Para as pendências por HU e os critérios de liberação, consulte o cronograma.

## Matriz completa dos requisitos

IDs nas colunas de predecessoras são US-xxx. Nível topológico é somente a distância máxima em dependências necessárias, sem considerar durações; não é caminho crítico.

| ID | Requisito | MoSCoW | Semana de introdução | Necessárias | Condicionais | Complementares |
|---|---|---|---|---|---|---|
| US-047 | Privacidade e proteção de dados | Must | 11 | — | — | — |
| US-049 | Acessibilidade e uso móvel | Should | 11 | — | — | — |
| US-001 | Acesso profissional | Must | 2 | US-047 | — | — |
| US-048 | Auditoria do atendimento | Must | 11 | US-001 | — | US-045 |
| US-002 | Início do atendimento | Must | 1 | US-001, US-048 | — | — |
| US-003 | Checklist de documentos | Must | 1 | US-002 | — | — |
| US-004 | Correção de respostas | Must | 2 | US-002, US-048 | — | — |
| US-005 | Dados mínimos do paciente | Must | 1 | US-002 | — | — |
| US-006 | Diagnóstico e fase | Must | 2 | US-005 | — | — |
| US-007 | Condições especiais | Must | 5 | US-005 | — | — |
| US-008 | Medicamentos concomitantes | Must | 2 | US-005 | — | — |
| US-009 | Barreiras de adesão | Must | 5 | US-005 | — | — |
| US-012 | Revisão da prescrição | Must | 1 | US-003, US-005 | — | — |
| US-045 | Versões de regras e fontes | Must | 3 | US-001 | — | — |
| US-046 | Precedência de fontes | Must | 3 | US-045 | — | — |
| US-019 | Limites de atuação profissional | Must | 3 | US-002, US-046 | — | — |
| US-021 | Aprovação das interações | Must | 4 | US-045, US-046 | — | — |
| US-010 | Exames opcionais | Must | 6 | US-006 | — | — |
| US-011 | HIV e notificação | Should | 6 | US-006 | — | US-010 |
| US-013 | Adequação do esquema | Must | 4 | US-006, US-012, US-046 | — | US-015 |
| US-014 | Dose e apresentação | Must | 4 | US-006, US-012, US-046 | — | — |
| US-016 | Formas especiais e encaminhamento | Must | 7 | US-006, US-007, US-046 | — | US-026, US-027 |
| US-020 | Verificação de interações | Must | 4 | US-008, US-012, US-021 | — | — |
| US-023 | Reações adversas | Must | 5 | US-007, US-012, US-046 | — | — |
| US-025 | Alergias e fatores de risco | Must | 7 | US-007, US-008, US-012, US-046 | — | — |
| US-041 | Transmissão e contatos | Must | 9 | US-006, US-046 | — | — |
| US-017 | Avaliação hepática e renal | Must | 6 | US-007, US-010, US-012, US-046 | — | — |
| US-022 | Destaque de interações relevantes | Must | 5 | US-020 | — | — |
| US-040 | Agenda de medicamentos | Must | 10 | US-008, US-012, US-020 | — | — |
| US-024 | Toxicidade hepática e renal | Must | 6 | US-017, US-023 | — | — |
| US-018 | Acesso e duplicidade terapêutica | Should | 10 | US-008, US-012 | — | — |
| US-027 | Adesão e interrupções | Must | 7 | US-006, US-012, US-046 | — | US-009, US-028 |
| US-026 | Avaliação da resposta | Must | 7 | US-006, US-010, US-046 | — | US-029 |
| US-032 | Resumo dos PRMs | Must | 8 | US-013, US-014, US-016, US-017, US-019, US-020, US-022, US-023, US-024, US-025, US-026, US-027 | US-015 | US-018, US-029 |
| US-033 | Revisão das condutas | Must | 8 | US-019, US-032 | — | — |
| US-034 | Decisão de dispensação | Must | 8 | US-033 | — | — |
| US-036 | Comunicações e encaminhamentos | Should | 10 | US-033 | — | — |
| US-038 | Carta ao profissional | Must | 9 | US-033 | — | US-036 |
| US-039 | Orientações personalizadas | Must | 9 | US-009, US-023, US-027, US-033 | — | US-030 |
| US-035 | Quantidade e cobertura | Must | 8 | US-012, US-034 | — | — |
| US-037 | Evolução para prontuário | Must | 9 | US-034, US-035 | — | US-029, US-036, US-043 |
| US-042 | Aprovação e exportação | Must | 10 | US-037, US-038, US-039, US-040, US-041 | — | — |
| US-028 | Registro de TDO | Should | 12 | US-005, US-006 | — | US-027 |
| US-029 | Acompanhamento longitudinal | Must | 11 | US-010, US-023, US-026, US-027 | — | US-028 |
| US-043 | Desfecho do tratamento | Must | 12 | US-026, US-027, US-029, US-046 | — | US-028, US-042 |
| US-030 | Programação dos retornos | Should | 12 | US-006, US-035 | — | — |
| US-044 | Consulta clínica com fontes | Should | 3 | US-045, US-046 | — | — |
| US-031 | Projeto Terapêutico Singular | Could | 13 | US-009 | — | US-029, US-036 |
| US-015 | Regime pediátrico encurtado | Must | 12 | US-006, US-007, US-010, US-046 | — | — |

## Justificativas das dependências

- **US-001 — Acesso profissional:** Usa a política de dados e as permissões definidas em US-047.
- **US-002 — Início do atendimento:** Precisa identificar o profissional e registrar os eventos básicos do atendimento.
- **US-003 — Checklist de documentos:** O checklist pertence ao atendimento aberto.
- **US-004 — Correção de respostas:** Precisa do registro de respostas e da trilha de alterações; cada módulo futuro deve implementar recálculo e invalidação de resultados.
- **US-005 — Dados mínimos do paciente:** Vincula os dados mínimos e o identificador ao atendimento.
- **US-006 — Diagnóstico e fase:** Vincula diagnóstico, tipo de cuidado e fase ao paciente/atendimento.
- **US-007 — Condições especiais:** Vincula condições clínicas ao paciente.
- **US-008 — Medicamentos concomitantes:** Vincula a lista concomitante ao paciente.
- **US-009 — Barreiras de adesão:** Vincula barreiras e vulnerabilidades ao paciente.
- **US-010 — Exames opcionais:** Classifica o exame conforme o contexto do tratamento e aceita estados sem resultado.
- **US-011 — HIV e notificação:** Diferencia TB/ILTB e registra situação conhecida; resultado laboratorial é complemento opcional.
- **US-012 — Revisão da prescrição:** Relaciona prescrição, identificação do atendimento e pendências documentais; ausência de documento não bloqueia a avaliação.
- **US-013 — Adequação do esquema:** Cruza diagnóstico/fase e prescrição com regras aprovadas; o perfil pediátrico encurtado é ampliado por US-015.
- **US-014 — Dose e apresentação:** Usa idade/peso já disponíveis por US-005 e os dados da prescrição; pode ser desenvolvido em paralelo a US-013.
- **US-015 — Regime pediátrico encurtado:** Usa contexto, condições especiais e estados de disponibilidade dos exames; critérios clínicos aplicáveis devem ser aprovados para cada cenário.
- **US-016 — Formas especiais e encaminhamento:** Reconhece formas e riscos com dados clínicos e regra aprovada; sinais posteriores de falha enriquecem a detecção.
- **US-017 — Avaliação hepática e renal:** Usa condições, prescrição e interface de exames, inclusive o estado indisponível; não depende de resultado real.
- **US-018 — Acesso e duplicidade terapêutica:** Compara prescrição, tratamentos concomitantes e disponibilidade informada.
- **US-019 — Limites de atuação profissional:** Aplica a distinção TB/TPT com regra institucional aprovada.
- **US-020 — Verificação de interações:** Necessita dos dois lados da comparação e de uma base de interações aprovada.
- **US-021 — Aprovação das interações:** Publica conteúdo de interações com versão e precedência de fontes.
- **US-022 — Destaque de interações relevantes:** Classifica e destaca as interações detectadas em US-020.
- **US-023 — Reações adversas:** Relaciona sintomas e condições aos medicamentos e ao manejo aprovado.
- **US-024 — Toxicidade hepática e renal:** Combina parâmetros/limitações da avaliação hepatorrenal com sintomas e reações; preserva alertas sem exames.
- **US-025 — Alergias e fatores de risco:** Cruza condições e tratamentos para individualizar os riscos.
- **US-026 — Avaliação da resposta:** Usa contexto e evidências disponíveis, inclusive ausência de exames; histórico longitudinal pode ser integrado depois.
- **US-027 — Adesão e interrupções:** Aplica critérios de adesão/interrupção ao esquema; barreiras e doses observadas enriquecem a análise.
- **US-028 — Registro de TDO:** Relaciona tomadas observadas ao tratamento; exames não são predecessores. Modalidade digital depende de aprovação própria.
- **US-029 — Acompanhamento longitudinal:** Compara dados seriados de sintomas, adesão e resposta, aceitando ausência de exames. Periodicidade mensal deve ser validada, pois foi retirada indevidamente na revisão anterior.
- **US-030 — Programação dos retornos:** Combina fase/duração do esquema com a cobertura calculada da dispensação.
- **US-031 — Projeto Terapêutico Singular:** Estrutura metas e responsabilidades a partir das necessidades identificadas; histórico e comunicações podem ser associados depois.
- **US-032 — Resumo dos PRMs:** Consolida as análises de indicação, efetividade, segurança e adesão habilitadas. A integração de US-015 é obrigatória se o escopo incluir recomendação pediátrica encurtada.
- **US-033 — Revisão das condutas:** Associa e confirma condutas aos PRMs sem ultrapassar os limites de atuação.
- **US-034 — Decisão de dispensação:** Registra decisão e justificativa após revisão das avaliações e condutas.
- **US-035 — Quantidade e cobertura:** Calcula cobertura a partir da posologia e da decisão de dispensar.
- **US-036 — Comunicações e encaminhamentos:** Relaciona comunicação e resolução a PRM/conduta. Não exige carta gerada para registrar contato manual.
- **US-037 — Evolução para prontuário:** A versão integral incorpora avaliação, decisão, quantidade quando houve dispensação e retorno; a introdução está na semana 9.
- **US-038 — Carta ao profissional:** Gera carta a partir do achado/conduta confirmada; pode ser desenvolvida em paralelo ao registro de comunicações.
- **US-039 — Orientações personalizadas:** Usa esquema, riscos e barreiras já disponíveis e a decisão de conduta; data de retorno pode ser informada manualmente até US-030.
- **US-040 — Agenda de medicamentos:** Usa posologia, concomitantes e interações para apresentar horários e separações pertinentes.
- **US-041 — Transmissão e contatos:** Seleciona conteúdo aprovado conforme tipo de TB e situação do tratamento.
- **US-042 — Aprovação e exportação:** A versão integral revisa os tipos de documentos disponíveis; a introdução está na semana 10.
- **US-043 — Desfecho do tratamento:** Usa evolução, doses e regras de desfecho; ausência de exames não comprova cura nem bloqueia o registro do atendimento.
- **US-044 — Consulta clínica com fontes:** Consulta apenas fontes governadas, com incerteza explícita e separação das regras decisórias.
- **US-045 — Versões de regras e fontes:** Publicação e revisão precisam de perfil autorizado; registrar fonte de modelos documentais desde a primeira fatia.
- **US-046 — Precedência de fontes:** Resolve conflitos entre fontes versionadas antes de habilitar as regras clínicas afetadas.
- **US-047 — Privacidade e proteção de dados:** Capacidade transversal: decisões institucionais e controles mínimos desde o primeiro fluxo; ampliar por finalidade e integração.
- **US-048 — Auditoria do atendimento:** Infraestrutura de eventos começa com autenticação; instrumentação clínica e versões são ampliadas em cada entrega.
- **US-049 — Acessibilidade e uso móvel:** Critério transversal da definição de pronto desde a primeira tela; validar novamente a cada incremento.

## Marcos externos de liberação

- **G-DADOS — Política de dados aprovada:** Bloqueia uso com dados reais; desenvolvimento e demonstração com dados fictícios podem continuar.
- **G-CLINICA — Escopo e conteúdo clínico aprovados:** Bloqueia ativação de cada regra clínica não revisada; não exige laboratório nem matriz inteira para desenvolver.
- **G-TDO — Modalidade digital aprovada:** Somente captura/modalidade digital da US-028; manter alternativa sem gravação.

## Aplicação de Scrum e XP

Proposta de Meta do Produto: apoiar o farmacêutico a registrar, revisar e documentar o atendimento de TB com rastreabilidade, preservando a decisão profissional.

1. O Product Owner confirma o público da primeira liberação e ordena o Product Backlog por valor observado, riscos e dependências. Atrasar US-015 só é aceitável se o regime pediátrico encurtado estiver fora do escopo inicial acordado; Must continua Must no escopo alvo.
2. No refinamento, dividir histórias grandes em fatias verticais com critérios BDD verificáveis. US-032/US-037/US-042 e histórias transversais não cabem automaticamente em uma sprint só.
3. Na Sprint Planning, selecionar uma Meta da Sprint e trabalho compatível com a capacidade real. A semana de introdução não define esforço nem compromisso de sprint. Não contar pais e suas fatias duas vezes nas estimativas.
4. Na Sprint Review, demonstrar atendimento funcionando com farmacêutico/cliente, inspecionar feedback e reordenar o backlog. Revisão não substitui homologação institucional ou validação clínica. Na retrospectiva, ajustar práticas da equipe.
5. Aplicar XP: exemplos clínicos/BDD discutidos com farmacêuticos; TDD para regras e transições críticas; testes de integração de persistência e exportação; integração contínua; refatoração protegida por testes; programação em pares ou revisão de código nas regras de maior risco.
6. Definição de Pronto por fatia: critérios aprovados passam, alterações recalculam/inutilizam resultados dependentes, estado sem exame é testado, acesso e auditoria funcionam, fonte/versão é rastreável quando houver regra clínica, interface móvel e teclado são utilizáveis, exportação reflete somente dados e decisões confirmadas. Controles e validação correspondem ao escopo efetivamente liberado.

## Conversão para cronograma

Importar dependencias-requisitos.csv; expandir as capacidades da primeira entrega em tarefas ou histórias menores; estimar esforço com a equipe e definir responsáveis. Usar somente predecessoras necessárias como relações de bloqueio; adicionar condicionais se o perfil pediátrico for habilitado. Manter complementares como oportunidades de integração. Reservar capacidade para testes, revisão clínica, privacidade e feedback. Com capacidade, durações e calendário definidos, calcular datas, folgas e caminho crítico. O nível topológico fornecido não substitui esse cálculo.

Exemplos de paralelismo após suas entradas: US-003/US-005; US-007/US-008/US-009; US-013/US-014/US-016/US-017; US-020/US-023/US-025; US-026/US-027; US-036/US-038; US-028/US-030; US-015/US-031/US-044 quando suas predecessoras estiverem disponíveis.

## Pendências para o refinamento

- Confirmar o escopo clínico inicial e a decisão de antecipar ou postergar a trilha pediátrica.
- Aprovar os critérios das fatias documentais antecipadas; não alterar silenciosamente os requisitos originais.
- Confirmar a periodicidade mensal em US-029: a retirada anterior foi além do pedido do cliente. Este planejamento não altera o DOCX.
- Completar rastreabilidade clínica e aprovar a cobertura inicial da matriz de interações, que está em construção.
- A seleção da arquitetura pode eliminar ou acrescentar dependências técnicas; validar esta proposta com o time antes de fixar datas.

## Referências de método

- Scrum Guide 2020: https://scrumguides.org/scrum-guide.html
- Agile Alliance — Extreme Programming: https://agilealliance.org/glossary/xp/
- Princípios do Manifesto Ágil: https://agilemanifesto.org/iso/ptbr/principles.html

Os métodos fundamentam a entrega incremental e as práticas de qualidade. As dependências e a ordem deste documento são uma análise proposta para este produto, não regras prescritas por Scrum ou XP.

# Instruções para implementação do chatbot de tuberculose

## Produto e escopo

Este projeto implementa um assistente de apoio ao cuidado farmacêutico em tuberculose ativa e infecção latente por tuberculose (ILTB/TPT). O usuário principal é o farmacêutico. O produto deve apoiar atendimento estruturado, revisão da prescrição, identificação de riscos e problemas relacionados aos medicamentos (PRMs), consulta documental por RAG e geração de documentos revisados pelo profissional.

A avaliação do sistema subsidia a decisão do farmacêutico. Prescrição, dispensação, encaminhamento e aprovação de documentos dependem de confirmação profissional. Trate uma funcionalidade demonstrada, uma regra testada e uma conduta clinicamente validada como resultados distintos.

## Fontes de autoridade e leitura por tarefa

Antes de implementar uma HU, leia a história, seus critérios de aceitação e as regras transversais em `Requisitos_Chatbot_Tuberculose_v0.2_revisado.md`. Preserve os IDs US-001 a US-049 para rastreabilidade. O DOCX de mesmo radical é a origem da conversão Markdown; consulte-o se houver dúvida de transcrição. Mantenha ambos coerentes ao alterar requisitos por solicitação do usuário.

- **Seleção e ordem de trabalho:** leia `planejamento/cronograma-semanal.md`. Sua ordem por valor substitui a sequência antiga de entregas. `planejamento/cronograma-semanal.json` contém a distribuição e as pendências por HU; CSV e SVG são representações do cronograma.
- **Dependências e integração:** consulte `planejamento/dependencias-requisitos.json` e as justificativas em `planejamento/plano-dependencias.md`. O grafo representa dependências para o aceite integral. O cronograma permite antecipar fatias com pendências explícitas; antecipação não remove a dependência.
- **Regra clínica, dose, interação, orientação ou desfecho:** leia a seção pertinente dos materiais em `Materiais_Tecnicos_tuberculose/` e registre a fonte e a versão usadas. A planilha de interações está em construção: uma entrada disponível não equivale a conteúdo aprovado.
- **Fluxo e documentos assistenciais:** consulte também `Materiais_Tecnicos_tuberculose/Etapas para o Assistente de Dispensação- atualizando.docx` e o protocolo de cuidado farmacêutico dessa pasta.

Em divergência, aplique as instruções atuais do usuário ao planejamento e registre o impacto. Conflitos clínicos exigem precedência de fontes aprovada, conforme US-045/US-046; evite escolher silenciosamente uma conduta. Preserve os documentos originais e sinalize pendências de validação.

## Prioridade de implementação

Entregue primeiro uma fatia de ponta a ponta do atendimento básico: abrir atendimento, vincular dados mínimos, verificar documentação e registrar/revisar a prescrição. Amplie esse fluxo com correção de respostas, diagnóstico/fase e medicamentos concomitantes.

Antecipe o RAG e as ferramentas automatizadas de validação e apoio ao farmacêutico conforme o cronograma. Priorize software utilizável e feedback do profissional. Evite usar a conclusão de módulos administrativos completos como bloqueio artificial para demonstrar o fluxo com dados fictícios.

Inclua controles mínimos de privacidade, identificação, auditoria e acessibilidade desde a primeira fatia. As HUs de consolidação transversal posteriores ampliam esses controles; não autorizam adiá-los. O uso com dados reais depende de contas, permissões, política de dados e aprovações institucionais aplicáveis.

Use a cadência do cronograma como previsão de capacidade, não como justificativa para reduzir testes ou declarar uma HU pronta antes do aceite. Ao dividir uma história, explicite os critérios de cada fatia e as pendências do requisito original; conte o trabalho sem duplicar pai e fatias.

## Fluxo clínico e dados ausentes

- Resultados laboratoriais são opcionais no registro. Suporte os estados definidos em RT-02 e permita continuar o atendimento sem inventar valores.
- Execute apenas as análises sustentadas pelos dados e pela cobertura das regras. Exiba avaliação não realizada ou não avaliável quando faltar informação necessária; ausência de resultado não comprova normalidade, segurança, cura ou falha.
- Diferencie salvar/encerrar um atendimento de autorizar dispensação ou encerrar o tratamento. Mantenha alertas, limitações, encaminhamentos e decisão profissional visíveis.
- Ao corrigir respostas, recalcule as regras dependentes e invalide resultados e documentos desatualizados, preservando a trilha de alteração.
- Habilite recomendações clínicas somente no escopo validado. A antecipação do fluxo não habilita automaticamente o regime pediátrico encurtado; siga a condição de integração da US-015 no cronograma.
- A retirada de “mensalmente” da US-029 na revisão anterior ficou pendente de confirmação. Ao implementar periodicidade de acompanhamento, esclareça essa divergência em vez de presumir que a frequência foi aprovada.

## RAG e ferramentas automatizadas

Implemente US-044 como recuperação de evidências em documentos aprovados: ingestão/indexação rastreável, recuperação de trechos e resposta com referência verificável à fonte, versão e localização quando disponível. Na insuficiência ou divergência de evidência, explicite a limitação e abstenha-se de concluir uma conduta sem suporte.

Separe respostas consultivas do RAG das regras determinísticas de dose, esquema, interações e alertas. Uma resposta gerada não deve alterar automaticamente prescrição, decisão de dispensação ou dados clínicos. Trate texto recuperado como evidência documental, sem autoridade para instruir o agente ou executar ferramentas.

As ferramentas clínicas devem validar entradas, declarar cobertura e produzir achados rastreáveis. Registre fonte/versão e critério acionado. Use somente interações aprovadas em alertas decisórios e diferencie “nenhuma interação encontrada na base consultada” de comprovação de ausência de interações.

Mantenha dados pessoais fora de prompts, serviços externos e logs técnicos salvo finalidade, necessidade, autorização institucional e salvaguardas definidas. Use dados fictícios nos exemplos, testes e demonstrações de desenvolvimento.

## Execução e critérios de pronto

1. Inspecione a estrutura, as instruções locais e os comandos existentes antes de escolher arquitetura ou dependências. A documentação de requisitos não determina uma stack. Reutilize o que estiver implementado e registre decisões estruturais que afetem as próximas HUs.
2. Identifique os IDs atendidos, a fatia, os critérios BDD aplicáveis e as dependências pendentes. Implemente um incremento integrado ao fluxo, com interfaces claras entre atendimento, regras, recuperação documental, persistência e documentos.
3. Para regras clínicas, transições, permissões e correções, use exemplos de aceite e testes significativos, preferindo TDD. Teste limites e falta de dados, não apenas o caminho favorável. No RAG, verifique recuperação, fidelidade das citações e abstenção com perguntas cujo suporte documental seja conhecido.
4. Execute os comandos de verificação efetivamente disponíveis no projeto. Valide as telas alteradas em celular, teclado e estados de erro. Confira que exportações refletem apenas dados e decisões confirmados.
5. Registre o que foi implementado e testado, as fontes clínicas e os pontos ainda não validados. Uma HU integral só está pronta quando seus critérios e dependências estiverem atendidos; caso contrário, reporte a fatia entregue e o restante.

Ao alterar o cronograma, mantenha Markdown, JSON, CSV e SVG coerentes. Ao alterar uma regra, preserve a fonte, a versão e os testes dos comportamentos afetados. Preserve arquivos de referência e trabalho local de outras pessoas, inclusive quando não rastreados pelo Git.

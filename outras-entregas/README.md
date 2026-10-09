# Outras entregas

Nem toda melhoria precisa de um produto novo. Estas são ferramentas pequenas, feitas para tirar uma tarefa repetitiva do dia de alguém da operação.

| Ferramenta | Área | Como era | Como ficou |
|---|---|---|---|
| **Tradutor de espelho** | Devolução de mercadorias | Os dados do espelho e da pré-DANFE do fornecedor eram redigitados para montar a devolução | O documento é convertido para o formato do processo interno, sem redigitação |
| **Separação de pisos entre filiais** | Logística e lojas | A lista de separação era montada à mão, consultando produto, fornecedor e endereço de cada código | A pessoa informa código e quantidade; a ferramenta cruza com a base da loja de origem e gera a lista pronta para imprimir |

## Tradutor de espelho

- **Problema:** cada fornecedor manda o espelho em um formato, e a devolução exige os dados no padrão da empresa.
- **Decisão:** resolver só a conversão, sem tentar automatizar a devolução inteira. É a etapa que mais consumia tempo e a de menor risco.
- **Resultado:** fim da redigitação e dos erros que vinham com ela.

## Separação de pisos entre filiais

- **Problema:** separar pisos para outra loja exigia localizar cada item no estoque da loja de origem.
- **Decisão:** a base muda conforme a loja de origem selecionada, porque o endereço do mesmo produto é diferente em cada uma.
- **Resultado:** lista com produto, fornecedor e endereço de cada item, pronta para impressão.
- **Próximo passo:** romaneio geral, que soma várias listas em uma só para a expedição.

## O que estas entregas mostram

Produto interno também é manutenção contínua da operação: ouvir onde o tempo está sendo perdido e resolver com o menor recorte possível.

## Stack

JavaScript · HTML/CSS · Vercel

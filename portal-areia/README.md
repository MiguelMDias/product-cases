# Portal Areia — verificação automática de complemento de nota fiscal

> **Área:** Check-In, Compras e fornecedores · **Meu papel:** produto e desenvolvimento, do levantamento à produção · **Status:** em produção

## Contexto

A areia chega por caminhão, e a quantidade da nota fiscal nem sempre bate com a que foi entregue. Por isso cada carga é medida no recebimento. Quando a medição passa do que está na nota, o fornecedor emite uma **nota complementar** para cobrir a diferença.

## Problema

A conferência entre a nota original e a complementar era feita na mão: alguém abria as duas lado a lado e comparava campo por campo. Os erros que passavam eram sempre os mesmos:

- tipo de areia trocado;
- quantidade diferente da que foi medida;
- complemento apontando para a nota errada;
- fornecedor trocado.

E não havia registro de quem tinha conferido, nem quando.

## Discovery

Acompanhei o processo com quem recebe a carga e com Compras. Três pontos definiram o produto:

1. **O dado já existe no XML da nota.** Ninguém precisava digitar nada; bastava ler o arquivo.
2. **O nome do fornecedor não é confiável.** A mesma empresa aparece escrita de formas diferentes. O CNPJ não muda.
3. **O gargalo era esperar o fornecedor.** Receber o XML do complemento por mensagem e subir no sistema era mais um passo manual.

## Decisões de produto

| Decisão | Por quê |
|---|---|
| Ler o **XML da NF-e** em vez de digitar | Elimina o erro de digitação na origem |
| Identificar fornecedor e loja pelo **CNPJ** | Nome muda de uma nota para outra; CNPJ não |
| **Portal para o fornecedor** subir o próprio XML | Tira um passo manual da equipe e acelera o ciclo |
| O fornecedor **nunca vê a comparação** nem os valores medidos | Ele entrega o documento; quem decide se está certo é a equipe interna |
| Comparação em **cartões visuais** (bate, diverge) | A pessoa enxerga a divergência em um segundo, sem ler campo por campo |
| **Perfis por área:** recebimento cria, Compras só consulta, administrador gerencia | Cada um faz só a parte que é sua |
| **Histórico com autor e data** de cada verificação | Rastreabilidade que o processo manual não tinha |
| **Retirar** a integração de envio automático por mensagem | Foi construída e depois removida: o portal do fornecedor resolveu o mesmo problema com menos complexidade |

## Validações que nasceram do uso real

Os primeiros dias em produção mostraram erros que nenhum levantamento tinha previsto. Cada um virou uma regra:

- **Clique duplo** gerava complemento duplicado → o botão trava após o primeiro clique.
- **Registro sem placa ou sem medição** → os dois campos passaram a ser obrigatórios.
- **Medições discrepantes** davam totais impossíveis → o sistema alerta quando os valores destoam muito entre si ou fogem do padrão de uma carga.
- **Complemento repetido para a mesma nota** → aviso antes de salvar.

## Solução

- **Criar complemento:** cálculo a partir da medição, com os dados da nota original preenchidos pelo XML.
- **Verificar complemento:** fila de pendentes e histórico; quando o fornecedor sobe o XML, a comparação já aparece pronta.
- **Portal do fornecedor:** acesso por empresa, só aos próprios pendentes.
- **Usuários:** criação e controle de acesso por área.

## Resultados

- A conferência deixou de depender de alguém comparar duas notas na tela: acontece assim que o XML é importado.
- Divergências de tipo, quantidade, fornecedor e nota de referência são apontadas automaticamente.
- Toda verificação tem autor e data.

## Aprendizados

- **Remover uma funcionalidade também é decisão de produto.** A integração por mensagem funcionava, mas o portal do fornecedor era mais simples de manter e de explicar.
- **Produção ensina o que o levantamento não mostra.** As validações mais úteis vieram de erros reais dos primeiros usuários.
- **Controle de acesso define o produto.** Decidir o que o fornecedor não vê foi tão importante quanto decidir o que ele faz.

## Stack

JavaScript · PostgreSQL (Supabase) · Vercel

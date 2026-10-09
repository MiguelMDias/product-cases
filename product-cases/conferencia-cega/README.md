# Auditoria por Conferência Cega

> **Área:** Logística · **Meu papel:** [descreva: o que você definiu e construiu, e quem mais participou] · **Status:** em produção

## Contexto

A empresa expede cargas de material de construção o dia todo. A conferência do que saía era feita com o conferente olhando a quantidade que o sistema dizia que deveria estar na carga.

## Problema

Quem confere sabendo o número esperado tende a encontrar exatamente esse número. É viés de confirmação: a divergência só aparecia depois, no inventário ou na reclamação do cliente, quando já não dava para saber onde o erro tinha acontecido.

## Decisões de produto

| Decisão | Por quê |
|---|---|
| O auditor **conta sem ver o esperado** | É o que elimina o viés; a comparação é feita pelo sistema, depois |
| **Seleção automática** das cargas a auditar, por amostragem ao longo do dia | Ninguém escolhe o que vai ser auditado |
| **Dupla conferência** antes de confirmar uma divergência | Separa erro de contagem de erro real de carga |
| Contagem **progressiva por código de barras** | Reduz erro de digitação e acelera o trabalho no pátio |
| **Bloqueio de auditoria simultânea** da mesma carga | Evita duas pessoas contando a mesma coisa |
| Painel de gestão separado do app do auditor | Quem conta não vê indicador; quem gere não interfere na contagem |

## Uma restrição real

O ERP da empresa não tem API. A solução foi tratar os relatórios que ele exporta e cruzar com um catálogo de quase 20 mil produtos. A decisão foi não esperar a integração ideal para entregar valor.

## Solução

- **App do auditor:** recebe a carga sorteada e conta por código de barras, sem acesso ao esperado.
- **Painel de gestão:** cobertura de auditoria, taxa de erro e anomalias por rota e transportador.
- **Liberação de cargas bloqueadas:** a carga com divergência confirmada só segue depois de tratada.

> _[Adicione aqui 2 ou 3 telas, com placas, nomes e transportadores cobertos.]_

## Resultados

- A auditoria deixou de depender de quem confere e passou a gerar indicador.
- Hoje dá para ver onde o erro se concentra (rota, transportador), em vez de descobrir no inventário.
- _[Adicione os números: cargas auditadas, cobertura atual, taxa de erro antes e depois.]_

## Aprendizados

- **O desenho do processo vale mais que a tela.** A regra "não mostrar o esperado" é o produto; o resto é suporte a ela.
- **Restrição de integração não é desculpa para não entregar.** Exportação de relatório resolveu a primeira versão.

## Stack

PostgreSQL (Supabase) · Node.js · Python (tratamento dos relatórios) · JavaScript

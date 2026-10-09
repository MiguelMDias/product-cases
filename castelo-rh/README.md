# Castelo RH — triagem de currículos com IA

> **Área:** RH · **Meu papel:** produto e desenvolvimento, do discovery à entrega · **Status:** em produção

![Dashboard do Castelo RH](img/01-dashboard.png)

## Contexto

O Grupo Castelo Forte recebe milhares de currículos por mês, para vagas de loja, logística, atendimento e administrativo. Todos chegavam por e-mail, na mesma caixa de entrada, sem separação por vaga.

## Problema

- **Volume sem filtro:** a equipe de RH passava horas por dia só triando, antes de conseguir avaliar alguém.
- **Reenvios:** o mesmo candidato mandava o currículo várias vezes, e cada reenvio era lido de novo.
- **Histórico em planilha:** quem já tinha sido entrevistado, aprovado ou reprovado ficava em uma planilha de Excel, separada dos currículos.
- **Risco:** um bom candidato podia se perder no volume.

## Discovery

Validei cada requisito com os diretores e com o time de RH. Três descobertas mudaram o desenho do produto:

1. **O RH não pensa em "vaga", pensa em "perfil".** A pergunta do dia a dia é "quem eu tenho para vendedor júnior?", e não "quem se candidatou à vaga 12?".
2. **O currículo é reaproveitável.** Quem não serve para a vaga de hoje pode servir para a de amanhã.
3. **Não dá para mudar o comportamento do candidato.** Ele vai continuar mandando e-mail, em PDF ou Word.

## Decisões de produto

| Decisão | Por quê |
|---|---|
| Classificar por **setor, função e nível**, e não por vaga | Um currículo recebido hoje já responde à vaga que abrir amanhã |
| **Uma pessoa, um cadastro** | Reenvios são reconhecidos e atualizam o cadastro, em vez de virar retrabalho |
| A IA **explica** a análise: pontos positivos, negativos e resumo | O RH precisa confiar na nota para usar; nota sem justificativa não é usada |
| **Revisão manual** quando a IA não tem segurança | Melhor uma fila de revisão do que uma classificação errada |
| **A decisão é sempre de uma pessoa** | O sistema classifica e ordena; não aprova nem elimina ninguém |
| Acompanhar o processo **até a contratação** na mesma ferramenta | Elimina a planilha paralela e fecha o funil |
| **Dados pessoais protegidos** antes de irem para a IA, e expurgo de inativos | LGPD tratada no desenho, e não depois |
| Nenhuma mudança para o candidato | O sistema se adapta ao e-mail; o candidato não precisa aprender nada |

## Solução

**Análise da IA.** Cada currículo recebe pontos positivos, pontos negativos e um resumo. A pessoa do RH lê em segundos e decide.

![Análise da IA](img/02-analise-ia.png)

**Candidatos em processo.** Nota do currículo, status e a próxima ação de cada candidato: agendar, registrar resultado, contratar.

![Candidatos em processo](img/03-em-processo.png)

**Entrevistas.** Agenda do dia e do mês, com o resultado registrado na mesma tela.

![Entrevistas](img/04-entrevistas.png)

**Histórico do candidato.** Substitui a planilha: todo contato anterior com a empresa fica ligado ao cadastro.

![Histórico do candidato](img/05-historico.png)

## Resultados

| Indicador | Antes | Depois |
|---|---|---|
| Encontrar um candidato apto | Horas de leitura na caixa de entrada | Alguns cliques, com filtro por setor, função e nível |
| Reenvios do mesmo candidato | Lidos um a um | Mais de 2 mil reconhecidos automaticamente |
| Base de candidatos | Caixa de e-mail | 3.048 candidatos únicos cadastrados |
| Histórico de processos seletivos | Planilha de Excel | Mais de 10 mil registros migrados para o sistema |

## Aprendizados

- **Em produto com IA, a parte difícil não é o modelo.** É definir o critério e decidir onde a pessoa entra.
- **A classificação por perfil foi a decisão que mais rendeu.** Ela só apareceu porque ouvi como o RH fala do próprio trabalho.
- **Fila de exceção é funcionalidade, não defeito.** Mostrar o que o sistema não conseguiu processar aumentou a confiança no que ele processou.

## Próximos passos

- Portal "Trabalhe Conosco" como segundo canal de entrada, além do e-mail.
- Indicadores de conversão por etapa do funil, do banco à contratação.

## Stack

Python · PostgreSQL (Supabase) · API de LLM · JavaScript

# WIC-EAP — doc e FINDINGS dos pré-registos 25–30

Compilação de duas fontes, sem alterações ao texto:

1. O doc **"WIC-EAP — auditoria independente, drawdown e sentimento"** ([claude.ai](https://claude.ai/artifact/6bL9HmN97kTJMWjhqPr9vS)), exportado em Markdown a 7/11/2026 (revisão 115). Cobre os pré-registos 1–30.
2. Os **FINDINGS25–30** do branch `ccr-698394c2-7q5oxi` (commit `67c5d8e`, 7/11/2026), pasta `TradingV2/research/ACOES/wic_trader_20261107/`. Os pré-registos, scripts e saídas (`out/`) ficam nesse branch.

Os FINDINGS dos pré-registos 1–24 estão noutros branches; a secção "Reprodução e fontes" do doc diz qual. Os títulos das duas fontes desceram um nível para caberem neste ficheiro.

## Índice

- [Parte 1 — o doc](#parte-1--o-doc)
- [Parte 2 — FINDINGS25–30](#parte-2--findings2530)


---

# Parte 1 — o doc

## WIC-EAP — auditoria independente, drawdown e sentimento

Nov 5, 2026 · @Kanashi

**Objetivo: +30% de lucro.** É a fasquia dos vencedores anteriores (+28,4% em 2024 e +33,3% em 2025) e o que é preciso para ganhar o voo para o Japão. Pelo site da JPSI, o voo é o prémio do 1.º lugar da Divisão Trader; a Divisão AI Agent dá subscrições de ChatGPT Pro ou Claude Max. As probabilidades deste doc foram calculadas para a Divisão AI Agent (fev–mar, 36 sessões), excepto a secção "Divisão Trader (pré-registo 25)", feita para a Divisão Trader (4/jan–25/mar, 57 sessões). A equipa está inscrita na Divisão AI Agent: a recomendação é para essa divisão.

**Estado a 7/11 (pré-registos 1–30):** a equipa está na Divisão AI Agent. A recomendação é a EAP 1,4× com M1b durante a janela e, se as opções forem permitidas, uma aposta binária no QQQ na última sessão, arriscando só os lucros acima de +2%. Dá **P(≥ 30%) de 31% (28,5% com custos de 20%), mediana +2% e 59% das trajetórias acima de zero**. O custo de bid-ask medido nas spreads reais de QQQ de 1 dia é \~9%. Sem opções, a P(≥ 30%) da EAP sozinha é \~0. O tecto antigo (\~27%) só valia para um NAV contínuo; uma aposta resolvida dentro de uma sessão não cria picos intermediários. A recomendação e as alternativas estão em "Recomendação actual".

**Atualização (5/11):** com as regras oficiais da WIC2026 (Divisão AI Agent, DQ a 20%, só o 1.º lugar tem prémio), a EAP sozinha não chega para ganhar: nunca passa de +10% em fev–mar. A recomendação passa a ser EAP 80% + uma camada de TQQQ ajustada à vol, com lock a +15% e piso a 88% do pico (P(≥ 15%) de 28–44%, 0,4% de desclassificação). Se for preciso 20% ou mais, calls de QQQ. Ver as secções a partir de "Torneio: regras oficiais da WIC2026".

**Atualização 3 (5/11, robustez):** a base passa a ser a EAP concentrada nos nomes mais voláteis (K=15, prioridade por vol idiossincrática, com hedge). Sozinha dá P(≥ 15%) de 31%, quase sem DQ e sem sensibilidade a choques. Passa o calendário SEC, K=10 e K=20, as duas metades e o bootstrap por ano (+5,9 pp sobre a EAP 80%, IC95% \[+3,7; +7,9\]). A camada de TQQQ por cima falha quando o intradiário é medido ação a ação e em choques de −8%. A única camada elegível são calls de QQQ com 5% do NAV e lock a +20% (P(≥ 20%) de 11–26%). Falta o viés de sobrevivência. Ver "Recomendação actual" e "Cenários das regras".

**Atualização 4 (6/11, torneio):** simulei o torneio com 14 adversários. A EAP concentrada sozinha tem a maior P(1.º): 41%, contra 27% das calls compradas no 1.º dia. Os adversários também estão comprados no QQQ, por isso as calls quase não te destacam deles. Para manter o alvo de +30%, o melhor é **ligar as calls pela classificação**, só quando o líder já passou de +10%. Ao fecho, isso dá P(1.º) de 35% e P(≥ 30%) de 7,5% / 16,6% (sem / com tendência). Um kill-switch 2 pp abaixo do piso e um limite ao tamanho das ordens deixam o DQ operacional em \~0%. Nenhum dos sinais clássicos prevê a tendência do QQQ. Ver as secções a partir de "O teto dos +30% e a previsão do QQQ".

**Atualização 5 (6/11, autocorrelação):** a EAP não tem autocorrelação negociável por ação, setor, mercado ou calendário. Nenhuma das 8 hipóteses do pré-registo 7 passa, e um win numa ação não torna o seguinte mais provável (52,1% contra 52,5% depois de um loss). As notícias repetem-se, mas o preço já as conta. A persistência que existe é de risco: o tamanho dos movimentos e o mesmo setor na mesma noite. Dentro da janela, o alfa da EAP concentrada não tem momentum, por isso o gatilho das calls deve continuar a olhar para o líder e não para o nosso arranque. Ver "Autocorrelação da EAP".

**Atualização 6 (6/11, testes recomendados):** nenhum dos testes do pré-registo 8 muda a recomendação actual. O gatilho θ com o alfa EAP que falta troca P(≥ 30%) por P(1.º) sem dominar a regra actual. As regras de stress e o teto por setor pioram o DD histórico da EAP concentrada e custam alfa. Volume e short volume não passam o corte. Na sobrevivência, datas isoladas chegam: na Bloomberg, os membros históricos pedem-se precisamente uma data de cada vez. O ponto de equilíbrio é \~16% dos eventos virem de nomes em falta. Ver "Testes recomendados (pré-registo 8)".

**Atualização 7 (6/11, cauda, dificuldade e short selling):** nada passa e a recomendação mantém-se. Depois de dias agitados, a cauda é mais grossa mas o prémio também é maior, por isso reduzir o tamanho custa alfa. As ações afundadas 50% ou mais são o segmento que mais rende, e tirá-las custa P(1.º) sem proteger da sobrevivência. O short volume tem um gradiente limpo por evento, mas não muda a carteira; o short interest não prevê nada. Ver "Cauda, dificuldade e short selling (pré-registo 9)".

**Atualização 8 (6/11, P(≥ 30%)):** com o DD medido ao fecho, há uma combinação melhor do que as calls no 1.º dia nas duas métricas. Strike +3% em vez de +5%, piso a 83% em vez de 85% e kill-switch a 81%. P(≥ 30%) sobe de 9,9% para 12,2% sem tendência (14,9% nos caminhos de 2001) com DQ \~0%. O custo é uma margem menor nas janelas reais. Ver "Combinação para P(≥ 30%) (pré-registo 10)".

**Atualização 9 (6/11, controlo do DD):** nenhum mecanismo novo passa. O que já está na recomendação (regra de venda, piso, kill-switch, limite de ordem) está perto da fronteira. Cortar o risco do livro EAP corta o alfa que dá a P(1.º). O quase-empate é reduzir o livro EAP só quando a folga até à desclassificação fica curta: ao fecho tira 80% do DQ nos choques sem mexer na P(≥ 30%), por −0,7 pp de P(1.º). Ver "Controlo do DD (pré-registo 11)".

**Atualização 10 (6/11, entrada em R−1 e camada intradiária):** pela regra, nada substitui a recomendação actual. Entrar no fecho de R−1 em vez de R−2 sobe o alfa da EAP concentrada em +4 a +5 pp, mas com as calls de referência o DQ passa para 0,6–7%. A camada intradiária de QQQ falha: um crash dentro da sessão atravessa o stop. Exploratório: a EAP com 10 nomes e entrada em R−1, com piso a 85% e o M1b, é elegível e sobe a P(1.º) de 28% para 42%. Com o calendário SEC, o ganho em P(≥ 30%) desaparece. Ver "Entrada em R−1 e camada intradiária (pré-registo 12)".

**Atualização 11 (6/11, R−1 confirmada):** a EAP com 10 nomes, entrada em R−1 e data confirmada por duas fontes passa todos os testes ao fecho e passa a ser a base recomendada. Quando as fontes diferem uma sessão, cobre as duas datas; quando diferem duas ou mais, não entra. Com calls 15%, +3%, piso 85% e M1b: P(1.º) de 43,9% contra 28,3% e P(≥ 30%) de 16,9% / 31,6% contra 12,2% / 28,7%, com DQ 0%. Sozinha: P(1.º) de 52,9% contra 40,8%. Passa as duas metades dos anos e os custos stress. No intradiário pessimista, as calls por cima falham o DQ em 2020–26; sozinha passa. Ver "Datas confirmadas e confirmação da entrada em R−1 (pré-registo 13)".

**Atualização 12 (6/11, calls pela classificação na nova base):** nenhum gatilho é confirmado. Ao fecho, os melhores ficam quase na P(1.º) da base sozinha (50–51% contra 51,5%), mas só com 8–11% de P(≥ 30%), contra 16,9% das calls no 1.º dia. Falham nas janelas de 2014–19 e com custos stress, porque aí a EAP já vai à frente do líder e as calls quase não são compradas. Ficam duas escolhas: a base sozinha para ficar em 1.º, ou as calls no 1.º dia para os +30%. Ver "Calls pela classificação na nova base (pré-registo 14)".

**Atualização 13 (6/11, validação):** a base nova passa a validação; o braço das calls está inflacionado. Sozinha, o leave-one-year-out não mostra inflação (0 pp); com calls, os 43,9% de P(1.º) valem \~38–40% fora da amostra. Sem confirmação da data em R−1, entra-se em R−1 pela data do calendário: aguenta até 50% de eventos sem confirmação, desde que o teste-sombra mostre que o calendário erra pouco. Fora de fev–mar o ganho aparece nas três épocas, mas não passa o corte (IC95% \[−0,2; +4,5\] pp). A janela exacta de 38 sessões não muda nada. Na sobrevivência, a Wikipedia resolve parte das listas, mas falta o S&P 600 de 2014–2019 e os preços de \~3/4 dos nomes que saíram. Ver "Validação da base nova (pré-registo 15)".

**Atualização 14 (6/11, eixos estruturais):** com o DD medido ao fecho, subir a base para 1,2× com o M1b leva a P(1.º) de 52,9% para 60,2% e a P(≥ 30%) de 7,6% para 26,1%, sem calls e sem inflação no leave-one-year-out. No intradiário pessimista só a 1,0× fica elegível. A entrada MOO em R−1, o reforço intradiário em R, o universo alargado e reduzir à frente falham. O alerta novo é a execução: com impacto realista nas MOC dos nomes ilíquidos, a P(≥ 30%) de todas as configurações vai a \~0. Ver "Eixos estruturais (pré-registo 16)".

**Atualização 15 (6/11, sobrevivência com as listas Bloomberg):** o universo actual infla o alfa. Em 2014–2020, com o S&P 600 e o S&P 400 da época e as empresas que saíram mas ainda cotam, o alfa fev–mar da base cai de 12,5% para 6,3% e a P(1.º) de 51,4% para 43,0%. Essas empresas têm EAP negativa (−82 bps por evento em fev–mar, contra +93 bps nos restantes nomes). Falta o efeito das 312 empresas que deixaram de cotar: entre +1,7 e −13 pp de alfa, conforme o cenário, e só se fecha com os preços delas. A 1,2× continua à frente da 0,8×, mas a vantagem encolhe. Ver "Sobrevivência com as listas Bloomberg (pré-registo 17)".

**Atualização 16 (6/11, candidatas e calendário, exploratório):** a melhor candidata não mudou. No universo da época, a EAP com 10 nomes, prioridade por vol e entrada em R−1 continua à frente das alternativas (15 nomes em R−1 ou R−2, 10 ou 50 nomes ao acaso), a 0,8× e a 1,2×, com e sem os cenários dos mortos. A 1,2× com M1b continua à frente, mas no cenário pessimista fica com P(1.º) de \~30% e P(≥ 30%) de \~1%. No calendário da Bloomberg (EVTS, 6/11–4/12), quando a data está confirmada o yfinance acerta o dia em 99%, mas a sessão de reação só em 92%: a hora antes/depois do mercado diverge em 8%. Quando a data da Bloomberg é estimada, só coincidem 12%. Ver "Sobrevivência com as listas Bloomberg (pré-registo 17)".

**Atualização 17 (6/11, universo da época completo):** com a composição da época do S&P 1500 em todos os 13 anos, o alfa fev–mar da base cai de 13,5% para 4,7% (IC95% \[−15,4; −2,0\] pp, já fora do zero). Com as empresas mortas fica em 4,9 / 3,2 / −0,7% (optimista / central / pessimista). A P(1.º) da base cai para \~26% no central e a P(≥ 30%) vai a \~0. A recomendação mantém-se (1,2× com M1b, P(1.º) \~30%), e a EAP continua muito melhor do que estratégias sem EAP (calls sozinhas: ≤ 10%). Os +30% deixam de ser um alvo realista. Ver "Universo da época completo e reajuste (pré-registo 18)".

**Atualização 18 (6/11, exploratório):** para os +30%, a EAP não é o caminho. Com o alfa corrigido, a maior P(≥ 30%) elegível é 6% sem tendência e 18% com tendência, e vem de calls de QQQ (25% do NAV, piso 83%) sem EAP, com a P(1.º) a cair para 12%. Com EAP 0,8× + calls fica em 4% / 12%. Quem sai dos índices é previsível (AUC 0,83 fora do ano): pouco volume, vol idiossincrática alta, preço baixo, longe do máximo e a cair em 12 meses. São exactamente os nomes que a prioridade por vol escolhe. Mas o filtro não se testa sem os preços das empresas mortas: nesse grupo, as que ficaram nos índices são sobreviventes e fazem o grupo parecer bom (+70 bps em fev–mar no decil de maior risco).

**Atualização 19 (6/11, fundamentais):** os financial statements (SEC XBRL, sem olhar para a frente) quase não acrescentam ao preço para prever quem sai dos índices (AUC 0,865 → 0,869). Nenhum filtro melhora a carteira: tirar os nomes em risco custa 3,2 pp de P(1.º) no cenário central, e tirar só os em risco e frágeis fica igual. A notícia útil é sobre as empresas mortas: os balanços delas parecem os das que ficaram (só 2–10% são frágeis), o que aponta para fusões. O alfa real da base fica mais perto dos cenários optimista e central (\~5–7% a 1,2×) do que do pessimista. A recomendação não muda. Ver "Fundamentais (pré-registo 19)".

**Atualização 20 (6/11, veto SEC e "não recupera"):** nada muda a recomendação. O modelo que prevê quem não recupera dentro dos nomes em risco acerta (AUC 0,73), mas esses nomes pagam mais a EAP: +332 bps em fev–mar, contra +12 bps do resto. Tirá-los custa 2,7 pp de alfa e 3,7 pp de P(1.º). O veto por filings da SEC (3.01, NT 10-K/Q, 4.01/4.02, 1.03) não custa nada, mas quase não separa as mortas dos nomes que ficaram (razão 2,5, abaixo dos 3 exigidos). Pelos filings, \~85% dos eventos das mortas são de empresas compradas, e os preços das não-fusão dão "inconclusivo" em \~90% dos casos: o pedido à Nasdaq vale sobretudo pelas compradas. Ver "Veto por filings e 'não recupera' (pré-registo 20)".

**Atualização 21 (6/11, P(≥ 30%) no pior cenário):** chegar aos +30% não garante o 1.º lugar: dá 70–84% de P(1.º) conforme os adversários, e \~48% com o relatório em 8.º. No pior cenário (DD intradiário desde o pico, sem tendência), a melhor combinação só com opções são puts de QQQ 6% abaixo do preço, a 30 dias, com toda a folga até um piso de 81%: P(≥ 30%) de 17,4% e P(1.º | ≥ 30%) de 83–85%, porque só chegam lá quando o mercado cai e os adversários perdem. Com calls, 13,9% (28,8% com tendência). Ver "P(≥ 30%) no pior cenário (pré-registos 21 e 22)".

**Atualização 22 (6/11, puts reais e EAP + opções):** a volatilidade implícita real das puts do SPY 6% abaixo do preço é 1,12× o VIX, abaixo dos 1,20× usados, por isso os 17,4% são conservadores. Nenhuma combinação EAP + opções é elegível no pior cenário (DQ de 26–68%). As puts são uma aposta: resultado mediano de −14%, negativo em 74% das vezes, e compradas ao ask real perderam 55% do prémio sem tendência.

**Atualização 23 (7/11, ML, filtros, opções com folga reservada, UVOL/DVOL):** nada passa e a recomendação mantém-se. O ML não escolhe melhores nomes do que a vol idiossincrática, e prever quem cai muito tira os eventos que mais pagam. Com folga reservada, a EAP + opções passa a caber ao fecho, mas não sobe a P(≥ 20%) acima dos 23% da EAP sozinha. Esses 23% vêm de 3 dos 13 anos e caem para 6,5% no cenário pessimista das mortas. Ver "ML, filtros e opções com folga reservada (pré-registo 23)".

**Atualização 24 (7/11, correlação negativa e timing):** juntar estratégias com correlação negativa baixa a variância mas não cria retorno, e escolher a estratégia pelo regime de mercado não bate o QQQ fora da amostra. Uma P(≥ 30%) acima de 80% exigiria um Sharpe anual de \~6 durante as 7 semanas; o QQQ tem 0,9. Ver "Correlação negativa e timing por regime (pré-registo 24)".

**Atualização 25 (7/11, edições anteriores e prémios):** o voo para o Japão é o prémio da Divisão Trader (equipas de 3, três contas de US$1M, 4/jan–25/mar), não da Divisão AI Agent. Os vencedores anteriores fizeram +28,4% (2024) e +33,3% (2025), com o QQQ a cair. O DD conta-se no fecho de cada sessão, desde o pico, e o capital inicial conta como pico. Ver "Edições anteriores da WIC e prémios".

**Atualização 26 (7/11, Divisão Trader):** refiz a análise com as regras da Divisão Trader (57 sessões desde 4/jan, DD ao fecho desde o pico, 16 equipas), adversários calibrados para que o melhor faça +30% e o DQ contado como derrota, sem o corte de elegibilidade. Janeiro não acrescenta alfa (4,6% contra 4,7% em fev–mar, a 1,2×). A P(1.º) da recomendação cai de \~30% para 18%. A melhor da grelha (EAP 1,4×) dá 18,8%, não passa a regra e depende de 4 anos fortes. Nenhuma combinação com opções melhora a P(1.º); a maior P(≥ 30%) é 17,8%. Exploratório: começar a EAP só a 1/fev dá 23–25%, mas foi escolhido depois de ver janeiro negativo. Ver "Divisão Trader (pré-registo 25)".

**Atualização 27 (7/11, AI Agent):** a equipa está na Divisão AI Agent, por isso refiz para ela as correcções da actualização 26 (pré-registo 26). Os adversários passam a ter o melhor em +15%, +22% ou +30%, porque a divisão não tem histórico; o DQ conta como derrota, sem corte de elegibilidade; e reporto a P(pódio), porque o site dá prémio ao 1.º–3.º. A recomendação passa de 1,2× para 1,4×: +2,2 pp de P(1.º) (25,2% contra 23,0%), à frente em todas as fasquias e sem inflação no leave-one-year-out. Pela P(pódio) a diferença é +1,6 pp e não chega ao corte. As opções continuam a não ajudar. Ver "Divisão AI Agent (pré-registo 26)".

**Atualização 28 (7/11, aposta final):** o tecto de P(≥ 30%) do doc assumia um NAV contínuo. Como o DD só conta ao fecho, uma aposta binária resolvida dentro de uma sessão chega a (1 − 0,81)/(1,30 − 0,81) = 38,8% sem edge (Dubins–Savage, "bold play"). No pré-registo 27, a EAP 1,4× nas sessões 1–35 seguida de uma aposta assim na última dá P(≥ 30%) de 37,5% (custos de 10%) e passa as duas regras. Até ao líder + 3 pp, a P(1.º) sobe de 25% para 34%. Depende de as opções serem permitidas, do custo real das spreads de 0–1 dias e de o relatório defender a aposta. Ver "Aposta final numa só sessão (pré-registo 27)".

**Atualização 29 (7/11, mediana da aposta final):** não há forma de ter a P(≥ 30%) alta e a mediana positiva ao mesmo tempo. Com mediana ≥ 0, a melhor P(≥ 30%) é 9% (apostar só se o NAV estiver abaixo de 1,06). As trajetórias que estão atrás têm pouca folga e más odds; a P(≥ 30%) vem das que já estão à frente. Meio-termo: apostar metade da folga dá P(≥ 30%) de 29% com mediana −2%. Ver "Aposta final e mediana (pré-registo 28)".

**Atualização 30 (7/11, aposta só com os lucros):** a mediana da aposta final com toda a folga é negativa porque tem de ganhar mais do que arrisca (de \~+5% a +30% arriscando \~20 pp), e ganha \~40% das vezes. Arriscando só os lucros acima de +2%, a trajetória acaba em +2% ou em +30%; abaixo de +2% aposta-se toda a folga, porque perder não baixa a mediana. Dá P(≥ 30%) de 31% com mediana +2% e 59% das trajetórias acima de zero. Ver "Aposta só com os lucros (pré-registo 29)".

**Atualização 31 (7/11, custo real e várias apostas):** nas cadeias reais do QQQ (fecho de 6/11), o bid-ask de uma spread de 1 dia equivale a um custo de \~9% (11–12% a 2–3 dias), sem contar o prémio de volatilidade. Os 10% usados cobrem o bid-ask; o custo real deve ficar entre 10% e 20%, e a regra dos lucros passa nos dois (31% e 28,5%). Apostar várias vezes não sobe a P(≥ 30%) (+0,6 pp no melhor caso). Uma aposta extra a meio da janela, só com os lucros, deixa a P(≥ 30%) igual e sobe as trajetórias acima de zero de 59% para 65%. Ver "Custo real e várias apostas (pré-registo 30)".

### Recomendação actual (7/11, Divisão AI Agent, depois dos pré-registos 26–30)

EAP concentrada a 1,4× com M1b durante a janela e, se as opções forem permitidas, uma aposta binária no QQQ na última sessão, arriscando só os lucros acima de +2%. Dá P(≥ 30%) de 31% (28,5% com custos de 20%), mediana +2%, 59% das trajetórias acima de zero e P(1.º) de 26% contra adversários cujo melhor faz +22%.

**1. EAP (sessões 1–35)**

- **Eventos e seleção:** membros actuais do S&P 1500 cotados na Nasdaq, ex-OLD, |β| ≤ 2,5; até 10 posições, por ordem de vol idiossincrática.
- **Entrada e saída:** entrada MOC no fecho de R−1, saída MOC no fecho de R, hedge de QQQ. Data e hora confirmadas pela Bloomberg; não entrar em datas só estimadas.
- **Tamanho e guardas:** 1,4× (14% do NAV inicial por nome), M1b (m1 = 0,15), piso 88%, kill-switch a 86%, limite de ordem. O kill-switch e o limite de ordem ficam fora do LLM: nas janelas reais, o pior DD da 1,4× fica a \~2 pp do DQ.
- **Sem camadas de opções durante a janela:** calls ou puts mantidas por cima da EAP descem a P(1.º) e a P(pódio).

**2. Aposta final (última sessão: 24/mar, ou manhã de 25/mar, fechada antes das 15:50)**

- **Instrumento:** put spread de QQQ de 1 dia (a call dá o mesmo em P(≥ 30%)), comprada na abertura e vendida antes do fecho. Custo de bid-ask \~9%.
- **Tamanho:** se o NAV estiver acima de +2%, arrisca-se só o que está acima de +2% (perdendo, acaba em +2%); abaixo de +2%, arrisca-se toda a folga até 81% do pico. Os strikes escolhem-se para que, ganhando, o NAV acabe em +30%.
- **Execução:** a EAP não abre posições para essa sessão. A decisão (fazer ou não, direção, tamanho) é do LLM, com esta regra escrita e registada antes da competição.
- **Opcional:** a mesma aposta, só com os lucros, também na sessão 18. A P(≥ 30%) fica igual e as trajetórias acima de zero sobem para 65%.

**Alternativas, conforme o objectivo (custo 10%):**

| Objectivo | Aposta final | P(≥ 30%) | Mediana | P(1.º) A22 | P(pódio) |
| --- | --- | --- | --- | --- | --- |
| +30% com mediana positiva (recomendada) | só os lucros acima de +2% | 31,0% | +2,0% | 25,8% | 40,3% |
| Máxima P(≥ 30%) | toda a folga | 37,5% | −10,3% | 29,2% | 40,1% |
| 1.º lugar, com classificação visível | até ao líder da véspera + 3 pp | 10,4% | −10,0% | 34,3% | 43,1% |
| Pódio, se o prémio for do 1.º ao 3.º | só se o NAV estiver abaixo de +6% | 9,0% | +7,5% | 29,7% | 47,3% |
| Sem opções | nenhuma (EAP sozinha) | 0,2% | +6,1% | 25,2% | 44,7% |

**Riscos que ficam:**

- **Opções permitidas?** Sem elas não há aposta binária, e a P(≥ 30%) volta a \~0.
- **Custo:** o bid-ask de \~9% vem de uma fotografia; com o prémio de volatilidade, o custo real deve ficar entre 10% e 20%.
- **Fills no paper:** a regra desclassifica quem aproveitar fills irrealistas. Ordens limitadas, registadas ao lado do bid/ask real.
- **Relatório (30% do ranking):** a aposta tem de ser apresentada como a estratégia óptima de torneio (Dubins–Savage), com a regra escrita antes.
- **Execução da EAP:** as ordens MOC ficam 17% maiores nos nomes ilíquidos.
- **Modelo:** adversários sintéticos; empresas mortas por cenários.

**Pendentes antes da competição:**

- No grupo de WhatsApp: as opções são permitidas? A classificação é visível, e com que atraso? O prémio é só para o 1.º ou do 1.º ao 3.º?
- Inscrição até 15/11.
- Período de testes (7–20/dez): uma spread de QQQ de 1 dia em paper (fill contra o bid/ask real), ordens MOC grandes num nome ilíquido e o short de QQQ.
- Escrever a tese da aposta final e a regra exacta para o relatório.
- Teste-sombra com o calendário EVTS depois de 4/12.

### Recomendação para a Divisão Trader (7/11, pré-registo 25)

Não mudou: EAP concentrada a 1,2× com M1b, sem opções. Continua a ser a forma mais robusta de ficar em 1.º, mas na Divisão Trader isso vale \~18% de P(1.º), não \~30%, e a P(≥ 30%) fica perto de 0.

**Execução:** como na recomendação anterior (abaixo), agora de 4/jan a 25/mar.

**Se só os +30% interessarem:** puts de QQQ 6% abaixo do preço a 86 dias, com toda a folga até um piso de 81% e sem EAP. P(≥ 30%) de 15,5%, P(1.º) de 16,5%, mediana −8,9%. Com puts de 30 dias recompradas no vencimento, 17,8% e mediana −14,6%. É uma aposta na queda do mercado.

**O que pesa mais do que a estratégia:** o relatório. Com a EAP 1,2×, a P(1.º) é 26% com o relatório em 1.º, 20% em 3.º e 7% em 8.º.

**Candidata a testar, sem adoptar:** a EAP só desde 1/fev (P(1.º) 23–25%, exploratório). Registar janeiro de 2027 no teste-sombra antes de decidir.

**Pendentes novos:** confirmar no grupo de WhatsApp a regra de ranking da Divisão Trader (há relatório? RRF?) e se o DQ também é a 20%; inscrever a equipa de 3 na Divisão Trader até 15/11.

### Recomendação anterior (6/11, Divisão AI Agent, depois dos pré-registos 16–22)

Substituída pela "Recomendação actual" acima (pré-registo 26, a mesma divisão). A execução descrita aqui continua válida, com o tamanho a passar de 1,2× para 1,4× e o piso para 88%.

EAP concentrada a 1,2× com M1b, sem calls e sem filtros: é a melhor opção testada para ficar em 1.º, em todos os cenários do viés de sobrevivência.

- **Eventos:** membros actuais do S&P 1500 cotados na Nasdaq, ex-OLD, |β| ≤ 2,5.
- **Seleção:** até 10 posições, por ordem de vol idiossincrática.
- **Entrada e saída:** entrada MOC no fecho de R−1, saída MOC no fecho de R, hedge de QQQ. Data e hora confirmadas pela Bloomberg; não entrar em datas só estimadas.
- **Tamanho e guardas:** 1,2× (12% do NAV inicial por nome), M1b (m1 = 0,15), piso 85%, kill-switch a 83%, limite de ordem.
- **Se o DD for medido no intradiário (todas as ações no mínimo):** 1,0× com piso 90% e M1 0,25.
- **Sem calls:** com o universo da época deixam de ser elegíveis (DQ 1,4–4%).
- **Sem filtros de risco de saída ou de fundamentais:** custam mais alfa do que poupam.
- **Sem veto por filings da SEC nem modelo de "não recupera":** o veto é neutro e não passa a regra; o modelo tira os eventos que mais pagam (pré-registo 20).
- **Se o objectivo passar a ser os +30%:** só puts de QQQ 6% abaixo do preço, 30 dias, toda a folga até um piso de 81% (83% para ter margem), sem EAP. P(≥ 30%) de 17% no pior cenário, mas P(1.º) de 19% e resultado mediano de −14% (pré-registos 21 e 22).

| Configuração | Alfa fev–mar: universo actual → época (central / optimista) | P(1.º) central | P(≥ 30%) sem / com tendência |
| --- | --- | --- | --- |
| 1,2×, M1b, piso 85% (recomendada) | 20,2% → 4,7% / 7,3% | 29,7% | \~0 / \~0 |
| 0,8×, sem M1 (base anterior) | 13,5% → 3,2% / 4,9% | 25,7% | \~0 / \~0 |
| Só calls de QQQ, 25% do NAV, piso 83% | — | 12% | 6% / 18% |

**Riscos que ficam:**

- **Empresas mortas:** só entram por cenários. Os balanços apontam para fusões, por isso o mais provável é o cenário central ou o optimista.
- **Execução:** ordens MOC grandes em nomes ilíquidos. Com impacto realista, o alfa cai mais; falta saber como a IBKR paper preenche estas ordens.
- **Calendário:** o yfinance erra a sessão de reação em \~8% das datas confirmadas.
- **Adversários sintéticos:** a P(1.º) serve para comparar configurações, não é uma previsão.

**Pendentes:**

- [ ] Inscrição até 15/11.
- [ ] Preços das empresas mortas: Nasdaq Data Link (até 2018) ou Bloomberg (pedido\_bloomberg\_mortos.csv). Pedir também as compradas: são \~85% dos eventos e as únicas com potência para separar os cenários; a regra de decisão está fixada no PREREG20.
- [ ] Período de testes (7–20/dez): fill de uma MOC de \~5% do volume diário num nome ilíquido, contra o fecho oficial.
- [ ] Teste-sombra com o calendário EVTS depois de 4/12 (shadow\_evts.py).
- [ ] Perguntar aos organizadores: o DD é medido desde o pico ou desde o capital inicial, ao fecho ou intradiário? Há opções? A classificação é visível? Qual é o k do RRF?

### Respostas diretas

1. **As contas anteriores estão certas?** Sim, a aritmética está. Reconstruí o ledger sem usar o código antigo e bate evento a evento (correlação 0,998; média 53,7 vs 53,6 bps). Os pontos fracos estão nos dados (calendário, sobrevivência) e num detalhe de inferência, não nos cálculos.
2. **Que tamanho mantém o DD abaixo de 15%?** Com hedge QQQ, o pior DD numa janela 1 fev–24 mar (2014–2026) foi −1,8% a 40% de alocação, −3,5% a 80% e −5,0% a 120%. No bootstrap, P(DD > 15%) é 0 em 20.000 trajetórias para todos os tamanhos. O que limita o tamanho são os cenários de stress, não a história. Recomendo K=50 com 60–80% de alocação ($12–16k por slot).
3. **O sentimento Fed ajuda?** Não se confirmou. No período que a investigação anterior não usou (2022–ago 2024), o efeito é zero: −0,5 bps por +10 pp, IC95% \[−13; +22\]. O hedge adaptativo perdeu em 3 das 4 janelas fev–mar testáveis.
4. **As odds de EPS ajudam?** Agora com 408 eventos em vez de 24, a diferença alto−baixo é +200 bps, mas o IC95% inclui zero. As odds preveem o *beat* melhor que o histórico da empresa, só que o *beat* quase não se traduz em retorno.
5. **E o vídeo?** O modelo do vídeo calcula o *fair value* de um contrato binário a partir de um subjacente observável e negoceia o desvio. Não é sentimento. Na EAP, o equivalente seria o *implied move* das opções contra o movimento histórico nos earnings, e isso exige dados de opções. Apliquei a outra metade do método: hipóteses e critérios de corte escritos antes de ver os resultados.

### Replicação da EAP

O prémio é real nestes dados: +58 bps brutos por evento coberto, contra −2 bps nas mesmas ações fora dos earnings. Fiz um novo download de preços Yahoo (desde 2012), datas yfinance e calendário Nasdaq, e reconstruí tudo sem reutilizar o código anterior. Usei R pela regra das 12:00 ET, entrada no fecho de R−2, beta contra QQQ em \[R−252, R−3\] e universo ex-OLD com |β| ≤ 2,5.

| Amostra (2014–out 2026) | Eventos | Média coberta, bps \[IC95% por semana\] | R−2→R−1 | Gap R−1→abertura R | Intraday R |
| --- | --- | --- | --- | --- | --- |
| Base WIC (515 ações) | 22.814 | +58,0 \[+44,1; +72,2\] | +7,4 | **+38,5** | +11,7 |
| Só 2022+ | 9.459 | +55,5 \[+30,0; +81,5\] | +4,3 | +40,3 | +10,5 |
| Só 1 fev–24 mar | 4.262 | +84,7 \[+51,5; +120,4\] | +12,4 | +40,6 | +31,8 |
| BMO (antes das 12:00) | 7.964 | +36,5 \[+14,7; +57,6\] | +6,1 | +19,0 | +11,0 |
| AMC | 14.850 | +69,5 \[+53,4; +85,6\] | +8,1 | +49,0 | +12,1 |
| Controlo: mesma ação ±10/20 sessões | 91.297 | −1,7 \[−8,7; +5,2\] |  |  |  |

- **Correspondência com o ledger anterior:** 25.957 eventos em comum, mesma data de entrada em 100%, correlação do beta 0,999 e do retorno 0,998.
- **Inferência:** os relatórios agruparam por empresa × trimestre, o que dá praticamente um evento por grupo e ignora choques comuns no mesmo dia. Agrupando por semana do calendário, o IC alarga mas continua longe de zero.
- **Distribuição:** a taxa de acerto é de 52,4% e a mediana +34 bps. O percentil 1% é −22,8% por evento e o pior −62,4%. Sem o melhor 1% dos eventos, a média cai para +23,5 bps: o prémio depende das caudas.
- **Por ano:** a média foi positiva nos 13 anos, mas quase nula em 2017 (+17), 2021 (+8) e 2025 (+12 bps).

### Drawdown: quanto se pode alavancar

Com K=50 e 80% de alocação, todos os cenários ficam abaixo de 15%, exceto o choque extremo. No pior ano histórico, o DD fev–mar foi −3,5%. O simulador usa ações inteiras dimensionadas pelo fecho de R−3, comissão IBKR fixa, hedge QQQ em ações inteiras, borrow, financiamento, dividendos, cap bruto de 1,9× e prioridade pseudo-aleatória com 3 sementes. O DD é medido sobre o NAV diário, e o limite intradiário assume o *Low* de cada ação e o *High* do QQQ ao mesmo tempo (pessimista).

| K=50, alocação | $/slot | Retorno médio fev–mar (base / stress) | Pior ano fev–mar | Pior DD fev–mar (fecho / limite intradiário) | Bootstrap 99,9% (custos stress, época de earnings) | Sem edge, 99,9% | Sem hedge: pior DD fev–mar | Choque: 2× pior dia histórico, livro cheio | Choque: todos no percentil 1% |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 40% | $8k | +1,7% / +1,3% | −0,5% | −1,8% / −3,6% | −4,7% | −4,2% | −4,0% (2020) | −6,2% | −9,1% |
| **80%** | **$16k** | **+3,5% / +2,7%** | **−1,0%** | **−3,5% / −7,1%** | **−9,5%** | **−8,5%** | **−7,9% (2020)** | **−12,4%** | **−18,3%** |
| 120% | $24k | +5,1% / +3,9% | −2,1% | −5,0% / −9,4% | −13,6% | −12,1% | −11,8% (2020) | −18,6% | −27,4% |

- **Bootstrap:** blocos estacionários de 5 sessões, 20.000 janelas de 36 sessões, só com dias de época de earnings (livro cheio, como em fevereiro). P(DD > 15%) foi 0,00% a 40% e 80%, e 0,04% a 120% com custos stress.
- **Sem edge:** retirei a média ao P&L diário para simular um prémio que desaparece em 2027. Mesmo com o edge invertido, a 80% o percentil 99,9% fica em −9,8%.
- **Choques:** o pior dia histórico foi 27/01/2026. Nesse dia, 14 eventos reagiram em simultâneo com média de −7,7% (CVLT −30%, SANM −21%). "Livro cheio" assume 50 posições a reagir na mesma noite, o que nunca aconteceu, porque metade do livro está sempre em R−1.
- **Hedge:** sem short de QQQ, 2020 teria sido o pior caso. O hedge é o que segura o DD, e a sua disponibilidade (borrow, margem) deve ser confirmada no paper em janeiro.
- **100 slots** não melhora o risco por unidade de retorno: 150% em K=100 deu +3,4% e DD −3,2%, quase igual a 80% em K=50. Em fevereiro, K=50 enche (máx. 50 posições), mas 100 slots duplica comissões mínimas.

**Recomendação de risco:** K=50 e 60–80% de alocação, com três regras determinísticas. Primeiro, cap por nome em 1,6% do NAV. Segundo, travar novas entradas se o DD chegar a −8%. Terceiro, reduzir para metade a −10% e não abrir posições sem hedge confirmado. Estas regras são um seguro barato, porque historicamente nunca disparariam.

### Sentimento Fed/QQQ

O sinal reaparece no período em que foi descoberto e desaparece no período novo. Pelo critério de corte fixado antes do teste, está morto como regra. Recolhi de novo os mercados Polymarket por reunião, que vão até dez/2022 (a investigação anterior começava em set/2024). Usei a definição anterior: S = P(corte) − P(subida) da próxima reunião, Δ7 com quote ≤ 15:45 ET e idade ≤ 24 h, e alvo QQQ fecho→fecho seguinte. O bootstrap é feito por reunião.

| Período | Dias / reuniões | bps no dia seguinte por +10 pp de Δ7 \[IC95%\] | Com controlo QQQ 5 dias |
| --- | --- | --- | --- |
| Set/2024–jul/2026 (janela da investigação anterior) | 396 / 16 | +19,0 \[+2,2; +32,7\] | +20,0 \[+4,1; +30,5\] |
| **Dez/2022–ago/2024 (nunca usado: holdout)** | **258 / 13** | **−0,5 \[−13,3; +21,8\]** | **−0,5 \[−13,4; +21,2\]** |
| Tudo, dez/2022–out/2026 | 708 / 30 | +9,3 \[+0,1; +19,1\] | +9,7 \[+0,6; +18,9\] |

Segundo critério de corte: o sinal tinha de melhorar a carteira EAP. Testei o hedge adaptativo com as mesmas regras anteriores (1,5× o beta se Δ7 < −10 pp, 0,5× se Δ7 > +10 pp) contra o hedge fixo, no mesmo motor, K=50 e 40%. O resultado foi −0,33 pp em fev–mar 2024, −0,11 pp em 2025 e −0,11 pp em 2026, sem diferença em 2023. Em ano completo deu +0,27 pp em 2025 e +0,28 pp em 2026, mas −0,34 pp em 2024 e −0,05 pp em 2023.

- **Não é reversão de curto prazo:** a correlação de Δ7 com o retorno QQQ dos 5 dias anteriores é 0,04, e o controlo não muda o coeficiente.
- **A leitura mais provável é uma dependência de regime.** Em 2024–26, num ciclo de cortes com inflação a descer, mais cortes era boa notícia para as ações. Noutros regimes, mais probabilidade de corte pode significar economia mais fraca (o ponto de Knox e Vissing-Jorgensen).
- **A versão robusta ao ciclo de subidas** (Δ da variação esperada em bps) também dá zero no holdout: −0,5 bps.
- **Kalshi:** os dados chegaram depois (911 mercados, 1,39 M velas horárias, desde mai/2023) e confirmam a conclusão. Kalshi dá +19,3 bps \[+6,5; +27,5\] na janela anterior e −3,9 \[−16,2; +18,0\] no holdout. A média Kalshi+Polymarket (o "consenso") dá +19,4 \[+4,6; +30,2\] na janela anterior e +8,1 \[−13,3; +52,7\] no holdout, com Spearman 0,004. Os Δ7 das duas plataformas têm correlação 0,88.

**Uso possível:** guardar Δ7 nos logs como contexto para o LLM, sem lhe dar poder sobre o hedge ou o tamanho.

### Odds de EPS e o *fair value* do vídeo

As odds de *beat* não passam o critério de corte como filtro. A direção (+) é consistente, mas o ruído é maior do que o efeito. Recolhi 1.608 mercados "beat quarterly earnings" com histórico horário (antes eram 350, com granularidade de 12 h). Isso deu 408 eventos EAP com quote ≤ 15:45 ET de R−2 e idade ≤ 24 h, entre out/2025 e nov/2026. Ficaram 112 ações, 75 eventos em fev–mar 2026 e cerca de 17% de cobertura dos eventos do universo. O corte é a mediana, fixada antes, em vez dos 80% escolhidos *post hoc*. O IC é bootstrap por semana.

| Variável em R−2 (ex-OLD, n≈298) | Alto − baixo, bps por evento \[IC95%\] | Spearman |
| --- | --- | --- |
| P(beat) | +215 \[−88; +433\] | 0,085 |
| ΔP nas 24 h anteriores | +118 \[−86; +324\] | 0,083 |
| *Gap* = P(beat) − taxa de beat da empresa nos 8 trimestres anteriores | +58 \[−108; +231\] | 0,025 |

Com todos os nomes (n=408), o P(beat) dá +202 \[−35; +402\] e o *gap* +132 \[−4; +269\]. Nenhum exclui zero.

- **As odds sabem prever o *beat*:** o Brier é 0,141, contra 0,156 do histórico da empresa e 0,154 da taxa constante (81% de beats). O problema é que o *beat* binário explica pouco do retorno, porque o guidance e a surpresa face ao preço já descontado mandam mais.
- **O *gap* é a tradução direta do vídeo:** preço de mercado contra um *fair value* calculado. Não há evidência de que o desvio preveja a ação. No vídeo, o subjacente (BTC) é observável em tempo real e o contrato converge para ele. Aqui, o contrato binário não é o ativo que negocias.
- **Próximo passo lógico:** com mais um ano de dados, o IC estreita cerca de √2. Vale a pena continuar a gravar as odds a partir de agora, mas não usá-las como filtro em fevereiro.

### O que os dados não resolvem

O maior risco para 2027 não é o DD, é o backtest estar otimista por razões de dados. Nenhum destes pontos se resolve com mais testes sobre os mesmos ficheiros.

- **Datas de R:** em 69% dos eventos, o maior movimento residual entre R−1, R e R+1 cai em R. Cai em R+1 em 20% e em R−1 em 11%. Atualização: a comparação com as datas da SEC (secção própria) mostra que isto é sobretudo comportamento natural do preço, e não datas erradas. As duas fontes concordam em 92,5% dos eventos e, quando discordam, o preço dá mais vezes razão ao yfinance. O calendário Nasdaq confirma a data (±5 sessões) em 92,6% dos casos, mas devolve "time-not-supplied" para quase todo o histórico, por isso não verifica BMO/AMC.
- **Sobrevivência:** o universo é a interseção entre os constituintes atuais das listas pop4 e o que hoje está cotado na Nasdaq (550 de 1.505). Empresas falidas, adquiridas ou que mudaram de bolsa não entram. O sentido provável do viés é inflacionar a média, mas a magnitude é desconhecida.
- **Execução:** o fecho Yahoo não é o NOCP, e o paper da IBKR simula os fills à sua maneira. O atraso de 15 min não afeta o preço MOC, mas afeta o dimensionamento (por isso uso o fecho de R−3).
- **Opções na Drive:** os ficheiros Cboe são amostras de um só dia (OptionTrades 07/01/2026, OptionQuotes, EOD Calcs 25/08/2023, TBT C1). Não dão para construir o painel de *implied move* por evento que o teste do vídeo exigiria.
- **Dados que não consegui:** o FRED deu timeout a partir do GitHub (não fez falta), e o Kalshi horário ainda estava a ser recolhido.

### O que testar a seguir

Deixar de procurar filtros de sentimento e gastar o tempo nos dados que podem estar a inflacionar o backtest. Testei mais uma ideia: dimensionar cada posição pelo inverso do risco idiossincrático. Piorou o Sharpe de 1,61 para 1,26 com a mesma exposição média, porque o prémio está nos nomes mais voláteis. Fica descartada.

1. **Bloomberg na sexta, 6/11, por esta ordem.** Primeiro, datas e horas históricas dos anúncios para todo o universo (ou uma amostra estratificada de \~100 nomes), para medir quantos R estão errados e refazer a EAP com as datas certas. Segundo, membros históricos dos índices, incluindo deslistadas, para medir o viés de sobrevivência. Terceiro, *implied move* pré-earnings (IV das opções antes e depois): é o único teste fiel ao vídeo, comparando o *implied move* com o movimento histórico nos earnings e verificando se o prémio EAP depende desse desvio.
2. **Teste-sombra a partir de hoje até 31/01.** Calendário forward (WSH na IBKR, se disponível), lista diária de candidatos, trades teóricos MOC e, em paralelo, Δ7 da Fed e odds de EPS com as regras congeladas. Critério de corte, escrito já: se mais de 5% dos trades tiverem a data errada, ou se o fill simulado se desviar do fecho oficial em mais de 10 bps em média, corrigir antes de fevereiro. O alfa não é medido aqui, porque 3 meses não chegam (desvio de \~8% por evento).
3. **Período de testes de janeiro na conta WIC.** Verificar se o MOC no paper preenche às 16:00 ao fecho, se o short de QQQ está disponível e qual o custo, como a IBKR conta a margem de 2× com o hedge, e o que acontece a ordens rejeitadas ou a halts.
4. **Papel do LLM que cumpre a regra e se consegue validar.** Confirmar data e hora no comunicado de relações com investidores de cada empresa antes de R−2 (ataca o maior risco, o calendário). Vetar situações especiais: fusão pendente, halt, reverse split, anúncio adiado. Registar a justificação. Não lhe dar poder sobre tamanho ou hedge sem evidência.
5. **Exposição em fevereiro.** Com 80% de alocação, fevereiro tem em média 28 posições (45% do NAV em ações, com picos de 50) e março apenas 4 (6% do NAV): quase todo o retorno vem de fevereiro. Testar se vale a pena subir o $/slot quando há poucos candidatos, mantendo o mesmo teto de stress, antes de fixar a regra.

### AMC vs BMO

As ações AMC rendem mais por evento, mas a vantagem caiu desde 2020 e em carteira um filtro só-AMC piora fev–mar. Esta comparação é exploratória, porque a diferença foi vista primeiro na tabela da amostra completa.

| Teste | AMC − BMO, bps por evento \[IC95% semanal\] |
| --- | --- |
| 2014–out 2026 (14.850 AMC, 7.964 BMO) | +33,0 \[+11,9; +57,7\] |
| 2014–2019 | +53,2 \[+23,1; +84,2\] |
| 2020–2026 | +18,4 \[−15,6; +49,9\] |
| Terço menos volátil (risco idiossincrático) | +5,9 \[−17,4; +30,2\] |
| Terço mais volátil | +58,7 \[+0,1; +115,8\] |

- **Parte é risco:** o prémio EAP sobe com a volatilidade da ação, e nas ações calmas AMC e BMO são quase iguais. Por unidade de desvio diário, AMC continua à frente (0,27 vs 0,13), por isso não é só risco.
- **Por ano:** AMC ganha em 10 de 13 anos, mas perde em 2014, 2021 e 2024.
- **Hora 16:00:** 90% dos AMC têm hora exatamente 16:00 no yfinance (+71 bps) e os restantes +56 bps. Não há sinal de que a hora por defeito esteja a criar o efeito.
- **Em carteira (K=50, 2014–2026, 3 sementes):**

| Política | Exposição bruta média | Sharpe contínuo | Fev–mar médio | Pior ano fev–mar | Pior DD fev–mar |
| --- | --- | --- | --- | --- | --- |
| Todos, 80% | 0,22 | 1,61 | +3,5% | −1,0% | −3,5% |
| Só AMC, 80% (mesmo $/slot) | 0,17 | 1,68 | +2,1% | −1,3% | −3,5% |
| Só AMC, 120% (mesma exposição) | 0,22 | 1,69 | +3,1% | −2,9% | −5,4% |

Os BMO têm média positiva e diversificam: tirá-los reduz o retorno da competição e alarga a cauda. Se quiseres explorar, a variante defensável é uma inclinação moderada (por exemplo, 1,25× o tamanho em AMC), fixada agora e avaliada só em dados futuros.

### Garantia de DD desde o máximo

As regras da primeira versão (cap por nome, travar a −8%) não garantiam nada contra um salto noturno das posições já abertas. Esta regra dá uma garantia condicional e, a 80%, quase não custa retorno.

**Regra:** só aceitar uma posição nova se *choque* × (nocional longo aberto + novo) ≤ NAV − (1 − 12%) × NAV máximo. O máximo é o pico do NAV desde o início, que é como a competição mede. Os 12% são 15% menos uma margem de 3% para intradiário e deslizes do hedge. Cada posição atravessa o seu anúncio uma única vez, por isso o pior caso do livro aberto é *choque* × nocional. Enquanto a perda média do livro inteiro não passar de *choque* e o hedge QQQ funcionar, o DD desde o máximo não passa de 12%.

| Alocação / regra | Retorno anual (base) | Sharpe | Pior DD 2014–2026 | Fev–mar médio | Pior DD fev–mar | Fev–mar médio, custos stress |
| --- | --- | --- | --- | --- | --- | --- |
| 80%, sem regra | 11,5% | 1,61 | −5,7% | +3,5% | −3,5% | +2,7% |
| **80%, choque 15%** | **11,5%** | **1,62** | **−5,3%** | **+3,5%** | **−3,5%** | **+2,7%** |
| 80%, choque 25% | 10,9% | 1,60 | −5,1% | +2,7% | −3,9% | +2,0% |
| 120%, sem regra | 17,5% | 1,64 | −7,1% | +5,1% | −5,0% | +3,9% |
| 120%, choque 15% | 16,5% | 1,58 | −7,5% | +4,3% | −7,7% | +3,4% |

- **Choque 15%:** é cerca de 2× a pior média de uma noite (−7,7% em 14 eventos a 27/01/2026). **Choque 25%:** é o percentil 1% de um evento isolado aplicado a todos.
- **Porque quase não custa:** a 80%, com DD 0, a regra permite até 80% do NAV em ações, e o livro raramente chega lá. A regra só aperta quando já há perdas. A −8% desde o máximo, o teto passa a \~27% do NAV.
- **O que a regra não cobre:** falha simultânea do hedge e do mercado, falha técnica (posição sem hedge ou ordem duplicada) e uma perda média do livro acima do choque. As duas primeiras resolvem-se com verificações determinísticas de execução, não com mais modelos.
- **Nota:** a 120% a regra corta entradas nos picos e muda a sequência de eventos, por isso o pior DD histórico pode até piorar. A garantia é sobre o cenário de stress, não sobre cada trajetória passada.

### Camadas de de-risking, falha do hedge e puts

Nenhuma camada melhora o histórico de forma visível, porque o histórico nunca se aproximou dos limites. O que conta é o que cada uma faz nos cenários que ainda não aconteceram. Mesmo motor: K=50, 80%, custos base, 3 sementes.

| Configuração | Retorno anual | Sharpe | Pior DD 2014–26 | Fev–mar médio | Pior ano fev–mar | Pior DD fev–mar (fecho / intradiário) |
| --- | --- | --- | --- | --- | --- | --- |
| Base 80% | 11,5% | 1,61 | −5,7% | +3,5% | −1,0% | −3,5% / −7,1% |
| Throttle do repo (H ou C4), DD desde o máximo, limite 15% | igual | igual | igual | igual | igual | igual |
| Regra de stress 15% | 11,5% | 1,62 | −5,3% | +3,5% | −1,2% | −3,5% / −7,1% |
| Regra de stress 15% + throttle H | igual à de cima |  |  |  |  |  |
| Inclinação AMC 1,25× | 11,8% | 1,65 | −5,5% | +3,5% | −1,1% | −3,8% / −7,2% |
| 10% dos hedges falham e ficam sem hedge | 11,8% | 1,67 | −5,5% | +3,5% | −1,3% | −3,9% / −7,0% |
| 10% falham, hedge alternativo na abertura seguinte | 11,6% | 1,63 | −5,7% | +3,5% | −1,0% | −3,6% / −7,4% |
| 10% falham, cancelar a compra | 9,9% | 1,43 | −6,3% | +3,2% | −1,5% | −3,4% / −7,4% |

- **Throttle do repo:** o DD nunca chegou a 7,5%, por isso nunca disparou. É seguro grátis: manté-lo, mas medido desde o pico do NAV e não desde o capital inicial como no código FTMO.
- **Falha do hedge em crash (todos os hedges falham), fev–mar 2020:** pior DD −2,9% com hedge, −7,9% sem hedge e −4,5% com o hedge alternativo na abertura seguinte. Em 2025 (crash de abril), ficar sem hedge até teria ajudado, porque o hedge perde quando o mercado recupera. A regra recomendada é nunca dormir sem hedge: se o short de QQQ falhar, entra SQQQ ou puts de QQQ na abertura seguinte. Cancelar a compra protege tanto como o alternativo, mas custa 1,6 pp/ano.
- **Puts de QQQ como seguro de cauda (aproximação):** puts 10% fora do dinheiro a 30 dias, renovados, valorizados com Black-Scholes e a vol do QQQ estimada a partir do VIX, porque não puxei o histórico de opções do QQQ. Com puts sobre 50% do NAV, o custo médio por janela foi −0,03 pp e em 2020 renderam +3,0%. Mas o Black-Scholes subavalia puts OTM, por isso o custo real deve ser várias vezes maior. Há ainda um efeito perverso com DD desde o máximo: o put dispara, cria um novo pico, e a devolução conta como DD (com 100% do NAV em puts, o pior DD fev–mar piorou para −6,2%). Antes de usar, testar com preços reais de opções do QQQ (a mesma base DoltHub deve ter).
- **LLM a escolher a mistura AMC/BMO:** não se consegue validar historicamente, porque o modelo conhece o passado. A inclinação fixa de 1,25× deu +0,3 pp/ano e Sharpe 1,65 contra 1,61, mas pior DD fev–mar (−3,8% vs −3,5%). Se usares, fixa-a já. O LLM pode escolher entre 1,0× e 1,25× com uma regra escrita, avaliada só em dados novos.

### Δ7 > 0 no QQQ

O DD mais baixo da regra "long QQQ só quando Δ7 > 0" vinha de estar fora do mercado em \~75% dos dias, não do sinal. Esta regra é timing do QQQ sozinho e não mexe na EAP. Comparei-a com 5.000 placebos que mantêm o mesmo padrão de dias dentro/fora, apenas deslocado no tempo. Usei o sinal Polymarket, porque o "consenso" anterior exigia Kalshi e Polymarket no mesmo dia.

| Período | Dias investidos / total | Retorno da regra | DD da regra | DD mediano do placebo | % placebos com DD melhor |
| --- | --- | --- | --- | --- | --- |
| Set/2024–jul/2026 (janela anterior) | 176 / 396 | +23,0% | −17,8% | −15,0% | 67% |
| **Dez/2022–ago/2024 (holdout)** | **113 / 258** | **+6,2%** | **−15,7%** | **−8,3%** | **98%** |

No período novo, a regra teve um DD pior do que 98% das escolhas aleatórias de dias. O −6,7% do relatório anterior era específico da amostra de 117 dias com as duas fontes. Não recomendo usar Δ7 para gerir o DD.

### Datas SEC 8-K vs yfinance

A EAP sobrevive à troca de calendário, e o yfinance revelou-se melhor do que eu tinha suposto. Corri o `ingest_sec_earnings.py` do repo, que usa a hora de submissão do 8-K Item 2.02 com a identificação exigida pela SEC: 545 ações e 26.443 eventos.

|  | yfinance | SEC 8-K |
| --- | --- | --- |
| Mesmo R nos 25.312 eventos emparelhados | 92,5% |  |
| Quando discordam, o maior movimento cai no R de… | **62%** | 28% |
| Eventos com o maior movimento em R (total) | 69% | 66,5% |
| Média coberta por evento, base WIC 2014–out 2026 | +58,0 bps \[+44,1; +72,5\] | +55,6 bps \[+40,6; +70,1\] |
| AMC / BMO | +69,5 / +36,5 | +65,2 / +33,6 |
| Carteira 80%, fev–mar médio / pior ano / pior DD | +3,5% / −1,0% / −3,5% | +2,9% / −1,6% / −3,9% |

- **Discordâncias (7,5%):** a maioria são casos em que a SEC põe R um dia depois (895). Isso acontece quando o 8-K é submetido horas depois do comunicado, um problema que o próprio ingest documenta. Nesses casos o preço dá razão ao yfinance.
- **Correção ao que escrevi antes:** os 69% de eventos com o maior movimento em R não são sobretudo datas erradas. Parte do movimento acontece naturalmente em R−1 ou R+1 (fugas de informação e deriva pós-anúncio), e com a SEC a percentagem é até menor.
- **Para a competição:** cerca de 7,5% dos eventos têm data ambígua entre duas fontes credenciadas. O sistema ao vivo deve exigir que o calendário forward (WSH) e o comunicado da empresa concordem antes de abrir. É uma tarefa natural para o LLM: ler o anúncio da data no site de relações com investidores.

### Opções: o teste do vídeo e o sentimento das opções

O preço das opções antes dos earnings está certo em média. O desvio face ao histórico da ação não prevê nada e, depois de pagar o spread, negociar straddles perde muito. O skew também não funciona como sentimento. Os dados são cadeias diárias de fecho com bid/ask por strike, da base pública DoltHub `post-no-preference/options`. Encontrei cadeia até R−2 para 11.149 eventos. Depois dos filtros de qualidade (vencimento até R+21 dias, strike a menos de 5% do preço, spread < 50%) ficaram 4.991 eventos, de 440 ações, entre mai/2019 e nov/2026, 1.059 deles em fev–mar.

- **Preço de mercado** = straddle ATM / preço, retirando a parte de volatilidade normal até ao vencimento. **Fair value** = movimento médio da ação nos 8 earnings anteriores. **Desvio** = mercado / fair − 1. Tudo isto foi definido antes de os dados chegarem.

| Teste | Resultado | Veredicto |
| --- | --- | --- |
| Quem prevê melhor o movimento real? | Erro médio: mercado 4,34%, histórico 4,23%. Correlação 0,34 vs 0,33; juntos explicam mais. O mercado pede 6,95% e o movimento real médio foi 6,58% | Empate. As opções sobrestimam um pouco |
| O desvio prevê o retorno EAP? (terço alto − baixo) | +15 bps \[−50; +86\] | Morto |
| Comprar straddle ao ask, vender ao bid no fecho de R | Média −22%, mediana −31%, ganha em 20% | Perde |
| Vender straddle ao bid, recomprar ao ask | Média −27%, pior 1% −223%, pior −407% | Perde, com cauda enorme |
| O mesmo ao preço médio, sem spread | −0,6% | Preço justo |
| Desvio para escolher straddles | −2,1 pp \[−6,0; +1,5\] | Morto |
| **Sentimento: skew** (IV put 25Δ − IV call 25Δ) vs retorno EAP | +28 bps \[−31; +85\], sinal contrário ao da literatura; 4.443 eventos | Morto |

- **O spread é o que mata:** o straddle custa 16% do prémio em ida e volta (mediana 14%) nos preços de fecho. Mesmo que na prática seja metade disso, não há margem, porque a média ao preço médio é zero.
- **Porque o vídeo não se transpõe:** no BTC de 15 minutos, o *fair value* vem de um preço à vista que muda ao segundo e o contrato converge para ele. Aqui o "fair value" é uma média de 8 trimestres, que o mercado de opções já usa e melhora.

### Informação dos pares do setor (a parte transponível do vídeo)

Os pares que já anunciaram ajudam a prever o tamanho do movimento, mas não a direção do retorno EAP. O sinal é construído assim: ações do universo com o mesmo SIC de 2 dígitos (fonte: SEC) cuja reação aos earnings ocorreu entre 10 e 1 sessões antes de R−2, com pelo menos 3 pares. Só usa fechos até R−3, por isso não depende do atraso de 15 minutos. Os tercis foram cortados em 2014–2021 e a hipótese tinha de se confirmar em 2022–2026. Houve 12.799 eventos com pares suficientes (mediana de 3 pares).

| Hipótese | Desenvolvimento 2014–2021 | Confirmação 2022–2026 | Veredicto |
| --- | --- | --- | --- |
| H1: reação média dos pares prevê o retorno EAP (tercil alto − baixo) | +36 bps \[−17; +87\] | +41 bps \[−30; +111\] | Morto pelo critério, embora o sinal seja o mesmo nos dois períodos |
| H3: reversão (Thomas–Zhang), retorno próprio nos 10 dias anteriores | +21 bps \[−27; +67\] | +38 bps \[−39; +110\] | Morto, e com o sinal contrário ao da reversão |
| H2: tamanho médio dos movimentos dos pares prevê o movimento próprio, além das opções | coeficiente 0,15 \[0,05; 0,26\] em 2.359 eventos (Holm p < 0,001) |  | Passa |

- **Uso prático de H2:** risco, não retorno. Na regra de stress, o choque de cada posição pode passar a ser o movimento esperado (opções + pares) em vez de um valor fixo. Isso aperta o orçamento nas semanas em que os pares estão a mexer muito, por exemplo quando um setor inteiro está a desapontar. Ainda não testei esta variante na carteira.
- **H1 merece ser seguido daqui para a frente** com a mesma regra congelada: a direção (continuação) repetiu-se nos dois períodos, mas não com força suficiente para a usar em fevereiro.

**Contexto que poderia limpar o sinal H1** (3 variantes fixadas antes, mesma divisão desenvolvimento/confirmação, Holm sobre 3):

| Variante | 2014–2021, alto − baixo | 2022–2026 | p Holm |
| --- | --- | --- | --- |
| V1 pares mais próximos (SIC 3 dígitos, ≥ 2) | +12 bps \[−52; +73\] | +1 bps \[−82; +90\] | 1,00 |
| V2 mais pares (≥ 5) | +51 bps \[−10; +109\] | +55 bps \[−24; +130\] | 0,51 |
| V3 pares concordantes (≥ 2/3 com o mesmo sinal) | +40 bps \[−48; +126\] | +22 bps \[−85; +138\] | 1,00 |

Nenhuma passa. Com ≥ 5 pares, o efeito é o mais estável (+51 e +55 bps), mas continua dentro do ruído. Procurar mais cortes até um sair significativo seria *data mining*. A forma honesta é congelar V2 e medi-lo nos earnings de janeiro e fevereiro.

### U2 em paralelo com a EAP

O U2 do repo passa o teste no QQQ e melhora o Sharpe do conjunto, mas a 2% de risco por trade piora demasiado o DD de fev–mar. A 1% fica no limite do critério. O U2 original foi validado em US500/SPY, e o SPY não é negociável na WIC (não está cotado na Nasdaq). Portei-o para o QQQ em barras diárias. Sinal: IBS < 0,10 no fecho. Entrada na abertura seguinte com stop a 1,5× ATR14. Saída na 3.ª abertura. Uma posição de cada vez. O sinal só usa o fecho, por isso não depende do atraso de 15 minutos.

|  | Retorno anual | Sharpe | Pior DD 2014–26 | Fev–mar médio | Pior DD fev–mar |
| --- | --- | --- | --- | --- | --- |
| EAP 80% | 11,8% | 1,66 | −5,7% | +3,5% | −3,5% |
| U2-QQQ, 2% de risco (pré-registado) | 7,8% | 1,01 | −8,1% | +0,9% | −8,4% (2018) |
| EAP + U2 2% | 19,6% | 1,87 | −7,9% | +4,4% | −7,2% |
| EAP + U2 1% (exploratório) |  | 1,94 | −6,8% | +3,9% | −4,5% (2021) |

- **O U2-QQQ tem edge próprio:** 261 trades desde 2014, R médio +0,23 \[+0,12; +0,35\], igual em 2014–19 e 2020–26, e correlação diária com a EAP de 0,0.
- **Veredicto pelo critério fixado:** passa no edge e no Sharpe, mas falha o DD de fev–mar a 2% (3,7 pp pior, para um limite de 1 pp). A 1% fica 0,95 pp pior, mas esse tamanho foi escolhido depois de ver os resultados.
- **Riscos específicos:** o U2 é long de mercado (compra quedas). Num crash com um salto através do stop, perde mais do que o risco nominal (fev 2018: −6,8% na janela a 2%). Na regra de stress, o U2 tem de contar com um choque de mercado próprio (por exemplo 12%, o pior dia do QQQ desde 2014). Ponto prático: o long de QQQ do U2 compensa parte do short de QQQ do hedge da EAP. Na conta, as duas posições compensam-se, o que poupa margem e comissões.

#### EAP + U2 na mesma conta: alavancagem, DD e camadas

A combinação cabe nos limites da WIC desde que as duas pernas de QQQ fiquem compensadas na conta, e o DD máximo fica longe de 15%. A melhor variante é EAP 80% + U2 a 0,5% com regra de stress e throttle. Tudo corre num só simulador: NAV partilhado, DD desde o máximo, regra de stress e throttle sobre o livro inteiro, U2 dimensionado sobre os $1M iniciais. Usei o choque de 15% para a EAP e de 12% para o U2 (o pior dia do QQQ desde 2014).

| Configuração (K=50) | Retorno anual | Sharpe | Pior DD 2014–26 | Fev–mar médio | Pior ano fev–mar | Pior DD fev–mar (fecho / intradiário) | Bruto máx. (QQQ compensado / sem compensar) | Crash no mesmo dia\* |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| A EAP 80% | 11,5% | 1,61 | −5,7% | +3,5% | −1,0% | −3,5% / −7,1% | 1,66× / 1,66× | −6,1% |
| B + U2 1% | 15,9% | 1,94 | −6,8% | +3,7% | −2,4% | −4,7% / −8,4% | 1,64× / **2,18×** | −13,0% |
| C + U2 2% | 19,4% | 1,87 | −7,9% | +3,9% | −5,5% | −6,7% / −9,7% | 1,63× / **2,57×** | −17,2% |
| D = B + regra 15% (+ throttle: igual) | 15,8% | 1,94 | −6,2% | +3,4% | −4,4% | −5,9% / −7,0% | 1,53× | −9,7% |
| H = D + 10% dos hedges falham, alternativo | 15,9% | 1,96 | −6,3% | +3,4% | −4,3% | −5,8% / −7,1% | 1,52× | −9,7% |
| I EAP 65% + U2 1% + regra + throttle (exploratório) | 13,6% | 1,94 | −5,2% | +2,8% | −4,1% | −5,3% / −6,5% | 1,34× | −10,1% |
| **J EAP 80% + U2 0,5% + regra + throttle (exploratório)** | **13,7%** | **1,86** | **−5,4%** | **+3,4%** | **−2,5%** | **−4,0% / −7,0%** | **1,54×** | **−7,8%** |

\* O pior dia do histórico em que, ao mesmo tempo, o QQQ abre −12% através do stop com o U2 aberto e o livro EAP perde 7,7% em média (a pior noite real).

- **Alavancagem:** o limite overnight da WIC é 2× (Reg T 50%). Com o QQQ compensado, o pico é 1,64× (margem \~82% do NAV) e cabe. Sem compensar, B e C passam de 2×. Na IBKR uma conta tem uma única posição de QQQ, por isso a compensação é automática, mas o executor tem de calcular a ordem líquida. O limite intradiário de 4× e o de short de 2× ficam folgados.
- **Bootstrap (20.000 janelas de 36 sessões, época de earnings):** P(DD > 15%) foi 0,00% em todas as variantes com o edge histórico. Com o edge a zero, foi 0,01% em B, 0,09% em C e 0,00% em D.
- **Camadas:** o throttle nunca dispara. A regra de stress melhora o DD contínuo e limita o crash, mas em fev–mar raciona a EAP enquanto há um U2 aberto. A 80% de EAP, a regra de 15% fica quase toda gasta pela própria EAP, por isso para caber U2 é preciso baixar um dos dois (variantes I e J).
- **Para a competição:** o U2 melhora muito o Sharpe anual, mas em fev–mar acrescenta pouco retorno médio (+0,2 pp a 1%) e mais cauda. O ganho é sobretudo fora da janela. Se entrar, J é o equilíbrio: o mesmo retorno fev–mar que a EAP sozinha, melhor DD contínuo e um crash limitado a −7,8%.

#### Testes de robustez do U2

**Regra de stress com prioridade à EAP (passa).** A regra continua a limitar o livro inteiro, mas as entradas da EAP nunca são bloqueadas por um U2 aberto. O U2 só recebe o orçamento que sobra depois de reservar o livro EAP atual e as entradas já no calendário para as 3 sessões seguintes. O calendário é conhecido antes, por isso não há lookahead. Critério fixado antes de correr: fev–mar ≥ 3,4%, crash no mesmo dia melhor que −10% e pior DD fev–mar ≤ 4,5%.

| EAP 80% + regra com prioridade EAP + throttle | Retorno anual | Sharpe | Pior DD 2014–26 | Fev–mar médio (base / stress) | Pior ano fev–mar | Pior DD fev–mar (fecho / intradiário) | Crash no mesmo dia |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **P1: + U2 1%** | **15,6%** | **1,92** | **−6,0%** | **+3,6% / +2,8%** | **−1,6%** | **−4,4% / −7,1%** | **−9,8%** |
| P2: + U2 0,5% | 13,6% | 1,84 | −5,4% | +3,6% / +2,7% | −1,6% | −3,9% / −7,1% | −7,6% |
| referência: EAP 80% sozinha | 11,5% | 1,61 | −5,7% | +3,5% / +2,7% | −1,0% | −3,5% / −7,1% | −6,1% |

As duas variantes passam. A P1 é a recomendação: mais Sharpe e o mesmo retorno de fev–mar que a EAP sozinha, com um crash limitado a −9,8% por construção.

**U2 em 1999–2013, período que nenhum teste tinha usado (passa, mas mais fraco).**

|  | Trades | R médio \[IC95%\] | 1999–2002 | 2003–07 | 2008–09 | 2010–13 | DD máx. isolado a 1% | Fev–mar 2000–13 a 1%: média / pior DD |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| QQQ | 356 | +0,10 \[+0,02; +0,19\] | +0,05 | +0,05 | +0,19 | +0,21 | −9,4% | +0,7% / −3,3% (2001) |
| SPY | 338 | +0,13 \[+0,04; +0,22\] | +0,00 | +0,22 | +0,21 | +0,15 | −10,8% | +0,3% / −3,9% (2001) |

No QQQ, o edge de 1999–2013 é metade do de 2014–2026 (+0,23) e quase nulo em 1999–2007. Convém contar com algo entre os dois. Mesmo assim, o U2 sobreviveu ao crash das dotcom e a 2008 com DD isolado < 10% a 1% de risco.

**U2 com barras de 15 minutos, como no repo (passa).** Reconstruí a sessão cash (09:30–16:00 NY) a partir de M1 da Dukascopy, com a regra de sessão válida do `u2_trader.py`. Usei o CFD do Nasdaq-100 (NSXUSD) e o do S&P 500 (SPXUSD) em 2014–2026.

|  | Trades | R médio \[IC95%\] | Acerto |
| --- | --- | --- | --- |
| NSXUSD, sessão M15 | 255 | +0,25 \[+0,13; +0,37\] | 59% |
| SPXUSD, sessão M15 | 257 | +0,22 \[+0,10; +0,34\] | 60% |
| QQQ, barras diárias (versão testada na carteira) | 261 | +0,23 | 59% |

Os sinais coincidem em 90% dos casos. Nos 235 trades comuns, a correlação do resultado é 0,95 (R médio +0,28 em M15 vs +0,26 em diário). A versão diária é uma boa aproximação, e com o feed de 15 minutos de atraso o sinal pode ser calculado no fecho sem perda.

**Espaço na carteira (exploratório).** Deixei o U2 crescer até 1,5% ou 2% de risco sempre que a regra de stress tivesse orçamento livre, sobretudo em março, quando a EAP está quase parada. O retorno fev–mar mal muda (+3,62% → +3,63% / +3,67%) e a cauda piora: o pior ano passa de −1,6% para −2,4% / −3,2% e o crash no mesmo dia de −9,8% para −11,3%. Em fevereiro o orçamento de risco já está quase todo usado pela EAP. Em março o U2 rende \~0,9% seja qual for o tamanho. Na prática, a carteira EAP 80% + U2 1% está cheia em risco, embora não em margem (pico de 1,52× contra o limite de 2×).

### Torneio: regras oficiais da WIC2026

O objetivo é ficar em 1.º lugar, não maximizar o Sharpe, e isso muda o que conta como boa estratégia. Fonte: *WIC2026 Participant Overview* (JPSI, 22/10/2026). A equipa entra na Divisão AI Agent; o que não está na página dessa divisão segue a Divisão Trader (*"All other regulations are the same as those for the Trader Division"*).

| Regra | Divisão AI Agent |
| --- | --- |
| Período | 1/fev–25/mar 2027; liquidação obrigatória às 15:50 ET de 25/mar |
| Conta | 1 conta paper IBKR de US$1M por equipa (Reg T); no máximo 15 equipas |
| Dados | Atraso de 15 minutos |
| LLM | Tem de decidir em tempo real; *"AI writes code that trades on fixed rules"* não conta |
| Instrumentos | Ações, ETFs e opções cotados na Nasdaq (pela regra geral; o topo da página diz *"trades U.S. equities"*) |
| Alavancagem | 4× intradiário, 2× overnight, short até 2× |
| Desclassificação | DD máximo de 20% ou mais (não diz se é medido ao fecho ou intradiário) |
| Ranking | RRF ponderado: 70% desempenho, 30% relatório |
| Relatório | *"Persuasiveness of return hypothesis, soundness of design, and consistency between strategy and actual behavior (verified against the record of LLM calls)"* |
| Prémio | Só o vencedor (subscrição anual de ChatGPT Pro ou Claude Max) |
| Inscrição | Até 15/nov/2026; o rulebook chega depois, pelo grupo de WhatsApp |

O que isto muda face ao que se assumia:

- **Os +30% não são a referência.** Os resultados de 2025 (LMU +33,3%, TU +14,0%, Genebra +1,2%) são da Divisão Trader, com traders humanos. A Divisão AI Agent é nova e não tem histórico.
- **O DD limite é 20%, não 15%.**
- **Só a posição conta.** O RRF usa a posição em cada ranking, não a margem: ganhar por muito vale o mesmo que ganhar por pouco. Com o k típico de 60, um 3.º lugar em desempenho com o melhor relatório bate um 1.º com relatório fraco (0,0160 contra 0,0159).
- **O SPY não é negociável** (está na NYSE Arca). Aqui só serve como dados de calibração.

### Porque a EAP sozinha não ganha

A EAP 80% nunca chega a +10% em fev–mar: o melhor ano foi +8,4% e a média é +3,5%. Se o vencedor fizer 10% ou mais, nenhum filtro na EAP resolve isso. Todos os testados (Fed, odds de EPS, AMC/BMO, pares, skew) mexiam em décimas de ponto percentual, e mesmo no limite de 2× a EAP fica à volta de +5%.

Num torneio onde só o 1.º conta, o que dá hipótese de ganhar é a variância gasta dentro do orçamento de DD. Num passeio aleatório sem edge e sem limite de tempo, a probabilidade de subir X antes de cair D desde o pico é e^(−X/D) em log: para +30% com D = 20%, dá cerca de 31%. A EAP usa menos de 4 pontos dos 20 de DD disponíveis.

A EAP continua a valer a pena, mas noutro papel: é o motor de alfa (+3,5% de média) por baixo de uma camada que gasta o resto do orçamento de DD.

### Camadas de risco por cima da EAP

Com valores realistas, uma camada por cima da EAP leva a P(acabar ≥ +15%) de 0% para 17–44%, quase sem desclassificação. Todas têm lock: ao chegar ao alvo, a camada fecha e fica só a EAP. Todas têm um piso de segurança a 88% do pico (ver a secção do drawdown).

| Camada | Como funciona |
| --- | --- |
| QQQ até 2×, ajustado à vol | Exposição long = folga até ao piso / (4 × vol diária do VXN), até ao limite de 2×. O long compensa o short de QQQ do hedge da EAP. Lock a +15% |
| TQQQ até 4,5×, ajustado à vol | O mesmo com k = 3 e exposição até 4,5× o QQQ. Lock a +15% |
| Calls de QQQ | Calls \~5% OTM com vencimento em março, 10% do NAV no início de fevereiro. Regra de venda diária. Lock a +20% |

**Método.** P&L diário real da EAP 80% em cada janela fev–mar 2014–2026 (3 sementes, `sim.py` da auditoria), mais janelas contínuas reais de 36 sessões do QQQ 2012–2026 com o Low intradiário e o VXN. As calls são avaliadas com Black-Scholes a 0,80 × VXN e spread de 2%, calibrados na secção seguinte. Tudo foi repetido com o QQQ sem tendência, porque 2012–26 foi um mercado em alta forte.

&#91;embedded content: curva\_final.csv (wic\_torneio\_20261105) · 40.000 janelas contínuas do QQQ 2012–26 × janelas fev–mar reais da EAP 2014–26 · calls a 0,80× VXN · piso 88%\]

A melhor camada depende de quanto será preciso para ganhar. Até +15%, o TQQQ é a melhor camada. O QQQ até 2× fica sempre abaixo do TQQQ e só bate as calls até \~+12%, porque as calls perdem o prémio muitas vezes. A partir de +20%, as calls são a única camada com probabilidade razoável. Se bastarem \~8%, a EAP sozinha é a melhor escolha: P(≥ 8%) = 13%, P(≥ 6%) = 23%, quase sem risco.

O que se aprendeu pelo caminho:

- **Exposição proporcional à folga com m fixo desclassificava em 2020 e 2022.** Quedas de −4% a −12% num dia atravessavam o piso. Dividir pela vol do VXN resolveu: nenhuma desclassificação nas 13 janelas reais.
- **A regra de venda das calls é obrigatória.** Todos os dias, se o valor das calls passar NAV − piso × pico, vende-se o excesso. Sem ela, em 2023 as calls levaram o pico a +24% num dia e evaporaram em duas semanas com o QQQ no mesmo sítio: DD de −21,8% e desclassificação. Aconteceu em 4 das 13 janelas reais. Com a regra, a P(+30%) quase não muda e a desclassificação vai a 0%.
- **O strangle e as puts sozinhas foram piores.** Dividir o prémio impede que qualquer das pernas chegue ao alvo.
- **As calls não melhoram o retorno esperado.** Sem tendência, a média desce de +3,5% para \~+2%, a mediana fica negativa e perde-se em 55–70% das janelas. A única coisa que compram é P(≥ 20%).

### Calls: verificação com opções reais do SPY

Calls reais do SPY \~5% OTM, compradas ao ask e seguradas até ao vencimento, renderam +46% do prémio em 2020–2026 e −25% sem a tendência de subida. O simulador só reproduz isto com IV ≈ 0,80 × o índice de vol. A DoltHub não tem cadeias do QQQ, por isso a calibração é feita no SPY face ao VIX e aplicada ao QQQ face ao VXN.

O teste usa 73 compras mensais: o 1.º dia disponível de cada mês, de jan/2020 a set/2026, a \~8 semanas do vencimento. O ganho no vencimento só depende do fecho do SPY, por isso não há modelo nenhum pelo meio.

| Calls do SPY | ATM | 3% OTM | 5% OTM |
| --- | --- | --- | --- |
| IV real / VIX (mediana) | 0,87 | 0,74 | 0,70 |
| Spread (ask − bid) / mid | 0,4% | 0,8% | 1,3% |
| Preço do modelo a 0,70× / ask real | 0,77 | 0,82 | 0,93 |
| Preço do modelo a 0,95× / ask real | 1,04 | 1,41 | 1,92 |
| Resultado real (soma ganhos / soma prémios − 1) | +21% | +36% | +46% \[IC95% +4%; +84%\] |
| Resultado real sem a tendência (+13,7%/ano) | −22% | −25% | −25% |
| Compras que pagaram alguma coisa | 63% | 44% | 30% |

- **Como preço, 0,70× está quase certo** (93% do ask real). A versão "conservadora" de 0,95× punha as calls a quase 2× o preço real.
- **O que era otimista era o simulador antigo.** Montava trajetórias do QQQ com blocos de 5 dias de anos diferentes, o que exagera a dispersão a 7 semanas (7,0% contra 6,3% em janelas contínuas). As calls OTM são muito sensíveis a isso. Sem tendência, a 0,70×: blocos +54%, janelas contínuas do QQQ −2%, SPY real −25%.
- **Nos blocos, os 0,95× acertavam por acaso** (−22% / +48% contra −25% / +46%): opções demasiado caras compensavam a dispersão exagerada. Os números deste doc usam janelas contínuas com 0,80×, que é onde o simulador reproduz o SPY real.

### Drawdown com valores realistas

As camadas gastam o orçamento de DD por desenho: nas trajetórias más, o DD acaba encostado ao piso de segurança. Um piso a 88% do pico (DD máximo \~−12%) custa 2–8 pp de probabilidade e deixa \~8 pp de margem até aos 20% da desclassificação. É o piso recomendado.

| Piso | Camada | DD 1 em 10 janelas | DD 1 em 100 | Desclassif. | P(≥ 15%), com / sem tendência |
| --- | --- | --- | --- | --- | --- |
| — | EAP 80% sozinha | −2,9% | −3,5% | 0% | 0 / 0 |
| 83% | QQQ até 2×, lock 15% | −16,0% | −18,5% | 0,3% | 34 / 19 |
| 83% | TQQQ até 4,5×, lock 15% | −17,4% | −21,5% | 2,0% | 52 / 36 |
| 83% | Calls 15% do NAV, lock 20% | −16,6% | −17,4% | 0% | 43 / 26 |
| 88% | QQQ até 2×, lock 15% | −11,7% | −13,7% | 0% | 31 / 17 |
| 88% | TQQQ até 4,5×, lock 15% | −12,8% | −17,5% | 0,4% | 44 / 28 |
| 88% | Calls 10% do NAV, lock 20% | −11,8% | −12,6% | 0% | 35 / 20 |

- **O DD típico sobe muito face à EAP sozinha.** Com piso a 83%, fica em −7% (QQQ), −10% (TQQQ) e −12% (calls, porque o prémio se vai perdendo quando o mercado não sobe). Com piso a 88%, encolhe na mesma proporção.
- **O TQQQ é a única camada com desclassificações reais.** Vêm de quedas de um dia que atravessam o piso antes de a exposição descer. As calls têm o teto mais firme, porque a perda máxima é o prémio.
- **Porquê 88%:** a margem cobre o que o modelo não vê. A forma exata de medir o DD, quedas maiores do que as históricas, execução com 15 minutos de atraso, um erro do agente. Com uma regra de desclassificação, qualquer um destes acaba com a competição.
- **Medição:** DD ao fecho, mais o Low intradiário da camada. O limite totalmente pessimista da EAP (todas as ações no Low e o hedge no High ao mesmo tempo) sobe a desclassificação nos piores casos, mas quase não muda a P(ganhar).

### Híbridos testados (A–D) e o U2 com notícias

A EAP concentrada nos nomes mais voláteis, com a camada TQQQ a k=4, bate a recomendação actual em probabilidade e em risco de choque. Mantém-se a ressalva de sobrevivência. Tudo foi pré-registado antes de correr (`TradingV2/research/ACOES/wic_hibridos_20261105/`, branch `ccr-ffa2d2bf-mi1yfs`). A única excepção é a variante com k=4, que é pós-hoc.

O motor decompõe a EAP em alfa diário e beta das ações. A camada decide a exposição total ao QQQ, com o bruto overnight ≤ 2×, piso a 88%, DQ a 80% e o VXN da véspera alinhado com a janela. Há 40.000 trajetórias com janelas contínuas reais do QQQ (2012–26; 2001–26 dá a mesma ordem).

| Variante | DQ | P(≥ 15%) sem / com tendência | P(≥ 20%) | DQ com um dia de −5σ | Janelas reais ≥ 15% / DQ |
| --- | --- | --- | --- | --- | --- |
| Recomendação actual (TQQQ k=3), VXN alinhado | 0,02% | 25 / 41 | 6 / 9 | 15% | 18 / 0 de 39 |
| A mesma, com o VXN aleatório do simulador anterior | 0,5% | 29 / 45 | 8 / 12 | — | — |
| A: Browne (meta até ao prazo), com tecto 3σ | 0,02% | 25 / 41 | 5 / 9 | 15% | 18 / 0 |
| A: Browne sem tecto | 9–12% | 37 / 50 | 13 / 18 | — | 24 / 6 |
| B: EAP sem hedge a 160% + camada | 0,4% | 35 / 49 | 16 / 23 | 18% | 21 / 0 |
| C: EAP K=15 por vol, sozinha | 0% | 31 / 31 | 0 / 0 | — | 12 / 0 |
| C: EAP K=15 por vol + camada k=3 | 0,2% | 40 / 54 | 22 / 31 | 19% | 21 / 0 |
| D: camada k=4 | 0,02% | 20 / 35 | 2 / 5 | 0,02% | 18 / 0 |
| **C + D: EAP K=15 por vol + camada k=4** (pós-hoc) | **0,04%** | **37 / 51** | **17 / 25** | **1,9%** | 18 / 0, pior −8,1% |

- **Browne não acrescenta nada.** Com tecto, o tecto manda e o resultado fica igual. Sem tecto, desclassifica 9–17% das trajetórias.
- **O k=3 é frágil a um dia de 5σ** face ao VXN da véspera. Desde 2001 houve dois dias assim no Low intradiário (6/5/2010 e 24/8/2015), nenhum no fecho. O k=4 custa \~5 pp de probabilidade e elimina esse risco.
- **A EAP concentrada por vol bate a EAP 80% em 12 de 13 anos.** Com a mesma exposição média, bate em 10 de 13. A média fev–mar é +9,1% contra +3,5%, com o pior DD na janela em −8,7%.
- **Sobrevivência é a ressalva principal.** As empresas voláteis que faliram não estão no universo, e são exactamente as que esta prioridade escolheria. Os membros históricos da Bloomberg de 6/11 decidem se a C fica.
- **U2 com CPI, NFP ou FOMC no hold: nada muda.** Com o hold planeado, o R é +0,27 com evento contra +0,21 sem (Δ +0,07, IC95 \[−0,19; +0,32\]). A janela até à saída real dava um falso efeito positivo, porque um stop encurta a janela.

### Robustez da EAP concentrada e camadas por cima

A EAP concentrada aguenta sozinha. A camada de TQQQ por cima não aguenta quando o intradiário é medido ação a ação (todas as ações no Low ao mesmo tempo). Isto corrige a variante com k=4 da secção anterior. Tudo foi pré-registado (`PREREG2.md`) e corrido uma vez.

| Teste de robustez da EAP concentrada | Resultado |
| --- | --- |
| Calendário SEC 8-K | +7,8% contra +2,9% da EAP 80%, à frente em 12 de 13 anos |
| K=10 / K=20 | +11,2% / +8,0% contra +3,4% |
| 2014–2019 / 2020–2026 | +6,2 / +5,6 pp sobre a EAP 80% |
| Bootstrap por ano | +5,9 pp, IC95% \[+3,7; +7,9\] |
| Intradiário pessimista, sozinha | DQ 0,02%; pior DD dentro da janela −8,7% |
| Inclinação AMC 1,25× | não ajuda (alfa igual, P(≥ 15%) cai) |

| Camada por cima (intradiário pessimista) | DQ | P(≥ 20%) sem / com tendência | P(≥ 30%) | DQ num dia de −5σ / −8% |
| --- | --- | --- | --- | --- |
| Nenhuma | 0,02% | 0 / 0 (P(≥ 15%) 31%) | 0 | 0,03% / 0,02% |
| **Calls 5% do NAV, lock 20%** | **0,2%** | **11 / 26** | 0,5 / 1,5 | **0,7% / 0,8–1,0%** |
| Calls 10% do NAV, lock 20% | 0,62% | 17 / 34 | 1,8 / 4,3 | 3,0% / 4,6–4,9% |
| Calls 15% do NAV, lock 30% | 0,9% | 12 / 28 | 6 / 16 | 4,3% / 6,5% |
| TQQQ k=4, lock 20% | 1,6–1,8% | 23 / 37 | 1,8 / 3,4 | 14% / 45% |
| TQQQ k=4, σ efectivo | 1,3–1,4% | 21 / 34 | 1,2 / 2,1 | 8,7% / 35% |
| TQQQ k=3 + puts 2× | 2,6–2,9% | 22 / 37 | 2,5 / 4,8 | 38–39% / 50–52% |
| Recomendação anterior (EAP 80% + TQQQ k=3) | 0,46% | 6 / 9 | 0 | 26–27% / 40–42% |

- **Porque o TQQQ falha:** com 15 nomes voláteis, o pior caso intradiário é grande (5% dos dias com −3,75% ou pior). Gasta a margem até ao piso que a camada usa por desenho, e um dia de −8% no QQQ acaba com ela. As calls têm a perda limitada ao prémio.
- **+30% é difícil com qualquer combinação:** no máximo 6% sem tendência e 16% com tendência. Precisa de um QQQ em subida.
- **O limite pessimista assume as 15 ações no Low ao mesmo tempo.** Se a WIC medir o DD ao fecho, o TQQQ volta a ser opção: sem o pessimismo, as calls a 10% dão DQ 0%, mas o TQQQ k=4 ainda dá 28% num dia de −8%.
- **Pendentes:** viés de sobrevivência (Bloomberg); se o agente pode negociar opções; como é medido o DD.

### Cenários das regras: o que fazer em cada caso

Se o agente puder negociar opções, a resposta são calls de QQQ por cima da EAP concentrada, seja qual for a forma de medir o DD. Muda só o tamanho. Sem opções, fica a EAP concentrada sozinha, ou o TQQQ k=4 se for aceite o risco de um crash tipo 1987. Pré-registo 3, corrido uma vez.

| Medição do DD | Com opções | Sem opções |
| --- | --- | --- |
| Fecho das 16:00 ET, ou intradiário moderado (ações ao fecho, QQQ no Low) | Calls 15% do NAV, lock 20%, piso 85%: P(≥ 20%) 22 / 41%, P(≥ 15%) 26 / 48%, DQ 0,04% | EAP concentrada sozinha: P(≥ 15%) 31%. Ou TQQQ k=4 com piso 88%: P(≥ 20%) 23 / 37%, mas DQ de 30% num dia de −8% |
| Intradiário pessimista (todas as ações no Low ao mesmo tempo) | Calls 5% do NAV, lock 20%, piso 88%: P(≥ 20%) 11 / 26%, DQ 0,2% | EAP concentrada sozinha |

- **Os valores são sem / com tendência.** Todas as escolhas têm menos de 1% de DQ nos choques de 5σ e de −8%, excepto o TQQQ.
- **O −8% com o VXN normal nunca aconteceu desde 2001.** Os 5 fechos do QQQ a −8% ou pior foram todos com o VXN da véspera acima de 50, quando a camada já tinha encolhido.
- **Se a EAP concentrada cair no teste de sobrevivência,** usa-se a EAP 80% com as mesmas calls (15% do NAV, piso 85%): P(≥ 20%) de 17 / 37%.

### Alternativas que não passaram (pré-registo 4)

Nenhuma das três alternativas melhora a escolha acima, por isso a recomendação da secção anterior mantém-se.

| Alternativa | Resultado |
| --- | --- |
| Call spreads de QQQ (comprar 5% OTM, vender 12–15%) | Praticamente iguais às calls simples em todos os modos (−0,2 a −0,5 pp de P(≥ 20%)) |
| Manter até R+1 ou R+3 (deriva pós-anúncio) | −2,5 pp e −5,3 pp de alfa fev–mar, piores em 9 de 13 anos |
| Tamanho maior em março quando há poucos nomes | +0,2 pp, IC95% \[−0,2; +0,7\] |
| Escolher os 15 nomes pelo movimento implícito das opções | −0,3 pp (só 35% dos eventos têm opções; 7 anos) |

### Sair na reversão rápida antes do breakeven (premium, U2, EAP)

A proposta era fechar uma posição que esteve em lucro quando o preço reverte de repente, antes de chegar ao breakeven. Não se aplica em nenhuma das três estratégias. O caso que a motivou foi um trade da U2 a \~+3% que reverteu até ao SL depois de notícias. Isso está dentro da distribuição esperada: 21% das pernas da U2 saem no stop inicial.

| Estratégia | Evidência | Veredicto |
| --- | --- | --- |
| U2 | No motor da conta, proteger o lucro mais cedo perde mais, sobre uma base de $362/ano por tentativa de $10k: breakeven depois de +1R −$91/ano \[IC90 −160; −35\], trailing a 1R ativado a +1R −$108, trailing a 0,5R −$153 (`FINDINGS_U2_TRAILING`, `FINDINGS_U2_RECONCILIACAO`). A regra proposta dispara ainda mais cedo. | Não |
| Premium | Alargar o TP de 1R para 1,5R deu +$134/ano. O R médio por perna sobe de +0,133 (TP a 1R) para +0,219 (1,5R) e +0,427 (sem TP): a premium vive de poucos vencedores grandes (`FINDINGS_PREMIUM_SAIDAS`). | Não |
| EAP | O retorno faz-se no gap noturno do anúncio (+38,5 dos 58 bps). Não há fase de lucro intradiário para proteger, e num gap não se consegue sair. | Não se aplica |

- **A U2 compra quedas.** Uma regra de "queda rápida, sair" vende precisamente as quedas que a U2 existe para comprar.
- **Num choque de notícias o movimento faz-se em 1–5 minutos.** Com o relógio de 60 s, a regra dispararia perto do mínimo.
- **A proteção de ganhos certa está ao nível da carteira:** o piso a 85–88% do pico e o lock.
- **Notícias agendadas no hold da U2 (CPI, NFP, FOMC) não pioram o resultado.** Com o hold planeado: R +0,27 com evento contra +0,21 sem; Δ +0,07, IC95% \[−0,19; +0,32\].

### O teto dos +30% e a previsão do QQQ

Há um teto matemático para P(≥ 30%), e a recomendação anterior já estava perto dele. Numa camada sem edge, com o DD medido desde o pico, a probabilidade máxima de chegar a +30% antes de bater no piso é 1,3^(−1/D), em que D é a distância do piso ao pico. A fórmula foi confirmada por Monte Carlo com 200 mil trajetórias. Correcção (pré-registo 27): o tecto só vale para um NAV contínuo; uma aposta binária resolvida dentro de uma sessão chega a 38,8%.

| Piso | Máximo teórico de P(≥ 30%), DD medido desde o pico | Idem, DD medido desde o capital inicial |
| --- | --- | --- |
| 88% | 11% | 29% |
| 85% | 17% | 33% |
| 80% (limite de DQ) | 27% | 40% |

- **Com a EAP concentrada a dar +9%**, a camada só precisa de fazer +19%, e o teto sobe para 23–31%. As calls compradas no 1.º dia dão 10% / 25% (sem / com tendência). A diferença vem sobretudo do custo das opções.
- **Se a WIC medir o DD desde o capital inicial e não desde o pico, o teto quase duplica.** É a pergunta aos organizadores que mais pesa.

**Previsão da tendência do QQQ (exploratório, não pré-registado):** nenhum sinal clássico prevê o QQQ nas 36 sessões seguintes. Usei 180 janelas sem sobreposição de 2001–2026; com esta amostra, o ruído da correlação é ±0,15.

| Sinal | Correlação com o retorno seguinte |
| --- | --- |
| Momentum 12–1 meses | +0,08 |
| Preço acima da média de 200 dias | +0,05 |
| Retorno dos 36 dias anteriores | −0,06 |
| Nível do VXN | −0,03 |
| VXN face à vol realizada | +0,04 (+0,40 em 2001–13, −0,01 em 2014–26) |
| Distância ao máximo de 52 semanas | +0,07 |

- **Fev–mar é historicamente fraco.** Em 2001–2026, o QQQ teve média de −1,0% em fev–mar, foi positivo em 13 dos 26 anos e subiu +7% ou mais em apenas 3.
- **O sentimento também não ajuda.** O sinal da Fed no Polymarket já morreu no holdout, e na literatura a maioria dos preditores do prémio de risco falha fora da amostra (Welch e Goyal, 2008).

### Torneio: P(1.º lugar) por camada

Sem tendência forte do QQQ, a EAP concentrada sozinha é a que ganha mais vezes, mesmo sem chegar a +20%. Ganhar é ficar à frente dos outros, e no modelo o melhor adversário fica abaixo de +22% em mediana. Pré-registo 5 (PREREG5.md), corrido uma vez.

**Método:**

- **Adversários:** 14 equipas sintéticas por torneio, sobre o mesmo caminho do QQQ que a nossa trajetória. Cada uma tem alavancagem e risco próprio sorteados, e é desclassificada se cair 20% desde o pico.
- **Cenários:** cauteloso, misto, agressivo e misto com 3 equipas competentes (+5,5% de alfa na janela). O melhor adversário que sobrevive fica, em mediana, entre +8% e +22% conforme o cenário. Os +33% do vencedor da Divisão Trader de 2025 ficam perto do p90 dos cenários misto e competente.
- **Ranking:** RRF com k=60, 70% desempenho e 30% relatório. O nosso relatório fica em 1.º, 3.º ou 8.º.

| Base C15v, DD ao fecho | P(1.º) sem tendência | Com tendência 2012–26 | Mediana | Retorno negativo |
| --- | --- | --- | --- | --- |
| EAP sozinha | 40,8% | 31,5% | +9,5% | 8% das vezes |
| Calls 5%, lock 20%, piso 88% | 33,6% | 33,9% | — | — |
| Calls 15%, lock 20%, piso 85% (rec. anterior) | 28,5% | 35,6% | +3,0% | 35% das vezes |
| Calls 15%, lock 30%, piso 85% | 27,1% | 36,0% | +3,0% | 35% das vezes |

- **A EAP sozinha ganha nas 12 combinações de cenário × relatório, sem tendência.** O mesmo vale com k=10, se os desclassificados forem excluídos e no modo intradiário pessimista.
- **O resultado depende da tendência do QQQ** (exploratório). Com 0%, \~10%, \~15% e 19,6% ao ano, a EAP sozinha dá P(1.º) de 40,8 / 36,2 / 33,8 / 31,5%, e as calls 15% dão 28,5 / 32,1 / 33,9 / 35,6%. O empate fica nos \~15%/ano. Com a EAP 80% desce para \~9%/ano.
- **Porquê:** os adversários também estão comprados no mercado. As calls apostam no mesmo fator, por isso não te destacam. O que te destaca é o alfa não correlacionado da EAP.
- **O RRF dá peso ao relatório.** Um 2.º lugar no desempenho com o melhor relatório ganha a um 1.º com o relatório em 4.º ou pior. Passar do 8.º para o 3.º lugar no relatório vale +24 a +34 pp de P(1.º), mais do que qualquer camada.
- **Ressalva:** se a fasquia real for +30% (como na Divisão Trader), a EAP sozinha nunca ganha em desempenho. Os adversários são sintéticos e quase sem alfa: os números servem para comparar camadas, não para prever a probabilidade de ganhar.

### DQ operacional e guardas determinísticas

As falhas de execução triplicam o DQ das calls. Duas guardas em código determinístico, fora do LLM, devolvem-no a \~0 sem custo em P(≥ 20%) nem em P(1.º). Pré-registo 5.

**Falhas simuladas** (incidentes em 1% ou 3% das sessões, cada um dura uma sessão):

- hedge ausente;
- hedge com o sinal trocado;
- o agente não executa a regra de venda nem o lock;
- ordem 10× maior num nome da EAP.

**Guardas:**

- **Kill-switch ao fecho:** se o NAV ficar abaixo de K × pico, fecha tudo e fica flat até ao fim.
- **Limite de ordem:** rejeita ordens acima de 1,5× o tamanho previsto.

| Calls 15%, lock 20%, piso 85%, DD ao fecho | DQ sem falhas | Falhas em 1% das sessões | Falhas em 3% das sessões | Trajetórias paradas pelo kill-switch |
| --- | --- | --- | --- | --- |
| Sem guardas | 0,04% | 0,14% | 0,31% | 0 |
| Limite de ordem | 0,04% | 0,07% | 0,10% | 0 |
| Kill-switch a piso − 2 pp (0,83) | 0,00% | 0,04% | 0,15% | 0,9% |
| **Kill-switch a piso − 2 pp + limite de ordem** | **0,00%** | **0,01%** | **0,02%** | 0,9% |
| Kill-switch a 0,86 fixo + limite de ordem | 0,00% | 0,01% | 0,01% | 11,9% |

- **O kill-switch tem de ficar 2 pp abaixo do piso.** Com piso a 85%, um kill-switch a 0,86 fixo dispara em 12% das trajetórias normais e custa 0,5 pp de P(1.º).
- **O limite de ordem é a guarda mais útil:** elimina a falha mais grave e não custa nada. Na EAP sozinha chega para manter o DQ entre 0,00 e 0,05%, mesmo com falhas em 3% das sessões.
- **No modo intradiário pessimista, o DQ residual das calls 5% (0,20%) vem do modelo:** são gaps intradiários que um kill-switch ao fecho não apanha.
- **Fora do modelo:** falhas de vários dias (ordens repetidas, um lock que nunca corre, uma posição esquecida depois de um reinício). São o que os testes de dezembro devem procurar.
- **O kill-switch deve ler o NAV da conta**, não preços com 15 minutos de atraso. Deve ficar declarado no relatório como guarda de risco, para não parecer "fixed rules".

### Calls ligadas pela classificação ou pela tendência

Para manter o alvo de +30%, é melhor comprar as calls só quando a classificação mostra que vai ser preciso do que no 1.º dia. Ao fecho ganha +8 pp de P(1.º) e fica com 75% da P(≥ 30%). Pré-registo 6 (PREREG6.md), corrido uma vez.

**Variantes:**

- **A, classificação:** começa-se só com a EAP concentrada. Compram-se calls se o melhor adversário estiver acima de θ e nós abaixo dele. A classificação é vista com um dia de atraso. A verificação é feita a meio da janela (sessão 18) ou em contínuo entre as sessões 10 e 25.
- **B, tendência:** compram-se calls quando o QQQ já subiu 3% ou 5% desde 1/fev.
- Em ambas: uma só compra, vencimento a 31/mar, lock a +30%, as regras de venda e de piso de sempre.

| DD ao fecho, piso 85% | P(1.º) sem / com tendência | P(≥ 30%) sem / com tendência | Compra calls em |
| --- | --- | --- | --- |
| EAP sozinha | 40,8 / 31,5 | 0 / 0 | — |
| A: θ 15%, sessão 18, 15% do NAV, strike +5% | 39,1 / 32,6 | 3,8 / 8,1 | 28% das janelas |
| A: θ 10%, sessão 18, 15% do NAV, strike +5% (escolhida pela regra) | 37,8 / 33,6 | 5,6 / 11,5 | 44% |
| **A: θ 10%, contínuo, 15% do NAV, strike +3%** | **35,1 / 35,4** | **7,5 / 16,6** | 68% |
| B: QQQ +3%, 15% do NAV, strike +5% | 35,0 / 31,5 | 4,9 / 13,1 | 45% |
| Calls compradas no 1.º dia, 15% do NAV | 27,1 / 36,0 | 10,0 / 25,0 | sempre |

- **A contínua com strike +3% é a mais robusta para os 30%.** Sem tendência ganha 8 pp de P(1.º) às calls no 1.º dia. Com tendência fica empatada (35,4 contra 36,0).
- **Ao fecho, nada ganha às calls no 1.º dia nas duas métricas.** A troca é \~2,5 pp de P(≥ 30%) por \~8 pp de P(1.º).
- **No intradiário pessimista, A (θ 10%, sessão 18, 15% do NAV, strike +5%) ganha nas duas métricas.** P(1.º) de 38,3% contra 33,8% e P(≥ 30%) de 3,5% contra 3,0% das calls 5% no 1.º dia. As variantes contínuas com 10–15% do NAV não são elegíveis neste modo (falham o choque).
- **A tendência (B) é sempre pior do que a classificação.** Fica só para o caso de não haver classificação visível.
- **Porque funciona:** a classificação mostra a tendência que não se consegue prever, porque os adversários estão comprados no mercado. Se ninguém passou de +10% a meio de fevereiro, não se gasta prémio. O custo é que as calls compradas tarde têm menos tempo para render.
- **Ressalvas:** a classificação visível e diária é uma hipótese. No modelo, o líder sobe sobretudo com o mercado. Se o líder real vier de alfa próprio, as calls podem não o acompanhar.

### Recomendação actual (6/11, depois dos pré-registos 1–6)

*Substituída pela "Recomendação actual" no topo (pré-registos 16–19). Fica como registo.*

A base é a EAP concentrada nos 15 nomes mais voláteis, com hedge de QQQ e guardas determinísticas. O alvo de +30% mantém-se: se o agente puder negociar opções, junta-se uma camada de calls de QQQ, comprada só quando a classificação mostra que vai ser preciso. Sai o TQQQ: falha no intradiário ação a ação e num dia de −8%. Os números estão em "Calls ligadas pela classificação ou pela tendência" e "Cenários das regras".

1. **Eventos:** os mesmos da EAP (universo ex-OLD, |β| ≤ 2,5). A data e a hora são confirmadas no calendário forward e no comunicado da empresa antes de R−2.
2. **Seleção:** no máximo 15 posições abertas. Quando há mais candidatos do que lugares, entram primeiro os de maior vol idiossincrática antes do evento: desvio-padrão dos resíduos contra o QQQ nas sessões R−252 a R−3, conhecido antes da entrada.
3. **Tamanho e execução:** 80% do NAV inicial / 15, ou seja \~$53k (5,3%) por posição, em ações inteiras dimensionadas pelo fecho de R−3. Entrada MOC no fecho de R−2 e saída MOC no fecho de R. Não se mantém depois de R.
4. **Hedge:** short de QQQ igual a β × notional na entrada, coberto em R. Nunca dormir sem hedge: se o short falhar, entra o hedge alternativo na abertura seguinte.
5. **Guardas (código determinístico, fora do LLM):** rejeitar ordens acima de 1,5× o tamanho previsto e kill-switch ao fecho 2 pp abaixo do piso (0,83 com piso a 85%; 0,86 com piso a 88%), lido do NAV da conta. Ficam declaradas no relatório como guardas de risco.
6. **Camada de calls (só com opções), ligada pela classificação:** começa-se só com a EAP. As calls de QQQ compram-se uma única vez, quando o melhor adversário está acima de +10% e nós abaixo dele (classificação vista com um dia de atraso). Vencimento a 31/mar.
   1. DD medido ao fecho ou com intradiário moderado: verificação contínua entre as sessões 10 e 25, 15% do NAV, strike +3%, piso a 85% do pico. P(1.º) de 35,1% / 35,4% e P(≥ 30%) de 7,5% / 16,6% (sem / com tendência).
   2. Intradiário ação a ação: verificação só na sessão 18, 15% do NAV, strike +5%, piso a 88%. P(1.º) de 38,3% e P(≥ 30%) de 3,5% / 7,8%.
   3. Sem classificação visível: calls compradas quando o QQQ sobe 3% desde 1/fev (15% do NAV, strike +5%). Se P(≥ 30%) for o único critério, no 1.º dia (10% / 25% ao fecho, mas P(1.º) de 27%).
   4. Regra de venda diária: se o valor das calls passar NAV − piso × pico, vende-se o excesso.
   5. Lock: ao chegar a +30%, vendem-se todas as calls e fica só a EAP.
7. **Sem opções:** só a EAP concentrada, com P(≥ 15%) de 31% e DQ quase nulo.
8. **Se a EAP concentrada cair no teste de sobrevivência:** volta a EAP 80% com K=50, mais as mesmas calls (15% do NAV e piso 85%; 10% e piso 85% no intradiário ação a ação). Sem opções, fica a EAP 80% sozinha, ou QQQ até 2× com k=4 se o DD for medido ao fecho. O gatilho pela classificação só foi testado sobre a EAP concentrada.

O papel do LLM e a tese do relatório da secção seguinte mantêm-se, com as calls no lugar do TQQQ. A camada continua a ser exposição dentro de um orçamento de DD, porque o objetivo é ficar em 1.º.

**Riscos que os testes não resolvem:**

- **Sobrevivência.** As empresas voláteis que faliram ou saíram de bolsa são exactamente as que esta seleção escolheria, e não estão no universo.
- **Poucos anos.** Só há 13 anos de fev–mar: as probabilidades da EAP concentrada sozinha são contagens de anos.
- **O intradiário ação a ação é um limite superior.** Assume as 15 ações no Low ao mesmo tempo.
- **Calls do QQQ calibradas no SPY.** IV = 0,80 × VXN, com o fator medido no SPY face ao VIX.
- **Janela.** As simulações usam 36 sessões, não exactamente 1/fev–25/mar de 2027. O pico é medido nos fechos.

**Pendentes:**

- [ ] Inscrição até 15/nov.
- [ ] Perguntar aos organizadores:
  - [ ] O DD é medido ao fecho das 16:00 ET ou intradiário, e o pico também? É medido desde o pico ou desde o capital inicial? (desde o capital inicial, o teto de P(≥ 30%) quase duplica)
  - [ ] O agente pode negociar opções de QQQ, e a que preço são marcadas?
  - [ ] O TQQQ é permitido?
  - [ ] Há classificação visível, e com que atraso? (decide se as calls são ligadas pela classificação) Qual é o k do RRF? Uma equipa desclassificada fica em último ou sai do ranking?
  - [ ] O período de testes conta para o pico?
- [ ] Bloomberg: membros históricos dos índices e preços das empresas deslistadas, para refazer a EAP concentrada. É o teste decisivo.
- [ ] Refazer as simulações com a janela exacta: 1/fev a 25/mar de 2027, liquidação às 15:50.
- [ ] Período de testes (7–20/dez): comprar uma call de QQQ, fazer short de QQQ, testar ordens MOC e ver como é contada a margem.
- [ ] Medir a IV das calls do QQQ face ao VXN nos ficheiros Cboe C1 de set/2026 da Drive.
- [ ] Testes de falha no período de testes: ordem rejeitada, short de QQQ indisponível, dados atrasados, reinício a meio de uma posição, ordem duplicada. Confirmar também se o NAV da conta vem com atraso em paper.
- [ ] Implementar o limite de ordem e o kill-switch fora do LLM.
- [ ] Escrever antes da competição a regra do gatilho das calls (θ, momento da verificação, tamanho, strike) e registá-la para o relatório.
- [ ] Bloomberg: ver se há barras intradiárias antigas (normalmente só \~140 dias úteis). Se não houver, a alternativa são as barras de minuto da Alpaca (desde 2016), para substituir o intradiário pessimista.

### Recomendação para fevereiro

*Substituída pela "Recomendação actual" acima (5/11, fim do dia). Fica como registo.*

EAP 80% como base, mais uma camada de TQQQ ajustada à vol (até 4,5× o QQQ), com lock a +15% e piso a 88% do pico. Sem o U2. Se o TQQQ não funcionar na conta, a mesma camada em QQQ até 2×. As calls ficam para o caso de haver razões para achar que vai ser preciso 20% ou mais.

1. **Base:** EAP 80% como está (K=50, hedge de QQQ, regra de stress, throttle).
2. **Camada:** exposição ao QQQ = (NAV − 0,88 × pico) / (3 × vol diária do VXN), até 4,5×, recalculada ao fecho e feita em TQQQ (um terço dessa exposição em % do NAV). Com a camada long, o short de QQQ do hedge da EAP sai e o TQQQ fica líquido dele; o bruto fica abaixo de 2× (a margem que a IBKR exige no TQQQ está por confirmar).
3. **Lock:** ao chegar a +15%, a camada fecha e fica só a EAP.
4. **Sem U2:** é long de QQQ a comprar quedas, duplica a aposta da camada e gasta o mesmo orçamento de DD. Em fev–mar só acrescentava +0,2 pp.
5. **Variantes:** sem TQQQ, a mesma regra em QQQ até 2× com k = 4 dá P(≥ 15%) de 31% / 17%, sem desclassificação (contra 44% / 28% e 0,4% do TQQQ). Se for preciso ≥ 20%: calls de QQQ \~5% OTM com 10% do NAV, vencimento a 31/mar (cobre a janela toda e ainda tem valor temporal na liquidação), regra de venda diária e lock a +20%.

**Papel do LLM em tempo real** (cumpre a regra sem lhe dar poder sobre o tamanho):

- Confirmar a data e a hora de cada earnings no site de relações com investidores antes de R−2 (o maior risco de dados da EAP).
- Vetar situações especiais: fusão pendente, halt, reverse split, anúncio adiado.
- Se houver classificação visível: escolher o lock entre 15%, 20% e 30% conforme o líder, com uma regra escrita antes da competição e uma fonte declarada.

**Relatório (30% do ranking).** A tese tem de ser explícita: a EAP gera o retorno; a camada de QQQ é exposição dentro de um orçamento de DD (Grossman–Zhou), porque o objetivo é maximizar a probabilidade de ficar em 1.º, não o retorno esperado. O relatório deve mostrar que as chamadas registadas ao LLM batem com as decisões.

**Pendentes:**

- [ ] Inscrição até 15/nov
- [ ] No grupo de WhatsApp: o agente pode negociar opções e TQQQ? O DD é medido ao fecho ou intradiário, e as opções são marcadas a mid? Há classificação visível? Qual é o k do RRF?
- [ ] No período de testes (7–20/dez): comprar QQQ, fazer short de QQQ, comprar TQQQ e uma opção de QQQ, para confirmar permissões e margem (a regra PRIIPs da UE pode bloquear ETFs americanos)
- [ ] Refazer as simulações com a janela exata de 1/fev a 25/mar 2027 e vencimento a 31/mar
- [ ] Escrever a regra do lock dinâmico antes da competição, se houver classificação visível

### Autocorrelação da EAP (pré-registo 7)

A EAP é um prémio pago a todos em média, não uma série de wins de certas ações ou setores. Testei a autocorrelação separada por ação, setor (SIC e pares por correlação de retornos), mercado e calendário, e nenhuma das 8 hipóteses passa. Pré-registo 7 (PREREG7.md), em commit antes de correr e corrido uma vez.

Método: ledger da auditoria (22.814 eventos, ex-OLD, |β| ≤ 2,5). O resultado é z, a EAP dividida pela vol idiossincrática de R−3, porque a EAP concentrada já escolhe por vol e interessa o que um sinal acrescenta para além dela. Todos os sinais usam só eventos com R até R−3. Tercis cortados em 2014–2021; a hipótese tinha de se confirmar em 2022–2026 com o mesmo sinal, IC95% sem o zero e Holm sobre as 8.

| Categoria | Sinal em R−2 | z alto − baixo 2014–21 | z alto − baixo 2022–26 \[IC95%\] | 2022–26 em bps \[IC95%\] | Veredicto |
| --- | --- | --- | --- | --- | --- |
| Ação | z do evento anterior | +0,02 | −0,03 \[−0,16; +0,10\] | −0 \[−43; +41\] | Morto |
| Ação | z de há 4 trimestres (sazonalidade) | −0,07 | +0,10 \[−0,06; +0,25\] | +29 \[−21; +77\] | Morto |
| Ação | média de z nos 8 eventos anteriores | +0,05 | −0,02 \[−0,17; +0,14\] | −16 \[−69; +35\] | Morto |
| Ação (notícia) | surpresa de EPS anterior (Bernard–Thomas) | −0,02 | +0,10 \[−0,06; +0,26\] | +45 \[−11; +100\] | Morto |
| Setor | SIC 2 dígitos, eventos dos 30 dias anteriores | +0,08 | +0,06 \[−0,15; +0,29\] | +34 \[−41; +111\] | Morto |
| Setor | 20 pares mais correlacionados, 30 dias | +0,01 | +0,13 \[−0,05; +0,31\] | +46 \[−8; +102\] | Morto |
| Mercado | todos os eventos dos 10 dias anteriores | +0,10 | −0,07 \[−0,23; +0,11\] | −17 \[−66; +37\] | Morto, troca de sinal |
| Calendário | atraso face ao mesmo trimestre do ano anterior | −0,12 | −0,12 \[−0,25; +0,01\] | −47 \[−90; −5\] | Morto (p 0,076; Holm 0,61) |

Wins não precedem wins: P(win | win anterior) = 52,1% e P(win | loss anterior) = 52,5%, diferença −0,35 pp \[−1,7; +0,9\]. A autocorrelação de z dentro da ação fica abaixo de 0,012 em todos os lags de 1 a 8.

No tercil mais volátil (o universo da EAP concentrada) o quadro é o mesmo: nada passa, e o atraso volta a ser o mais forte (−87 bps, IC no limite do zero).

Os pares do setor repetem o que o H1 já mostrava: continuação positiva nos dois períodos, mas dentro do ruído. Trocar o SIC por pares de correlação não limpa o sinal.

#### Notícias semelhantes

As notícias repetem-se; a reação só se repete quando a notícia se repete, e isso não se sabe em R−2. A surpresa de EPS tem autocorrelação +0,20 com a do trimestre anterior, mas o retorno não tem (+0,003). O mercado já desconta a parte previsível das surpresas.

| Ex post (não negociável) | corr(z, z anterior) | n |
| --- | --- | --- |
| Surpresa com o mesmo sinal da anterior | +0,064 | 15.333 |
| Surpresa com o sinal trocado | −0,157 | 6.830 |
| Beat depois de beat | +0,014 | 12.934 |

Depois de dois beats seguidos, o z médio é o mesmo quer o evento anterior tenha ganho (+0,523) quer tenha perdido (+0,522). As sequências de beats também não dão um padrão (0 beats: 68 bps; 8 ou mais: 39 bps).

#### Onde há persistência: no risco

A direção não persiste, mas o tamanho dos movimentos e a correlação dentro do setor sim. É informação para a regra de stress, não para escolher nomes.

- Tamanho: corr(|z|, |z| anterior da ação) = +0,10; corr(|z|, |z| médio do mercado nos 10 dias anteriores) = +0,14. É o mesmo resultado do H2 dos pares, agora ao nível do mercado.
- Mesma noite: correlação média de z +0,018 entre todos os eventos; +0,072 no mesmo SIC2; +0,013 entre setores diferentes. 15 nomes na mesma noite valem cerca de 12 independentes.
- Série agregada: a média semanal de z tem autocorrelação de +0,04 a +0,12 (ruído \~±0,07) e de −0,04 de época para época. Out–nov contra o fev–mar seguinte dá −0,65, mas com 12 anos e entre \~20 secundárias trato-o como acaso.

#### O atraso do anúncio (o que esteve mais perto)

As empresas que anunciam mais tarde do que no ano anterior rendem menos, como na literatura (So, 2016), mas isso não acrescenta nada à EAP concentrada. Exploração pós-hoc, sem poder de decisão.

| Atraso face ao ano anterior (yfinance) | Eventos | z médio | bps |
| --- | --- | --- | --- |
| 8 dias ou mais cedo | 333 | 0,19 | +93 |
| 2 a 7 dias mais cedo | 1.660 | 0,27 | +81 |
| No prazo (±1 dia) | 13.893 | 0,17 | +63 |
| 2 a 7 dias mais tarde | 5.189 | 0,07 | +35 |
| 8 dias ou mais tarde | 896 | 0,08 | +21 |

Com o calendário SEC 8-K, os atrasados ≥ 8 dias ficam −61 bps \[−115; −5\] abaixo dos que anunciam no prazo, negativos em 10 de 13 anos. Na carteira (sim3, K=15, prioridade = vol × (1 + 0,5·s) pelo tercil do atraso), o ganho é +0,05 pp \[IC95% por ano −1,6; +1,7\]: a prioridade por vol já capta o que interessa. O C15v deste teste reproduz o da secção "Torneio" ao cêntimo (+9,28%).

Uso prático: o LLM já confirma a data no comunicado antes de R−2. Registar o atraso face ao ano anterior custa nada e deixa o sinal medido em dados novos, com a regra congelada.

#### O que isto muda no θ

O alfa da EAP concentrada não tem momentum dentro da janela, por isso o nosso arranque não diz nada sobre o resto da janela. O gatilho das calls deve continuar a depender do líder e da distância a ele, como na regra θ = 10%.

- Autocorrelação do alfa diário (13 anos × 3 sementes): entre −0,07 e +0,03 nos lags 1 a 5; rácio de variância da janela 0,67.
- Alfa das sessões 0–17 contra o das sessões 18–36: corr −0,15 \[IC95% −0,65; +0,40\].
- Em média chegam +6,9% de alfa nas sessões 0–17 e só +2,4% depois. Na verificação da sessão 18, cerca de três quartos da EAP já estão feitos.

Isto sugere uma variante do gatilho a pré-registar: comprar calls quando o líder estiver acima de θ e acima de nós mais o alfa EAP que ainda falta em média nessa sessão (uma tabela fixa, 6,9% → 2,4% → 0). Hoje a regra compara o líder com o nosso NAV atual e subestima o que a EAP ainda vai render no início da janela.

#### O que testar a seguir

Nenhum resultado desta secção muda a recomendação actual. Por ordem de valor:

1. Sobrevivência (Bloomberg, membros históricos): continua a ser o teste decisivo. A Drive só tem de novo um ficheiro de surpresas do NVDA (BBT/7), que não chega.
2. Gatilho θ com o alfa EAP que falta (acima), no motor do pré-registo 6, medido em P(1.º) e P(≥ 30%).
3. Regra de stress com choque proporcional ao |z| médio recente do mercado, e um teto para o mesmo SIC2 na mesma noite. Medir no DQ e no pior DD, não no retorno.
4. Volume e short volume anormais antes do anúncio (Frazzini–Lamont; Christophe, Ferri e Angel, 2004). Há volume no ledger e o ingest FINRA do repo, mas o sinal geral de short volume já falhou e o histórico é curto.
5. Teste-sombra até 31/01: juntar o atraso face ao ano anterior e o sinal dos pares por correlação aos registos, com as regras congeladas.

### Testes recomendados (pré-registo 8)

Nenhum dos testes recomendados na secção anterior muda a recomendação actual. A única hipótese que passa é descritiva: a cauda esquerda dos eventos engrossa depois de dias com movimentos grandes. Pré-registo 8 (PREREG8.md), em commit antes de correr.

| Teste | Resultado | Veredicto |
| --- | --- | --- |
| Gatilho θ com o alfa EAP que falta | Ao fecho: P(1.º) 37,5% contra 35,1%, mas P(≥ 30%) 5,3% contra 7,5% | Não substitui |
| Cauda esquerda depois de movimentos grandes | Quantil 5% de z −0,60 \[−1,05; −0,11\] mais baixo em 2022–26 (−1,09 em 2014–21) | Passa (descritivo) |
| Regra de stress fixa, dinâmica ou com teto por setor | Pior DD da EAP concentrada −9,5% a −9,9% contra −8,6% sem regra; alfa −0,2 a −0,5 pp | Nenhuma adoptada |
| Volume esperado (Frazzini–Lamont) | 2014–21 +0,15; 2022–26 +0,07 \[−0,09; +0,23\] | Morto |
| Volume anormal antes do anúncio | Troca de sinal | Morto |
| Short ratio FINRA anormal antes do anúncio | Negativo nos dois períodos, 2022–26 −38 bps \[−86; +10\], Holm 0,20 | Morto, o mais próximo |

#### Gatilho θ

O alfa que falta funciona como um θ mais alto: compra calls menos vezes, ganha P(1.º) sem tendência e perde P(≥ 30%). Em média faltam 9,2% de alfa na sessão 0, 6,4% na 10 e 2,3% na 18. Calculei-o deixando de fora o ano de cada trajetória.

| Modo | Variante | P(1.º) sem / com tendência | P(≥ 30%) sem / com | Compra calls |
| --- | --- | --- | --- | --- |
| Fecho | Actual: θ 10%, contínuo | 35,1 / 35,4 | 7,5 / 16,6 | 68% |
| Fecho | Alfa que falta, θ 10%, contínuo | 35,8 / 35,4 | 6,8 / 15,5 | 65% |
| Fecho | Alfa que falta, θ 15%, contínuo | 37,5 / 33,9 | 5,3 / 12,3 | 47% |
| Pessimista | Actual: θ 10%, sessão 18 | 38,3 / 33,2 | 3,5 / 7,8 | 44% |
| Pessimista | Alfa que falta, θ 15%, sessão 18 | 39,9 / 32,6 | 2,2 / 5,2 | 26% |

A escolha continua a ser quanto vale o alvo de +30%. Se P(1.º) for o único objectivo, θ mais alto (ou a EAP sozinha) ganha; se o alvo de +30% contar, fica o θ de 10%.

#### Regra de stress

As regras só cortam entradas novas depois de perdas. O DD vem do salto noturno das posições já abertas, e cortar entradas tira os eventos que recuperariam. A regra vê o NAV com hedge, que é o da conta. O motor sem regra reproduz o pior DD de −8,7% da secção "Robustez".

| Variante (EAP concentrada) | Alfa fev–mar | Pior DD fecho / intradiário | P(1.º) fecho com calls |
| --- | --- | --- | --- |
| Sem regra (actual) | 9,3% | −8,6% / −10,4% | 35,1% |
| Choque fixo 15% | 9,0% | −9,6% / −12,4% | 34,8% |
| Choque proporcional ao movimento médio recente do mercado | 8,9% | −9,6% / −10,7% | 33,9% |
| Choque fixo + máx. 3 do mesmo setor por noite | 8,8% | −9,9% / −11,1% | 33,9% |
| Só máx. 3 do mesmo setor por noite | 9,0% | −9,5% / −11,1% | 34,5% |

A protecção certa continua a ser o piso da camada e o kill-switch. A cauda mais grossa depois de dias agitados é um facto para o relatório e para o LLM registar, não uma regra de tamanho.

#### Sobrevivência

Sem membros históricos, calculei quanto teriam de render os nomes em falta para anular a vantagem da EAP concentrada sobre a EAP 80% (+5,9 pp). Calibração: as 225 ações do universo que caíram 70% ou mais e sobreviveram tiveram EAP média de −309 bps no ano anterior à queda.

| Eventos vindos de nomes em falta | Retorno médio −3,1% (calibrado) | −10% | −20% |
| --- | --- | --- | --- |
| 2% | −0,7 pp | −1,9 pp | −3,6 pp |
| 5% | −1,8 pp | −4,8 pp | −9,1 pp |
| 10% | −3,7 pp | −9,6 pp | −18,2 pp |

A vantagem desaparece com 16% dos eventos em falta ao retorno calibrado, ou 6% se esses nomes perdessem em média 10% por evento.

Datas isoladas chegam para o teste. Na Bloomberg, os membros históricos pedem-se uma data de cada vez com um override de data, por exemplo =BDS("SML Index","INDX\_MWEIGHT\_HIST","END\_DATE\_OVERRIDE=20131231"). O pedido mínimo:

1. Membros do S&P 500 (SPX Index), S&P 400 (MID Index) e S&P 600 (SML Index) em 31/12 de 2013, 2016, 2019 e 2022: 12 pedidos. São as listas de onde vem o universo.
2. Com essas listas, calculo os nomes que saíram e a fração f real. Para esses nomes, só faltam preços diários ajustados (abertura, fecho, máximo, mínimo, volume) até à saída.
3. As datas dos anúncios das empresas que saíram vêm da SEC (8-K Item 2.02) com o ingest do repo, porque as empresas deslistadas mantêm os registos no EDGAR.

### Cauda, dificuldade e short selling (pré-registo 9)

Nenhuma das três pistas muda a recomendação. A cauda e o short volume usam dados já vistos e contam como exploração; o filtro de ações afundadas e o short interest eram hipóteses novas. Pré-registo 9 (PREREG9.md), em commit antes de correr.

#### A cauda depois de dias agitados paga mais

A cauda esquerda é mais grossa depois de dias com reações grandes, mas o prémio médio também sobe. É compensação de risco, não um aviso para reduzir.

| Agitação nos 10 dias anteriores | 2014–21: bps / quantil 5% de z | 2022–26: bps / quantil 5% de z |
| --- | --- | --- |
| Baixa | +57 / −3,50 | +49 / −4,20 |
| Média | +58 / −4,20 | +13 / −4,90 |
| Alta | +75 / −4,59 | +106 / −4,80 |

Não é um regime de volatilidade: o efeito mantém-se com a vol de 60 dias, e a correlação com o VXN é −0,21. Reduzir o tamanho nos dias agitados custa 0,8 a 1,1 pp de alfa e 1,8 a 2,8 pp de P(1.º).

#### Ações afundadas

As ações que caíram 50% ou mais desde o máximo de um ano são o segmento que mais rende (+166 a +195 bps por evento). É também onde o viés de sobrevivência mais deve pesar, porque só ficaram as que recuperaram.

| EAP concentrada | Alfa fev–mar | Pior DD | P(1.º) médio | Ponto de equilíbrio da sobrevivência |
| --- | --- | --- | --- | --- |
| Actual | 9,28% | −8,6% | referência | 16% |
| Sem as afundadas 50% ou mais | 8,78% | −7,9% | −2,9 pp | 14% |

As vagas libertadas são reocupadas em 73% dos casos, por nomes voláteis com retorno parecido (+257 contra +266 bps) e a mesma proporção de AMC (66%). A perda vem das vagas que ficam vazias, sobretudo em março.

O filtro não protege da sobrevivência: só apanha 14% dos eventos do ano anterior a uma queda de 70%. As empresas que vão afundar ainda não parecem afundadas um ano antes. O teste continua a depender dos membros históricos da Bloomberg.

#### Short selling

O short volume anormal antes do anúncio tem um gradiente limpo por evento: +86, +85, +64, +57 e +26 bps do quintil mais baixo ao mais alto. É informação independente da dificuldade e do short interest. Mas vetar o tercil alto na EAP concentrada (2019–26) dá −0,04 pp, com IC95% de −4,2 a +3,4.

O short interest quinzenal da FINRA (12/2017–10/2026, sem chave de API) não prevê nada: days to cover +0,04 e variação do short interest +0,05 em 2022–26, ambos com o sinal contrário ao esperado.

Uso prático: registar o short ratio anormal no teste-sombra e no relatório, com a regra congelada (vetar o tercil alto), e avaliá-lo só em dados novos.

### Combinação para P(≥ 30%) (pré-registo 10)

Se o objetivo for chegar a +30% com o DQ controlado, a melhor combinação é a EAP concentrada mais calls de QQQ no 1.º dia, com strike +3% e piso a 83%, protegida pelo kill-switch a 81%. Bate as calls no 1.º dia da secção "Calls ligadas pela classificação" tanto em P(≥ 30%) como em P(1.º). Só vale se o DD for medido ao fecho e o agente puder negociar opções.

Método: grelha de 100 combinações por modo (EAP com 15 ou 10 nomes, piso 85% ou 83%, 10–17% do NAV, strike +0% a +10%, vencimento a 31/mar ou em maio). A escolha foi feita nos caminhos do QQQ de 2012–26 e confirmada nos de 2001–26 e nas 39 janelas reais, que a escolha não viu.

| Ao fecho, com kill-switch (piso − 2 pp) | P(≥ 30%) sem / com tendência | Caminhos de 2001 | DQ / DQ nos choques | Pior DD nas janelas reais | P(1.º) sem / com tendência |
| --- | --- | --- | --- | --- | --- |
| Calls no 1.º dia: 15% do NAV, strike +5%, piso 85% | 9,9 / 25,0 | 12,2 / 21,2 | 0,00 / 0,06 | −16,8% | 27,0 / 35,9 |
| Recomendada: 15% do NAV, strike +3%, piso 83% | 12,2 / 28,7 | 14,9 / 24,6 | 0,01 / 0,58 | −18,8% | 28,3 / 39,1 |
| Agressiva: EAP com 10 nomes, 17% do NAV, strike +3%, piso 83% | 13,3 / 29,8 | 15,9 / 25,3 | 0,13 / 2,93 | −19,1% | 33,4 / 42,7 |
| EAP concentrada sozinha | 0 / 0 | 0 / 0 | 0 / 0 | −8,7% | 40,8 / 31,5 |

- Strike +3% é melhor do que +5%, e +8% a +10% pior: as calls mais longe raramente chegam. O vencimento em maio nunca entrou nas 10 melhores.
- A agressiva foi a escolhida pela regra pré-registada e confirmou-se, mas fica no limite: DQ de 4,9% nos choques sem guardas (o corte era 5%) e 2,9% com o kill-switch. Além disso, a EAP com 10 nomes é mais exposta à sobrevivência. Por isso recomendo a do meio, que perde \~1 pp de P(≥ 30%) e mantém o DQ perto de zero.
- O custo é a margem: com piso a 83%, o pior DD das janelas reais fica a 1,2 pp da desclassificação, contra 3,2 pp com piso a 85%. A margem que o piso de 88% dava para erros fora do modelo deixa de existir.
- O preço de perseguir os +30% continua alto: P(1.º) de 28% contra 41% da EAP sozinha sem tendência. Os +30% só ficam prováveis com tendência (28,7%).
- No modo intradiário ação a ação, nenhuma combinação com piso 85% ou 83% é elegível; ficam as calls de 5% com piso 88% (P(≥ 30%) \~3%).

O teto teórico com piso a 83% e DD desde o pico é \~21%; a recomendada chega a 12% sem tendência. A pergunta aos organizadores sobre como se mede o DD continua a ser a que mais pesa.

### Controlo do DD (pré-registo 11)

As guardas que já estão na recomendação estão perto do melhor que se consegue: tudo o que testei por cima corta o alfa da EAP, que é o que dá a P(1.º). Pré-registo 11 (PREREG11.md), em commit antes de correr.

De onde vem o risco: com a regra de venda diária, as calls nunca valem mais do que a distância ao piso, por isso sozinhas não o atravessam. O que atravessa o piso são os saltos noturnos do livro EAP. Os mecanismos atacam esse risco.

| Ao fecho, combinação recomendada com kill-switch | P(≥ 30%) sem / com tendência | DQ nos choques 5σ / −8% | Pior DD real | P(1.º) |
| --- | --- | --- | --- | --- |
| Sem mecanismo | 12,2 / 28,7 | 0,19 / 0,58 | −18,8% | 28,3% |
| Reduzir a EAP se a folga até ao DQ < 15% do livro | 12,2 / 28,7 | 0,01 / 0,11 | −17,9% | 27,6% |
| Reduzir a EAP se a folga até ao DQ < 25% do livro | 11,9 / 28,2 | 0,00 / 0,06 | −16,9% | 24,9% |
| Máximo de 5 posições a reagir na mesma noite | 10,1 / 25,6 | 1,18 / 1,33 | −15,4% | 24,0% |
| As duas | 10,1 / 25,4 | 0 / 0 | −16,6% | 22,5% |

- O teto por noite é caro: fevereiro tem noites com muitos anúncios, e o alfa da EAP cai de 9,3% para 8,1%.
- Reduzir a EAP com folga < 15% é quase grátis ao fecho: tira 80% do DQ nos choques e 0,9 pp ao pior DD real, sem mexer na P(≥ 30%). Falhou a regra por pouco (−0,7 pp de P(1.º), o corte era −0,5) e porque no modo intradiário não faz nada: lá o kill-switch a 86% dispara primeiro.
- No modo intradiário, os mecanismos baixam o DQ (0,21% → 0,01–0,07%) mas custam 2 a 6 pp de P(1.º). As calls de 5% com piso 88% continuam a ser a melhor opção.

O que recomendo: manter as guardas actuais. Se quiseres um seguro extra no modo fecho, a regra de reduzir a EAP com folga < 15% é o candidato, mas não passou o critério e conta como escolha de preferência. O controlo de DD que mais pesa continua a ser escolher o piso (83% ou 85%), que é a troca directa entre P(≥ 30%) e margem. Os riscos fora do modelo (dados com atraso, reinícios, ordens duplicadas) resolvem-se nos testes de dezembro, não com mais regras.

### Entrada em R−1 e camada intradiária (pré-registo 12)

Nenhuma das duas ideias passa a regra. A entrada em R−1 é a melhoria mais forte desde a EAP concentrada, mas para a P(1.º), não para os +30%. Premissa: o DD é medido desde o máximo da conta. Pré-registo 12 (PREREG12.md), em commit antes de correr.

#### A: entrar no fecho de R−1

O capital deixa de ficar parado na noite R−2→R−1, que só dá 14–22% do alfa nos nomes voláteis. Com o mesmo livro médio (\~47% do NAV), a EAP com 8 nomes rende 14,4% em fev–mar, contra 9,3% da actual.

| Base (fev–mar, 13 anos × 3 sementes) | Alfa | Δ face à actual \[IC95% por ano\] | Anos melhores |
| --- | --- | --- | --- |
| Actual: 15 nomes, entrada em R−2 | 9,28% | — | — |
| 10 nomes, R−2 | 11,23% | +1,95 \[+0,24; +3,66\] | 8/13 |
| 15 nomes, R−1 | 9,84% | +0,56 \[−1,33; +2,47\] | 7/13 |
| 10 nomes, R−1 | 13,46% | +4,18 \[+1,26; +6,76\] | 11/13 |
| 8 nomes, R−1 | 14,41% | +5,13 \[+1,56; +8,24\] | 10/13 |

- Com o mesmo tamanho por nome, R−1 vale +2,2 pp sobre R−2 (melhor em 10 de 13 anos). A vantagem é igual nas duas metades: +4,1 pp em 2014–19 e +4,2 pp em 2020–26.
- Pela regra falha: com as calls de referência (15%, +3%, piso 83%), o DQ sobe para 0,6% (15 nomes), 3,9% (10) e 7,1% (8). Todas as posições passam a atravessar um anúncio todas as noites.
- Os anos maus pioram: 2021 dá −7,9% contra +1,1% da actual.

#### B: camada intradiária de QQQ

Falha. No fecho, a única combinação elegível tem P(≥ 30%) de 1,7%, contra 12,2% das calls; no intradiário pessimista, nenhuma é elegível.

- Se o stop sair no mínimo do dia, um choque de −8% dentro da sessão leva o DQ a 15–80%. Um stop da corretora não protege de uma queda que o atravessa.
- Mesmo com o stop perfeito, o máximo foi 14,0% / 18,7% (sem / com tendência, DQ 1,3%), contra 12,2% / 28,7% das calls. As calls ficam com a deriva noturna e com a convexidade.

#### Exploratório: uma configuração elegível com R−1

Com mais alfa, o piso pode subir para 85%, e o M1b (reduzir o livro EAP quando a folga até à desclassificação fica curta) tira o DQ dos choques. Não foi pré-registado.

| Ao fecho, com kill-switch | P(≥ 30%) sem / com tendência | 2001 sem / com | DQ / choque máx. | Pior DD real | P(1.º) |
| --- | --- | --- | --- | --- | --- |
| Recomendação actual: 15 nomes R−2 + calls 15%, +3%, piso 83% | 12,2 / 28,7 | 14,9 / 24,7 | 0,01 / 0,58 | −18,8% | 28,3% |
| 10 nomes R−1 + calls 15%, +3%, piso 85%, M1b | 14,5 / 29,2 | 16,9 / 25,6 | 0 / 0,09 | −17,0% | 41,6% |
| 15 nomes R−2 sozinha | 0 | 0 | 0 / 0 | −8,7% | 40,8% |
| 10 nomes R−1 sozinha | 0 | 0 | 0 / 0 | −15,6% | 51,5% |

- No intradiário pessimista, 10 nomes R−1 + calls 5%, +5%, piso 90% e M1b dá P(≥ 30%) de 4,8 / 12,9 e P(1.º) de 44,7%, contra 3,0 / 9,2 e 33,8%.
- Com o calendário SEC 8-K, o ganho de alfa cai para +2,4 pp \[IC95% −1,1; +5,5\]. Quando o 8-K põe R um dia depois, entrar em R−1 é entrar depois do anúncio.
- No torneio com as datas SEC, a P(1.º) continua a subir (33,9% contra 25,2% com calls; 43,1% contra 36,1% sozinha). A P(≥ 30%) não: 11,2 / 23,4 contra 10,6 / 25,8.

O que isto muda: se o objetivo for a P(1.º), a EAP com 10 nomes e entrada em R−1 é a melhor candidata. Antes de a usar precisa de um pré-registo novo e de datas confirmadas antes do fecho de R−1, porque um erro de um dia custa mais do que com R−2. O teste-sombra deve medir a taxa de datas erradas a R−1. Para os +30%, nada mudou: \~12–15% sem tendência e \~23–29% com tendência.

### Datas confirmadas e confirmação da entrada em R−1 (pré-registo 13)

A EAP com 10 nomes e entrada em R−1, com a data confirmada por duas fontes, passa a regra ao fecho, com calls e sozinha, e passa sozinha no intradiário pessimista. As configurações foram congeladas antes de correr, a partir do exploratório do pré-registo 12. Pré-registo 13 (PREREG13.md), em commit antes de correr.

#### Calendário com duas fontes

Cobrir as duas datas recupera o ganho que se perdia com as datas SEC. A segunda fonte do teste é o 8-K, que só existe depois do anúncio, por isso funciona como substituto do comunicado da empresa. Concordam 21.679 eventos, 1.197 diferem uma sessão e 614 diferem duas ou mais.

| 10 nomes, R−1 (fev–mar) | Alfa | Δ face à actual \[IC95%\] | Anos melhores | 2021 |
| --- | --- | --- | --- | --- |
| Só yfinance | 13,46% | +4,18 \[+1,26; +6,76\] | 11/13 | −7,9% |
| Só SEC | 10,25% | +2,43 \[−1,11; +5,47\] | 9/13 | −12,7% |
| Duas fontes, cobrir as duas datas (P1) | 14,43% | +5,15 \[+1,89; +8,07\] | 11/13 | −8,4% |
| Duas fontes, só as confirmadas (P2) | 13,04% | +3,76 \[−0,20; +6,90\] | 11/13 | −13,2% |

Saltar os eventos em desacordo custa: são eventos com reação grande.

#### Confirmação congelada

Ao fecho, com calls 15%, +3%, piso 85% e M1b, contra a recomendação actual (15 nomes R−2, calls piso 83%), recalculada em cada variante:

| Variante | P(1.º) | P(≥ 30%) sem / com tendência | DQ | Pior DD real |
| --- | --- | --- | --- | --- |
| Base | 43,9% vs 28,3% | 16,9 / 31,6 vs 12,2 / 28,7 | 0% vs 0,01% | −16,2% vs −18,8% |
| Só janelas de 2014–19 | 45,6% vs 29,8% | 18,0 / 35,7 vs 14,2 / 33,1 | 0% | −16,2% vs −14,7% |
| Só janelas de 2020–26 | 42,4% vs 27,2% | 16,0 / 28,1 vs 10,6 / 24,9 | 0% vs 0,02% | −15,4% vs −18,8% |
| Custos stress | 38,5% vs 25,5% | 13,2 / 26,8 vs 10,8 / 26,0 | 0% vs 0,01% | −17,1% vs −19,0% |

- Sozinha, ao fecho: P(1.º) de 52,9% contra 40,8%, e passa nas quatro variantes. O pior DD real sobe de −8,7% para −16,9%.
- Intradiário pessimista, sozinha (piso 88%, M1 a 25%): P(1.º) de 51,6% contra 41,3%, DQ 0,07%. Com calls 5% e piso 90% falha: o DQ chega a 0,76% em 2020–26.
- Com 8 nomes o resultado é o mesmo dentro do ruído (P(1.º) +0,9 pp com calls). A regra desempata para os 10 nomes. Sem a segunda fonte, os 8 nomes falham no calendário SEC.
- 2021 (exploratório) não foi uma noite má: foi um ano mau para a EAP volátil, com acerto de 49% e média de −36 bps, na rotação contra software e crescimento. Um teto por setor não ajuda.

O que muda na recomendação:

- **Base:** 10 nomes de maior vol idiossincrática, 8% do NAV inicial cada, entrada MOC no fecho de R−1 com o tamanho do fecho de R−2 e saída MOC no fecho de R. Hedge e guardas como antes.
- **Calendário:** o LLM confirma a data no comunicado da empresa. Se o calendário e o comunicado concordam, entra em R−1. Se diferem uma sessão, entra em R−1 da data mais cedo e sai no fecho da mais tarde. Se diferem mais, não entra.
- **Calls:** ao fecho, 15% do NAV, strike +3%, piso 85% do pico, M1b (reduzir o livro EAP quando a folga até à linha de DQ fica abaixo de 15% do livro) e kill-switch a 83%. No intradiário pessimista, só a EAP.

Riscos novos: a carteira fica mais concentrada, por isso o viés de sobrevivência pesa mais. E a taxa real de desacordo entre o calendário e o comunicado ainda tem de ser medida no teste-sombra.

### Calls pela classificação na nova base (pré-registo 14)

Na nova base (10 nomes, entrada em R−1, data confirmada por duas fontes), ligar as calls pela classificação não passa a regra. Repeti a grelha do pré-registo 6 (48 gatilhos) com o piso, o M1b e o kill-switch da nova base. Pré-registo 14 (PREREG14.md), em commit antes de correr.

| Ao fecho | P(1.º) | P(≥ 30%) sem / com tendência | Compra calls | Confirmado |
| --- | --- | --- | --- | --- |
| Base sozinha (piso 85%, M1b) | 51,5% | 7,6 / 7,6 | — | referência |
| Calls no 1.º dia: 15%, +3% | 43,9% | 16,9 / 31,6 | sempre | referência |
| Líder acima de 20% na sessão 18: 15%, +3% | 50,6% | 9,8 / 12,5 | 15% | não |
| Líder acima de 15% na sessão 18: 15%, +3% | 50,1% | 10,6 / 14,2 | 23% | não |
| Líder acima de 10% na sessão 18: 5%, +3% | 50,0% | 8,6 / 11,0 | 34% | não |

- O gatilho faz o que foi desenhado para fazer: só compra quando estamos atrás. Por isso quase não acrescenta P(≥ 30%) nos anos em que a EAP já ganha. Nas janelas de 2014–19, a P(≥ 30%) cai para 2,5–3,6% contra 18,0% das calls no 1.º dia.
- No intradiário pessimista também nenhum passa: os gatilhos dão 1–3% de P(≥ 30%) com P(1.º) de \~50–51%.

#### Recomendação depois dos pré-registos 12–14

A base é sempre a EAP com 10 nomes, entrada no fecho de R−1 e data confirmada por duas fontes, com hedge de QQQ, limite de ordem e kill-switch 2 pp abaixo do piso. A escolha da camada depende do objetivo e das regras:

| Cenário | Combinação | P(1.º) | P(≥ 30%) sem / com tendência |
| --- | --- | --- | --- |
| Opções permitidas, DD ao fecho, alvo +30% | + calls de QQQ no 1.º dia: 15% do NAV, strike +3%, piso 85%, M1b | 43,9% | 16,9 / 31,6 |
| Objetivo só ficar em 1.º, ou sem opções, DD ao fecho | sozinha, piso 85% | 52,9% | \~0 |
| DD intradiário pessimista | sozinha, piso 88%, M1 a 25% | 51,6% | \~0 |

As calls no 1.º dia custam \~9 pp de P(1.º) e dão a P(≥ 30%). O sell-off de novembro de 2026 (moratórias de datacenters) não muda os números: nos 4 anos em que fev–mar veio depois de um sell-off forte da tecnologia, a base rendeu +14% a +24%. Muda o risco de concentração, porque a seleção por vol vai encher-se de nomes ligados à IA. O teste-sombra deve registar essa fração e o retorno dos eventos de novembro a janeiro.

### Validação da base nova (pré-registo 15)

A base nova (10 nomes, R−1, duas fontes) aguenta a validação e mantém-se; o braço das calls vale menos do que parecia. Pré-registo 15 (PREREG15.md), em commit antes de correr. As janelas são fev–mar de 2014–2026 (13 × 3 sementes) e, no teste das épocas, também mai–jun, ago–set e nov–dez (51 janelas). As verificações reproduzem o pré-registo 13 sem diferenças.

#### Data sem confirmação em R−1

No pré-registo 13, a segunda fonte era o 8-K, que é a data real do anúncio. Ao vivo, o comunicado da empresa pode não existir ao fecho de R−1. Simulei uma fração p de eventos sem confirmação, ao acaso ou concentrada nas menos líquidas.

| Regra para os não confirmados | P(1.º) sozinha, p = 10 / 30 / 50% (ao acaso) | Idem, nas menos líquidas | Maior p que ainda passa |
| --- | --- | --- | --- |
| Não entra | 52,3 / 40,8 / 32,3 | 50,6 / 43,6 / 23,1 | 10–20% |
| Entra em R−2 pelo calendário | 52,6 / 46,7 / 42,8 | 52,2 / 46,5 / 45,9 | 30–50% |
| Entra em R−1 pelo calendário | 52,8 / 53,1 / 51,6 | 53,3 / 52,4 / 52,2 | 50% |

Com todas as datas confirmadas, a P(1.º) é 52,9%. Saltar eventos esvazia vagas em fevereiro, e a R−2 ocupa a vaga duas noites. A regra escolhida é entrar em R−1 pelo calendário.

Ressalva: o calendário do teste é o histórico do yfinance, gravado depois dos factos. Ao vivo, a data de um evento não confirmado é uma projecção e erra mais. O teste-sombra tem de medir esse erro; se for alto, usa-se a R−2.

#### Viés de seleção da cadeia

Refiz as escolhas (8, 10 ou 15 nomes; R−2 ou R−1; piso 83, 85 ou 88%; com ou sem M1) deixando um ano de fora e medi nesse ano. A diferença entre o melhor resultado na amostra toda e o resultado fora da amostra mede a inflação.

| Dados | Braço | Melhor na amostra | Fora da amostra | Inflação | Ganho fora da amostra face à base antiga |
| --- | --- | --- | --- | --- | --- |
| fev–mar | sozinha | 53,7% | 53,7% | 0,0 pp | +12,9 pp |
| fev–mar | calls | 45,5% | 39,8% | +5,7 pp | +11,5 pp |
| 51 janelas | sozinha | 38,8% | 38,3% | +0,5 pp | +8,8 pp |
| 51 janelas | calls | 33,3% | 33,3% | 0,0 pp | +13,0 pp |

A base sozinha é robusta: os 13 anos escolhem a mesma configuração. No braço das calls em fev–mar a regra manda parar de afinar, e os 43,9% devem ler-se como \~38–40%. A melhor configuração (8 nomes, piso 83%) fica só 0,8 pp acima da actual, dentro do ruído e com menos margem até ao DQ; não justifica mudar.

#### Todas as épocas de resultados

Não é preciso limitar os testes a fev–mar: as outras épocas dão quase 4× mais dados sobre o mesmo mecanismo. Mas os números de fevereiro calibram-se em fev–mar, que rende cerca do dobro.

| Época (janelas) | Base antiga, alfa | 10 nomes R−2, alfa | Base nova, alfa | Efeito de 10 nomes | Efeito da R−1 |
| --- | --- | --- | --- | --- | --- |
| fev–mar (13) | 9,3% | 11,2% | 14,4% | +1,9 pp | +3,2 pp |
| mai–jun (13) | 3,9% | 5,4% | 6,5% | +1,5 pp | +1,1 pp |
| ago–set (13) | 3,6% | 4,2% | 5,4% | +0,6 pp | +1,2 pp |
| nov–dez (12) | 5,2% | 8,2% | 8,2% | +2,9 pp | +0,1 pp |

O teste decisivo falha por pouco: fora de fev–mar, a base nova ganha +2,5 pp por janela, IC95% por ano \[−0,2; +4,5\], e é melhor em 63% das janelas (o corte era IC acima de zero e 60%). Os 10 nomes repetem o ganho em todas as épocas. A entrada em R−1 vale sobretudo em fevereiro, que é quando o livro anda cheio e libertar vagas conta. No torneio com as 51 janelas, a P(1.º) sozinha é 38,6% contra 29,5% da base antiga.

#### Fronteira P(1.º) × P(≥ 30%) e janela exacta

Ao fecho, cada +2,5% do NAV em calls custa \~1,5 pp de P(1.º) e dá \~+3 pp de P(≥ 30%). O tamanho das calls escolhe-se por esta tabela, conforme o peso que se dá aos +30%.

| Calls no 1.º dia (% do NAV) | P(1.º) | P(≥ 30%) sem / com tendência | Pior DD real |
| --- | --- | --- | --- |
| 0 | 52,9% | 7,6 / 7,6% | −16,9% |
| 2,5 (dominada) | 50,6% | 4,2 / 8,7% | −15,0% |
| 5 | 49,3% | 8,0 / 17,9% | −15,3% |
| 7,5 | 47,7% | 11,6 / 25,1% | −15,2% |
| 10 | 45,8% | 14,4 / 29,0% | −15,4% |
| 12,5 | 44,4% | 16,2 / 31,0% | −15,4% |
| 15 | 43,9% | 16,9 / 31,6% | −16,2% |

Na P(1.º) com calls, descontar \~5 pp (inflação acima). No intradiário pessimista, calls com piso 88% falham o DQ; com piso 90% passam à justa (DQ 0,4%), e a base sozinha com piso 88% continua a melhor (51,6%).

A janela exacta (1/fev–25/mar de 2027, 38 sessões) não muda nada: P(1.º) mexe no máximo 0,4 pp e P(≥ 30%) sobe 0,4–0,9 pp.

O que muda na recomendação: a base fica igual; sem confirmação em R−1 entra-se em R−1 pelo calendário, sujeito ao teste-sombra; o tamanho das calls sai da fronteira, com a P(1.º) descontada.

### Sobrevivência: Wikipedia ou Bloomberg

A Wikipedia resolve as listas do S&P 500 e do S&P 400, mas não chega sozinha: falta o S&P 600 antes de 2020 e os preços da maioria dos nomes que saíram. O S&P 600 é o grupo que mais pesa: 57% das posições e 55% do P&L idiossincrático da base nova. O S&P 500 é só 17,5% das posições e 24% do P&L, por isso um pedido só ao SPX cobre cerca de um quarto.

| Índice | Histórico de alterações na Wikipedia | Remoções desde 2013 (fora do universo actual) |
| --- | --- | --- |
| S&P 500 | desde 1976, completo ([Historical components of the S&P 500](https://en.wikipedia.org/wiki/Historical_components_of_the_S%26P_500)) | 314 (205) |
| S&P 400 | desde jan/2012 ([List of S&P 400 companies](https://en.wikipedia.org/wiki/List_of_S%26P_400_companies)) | 609 (334) |
| S&P 600 | só desde dez/2019 ([List of S&P 600 companies](https://en.wikipedia.org/wiki/List_of_S%26P_600_companies)) | 491 desde 2019 (403) |

Ao todo são 762 nomes únicos fora do universo, sem contar o S&P 600 de 2014–2019, que deve juntar mais \~300–400. Numa amostra de 80, o Yahoo só tem preços que cobrem o período no índice para 26%: os que ainda cotam. Os restantes \~74% foram adquiridos ou saíram de bolsa e não têm dados. As datas dos anúncios vêm da SEC (8-K), que guarda as empresas deslistadas.

O ponto de equilíbrio precisa de duas coisas: a fração de eventos vinda de nomes em falta e o retorno médio desses eventos. A fração calcula-se com as listas e as datas da SEC, sem preços. O retorno estima-se com uma amostra.

Pedido mínimo à Bloomberg:

1. Membros do S&P 600 em 31/12 de cada ano de 2013 a 2019 (7 datas; com 3 anos entre fotografias perdem-se os nomes que entram e saem pelo meio, e o índice roda 50–90 nomes por ano). Sem Excel: SML Index MEMB, com a data no campo do topo, e exportar para PDF. Os pesos não fazem falta, só os tickers. Opcional: o S&P 400 em 31/12/2013, para conferir a Wikipedia.
2. Para uma amostra estratificada de \~150 nomes que saíram e o Yahoo não tem: preços diários ajustados (abertura, máximo, mínimo, fecho, volume) até à saída, e a bolsa (para ficar só com os cotados na Nasdaq). Eu faço a lista da amostra a partir da Wikipedia e das listas do passo 1.

### Eixos estruturais (pré-registo 16)

Só a alocação passa, e só com o DD medido ao fecho. A 1,2× com o M1b, a base sozinha chega a P(1.º) de 60,2% e P(≥ 30%) de 26,1%, melhor nas duas métricas do que qualquer combinação com calls. Pré-registo 16 (PREREG16.md), em commit antes de correr.

| Teste | Veredicto | Número principal |
| --- | --- | --- |
| Entrada MOO na abertura de R−1 | Falha | +0,8 pp de alfa \[−1,1; +2,8\]; equilíbrio com o leilão de abertura a 15 bps; pessimista não elegível |
| Reforço intradiário no dia de saída (1,0×) | Falha | +3,9 pp de alfa \[−0,5; +8,5\]; DQ 4,9% no pessimista |
| Alocação 1,0–1,4× com M1b (P(1.º)) | Falha só no pessimista | 1,4×: 61,9%, LOYO 61,4%; DQ 3,6% no pessimista |
| Alocação (P(≥ 30%), fronteira para fora) | Passa ao fecho | 17 de 48 configurações acima da fronteira das calls |
| Universo alargado (Nasdaq fora dos índices, ADRs) | Falha | Nomes novos +6 bps por evento \[−21; +35\], contra +56 na base |
| Reduzir o livro quando vamos à frente | Falha | P(1.º) 52,8% contra 52,9%; mata a P(≥ 30%) |

**Alocação.** Sem o M1b, nenhuma alocação acima de 0,8× é elegível; é o M1b que a torna possível. O alfa sobe +3,6 / +7,2 / +10,8 pp a 1,0 / 1,2 / 1,4×, melhor em 12 de 13 anos e nas duas metades, e também fora de fev–mar (+3,3 pp a 1,2×, IC95% \[+1,3; +4,9\]). Hedge parcial ou sem hedge não ajudam, e o SQQQ só muda algo sem o M1b.

| Sozinha, fecho, piso 85% | P(1.º) | P(≥ 30%) sem / com tendência | Pior DD real |
| --- | --- | --- | --- |
| Base actual (0,8×, sem M1) | 52,9% | 7,6 / 7,6% | −16,9% |
| 1,0× com M1b | 56,8% | 15,1 / 15,1% | −15,4% |
| 1,2× com M1b | 60,2% | 26,1 / 27,0% | −17,2% |
| 1,4× com M1b | 61,9% | 28,2 / 29,3% | −18,7% |

Com calls de 15% por cima da 1,2×, a P(1.º) cai para 51,7% e a P(≥ 30%) só sobe com tendência (39,4%). No intradiário pessimista, a 1,0× com piso 88% e M1 0,25 é elegível (P(1.º) 53,9% contra 51,6%, exploratório); 1,2× e 1,4× não.

**Execução (exploratório, pós-hoc).** A P(≥ 30%) de qualquer configuração depende de o custo real ser perto dos 3 bps do modelo. As posições valem em mediana 0,4–0,7% do volume diário, mas o p99 vai a 31–54%. Com impacto pela lei da raiz quadrada (Y × vol idiossincrática × √(nocional / volume), por lado):

| P(1.º) sozinha (P(≥ 30%)) | Sem impacto | Y = 0,3 | Y = 0,5 | Y = 1 |
| --- | --- | --- | --- | --- |
| Base actual | 52,9 (7,6) | 44,1 (0) | 40,7 (0) | 31,7 (0) |
| 1,2× com M1b | 60,2 (26,1) | 53,9 (8,3) | 48,7 (0) | 33,6 (0) |

Limitar cada posição a 1% ou 2,5% do volume piora sempre: o prémio está nos nomes ilíquidos. A WIC é uma conta paper da IBKR, e o fill simulado de uma MOC pode não ter impacto. Por isso a pergunta passa a ser como a IBKR paper preenche MOC grandes. Teste para 7–20/dez: uma MOC de \~5% do volume diário num nome ilíquido, comparando o fill com o fecho oficial.

**Universo alargado.** 730 nomes cotados hoje na Nasdaq fora das listas S&P, 11 498 eventos, com o viés de sobrevivência a favor deles. Mesmo assim não há prémio: +6 bps por evento, +14 bps no tercil volátil de fev–mar (contra +139 na base) e −5 bps em março. Juntá-los à base tira 6 pp de alfa. Isto reforça a pergunta da sobrevivência: se os nomes fora dos índices não pagam, os que saíram dos índices podem não pagar também.

**O que muda na recomendação:**

- DD medido ao fecho: base a 1,2× (12% do NAV inicial por nome), M1b, piso 85%, kill-switch 83%, hedge QQQ, sem calls. A 1,4× dá +1,7 pp de P(1.º) com o pior DD real a −18,7%; fico na 1,2× pela margem.
- Intradiário pessimista: 1,0× com piso 88% e M1 0,25.
- Antes de fixar: medir no período de testes o fill da IBKR paper em MOC grandes. Com impacto real, nenhuma P(≥ 30%) deste doc se aguenta.

Verificações V29–V35 com Δ = 0. Uma correcção de reporte, declarada no FINDINGS16: o script contava como "para fora da fronteira" qualquer ponto acima do maior P(≥ 30%) da fronteira das calls. Com a fronteira prolongada na horizontal, as calls sobre a base deixam de estar para fora; a alocação continua.

### Sobrevivência com as listas Bloomberg (pré-registo 17)

O universo actual infla o alfa da EAP. O universo do backtest são os membros *de hoje* dos índices S&P, por isso inclui as empresas que vieram a crescer e deixa de fora as que encolheram. Com as fotografias de 31/12 de 2013–2019 do S&P 600 e do S&P 400, em cada ano 53–65% dos membros do S&P 600 cotados na Nasdaq não estão no universo actual (32–56% no S&P 400). Pré-registo 17 (PREREG17.md), em commit antes de correr.

Universo da época (parcial), nas janelas fev–mar de 2014–2020: os nomes actuais que eram membros na data, mais as empresas que saíram dos índices e ainda cotam (56–86 por ano, com preços no Yahoo). Ficam de fora os nomes que só entraram depois e as 122–221 empresas por ano que deixaram de cotar.

| Alfa fev–mar 2014–2020 | Universo actual | Universo da época | Δ \[IC95% por ano\] |
| --- | --- | --- | --- |
| Base 0,8× | 12,5% | 6,3% | −6,3 pp \[−12,3; +0,2\] |
| 1,2× com M1b | 18,7% | 9,3% | −9,4 pp \[−18,6; +0,2\] |

- **As empresas que saíram e ainda cotam têm EAP negativa:** −39 bps por evento (z −0,19) e −82 bps em fev–mar, contra +48 e +93 bps nos restantes. São voláteis, por isso a seleção escolhe-as: ficam com 23% do nocional.
- **Decomposição:** tirar os nomes que entraram depois custa \~2 pp; juntar as que saíram e ainda cotam custa \~4 pp. 5 dos 7 anos são negativos, mas o IC toca o zero (+0,2), por isso pela regra não passa o corte.
- **Torneio** (2014–2020 com o universo da época, 2021–2026 como antes): a P(1.º) da base cai de 51,4% para 43,0%, e a da 1,2× de 59,0% para 48,5%, com a P(≥ 30%) a 9%. Só nas trajetórias de 2014–2020: 31,7% e 37,8%.

**As que deixaram de cotar (cenários).** São 312: 33 falências, 44 deslistadas re-codificadas e 235 outras, sobretudo fusões. Sem preços, o efeito vai de +1,7 pp de alfa (se renderem como os nomes que ficaram) a −13 pp (se renderem como as que saíram e ainda cotam). Uma mistura de 25% / 75% dá \~−2 pp, ou seja, um alfa da base à volta de 4% em 2014–2020. Os cenários pré-registados mais duros (−3,09% e −10% por trade) põem o alfa negativo, mas são pouco plausíveis com tantas fusões.

**O que muda:**

- Os números de P(1.º) e P(≥ 30%) deste doc estão optimistas. Com o que se consegue medir, a base fica com metade do alfa em 2014–2020.
- A 1,2× continua melhor do que a 0,8× em todos os cenários, mas no cenário pessimista fica abaixo da margem de +3 pp exigida.
- O teste decisivo passa a ser pedir à Bloomberg os preços das 313 empresas da lista pedido\_bloomberg\_mortos.csv: preços diários ajustados de 2012 até à saída e, se possível, a data e o motivo da saída. A fórmula é =BDH("\<raw>","PX\_LAST,PX\_OPEN,PX\_HIGH,PX\_LOW,PX\_VOLUME","20120101","20201231"), com o identificador da coluna raw.

**A melhor candidata no universo da época (exploratório).** P(1.º) sozinha ao fecho, em três casos: universo actual / universo da época sem mortos / mortos como os vivos.

| Candidata | 0,8× | 1,2× (M1b) |
| --- | --- | --- |
| 10 nomes por vol, R−1 (actual) | 51,4 / 43,0 / 27,8 | 59,0 / 48,5 / 29,6 |
| 15 nomes por vol, R−1 | 43,5 / 36,1 / 23,3 | 51,9 / 42,5 / 26,2 |
| 15 nomes por vol, R−2 (antiga) | 40,8 / 35,0 / 24,2 | 49,4 / 41,2 / 27,6 |
| 10 nomes ao acaso, R−1 | 41,3 / 29,8 / 16,1 | 45,3 / 31,1 / 15,2 |
| 50 nomes ao acaso, R−2 (EAP original) | 21,9 / 19,2 / 14,4 | 28,5 / 24,3 / 17,1 |

A prioridade por vol perde mais alfa em termos absolutos, mas continua a ganhar às alternativas em todos os casos. A distância para a segunda encolhe no cenário pessimista (29,6 contra 27,6 a 1,2×).

Verificações V36–V38 com Δ = 0. Limites: sem S&P 500 da época, códigos de bolsa de hoje, só 7 janelas.

### Universo da época completo e reajuste (pré-registo 18)

Com a composição da época do S&P 1500 em todos os anos de 2014 a 2026, o prémio da EAP concentrada fica em cerca de um terço do que se media. A composição vem da Bloomberg (S&P 400/600 de 2013–2019) e da Wikipedia (S&P 500 e o resto), com 78–93% de acordo onde as duas se sobrepõem. Pré-registo 18 (PREREG18.md), em commit antes de correr.

| Alfa fev–mar | Universo actual | Universo da época | Δ \[IC95% por ano\] | Com mortos: optimista / central / pessimista |
| --- | --- | --- | --- | --- |
| 0,8× | 13,5% | 4,7% | −8,7 \[−15,4; −2,0\] | 4,9 / 3,2 / −0,7% |
| 1,2× | 20,2% | 7,1% | −13,1 \[−23,1; −3,3\] | 7,3 / 4,7 / −1,1% |

- **O efeito é maior em 2020–2026 (−12,9 pp) do que em 2014–2019 (−3,9 pp).** Nos anos recentes, o universo actual inclui empresas que só entraram nos índices depois. Em 2024 são 48 dos 198 trades, todas com a entrada registada na Wikipedia depois da data, por isso não é erro de ticker.
- **As empresas que saíram e ainda cotam** ficam com 19% do nocional e rendem −93 bps por trade, contra +74 dos restantes.
- **Cenário central dos mortos:** as fusões rendem como os nomes que ficaram e as saídas por perda de capitalização rendem como as empresas que saíram e ainda cotam. O motivo vem da coluna Reason da Wikipedia.

**Reajuste** (grelha de alloc × M1 × piso, sozinha ao fecho; P(1.º) optimista / central / pessimista):

| Configuração | P(1.º) | P(≥ 30%) |
| --- | --- | --- |
| 0,8×, sem M1, piso 85% (base) | 29,9 / 25,7 / 16,5 | \~0 |
| 1,2×, M1b, piso 85% (recomendação) | 34,7 / 29,7 / 17,9 | \~0 |
| 1,4×, M1b, piso 88% (melhor da grelha) | 35,6 / 31,4 / 18,4 | \~0 |
| Sem EAP, calls de QQQ 15% (exploratório) | — / 10,3 / — | 3,2% (11,5% com tendência) |

- A melhor da grelha fica +1,7 pp acima da recomendação, abaixo dos +2 pp exigidos, por isso a recomendação mantém-se. O leave-one-year-out não mostra inflação (S = 0).
- As calls por cima da EAP deixam de ser elegíveis (DQ 1,4–4%), porque o universo da época tem quedas de um dia nas empresas que depois saíram dos índices.
- No intradiário pessimista, só 0,8× ou 1,0× com piso 90% e M1 0,25 são elegíveis (P(1.º) 25–27%, exploratório).

**O que muda:**

- O prémio real é \~3–5% em fev–mar a 0,8×, e não 13–14%.
- A recomendação fica: EAP com 10 nomes, prioridade por vol e entrada em R−1, a 1,2× com M1b e piso 85%, sem calls. Com o DD intradiário, 1,0× com piso 90%.
- Os +30% deixam de ser um alvo realista. A P(1.º) de \~30% é contra adversários sintéticos quase sem alfa.
- Pendentes: os preços das empresas mortas (Bloomberg), o fill da IBKR paper e o teste-sombra com o EVTS depois de 4/12 (shadow\_evts.py).

### Fundamentais (pré-registo 19)

Quem sai dos índices define-se pelo preço e pela liquidez, não pelo balanço, e nenhum filtro baseado nisso melhora a carteira. Fundamentais dos frames XBRL da SEC, com 95 dias de atraso para não olhar para a frente; F-score de Piotroski. Pré-registo 19 (PREREG19.md), em commit antes de correr.

| Medianas | F-score | ROA | CFO/activos | Passivo/activos |
| --- | --- | --- | --- | --- |
| Ficaram nos índices | 0,71 | 4,7% | 9,2% | 0,57 |
| Mortas (saíram e deixaram de cotar) | 0,67 | 3,4% | 8,7% | 0,53 |
| Saíram e ainda cotam | 0,67 | 3,2% | 6,9% | 0,49 |

- **Prever quem sai:** com o preço, AUC 0,865; com preço e fundamentais, 0,869. Só com fundamentais, incluindo as mortas, 0,55.
- **EAP dos frágeis no grupo em risco:** em fev–mar, −60 bps contra +67 bps dos fortes. Com 34 eventos frágeis o intervalo vai de −332 a +588 bps, por isso não decide nada.
- **Filtros na carteira (1,2×, P(1.º) otimista / central / pessimista):** sem filtro 34,7 / 29,7 / 17,9; sem os em risco 29,0 / 26,4 / 20,5; sem os em risco e frágeis 33,3 / 29,9 / 19,3, não elegível num cenário. Ambos falham.
- **Leitura:** os nomes em risco são também os que pagam o prémio, e tirá-los custa mais alfa do que o risco que poupa. As mortas têm balanços de empresas normais (sobretudo fusões), por isso o cenário pessimista dos PREREG17/18 é pouco provável.

### Veto por filings e "não recupera" (pré-registo 20)

Nada muda a recomendação. Prever quem não recupera funciona, mas esses nomes são os que mais pagam a EAP; o veto por filings é neutro. Pré-registo 20 (PREREG20.md), em commit antes de correr; índice de filings da SEC de 2 317 CIK (3,1 M filings).

| Teste | Veredicto | Número principal |
| --- | --- | --- |
| "Não recupera" dentro dos em risco (filtro R2) | Falha | AUC 0,73 \[0,68; 0,77\]; o terço previsto rende +332 bps em fev–mar contra +12; −2,7 pp de alfa, −3,7 pp de P(1.º) |
| Veto por filings (3.01, NT 10-K/Q, 4.01/4.02, 1.03, 90 dias antes de R−1) | Não se adopta | Bandeiras em 4,7% dos eventos das mortas não-fusão contra 1,9% dos que ficaram (razão 2,5 < 3); custo −0,01 pp de alfa, P(1.º) 29,6% contra 29,7% |
| Potência dos preços das mortas não-fusão | Quase nenhuma | \~97 trades escolhidos; o IC apanha o ponto médio em \~90% dos casos |

**"Não recupera".** O risco de não recuperar, quando se vê antes, é pago no anúncio. Os −93 bps das empresas que saíram vêem-se depois do facto: muitas saíram por causa de más reações aos resultados.

**Veto.** Em fev–mar as bandeiras quase não distinguem as mortas não-fusão (1,8%) dos que ficaram (1,3%). Pode ficar como registo para o LLM, sem poder de veto.

**Mortas.** Os "44 deslistados" do pré-registo 17 eram o código Bloomberg de ticker deslistado, que inclui fusões (Rosetta Resources, Compuware). Pelos filings, \~85% dos eventos das mortas são de empresas que acabaram compradas. Com as taxas dos que ficaram, as compradas dão \~400 trades e 30–40% de hipótese de separar os cenários (exploratório).

### P(≥ 30%) no pior cenário (pré-registos 21 e 22)

No pior cenário, a maior P(≥ 30%) é 17,4%, com puts de QQQ sozinhas; juntar a EAP não cabe no orçamento de DD. Pior cenário: DD intradiário desde o pico, sem tendência do QQQ, mortas pessimistas. Pré-registos 21 e 22 (PREREG21.md, PREREG22.md), em commit antes de correr.

| Configuração (só opções, toda a folga) | P(≥ 30%) sem tendência / 2001–26 / com tendência | P(1.º) |
| --- | --- | --- |
| Put 0,94, 30 dias, piso 81% (escolhida) | 17,4 / 14,2 / 12,6% | 19,4% |
| Put 0,94, 30 dias, piso 83% | 14,4 / 11,4 / 10,2% | 18,3% |
| Put 0,94, 58 dias, piso 81% | 14,2 / 11,7 / 10,9% | 20,3% |
| Call 1,03, 30 dias, piso 81% | 13,9 / 16,1 / 28,8% | 16,8% |
| Referência anterior: calls 25%, 58 dias, piso 83% | 6,0 / — / 18,1% | 11,9% |

**O que conta:** prazo curto, piso baixo e tudo de uma vez. Recompras e straddles pioram. O teto teórico com piso 81% é 25%. Com custos stress (IV +0,10× o VXN, spreads a dobrar), a escolhida fica em 12,3%. A primeira corrida deu 24% por um erro do simulador (opções expiradas continuavam a seguir o spot); foi corrigido e a saída errada fica guardada.

**+30% não garante o 1.º lugar.** Por origem dos +30%, P(1.º | ≥ 30%) contra adversários agressivos e com o relatório em 1.º / 3.º / 8.º:

| Origem dos +30% | Adversários agressivos | Relatório 1.º / 3.º / 8.º |
| --- | --- | --- |
| Sem relação com o mercado | 70% | 95 / 93 / 48% |
| Calls (o mercado subiu) | 57% | 89 / 86 / 43% |
| Puts (o mercado caiu) | 83% | 100 / 99 / 53% |

**Puts reais.** Em 162 datas de opções do SPY (DoltHub, 2020–2026), as puts 6% abaixo do preço a \~28 dias custam 1,12× o VIX (p25–p75 1,08–1,17), abaixo dos 1,20× do modelo; as calls 3% acima, 0,72×, abaixo dos 0,80×. Compradas ao ask e seguradas até ao vencimento, as puts perderam 68% do prémio (55% sem tendência).

**EAP + opções.** Nenhuma das 72 combinações é elegível (DQ de 26–68%): as opções ocupam a folga até ao piso e o mínimo intradiário da EAP passa o limite. Uma versão que guarde folga para a EAP não foi testada.

**É uma aposta.** A escolhida acaba negativa em 74% das vezes, perto do piso (−15% a −19%) em metade, com resultado mediano de −14% e médio de −3,7%. Só faz sentido se o objectivo for a P(≥ 30%) e não a P(1.º). Riscos: piso a 81% deixa 1 pp até ao DQ (83% dá margem), venda diária de opções com dados de 15 minutos de atraso, e uma tese fraca para o relatório.

**Hedging não garante lucro constante.** Sem risco só se ganha a taxa sem risco (\~0,5–0,6% em fev–mar). O que se pode fazer é guardar um lucro já feito: o lock a +30% vende tudo e fica em caixa.

### ML, filtros e opções com folga reservada (pré-registo 23)

Nada muda a recomendação. O ML não escolhe melhores nomes do que a vol idiossincrática; prever quem cai muito funciona, mas esses eventos são os que pagam o prémio; e reservar folga para a EAP deixa as opções caber ao fecho sem subir a P(≥ 20%). Pré-registo 23 (PREREG23.md) e adenda 23b (UVOL/DVOL), em commit antes de correr.

| Teste | Veredicto | Número principal |
| --- | --- | --- |
| ML no ranking (LightGBM walk-forward, 23 variáveis; XGBoost, RandomForest e Ridge como referência) | Falha | IC fev–mar +0,010 (t 0,58); Δ alfa +2,3 pp \[−4,9; +8,8\]; não elegível |
| Filtro de cauda (P(r < −10%) acima do percentil 90) | Falha | AUC 0,695, mas os excluídos rendem +60 bps contra +24 em fev–mar; Δ alfa −1,2 pp |
| EAP + opções com folga reservada (res 4–10 pp) | Falha | Ao fecho, 24 de 108 elegíveis; a melhor dá P(≥ 20%) de 18,1% contra 22,7% da EAP sozinha; no pessimista nenhuma |
| Opções compradas pela classificação | Falha | P(≥ 20%) desce para 18–22%; P(1.º) igual ou −1 pp |
| Alternativas: reversão semanal, pre-FOMC, viragem do mês, noite | Nenhuma candidata | Só a noite tem Sharpe acima de zero (0,89), o mesmo do QQQ, e é negativa em fev–mar |
| UVOL/DVOL (proxy com \~1 500 ações) | Nenhum candidato | ρ com o QQQ a 5 e 20 sessões entre −0,08 e −0,01; com a EAP 0,00 |

O alfa é irregular. Por ano, a 1,2× no universo da época: +42,6% em 2014, +33,8% em 2016, +24,7% em 2026 e −29,1% em 2020, com 5 dos 13 anos negativos. As P(≥ X) da EAP sozinha são quase a fração destes 13 anos acima de X.

| Sem adversários, ao fecho, sem tendência | P(≥ 10%) | P(≥ 20%) | P(≥ 30%) | Mediana |
| --- | --- | --- | --- | --- |
| EAP 1,2× sozinha, mortas optimista | 30,9% | 22,8% | 0% | +7,6% |
| EAP 1,2× sozinha, mortas central | 30,7% | 22,7% | 0% | +4,8% |
| EAP 1,2× sozinha, mortas pessimista | 23,0% | 6,5% | 0% | −1,2% |
| Só puts 0,94 a 30 dias, piso 81% | 20,0% | 18,8% | 17,4% | −14,4% |

O que muda:

- A recomendação fica igual: EAP 1,2× com M1b, piso 85%, sem calls e sem filtros.
- Os preços das empresas compradas passam a decidir se os +20% são realistas (23% contra 6,5%). O pedido à Bloomberg deve incluí-las, não só as não-fusão.
- A soma de percentis (vol + LightGBM) ficou perto: +2,2 pp de alfa \[−0,9; +5,4\] e +3 pp de P(1.º). Não era escolhível pela regra e não é elegível; pode ficar registada no teste-sombra, sem decidir nada.
- Fuga apanhada antes de correr: a hora do anúncio, a estimativa de EPS e a surpresa estavam 100% em falta nas empresas que saíram dos índices, o que as denunciaria a um modelo. Foram reconstruídas da mesma fonte yfinance.

### Correlação negativa e timing por regime (pré-registo 24)

Nenhuma regra passa: a correlação negativa controla o risco mas não cria retorno, e o timing por regime não prevê o suficiente fora da amostra. Biblioteca de 8 estratégias (QQQ comprado e vendido, só à noite e só de dia, momentum, reversão, baixa e alta vol cobertas), 13 condições conhecidas na véspera, decisão semanal, walk-forward 2016–out/2026. Pré-registo 24 (PREREG24.md), em commit antes de correr.

| Regra | Retorno/ano | Sharpe \[IC95%\] | Sharpe − QQQ \[IC95%\] |
| --- | --- | --- | --- |
| A, células (tercil do VIX × tendência) | +16,8% | 0,82 \[0,32; 1,48\] | −0,09 \[−0,47; +0,26\] |
| B, LightGBM por estratégia | +7,3% | 0,33 \[−0,11; 0,84\] | −0,58 \[−1,23; −0,03\] |
| C, mínima variância | −0,3% | vol \~0 | — |
| QQQ comprado (referência) | +20,2% | 0,91 \[0,44; 1,53\] | — |

- A escolhe o QQQ em 77% das semanas. C põe 50% em QQQ comprado e 50% vendido: variância zero, retorno zero. Sem esse par (exploratório) junta noite, dia e baixa vol: +0,6%/ano com 5% de vol.
- Nas regras da WIC, a melhor elegível dá P(≥ 30%) de 0,6%; o QQQ a 2× dá 10% com 7% de DQ.
- Exploratório: com o DQ ≤ 0,5%, a P(≥ 30%) é 3% com Sharpe 1, 13% com 2, 31% com 3, 45% com 4 e 83% com 6.
- Duas correcções antes de ler os resultados (primeira corrida guardada): o descritivo usava o regime do próprio dia do retorno, e a regra C não optimizava por falta de escala.

Ficheiros: wic\_ml\_20261107/ (PREREG24.md, s24.py, FINDINGS24.md, x24\_minvar.py, x24\_sharpe.py), branch ccr-41562e25-8itdla.

### Edições anteriores da WIC e prémios

Os vencedores fizeram \~30% nas duas edições, com o mercado a cair. O voo para o Japão é da Divisão Trader. Fontes: WIC2026 Participant Overview (JPSI, 22/10/2026) e as páginas [WIC past](https://jpsi-association.com/wic/past), [live](https://jpsi-association.com/live) e [rules](https://jpsi-association.com/wic/rules) da JPSI.

| Edição | Período | Equipas | 1.º | 2.º | 3.º | QQQ no período |
| --- | --- | --- | --- | --- | --- | --- |
| WIC2025 | 15/dez/2025–13/mar/2026 | 16 universidades, 9 países | LMU Munique +33,3% | TU Munique +14,0% | Genebra +1,2% | −3,1% |
| WIC2024 | 2 meses (datas por confirmar) | 12 universidades, 9 países | TU Munique +28,4% | — | — | −6% a −10% (jan–mar 2025) |

- Individuais WIC2025 (top 10): de +54,1% (Sheffield) a +13,2% (UCLA). Os três da LMU fizeram +44,8%, +34,7% e +20,3%. A LMU ganhou também o prémio de opções (+46,2%).
- Relatório WIC2025: TU Munique 93/100, Toronto 86, Sheffield 79. A LMU ganhou o geral sem estar no top 3 dos relatórios.
- Só se publica o top 3 das equipas. O salto de +14% para +1,2% sugere que a maior parte das outras ficou perto de zero ou abaixo.

Prémios WIC2026:

| Prémio | Para quem | O que é |
| --- | --- | --- |
| Overall Performance Award | 1.º geral da Divisão Trader | Voos de ida e volta para o Japão (3 pessoas) |
| Most Valuable Player | Maior retorno individual (Trader) | TradingView Premium, 1 ano |
| AI Agent Award | 1.º–3.º da Divisão AI Agent | ChatGPT Pro ou Claude Max, até 12 meses |

Texto do site da JPSI ([WIC](https://jpsi-association.com/wic)): "Trader division, 1st place" — "Round-trip flights to Japan for all three members"; "AI Agent division, 1st – 3rd" — "Subscriptions such as ChatGPT Pro or Claude Max for up to 12 months, for every member". A [página da Divisão Trader](https://jpsi-association.com/wic/trader) repete: "1st overall — round-trip flights to Japan for the team's three members." A [da AI Agent](https://jpsi-association.com/wic/ai-agent) só lista as subscrições. Nenhuma página diz que uma equipa da AI Agent pode ganhar o voo. No PDF, os números ①②③ dos prémios correspondem aos ①②③ das categorias. Confirmar no grupo de WhatsApp depois da inscrição.

O que isto muda:

- A análise deste doc foi feita para a Divisão AI Agent (fev–mar, 36 sessões). O voo exige a Divisão Trader: 3 estudantes da mesma organização, três contas de US$1M somadas, 4/jan–25/mar (\~55 sessões), dados em tempo real e decisões humanas. A inscrição dupla é permitida.
- Pergunta respondida: o DD conta-se no fecho de cada sessão, desde o pico, e o capital inicial conta como pico. No Trader soma-se o NAV das três contas.
- A fasquia observada é \~30%, por isso a P(1.º) com adversários sintéticos (melhor adversário em +8% a +22%) era otimista para a Divisão Trader.
- Regra nova: aproveitar atrasos ou fills irrealistas do ambiente demo dá desclassificação imediata. Isto pesa no teste das MOC grandes em nomes ilíquidos.
- Pendente: as datas da WIC2024 e o rulebook de 2025 (/documents/wic2025-rulebook.pdf).

### Aposta final numa só sessão (pré-registo 27)

Uma única aposta binária no QQQ na última sessão, depois da EAP, leva a P(≥ 30%) de 17% para 37,5%. É a melhor forma de atingir um alvo num jogo desfavorável (Dubins–Savage), e o DD medido só ao fecho permite-a: uma aposta comprada na abertura e resolvida antes do fecho não cria picos intermediários. Sem edge, uma aposta justa que acaba em 1,30 ou em 0,81 ganha com probabilidade (1 − 0,81)/(1,30 − 0,81) = 38,8%; a simulação dá 39%. Pré-registo 27 (PREREG27.md), em commit antes de correr.

**Instrumento:** um digital sobre o QQQ numa só sessão (call ou put spread de 0–1 dias), pago a q × (1 + v), com v o custo (bid-ask e prémio de volatilidade): 10% na manchete, 5% e 20% como sensibilidade. Arrisca-se toda a folga até 81% do pico, com o payoff para acabar no alvo; perdendo, o NAV fica em 81% do pico, sem DQ. Adversários do pré-registo 26.

| Variante | Custo | P(≥ 30%) | P(1.º) A15 / A22 / A30 | P(pódio) | Mediana |
| --- | --- | --- | --- | --- | --- |
| EAP 1,4× sozinha (referência) | — | 0,2% | 30,5 / 25,2 / 21,5% | 44,7% | +6,1% |
| Só put 0,94 a 30 dias (melhor anterior) | — | 17,4% | 17,8 / 16,8 / 15,6% | 23,5% | −14,4% |
| EAP + aposta final até +30% | 10% | 37,5% | 31,9 / 29,2 / 25,7% | 40,1% | −10,3% |
| EAP + aposta final até +30% | 20% | 34,4% | 29,8 / 27,2 / 24,0% | 38,0% | −10,5% |
| Só a aposta, no 1.º dia | 10% | 35,5% | 28,5 / 26,1 / 22,9% | 35,1% | −19,0% |
| EAP + aposta final até ao líder + 3 pp (put) | 10% | 10,4% | 40,4 / 34,3 / 28,9% | 43,1% | −10,0% |

**Passa as duas regras.** Para os +30%: 37,5% ≥ 17,4% + 5 pp, 34,4% com custos de 20% e 37,5% nos caminhos de 2001–26. Para o 1.º lugar: a aposta até ao líder dá +9 pp contra A22 e fica à frente em todas as fasquias; exige a classificação visível.

**Alvos maiores pioram:** a +35% e a +40%, a P(≥ 30%) cai para 32% e 28%. Call ou put dá quase o mesmo; a put dá um pouco mais de P(1.º), porque ganha quando os adversários perdem.

**O que pode deitar isto abaixo:** (1) se as opções não forem permitidas, não há forma de fazer o digital; (2) o custo real das spreads de 0–1 dias do QQQ, a medir no período de testes; (3) fills irrealistas no paper dão DQ, por isso as ordens devem ser limitadas e registadas com o preço de mercado; (4) o relatório tem de apresentar a aposta como estratégia óptima de torneio, senão perde lugares; (5) o LLM tem de tomar a decisão final em tempo real, com regras escritas antes; (6) perde \~61% das vezes, e o valor esperado da aposta é negativo.

### Aposta final e mediana (pré-registo 28)

Com a mediana ≥ 0, a melhor P(≥ 30%) é 9%: a P(≥ 30%) alta e a mediana positiva não são compatíveis. Testei apostar só quando o NAV da sessão 35 está abaixo de um limiar e apostar só metade da folga. A hipótese (as trajetórias atrás podem apostar sem baixar a mediana) falhou: atrás, a folga até ao piso é pequena e as odds são más. Pré-registo 28 (PREREG28.md), em commit antes de correr.

| Regra da aposta final (put, custos 10%) | Apostam | P(≥ 30%) | Mediana | Média | P(1.º) A22 | P(pódio) |
| --- | --- | --- | --- | --- | --- | --- |
| Sempre, toda a folga | 98% | 37,4% | −10,4% | +2,8% | 29,2% | 40,0% |
| Sempre, metade da folga | 98% | 28,9% | −2,0% | +3,4% | 25,5% | 37,3% |
| Só se NAV < 1,10 | 70% | 16,4% | −10,4% | +3,3% | 30,9% | 43,3% |
| Só se NAV < 1,06 | 52% | 9,0% | +7,5% | +3,6% | 29,7% | 47,3% |
| EAP 1,4× sozinha | 0% | 0,2% | +6,1% | +3,8% | 25,2% | 44,7% |

**A regra não aceita nenhuma:** a única com mediana ≥ 0 tem 9% de P(≥ 30%), longe dos 22,4% exigidos. Com custos de 20% e nos caminhos de 2001–26, os números mudam menos de 1 pp.

**Metade da folga é o meio-termo:** 28,9% de P(≥ 30%), ainda acima do corte do pré-registo 27, com mediana −2%.

**Apostar só se NAV < 1,06 melhora a EAP sozinha em quase tudo:** P(1.º) +4,5 pp, P(pódio) +2,6 pp e mediana +1,4 pp, com a média 0,2 pp abaixo. É a melhor opção se o prémio for do 1.º ao 3.º, mas não serve para os +30%.

**A média é positiva em todas.** A mediana negativa vem da assimetria (muitas perdas moderadas, alguns ganhos grandes), não de um valor esperado negativo.

### Aposta só com os lucros (pré-registo 29)

Arriscar só os lucros acima de +2% dá P(≥ 30%) de 31% com mediana +2% e 59% das trajetórias acima de zero. Com toda a folga, a aposta tem de ganhar mais do que arrisca, por isso ganha \~40% das vezes e a mediana fica no resultado de perder. Arriscando só os lucros, a trajetória nunca acaba abaixo de +2%; abaixo disso aposta-se toda a folga, porque essas trajetórias já estão abaixo da mediana. Pré-registo 29 (PREREG29.md), em commit antes de correr.

| Regra da aposta final (put, custos 10%) | P(≥ 30%) | P(> 0) | Mediana | P(1.º) A22 | P(pódio) |
| --- | --- | --- | --- | --- | --- |
| Lucros acima de +2%, toda a folga abaixo (recomendada) | 31,0% | 59% | +2,0% | 25,8% | 40,3% |
| Lucros acima de +4%, toda a folga abaixo | 29,6% | 59% | +4,0% | 26,1% | 42,5% |
| Lucros acima de +2%, sem aposta abaixo | 25,2% | 55% | +2,0% | 21,6% | 36,1% |
| Toda a folga sempre (pré-registo 27) | 37,4% | 41% | −10,4% | 29,2% | 40,0% |
| Metade da folga sempre (pré-registo 28) | 28,9% | 40% | −2,0% | 25,5% | 37,3% |
| EAP 1,4× sozinha | 0,2% | 55% | +6,1% | 25,2% | 44,7% |

**Passa a regra:** com custos de 20% dá 28,5%, mediana +2% e 59% acima de zero; nos caminhos de 2001–26 é igual.

**O +2% conta:** arriscando os lucros acima de 0%, muitas trajetórias acabam exactamente em 0% e só 36% ficam acima de zero. Com +4%, a mediana sobe para +4% por 1,4 pp de P(≥ 30%).

**Para o 1.º lugar,** a aposta até ao líder (pré-registo 27, P(1.º) 34%) continua melhor, mas com mediana −10%.

### Custo real e várias apostas (pré-registo 30)

O custo de bid-ask das spreads de QQQ de 1 dia equivale a \~9%, perto dos 10% usados; várias apostas ao longo da janela não sobem a P(≥ 30%). Nenhum dado do repositório ou da Drive tem opções de índice de 0–1 dias (DoltHub só tem vencimentos a 2+ semanas; as amostras Cboe só têm SPX mensal e AAPL), por isso medi nas cadeias reais do QQQ no Yahoo, ao fecho de 6/11/2026. Pré-registo 30 (PREREG30.md).

| Vencimento | Entrada (sobre o mid) | Saída num ganho (% da largura) | Custo equivalente |
| --- | --- | --- | --- |
| 1 dia | 4,5% (3,1–6,9%) | 4,4% | 9,3% |
| 2 dias | 6,5% | 3,8% | 10,7% |
| 3 dias | 7,4% | 4,5% | 12,5% |

**O que falta no custo:** o prémio de volatilidade (o mid pode estar acima da probabilidade real) e mais do que uma fotografia, que foi tirada depois do fecho, num dia de volatilidade alta. O custo real deve ficar entre 10% e 20%.

| Várias apostas só com os lucros (custo 10%) | P(≥ 30%) | Acima de zero | Mediana | Média |
| --- | --- | --- | --- | --- |
| Só na última sessão (pré-registo 29) | 31,0% | 59% | +2,0% | +3,1% |
| Sessões 18 e 36 | 31,0% | 65% | +2,0% | +4,2% |
| Sessões 12, 24 e 36, intermédias só se NAV ≥ +10% | 31,6% | 54% | +2,0% | +2,8% |
| Sessões 12, 24 e 36, com qualquer lucro | 33,7% | 49% | −3,1% | +2,7% |
| Sessões 9, 18, 27 e 36 | 29,2% | 47% | −3,1% | +1,6% |

**A regra mantém a aposta única:** a melhor com mediana positiva dá +0,6 pp (eram precisos +2). Mais apostas pagam mais custos, e só sobem a P(≥ 30%) quando arriscam qualquer lucro, com a mediana a voltar a negativa.

**A aposta extra a meio é quase grátis:** P(≥ 30%) igual, mais trajetórias acima de zero e média mais alta. Depois de perder a meio, o NAV fica em +2% e o M1b reduz a EAP, o que estabiliza o resto da janela.

### Divisão AI Agent (pré-registo 26)

Na AI Agent, a EAP 1,4× com M1b sozinha é a melhor configuração contra qualquer fasquia de adversários, e passa a regra: +2,2 pp de P(1.º) sobre a 1,2×. Mesmas janelas fev–mar do pré-registo 18 (36 sessões), DD ao fecho, 15 equipas, DQ como derrota e sem corte de elegibilidade. Pré-registo 26 (PREREG26.md), em commit antes de correr.

**Adversários:** a divisão é nova, por isso há três fasquias, com o melhor adversário em +15% (A15), +22% (A22, a manchete) ou +30% (A30), mais os adversários antigos (TN, melhor entre +8% e +22%). Com os antigos, o motor reproduz os 29,7% e 31,4% do pré-registo 18.

| Configuração | P(1.º) A22 | A15 | A30 | Antigos | Mortas pessimistas | P(pódio) A22 | P(≥ 30%) | Mediana | DQ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| EAP 1,4×, piso 88% (recomendada) | 25,2% | 30,5% | 21,5% | 31,4% | 13,3% | 44,7% | 0,2% | +6,1% | 0,0% |
| EAP 1,4×, piso 85% (escolhida pela regra) | 25,2% | 30,6% | 21,5% | 31,5% | 13,5% | 45,0% | 0,2% | +6,1% | 2,4% |
| EAP 1,2×, piso 85% (anterior) | 23,0% | 28,2% | 19,6% | 29,7% | 12,3% | 43,4% | 0,0% | +4,8% | 0,0% |
| EAP 1,4× + put 0,97 a 58 dias, meia folga | 23,1% | 27,3% | 19,9% | 28,0% | 12,9% | 39,2% | 5,5% | +0,6% | 8,0% |
| EAP 1,4× + call 1,03 a 58 dias, meia folga | 21,8% | 26,2% | 18,7% | 27,4% | 10,9% | 40,6% | 6,3% | +0,9% | 6,8% |
| Só put 0,94 a 30 dias, piso 81% | 16,8% | 17,8% | 15,6% | 19,0% | 16,8% | 23,5% | 17,4% | −14,4% | 0,0% |

**A regra muda a recomendação.** A 1,4× passa os cinco critérios: +2,2 pp, à frente em A15, A30 e nos antigos, LOYO de 25,1% (sem inflação) e à frente com mortas pessimistas. Escolhe-se a 1,4× em todos os 13 anos deixados de fora.

**Piso 88% e não 85%.** A regra escolhe o 85% por 0,04 pp, mas com 2,4% de DQ e um pior DD real de −19,8%, a 0,2 pp da desclassificação. O 88% tem a mesma P(1.º), DQ \~0 e pior DD real de −18,2%.

**P(pódio):** 45,0% contra 43,4% (+1,6 pp). Se o prémio for do 1.º ao 3.º, a diferença fica abaixo do corte.

**Opções:** pioram a P(1.º) e a P(pódio). As calls só ajudam com tendência de subida (24,9% contra 21,5% nos caminhos com tendência); as puts só num crash (42–46% com um dia de −8%).

**Porque muda agora:** a vantagem da 1,4× era +1,7 pp contra os adversários antigos (abaixo do corte) e é de +1,9 a +2,4 pp contra as fasquias calibradas. A ordem é a mesma em todos os campos.

### Divisão Trader (pré-registo 25)

Na Divisão Trader, contra adversários cujo melhor faz +30%, a melhor P(1.º) é \~19% e a recomendação não muda. Esta secção corrige três problemas da análise anterior: estava calibrada para a Divisão AI Agent, os adversários ficavam em +8% a +22%, e as configurações com DQ acima de 0,5% eram eliminadas antes de comparar. Pré-registo 25 (PREREG25.md), em commit antes de correr.

**Regras simuladas:** 57 sessões desde 4/jan (as de 4/jan a 25/mar de 2027), DD ao fecho desde o pico com o capital inicial como pico, DQ a 20%, 16 equipas, RRF 70/30 com o nosso relatório em 1.º, 3.º ou 8.º. EAP no universo da época, empresas mortas no cenário central. O DQ conta como derrota dentro da P(1.º), sem corte à parte.

**Janeiro não acrescenta alfa.** A 1,2×, a EAP rende 4,6% na janela Trader contra 4,7% em fev–mar, com mais variância (16 contra 14 pp por ano). As sessões de janeiro rendem −1,5% em bruto, negativas em 8 de 13 anos (t ≈ −0,7, ruído).

**Adversários:** duas famílias calibradas para que o melhor faça +30% em mediana. Na A, o 2.º e o 3.º ficam em +17% e +11%; na B, em +15% e +8,5% (em 2025 foram +14% e +1%). A22 e A38 servem de sensibilidade.

| Configuração | P(1.º) A30 | B30 | 2001–26 sem tendência | Dia de −8% | Mortas pessimistas | P(≥ 30%) | Mediana | DQ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| EAP 1,4×, piso 85% (melhor da grelha) | 18,8% | 20,5% | 18,3% | 24,5% | 11,0% | 2,0% | +1,4% | 0,4% |
| EAP 1,2×, piso 85% (recomendada) | 18,0% | 20,0% | 17,5% | 24,0% | 11,4% | 0,0% | +0,2% | 0,0% |
| EAP 1,4× + put 0,94 a 86 dias, meia folga | 17,4% | 18,9% | 16,8% | 32,0% | 10,6% | 5,7% | −2,2% | 5,6% |
| Só put 0,94 a 86 dias, piso 81% | 16,5% | 17,0% | 14,9% | 45,3% | 16,5% | 15,5% | −8,9% | 0,0% |
| EAP 1,4× + call 1,03 a 86 dias, meia folga | 15,9% | 17,6% | 16,5% | 17,2% | 8,5% | 5,2% | −2,0% | 4,5% |
| Só put 0,94 a 30 dias com recompra, piso 81% | 15,4% | 15,5% | 13,5% | 34,9% | 15,4% | 17,8% | −14,6% | 0,0% |

**A regra mantém a recomendação.** A EAP 1,4× fica +0,8 pp acima da actual (eram precisos +2 pp) e cai para 10,9% no leave-one-year-out. A P(1.º) da EAP vem de 4 anos: 64–66% em 2014 e 2016, 39–43% em 2018 e 2019, e menos de 3% em 8 dos 13 anos.

**As opções não ajudam a ficar em 1.º.** Calls por cima da EAP descem a P(1.º), porque os adversários estão comprados no mesmo mercado. As puts só ganham quando o mercado cai: com um dia de −8%, a put sozinha sobe para 45%.

**O corte de elegibilidade antigo quase não mudava nada.** Com ele, a melhor seria a EAP 1,4× com piso 88% (18,2%). Pisos sem margem até ao DQ (81%) desclassificam 23% das trajetórias sem mudar a P(1.º).

**Exploratório (pós-hoc):** com a EAP 1,2×, a P(1.º) é 26 / 20 / 7% com o relatório em 1.º / 3.º / 8.º. A EAP só desde 1/fev dá P(1.º) de 23% (1,2×) e 25% (1,4×), com P(≥ 30%) de 0% e 7,6%. Foi escolhida depois de ver janeiro negativo, por isso fica para o teste-sombra.

### Reprodução e fontes

Tudo está no branch isolado [wic-audit-claude-20261105](https://github.com/KuroTori21/AlgoT/tree/wic-audit-claude-20261105). O `main` não foi tocado e nenhuma ordem foi enviada. Os scripts e resultados estão em `TradingV2/research/ACOES/wic_audit_20261105/` (com README e ordem de execução). As hipóteses e os critérios de corte estão no docstring de cada script, escritos antes de correr.

- **Dados brutos:** `TradingV2/data/wic_audit_20261105/`, recolhidos pelo [workflow 41988278081](https://github.com/KuroTori21/AlgoT/actions/runs/41988278081) a 5/11/2026. Incluem preços Yahoo v8 desde 2012 (550 ações + QQQ, SPY, VIX), datas yfinance, calendário público da Nasdaq 2014–2026 (179 mil linhas), Polymarket Gamma/CLOB (2.058 mercados Fed e EPS, 1,35 M pontos horários) e os artefactos dos runs anteriores convertidos para CSV.
- **Ficheiros de resultados (`out/`):** `eap_stats.csv` e `eap_per_year.csv`; `dd_continuous_*.csv`, `dd_windows_*.csv`, `dd_boot_*.csv` e `stress.csv`; `fed_tests_poly.csv`, `fed_signal_poly.csv` e `fed_eap.csv`; `eps_odds_tests.csv` e `eps_odds_matched.csv`; `volsize.csv`.
- **Limites desta versão:** não há dados Kalshi (recolha ainda a correr), NOCP, calendário point-in-time, empresas deslistadas nem opções históricas. Todas as médias são retornos sobre os $1M iniciais, sem capitalização.

Secções do torneio (5/11): scripts, dados e resultados em `TradingV2/research/ACOES/wic_torneio_20261105/` no branch `ccr-b1e1bb3e-e2ygjk` (README com a ordem de execução). `wic_layer.py` é o simulador das camadas (`CONTIG=1` para janelas contínuas; `PESS=1` para o limite intradiário pessimista); `curva_final.py`, `dd_dist.py` e `dd_floor.py` geram as tabelas destas secções; `spy_monthly.py` e `spy_check.py` fazem a verificação com opções reais do SPY (DoltHub `post-no-preference/options`). O VXN vem do Yahoo (^VXN). Regras: *WIC2026 Participant Overview*, JPSI, 22/10/2026.

**Secções de 5/11 à tarde** (Híbridos, Robustez, Cenários, Alternativas, Recomendação actual): `TradingV2/research/ACOES/wic_hibridos_20261105/` no branch `ccr-ffa2d2bf-mi1yfs`. Nada em produção foi tocado.

- **Pré-registos:** `PREREG.md` a `PREREG4.md`, cada um num commit antes de correr (2638ce5, 335fda5, 601093f, 5811261). Os scripts conferem o SHA-256 e não correm se o ficheiro mudar. As únicas análises pós-hoc são `explore_k4.py` e a janela do hold planeado no teste das notícias; estão marcadas como tal.
- **Resultados:** `FINDINGS.md` a `FINDINGS4.md`, com as tabelas brutas em `out/`.
- **Scripts:**
  - `eap_runs.py`, `eap_runs2.py` e `eap_runs3.py` correm as janelas EAP no simulador da auditoria, com o P&L decomposto em alfa diário e beta das ações (`sim2.py` e `sim3.py`, por substituições exactas).
  - `layer2.py` a `layer5.py` são o motor das camadas: VXN alinhado, bruto ≤ 2×, piso, DQ, lock, os três modos de medição, calls e call spreads.
  - `run_all.py`, `run_bloco3.py`, `run_matriz.py` e `run_t1.py` correm os braços; `e_u2_news.py` faz o teste das notícias.
- **Verificações:** V0–V7, todas passaram. Por exemplo, o motor novo reproduz o anterior bit a bit quando as substituições estão inactivas.
- **Dados:**
  - QQQ e ^VXN do Yahoo, com o VXN conferido com a Cboe;
  - CPI do Bloomberg ECO (Drive, BBT/3/ECO\_US\_Prices.xlsx);
  - NFP por regra, conferida com o BBT/6/ECO\_Releases.xlsx (91% das datas);
  - FOMC do `scheduled_fomc.csv` do repo;
  - tudo o resto vem da auditoria, por isso é preciso o checkout de `wic-audit-claude-20261105` em `WIC_AUDIT_DIR`.

**Secções de 6/11** (O teto dos +30%, Torneio, DQ operacional, Calls ligadas pela classificação): `TradingV2/research/ACOES/wic_hibridos_20261105/` no branch `ccr-2eb2404d-awg57t`. Nada em produção foi tocado.

- Pré-registos: PREREG5.md e PREREG6.md, cada um num commit antes de correr (debb19f, 57d4ac4). Resultados em FINDINGS5.md e FINDINGS6.md, com as tabelas em `out/t5*` e `out/t6*`.
- Scripts: `run_prereg5.py` e `run_prereg6.py` correm os testes. `layer6.py` acrescenta as falhas e as guardas, `layer7.py` a compra adiada das calls e `torneio.py` os adversários e a P(1.º). `explore_t5_drift.py` (sensibilidade à tendência) é pós-hoc.
- Verificações V8–V13: todas passaram (Δ 0). O teto teórico e a previsão do QQQ foram verificações ad hoc, não guardadas no repositório.

Secção de 6/11 (Autocorrelação da EAP): TradingV2/research/ACOES/wic\_autocorr\_20261106/ no branch claude/wic-eap-autocorrelation-analysis-ourlcf. Pré-registo PREREG7.md em commit antes de correr (5cd6af2); resultados em FINDINGS7.md e out/. autocorr.py corre as 8 hipóteses e as secundárias; prefix\_check.py confirma a causalidade por prefixo em 3 cortes (apanhou e corrigiu uma fuga no universo dos pares, sem mudar os números); explore\_timing.py, explore\_portfolio.py e explore\_pnl.py são pós-hoc. Precisa dos checkouts de wic-audit-claude-20261105 (WIC\_AUDIT\_DIR) e de ccr-2eb2404d-awg57t (WIC\_HIB\_DIR). Nada em produção foi tocado.

Secção de 6/11 (Testes recomendados): mesma pasta e branch. Pré-registo PREREG8.md (commit 6bb0b47); resultados em FINDINGS8.md e out/t8\_\*. t1\_theta.py (layer8.py: gatilho com o alfa que falta e pior DD por trajetória), t2\_stress.py (sim4.py: regra de stress com NAV com hedge, choque dinâmico e teto por setor), t3\_volume.py, t4\_surv.py. Short volume FINRA 08/2018–10/2026 em data/finra\_shvol.csv.gz (fetch\_finra.py). Verificações V14 e V15: Δ 0.

Secção de 6/11 (Cauda, dificuldade e short selling): mesma pasta e branch. Pré-registo PREREG9.md (commit 51dd229); resultados em FINDINGS9.md e out/t9\_\*. p9\_events.py (evento), p9\_portfolio.py (carteira e torneio), explore\_b2\_slots.py (vagas, exploratório). Short interest FINRA em data/finra\_si.csv.gz (fetch\_short\_interest.py).

Secção de 6/11 (Combinação para P(≥ 30%)): mesma pasta e branch. Pré-registo PREREG10.md (commit 7a25f49); resultados em FINDINGS10.md e out/t10\*. layer9.py abre o strike e o prazo das calls do 1.º dia (V16: Δ 0); p10\_grid.py corre a grelha; explore\_p30.py (exploratório) compara as combinações com o kill-switch.

Secção de 6/11 (Controlo do DD): mesma pasta e branch. Pré-registo PREREG11.md (commit 47f5a7a); resultados em FINDINGS11.md e out/t11\*. layer10.py (redução do livro EAP pela folga até ao DQ; V17: Δ 0), sim5.py (teto por noite; V18: Δ 0), p11.py.

Secção de 6/11 (Entrada em R−1 e camada intradiária): TradingV2/research/ACOES/wic\_r1\_intra\_20261106/ no branch ccr-97960405-vhq8ro. Pré-registo PREREG12.md (commit 2aaaf06); resultados em FINDINGS12.md e out/t12\*. sim6.py (sim4 com entrada em R − LAG; V19: Δ 0), layer11.py (layer10 com a camada intradiária e a abertura do QQQ nos caminhos; V20: Δ 0), eap\_windows12.py, p12.py. Exploratórios: explore12.py (grelha de piso, calls e M1b), explore12\_sec.py e explore12\_sec2.py (calendário SEC). Precisa dos três checkouts anteriores (env.sh). Na Drive só há amostras de um dia, por isso o stop intradiário foi limitado entre sair no stop e sair no mínimo do dia.

Secção de 6/11 (Datas confirmadas e confirmação da entrada em R−1): mesma pasta e branch. Pré-registo PREREG13.md (commit fb41f20); resultados em FINDINGS13.md e out/t13\*. p13\_windows.py (calendário com duas fontes, janelas stress e SEC; V22: Δ 0), p13.py close|pess (confirmação congelada; V21: Δ 0), t3\_2021.py (exploratório).

Secção de 6/11 (Calls pela classificação na nova base): mesma pasta e branch. Pré-registo PREREG14.md (commit 73bee6b); resultados em FINDINGS14.md e out/t14\*. p14.py close|pess grid0|grid1|final (V23: Δ 0).

Secção de 6/11 (Validação da base nova): TradingV2/research/ACOES/wic\_validacao\_20261106/ no branch ccr-cee99e74-qxmkrp. Pré-registo PREREG15.md (commit 4e4ef87); resultados em FINDINGS15.md e out/t15\_\*. sim7.py (sim6 com a entrada desfasada evento a evento; V24: Δ 0), windows15.py (janelas; V25 e V26: Δ 0), p15.py feb|seas|t38 (V27 reproduz o pré-registo 13; V28: ±0,3 pp). Precisa dos quatro checkouts anteriores (env.sh). O branch ccr-97960405-vhq8ro não tinha o PREREG12\_FREEZE.json; foi reconstruído a partir do commit 2aaaf06. Cobertura da Wikipedia e do Yahoo medida a 6/11/2026 (análise ad hoc, não pré-registada).

Secção de 6/11 (Eixos estruturais): TradingV2/research/ACOES/wic\_eixos\_20261106/ no branch ccr-3463ad68-dbzy1e. Pré-registo PREREG16.md (commit f6e4038); resultados em FINDINGS16.md e out/t16\_\* (commits a234561 e 06d3bb8). sim8.py (sim7 com entrada MOO e reforço intradiário; V29–V31), layer12.py (layer11 com hedge parcial, SQQQ e reduzir à frente; V32, V34), windows16.py, p16.py main|t5|seas, collect\_univ.py e univ16.py (universo alargado; dados em TradingV2/data/wic\_eixos\_20261106/, Nasdaq Trader, screener da Nasdaq e Yahoo a 6/11/2026; V35). Exploratórios: explore16\_alloc.py, x16\_impact.py e x16\_liqcap.py. Precisa dos cinco checkouts anteriores (env.sh) e dos PREREG12\_FREEZE.json e PREREG15\_FREEZE.json reconstruídos localmente (os .md não mudaram desde 2aaaf06 e 4e4ef87). A Drive (BBT, Cboe Free Samples, Cboe Samples) não tem dados de leilões de ações, por isso o custo do leilão de abertura é uma hipótese com ponto de equilíbrio.

Secção de 6/11 (Sobrevivência com as listas Bloomberg): TradingV2/research/ACOES/wic\_surv\_20261106/ no branch ccr-3463ad68-dbzy1e. Pré-registo PREREG17.md (commit 0d065f4); resultados em FINDINGS17.md e out/t17.txt (commit 480907d). surv17.py verify|run (V36–V38), collect\_surv.py e collect\_surv\_dates.py (preços Yahoo e datas yfinance das empresas que saíram e ainda cotam), x17\_decomp.py (exploratório). Listas da Bloomberg (Drive BBT/8) em TradingV2/data/wic\_surv\_20261106/bbg/; pedido dos preços em falta em pedido\_bloomberg\_mortos.csv.

Secção de 6/11 (Universo da época completo e reajuste): TradingV2/research/ACOES/wic\_pit\_20261106/ no branch ccr-3463ad68-dbzy1e. Pré-registo PREREG18.md (commit 663c074); resultados em FINDINGS18.md e out/t18\_run.txt (commit de86667). pit\_members.py (composição Wikipedia + Bloomberg e validação), collect\_pit.py (bolsa e preços Yahoo), pit18.py dates|verify|run (V39–V41), exploratórios x18\_diag.py e x18\_alt.py, shadow\_evts.py (teste-sombra EVTS). Páginas da Wikipedia lidas a 6/11/2026 em TradingV2/data/wic\_pit\_20261106/.

Secção de 6/11 (Fundamentais): TradingV2/research/ACOES/wic\_fund\_20261106/ no branch ccr-3463ad68-dbzy1e. Pré-registo PREREG19.md (commit 0418b82); resultados em FINDINGS19.md e out\_t19.txt (commit 7920b2d). map\_cik.py (CIK pela pesquisa de entidades do EDGAR), collect\_frames.py (frames XBRL da SEC), fund19.py verify|run (V42–V43). Dados em TradingV2/data/wic\_fund\_20261106/.

Secção de 6/11 (Veto por filings e "não recupera"): TradingV2/research/ACOES/wic\_veto\_20261106/ no branch claude/wic-eap-artifact-analysis-f0druw. Pré-registo PREREG20.md (commit bafa025); resultados em FINDINGS20.md e out/t20.txt (commits e6c1437 e f9b0f5a). collect\_sec.py (índice de filings de data.sec.gov/submissions, hora de aceitação em UTC convertida para ET), veto20.py verify|run (V44–V46), x20\_power.py (exploratório). Dados em TradingV2/data/wic\_veto\_20261106/. Precisa dos checkouts anteriores (env.sh); o PREREG12/15\_FREEZE.json foram reconstruídos localmente como antes.

Secção de 6/11 (P(≥ 30%) no pior cenário): TradingV2/research/ACOES/wic\_p30\_20261106/ no mesmo branch. Pré-registos PREREG21.md (commit d96f756) e PREREG22.md (commit cce0a31); resultados em FINDINGS21.md, FINDINGS22.md, out/t21.txt e out/t22.txt (commits c5b07b5 e ccc50dc). opt21.py (simulador só de opções; V47: igual ao layer12, Δ 0; V48 e V48b), opt22.py (EAP + opções; V50–V51b: Δ 0), p21.py e p22.py verify|run, collect\_spy\_opts.py (cadeias SPY da DoltHub post-no-preference/options, 162 datas 2020–2026), x22\_dist.py (descritivo). A corrida com o erro da expiração fica em out/descartado\_bug\_expiracao/. Os ficheiros C1 TBT da pasta "Cboe Samples" não foram usados: exigem login e passam o limite de 10 MB do conector.

Secção de 7/11 (pré-registo 23): TradingV2/research/ACOES/wic\_ml\_20261107/ no branch ccr-41562e25-8itdla. PREREG23.md (commit b6ad83b) e PREREG23b.md (07fea53) antes de correr; resultados em FINDINGS23.md e out/. ml23.py faz o ML e o filtro (V53, V54), opt23.py e p23opt.py a folga reservada e o gatilho (V52), t5.py as alternativas e o UVOL/DVOL; x23\_eapdist.py é exploratório. Os \*\_FREEZE.json dos pré-registos anteriores nunca entraram nos commits, porque o .gitignore ignora \*.json; foram recriados localmente.

Secção de 7/11 (Divisão Trader, pré-registo 25): TradingV2/research/ACOES/wic\_trader\_20261107/ no branch ccr-698394c2-7q5oxi. PREREG25.md e PREREG25\_FREEZE.json em commit antes de correr (001540a; o JSON entrou com git add -f); resultados em FINDINGS25.md, out/t25.txt e out/grid25.csv (09906a5). win25.py faz as janelas no universo da época (V55–V56), sim25.py é o opt22 com T livre e recompra (V57–V59, Δ 0), p25.py faz a calibração, a grelha e a regra, e x25\_report.py é exploratório. Duas correcções antes de ler a grelha (nanmedian na calibração e a formatação do relatório), com as saídas erradas guardadas. Os PREREG12/15\_FREEZE.json foram reconstruídos localmente a partir dos .md, que não mudaram.

Secção de 7/11 (Divisão AI Agent, pré-registo 26): mesma pasta e branch. PREREG26.md e PREREG26\_FREEZE.json em commit antes de correr (ac52991); resultados em FINDINGS26.md, out/t26.txt e out/grid26.csv (c435ffa). p26.py faz a calibração, a grelha, a P(pódio) e a regra sobre as janelas fev–mar do win25.py; V60 reproduz a P(1.º) do pré-registo 18 (29,7% e 31,4%).

Secção de 7/11 (aposta final, pré-registo 27): mesma pasta e branch. PREREG27.md e PREREG27\_FREEZE.json em commit antes de correr (51f70da); resultados em FINDINGS27.md, out/t27.txt e out/grid27.csv (45280f6). p27.py faz as três variantes (S, E, L) sobre o motor e os adversários do p26; V61 confirma os 38,8% teóricos sem custos, V62 os caminhos com o retorno abertura→fecho. O sim25.py passou a devolver o pico e o NAV finais (aditivo; V57 com Δ 0).

Secção de 7/11 (aposta final e mediana, pré-registo 28): mesma pasta e branch. PREREG28.md e PREREG28\_FREEZE.json em commit antes de correr (300a701); resultados em FINDINGS28.md, out/t28.txt e out/grid28.csv (232a229). p28.py reutiliza a montagem do p27 com o limiar e a fracção da folga; V64 reproduz o pré-registo 27.

Secção de 7/11 (aposta só com os lucros, pré-registo 29): mesma pasta e branch. PREREG29.md e PREREG29\_FREEZE.json em commit antes de correr (7e8aecf); resultados em FINDINGS29.md, out/t29.txt e out/grid29.csv (25299cb). p29.py reutiliza a montagem do p27; V65 reproduz o pré-registo 27 e a EAP até à sessão 35.

Secção de 7/11 (custo real e várias apostas, pré-registo 30): mesma pasta e branch. PREREG30.md e PREREG30\_FREEZE.json em commit antes do teste 2 (08732ca); resultados em FINDINGS30.md, out/x30\_cost.txt, out/t30.txt e out/grid30.csv (67c5d8e). x30\_cost.py grava e mede as cadeias do QQQ (TradingV2/data/wic\_trader\_20261107/qqq\_chain\_yahoo\_20261106.csv); p30.py corre os calendários; V66 reproduz o pré-registo 29. O sim25.py aceita um estado inicial (aditivo; V57 com Δ 0).

---

# Parte 2 — FINDINGS25–30

Origem: `ccr-698394c2-7q5oxi:TradingV2/research/ACOES/wic_trader_20261107/FINDINGS<n>.md`.

## FINDINGS25 — Divisão Trader, adversários na fasquia real, DQ como derrota

PREREG25 (commit 001540a, antes de correr). Saída completa em out/t25.txt e out/grid25.csv; exploratórios em
out/x25_report.txt.

### Resposta curta
Na Divisão Trader, contra adversários cujo melhor faz +30%, nenhuma configuração passa de **~19% de P(1.º)**
(uma equipa ao acaso tem 6%). A recomendação mantém-se pela regra: a EAP 1,2× com M1b e piso 85%, sozinha, tem
18,0%; a melhor da grelha (EAP 1,4×) tem 18,8% (+0,8 pp, abaixo dos +2 pp exigidos, e o LOYO cai para 10,9%).
**Os +30% continuam fora de alcance:** a maior P(≥ 30%) é 17,8% (puts de 30 dias com recompra), com mediana −14,6%.

### T1 — janeiro não acrescenta alfa
| EAP B, mortas central | Janela Trader (57 sessões) | Fev–mar (PREREG18) |
| --- | --- | --- |
| 0,8× | 3,1% (anos negativos 4/13) | 3,2% (5/13) |
| 1,2× | 4,6% (4/13), desvio por ano 16,4 pp | 4,7% (5/13), 13,8 pp |
| 1,2×, mortas optimista / pessimista | 7,0% / −0,5% | 7,3% / −1,1% |

Em bruto, as sessões de janeiro rendem −1,5% a 1,2× (~80 trades por janela), negativas em 8 de 13 anos
(t ≈ −0,7: ruído). A janela mais longa dá mais variância, não mais alfa.

### C0 — adversários calibrados
| Campo | Parâmetro | 1.º / 2.º / 3.º (medianas) | Adversários DQ |
| --- | --- | --- | --- |
| A30 | s_max 0,0352 | +30,0 / +17,4 / +11,1% | 35% |
| B30 | π 0,494 | +30,0 / +14,8 / +8,5% | 34% |
| A22 | s_max 0,0239 | +22,0 / +13,6 / +9,2% | 22% |
| A38 | s_max 0,0532 | +38,0 / +19,2 / +10,6% | 51% |

WIC2025: +33,3 / +14,0 / +1,2%. A B30 é a mais parecida no 2.º lugar.

### G — grelha (348 configurações, ao fecho, sem corte de elegibilidade)
| Configuração | P(1.º) A30 | B30 | 2001s | 2012c | Dia de −8% | Mortas pess. | P(≥ 30%) | Mediana | DQ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| EAP 1,4× sozinha, piso 85% (melhor) | 18,8 | 20,5 | 18,3 | 15,2 | 24,5 | 11,0 | 2,0 | +1,4% | 0,4% |
| EAP 1,2× sozinha, piso 85% (actual) | 18,0 | 20,0 | 17,5 | 14,3 | 24,0 | 11,4 | 0,0 | +0,2% | 0,0% |
| EAP 1,4× + put 0,94 86d, meia folga, piso 85% | 17,4 | 18,9 | 16,8 | 12,5 | 32,0 | 10,6 | 5,7 | −2,2% | 5,6% |
| Só put 0,94 86d, piso 81% | 16,5 | 17,0 | 14,9 | 11,2 | 45,3 | 16,5 | 15,5 | −8,9% | 0,0% |
| EAP 1,4× + call 1,03 86d, meia folga, piso 85% | 15,9 | 17,6 | 16,5 | 18,2 | 17,2 | 8,5 | 5,2 | −2,0% | 4,5% |
| Só put 0,94 30d com recompra, piso 81% (maior P(≥ 30%)) | 15,4 | 15,5 | 13,5 | 10,8 | 34,9 | 15,4 | 17,8 | −14,6% | 0,0% |

- **Regra de decisão:** a escolhida (EAP 1,4×) falha os +2 pp e o S (LOYO 10,9%, S +7,9 pp). A recomendação mantém-se.
- **O S alto mostra a fragilidade:** sem 2014 ou sem 2016, a melhor passa a ser a put. A P(1.º) da EAP 1,4× por
  ano é 64% (2014), 66% (2016), 39% (2018), 43% (2019), 15% (2017), 9% (2023) e abaixo de 3% nos outros 7 anos:
  ganha-se em anos de EAP forte, e na maioria dos anos não.
- **Calls por cima da EAP pioram a P(1.º)** (adversários comprados no mesmo mercado), excepto com tendência (2012c).
- **Puts protegem nos crashes:** com um dia de −8%, a put sozinha sobe para 45% de P(1.º) (os adversários caem).
- **O corte de elegibilidade antigo quase não mudava nada aqui:** com ele, a melhor seria a EAP 1,4× com piso 88%
  (18,2%). As configurações com DQ alto não ganham mais vezes, por isso o problema 3 era real em princípio mas
  pouco material na prática. O piso de 81% sem margem até ao DQ (kill-switch a 79%) dá 23% de DQ sem mudar a P(1.º).
- **Stress de custos** (IV + 0,10 × VXN, spreads × 2): sem efeito na EAP sozinha (não usa opções).

### Exploratório (pós-hoc, não decide nada) — out/x25_report.txt
| Contra A30, 2012s | Relatório 1.º / 3.º / 8.º | Média | P(≥ 30%) | Mediana |
| --- | --- | --- | --- | --- |
| EAP 1,2× sozinha, piso 85% | 26,2 / 20,5 / 7,4 | 18,0 | 0,0 | +0,2% |
| EAP 1,4× sozinha, piso 85% | 26,9 / 21,5 / 8,0 | 18,8 | 2,0 | +1,4% |
| Só put 0,94 86d, piso 81% | 21,6 / 19,2 / 8,8 | 16,5 | 15,5 | −8,9% |
| EAP 1,2× só desde 1/fev | 33,2 / 26,4 / 9,5 | 23,0 | 0,0 | +5,9% |
| EAP 1,4× só desde 1/fev | 35,3 / 28,8 / 11,0 | 25,0 | 7,6 | +7,2% |

- O lugar no relatório vale mais do que qualquer escolha de estratégia: do 8.º para o 1.º, +19 pp.
- Saltar janeiro sobe a P(1.º) em 5–6 pp, mas foi escolhido depois de ver janeiro negativo nestes 13 anos (t ≈ −0,7).
  Só pode entrar com um teste fora da amostra (janeiro de 2027 no teste-sombra, ou um pré-registo com outras épocas).

### Correcções durante a corrida (antes de ler a grelha)
1. Calibração: `order_stats` usava `np.median`, que dá NaN quando há trajectórias com os 15 adversários
   desclassificados; a bissecção convergia mal (A30 em +23%, A38 igual ao A30). Corrigido para `np.nanmedian`, a
   leitura literal do pré-registo ("mediana do melhor não desclassificado"). Saída errada em out/descartado_bug_calibracao/.
2. Relatório: `r.median` numa Series do pandas é o método; corrigido para `r["median"]`. A grelha foi recalculada
   (os números do top 15 coincidem com a primeira corrida, guardada em out/descartado_bug_relatorio/).

### Limites
Adversários sintéticos calibrados a dois vencedores; regra de ranking da Divisão Trader por confirmar (fica a RRF da
AI Agent); mortas por cenários; opções calibradas no SPY; execução humana das MOC e a regra de DQ por fills
irrealistas fora do modelo; 13 anos de janelas.

## FINDINGS26 — Divisão AI Agent: fasquia dos adversários, DQ como derrota, P(pódio)

PREREG26 (commit ac52991, antes de correr). Saída em out/t26.txt e out/grid26.csv; V60 em out/v60.txt.

### Resposta curta
**A recomendação muda, por pouco: de EAP 1,2× para EAP 1,4×, com M1b, sozinha.** A 1,4× ganha +2,2 pp de P(1.º)
contra a fasquia de manchete (A22: 25,2% contra 23,0%) e fica à frente em todas as fasquias, nos dois períodos e
com mortas pessimistas. O LOYO não mostra inflação (25,1%). Pela P(pódio) a diferença é +1,6 pp, abaixo dos 2 pp:
se o prémio for do 1.º ao 3.º, a regra não mexe. Nenhuma combinação com opções melhora a P(1.º) nem a P(pódio).
A P(≥ 30%) continua perto de 0 com a EAP (0,2%); a maior é 18,0% com puts, mediana −14,4%.

### Adversários (14 por trajectória, 36 sessões)
| Campo | 1.º / 2.º / 3.º (medianas) | Adversários DQ |
| --- | --- | --- |
| A15 | +15,0 / +9,5 / +6,5% | 10% |
| A22 (manchete) | +22,0 / +13,4 / +8,9% | 18% |
| A30 | +30,0 / +17,1 / +10,7% | 31% |
| TN (antigos, O1–O4) | melhor +7,7 / +15,1 / +22,2 / +17,2% | — |

V60: com os TN, a grelha reproduz o PREREG18 (29,7% e 31,4%).

### Grelha (252 configurações, ao fecho, sem corte de elegibilidade)
| Configuração | P(1.º) A22 | A15 | A30 | TN | 2001s | Mortas pess. | P(pódio) A22 | P(≥ 30%) | Mediana | DQ | Pior DD real |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| EAP 1,4×, piso 85% (escolhida pela regra) | 25,2 | 30,6 | 21,5 | 31,5 | 24,2 | 13,5 | 45,0 | 0,2 | +6,1% | 2,44% | −19,8% |
| EAP 1,4×, piso 88% | 25,2 | 30,5 | 21,5 | 31,4 | 24,2 | 13,3 | 44,7 | 0,2 | +6,1% | 0,00% | −18,2% |
| EAP 1,2×, piso 85% (anterior) | 23,0 | 28,2 | 19,6 | 29,7 | 22,0 | 12,3 | 43,4 | 0,0 | +4,8% | 0,01% | −18,4% |
| EAP 0,8×, piso 85% | 17,2 | 22,3 | 14,6 | 25,2 | 16,5 | 9,6 | 40,0 | 0,0 | +3,9% | 0,00% | −17,4% |
| EAP 1,4× + put 0,97 58d, meia folga | 23,1 | 27,3 | 19,9 | 28,0 | 21,9 | 12,9 | 39,2 | 5,5 | +0,6% | 7,95% | — |
| EAP 1,4× + call 1,03 58d, meia folga | 21,8 | 26,2 | 18,7 | 27,4 | 22,1 | 10,9 | 40,6 | 6,3 | +0,9% | 6,77% | — |
| Só put 0,94 30d, piso 81% | 16,8 | 17,8 | 15,6 | 19,0 | 14,7 | 16,8 | 23,5 | 17,4 | −14,4% | 0,00% | — |
| Só put 0,94 30d com recompra, piso 81% | 16,3 | 17,2 | 15,3 | 18,4 | 14,0 | 16,3 | 22,8 | 18,0 | −14,4% | 0,00% | — |

- **Regra (P(1.º)):** a escolhida (1,4×, piso 85%) passa os cinco critérios (outra; +2,2 pp; A15/A30/TN; S +0,0 pp;
  pessimista) → **muda**. A escolha por ano é a 1,4× em todos os 13 folds (pisos 85% ×11, 83% ×1, 88% ×1).
- **Piso:** a regra escolhe 85% por 0,04 pp sobre 88%, mas com 2,4% de DQ contra 0,00% e um pior DD real de −19,8%
  (0,2 pp do DQ) contra −18,2%. A diferença está abaixo do ruído e o 88% também passa os critérios de desempenho
  (+2,2 pp contra a anterior, à frente em A15/A30/TN e com mortas pessimistas); recomendo **piso 88%, kill-switch a 86%**, para não depender da precisão do modelo a 0,2 pp do DQ.
- **P(pódio):** 1,4× com 45,0% contra 43,4% (+1,6 pp, abaixo dos 2) → pela regra do pódio, mantém-se.
- **Opções:** calls por cima da EAP só ajudam com tendência (2012c: 24,9% contra 21,5%); puts protegem num crash
  (dia de −8%: 42–46%). Na manchete, ambas pioram a P(1.º) e a P(pódio).
- **Corte de elegibilidade antigo:** a melhor seria a 1,4× com piso 88% (25,2%). O problema 3 não muda a escolha.
- **Stress de custos:** sem efeito na EAP sozinha.
- **Porque muda agora e não no PREREG18:** a diferença 1,4× − 1,2× é de +1,7 pp contra os TN (31,4 − 29,7, abaixo
  do corte) e de +1,9 a +2,4 pp contra as fasquias calibradas. A manchete passou a ser a A22; a ordem é a mesma em
  todos os campos.

### Limites
Fasquia da AI Agent desconhecida (por isso três); adversários sintéticos; mortas por cenários; com a 1,4× o pior DD
das janelas reais fica a ~2 pp do DQ, por isso o kill-switch e o limite de ordem (fora do LLM) são obrigatórios.

## FINDINGS27 — aposta binária numa só sessão ("bold play") para os +30%

PREREG27 (commit 51f70da, antes de correr). Saída em out/t27.txt e out/grid27.csv; V61–V62 em out/v61_62.txt.

### Resposta curta
**A aposta final mais do que duplica a P(≥ 30%): de 17,4% (melhor do doc, puts de 30 dias) para 37,5%**, com 10% de
custos, e 34,4% com 20%. A forma: EAP 1,4× nas sessões 1–35 e, na última sessão, uma só aposta binária no QQQ
(call ou put spread de 0–1 dias, comprada na abertura e vendida antes do fecho), com toda a folga até 81% do pico e
o payoff para acabar em +30%. Passa as duas regras: R1 (+30%) e R2 (1.º lugar: com classificação visível, apostar
até ao líder + 3 pp dá P(1.º) de 34,3% contra 25,2% da EAP sozinha).
**É uma aposta:** perde ~61% das vezes, com mediana −10%, e o valor esperado da aposta é negativo (−v).

### Porque funciona
O tecto do doc (1,3^(−1/D), ~27% com piso 80%) vale para um NAV contínuo, em que cada pico novo sobe o piso. O DD
só conta ao fecho; uma aposta resolvida dentro de uma sessão não cria picos intermédios. Uma aposta justa que acaba
em 1,30 ou em 0,81 ganha com probabilidade (1 − 0,81) / (1,30 − 0,81) = 38,8% (V61: 39,1% / 38,6% na simulação).
Num jogo desfavorável, a aposta única e máxima é a óptima para atingir um alvo (Dubins e Savage). A EAP antes sobe
o NAV de partida em média, e por isso a variante E ganha à S.

### Resultados (2012s, adversários do PREREG26; v = custo do digital)
| Variante | v | P(≥ 30%) | 2001s | P(1.º) A15 / A22 / A30 | P(pódio) A22 | P(1.º \| ≥ 30%) | Mediana |
| --- | --- | --- | --- | --- | --- | --- | --- |
| EAP 1,4× piso 88% sozinha (referência) | — | 0,2% | — | 30,5 / 25,2 / 21,5 | 44,7 | 52% | +6,1% |
| Só put 0,94 30d piso 81% (PREREG26) | — | 17,4% | — | 17,8 / 16,8 / 15,6 | 23,5 | 81% | −14,4% |
| **E: EAP + aposta final até +30%, F_b 0,81** | 0,10 | **37,5%** | 37,5% | 31,9 / 29,2 / 25,7 | 40,1 | 75% | −10,3% |
| E, idem | 0,20 | 34,4% | 34,7% | 29,8 / 27,2 / 24,0 | 38,0 | 74% | −10,5% |
| S: só a aposta no 1.º dia, F_b 0,81 | 0,10 | 35,5% | 35,5% | 28,5 / 26,1 / 22,9 | 35,1 | 73% | −19,0% |
| **L: EAP + aposta final até ao líder + 3 pp, put** | 0,10 | 10,4% | — | 40,4 / 34,3 / 28,9 | 43,1 | 81% | −10,0% |
| L, idem | 0,20 | 9,6% | — | 38,5 / 32,5 / 27,4 | 41,1 | 81% | −10,3% |

- **R1 (+30%) passa:** 37,5% ≥ 22,4% a v = 0,10; 34,4% ≥ 17,4% a v = 0,20; 37,5% nos 2001s.
- **R2 (1.º lugar) passa:** a L (put, líder + 3 pp) dá +9,1 pp contra A22, à frente em A15 (+9,9) e A30 (+7,4), e
  32,5% a v = 0,20. Exige a classificação visível (com um dia de atraso).
- **Alvos maiores pioram tudo:** alvo 35% → P(≥ 30%) 31,8%; 40% → 28,0% (v = 0,10). O piso da aposta a 0,82 / 0,84
  custa 1,4 / 4,1 pp de P(≥ 30%) e dá margem até ao DQ.
- **Call ou put dá quase o mesmo** em P(≥ 30%); a put dá um pouco mais de P(1.º) (ganha quando os adversários,
  comprados no mercado, perdem).
- **Pódio:** a E baixa a P(pódio) de 44,7% para ~40%; a L fica perto (43,1%). Se o prémio for do 1.º ao 3.º, a EAP
  sozinha continua a melhor para o pódio.

### Limites (o que pode deitar isto abaixo)
1. **Opções permitidas?** Sem opções não há forma de fazer o digital (com ações alavancadas o resultado não é binário
   e volta ao tecto contínuo). Perguntar no grupo.
2. **Custo real (v):** não há cadeias 0DTE do QQQ nos dados. A 20% ainda passa; medir bid-ask e preço face ao
   movimento realizado no período de testes (7–20/dez).
3. **Fills no paper da IBKR e a regra de DQ por fills irrealistas:** usar spreads de 1 dia muito líquidos, ordens
   limitadas ao mid/ask real, e registar os preços de mercado ao lado do fill.
4. **Relatório (30% do ranking):** uma aposta final é uma tese fraca se não for apresentada como a estratégia óptima
   de torneio (Dubins–Savage; Browne). As P(1.º) acima assumem o nosso relatório em 1.º/3.º/8.º como antes; se a
   aposta custar lugares no relatório, parte do ganho desaparece.
5. **LLM em tempo real:** a decisão final (fazer ou não, direcção, tamanho) tem de ser do LLM, com regras escritas
   antes e registadas; o motor não muda.
6. **Execução até às 15:50 de 25/mar** (liquidação obrigatória): a aposta tem de ser feita e fechada antes, por
   exemplo a 24/mar ou na manhã de 25/mar. O modelo usa abertura→fecho.
7. Adversários sintéticos; mortas no cenário central; caminhos do QQQ de 2012–26 e 2001–26.

## FINDINGS28 — aposta final e mediana: a fronteira

PREREG28 (commit 300a701, antes de correr). Saída em out/t28.txt e out/grid28.csv; V64 em out/v64.txt (reproduz o
PREREG27: 37,39% e −10,37%).

### Resposta curta
**Não há forma de ter a P(≥ 30%) alta e a mediana positiva ao mesmo tempo.** Com a mediana ≥ 0, a melhor P(≥ 30%)
é 9,0% (apostar só se o NAV da sessão 35 estiver abaixo de 1,06). Falha a regra (precisava de 22,4%). A hipótese do
registo estava errada: as trajectórias que estão atrás têm pouca folga até ao piso (o pico ficou alto), por isso as
suas odds são más; quase toda a P(≥ 30%) vem das que já estão à frente, e são essas que, perdendo, baixam a mediana.

### Fronteira (put, alvo +30%, F_b 0,81, v = 0,10, 2012s)
| Regra da aposta final | Apostam | P(≥ 30%) | Mediana | Média | P(< 0) | P(1.º) A22 | P(pódio) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Sempre, toda a folga (PREREG27) | 98% | 37,4% | −10,4% | +2,8% | 59% | 29,2% | 40,0% |
| Sempre, metade da folga | 98% | 28,9% | −2,0% | +3,4% | 60% | 25,5% | 37,3% |
| Só se NAV < 1,10, toda a folga | 70% | 16,4% | −10,4% | +3,3% | 55% | 30,9% | 43,3% |
| **Só se NAV < 1,06, toda a folga** | 52% | 9,0% | **+7,5%** | +3,6% | 44% | 29,7% | **47,3%** |
| EAP 1,4× sozinha | 0% | 0,2% | +6,1% | +3,8% | 45% | 25,2% | 44,7% |

- A v = 0,20 e nos caminhos de 2001–26 a fronteira é a mesma (±1 pp). Call e put dão o mesmo.
- **Apostar só se NAV < 1,06 melhora a EAP sozinha em tudo menos a média** (−0,2 pp): P(1.º) +4,5 pp, P(pódio)
  +2,6 pp, mediana +1,4 pp, P(< 0) −1 pp. Não serve para os +30% (9%), mas é a melhor opção do registo para o pódio.
- **A metade da folga** é o meio-termo: P(≥ 30%) ainda passa o corte do PREREG27 (28,9% ≥ 22,4%), com mediana −2%.
  Não foi a regra escolhida (mediana < 0); fica como opção, se −2% for aceitável.
- A média é positiva em todas (+2,8% a +3,8%): a mediana negativa vem da assimetria (muitas perdas moderadas,
  alguns ganhos grandes), não de um valor esperado negativo do conjunto EAP + aposta.

### Limites
Os do PREREG27. As fracções intermédias (k entre 0,5 e 1) e outros limiares não foram testados.

## FINDINGS29 — aposta final só com os lucros

PREREG29 (commit 7e8aecf, antes de correr). Saída em out/t29.txt e out/grid29.csv; V65 em out/v65.txt.

### Resposta curta
**Apostar só os lucros acima de +2% dá P(≥ 30%) de 31,0% com mediana +2,0% e 59% das trajectórias acima de 0**
(custo 10%). Com custo 20%: 28,5%, mediana +2,0%, 59% acima de 0. Nos caminhos de 2001–26 é igual. Passa a regra.
Face à aposta com toda a folga (37,4%, mediana −10,4%), custa 6,4 pp de P(≥ 30%); face à metade da folga do
PREREG28 (28,9%, mediana −2,0%), é melhor nas duas coisas.

### A regra (última sessão, put spread de QQQ de 0–1 dias)
- **NAV ≥ +2%:** arrisca-se só o que está acima de +2% (e nunca abaixo de 81% do pico); ganhando, acaba em +30%;
  perdendo, acaba em +2%.
- **NAV < +2%:** arrisca-se toda a folga até 81% do pico, como no PREREG27 (já está abaixo da mediana, por isso
  perder não a baixa).

### Resultados (put, alvo +30%, 2012s)
| Regra | Custo | P(≥ 30%) | P(> 0) | Mediana | Média | P(1.º) A15 / A22 / A30 | P(pódio) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **Lucros acima de 2%, toda a folga abaixo** | 10% | **31,0%** | 59,4% | **+2,0%** | +3,1% | 28,5 / 25,8 / 23,1 | 40,3% |
| Idem | 20% | 28,5% | 58,9% | +2,0% | +2,4% | 27,0 / 24,3 / 21,8 | 38,9% |
| Lucros acima de 4%, toda a folga abaixo | 10% | 29,6% | 59,2% | +4,0% | +3,2% | 29,5 / 26,1 / 23,2 | 42,5% |
| Lucros acima de 2%, sem aposta abaixo | 10% | 25,2% | 54,9% | +2,0% | +3,4% | 23,9 / 21,6 / 19,5 | 36,1% |
| Lucros acima de 0%, toda a folga abaixo | 10% | 32,1% | 35,9% | 0,0% | +3,1% | 28,3 / 25,9 / 23,2 | 38,7% |
| Toda a folga sempre (PREREG27) | 10% | 37,4% | 41% | −10,4% | +2,8% | 31,9 / 29,2 / 25,9 | 40,0% |
| Metade da folga sempre (PREREG28) | 10% | 28,9% | 40% | −2,0% | +3,4% | 28,1 / 25,5 / 22,7 | 37,3% |
| EAP 1,4× sozinha | — | 0,2% | 55% | +6,1% | +3,8% | 30,5 / 25,2 / 21,5 | 44,7% |

- **Com m = 0, muitas trajectórias acabam exactamente em 0%** (P(> 0) de 36%): o +2% é o que põe mais de metade acima
  de zero. Com m = 4%, a mediana sobe para +4% por 1,4 pp de P(≥ 30%), com um pouco mais de P(1.º) e de pódio.
- **Apostar toda a folga abaixo de +m é melhor do que não apostar:** +5,8 pp de P(≥ 30%), sem mudar a mediana.
- **P(1.º):** ~26% contra A22, igual à EAP sozinha; para o 1.º lugar, a aposta até ao líder (PREREG27, 34%) continua
  melhor, mas com mediana −10%.

### Limites
Os do PREREG27 (opções permitidas, custo real das spreads de 0–1 dias, fills no paper, relatório, decisão do LLM).

## FINDINGS30 — custo real da aposta e várias apostas só com os lucros

PREREG30 (commit 08732ca; teste 1 descritivo feito antes, teste 2 corrido depois). Saídas em out/x30_cost.txt,
out/t30.txt e out/grid30.csv; V66 em out/v66.txt.

### Resposta curta
1. **O custo de bid-ask das spreads de QQQ de 1 dia equivale a v ≈ 9%** (11–12% a 2–3 dias), medido nas cadeias
   reais do Yahoo ao fecho de 6/11/2026. Os 10% da manchete cobrem o bid-ask; com prémio de volatilidade (não medido),
   o custo real deve ficar entre 10% e 20%. A regra dos lucros acima de +2% passa nos dois (31,0% e 28,5%).
2. **Várias apostas não sobem a P(≥ 30%):** a melhor elegível (12/24/36, só com lucros acima de 10%) dá 31,6%,
   +0,6 pp sobre uma só aposta. Não passa a regra (precisava de +2 pp). A regra do PREREG29 mantém-se.

### Teste 1 — custo (QQQ 656,10; spreads de strikes adjacentes com mid/largura 0,25–0,50)
| Vencimento | Entrada (mediana, intervalo) | Saída num ganho (% da largura) | v equivalente |
| --- | --- | --- | --- |
| 9/11 (1 dia) | 4,5% (3,1–6,9%) | 4,4% | 9,3% |
| 10/11 (2 dias) | 6,5% (5,4–8,0%) | 3,8% | 10,7% |
| 11/11 (3 dias) | 7,4% (5,0–9,1%) | 4,5% | 12,5% |

Limites: uma fotografia, depois do fecho, num dia de volatilidade alta (o QQQ caiu ~5% a 5/11); o Yahoo mostra só
parte dos strikes; não mede o prémio de volatilidade. Correcção na 1.ª versão: a saída usava spreads muito dentro do
dinheiro, com cotações desactualizadas (77%); passou a usar as pernas 0,5–2% dentro do dinheiro.

### Teste 2 — várias apostas (put, alvo +30%, v = 0,10, 2012s)
| Calendário e regra | Apostas por traj. | P(≥ 30%) | P(> 0) | Mediana | Média | P(1.º) A22 | P(pódio) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Só na sessão 36, lucros acima de 2% (PREREG29) | 0,98 | 31,0% | 59,4% | +2,0% | +3,1% | 25,8% | 40,3% |
| 18 e 36, lucros acima de 2% | 1,12 | 31,0% | **64,8%** | +2,0% | **+4,2%** | 25,8% | 40,7% |
| 12/24/36, intermédias só se NAV ≥ +10% (escolhida) | 1,11 | 31,6% | 53,7% | +2,0% | +2,8% | 25,3% | 38,3% |
| 12/24/36, intermédias com qualquer lucro acima de 2% | 1,45 | 33,7% | 49,1% | −3,1% | +2,7% | 26,4% | 38,3% |
| 9/18/27/36, lucros acima de 2% | 1,79 | 29,2% | 47,0% | −3,1% | +1,6% | 23,3% | 34,4% |
| 18 e 36, lucros acima de 4% | 0,97 | 30,0% | 63,1% | +4,0% | +4,3% | 26,5% | 43,4% |

- **Mais apostas pagam mais custos.** Com 3–4 apostas, a P(≥ 30%) só sobe se as intermédias arriscarem qualquer
  lucro, e aí a mediana volta a ficar negativa (−3%).
- **Uma aposta extra a meio (sessão 18) quase não custa nada e melhora a distribuição:** P(≥ 30%) igual (31,0%),
  P(> 0) de 59% para 65%, média de +3,1% para +4,2%. Depois de uma aposta perdida a meio, o NAV fica em +2% e o M1b
  reduz a EAP (menos folga até ao piso), o que estabiliza o resto da janela. Não era o critério pré-registado (a
  P(≥ 30%)), por isso fica como opção, não como recomendação.
- Com custos de 20% a ordem é a mesma (18/36: 29,3% contra 28,5% de uma só aposta).

### Limites
Os do PREREG27. A EAP fica parada nos dias de aposta (simplificação).

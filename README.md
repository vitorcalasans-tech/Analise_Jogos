🎮 Análise da Classificação Indicativa de Jogos Eletrônicos no Brasil
Python Jupyter pandas status

Projeto Final da disciplina Introdução à Ciência de Dados . A análise investiga como a presença de conteúdos sensíveis nos jogos eletrônicos evoluiu ao longo das décadas no Brasil e qual o nível de alinhamento entre os produtos e o órgão regulador (a ClassInd, do Ministério da Justiça e Segurança Pública).

❓ Pergunta orientadora
Como a presença de conteúdos sensíveis nos jogos evoluiu ao longo das décadas e qual o nível de alinhamento entre as produtoras e o órgão regulador brasileiro?

Em termos analíticos: existe clareza entre o ano de produção e a diversidade/intensidade dos descritores de conteúdo (violência, conteúdo sexual, drogas) nos jogos registrados?

Perguntas separadas
P1 — A diversidade e a intensidade dos descritores de conteúdo mudaram ao longo das décadas?
P2 — Qual é a distribuição das classificações etárias (Livre, 10, 12, 14, 16, 18) no acervo?
P3 — Quais plataformas aparecem com maior frequência? Há mudanças nas plataformas dominantes ao longo do tempo?
P4 — Qual o percentual de concordância entre a classificação pretendida pelos distribuidores e a atribuída pelo órgão? Nas divergências, o órgão é mais rígido ou mais flexível?
📊 Conjunto de dados
Fonte	Portal de Dados Abertos do Ministério da Justiça e Segurança Pública (MJSP) — Classificação Indicativa de Jogos Eletrônicos
Link	dados.mj.gov.br
Formato	.xlsx(lido diretamente da URL, com fallback para arquivo local)
Tamanho	Milhares de registros, cobrindo décadas de lançamentos
Colunas principais	Título, Ano, Classificação Pretendida, Classificação Atribuída, Descritores de Conteúdo, Plataforma, Distribuidor
Contexto técnico: o que é um "descritor de conteúdo"
Na Classificação Indicativa, cada jogo recebe duas informações distintas . A faixa etária (Livre a 18) diz a partir da idade que o conteúdo é recomendado. Já os descritores de conteúdo dizem o que faixa — quais tipos de conteúdo confidencial foram identificados (violência, conteúdo sexual, drogas, linguagem imprópria). Como um mesmo jogo pode ter vários descritores, eles são tratados como variável multivalorada nesta análise.

🔎 Principais resultados
Conteúdos sensíveis cresceram (P1 / pergunta orientadara): há uma ruptura clara a partir de 2014/2015. A proporção de jogos com algum descritor saltou de ~45% para quase 70%, e a média de descritores por jogo quase dobrou no último período (0,57 → 1,10). A demonstração de Pearson (≈ 0,17) confirma a tendência de alta, diminuindo que o ano de influência, mas não é o único fator.
Acervo majoritariamente "Livre" (P2): ~54,9% dos jogos são "Livre"; as faixas mais altas (16/18) somam cerca de 15%.
Migração de plataformas (P3): o PC é líder absoluto do acervo (>4.200 títulos). Ao longo do tempo, o PC/Mac dominou em 1996–2005 (~78%) e, em 2016–2025, PlayStation e Xbox se consolidaram como plataformas dominantes (~65% e ~56%).
Empresas mais conservadoras que o regulador (P4): distribuidores e órgão concordam em ~76,9% dos casos. Entre os ~23% de divergências, o órgão foi mais flexível (reduziu a faixa) em 57,2% das vezes, contra 42,8% em que foi mais rígido.
📁 Estrutura do repositório
.
├── analise_jogos_classificacao_final.ipynb   # Notebook com toda a análise (código + gráficos)
├── Projeto_Final__Classificação_de_Jogos.pdf  # Slides de apresentação
└── README.md
🛠️ Tecnologias
Python 3
pandas / numpy — manipulação e limpeza de dados
matplotlib / seaborn — visualização
openpyxl — leitura do arquivo.xlsx
Jupyter Notebook (compatível com Google Colab)
▶️Como executar
Clonar o:
git clone https://github.com/<seu-usuario>/<seu-repositorio>.git
cd <seu-repositorio>
Instale as partes:
pip install pandas numpy matplotlib seaborn openpyxl jupyter
Abra o caderno:
jupyter notebook analise_jogos_classificacao_final.ipynb
O notebook baixa os dados automaticamente da URL do Portal de Dados Abertos. Se o download falhar, ele tenta um arquivo local de reserva ( jogoeletronico202511141500.xlsx) ou pede o upload manual (no Google Colab).

Você também pode abrir o projeto_final_ics.htmldiretamente no navegador para visualizar o relatório sem rodar o código.

⚠️Limitações
O campo "Sem informação" (em ano, descritores e plataformas) pode subestimar conteúdos de jogos antigos: parte do crescimento dos descritores pode refletir melhoria de registro, e não só aumento real de conteúdo.
O ano de 2025 está incompleto , então não deve ser lido como uma queda real.
A base tem registros desde 1980; jogos antigos quase não possuem plataforma apresentada e aparecem pouco nos gráficos de plataforma.
Descritores e plataformas são multivalorados — um mesmo jogo pode ter vários, então os percentuais por categoria somam mais de 100%.
👥 Autores
Arthur Bueno
Leonardo Lins
Pedro Lima
Vitor Calasans
📄 Fonte e créditos
Dados públicos do Ministério da Justiça e Segurança Pública (Portal de Dados Abertos). Projeto desenvolvido para fins acadêmicos na disciplina de Introdução à Ciência de Dados.

Seu README já está muito bom e tem todas as informações necessárias, mas ele peca em pequenos erros de digitação (como *"Clonar o:"*, *"Instale as partes:"*, *"orientadara"*) e na formatação visual, que pode ser organizada para ficar muito mais atraente e fácil de ler no GitHub.

Aqui está uma versão revisada, corrigida e com um visual profissional usando tabelas, blocos de destaque (blockquotes) e caminhos de execução mais claros.

---

# 🎮 Análise da Classificação Indicativa de Jogos Eletrônicos no Brasil

Este é o **Projeto Final** da disciplina *Introdução à Ciência de Dados*. A análise investiga como a presença de conteúdos sensíveis nos jogos eletrônicos evoluiu ao longo das décadas no Brasil e qual o nível de alinhamento entre as produtoras/distribuidoras e o órgão regulador nacional (a **ClassInd**, do Ministério da Justiça e Segurança Pública).

---

## ❓ Perguntas Orientadoras

> **Pergunta Central:**
> Como a presença de conteúdos sensíveis nos jogos evoluiu ao longo das décadas e qual o nível de alinhamento entre as produtoras e o órgão regulador brasileiro? Em termos analíticos: existe relação entre o ano de produção e a diversidade/intensidade dos descritores de conteúdo (violência, conteúdo sexual, drogas) nos jogos registrados?

Para responder a essa questão, dividimos a análise em quatro frentes:

* **P1** — A diversidade e a intensidade dos descritores de conteúdo mudaram ao longo das décadas?
* **P2** — Qual é a distribuição das classificações etárias (Livre, 10, 12, 14, 16, 18) no acervo?
* **P3** — Quais plataformas aparecem com maior frequência? Há mudanças nas plataformas dominantes ao longo do tempo?
* **P4** — Qual o percentual de concordância entre a classificação pretendida pelos distribuidores e a atribuída pelo órgão? Nas divergências, o órgão é mais rígido ou mais flexível?

---

## 📊 Conjunto de Dados

| Atributo | Detalhes |
| --- | --- |
| **Fonte** | Portal de Dados Abertos do Ministério da Justiça e Segurança Pública (MJSP) |
| **Link** | [dados.mj.gov.br](https://www.google.com/search?q=http://dados.mj.gov.br) |
| **Formato** | `.xlsx` (lido via URL com fallback local) |
| **Volume** | Milhares de registros abrangendo várias décadas de lançamentos |
| **Campos Principais** | `Título`, `Ano`, `Classificação Pretendida`, `Classificação Atribuída`, `Descritores de Conteúdo`, `Plataforma`, `Distribuidor` |

### 🔍 Contexto Técnico: O que é um "Descritor de Conteúdo"?

Na Classificação Indicativa, cada jogo recebe duas informações distintas:

1. **Faixa Etária:** Recomendação de idade (Livre, 10, 12, 14, 16, 18).
2. **Descritores de Conteúdo:** Indicam quais tipos de conteúdo sensível foram identificados (violência, conteúdo sexual, drogas, linguagem imprópria).

Como um mesmo jogo pode ter múltiplos descritores, eles são tratados como uma **variável multivalorada** nesta análise.

---

## 🔎 Principais Resultados

* **📈 Crescimento de conteúdos sensíveis (P1):** Há uma ruptura clara a partir de 2014/2015. A proporção de jogos com algum descritor saltou de ~45% para quase 70%, e a média de descritores por jogo quase dobrou no último período (de 0,57 para 1,10). A correlação de Pearson (~0,17) confirma a tendência de alta com o passar dos anos, embora o tempo não seja o único fator.
* **👶 Acervo majoritariamente "Livre" (P2):** Cerca de **54,9%** dos jogos são classificados como "Livre". As faixas mais restritivas (16 e 18 anos) somam juntas cerca de 15%.
* **💻 Transição de Plataformas (P3):** O PC é o líder absoluto do acervo histórico (>4.200 títulos). No período de 1996–2005, PC/Mac dominavam com ~78% do mercado. Já em 2016–2025, PlayStation e Xbox se consolidaram como as plataformas dominantes, representando ~65% e ~56% respectivamente.
* **⚖️ Empresas mais conservadoras que o regulador (P4):** Distribuidores e o órgão regulador concordam em **76,9%** dos casos. Nas divergências (23,1%), o órgão foi **mais flexível** (reduziu a faixa pretendida) em 57,2% das vezes, contra 42,8% em que foi mais rígido.

---

## 📁 Estrutura do Repositório

```text
.
├── analise_jogos_classificacao_final.ipynb   # Notebook principal (código + visualizações)
├── Projeto_Final__Classificação_de_Jogos.pdf  # Slides da apresentação do projeto
└── README.md                                 # Documentação do projeto

```

---

## 🛠️ Tecnologias e Bibliotecas

* **Python 3**
* **pandas & numpy** — Manipulação, tratamento e limpeza de dados
* **matplotlib & seaborn** — Geração de gráficos e visualização de dados
* **openpyxl** — Mecanismo para leitura do arquivo `.xlsx`
* **Jupyter Notebook** (Totalmente compatível com Google Colab)

---

## ▶️ Como Executar o Projeto

Siga os passos abaixo para preparar o ambiente e rodar a análise localmente:

### 1. Clonar o Repositório

```bash
git clone https://github.com/<seu-usuario>/<seu-repositorio>.git
cd <seu-repositorio>

```

### 2. Instalar as Dependências

```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter

```

### 3. Executar o Notebook

```bash
jupyter notebook analise_jogos_classificacao_final.ipynb

```

> **Nota sobre os dados:** O notebook está configurado para baixar a base de dados mais recente de forma automática diretamente da URL do Portal de Dados Abertos do MJSP. Caso a conexão falhe, o script usará um arquivo de backup local (`jogoeletronico202511141500.xlsx`) ou solicitará o upload manual (caso esteja rodando no Google Colab).
> *(Opcional)* Caso queira apenas visualizar o relatório final formatado sem rodar códigos, abra o arquivo `projeto_final_ics.html` diretamente em qualquer navegador web.

---

## ⚠️ Limitações da Base de Dados

1. **Dados Omissos:** Registros antigos possuem muitos campos marcados como "Sem informação" (principalmente em ano, descritores e plataformas). Parte do aumento recente de descritores pode ser fruto da melhoria de registro do órgão público, e não apenas de uma mudança real na indústria.
2. **Dados Incompletos:** O ano de 2025 está incompleto na base pública, o que pode gerar distorções se interpretado de forma literal como uma queda na produção desse ano.
3. **Plataformas de Jogos Antigos:** A base conta com dados desde 1980, mas jogos do século passado raramente possuem informações de plataforma registradas, diminuindo sua amostragem nos gráficos desta categoria.
4. **Variáveis Multivaloradas:** Como descritores e plataformas aceitam múltiplas respostas para um mesmo jogo, os somatórios de participação percentual entre categorias podem ultrapassar 100%.

---

## 👥 Autores

* [Arthur Bueno](https://www.google.com/search?q=https://github.com/seu-usuario)
* [Leonardo Lins](https://www.google.com/search?q=https://github.com/seu-usuario)
* [Pedro Lima](https://www.google.com/search?q=https://github.com/seu-usuario)
* [Vitor Calasans](https://www.google.com/search?q=https://github.com/seu-usuario)

---

*Este projeto foi desenvolvido estritamente para fins acadêmicos como parte da disciplina Introdução à Ciência de Dados.*

# Teste técnico TERA Capital
Script Python desenvolvido com a intenção de analisar dados financeiros de uma carteira de títulos internacionais, a fim de consolidar informações e gerar insights que auxiliem na avaliação do desempenho dos ativos, apresentando resultados em reais (BRL) e dólares (USD) de forma clara e estruturada.


## Contexto
Em 1 de janeiro de 2010, um cliente aplicou um valor único em títulos pré-fixados emitidos por diferentes países. Cada posição cresceu ao longo dos anos apenas pela taxa fixa indicada, sem novos aportes. Como os investimentos foram feitos em contas bancárias nos países de emissão, os saldos eram visualizados em suas respectivas moedas, o que dificultava avaliar o desempenho real da carteira considerando a flutuação cambial.

Não há datas de vencimento, permitindo ao usuário consultar o desempenho de cada título a partir do ano de aporte inicial (2010) até o ano presente.

O retorno da carteira é calculado utilizando juros compostos e conversão cambial, com cotações históricas oficiais das moedas obtidas via API PTAX do Banco Central do Brasil.

Para conversão, utiliza-se a taxa de compra para reais (BRL) e a paridade de compra para dólares (USD).

O usuário informa o ano e o formato do arquivo (Excel, CSV ou Parquet) na linha de comando, e o script Python gera um relatório com o desempenho da carteira, apresentando ao final o retorno de cada título em real e em dólar, tanto em valores absolutos quanto em percentuais.


## Objetivo
Criar um script em Python que receba o ano como argumento na linha de comando e gere um relatório da carteira em formato tabular (Excel, CSV ou Parquet).

Exemplo:
```bash
python analise.py 2025 excel
```

## 📌 Observações
O peso argentino foi ignorado, pois a URL correspondente retornava dados incorretos, associando a moeda a outros códigos e não apresentando as colunas necessárias (Data de Câmbio, Taxa de Compra e Paridade de Compra). Além disso, havia mais de um código que supostamente correspondia à mesma moeda, o que tornava a utilização imprecisa.

A intenção principal era iniciar o teste o mais rápido possível, por isso o desenvolvimento foi feito no Google Colab em vez do VS Code, já que mesmo com pandas instalado surgiam erros relacionados ao kernel. 

Como resultado, os commits não foram feitos durante o desenvolvimento, apenas ao final, quando tudo estava pronto. Foram criados para demonstrar conhecimento em versionamento, embora não tenham acompanhado a evolução real do projeto.

## Tecnologias e Ferramentas
- Python 3.13.5 – linguagem utilizada para toda a lógica do projeto;
- Git 2.51.0 - controle de versão utilizado para gerenciamento dos commits;
- Pandas – biblioteca usada para manipulação e análise de dados, criação de DataFrames e exportação de arquivos;
- Google Colab – ambiente de desenvolvimento completo, usado do início ao fim do projeto;
- API PTAX do Banco Central – consulta de cotações de moedas estrangeiras;
- Terminal / Linha de comando – execução do script local e passagem de argumentos.


## Como rodar o programa
**1. Instalar o python**
   
- Verifique se você já tem o Python instalado;
   
- Para conferir, abra o terminal e rode:
```bash
python --version
```
ou
```bash
python3 --version
```
Caso não tenha, você pode baixar em: [python.org](https://www.python.org/downloads/)

**2. Baixar o programa**

- Clone o repositório;

- Salve em uma pasta de fácil acesso (ex.: Downloads).

**3. Usando um ambiente virtual Python**

Para garantir a compatibilidade do programa em diferentes ambientes (Mac OS / Windows / Linux), recomenda-se o uso de um ambiente virtual exclusivo para este projeto. Caso já possua o ambiente Python adequado, não é necessário a criação deste ambiente.

Acesse a pasta do projeto (ex.: Downloads) e execute os seguintes comandos:

```bash
python -m venv venv
```
e

```bash
source venv/bin/activate  # Para macOS/Linux

#ou

venv\Scripts\activate     # Para Windows
```

Este projeto utiliza as seguintes dependências:

- Pandas;
- openpyxl (usado para exportar arquivos excel);
- pyarrow (usado para exortar arquivos parquet).

Para instalar as dependências necessárias, execute o comando:

```bash
pip install pandas openpyxl pyarrow

```

**4. Executar o programa**

Dentro da pasta do projeto, execute o programa passando o ano e o tipo de arquivo (Excel, CSV ou Parquet):
```bash
python analise.py 2025 excel
python analise.py 2018 csv
python analise.py 2012 parquet
```
**5. Resultado**

O arquivo gerado (`relatorio.xlsx`, `relatorio.csv` ou `relatorio.parquet`) vai aparecer na mesma pasta onde está o `analise.py`.

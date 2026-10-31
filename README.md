# Mini-Projeto Avaliativo - Módulo / Semana 7 (Turma T8)
**Aluno:** Izack Jacob Nascimento Ribeiro Serra  
**Curso:** Análise de Dados com Python (SCTEC)  

---

## 1. Objetivo
Desenvolver uma Análise Exploratória de Dados (AED) aplicada ao setor de varejo de grande volume, transformando dados transacionais brutos em informações acionáveis para tomada de decisões gerenciais. O projeto abrange etapas de carregamento eficiente via ficheiros compactados (`.zip`), diagnóstico de qualidade estrutural, remoção em larga escala de registos duplicados, tratamento de colunas vazias desnecessárias, padronização de campos textuais e de datas (`datetime`), além da estruturação de funções reutilizáveis, resumos executivos e exportação da base tratada.

---

## 2. Origem da Base de Dados
* **Fonte Original:** Base de Varejo obtida do Kaggle (`Base Varejo.csv`).
* **Arquivo de Entrada:** `Base Varejo.csv.zip` (Base transacional real contendo inicialmente 830.000 linhas e 14 colunas).
* **Arquivo Tratado de Saída:** `base_varejo_tratada.csv` (Base limpa e higienizada, contendo 733.447 registos válidos).

---

## 3. Significado das Principais Colunas Utilizadas
* **DATA:** Data em que a transação comercial foi realizada.
* **CO_ID:** Código identificador único da transação/compra.
* **CL_ID:** Código de identificação exclusivo de cada cliente.
* **CL_GENERO:** Género declarado ou registrado do cliente.
* **PR_ID:** Código identificador único do produto comercializado.
* **PR_CAT:** Categoria à qual o produto pertence.
* **PR_NOME:** Descrição/nome comercial do produto adquirido.

---

## 4. Processo e Decisões de Limpeza
O carregamento inicial foi realizado utilizando as bibliotecas `pandas` e `zipfile`, seguido de um diagnóstico estrutural aprofundado que fundamentou as seguintes decisões metodológicas:

1. **Remoção de Colunas Vazias:** Eliminação automática de colunas auxiliares excedentes (`Unnamed: 10` a `Unnamed: 13`) que estavam 100% vazias devido a delimitadores extras no ficheiro CSV original.
2. **Tratamento de Registros Duplicados:** Identificação e exclusão rigorosa de **96.553 linhas inteiramente duplicadas**, evitando a distorção volumétrica e o inflacionamento artificial de métricas de vendas e frequência.
3. **Padronização Textual:** Uniformização de campos textuais (`PR_CAT`, `PR_NOME`, `CL_GENERO`) utilizando conversão para maiúsculas/título e remoção de espaços em branco indesejados (`.str.strip()`). O campo de género recebeu tratamento de nulos mapeados para "Não Informado" e normalização de abreviaturas.
4. **Conversão de Datas:** A coluna `DATA` foi convertida com segurança para o tipo nativo `datetime` (`pd.to_datetime`), permitindo análises temporais consistentes.
5. **Gravação:** A base final tratada e otimizada foi exportada com sucesso para o ficheiro `base_varejo_tratada.csv` sem incluir o índice (`index=False`).

---

## 5. Conclusões e Resultados Numéricos
* **Volume Consolidado:** O pipeline processou com total integridade uma base robusta, resultando em **733.447 registos válidos** após a limpeza.
* **Diversidade de Clientes e Produtos:** A base higienizada abrange um ecossistema de **1.000 clientes únicos** e **229 produtos únicos** distribuídos ao longo do período transacional.
* **Amplitude Temporal:** O histórico de transações tratadas abrange o período compreendido entre **04/01/2019 e 08/12/2022**.
* **Desempenho por Categoria:** O agrupamento evidenciou que o setor de **ALIMENTOS** lidera de forma expressiva o volume de vendas na base (com 384.197 transações), seguido por **HIGIENE** (137.702) e **LIMPEZA** (128.632).
* **Recomendação de Negócio:** Direcionar campanhas de marketing direcionadas, gestão de stock otimizada e programas de fidelização para as categorias de maior saída (Alimentos e Higiene), mitigando rupturas de inventário.
* **Limitação da Análise:** A ausência de colunas detalhadas de custos operacionais impede a apuração direta da margem de lucro líquida por categoria, limitando a avaliação estritamente ao volume de transações e comportamento de compra.

---

## 6. Instruções para Execução
1. Certifique-se de possuir o **Python** e as bibliotecas `pandas` e `numpy` instaladas em seu ambiente de desenvolvimento.
2. Posicione o ficheiro compactado `Base Varejo.csv.zip` no mesmo diretório do script ou do Google Colab.
3. Execute as células do projeto sequencialmente (do carregamento até a exportação).
4. O ficheiro final tratado `base_varejo_tratada.csv` será gerado automaticamente no diretório de trabalho.

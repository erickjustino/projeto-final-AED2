![DCA](Imagens/img.jpg)
# 🌐 Análise da Taxa de Reprovação dos Cursos da UFRN com Grafos

## 📝 Descrição do Projeto

Este projeto realiza uma análise aprofundada dos dados de matrículas e reprovações nos cursos da **Universidade Federal do Rio Grande do Norte (UFRN)**. Utilizando a teoria dos grafos, o estudo modela a relação entre os diversos cursos (graduação, técnicos, etc.) para identificar padrões e conexões que possam explicar as taxas de reprovação.

A análise transforma uma massa de dados acadêmicos em uma visualização de rede, permitindo a identificação de cursos que funcionam como "hubs" de reprovação e grupos de cursos (clusters) com desafios sistêmicos semelhantes.

---

## 🎯 Objetivos

O principal objetivo é responder às seguintes perguntas:

* **Identificação:** Quais cursos possuem os maiores índices de reprovação?
* **Conexão:** Como os cursos se relacionam com base na similaridade de suas taxas de reprovação?
* **Visualização:** Como a "rede de reprovação" da universidade está estruturada e onde estão seus pontos mais críticos?

---

## 🛠️ Metodologia

A análise foi conduzida em um notebook Jupyter (`.ipynb`), seguindo os seguintes passos:

1.  **Coleta e Tratamento dos Dados:**
    * Carga de 7 arquivos `.csv` com dados públicos da UFRN.
    * Limpeza e normalização dos dados, com destaque para a criação de uma flag `reprovado` para facilitar os cálculos.
    * Padronização dos nomes das colunas para garantir consistência.

2.  **Análise e Agregação:**
    * Criação de rankings de reprovação por disciplina, por disciplina/curso e, finalmente, um ranking consolidado por curso.

3.  **Modelagem e Análise do Grafo:**
    * **Nós (Vértices):** Cada curso é representado por um nó.
    * **Arestas (Conexões):** Uma aresta ponderada é criada entre dois cursos se suas taxas de reprovação forem similares (com uma diferença abaixo de um limiar pré-definido). O peso da aresta indica o quão forte é essa similaridade.
    * **Métricas de Rede:** Análise de métricas como **densidade, grau médio e assortatividade** para entender a estrutura e a coesão da rede.

4.  **Visualização de Dados:**
    * Criação de um grafo 2D interativo e 3D onde o **tamanho dos nós** representa o número absoluto de reprovações e a **cor** indica a taxa de reprovação.
---

## 📊 Principais Resultados

A análise revelou que o problema de reprovação **não se concentra em cursos isolados**, mas sim em um **grupo coeso e densamente conectado** de cursos com perfis de reprovação semelhantes.

A alta **assortatividade (0.6577)** indica a formação de um **"núcleo duro"**, onde cursos com muitas conexões (hubs) tendem a se conectar entre si, formando o epicentro do problema.

| Métrica | Valor | Interpretação |
| :--- | :--- | :--- |
| **Nós (Cursos)** | 30 | Foco nos 30 cursos com maior número de reprovações. |
| **Arestas (Conexões)**| 122 | Rede densamente conectada. |
| **Grau Médio** | 8.13 | Em média, cada curso é similar a outros 8 cursos. |
| **Assortatividade** | 0.6577 | Cursos problemáticos tendem a se conectar entre si. |

### Visualizações

**Grafo 2D dos Cursos**
![Grafo de Cursos](Imagens/grafo2d.png)

---

## 🚀 Como Executar o Projeto

Para replicar esta análise, siga os passos abaixo:

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    cd seu-repositorio
    ```

2.  **Abra o Notebook:**
    * Faça o upload do arquivo `manipulação dos dados e visualização.ipynb` para o [Google Colab](https://colab.research.google.com/).

3.  **Execute a Célula de Upload:**
    * Rode a primeira célula de código e, quando solicitado, faça o upload dos 7 arquivos .csv **Atenção:** os arquivos estão em uma pasta .zip e precisam ser descompactados primeiro.

4.  **Execute as Células:**
    * Execute todas as células na sequência para reproduzir os rankings e as visualizações.

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** `Python 3`
* **Ambiente:** `Google Colab`
* **Bibliotecas Principais:**
    * `Pandas`: Para manipulação e tratamento dos dados.
    * `NetworkX`: Para a criação, manipulação e estudo da estrutura do grafo.
    * `Matplotlib`: Para a geração dos gráficos estáticos.
    * `Plotly`: Para visualizações interativas (não incluído no README final, mas usado no processo).
    * `adjustText`: Para melhorar a legibilidade dos rótulos no grafo.

---

> Este projeto foi desenvolvido por Erick Vinicius Justino da Silva e Leonardo Pessoa Cavalcanti para a 1ª unidade da disciplina de Algoritmos e Estrutura de Dados II (DCA/UFRN).

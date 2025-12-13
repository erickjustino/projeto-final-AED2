![DCA](Imagens/img.jpg)

# Análise de Redes Complexas: A Teia da Wikipédia

## Apresentação do Projeto
> **[INSIRA AQUI O LINK PARA O VÍDEO NO YOUTUBE/LOOM]**

---

## Descrição do Projeto

Este trabalho final da disciplina de **Estrutura de Dados II** tem como objetivo construir, visualizar e analisar uma rede complexa baseada em páginas da Wikipédia. Utilizando conceitos de Teoria dos Grafos, exploramos como tópicos aparentemente distintos se conectam através de hiperlinks.

A rede foi gerada a partir da fusão de dados de **5 Seeds (Sementes)** de domínios variados, explorando conexões até o **Nível 2 (Altura < 3)**. Devido ao crescimento exponencial da rede nesta profundidade, foi implementada uma **heurística de otimização** para viabilizar a coleta de dados e manter a coesão temática.

### Seeds Utilizados
1. **Transformer (Deep Learning)** - Tecnologia
2. **The Beatles** - Música/Cultura Pop
3. **Revolução Francesa** - História
4. **One Piece** - Entretenimento
5. **Rio Grande do Norte** - Geografia

---

## Objetivos

O projeto visa responder, visualmente e metricamente, às seguintes questões de análise de redes:

* **Centralidade:** Quais são as páginas mais influentes da rede? (Degree, Closeness ou Betweenness ou Eigenvector Centrality).
* **Topologia:** Como a rede se estrutura em termos de camadas (K-Core e K-Shell)?
* **Comunidades:** Existem grupos de páginas que formam "bolhas" de conteúdo distintas?
* **Desafio Computacional:** Como coletar uma rede massiva (Nível 2) de forma eficiente utilizando uma estrutura de dados e uma heurística ?

---

## Metodologia e Solução com uma heurística e Estrutura de Dados

A coleta de dados seguiu um pipeline rigoroso para garantir a relevância e viabilidade técnica, conforme exigido pelo **Requisito 4** do trabalho.

### 1. Coleta Inteligente (Heurística e Priority Queue)
A abordagem tradicional de busca em largura (BFS) inviabilizaria a coleta até a altura < 3 devido à explosão combinatória de links. Para resolver isso, implementamos uma **Busca Baseada em Heurística**:

* **Estrutura de Dados:** Substituímos a fila comum por uma **Fila de Prioridade (Min-Heap)** usando a biblioteca `heapq`.
* **Heurística de Score:** Cada link recebe uma pontuação inicial que é ajustada dinamicamente:
    * **Bonificação (-50 pts):** Links que contêm palavras-chave dos Seeds (ex: "Brasil", "Revolução", "Beatles") ganham alta prioridade (furam a fila).
    * **Penalidade (+20 pts):** Títulos excessivamente longos (>40 caracteres) ou irrelevantes recebem baixa prioridade.
* **Resultado:** O algoritmo prioriza a expansão de nós semanticamente relevantes, garantindo uma base de dados rica mesmo sob limitações computacionais.

### 2. Tratamento dos Dados
* **Limpeza:** Remoção de *Self-Loops* e fusão de nós duplicados (ex: Plurais e variações com hífen).
* **Filtragem (Core):** Aplicação de um filtro para manter apenas nós com **Grau ≥ 2**, eliminando páginas isoladas e reduzindo o ruído visual.

---

## Resultados e Visualizações

### 1. Métricas de Centralidade
Nesta visualização, o tamanho dos nós é proporcional ao **Grau (Degree)** e as cores representam o ****.

![Grafo Centralidade](caminho/para/imagem_requisito1.png)
> *[Adicione aqui sua análise: Ex: Os nós centrais atuam como pontes entre os clusters de História e Geografia...]*

### 2. Decomposição K-Core e K-Shell
Análise da estrutura topológica da rede, destacando o núcleo mais conectado (Core) versus a periferia (Shell).

![Grafo K-Core](caminho/para/imagem_requisito2.png)
> *[Adicione aqui sua análise: Ex: O núcleo duro da rede (K-Core máximo) é composto principalmente por páginas sobre...]*

### 3. Detecção de Comunidades
Visualização da modularidade da rede. As cores indicam diferentes comunidades (clusters) detectadas pelo algoritmo.

![Grafo Comunidades](caminho/para/imagem_requisito3.png)
> *[Adicione aqui sua análise: Ex: Foram identificadas 5 grandes comunidades bem definidas, correspondendo aos temas dos Seeds iniciais...]*

---

## Como Executar o Projeto

Para replicar a coleta e análise:

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    cd seu-repositorio
    ```

2.  **Abra o Notebook:**
    * Faça o upload do arquivo `.ipynb` para o [Google Colab](https://colab.research.google.com/).

3.  **Execute as Células:**
    * Execute todas as células na sequência para reproduzir os resultados.


## Tecnologias Utilizadas

* **Linguagem:** `Python 3`
* **Bibliotecas Principais:**
    * `Wikipedia`: Extração de dados.
    * `NetworkX`: Modelagem de grafos e algoritmos.
    * `Heapq`: Implementação de estruturas de dados eficientes.
* **Software:**
    * `Gephi`: Visualização e Análise.


> Este projeto foi desenvolvido por Alice Maria Fonseca Victorino Freire e Erick Vinicius Justino da Silva para a disciplina de Algoritmos e Estrutura de Dados II (DCA/UFRN).

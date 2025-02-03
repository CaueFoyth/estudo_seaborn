# Estudos sobre Seaborn

Este repositório contém exemplos e anotações sobre o uso da biblioteca **Seaborn** para visualização de dados em Python. Aqui, explorei diferentes tipos de gráficos, incluindo **plots de distribuição**, **plots categóricos**, **plots de regressão** e **plots matriciais**. Todos os exemplos foram desenvolvidos utilizando o **Jupyter Lab** com o **Anaconda**.

---

## Ferramentas Utilizadas
- **Python**: Linguagem de programação principal.
- **Seaborn**: Biblioteca para visualização de dados estatísticos.
- **Matplotlib**: Biblioteca para criação de gráficos.
- **Jupyter Lab**: Ambiente interativo para desenvolvimento de código.
- **Anaconda**: Distribuição Python que facilita o gerenciamento de pacotes e ambientes.

---

## Plots de Distribuição e Categóricos

Nesta seção, explorei como visualizar a distribuição de dados e trabalhar com variáveis categóricas. Abaixo estão os principais conceitos e exemplos de código que aprendi:

### Exemplos de Código

1. **Distribuição de Dados com `displot`**:
   ```python
   tips = sns.load_dataset('tips')
   sns.displot(tips['total_bill'], kde=True)  # Valores concentrados com linha de densidade
   sns.displot(tips['total_bill'], kde=False, bins=30)  # Valores concentrados em colunas
   ```

2. **Gráficos de Dispersão com `jointplot`**:
   ```python
   sns.jointplot(x="total_bill", y="tip", data=tips, kind="reg")  # Gráfico de dispersão com linha de regressão
   sns.jointplot(x="total_bill", y="tip", data=tips, kind="hex")  # Gráfico de dispersão com hexbin
   ```

3. **Correlação entre Variáveis com `pairplot`**:
   ```python
   sns.pairplot(tips, hue="sex", palette="coolwarm")  # Correlação entre variáveis numéricas, colorido por sexo
   ```

4. **Visualização de Concentração de Dados**:
   ```python
   sns.rugplot(tips["total_bill"])  # Rugplot para ver concentração de dados
   sns.kdeplot(tips["total_bill"])  # KDE plot para estimativa de densidade
   ```

5. **Gráficos Categóricos**:
   ```python
   sns.barplot(x="sex", y="total_bill", data=tips)  # Média de total_bill por sexo
   sns.barplot(x="sex", y="total_bill", data=tips, estimator=np.std)  # Desvio padrão de total_bill por sexo
   sns.countplot(x="sex", data=tips)  # Contagem de sexos
   ```

6. **Boxplot e Violinplot**:
   ```python
   sns.boxplot(x="day", y="total_bill", data=tips, hue="day", palette="rainbow")  # Boxplot por dia
   sns.violinplot(x="total_bill", y="day", data=tips, hue="sex", palette="rainbow", split=True)  # Violinplot dividido por sexo
   ```

7. **Swarmplot**:
   ```python
   sns.swarmplot(x="day", y="total_bill", data=tips)  # Swarmplot para visualização de pontos individuais
   ```

---

## Plots de Regressão

Nesta seção, explorei como criar gráficos de regressão para visualizar relações entre variáveis e ajustar modelos lineares. Abaixo estão os principais conceitos e exemplos de código que aprendi:

### Exemplos de Código

1. **Gráfico de Regressão com `lmplot`**:
   ```python
   sns.lmplot(x="total_bill", y="tip", data=tips, hue="sex", markers=['o', 'v'], scatter_kws={'s':100}, aspect=1.6)
   plt.show()
   ```
   - **`hue`**: Diferencia os pontos por sexo.
   - **`markers`**: Personaliza os marcadores dos pontos.
   - **`scatter_kws`**: Ajusta o tamanho dos pontos.
   - **`aspect`**: Controla o tamanho do gráfico.

2. **Gráfico de Regressão com Facetas**:
   ```python
   sns.lmplot(x="total_bill", y="tip", data=tips, hue="sex", col="time", row="day")
   plt.show()
   ```
   - **`col`**: Divide o gráfico em colunas com base no horário (almoço e jantar).
   - **`row`**: Divide o gráfico em linhas com base no dia da semana.

---

## Plots Matriciais

Nesta seção, explorei como criar visualizações matriciais, como heatmaps e clustermaps, para analisar dados em formato de matriz. Abaixo estão os principais conceitos e exemplos de código que aprendi:

### Exemplos de Código

1. **Organizando Dados em uma Matriz**:
   ```python
   flights = sns.load_dataset('flights')
   df_flights_matrix = flights.pivot_table(index="year", columns="month", values="passengers", observed=True)
   df_flights_matrix
   ```
   - **`pivot_table`**: Transforma os dados em uma matriz, onde as linhas são os anos, as colunas são os meses e os valores são o número de passageiros.

2. **Heatmap**:
   ```python
   fig, ax = plt.subplots(figsize=(15, 5))  # Define o tamanho do gráfico
   sns.heatmap(df_flights_matrix, ax=ax, annot=True, fmt=".0f", linewidths=1, cmap="magma")
   plt.show()
   ```
   - **`annot`**: Exibe os valores dentro das células.
   - **`fmt`**: Formata os valores (ex.: `.0f` para números inteiros).
   - **`linewidths`**: Define a espessura das linhas entre as células.
   - **`cmap`**: Escolhe o mapa de cores (ex.: "magma").

3. **Clustermap**:
   ```python
   sns.clustermap(df_flights_matrix)
   plt.show()
   ```
   - **`clustermap`**: Cria um heatmap com agrupamento hierárquico (clustering) para identificar padrões nos dados.

---

## Como Executar os Exemplos

1. Instale o [Anaconda](https://www.anaconda.com/products/distribution) para gerenciar pacotes e ambientes Python.
2. Abra o **Jupyter Lab** a partir do Anaconda Navigator.
3. Clone este repositório ou baixe os arquivos `.ipynb`.
4. Execute os códigos no Jupyter Lab para visualizar os gráficos.

---

## Conclusão

Este repositório é um guia prático para aprender a usar o Seaborn, desde gráficos básicos até visualizações mais avançadas. Sinta-se à vontade para explorar, modificar e expandir os exemplos!

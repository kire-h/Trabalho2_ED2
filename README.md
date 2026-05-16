# 🗺️ Análise de Redes Viárias Urbanas — ED2

Ferramenta para análise de redes viárias urbanas a partir de dados do OpenStreetMap, com cálculo de métricas de centralidade, identificação de hubs, decomposição K-Core e exportação para o Gephi.
Nesse trabalho foi analisada a rede viária do bairro **Potengi, Natal/RN**, modelada como um grafo não-direcionado de vias de tráfego.

### Justificativa da escolha da região:

Os alunos moram na zona norte e estudaram no IFZN localizado nesse bairro.

![IFRN Campus Natal Zona Norte](images/IFRN.jpg)

### Alunos:
- Alan César Rebouças de Araújo Carvalho
- Erick Henrique da Silva Paz
- Matheus Silva Mendes

---

## 🚀 Instalação

### 📦 Dependências

| Biblioteca | Uso |
|---|---|
| `osmnx` | Download e modelagem da rede viária via OpenStreetMap |
| `networkx` | Construção e análise dos grafos |
| `matplotlib` | Visualização dos grafos e histogramas |
| `numpy` | Cálculo de percentis e estatísticas |

### 1. Clone o repositório

```bash
git clone https://github.com/kire-h/Trabalho2_ED2
cd Trabalho2_ED2
```

### 2. Instale as dependências Python

```bash
pip install osmnx networkx matplotlib numpy
```

> ⚠️ O notebook foi desenvolvido no **Google Colab**. Para rodar localmente, certifique-se de que as dependências acima estão instaladas no seu ambiente.

---

## ▶️ Como usar

### Google Colab (recomendado)

1. Faça upload do arquivo `Trabalho_ED2.ipynb` no Google Colab
2. Execute as células em ordem
3. Os grafos e arquivos `.graphml` serão gerados automaticamente

### Localmente

```bash
jupyter notebook Trabalho_ED2.ipynb
```

> ⚠️ A célula de instalação (`!pip install osmnx`) pode ser ignorada se as dependências já estiverem instaladas.

---

## 🖥️ Estrutura do Notebook

O notebook está organizado nas seguintes etapas:

1. **Download da rede viária** — extração do grafo do bairro Potengi via OSMnx
2. **Conversão do grafo** — transformação de MultiDiGraph em grafo não-direcionado simples
3. **Cálculo das métricas** — grau, betweenness, closeness e core number
4. **Visualizações** — mapas coloridos por centralidade e histogramas de distribuição
5. **Exportação** — salvamento do grafo em formato `.graphml` compatível com o Gephi


## 📁 Estrutura do repositório

```text
├── Trabalho_ED2.ipynb        # Notebook principal de análise
├── rede_urbana.graphml       # Grafo exportado com atributos (padrão NetworkX)
├── rede_urbana_2.graphml     # Grafo exportado compatível com Gephi
├── images                    # Pasta com as imagens utilizadas no README.md
└── README.md                 # Documentação principal do repositório
```
---

## 🔬 Abrindo no Gephi

1. Gere o arquivo `rede_urbana_2.graphml` rodando o notebook
2. Abra o Gephi
3. **File → Open** → selecione o arquivo `rede_urbana_2.graphml`
4. O grafo será carregado com os atributos de latitude, longitude, grau, betweenness, closeness e core number já tipados corretamente

> O notebook corrige automaticamente os tipos dos atributos no `.graphml` (double, int) para garantir compatibilidade total com o Gephi.

---

## Objetivos do Trabalho 


1. Modelar a malha viária do bairro Potengi (Natal/RN) como um grafo a partir de dados reais do OpenStreetMap
2. Calcular métricas de centralidade da rede, como Betweenness e Closeness Centrality, identificando os cruzamentos mais críticos para o fluxo urbano
3. Identificar os principais hubs da rede, ou seja, os nós com maior número de conexões
4. Aplicar a decomposição K-Core para encontrar o núcleo mais denso e bem conectado da malha viária
5. Visualizar as métricas calculadas diretamente sobre o mapa do bairro, com coloração por intensidade
6. Exportar o grafo no formato .graphml compatível com o Gephi para análises visuais avançadas

---

## 📈 Metodologia 

1. Extração da rede viária do bairro Potengi via OSMnx
2. Conversão do grafo original (MultiDiGraph direcionado) para um grafo não-direcionado simples, removendo arestas paralelas e laços para viabilizar as análises
3. Cálculo do grau de cada nó e plotagem da distribuição de grau da rede para compreender o perfil de conectividade dos cruzamentos
4. Identificação dos Top 10 Hubs — os cruzamentos com maior número de conexões diretas na malha viária
5. Cálculo da Betweenness Centrality ponderada pela distância real das vias (weight='length'), identificando os nós que funcionam como principais pontes de fluxo
6. Cálculo da Closeness Centrality também ponderada pela distância real, identificando os nós com melhor acesso ao restante da rede
7. Aplicação do algoritmo de K-Core para decompor a rede em subgrafos por densidade, extraindo o Main Core (subgrafo com o maior k possível)
8. Visualização das métricas sobre o mapa urbano real usando paletas de cores (inferno para Betweenness, plasma para Closeness)
9. Exportação do grafo enriquecido com todos os atributos calculados para o formato .graphml, com correção manual dos tipos de dados para compatibilidade com o Gephi

---

## Resultados Obtidos

### Grafo da região obtido

![Potengi, Zona Norte](images/mapa.svg)

### Grafo da distribuição de grau


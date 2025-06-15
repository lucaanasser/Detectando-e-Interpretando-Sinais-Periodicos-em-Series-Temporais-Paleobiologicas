# Detectando e Interpretando Sinais Periódicos em Séries Temporais Paleobiológicas

**Análise Espectral de Diversidade de Gêneros Marinhos**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![NumPy](https://img.shields.io/badge/NumPy-1.21+-green.svg)](https://numpy.org/)
[![SciPy](https://img.shields.io/badge/SciPy-1.7+-red.svg)](https://scipy.org/)

## Resumo

Este projeto implementa uma análise espectral robusta para detectar e interpretar sinais periódicos em séries temporais paleobiológicas. Utilizamos dados de diversidade de gêneros marinhos ao longo do tempo geológico (últimos 542 milhões de anos) para investigar padrões cíclicos que podem estar relacionados a processos geológicos, climáticos ou astronômicos.

## Objetivos

O projeto busca detectar e interpretar sinais periódicos em séries temporais de diversidade de gêneros marinhos ao longo do tempo geológico. A análise é baseada em métodos espectrais e testes estatísticos, seguindo a metodologia apresentada no artigo de referência. Mais especificamente:

- **Detectar periodicidades** significativas na diversidade de gêneros marinhos
- **Validar estatisticamente** os padrões encontrados usando modelos nulos

## Metodologia

### 1. Pré-processamento de Dados
- **Carregamento:** Dados CSV de diversidade temporal
- **Remoção de tendência:** Ajuste polinomial de grau 3

### 2. Análise Espectral
- **Transformada de Fourier (FFT)** com zero-padding para melhor resolução
- **Identificação de picos**

### 3. Modelos Nulos (Monte Carlo)
- **Modelo R (Random Walk):** Embaralhamento de incrementos temporais
- **Modelo W (Windowed Bootstrap):** Embaralhamento de blocos contíguos
- **30.000 simulações** para cada modelo nulo

### 4. Testes de Significância
- **Significância pontual:** P-valor na frequência específica
- **Significância global:** P-valor considerando todas as frequências

## Resultados

### Periodicidades Identificadas
- **62 Myr:** Pico altamente significativo 
- **140 Myr:** Pico não significativo 

### Testes de Significância
| Período | R (pontual) | W (pontual) | R (global) | W (global) |
|---------|-------------|-------------|------------|------------|
| 62 Myr  | < 5×10⁻⁵    | < 4×10⁻⁴    | < 0.002    | < 0.02     |
| 140 Myr | ~ 0.12      | < 0.006     | ~ 0.71     | ~ 0.13     |

## Estrutura do Projeto

```
├── ep1.ipynb                 # Notebook principal com análise completa
├── README.md                 # Este arquivo
├── requirements.txt          # Dependências do projeto
├── data/
│   ├── raw/
│   │   └── genera_data.csv   # Dados originais de diversidade
│   └── processed/            # Resultados e gráficos gerados
│       └── *.png            # Visualizações da análise
│       
└── comp4_ep1_instrucoes.pdf # Instruções do projeto
```

## Dependências
- numpy 
- pandas 
- matplotlib 
- scipy 
- plotly 
- pathlib

## Como Executar

### 1. Preparação do Ambiente
```bash
# Clone o repositório
git clone <https://github.com/lucaanasser/Detectando-e-Interpretando-Sinais-Periodicos-em-Series-Temporais-Paleobiologicas.git>

# Crie e ative um ambiente virtual
python -m venv venv

# Instale as dependências
pip install -r requirements.txt
```

### 2. Execução da Análise
```bash
# Inicie o Jupyter Notebook
jupyter notebook

# Abra o arquivo ep1.ipynb
# Execute todas as células sequencialmente
```

### 3. Estrutura dos Dados
Certifique-se de que o arquivo `data/raw/genera_data.csv` contenha:
- **TimeBin:** Idade em milhões de anos (Myr)
- **Diversity:** Número de gêneros marinhos

## Informações do Projeto

**Disciplina:** CCM0228 - Computação IV (2025.1)  
**Autores:**
- Helena Baptista Reis (NUSP: 14577622)
- Luca Marinho Nasser Valadares Paiva (NUSP: 13691375)



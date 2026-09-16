# 🐜 Turismo ACO

Otimização de roteiros turísticos urbanos com Ant Colony Optimization.

[![Python 3.11+](https://img.shields.io/badge/python-3.11%2B-blue)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Projeto

Um sistema que planeja roteiros em cidades reais usando formigas virtuais (Ant Colony Optimization).

**Problema:** Com 15 pontos turísticos, existem 1,3 **trilhões** de combinações possíveis.  
**Solução:** ACO encontra roteiros excelentes em segundos, respeitando orçamento e tempo.

## Status

| Fase | Descrição | Status |
|------|-----------|--------|
| 1 | Dados e grafos (OSMnx) | 📍 Desenvolvimento |
| 2 | Motor ACO Puro (TDD) | 🎯 Próxima |
| 3 | Variantes + Comparação | 📖 Planejando |
| 4 | Restrições Turísticas | 📖 Planejando |
| 5 | Interface Streamlit | 📖 Planejando |

[📊 Acompanhar progresso no Project](https://github.com/users/luanfelixcoding/projects/1)

## Quick Start

```bash
# Setup
git clone https://github.com/seu-user/ant-colony-tourism.git
cd ant-colony-tourism

python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt

# Rodar testes
pytest

# Rodar interface
streamlit run app.py
```

## Stack

- **Dados:** OSMnx, NetworkX, Pydantic v2
- **Algoritmo:** NumPy, multiprocessing, scipy
- **UI:** Streamlit, Folium, Plotly
- **Testes:** pytest, hypothesis
- **DevOps:** Docker

## Estrutura
```bash
ant-colony-tourism/
│
├── src/
│   ├── __init__.py
│   │
│   ├── domain/                              # Modelos e regras centrais do domínio
│   │   ├── __init__.py
│   │   ├── models.py                        # PontoTuristico, PerfilTurista, Rota etc.
│   │   └── enums.py                         # TipoAlgoritmo, CategoriaPonto etc.
│   │
│   ├── maps/                                # Integração com mapas e dados geográficos
│   │   ├── __init__.py
│   │   ├── downloader.py                    # Baixa e armazena grafos do OpenStreetMap
│   │   ├── graph_builder.py                 # Constrói e prepara grafos com OSMnx/NetworkX
│   │   └── distance_matrix.py               # Calcula matrizes de distância entre pontos
│   │
│   ├── optimization/                        # Núcleo dos algoritmos de otimização
│   │   ├── __init__.py
│   │   ├── ant.py                           # Representa uma formiga e constrói uma solução
│   │   ├── colony.py                        # Gerencia a colônia, iterações e feromônios
│   │   ├── variants.py                      # Variantes do ACO: ACS, MMAS, AS elitista
│   │   ├── fitness.py                       # Avaliação e cálculo da qualidade das rotas
│   │   └── baseline.py                      # Algoritmos de referência: Greedy e 2-opt
│   │
│   ├── benchmark/                           # Avaliação experimental dos algoritmos
│   │   ├── __init__.py
│   │   ├── profiler.py                      # Mede desempenho e tempo de execução
│   │   └── comparator.py                    # Executa algoritmos e compara resultados
│   │
│   └── ui/                                  # Interface gráfica da aplicação
│       ├── __init__.py
│       ├── map_renderer.py                  # Renderiza rotas e pontos com Folium
│       ├── sidebar.py                       # Controles e parâmetros do usuário
│       ├── charts.py                        # Gráficos e visualizações com Plotly
│       └── pdf_exporter.py                  # Gera relatórios e exporta rotas para PDF
│
├── tests/                                   # Testes automatizados do projeto
│   ├── __init__.py
│   ├── conftest.py                          # Fixtures e configurações compartilhadas
│   ├── test_models.py                       # Testes dos modelos do domínio
│   ├── test_ant.py                          # Testes da construção de soluções pela formiga
│   ├── test_colony.py                      # Testes do comportamento da colônia
│   ├── test_fitness.py                     # Testes das funções de avaliação
│   └── test_integration.py                 # Teste completo do fluxo da aplicação
│
├── data/                                   # Dados gerados e armazenados pela aplicação
│   ├── .gitkeep
│   ├── graphs/                             # Grafos OSMnx armazenados em cache
│   │   └── .gitkeep
│   └── distance_matrices/                  # Matrizes de distância pré-calculadas
│       └── .gitkeep
│
├── .github/
│   └── workflows/
│       └── ci.yml                          # Pipeline de integração contínua
│
├── .gitignore                              # Arquivos ignorados pelo Git
├── README.md                               # Documentação, instalação e uso do projeto
├── requirements.txt                        # Dependências Python do projeto
├── pyproject.toml                           # Configurações de Python, Ruff, Mypy e Pytest
├── Dockerfile                              # Configuração para execução em container
└── app.py                                  # Ponto de entrada da aplicação Streamlit

```

## Autores

- [Luan Felix](https://github.com/luanfelixcoding)
- [Thiago Medeiros](https://github.com/ThiagoMedeiros12)

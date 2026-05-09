# Problema de Corte Unidimensional — AV2

Trabalho da disciplina **Modelagem em Programação Matemática** (Unifor).
Implementação de um modelo genérico de **Programação Linear Inteira** para o **Problema de Corte Unidimensional** (Cutting Stock 1D), utilizando **OR-Tools** com o solver SCIP.

## Equipe

| Integrante  | Matrícula   |
| ----------- | ----------- |
| Nelson      | _matrícula_ |
| Luiz Carlos | _matrícula_ |
| Isaias      | _matrícula_ |

## Sobre o problema

Dada uma barra de comprimento `L` e um conjunto de itens com tamanhos `ℓ₁, …, ℓₙ` e demandas `d₁, …, dₙ`, o objetivo é decidir **como cortar as barras** de forma a **atender exatamente toda a demanda minimizando o desperdício total** (sobras das barras).

A formulação adotada é a clássica de **Gilmore-Gomory**, baseada em **padrões de corte maximais**:

- Enumera-se o conjunto `P` de todos os padrões maximais válidos (combinações `(a₁ⱼ, …, aₙⱼ)` em que a sobra é menor que o menor item, de modo que nenhum item adicional caberia).
- Variável de decisão: `xⱼ ∈ ℤ₊` = nº de barras cortadas usando o padrão `j`.
- Objetivo: `min Σⱼ wⱼ · xⱼ`, onde `wⱼ = L − Σᵢ aᵢⱼ ℓᵢ` é o desperdício do padrão `j`.
- Restrição: `Σⱼ aᵢⱼ · xⱼ = dᵢ`, para cada tipo de item `i` (atendimento exato da demanda).

A formulação completa está documentada em [planning.md](planning.md) e na primeira célula do notebook.

## Estrutura do projeto

```text
AVF2_ModelagemProgMat_Unifor/
├── README.md                    # este arquivo
├── trabalho.md                  # enunciado do trabalho
├── planning.md                  # documento de planejamento e decisões de modelagem
├── corte_unidimensional.ipynb   # implementação principal (entrega)
└── TRABALHO_CC_OR_TOOLS_CORTE.pdf
```

## Requisitos

- Python 3.8+
- Jupyter (para abrir o notebook) ou Google Colab
- Biblioteca `ortools` (instalada pela primeira célula do notebook)

## Como executar

### Opção 1 — Google Colab (recomendado para a apresentação)

1. Faça upload do arquivo `corte_unidimensional.ipynb` no [Google Colab](https://colab.research.google.com).
2. Execute as células em ordem (`Shift + Enter`).
3. Quando a célula de entrada for executada, **digite os dados do problema** nos prompts que aparecerão.

### Opção 2 — Jupyter local

```bash
pip install jupyter ortools
jupyter notebook corte_unidimensional.ipynb
```

Execute as células sequencialmente. A célula de entrada solicitará os dados via `input()`.

## Exemplo de entrada (caso do enunciado)

Quando os prompts aparecerem, digite:

```text
Tamanho da barra: 150
Quantidade de tipos de itens: 3
Tamanho do item tipo 1: 80
Tamanho do item tipo 2: 60
Tamanho do item tipo 3: 50
Demanda do item tipo 1: 70
Demanda do item tipo 2: 100
Demanda do item tipo 3: 120
```

### Saída esperada

- **5 padrões maximais** gerados:

| j | (a₁, a₂, a₃) | Desperdício |
| - | ------------ | ----------- |
| 1 | (0, 0, 3)    | 0           |
| 2 | (0, 1, 1)    | 40          |
| 3 | (0, 2, 0)    | 30          |
| 4 | (1, 0, 1)    | 20          |
| 5 | (1, 1, 0)    | 10          |

- **Modelo PLI** impresso em formato LP via `solver.ExportModelAsLpFormat(False)`.
- **Solução ótima**:
  - x₁ = 40 — padrão (0,0,3)
  - x₃ = 15 — padrão (0,2,0)
  - x₅ = 70 — padrão (1,1,0)
- **Total de barras**: 125
- **Desperdício total**: 1150 m

## Outro exemplo de entrada (para teste)

```text
Tamanho da barra: 100
Quantidade de tipos de itens: 2
Tamanho do item tipo 1: 45
Tamanho do item tipo 2: 30
Demanda do item tipo 1: 50
Demanda do item tipo 2: 80
```

## Observações sobre a implementação

- Utiliza **exclusivamente** a biblioteca OR-Tools (`pywraplp` + SCIP), conforme exigência do enunciado.
- Sintaxe alinhada com os exercícios da disciplina (`Solver.CreateSolver('SCIP')`, `IntVar`, `Objective` + `SetCoefficient` + `SetMinimization`, `RowConstraint` + `SetCoefficient`, `ExportModelAsLpFormat`).
- A geração dos padrões é feita por busca recursiva e produz **todos os padrões maximais — nem mais, nem menos** — atendendo o requisito crítico do enunciado.

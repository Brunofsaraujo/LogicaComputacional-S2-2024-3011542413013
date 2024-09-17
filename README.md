# Lógica Computacional - Fatec Votorantim 2S-2024
- Bruno Felipe de Souza Araujo
- bruno.araujo25@fatec.sp.gov.br
- https://github.dev/Brunofsaraujo

Repositório referente ao exercício avaliativo de Lógica Computacional da instituição **Fatec Votorantim** - 2º Semestre de 2024.

## 📚 Atividade Avaliativa

**Objetivo:** Geração da tabela-verdade para demonstração da propriedade do **Dilema Construtivo (DC)**.

### Formulação:

A fórmula que demonstra o Dilema Construtivo (DC) é a seguinte:

```python
((p -> q) AND (r -> s) AND (p OR r)) -> (q OR s)
```

## 📦 Dependências

O módulo utiliza as seguintes bibliotecas Python:

- `pandas`: Para manipulação de dados utilizando `DataFrames`.
- `tabulate`: Para imprimir as tabelas formatadas no terminal.

Você pode instalar as dependências utilizando o comando:

```bash
%pip install pandas
%pip install tabulate
```

## 🚀 Funções

Esta atividade contém funções para calcular operações lógicas básicas e gerar tabelas verdade para fórmulas lógicas. 

### Funções disponíveis:
### conversao_booleano(valor):
- Converte um valor fornecido para um booleano. Aceita valores como 0, 1, 'V', 'F', True, False e suas representações em string.

### conjuncao(x, y):
- Calcula a conjunção (AND) lógica entre dois valores. Retorna 'V' se ambos os valores forem verdadeiros, caso contrário, 'F'.

### disjuncao(x, y):
- Calcula a disjunção (OR) lógica entre dois valores. Retorna 'V' se pelo menos um dos valores for verdadeiro, caso contrário, 'F'.

### condicional(x, y):
- Calcula a condicional (implicação) lógica entre dois valores. Retorna 'V' se a implicação lógica for verdadeira, caso contrário, 'F'.

### bicondicional(x, y):
- Calcula o bicondicional (equivalência lógica) entre dois valores. Retorna 'V' se ambos os valores forem iguais, caso contrário, 'F'.

### imprimir_tabela_verdade(df):
- Imprime a tabela verdade em formato tabulado utilizando a biblioteca tabulate.

### gerar_dataframe_base_tabela_verdade(proposicoes: list[str]) -> pd.DataFrame:
- Gera um DataFrame base para a tabela verdade com base nas proposições fornecidas. Calcula as combinações de valores booleanos possíveis.

### avaliar_formula(coluna, passo):
- Avalia uma fórmula lógica utilizando os operadores lógicos AND, OR, implicação e equivalência. Retorna o resultado da operação para a coluna fornecida.

### resolucao_tabela_verdade(formula: str, passos_resolucao: dict[str, str]) -> pd.DataFrame:
- Resolve uma fórmula lógica dada e retorna a tabela verdade correspondente. Utiliza a fórmula e os passos de resolução para calcular os valores booleanos.

```python
Exemplo de uso:
    passos_resolucao = {
        'a': 'p -> q',
        'b': 'r -> s',
        'c': 'p OR r',
        'd': 'a AND b',
        'e': 'd AND c',
        'f': 'q OR s',
        'g': 'e -> f',
    }

    formula_dilema_construtivo = "((p -> q) AND (r -> s) AND (p OR r)) -> (q OR s)"

    dataFrame = resolucao_tabela_verdade(formula_dilema_construtivo, passos_resolucao)
    dataFrame.rename(columns={'a': 'p -> q'}, inplace=True)
    dataFrame.rename(columns={'b': 'r -> s'}, inplace=True)
    dataFrame.rename(columns={'c': 'p OR r'}, inplace=True)
    dataFrame.rename(columns={'d': '(p -> q) AND (r -> s)'}, inplace=True)
    dataFrame.rename(columns={'e': '(p -> q) AND (r -> s) AND (p OR r)'}, inplace=True)
    dataFrame.rename(columns={'f': 'q OR s'}, inplace=True)
    dataFrame.rename(columns={'g': '((p -> q) AND (r -> s) AND (p OR r)) -> (q OR s)'}, inplace=True)
    
    imprimir_tabela_verdade(dataFrame)
```
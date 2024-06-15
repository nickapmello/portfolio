---
title: Aula Prática 2
date: 2024-06-01
---

### Introdução à Interpolação Polinomial de Newton

A interpolação polinomial de Newton é uma técnica matemática utilizada para estimar valores desconhecidos que se encontram dentro do intervalo de um conjunto de pontos conhecidos. Em muitas aplicações práticas, temos um conjunto de dados discretos e precisamos prever ou estimar valores entre esses pontos. A interpolação de Newton é uma forma eficiente de construir polinômios interpoladores que passam exatamente por cada ponto dado.

### Objetivo do Código

O código desenvolvido para a atividade prática tem como objetivo realizar a interpolação polinomial de Newton entre vários pontos fornecidos pelo usuário. Ele calcula os coeficientes do polinômio interpolador usando diferenças divididas e, em seguida, usa esses coeficientes para estimar valores intermediários. Abaixo está o código completo seguido de uma explicação detalhada de suas funções:

```python
def calc_coeficientes(x, y):
    if len(y) == 1:
        return y[0]
    else:
        return (calc_coeficientes(x[1:], y[1:]) - calc_coeficientes(x[:-1], y[:-1])) / (x[-1] - x[0])

def polinomio(x, y):
    n = len(x)
    coeficientes = []
    for i in range(n):
        coeficientes.append(calc_coeficientes(x[:i + 1], y[:i + 1]))
    return coeficientes

def calc_polinomio(coeficientes, x, valor):
    n = len(coeficientes)
    resultado = coeficientes[0]
    for i in range(1, n):
        termo = coeficientes[i]
        for j in range(i):
            termo *= (valor - x[j])
        resultado += termo
    return resultado

def interpolacao(x, y, valor):
    coeficientes = polinomio(x, y)
    return calc_polinomio(coeficientes, x, valor)

x_pontos = [1, 2.4, 3, 3.7, 5]
y_pontos = [0.6, 1.3, 1.6, 1.9, 1.2]

valor_a_interpolar = 4

valor_interpolado = interpolacao(x_pontos, y_pontos, valor_a_interpolar)
print(f"O valor interpolado em x = {valor_a_interpolar} é {valor_interpolado:.4f}")
```

### Explicando o código desenvolvido
```python
def calc(x, y):
    if len(y) == 1:
        return y[0]
    else:
        return (calc(x[1:], y[1:]) - calc(x[:-1], y[:-1])) / (x[-1] - x[0])
```
Esta função calcula os coeficientes de diferenças divididas recursivamente. A diferença dividida é uma generalização do coeficiente angular usado na interpolação linear, permitindo calcular coeficientes para polinômios de grau superior. Se houver apenas um ponto, a função retorna o valor de y. Caso contrário, calcula a diferença dividida entre os pontos.

```python
def polinomio(x, y):
    n = len(x)
    coeficientes = []
    for i in range(n):
        coeficientes.append(calc(x[:i + 1], y[:i + 1]))
    return coeficientes

```
Esta função usa a função 'calc' para calcular os coeficientes do polinômio interpolador de Newton. Ela itera sobre o conjunto de pontos, calculando as diferenças divididas necessárias e armazenando esses coeficientes em uma lista.

```python
def calc_polinomio(coeficientes, x, valor):
    n = len(coeficientes)
    resultado = coeficientes[0]
    for i in range(1, n):
        termo = coeficientes[i]
        for j in range(i):
            termo *= (valor - x[j])
        resultado += termo
    return resultado
```
Esta função avalia o polinômio interpolador em um valor específico usando os coeficientes calculados. Ela aplica o método de Horner para calcular o valor do polinômio de forma eficiente.

```python
def interpolacao(x, y, valor):
    coeficientes = polinomio(x, y)
    return calc_polinomio(coeficientes, x, valor)

```
A função 'interpolacao' coordena o cálculo dos coeficientes e a avaliação do polinômio. Ela primeiro calcula os coeficientes do polinômio interpolador usando a função 'polinomio' e, em seguida, avalia o polinômio no valor desejado usando a função 'calc_polinomio'.

```python
x_pontos = [1, 2.4, 3, 3.7, 5]
y_pontos = [0.6, 1.3, 1.6, 1.9, 1.2]

valor_a_interpolar = 4

valor_interpolado = interpolacao(x_pontos, y_pontos, valor_a_interpolar)
print(f"O valor interpolado em x = {valor_a_interpolar} é {valor_interpolado:.4f}")
```
Este é o final do código, onde são listados 5 específicos valores para os pontos de 'x' e para os pontos de 'y' e o valor de 'x' no qual queremos interpolar de um valor estimado para obter o valor final de 'y'. Por tanto, o código executa a interpolação para o valor de x especificado 'valor_a_interpolar', calculando o valor correspondente de y usando o polinômio interpolador de Newton construído a partir dos pontos fornecidos.


Para mais informações, este é o meu GitHub com os dados corretos:
[GitHub - Portfólio Calculo Numerico](https://github.com/nickapmello/portfolio).

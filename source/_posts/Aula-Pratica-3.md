---
title: Aula Prática 3
date: 2024-06-03
---

### Introdução à Interpolação Polinomial de Lagrange

A interpolação de Lagrange é uma técnica matemática utilizada para estimar valores desconhecidos dentro do intervalo de um conjunto de pontos conhecidos. Em muitas aplicações práticas, temos um conjunto de dados discretos e precisamos prever ou estimar valores entre esses pontos. A interpolação de Lagrange constrói um polinômio que passa exatamente por cada ponto dado, sendo uma ferramenta poderosa e flexível para diversas aplicações.

### Objetivo do Código

O código desenvolvido para a atividade prática tem como objetivo realizar a interpolação de Lagrange entre vários pontos fornecidos pelo usuário. Ele calcula o valor interpolado usando os polinômios básicos de Lagrange e a soma ponderada dos valores de y nos pontos dados. Abaixo está o código completo seguido de uma explicação detalhada de suas funções:

```python
def calc_polinomio(pontos_x, i, x_interpolar):
    polinomio_basico = 1
    for j in range(len(pontos_x)):
        if i != j:
            polinomio_basico *= (x_interpolar - pontos_x[j]) / (pontos_x[i] - pontos_x[j])
    return polinomio_basico

def calc_poli_lagrange(pontos_x, pontos_y, x_interpolar):
    resultado_interpolado = 0
    for i in range(len(pontos_x)):
        L_i = calc_polinomio(pontos_x, i, x_interpolar)
        resultado_interpolado += pontos_y[i] * L_i
    return resultado_interpolado

def solicitar_pontos():
    quantidade_de_pontos = int(input("Quantos pontos você deseja inserir? "))
    pontos_x = []
    pontos_y = []

    for i in range(quantidade_de_pontos):
        x = float(input(f"Digite o valor de x_{i}: "))
        y = float(input(f"Digite o valor de f(x_{i}): "))
        pontos_x.append(x)
        pontos_y.append(y)

    return pontos_x, pontos_y

def valor_final():
    pontos_x, pontos_y = solicitar_pontos()
    x_interpolar = float(input("Digite o valor de x para interpolação: "))
    resultado = calc_poli_lagrange(pontos_x, pontos_y, x_interpolar)
    print(f"O valor interpolado em x = {x_interpolar} é {resultado}")

if __name__ == "__valor_final__":
    valor_final()
```

### Explicando o código desenvolvido
```python
def calc_polinomio(pontos_x, i, x_interpolar):
    polinomio_basico = 1
    for j in range(len(pontos_x)):
        if i != j:
            polinomio_basico *= (x_interpolar - pontos_x[j]) / (pontos_x[i] - pontos_x[j])
    return polinomio_basico
```
Esta função calcula o polinômio básico de Lagrange Li(x) para um ponto específico 'i'. O polinômio básico é construído como um produto de frações que dependem dos pontos fornecidos, exceto o ponto 'i'. Este polinômio é usado para calcular a contribuição de cada ponto yi na interpolação.

```python
def calc_poli_lagrange(pontos_x, pontos_y, x_interpolar):
    resultado_interpolado = 0
    for i in range(len(pontos_x)):
        L_i = calc_polinomio(pontos_x, i, x_interpolar)
        resultado_interpolado += pontos_y[i] * L_i
    return resultado_interpolado
```
Esta função calcula o valor interpolado em 'x' usando os polinômios básicos de Lagrange. Ela soma as contribuições ponderadas de cada ponto 'yi' onde os pesos são os valores dos polinômios básicos calculados na função anterior.

```python
def solicitar_pontos():
    quantidade_de_pontos = int(input("Quantos pontos você deseja inserir? "))
    pontos_x = []
    pontos_y = []

    for i in range(quantidade_de_pontos):
        x = float(input(f"Digite o valor de x_{i}: "))
        y = float(input(f"Digite o valor de f(x_{i}): "))
        pontos_x.append(x)
        pontos_y.append(y)

    return pontos_x, pontos_y
```
Esta função solicita ao usuário que insira a quantidade de pontos e os valores 'x' e 'y' correspondentes para cada ponto. Os valores são convertidos para 'float' para garantir precisão decimal e armazenados em listas.

```python
def valor_final():
    pontos_x, pontos_y = solicitar_pontos()
    x_interpolar = float(input("Digite o valor de x para interpolação: "))
    resultado = calc_poli_lagrange(pontos_x, pontos_y, x_interpolar)
    print(f"O valor interpolado em x = {x_interpolar} é {resultado}")

if __name__ == "__valor_final__":
    valor_final()
```
A função 'main' finaliza o código, onde ela chama a função 'solicitar_pontos' para obter os pontos fornecidos pelo usuário, também solicita o valor de 'x' onde a interpolação deve ser calculada e, em seguida, calcula o valor interpolado usando a função 'calc_poli_lagrange'.


Para mais informações, este é o meu GitHub com os dados corretos:
[GitHub Nicolas Mello - Portfólio Calculo Numerico](https://github.com/nickapmello/portfolio).

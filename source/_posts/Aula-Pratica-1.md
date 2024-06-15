---
title: Aula Prática 1
date: 2024-05-29
---

### Introdução à Interpolação Linear

A interpolação linear é uma técnica matemática utilizada para estimar valores desconhecidos que se encontram dentro do intervalo de dois pontos conhecidos. Em muitas aplicações práticas, temos um conjunto de dados discretos e precisamos prever ou estimar valores entre esses pontos. A interpolação linear é a forma mais simples de interpolação, e envolve a construção de uma reta que conecta dois pontos dados.

### Objetivo do Código

O código desenvolvido para a primeira atividade prática tem como objetivo realizar a interpolação linear entre dois pontos fornecidos pelo usuário. Ele calcula a equação da reta que passa por esses pontos, encontrando os dois coeficientes angulares, a1 e a0, que definem essa reta. A equação da reta é então usada para prever valores intermediários entre os dois pontos.
Abaixo está o código completo seguido de uma explicação detalhada de suas funções:

```python
def coef_angular1(x0, y0, x1, y1):
    return (y1 - y0) / (x1 - x0)

def coef_angular0(a1, x0, y0):
    return y0 - a1 * x0

def pontos():
    print("Insira os valores dos pontos para realizar a interpolação linear.")
    
    x0 = float(input("Digite o valor de x0: "))
    y0 = float(input("Digite o valor de y0: "))
    
    x1 = float(input("Digite o valor de x1: "))
    y1 = float(input("Digite o valor de y1: "))
    
    return x0, y0, x1, y1

def main():
    x0, y0, x1, y1 = pontos()

    a1 = coef_angular1(x0, y0, x1, y1)
    a0 = coef_angular0(a1, x0, y0)

    print(f"Coeficiente a1 = {a1:.3f}")
    print(f"Coeficiente a0 = {a0:.3f}")
    print(f"P(x) = {a0:.3f} + {a1:.3f}x")

if __name__ == "__main__":
    main()

# Pontos específicos da aula para teste
# x0, y0 = 0.1, 1.221 ; x1, y1 = 0.6, 3.320
```

### Explicando o código desenvolvido
```python
def coef_angular1(x0, y0, x1, y1):
    return (y1 - y0) / (x1 - x0)
```
Esta função calcula o coeficiente angular a1, que é a inclinação da reta que conecta os dois pontos (x0,y0) e (x1,y1). A inclinação é dada pela razão entre a diferença nas coordenadas y e a diferença nas coordenadas x, sendo:  a1 = (y1-y0) / (x1-x0)

```python
def coef_angular0(a1, x0, y0):
    return y0 - a1 * x0
```
Esta função calcula o coeficiente linear a0, que é o ponto onde a reta intercepta o eixo y. Este coeficiente é calculado rearranjando a equação da reta y = a1 * x + a0 para resolver a0, sendo: a0 = y0 - a1 * x0

```python
def pontos():
    print("Insira os valores dos pontos para realizar a interpolação linear.")
    
    x0 = float(input("Digite o valor de x0: "))
    y0 = float(input("Digite o valor de y0: "))
    
    x1 = float(input("Digite o valor de x1: "))
    y1 = float(input("Digite o valor de y1: "))
    
    return x0, y0, x1, y1
```
Esta função solicita ao usuário que insira os valores dos dois pontos necessários para a interpolação linear. Os valores são lidos como entradas do usuário e convertidos para o tipo 'float' para garantir precisão decimal. A função retorna os valores dos pontos x0,y0 e x1,y1.

Após passar por todos esses processos, o código chama a função 'pontos' para obter os valores dos pontos fornecidos pelo usuário, calcula os coeficientes a1 e a0 usando as funções 'coef_angular1' e 'coef_angular0'. Por final, imprime os coeficientes e a equação da reta resultante no formato P(X) = a0 + a1 * x.


Para mais informações, este é o meu GitHub com os dados corretos:
[GitHub - Portfólio Calculo Numerico](https://github.com/nickapmello/portfolio).


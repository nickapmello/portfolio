---
title: Lista
date: 2024-06-15
---

## Introdução a Lista

Na seguinte lista de exercícios, foi proposta a ideia de utilizar os códigos que desenvolvemos em aula para apresentar a solução dos três seguintes exercícios de interpolação. Para cada exercício, deve ser utilizado os métodos de interpolação de Newton e Lagrange. Printando o código demostrando a resposta calculada.

## Exibição de códigos desenvolvidos
### Método de Newton (Ajustei para pedir quantidade e valor dos pontos)
```python
def calc(x, y):
    if len(y) == 1:
        return y[0]
    else:
        return (calc(x[1:], y[1:]) - calc(x[:-1], y[:-1])) / (x[-1] - x[0])

def polinomio(x, y):
    n = len(x)
    coeficientes = []
    for i in range(n):
        coeficientes.append(calc(x[:i + 1], y[:i + 1]))
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
    resultado = interpolacao(pontos_x, pontos_y, x_interpolar)
    print(f"O valor interpolado em x = {x_interpolar} é {resultado:.4f}")

if __name__ == "__valor_final__":
    valor_final()
```

### Método de Lagrange
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

### Exercício 1
![](/images/exercicio1.png)

Solução com método de Newton:
![](/images/print1-newton.png)

Solução com método de Lagrange:
![](/images/print1-lagrange.png)


### Exercício 2
![](/images/exercicio2.png)

Solução com método de Newton:
![](/images/print2-newton.png)

Solução com método de Lagrange:
![](/images/print2-lagrange.png)

### Exercício 3
![](/images/exercicio3.png)

Solução com método de Newton:
![](/images/print3-newton.png)

Solução com método de Lagrange:
![](/images/print3-lagrange.png)

### Conclusão

Os resultados para o exercício 1 são exatamente iguais. Para o exercício 2 são praticamente iguais, com uma pequena diferença decimal  de 1820.234375 para 1820.2344. Para o exercício 3 são também praticamente iguais, com uma pequena diferença decimal de  2.5096001157625 para 2.5096. Portanto, é correto dizer que com os testes realizados nessa atividade, ambos os métodos de Newton e Lagrange são eficazes para realizar a interpolação de polinômios, produzindo resultados consistentes.


Para mais informações, este é o meu GitHub com os dados corretos:
[GitHub Nicolas Mello - Portfólio Calculo Numerico](https://github.com/nickapmello/portfolio).

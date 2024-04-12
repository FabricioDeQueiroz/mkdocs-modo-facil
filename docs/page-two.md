# Teste

Página dois, tal tal tal.

## Exemplo de código

``` py title="Bubble Sort - Python3" linenums="1"
def bubblesort(elements):
    for n in range(len(elements)-1, 0, -1):
        swapped = False
        for i in range(n):
            if elements[i] > elements[i + 1]:
                swapped = True
                elements[i], elements[i + 1] = elements[i + 1], elements[i]
        if not swapped:
            return
```
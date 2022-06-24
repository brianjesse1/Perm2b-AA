# Perm2b-AA
Perm2b-Algebra Abstracta

**Integrantes**

-Marcelo Torres Acuña

-Jhon Berly Taype Alccaccahua 

-Brian Bermudez Navarro

------------

#### **Modo de ejecucion:

Para la ejecucion del programa es necesario ejecutar el archivo:

```
RSA.py
```

#### **1) Implementar RSA KEY GENERATOR**

#### - Funcionamiento:
a. Recibe como parámetro un número "K" de bits.
b. Genera dos números primos (p,q) que ocupan la mitad de "K" bits cada uno.
c. Multiplica los números (n=p*q)
d. Halla phiN (phiN = phi(n))
e. phi(n): Halla la cantidad de números coprimos menores a "n" con respecto a "n"
f. Genera un número "e" tal que sea coprimo con phiN
g. Halla la inversa de "e" (d = inversa(e))
h. (e*d) es congruente con 1 en módulo phiN
i. Retorna los valores "e", "d" y "n"

```
def RSA(k):
    a=Random_primos(int(k/2))
    p=a[0]
    q=a[1]
    n=pq
    phi_n=(p-1)(q-1)
    while (True):
        e=random.randint(2,n-1)
        if(euclides(e,phi_n )==1):
            break
    d=inverso(e,phi_n)
    return e,d,n
```

#### *Output:*

#### **2) Crear un sistema RSA-64 (de k = 64 bits), y mostrar los valores para e, d y n. Generar una tabla con tres columnas m, c = P(m) y m' = S(c) - en teoría se cumple m' = m. Para las filas usar 10 valores números aleatorios distintos para m.**

#### *Output:*

# Perm2b-AA
#### ** Perm2b-Algebra Abstracta

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

#### Funcionamiento:

- La funcion recibe como parametro la variable "k", el cual contiene el numero de bits.

- Seguidamente se generan los numeros primos "p" y "q", los cuales tienen la mitad de "k" bits cada uno correspondientemente 

- Se multiplica los números "p" y "q" 

- Se procede a calcular phin_n = (p-1)(q-1)

- Calculamos los números coprimos menores a "n"

- Generamos un número "e" tal que sea coprimo con phi_n

- Tenemos que la multiplicacion de "e" y "d" es congruente con 1 en módulo phi_n

- Calculamos la inversa de "e" que vendria a estar dada por "d" (d = inverso(e,phin_n))

- Finalmente la funcion retorna los valores "e", "d" y "n"

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

- El sistema RSA-64 procede a cifrar un "mensaje" utilizando las llaves "e" y "n"
- El sistema RSA-64 procede a decifrar un "mensaje" utilizando las llaves "d" y "n"

#### *Output:*

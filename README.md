# Perm2b-AA
####  Perm2b-Algebra Abstracta

**Integrantes**

-Marcelo Torres Acuña

-Jhon Berly Taype Alccaccahua 

-Brian Bermudez Navarro

------------

#### Modo de ejecucion:

Para la ejecucion del programa es necesario ejecutar el archivo:

```
RSA.py
```

#### **1) Implementar RSA KEY GENERATOR**

#### Funcionamiento:

- Random_primos es una funcion anteriormente estudiada de Miller Rabin la cual nos genera si un numero es primo retornando true o false

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
    p=Random_primos(int(k/2))
    while (True):
        q=Random_primos(int(k/2))
        if (p!=q):
            break
    n=p*q
    phi_n=(p-1)*(q-1)
    print(p)
    print(q)
    while (True):
        e=random.randint(2,n-1)
        if(euclides(e,phi_n )==1):
            break    
    d=inverso(e,phi_n)    
    return e,d,n
```

#### *Output:*

```
e: 12885139048985579
d: 7791578994143519
n: 12975339517522301
```



#### **2) Crear un sistema RSA-64 (de k = 64 bits), y mostrar los valores para e, d y n. Generar una tabla con tres columnas m, c = P(m) y m' = S(c) - en teoría se cumple m' = m. Para las filas usar 10 valores números aleatorios distintos para m.**

- El sistema RSA-64 procede a cifrar un "mensaje" utilizando las llaves "e" y "n"
- El sistema RSA-64 procede a decifrar un "mensaje" utilizando las llaves "d" y "n"

```
e,d,n=RSA(54)
print("e:",e)
print("d:",d)
print("n:",n)
print()
lista=[]
print("-"*64)
print("|{:^20}|{:^20}|{:^20}|".format("m","c=m^e mod n","m'=c^d mod n"))
print("-"*64)
for i in range(10):
    m = random.randint(2, n-1)
    while(True):
        if (m not in lista):
            lista.append(m)
            c = EXPMOD(m, e, n)
            m_i = EXPMOD(c, d, n)
            print("|{:^20}|{:^20}|{:^20}|".format(m,c,m_i))
            break
        else:
            m = random.randint(2, n-1)
print("-"*64)
```

#### *Output:*
```
e: 12885139048985579
d: 7791578994143519
n: 12975339517522301
----------------------------------------------------------------
|         m          |    c=m^e mod n     |    m'=c^d mod n    |
----------------------------------------------------------------
|  400171200140434   | 10075583705958564  |  8741298638189657  |
|  1148856302793491  |  4251221955982454  | 11192274515566936  |
|  8617309351195662  |  5921505795818399  |  1660312198066354  |
| 11761869039148567  | 11430046776943979  |  4083990286718607  |
|  1943925624120329  |  4276368215749597  |  8069418285491343  |
|  6191593443077085  |  4035570721462275  |  316384485256122   |
|  372449417360434   |  8687683673319042  |  431612880641510   |
|  4703216317472751  |  5657682954565069  |  4712015067178620  |
|  2764817639141822  | 11279171918376808  | 12919186986766495  |
|  108243894672831   |  5463145782962134  | 10394926153502872  |
----------------------------------------------------------------
```

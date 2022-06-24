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
----------------------------------------------------------------
|         m          |    c=m^e mod n     |    m'=c^d mod n    |
----------------------------------------------------------------
|  9434277636400317  |  1852204384287201  |  9434277636400317  |
|  2091517729613679  |  3922931521191626  |  2091517729613679  |
| 11711897390972490  |  5140646541321376  | 11711897390972490  |
|  3799626446501410  |  1499383592540195  |  3799626446501410  |
|  523594924423977   |  3820728109464182  |  523594924423977   |
|  5528459518900054  |  3201761294804551  |  5528459518900054  |
|  6261621457046937  | 11981299482745609  |  6261621457046937  |
|  8191958048924347  |  4268832510776538  |  8191958048924347  |
| 10245312570953497  |  1994183448689615  | 10245312570953497  |
|  4996108318984723  | 11955745065604279  |  4996108318984723  |
----------------------------------------------------------------
```

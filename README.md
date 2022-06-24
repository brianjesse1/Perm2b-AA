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

- Seguidamente se generan los numeros primos "p" y "q", los cuales tienen la mitad de "k" bits cada uno correspondientemente. Utilizando la funcion Random_primos que emplea Miller Rabin la cual nos genera si un numero es primo o no lo es. Seguidamente se verifica que "p" y "q" no se repitan. 

- Se multiplica los números "p" y "q" 

- Se procede a calcular phin_n = (p-1)(q-1)

- Para el valor de "e" generamos numeros random, que con el algoritmo de Euclides verificamos si "e" y phi_n son coprimos

- Calculamos la inversa donde la funcion "inversa" emplea tanto el algoritmo de Euclidos como el Extendido de euclides para hallar el valor  de "d" (d =
= inverso(e,phin_n))

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
    while (True):
        e=random.randint(2,n-1)
        if(euclides(e,phi_n )==1):
            break    
    d=inverso(e,phi_n)    
    return e,d,n
```

#### *Output:*

```
e: 3330149734882679
d: 1761223733132807
n: 9446179903526957
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
e: 3330149734882679
d: 1761223733132807
n: 9446179903526957

----------------------------------------------------------------
|         m          |    c=m^e mod n     |    m'=c^d mod n    |
----------------------------------------------------------------
|  1060038641509762  |  262783245064137   |  1060038641509762  |
|  6121072337179987  |  6322011108007899  |  6121072337179987  |
|  6548199241649107  |  9337246989195229  |  6548199241649107  |
|  8857689963672212  |  5133177868739961  |  8857689963672212  |
|  4824380607017515  |  1235649872655868  |  4824380607017515  |
|  6144383801539162  |  3746467773999599  |  6144383801539162  |
|  5883645367686385  |  4271565591895572  |  5883645367686385  |
|  6488778730916268  |  7741079461466424  |  6488778730916268  |
|  6287893357660114  |  4914166874331105  |  6287893357660114  |
|  3234594523718373  |  1843940599798013  |  3234594523718373  |
----------------------------------------------------------------
```

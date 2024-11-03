+++
title = 'Shortening Code in C++'
description = "Tips para comenzar a acortar codigo como todo un chad en programacion competitiva"
date = 2024-11-03
categories = [
    "Programming",
    "C++"
]
tags = [
    "competitive Programming",
    "Shortening Code",
]
image = "wallpaper.png"
+++


El código corto es ideal en la programación competitiva, ya que los programas deben escribirlos lo más rápido posible. Debido a esto, la programación competitiva a menudo define nombres más cortos para tipos de datos y otras partes del código. A continuacion se muestra como usar estos tipos de datos,


## Type names

Usando el comando `typedef`, es posible dar un nombre más corto a un tipo de dato; por ejemplo, el nombre _long long_ es largo, así que podemos definir un nombre más corto, como por ejemplo:

```C++
typedef long long ll
```

Despues el codigo:
```C++
ll a = 123456789;
ll b = 987654321;

std::cout << a * b << "\n";
```

El comando `typedef` también se puede usar con tipos más complejos; por ejemplo, el siguiente código da el nombre "_vi_" para un vector de enteros y el nombre "_pi_" para un par que contiene dos enteros.

```C++
typedef vector <int> vi;
typedef pair <int, int> pi;
```

## Macros

Otra forma de acortar el código es definir **macros**. Una _macro_ significa que ciertas cadenas en el código se cambiarán antes de la compilación. En C++, las _macros_ se definen usando la palabra clave `#define`.

Por ejemplo, podemos definir las siguientes macros.
```C++
#define F first
#define S second
#define PB push_back
#define MP make_pair
```

Despues de esto, el codigo:
```C++
array.push_back(make_pair(y1, x1));
array.push_back(make_pair(y2, x2));

int d = array[i].first + array[i].second;
```

Puede abreviarse como sigue:
```C++
array.PB(MP(y1, x1));
array.PB(MP(y2, x2));

int d = array[i].F + array[i].S;
```

### Macros con parametros

Una macro también puede tener parámetros que permiten acortar bucles y otras estructuras, por ejemplo, podemos definir la siguiente macro:

```C++
#define REP(i, a, b) for (int i = a; i < b; i++)
```

Despues de esto, el codigo:
```C++
for (int i=0; i<b; i++) {
	search(10);
}
```

Puede abreviarse como sigue:
```C++
REP(i, 0, n) {
	search(10);
}
```

### Errores mientras hacemos uso de los macros

A veces las macros causan errores que pueden ser difíciles de detectar, por ejemplo, considere la siguiente macro que calcula el cuadrado de un número 

```C++
#define SQ(a) a * a
```
Esta maro no siempre puede funcionar como se espera, como por ejemplo en este codigo:
```C++
std::cout << SQ(3+3) << "\n";
```

Corresponde a esta operacion:

```C++
std::cout << SQ(3 + 3 * 3 + 3) << "\n"; // 15
```

Una mejor version de la macro is como la siguiente:

```C++
#define SQ(a) (a)*(a)
```

Ahora el codigo:

```C++
std::cout << SQ(3 + 3) << "\n";
```

Corresponde a esta operacion:

```C++
std::cout << (3+3) * (3+3) << "\n"; // 36
```


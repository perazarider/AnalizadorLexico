# AnalizadorLexico
Objetivo del Software
Este software es un analizador léxico y sintáctico que implementa un lenguaje de programación básico. Su propósito es:
Analizar léxicamente (tokenizar) el código fuente, identificando los componentes básicos como números, operadores, identificadores, etc.
Analizar sintácticamente la estructura del código, verificando que siga las reglas gramaticales definidas.
Construir un árbol de sintaxis abstracta (AST) que representa la estructura lógica del código.
Es una herramienta fundamental para:
Compiladores e intérpretes de lenguajes
Procesamiento de lenguajes específicos de dominio (DSL)
Validación de sintaxis en editores de código
Aprendizaje de conceptos de compiladores

Instrucciones para Ejecutar el Programa
Requisitos previos:
Python 3.x instalado
Biblioteca PLY instalada (ejecuta pip install ply)
Pasos para ejecutar:
# 1. Guarda el código en un archivo (ej. analizador.py)
# 2. Ejecuta desde la terminal:
python analizador.py
Uso del programa:
El programa iniciará un prompt interactivo (>)
Ingresa expresiones válidas (ver ejemplos abajo)
Escribe "salir" para terminar
Para cada entrada mostrará:
Los tokens identificados
El árbol de sintaxis abstracta generado

Ejemplos de Entrada y Salida
Ejemplo 1: Expresión aritmética
Entrada:
3 + 4 * (5 - 2);
Salida:
Tokens:
LexToken(NUMBER,3.0,1,0)
LexToken(PLUS,'+',1,2)
LexToken(NUMBER,4.0,1,4)
LexToken(TIMES,'*',1,6)
LexToken(LPAREN,'(',1,8)
LexToken(NUMBER,5.0,1,9)
LexToken(MINUS,'-',1,11)
LexToken(NUMBER,2.0,1,13)
LexToken(RPAREN,')',1,14)
LexToken(SEMICOLON,';',1,15)
Árbol de sintaxis abstracta:
('program', ('statement', ('binop', '+', ('number', 3.0), ('binop', '*', ('number', 4.0), ('group', ('binop', '-', ('number', 5.0), ('number', 2.0))))))
Ejemplo 2: Asignación de variable
Entrada:
x = 10 + 5;
Salida:
Tokens:
LexToken(ID,'x',1,0)
LexToken(EQUALS,'=',1,2)
LexToken(NUMBER,10.0,1,4)
LexToken(PLUS,'+',1,7)
LexToken(NUMBER,5.0,1,9)
LexToken(SEMICOLON,';',1,10)
Árbol de sintaxis abstracta:
('program', ('statement', ('assignment', 'x', ('binop', '+', ('number', 10.0), ('number', 5.0)))))
Ejemplo 3: Estructura if-else
Entrada:
if (x > 0) { y = x * 2; } else { y = 0; }
Salida:
Tokens:
LexToken(IF,'if',1,0)
LexToken(LPAREN,'(',1,3)
LexToken(ID,'x',1,4)
LexToken(GT,'>',1,6)
LexToken(NUMBER,0.0,1,8)
LexToken(RPAREN,')',1,9)
LexToken(LBRACE,'{',1,11)
LexToken(ID,'y',1,13)
LexToken(EQUALS,'=',1,15)
LexToken(ID,'x',1,17)
LexToken(TIMES,'*',1,19)
LexToken(NUMBER,2.0,1,21)
LexToken(SEMICOLON,';',1,22)
LexToken(RBRACE,'}',1,24)
LexToken(ELSE,'else',1,26)
LexToken(LBRACE,'{',1,31)
LexToken(ID,'y',1,33)
LexToken(EQUALS,'=',1,35)
LexToken(NUMBER,0.0,1,37)
LexToken(SEMICOLON,';',1,38)
LexToken(RBRACE,'}',1,40)
Árbol de sintaxis abstracta:
('program', ('statement', ('if-else', ('binop', '>', ('id', 'x'), ('number', 0.0), ('statements', ('statement', ('assignment', 'y', ('binop', '*', ('id', 'x'), ('number', 2.0)))), ('statements', ('statement', ('assignment', 'y', ('number', 0.0))))))
Ejemplo 4: Bucle while
Entrada:
while (i < 10) { i = i + 1; }
Salida:
Tokens:
LexToken(WHILE,'while',1,0)
LexToken(LPAREN,'(',1,6)
LexToken(ID,'i',1,7)
LexToken(LT,'<',1,9)
LexToken(NUMBER,10.0,1,11)
LexToken(RPAREN,')',1,13)
LexToken(LBRACE,'{',1,15)
LexToken(ID,'i',1,17)
LexToken(EQUALS,'=',1,19)
LexToken(ID,'i',1,21)
LexToken(PLUS,'+',1,23)
LexToken(NUMBER,1.0,1,25)
LexToken(SEMICOLON,';',1,26)
LexToken(RBRACE,'}',1,28)
Árbol de sintaxis abstracta:
('program', ('statement', ('while', ('binop', '<', ('id', 'i'), ('number', 10.0), ('statements', ('statement', ('assignment', 'i', ('binop', '+', ('id', 'i'), ('number', 1.0)))))))
Notas Importantes
El lenguaje reconoce:
Operadores aritméticos: + - * /
Comparadores: == != < > <= >=
Estructuras de control: if-else, while
Asignación de variables con =
Bloques de código entre { }
Cada declaración debe terminar con ;
El programa mostrará errores claros cuando:
Haya tokens no reconocidos
La sintaxis no coincida con la gramática definida
Falten elementos requeridos (como paréntesis o llaves)

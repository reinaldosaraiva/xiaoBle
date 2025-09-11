# Debug do Mapeamento - Teclado Chipper

## BASE Layer (DEF) - Físico
```
Lado Esquerdo:                          Lado Direito:
[0] ESC  [1] Q  [2] W  [3] E  [4] R  [5] T  |  [6] Y  [7] U  [8] I  [9] O  [10] P  [11] DEL
[0] TAB  [1] A  [2] S  [3] D  [4] F  [5] G  |  [6] H  [7] J  [8] K  [9] L  [10] ;  [11] Enter
[0] Bspc [1] Z  [2] X  [3] C  [4] V  [5] B  |  [6] N  [7] M  [8] ,  [9] .  [10] ?  [11] RAlt
                    [3]Shift [4]GUI [5]Space |  [6]Space [7]Bspc [8]Multi
```

## NUM Layer - Mapeamento no código (linha 117-121)
```
Linha 117 (row 0):
[0] ___  [1] "?  [2] <  [3] $  [4] >  [5] \  |  [6] !=  [7] +7  [8] -8  [9] _9  [10] Cmd+P  [11] ___

Linha 119 (row 1):  
[0] ___  [1] @  [2] (  [3] &  [4] )  [5] `  |  [6] .#  [7] *4  [8] /5  [9] \6  [10] {  [11] ___

Linha 121 (row 2):
[0] ___  [1] ~  [2] [  [3] ^  [4] ]  [5] ___  |  [6] %0  [7] |1  [8] &2  [9] #3  [10] }  [11] ___
```

## PROBLEMA ENCONTRADO!

Quando você pressiona SPACE direito + ; (posição física [10] na linha 1):
- BASE layer: posição [10] = semicolon (;)
- NUM layer linha 119: posição [10] = LBRC ({)

MAS se aparecer &, está pegando:
- NUM layer linha 119: posição [3] = & (AMPS)

## ISSO SIGNIFICA:
O teclado está interpretando a tecla ; como posição [3] ao invés de [10]!

## Possível causa: 
- Transform matrix invertida no lado direito
- Ou teclado de 5 colunas ao invés de 6

Vamos verificar se está usando five_column_transform!
# Layout Guide - Teclado Chipper (36 keys)

Este guia visual mostra todas as camadas do teclado para facilitar o aprendizado e memorização.

## 🎹 Camada Base (DEF) - Layer 0

```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ ESC │  Q  │  W  │  E  │  R  │  T  │   │  Y  │  U  │  I  │  O  │  P  │ DEL │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│ TAB │  A  │  S  │  D  │  F  │  G  │   │  H  │  J  │  K  │  L  │  ;  │Enter│
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│Ctrl │  Z  │  X  │  C  │  V  │  B  │   │  N  │  M  │  ,  │  .  │  ?  │RAlt │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                  │Shift│ GUI │Space│   │Space│Bspc │Enter│
                  └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

### Teclas Especiais Layer Base:
- **Ctrl (canto inferior esquerdo)**: TAP = CONTROL | HOLD = COMMAND/GUI
- **Space (esquerdo)**: Hold = NAV layer
- **Space (direito)**: Hold = NUM layer
- **P**: Hold = FN layer
- **Z**: Hold = FN layer
- **I**: Hold = | (pipe)
- **H**: Hold = # (hash)
- **A**: Hold = Cmd+A
- **F**: Hold = Cmd+F
- **X**: Hold = Cmd+X
- **C**: Hold = Cmd+C
- **V**: Hold = Cmd+V
- **,**: Hold = ; (semicolon)
- **.**: Hold = : (colon)
- **?**: Hold = ' (quote)

## 🧭 Camada Navegação (NAV) - Layer 1
**Ativação**: Hold SPACE (esquerdo)

```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │ ESC │Sh+CT│  ↑  │ C+T │Cmd+T│   │  /  │  _  │  |  │     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │ TAB │  ←  │  ↓  │  →  │     │   │  #  │  $  │  ↓  │  →  │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │   │  &  │     │     │     │     │     │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                  │     │     │ ▓▓▓ │   │     │     │     │
                  └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

### Funções NAV:
- **Setas**: Navegação básica (↑↓←→)
- **Tab navegação**: Sh+Ctrl+Tab, Ctrl+Tab, Cmd+Tab
- **Símbolos**: /, _, |, #, $, &

## 🎛️ Camada Funções (FN) - Layer 2
**Ativação**: Hold P ou Hold Z

```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │     │     │     │     │     │   │     │ F7  │ F8  │ F9  │ F12 │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │   │     │ F4  │ F5  │ F6  │ F11 │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │     │   │     │ F1  │ F2  │ F3  │ F10 │     │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                  │     │     │     │   │     │     │     │
                  └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

### Funções FN:
- **Teclas F**: F1-F12 organizadas em 3 colunas
- **Layout**: F7-F9-F12, F4-F6-F11, F1-F3-F10

## 🔢 Camada Números (NUM) - Layer 3
**Ativação**: Hold SPACE (direito)

```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │ "?  │  <  │  $  │  >  │  \  │   │ !=  │ +7  │ -8  │ _9  │Cmd+P│     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │  @  │  (  │  {  │  )  │  `  │   │ .#  │ *4  │ /5  │ \6  │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │  ~  │  [  │  }  │  ]  │     │   │ %0  │ |1  │ &2  │ #3  │     │     │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                  │     │     │     │   │     │ DEL │     │
                  └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

### Funções NUM:
- **Números**: 0-9 com símbolos em hold
- **Símbolos matemáticos**: +, -, *, /, =, %
- **Parênteses**: ( ), [ ], < >
- **Chaves**: { } (NOVO! - SPACE direito + L/;)
- **Símbolos especiais**: @, &, ^, ~, `, \, |, #

## ⚙️ Camada Sistema (SYS) - Layer 4
**Ativação**: NAV + FN (SPACE esquerdo + P/Z simultaneamente)

```
┌─────┬─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┬─────┐
│     │ BT1 │ BT2 │ BT3 │ BT4 │CLEAR│   │CLEAR│ BT1 │     │     │     │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │  A  │     │     │BOOT │     │   │BOOT │     │     │     │  A  │     │
├─────┼─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │     │RESET│   │RESET│     │     │     │     │     │
└─────┴─────┴─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┴─────┴─────┘
                  │     │     │     │   │     │     │     │
                  └─────┴─────┴─────┘   └─────┴─────┴─────┘
```

### Funções SYS:
- **Bluetooth**: BT1-4 (conectar dispositivos), CLEAR (limpar conexões)
- **Sistema**: BOOT (bootloader), RESET (reiniciar)
- **Acesso**: Apenas via combinação NAV+FN

## 🎯 Combo Especial

### Combo "nayeon":
- **Posições**: 6 + 30 (Y + thumb direito)
- **Resultado**: Digita "nayeon" + Enter
- **Timeout**: 60ms

## 📝 Dicas de Uso

### Para se habituar:
1. **Comece com a layer base** - pratique digitação normal
2. **Adicione NAV** - use SPACE esquerdo para navegação
3. **Inclua NUM** - use SPACE direito para números
4. **Domine FN** - teclas F com P ou Z
5. **SYS só quando necessário** - Bluetooth e updates

### Teclas-chave para lembrar:
- **Canto inferior esquerdo** = CONTROL (tap) / COMMAND (hold)
- **SPACE esquerdo** = Navegação
- **SPACE direito** = Números
- **P ou Z** = Funções F
- **SPACE+P/Z** = Sistema/Bluetooth
- **Backspace** = Thumb direito (removido do canto esquerdo)

### Sequências importantes:
- **Bootloader**: SPACE esquerdo + Z + F
- **Bluetooth 1**: SPACE esquerdo + Z + Q
- **Reset**: SPACE esquerdo + Z + B
# Guia de Bootloader e Bluetooth - Teclado Corne (Chipper)

## 📋 Resumo

Este guia documenta como ativar o modo bootloader para atualização de firmware e como usar as funções Bluetooth no teclado Corne customizado (shield "Chipper") com Seeeduino XIAO BLE.

## 🔧 Modo Bootloader (Pendrive)

### Como ativar o bootloader para upload de firmware:

#### Sequência de teclas:
1. **Segure SPACE** (polegar esquerdo) → ativa NAV layer
2. **Segure Z** (mindinho esquerdo) → ativa FN layer  
3. **NAV + FN** = SYS layer ativo automaticamente
4. **Com ambas seguradas, aperte F** → ativa `&bootloader`

#### Layout visual:
```
┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
│  Q  │  W  │  E  │  R  │  T  │   │  Y  │  U  │  I  │  O  │  P  │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│  A  │  S  │  D  │  F* │  G  │   │  H* │  J  │  K  │  L  │Enter│ 
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│  Z* │  X  │  C  │  V  │  B  │   │  N  │  M  │  ,  │  .  │  ?  │
└─────┴─────┴─────┼─────┼─────┤   ├─────┼─────┼─────┴─────┴─────┘
                  │Shift│Space*│  │Space│Bspc │
                  └─────┴─────┘   └─────┴─────┘
```

**Legenda:**
- `Space*` = NAV layer (segurar)
- `Z*` = FN layer (segurar)  
- `F*` ou `H*` = bootloader (apertar com as outras seguradas)

#### Resultado:
- Teclado desconecta temporariamente
- Reconecta como pendrive no sistema operacional
- Arrastar arquivos `.uf2` para cada lado do teclado
- Reinicia automaticamente após upload

### Compatibilidade:
- ✅ macOS
- ✅ Windows 11
- ✅ Linux

## 📱 Controles Bluetooth

### Acessar controles Bluetooth:
Mesma sequência: **SPACE + Z** (SYS layer ativo)

### Layout SYS layer - Funções Bluetooth:
```
┌─────┬─────┬─────┬─────┬─────┐   ┌─────┬─────┬─────┬─────┬─────┐
│ BT1 │ BT2 │ BT3 │ BT4 │CLEAR│   │CLEAR│ BT1 │     │     │     │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│  A  │     │     │BOOT │     │   │BOOT │     │     │     │  A  │
├─────┼─────┼─────┼─────┼─────┤   ├─────┼─────┼─────┼─────┼─────┤
│     │     │     │     │RESET│   │RESET│     │     │     │     │
└─────┴─────┴─────┼─────┼─────┤   ├─────┼─────┼─────┴─────┴─────┘
                  │     │     │   │     │     │
                  └─────┴─────┘   └─────┴─────┘
```

### Comandos Bluetooth:

#### Conectar dispositivos:
- **SPACE + Z + Q** = Dispositivo Bluetooth 1
- **SPACE + Z + W** = Dispositivo Bluetooth 2  
- **SPACE + Z + E** = Dispositivo Bluetooth 3
- **SPACE + Z + R** = Dispositivo Bluetooth 4

#### Limpar conexões:
- **SPACE + Z + T** = Limpar todas as conexões Bluetooth
- **SPACE + Z + Y** = Limpar todas as conexões Bluetooth (duplicado)

### Capacidade:
- Suporta até **4 dispositivos** pareados simultaneamente
- Útil para alternar entre Mac, iPhone, iPad, Windows, etc.
- Memória persistente das conexões

## ⚙️ Configuração Técnica

### Arquivo keymap:
- **Local**: `xiaoBle/config/boards/shields/chipper/chipper.keymap`
- **Layer SYS**: Layer 4 (ativado por conditional layer NAV + FN)
- **Linha 138**: `&bootloader` nas posições F e H
- **Linha 141**: `&sys_reset` nas posições B e N
- **Linhas 136**: Controles Bluetooth na fileira superior

### Conditional layer:
```c
conditional_layers {
    compatible = "zmk,conditional-layers";
    tri_layer {
        if-layers = <1 2>;  // NAV + FN
        then-layer = <4>;   // = SYS
    };
};
```

### Definições:
```c
#define NAV 1    // Navigation layer
#define FN 2     // Function layer  
#define SYS 4    // System layer (Bluetooth + Reset)
```

## 🔄 Processo de Atualização de Firmware

1. **Modificar keymap** no repositório GitHub
2. **Commit e push** → GitHub Actions compila automaticamente
3. **Download** dos arquivos `.uf2` gerados
4. **Ativar bootloader** com sequência SPACE + Z + F
5. **Arrastar arquivos** para cada lado do teclado:
   - `chipper_left-*.uf2` → lado esquerdo
   - `chipper_right-*.uf2` → lado direito
6. **Reinicialização automática** com novo firmware

## ⚠️ Observações Importantes

- Fazer **um lado por vez** durante upload de firmware
- Usar apenas firmware **gerado pelo próprio repositório**
- **Não usar** firmwares "oficiais" da internet (incompatíveis)
- Backup method: **duplo clique no botão RST** físico do microcontrolador

## 📚 Referências

- **Hardware**: Seeeduino XIAO BLE (nRF52840)
- **Firmware**: ZMK (Zephyr Mechanical Keyboard)
- **Shield**: Custom "Chipper" (36-key split)
- **Layout**: 3x6 + 3 thumb keys por lado
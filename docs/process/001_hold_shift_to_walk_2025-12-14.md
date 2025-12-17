# Hold Shift to Walk Feature

**Data:** 2025-12-14
**Projeto:** TazUO (ClassicUO fork)

## Resumo

Implementada funcionalidade "Hold Shift to Walk" que permite ao jogador forcar o personagem a andar (walk) ao invés de correr segurando a tecla Shift.

## Comportamento

| Shift | Comportamento |
|-------|---------------|
| Solto | Normal (corre se distancia > 190px ou Always Run ativo) |
| Pressionado | Forca andar (walk) sempre |

## Arquivos Modificados

### 1. Profile.cs
- **Caminho:** `src/ClassicUO.Client/Configuration/Profile.cs`
- **Mudanca:** Adicionada propriedade `HoldShiftToWalk` (bool)

### 2. GameSceneInputHandler.cs
- **Caminho:** `src/ClassicUO.Client/Game/Scenes/GameSceneInputHandler.cs`
- **Mudanca:** Adicionada verificacao de Shift no movimento por mouse

### 3. GameScene.cs
- **Caminho:** `src/ClassicUO.Client/Game/Scenes/GameScene.cs`
- **Mudanca:** Adicionada verificacao de Shift no movimento por teclado

### 4. PlayerMobile.cs
- **Caminho:** `src/ClassicUO.Client/Game/GameObjects/PlayerMobile.cs`
- **Mudanca:** Adicionada verificacao de Shift no metodo Walk como fallback
- **Import adicionado:** `using ClassicUO.Input;`

### 5. ModernOptionsGump.cs
- **Caminho:** `src/ClassicUO.Client/Game/UI/Gumps/ModernOptionsGump.cs`
- **Mudanca:** Adicionado checkbox "Hold Shift to Walk" nas opcoes

## Configuracao

A opcao aparece nas configuracoes do cliente, abaixo de "Always Run" e "Run Unless Hidden".
- Padrao: Desabilitado
- Quando habilitado: Segurar Shift forca o personagem a andar

## Notas Tecnicas

- A funcionalidade respeita as restricoes existentes (stamina baixa, hidden, CantRun)
- Funciona tanto para movimento por mouse quanto por teclado
- Compativel com a opcao "Always Run" - Shift sobrescreve para andar

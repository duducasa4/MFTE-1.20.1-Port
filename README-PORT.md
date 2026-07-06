# ISS: Magic From The East — Port 1.21.1 (NeoForge) → 1.20.1 (Forge)

Port não-oficial feito a partir do source 1.21.x. Alvos:
- Minecraft 1.20.1 + Forge 47.3.22
- Iron's Spells 'n Spellbooks 1.20.1-3.4.0.9
- GeckoLib 4.7.1.1 (1.20.1), Curios 5.x, player-animator 1.0.2-rc1

## Como compilar
1. Instale um JDK 17 (Temurin recomendado).
2. Na raiz do projeto: `gradlew build` (Windows) ou `./gradlew build` (Linux/macOS).
   - Primeira execução baixa Forge/mappings/dependências (demora).
3. O jar sai em `build/libs/iss_magicfromtheeast-1.1.5-1.20.1-port.jar`.
4. Para testar no IDE: `gradlew genIntellijRuns` ou `genEclipseRuns` e rode o client.

Se a dependência `io.redspace:irons_spellbooks:1.20.1-3.4.0.9` não resolver no maven do Iron,
troque no build.gradle pela linha comentada do CurseMaven (pegue o fileId da versão 1.20.1
mais recente na página de arquivos do mod no CurseForge).

## O que esperar
O port foi feito manualmente contra a API do ISS 1.20.1 e do Forge 1.20.1, mas NÃO foi
compilado nem testado em jogo (feito em ambiente sem acesso aos mavens). É esperado que a
primeira compilação aponte um punhado de erros pontuais — em geral fáceis de corrigir
(assinatura ligeiramente diferente, import faltando). Os pontos de maior risco estão
marcados no código com `// TODO PORT 1.20.1:` (59 arquivos têm marcações).

## Cortes conhecidos (recursos 1.21 sem equivalente na 1.20.1)
- Corações customizados (jade/soul): reimplementados com overlay próprio (MFTEHeartOverlayHandler,
  padrão Overflowing Bars) — o overlay só assume a barra de vida enquanto Reversal Healing ou
  Soulburn estiver ativo; fora isso o vanilla/outros mods de HUD renderizam normalmente.
- Encantamentos viraram classes Java clássicas (na 1.21 eram data-driven). Lógica preservada.
- Data components viraram NBT (MFTEDataComponentRegistries é um utilitário NBT agora).
- SummonManager (1.21) → padrão SummonTimer/OwnerHelper do ISS 1.20.1.
- Atributos 1.20.5+ (SCALE, SNEAKING_SPEED, SAFE_FALL_DISTANCE, ENTITY_INTERACTION_RANGE):
  emulados quando possível (ForgeMod.*) ou cortados com TODO.
- Receitas: alguns materiais 1.21-only substituídos por análogos do ISS 1.20.1
  (bloody_vellum→hogskin, divine_soulshard→divine_pearl, mithril_weave→magic_cloth,
  breeze_rod→blaze_rod). Recipes de alchemist cauldron cortadas (API diferente na 1.20.1).
- Loot de trial chambers mantido porém inerte (estrutura não existe na 1.20.1).

## Créditos
Mod original: WarPhan (e contribuidores). Iron's Spells 'n Spellbooks: Iron431 e Lab3.
Licença original: All Rights Reserved — este port é para uso pessoal; não distribua sem
permissão do autor.

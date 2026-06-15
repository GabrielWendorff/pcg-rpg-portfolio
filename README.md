# 🐉 Análise de Geração Procedural em Sistemas Interativos
### Uma Proposta de RPG 2D com Coerência Semântica

> **Portfólio PAC VII — 2026/1**  
> Gabriel Wendorff | Centro Universitário Católica de Santa Catarina  
> gabriel.wendorff@catolicasc.edu.br

---

## 🎬 Pitch

[![Assista ao Pitch no YouTube](https://img.shields.io/badge/YouTube-Assistir%20ao%20Pitch-red?style=for-the-badge&logo=youtube)](SEU_LINK_AQUI)

> ⏱️ Duração: ~4 minutos

---

## 📄 Resumo

A **Geração Procedural de Conteúdo (PCG)** é uma técnica consolidada no desenvolvimento de jogos digitais, permitindo a criação automática de cenários, fases e personagens. Entretanto, os trabalhos existentes apresentam um trade-off recorrente: jogos comerciais privilegiam **escala** em detrimento da **coerência**, enquanto abordagens acadêmicas alcançam qualidade ao custo do **desempenho em tempo real**.

Este trabalho analisa três artigos científicos de referência (Hendrikx, Togelius e Shaker) e três jogos comerciais (Minecraft, No Man's Sky e Spelunky), identificando lacunas relacionadas à coerência semântica do conteúdo gerado.

A partir dessa análise, propõe-se um **RPG 2D inspirado em Pokémon Emerald**, com geração procedural de criaturas baseada em **atributos correlacionados**.

---

## 🌍 Contexto

PCG é usada em jogos como:

| Jogo | Técnica | Limitação |
|---|---|---|
| **Minecraft** | Ruído de Perlin + chunks | Geração puramente estocástica |
| **No Man's Sky** | 18 quintilhões de planetas | Criaturas com combinações arbitrárias |
| **Spelunky** | Templates + aleatoriedade | Escala limitada |

A literatura acadêmica (Hendrikx 2013, Togelius 2011, Shaker 2016) propõe técnicas mais sofisticadas, como busca evolutiva e geração adaptativa — mas com custo computacional inviável para tempo real.

**O gap identificado:** nenhum trabalho combina escala + coerência semântica + performance simultaneamente.

---

## 💡 Proposta de Solução

Um RPG 2D híbrido que separa duas camadas:

### 🎨 Camada Autoral (Fixo)
- NPCs principais e diálogos
- Cidades, ginásios e rotas obrigatórias
- Narrativa central coesa

### 🎲 Camada Procedural (Gerado por seed)
- ~100 criaturas únicas por seed
- Ambientação secundária (vegetação, construções menores)
- Reprodutível: mesma seed = mesmo mundo

---

## ⭐ Inovação: Atributos Correlacionados

A contribuição original é o conceito de **Atributos Correlacionados**.

Em vez de sortear cada característica de forma independente (como No Man's Sky), os **atributos derivados** são gerados com probabilidade **condicionada aos atributos primários**:

```
🔥 Fogo + 🐈 Gato  →  cores quentes, garras, presas        (alta probabilidade)
💧 Água + 🐟 Peixe  →  cores frias, escamas, nadadeiras    (alta probabilidade)  
🌿 Planta + 🦎 Lagarto  →  tons verdes, folhagem, camuflagem
```

### Tabela Comparativa (8 critérios)

| Trabalho | Ger. | IA | Rej. | Coer. | Esc. | Qual. | Perf. | **A.C.** |
|---|---|---|---|---|---|---|---|---|
| Hendrikx (2013) | ✓ | ✗ | ✓ | ✗ | ✓ | ✗ | ✗ | ✗ |
| Togelius (2011) | ✓ | ✓ | ✓ | ✓ | ✗ | ✓ | ✗ | ✗ |
| Shaker (2016) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ |
| Minecraft | ✓ | ✗ | ✓ | ✗ | ✓ | ✗ | ✓ | ✗ |
| No Man's Sky | ✓ | ✗ | ✓ | ✗ | ✓ | ✗ | ✓ | ✗ |
| Spelunky | ✓ | ✗ | ✓ | ✓ | ✗ | ✓ | ✓ | ✗ |
| **✨ Proposta** | ✓ | ✗ | ✓ | ✓ | ✓ | ✓ | ✓ | **✓** |

> **A.C. = Atributos Correlacionados** — único critério em que apenas esta proposta se destaca.

---

## 🏗️ Arquitetura

```
                        [ SEED ]
                           │
           ┌───────────────┴───────────────┐
           ▼                               ▼
  🎲 Gerador de Criaturas       🌿 Gerador de Ambientação
  (atributos correlacionados)   (vegetação, construções)
           │                               │
           └───────────────┬───────────────┘
                           ▼
                  📖 Núcleo Autoral
              (NPCs, mapas, diálogos fixos)
                           │
                           ▼
              🖥️ Camada de Apresentação
           (exploração, batalha, diálogo)
```

**Tecnologias previstas:**
- Engine: **Godot 4** (GDScript)
- Arte: Pixel art com paletas dinâmicas
- Versionamento: Git/GitHub
- Artigo: LaTeX (template SBC Reviews)

---

## 📈 Necessidade de Mercado

O mercado indie de jogos enfrenta um dilema real:

- Estúdios pequenos **não têm equipe** para criar centenas de criaturas únicas à mão
- O público **rejeita** conteúdo procedural genérico e sem identidade

Esta proposta entrega o meio-termo viável:

> **Identidade visual reconhecível + custo de produção baixo**

Aplicável a: RPGs indie · Jogos mobile · Roguelikes · Ferramentas de geração de assets

---

## 📅 Cronograma (PAC VII → PAC VIII)

| Semanas | Atividade |
|---|---|
| 1–2 | Revisão de literatura e fechamento do escopo técnico |
| 3–4 | Definição das tabelas de atributos e distribuições de probabilidade |
| 5–6 | Prototipagem do gerador de criaturas (módulo isolado) |
| 7–8 | Implementação do Núcleo Autoral em Godot 4 |
| 9–10 | Produção dos sprites base e paletas dinâmicas |
| 11–12 | Gerador procedural de ambientação secundária |
| 13–14 | Integração final dos módulos e camada de apresentação |
| 15–16 | Testes de coerência e inspeção visual |
| 17–18 | Coleta de métricas e validação |
| 19–20 | Artigo final, documentação e entrega |

---

## 📋 Resultados Esperados

- ✅ ~100 criaturas únicas por seed com identidade visual reconhecível
- ✅ Coerência semântica validável entre atributos primários e derivados
- ✅ Reprodutibilidade integral do mundo a partir da seed
- ✅ Tempo de geração < 2 segundos para o bestiário completo
- ✅ Coesão narrativa mantida pela camada autoral fixa

---

## 📚 Referências

- HENDRIKX, M. et al. Procedural content generation for games: A survey. *ACM TOMM*, 9(1):1–22, 2013.
- TOGELIUS, J. et al. Search-based procedural content generation: A taxonomy and survey. *IEEE TCIAIG*, 3(3):172–186, 2011.
- SHAKER, N.; TOGELIUS, J.; NELSON, M. J. *Procedural Content Generation in Games*. Springer, 2016.
- Mojang Studios. Minecraft. https://www.minecraft.net
- Hello Games. No Man's Sky. https://www.nomanssky.com
- YU, D.; HULL, A. Spelunky. https://www.spelunkyworld.com, 2008.

---

## 📎 Artigo Completo

O artigo completo está disponível no repositório: [`artigo/`](./artigo/)

Publicado no template **SBC Computing Reviews 2025**, em português.

---

<p align="center">
  <sub>Centro Universitário Católica de Santa Catarina · PAC VII · 2026/1</sub>
</p>

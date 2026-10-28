# Atos pró-Lula nas ruas · 2026

Mapa e calendário dos atos de rua a favor de Luiz Inácio Lula da Silva na eleição presidencial de 2026, da reta final do 1º turno (28/09) até o 2º turno (25/10), no Brasil e entre brasileiros no exterior.

**Site:** `https://<seu-usuario>.github.io/atos-pro-lula-2026/` (GitHub Pages, branch `main`)

Projeto independente, sem vínculo com partidos, campanhas ou candidaturas. Responsável pelo conteúdo: Vinícius.

## O que tem no mapa

Cada registro é um ato de rua (caminhada, passeata, concentração em praça, ato cultural aberto) com:

| Campo | O que significa |
|---|---|
| `d` | Data do ato (horário de Brasília) |
| `cidade`, `uf`, `local` | Onde aconteceu; `lat`/`lon` apontam para o local do ato, ou para o centro da cidade quando a fonte não diz o local |
| `pais` | Só nos atos no exterior: país do ato (o mesmo nome vai em `uf`) |
| `t` | Tipo: `L` ato de campanha com Lula presente · `E` estudantil · `M` comitês, movimentos e outros |
| `s` | Situação: `R` realizado (há fonte confirmando) · `C` convocado, ainda sem confirmação |
| `hora` | Horário ou duração, quando informado |
| `pub` | Público como a fonte descreve |
| `pubFonte` | Quem estimou o público (PM, organizadores, partido, imprensa) |
| `conv` | Quem convocou ou organizou |
| `fontes` | Reportagens e posts usados |
| `midia` | Posts públicos com foto ou vídeo do ato, incorporados do X |

Os dados ficam em [`data/atos.json`](data/atos.json).

## Metodologia

- **Fontes:** imprensa nacional e regional, veículos de movimentos e partidos (sinalizados como tal quando relevante), agendas públicas e posts públicos no X.
- **Confirmação:** um ato só passa de "convocado" para "realizado" quando há reportagem ou registro (foto, vídeo, relato) feito depois do horário marcado.
- **Público:** quase nunca há contagem independente. O número publicado é sempre o da fonte e vem acompanhado de quem o estimou. O mapa não desenha os pontos pelo tamanho do público, para não amplificar estimativas de organizadores.
- **Redes sociais:** posts de perfis pessoais servem para confirmar que um ato aconteceu, mas o link não é publicado (aparece só "relato em rede social"). Só são incorporados posts de veículos, movimentos, organizações e figuras públicas.
- **Exterior:** atos de brasileiros fora do país aparecem numa área própria do mapa (botão “Exterior”), com três recortes: EUA e Canadá, Europa e Austrália. Na lista e no calendário entram junto com os demais.
- **Fora do mapa:** atos contra Lula, eventos fechados (plenárias em auditório), panfletagens e citações sem cidade ou local.

## Atualização

Atualização manual, uma vez por dia: a pesquisa é refeita, os registros novos ou corrigidos entram em `data/atos.json` e o commit traz o resumo do que mudou. O site mostra a data da última atualização.

Encontrou um erro ou um ato que falta? Abra uma *issue* com o link da fonte.

## Estrutura

```
index.html        mapa, calendário, tabela, linha do tempo, filtros e lista (HTML, CSS e JS num só arquivo; usa d3 via cdnjs)
data/atos.json    registros dos atos
data/br-uf.json   contorno dos estados (geodata simplificado)
data/mundo.json   contorno dos países nos recortes do exterior (geodata simplificado)
data/populacao.json  população das cidades e brasileiros por jurisdição consular (eixo vertical da linha do tempo)
```

Para rodar localmente: `python3 -m http.server` na pasta do projeto e abrir `http://localhost:8000`.

## Créditos

- Paleta e tipografia inspiradas na identidade visual de 2026 do site do PT (vermelho #e4142c, Sofia Sans Extra Condensed e Asap, via Google Fonts).
- Contorno dos estados: [click_that_hood / brazil-states](https://github.com/codeforgermany/click_that_hood), simplificado com mapshaper.
- Contorno dos países: [world-atlas](https://github.com/topojson/world-atlas) (Natural Earth, 1:50m), recortado e simplificado com mapshaper.
- População das cidades brasileiras: IBGE, [Censo Demográfico 2022](https://sidra.ibge.gov.br/tabela/4709) (tabela 4709); Ceilândia (DF), região administrativa sem dado municipal, pela PDAD 2021 (IPEDF Codeplan).
- Brasileiros no exterior: Itamaraty, *Comunidades Brasileiras no Exterior*, ano-base 2022 (ago. 2023), estimativa por jurisdição consular.
- Mapa com [d3](https://d3js.org/).

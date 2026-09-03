# Etapa 4 — Layout compacto / D&D-inspired

Esta etapa é principalmente de interface e não altera o schema de save (`v20`).

## Estrutura

- `Visão geral`: atributos + perícias + talentos + referência rápida no mesmo painel de consulta.
- `Combate & Poderes`: reúne recursos de combate, condições, descansos, equipamentos em uso e habilidades.
- `Inventário`: o baralho equipado continua como consulta visual, mas agora cada carta possui ação de edição.
- Demais abas: receberam a mesma linguagem visual, densidade, bordas e ritmo de espaçamento.

## Poderes

- Passivas e ativas não possuem mais aba isolada.
- As descrições 0–15, 16–29 e 30+ ficam simultaneamente visíveis quando cadastradas.
- A estaca atual continua selecionável por slider e botões rápidos.

## Perfil

- Retrato vertical maior.
- Nome, deus, nível, BP, Defesa, DT, HP, Energia, Sanidade e recurso especial no rail lateral.
- Testes contra a morte ficam compactos no perfil e funcionam em qualquer aba.

## Testes executados

- `node --check app.js` sem erros.
- Renderização automatizada sem erros de JavaScript.
- Navegação pelas oito abas validada.
- Edição do baralho → editor do Inventário validada.
- Teste contra a morte validado fora da aba de Combate.
- Habilidades renderizadas com as faixas de estaca simultaneamente visíveis.

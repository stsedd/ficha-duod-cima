# Etapa 4.3 — correção real solicitada pela revisão final

Esta revisão mantém o schema `v21`, mas refaz a entrega que havia ficado incompleta.

## Ajustes feitos

- **Perícias realmente compactadas**: a grade foi reequilibrada para alta densidade, com caixas de P/E menores e blocos aproximadamente pela metade da altura anterior.
- **Símbolo da Legião corrigido**: removida a dependência do asset remoto quebrado; o header agora usa um ícone local incluído no pacote.
- **Talentos revisados**: os **32 talentos** continuam cadastrados e o seletor de talentos ficou aberto por padrão, deixando a edição mais óbvia.
- **Cartas do baralho / inventário**: mantidas e validadas as imagens em armas, armadura, escudo e itens gerais; itens gerais seguem podendo ser marcados para aparecer no baralho.
- **Compatibilidade de preview local**: a ficha agora usa fallback de armazenamento em memória quando `localStorage` não estiver disponível, o que ajuda em ambientes restritos e nos testes automatizados.
- **Cache busting**: CSS e JS agora são carregados com `?v=4.3` para reduzir risco de o navegador reaproveitar arquivos antigos.

## Testes refeitos

- Contagem do banco de talentos conferida: **32 talentos**.
- Interação de adicionar talento validada.
- Ação **Editar** no baralho levando ao editor do item validada.
- Presença das categorias de inventário, incluindo **Arma mágica**, validada.
- Screenshot desktop e mobile geradas após a revisão.

---

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

---

# Etapa 4.2 — acabamento funcional

Esta revisão atualiza o save para `v21`. A versão anterior `v20` é migrada automaticamente.

## Perícias
- Blocos reduzidos para densidade de ficha tradicional.
- Marcas de **P** (Perito/proficiência) e **E** (Expertise) viraram checkboxes mínimos antes do nome da perícia.
- Origem e detalhes continuam editáveis no menu `•••`, sem ocupar espaço quando fechados.

## Talentos
- Banco atualizado para **32 talentos**.
- Talentos de nível 30+ e 60+ permanecem visíveis na lista antes do nível necessário, mas aparecem bloqueados até serem elegíveis.
- Restrições de escolha única são respeitadas para os talentos que explicitamente dizem que só podem ser escolhidos uma vez.
- Expert, Perito, Resiliente, Adepto Elemental e Aumento de Atributo possuem os campos necessários para registrar suas escolhas.

## Atributos e Defesa
- Atributos-base continuam editáveis depois da criação da ficha.
- Durante a criação, o limite de 8 pontos continua obrigatório.
- Depois da criação, a edição é livre para corrigir um valor diretamente; o Diagnóstico apenas avisa se o total-base terminar diferente de 8.
- Defesa ganhou um **ajuste manual persistente**, visível no perfil e em Combate & Poderes, para buffs, penalidades e outros efeitos situacionais.

## Inventário e imagens
- Armadura, escudo, armas e itens gerais aceitam imagem enviada pelo usuário.
- As imagens são reduzidas antes de serem guardadas e entram no JSON exportado junto da ficha.
- Itens gerais podem ser marcados como **no baralho** e passam a aparecer no baralho visual junto do equipamento.
- Categorias adicionadas/organizadas: Geral, Arma, Arma mágica, Armadura, Escudo, Herança, Relíquia, Consumível, Material, Crafting, Ferramenta, Missão, Mágico/especial e Outro.

## Verificações
- `node --check app.js` sem erros.
- `node --check talents.js` sem erros.
- Banco de talentos conferido: 32 IDs e 32 nomes únicos.

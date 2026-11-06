# Gerador de Simulações BP

Ferramenta web (arquivo único) que monta mensagens de simulação de crédito a partir de **data**, **nome do cliente**, **valor da parcela** e **valor do troco**. Feita no mesmo estilo do Gerador de Termos BP: página única, sem instalação, roda direto no navegador.

## Modo rápido — colar o texto

1. Cole o texto do sistema na primeira área e clique em **Processar Dados**.
2. A ferramenta localiza sozinha os dados (veja os formatos aceitos abaixo).
3. Os campos aparecem preenchidos para conferência (editáveis) e a simulação já é gerada em seguida.
4. Se algum dado não for localizado, ele fica destacado para você completar e clicar em **Gerar Simulação**.

Também dá para usar só os campos, digitando à mão, sem colar nada. E se você colar o texto e clicar direto em **Gerar Simulação** (sem passar antes por *Processar Dados*), o texto é interpretado automaticamente antes de gerar.

## Formatos reconhecidos no texto colado

**1. Texto do sistema BP (formato principal):**

- **Nome do cliente**: primeira linha, em CAIXA ALTA (sem rótulo e sem números);
- **Parcela**: tem prioridade o valor de `Parcela unificada X`; depois `PARCELA R$X` (linha do benefício); por último rótulos como `Nova parcela:`, `Valor da parcela:`, `Parcela:`;
- **Troco**: tem prioridade `Troco aproximado: X`; depois `TROCO R$X`; por último `Valor do troco:`, `Troco previsto:`, `Troco:`;
- **Data**: se houver linha com `Data: DD/MM/AAAA` (ou DD-MM-AAAA), ela é usada; caso contrário entra a data de hoje (ajustável no campo).

**2. Texto com rótulos tradicionais:**

- `Cliente:`, `Nome:`, `Beneficiário:`, `Segurado:`, `Titular:` para o nome;
- `Data: 05/11/2026` para a data;
- `Nova parcela:`, `Valor da parcela:`, `Parcela:` para a parcela;
- `Valor do troco:`, `Troco aproximado:`, `Troco:` para o troco.

Os nomes procurados podem ser ampliados editando os arrays `ROTULOS_NOME`, `ROTULOS_PARCELA` e `ROTULOS_TROCO` dentro do `<script>`.

## Botões de saída

- **Mensagem de Simulação** — completa, formatada para WhatsApp;
- **Versão Curta** — resposta rápida com o primeiro nome do cliente;
- **Ficha de Registro Interno** — texto simples para controle.

Se o **troco** ficar em branco (ou zero), a linha dele sai automaticamente das mensagens. Os últimos preenchimentos ficam salvos na memória do navegador (botão **Limpar** apaga tudo).

## Onde editar

Tudo fica dentro do `index.html`, no bloco marcado do `<script>`:

- **Empresa / canal de atendimento:** constantes `EMPRESA` e `CANAL_ATENDIMENTO`.
- **Textos das mensagens:** constantes `MODELO_PADRAO`, `MODELO_CURTO` e `MODELO_FICHA`. Edite livremente mantendo os marcadores `{{...}}` intactos.
- **Nomes reconhecidos na colagem:** `ROTULOS_NOME`, `ROTULOS_PARCELA`, `ROTULOS_TROCO`.

## Publicar no GitHub Pages (mesmo jeito do Gerador de Termos)

1. Crie um repositório novo, ex.: `gerador-simulacoes-bp`, e envie o `index.html` (+ este README). Na criação do repo dá para arrastar o ZIP direto.
2. Em **Settings → Pages**, ative *Deploy from a branch* (branch `main`).
3. A ferramenta fica em `https://<seu-usuario>.github.io/gerador-simulacoes-bp/`.

---

Ferramenta interna — BP Promotora de Créditos.

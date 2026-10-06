# CONTEXTO DO PROJETO — Pit Lane F1

> Documento de referência criado **somente a partir dos arquivos recebidos** (`index.html`, `login.html`, `cadastro.html`, `style.css`).
> Nenhum arquivo do projeto foi alterado.

**Legenda usada neste documento**

| Marca | Significado |
|---|---|
| **[IDENTIFICADO]** | Está escrito diretamente nos arquivos. |
| **[INTERPRETAÇÃO]** | Conclusão necessária para explicar o funcionamento, baseada em evidências dos arquivos. |
| **[NÃO DETERMINADO]** | Não dá para saber só com os arquivos recebidos. |

---

## 1. Inventário do projeto

### 1.1 Arquivos recebidos

```
(pasta do projeto — estrutura real NÃO DETERMINADA, ver 1.3)
├── index.html
├── login.html
├── cadastro.html
└── style.css
```

| Tipo | Arquivos | Quantidade |
|---|---|---|
| HTML | `index.html`, `login.html`, `cadastro.html` | 3 |
| CSS | `style.css` | 1 |
| JavaScript | — | **0** (nenhum arquivo `.js` e nenhuma tag `<script>` nos 3 HTML) |
| JSON / configuração | — | 0 |
| Imagens recebidas | — | 0 |
| Fontes locais | — | 0 |
| Bibliotecas / frameworks | — | 0 |

### 1.2 Recursos referenciados que NÃO foram recebidos

**[IDENTIFICADO]** O `index.html` referencia estas imagens (todas em `img/...`), mas elas não estavam entre os arquivos:

| Caminho referenciado | Usado em |
|---|---|
| `img/circuitos/hero.jpg` | Fundo da seção inicial (hero) |
| `img/carros/ferrari.jpg`, `mclaren.jpg`, `mercedes.jpg` | Cards de carros |
| `img/pilotos/verstappen.jpg`, `norris.jpg`, `leclerc.jpg`, `hamilton.jpg` | Cards de pilotos |
| `img/circuitos/interlagos.jpg`, `monaco.jpg`, `monza.jpg`, `suzuka.jpg` | Cards de circuitos |
| `img/equipes/ferrari.png` | Aparece **somente em um comentário HTML** (exemplo de como trocar o texto "SF" por um logo); não é usado na página |

### 1.3 Estrutura de diretórios

**[IDENTIFICADO]** Os HTML referenciam `style.css` por caminho relativo simples (`href="style.css"`), então ele deve estar na mesma pasta dos HTML. Os caminhos `img/carros/`, `img/pilotos/`, `img/circuitos/` e `img/equipes/` indicam uma pasta `img/` com subpastas.

**[NÃO DETERMINADO]** Se essa pasta `img/` realmente existe e o que há dentro dela.

---

## 2. Finalidade do projeto

**[IDENTIFICADO]** É um **site informativo sobre Fórmula 1**, chamado **Pit Lane F1**. Evidências:

- `<title>`: "Pit Lane F1 | Carros, pilotos, equipes e circuitos".
- `<meta name="description">`: "portal sobre Fórmula 1 com carros, pilotos, equipes, circuitos e calendário da temporada".
- Seções do `index.html`: Sobre a F1, Carros, Pilotos, Equipes, Circuitos, Calendário.

**[IDENTIFICADO]** É um **projeto acadêmico**: o rodapé traz "Projeto acadêmico", "ADS", "Web Front End" e "© 2026 Pit Lane F1 — Projeto acadêmico."

**[IDENTIFICADO]** As telas de login e cadastro são **demonstração de interface**. Os próprios arquivos avisam: "Demonstração de interface: não existe autenticação real." (login) e "nenhum dado é enviado ou salvo" (cadastro).

---

## 3. Visão geral do sistema

### 3.1 O que o usuário consegue fazer

- Ler informações sobre a F1, 3 carros, 4 pilotos, 4 equipes, 4 circuitos e 4 etapas de um calendário.
- Navegar entre as seções da página inicial pelo menu, pelos atalhos e pelos botões.
- Abrir as telas de login e cadastro, preencher os campos e enviar o formulário (apenas navega para outra página).

### 3.2 Telas existentes

| Tela | Arquivo |
|---|---|
| Página inicial (site completo) | `index.html` |
| Entrar | `login.html` |
| Criar conta | `cadastro.html` |

### 3.3 Fluxo de navegação

```
index.html ──(botão "Login" no menu)──► login.html ──(link "Criar conta")──► cadastro.html
    ▲                                       │  ▲                                  │
    │                                       │  └────(link "Entrar")───────────────┤
    └──(envio do formulário de login)───────┘                                     │
    └──(logo / link "← Voltar ao site")───────────────────────────────────────────┘

cadastro.html ──(envio do formulário)──► login.html
```

---

## 4. Estrutura e responsabilidade dos arquivos

| Arquivo | Responsabilidade | Depende de |
|---|---|---|
| `index.html` | Página principal. Todo o conteúdo informativo (texto e dados) está escrito direto no HTML. | `style.css`, Google Fonts, imagens `img/...` |
| `login.html` | Tela de login (formulário com e-mail e senha). | `style.css`, Google Fonts |
| `cadastro.html` | Tela de cadastro (nome, e-mail, senha e confirmação). | `style.css`, Google Fonts |
| `style.css` | Único arquivo de estilos, usado pelas 3 páginas. | Fonte "Titillium Web" (carregada no `<head>` dos HTML) |

---

## 5. HTML

### 5.1 `index.html`

Estrutura (nesta ordem):

| Bloco | ID | Conteúdo |
|---|---|---|
| `<header class="site-header">` | — | Logo "PIT LANE F1", menu e botão "Login". |
| Hero | `inicio` | Título, texto, 2 botões, 4 números (`.stats`) e uma nota. |
| Atalhos (`div.atalhos`) | — | 5 links para seções. |
| Sobre a Fórmula 1 | `f1` | Texto + 6 cards informativos (FIA, Grandes Prêmios, Pilotos, Construtores, Pontuação, Pit Stop). |
| Carros | `carros` | 3 cards: Ferrari SF-26, McLaren MCL40, Mercedes W17. |
| Pilotos | `pilotos` | 4 cards: Verstappen, Norris, Leclerc, Hamilton. |
| Equipes | `equipes` | 4 cards: Ferrari, McLaren, Mercedes, Red Bull Racing. |
| Circuitos | `pistas` | Lista de "chips" + 4 cards: Interlagos, Mônaco, Monza, Suzuka. |
| Calendário | `calendario` | Lista ordenada (`<ol>`) com 4 etapas. |
| `<footer class="site-footer">` | — | Descrição, navegação, redes (links `#`), informações. |

**Elementos semânticos usados [IDENTIFICADO]:** `header`, `nav`, `main`, `section`, `article`, `footer`, `ol`, `ul`, `dl/dt/dd`, `h1` a `h3`. Há `aria-label` e `aria-labelledby` em vários elementos.

**Menu mobile sem JavaScript [IDENTIFICADO]:** um `<input type="checkbox" id="menu-toggle">` escondido e um `<label for="menu-toggle" class="menu-btn">☰</label>`. O CSS usa o estado `:checked` do checkbox para abrir o menu.

**Imagens [IDENTIFICADO]:** nenhuma tag `<img>` é usada. As imagens entram por CSS, pela variável `--img` definida em `style="--img:url('...')"` nos elementos `.hero-bg` e `.media`. Cada `.media` tem `data-label` (texto exibido quando não há foto).

**Links do menu:** `#inicio`, `#f1`, `#carros`, `#pilotos`, `#equipes`, `#pistas`, `#calendario` e `login.html`.

### 5.2 `login.html`

- `<form class="form-card" action="index.html">`
- Campos: **E-mail** (`type="email"`, `required`, id `email`) e **Senha** (`type="password"`, `required`, id `senha`).
- Botão "Entrar" (`type="submit"`).
- Links: "Esqueci minha senha" (`href="#"`), "Criar conta" (`cadastro.html`), "← Voltar ao site" (`index.html`).
- Aviso visível (`.aviso`): demonstração de interface.

### 5.3 `cadastro.html`

- `<form class="form-card" action="login.html">`
- Campos: **Nome** (`text`, `required`), **E-mail** (`email`, `required`), **Senha** (`password`, `required`, `minlength="8"`, dica "Use pelo menos 8 caracteres."), **Confirmar senha** (`password`, `required`, `minlength="8"`).
- Botão "Cadastrar".
- Links: "Entrar" (`login.html`), "← Voltar ao site" (`index.html`).

**[IDENTIFICADO]** Nos dois formulários, os `<input>` **não têm atributo `name`**, como o comentário do `login.html` confirma ("os campos não têm 'name', então nenhum dado é enviado").

---

## 6. CSS (`style.css`)

### 6.1 Organização

O arquivo é dividido em 16 blocos numerados, listados no comentário do topo: 1 Reset, 2 Variáveis, 3 Base, 4 Header, 5 Hero, 6 Botões, 7 Seções, 8 Cards, 9 Carros, 10 Pilotos, 11 Equipes, 12 Circuitos, 13 Calendário, 14 Formulários, 15 Footer, 16 Responsivo.

### 6.2 Variáveis (bloco 2, `:root`)

| Variável | Função |
|---|---|
| `--bg-primary`, `--bg-secondary`, `--bg-card` | Fundos (preto/cinza escuro). |
| `--accent`, `--accent-dark`, `--accent-text` | Vermelho de destaque (o último é um vermelho mais claro para texto pequeno, por contraste). |
| `--text-primary`, `--text-secondary`, `--metal` | Cores de texto. |
| `--border`, `--shadow`, `--radius`, `--ease` | Borda, sombra, arredondamento e transição padrão. |
| `--fonte` | Titillium Web, com Segoe UI, Arial e sans-serif como reserva. |

O comentário indica que a paleta e as medidas devem ser alteradas somente nesse bloco.

### 6.3 Componentes principais

| Classe | Função na interface |
|---|---|
| `.container` | Largura máxima de 1150px, centralizada. |
| `.site-header`, `.menu` | Cabeçalho fixo no topo (`position: sticky`) com menu horizontal. |
| `.hero`, `.hero-bg`, `.stats`, `.atalhos` | Seção inicial com fundo em degradê/imagem, números e atalhos. |
| `.btn`, `.btn-primary`, `.btn-outline`, `.btn-sm` | Botões. |
| `.section`, `.section--alt`, `.section-head`, `.grid` | Seções e grade responsiva de cards. |
| `.card`, `.card-body`, `.media`, `.tag`, `.link-seta`, `.dados` | Card reutilizado em carros, pilotos, equipes e circuitos. |
| `.media--car`, `.media--driver`, `.driver-num` | Variações do card (proporção da imagem e número do piloto). |
| `.team-logo` | Área do "logo" da equipe (hoje um texto como "SF", "MCL"). |
| `.chips`, `.circuit`, `.ficha` | Lista de circuitos e ficha técnica (km e curvas). |
| `.calendario`, `.corrida`, `.status` | Linhas do calendário. |
| `.auth`, `.form-card`, `.campo`, `.aviso`, `.dica`, `.form-links` | Telas de login e cadastro. |
| `.site-footer`, `.footer-grid`, `.footer-fim` | Rodapé. |

### 6.4 Técnicas de layout e interação [IDENTIFICADO]

- **Flexbox** (header, menu, botões, cards) e **CSS Grid** (grades de cards, calendário, rodapé, formulários).
- **Estados `:hover` e `:focus-visible`**: elevação dos cards, sublinhado do menu, anel de foco.
- **Animação** de entrada das seções (`@keyframes entrada`).
- **Link ativo do menu sem JavaScript**: usa `:target` junto com `body:has(...)` para destacar o link da seção clicada.
- **Menu hambúrguer sem JavaScript**: `.menu-toggle:checked ~ nav .menu`.
- **Destaque de circuito**: `.circuit:target` muda a cor da borda do card quando o chip correspondente é clicado.
- **Campo inválido**: `.campo input:not(:placeholder-shown):invalid` pinta a borda de laranja (`#ff8a4d`).
- Funções e propriedades modernas usadas: `clamp()`, `min()`, `aspect-ratio`, `backdrop-filter`, `-webkit-text-stroke`, variáveis CSS.

### 6.5 Responsividade (media queries) [IDENTIFICADO]

| Condição | O que muda |
|---|---|
| `max-width: 1024px` | "Sobre" vira 1 coluna; rodapé vira 2 colunas. |
| `max-width: 850px` | Aparece o botão ☰ e o menu vira lista vertical. |
| `max-width: 700px` | Menos espaçamento nas seções; cards "Sobre" em 1 coluna; calendário e rodapé em layout compacto; formulário com menos padding. |
| `prefers-reduced-motion: reduce` | Desativa animações e transições. |

### 6.6 Classes usadas no HTML e sem regra no CSS

**[IDENTIFICADO]** `corrida--realizada` é aplicada às etapas 01 e 02 do calendário, mas **não existe regra CSS** para ela. As etapas "realizadas" ficam com o estilo base de `.corrida`. Já `corrida--proxima` e `corrida--breve` têm regras próprias.

---

## 7. JavaScript

**[IDENTIFICADO]** **Não existe JavaScript neste projeto.** Nenhum arquivo `.js` e nenhuma tag `<script>` (nem inline) nas 3 páginas. Comentários dos arquivos confirmam a intenção ("Sem JavaScript e sem backend"). Todo o comportamento interativo vem de HTML e CSS (âncoras, checkbox, `:target`, `:has()`, validação nativa dos formulários).

---

## 8. Fluxo dos dados

```
Dados dos cards, calendário e números
        ↓ (escritos manualmente no HTML)
index.html ──► navegador ──► tela

Entrada do usuário (login / cadastro)
        ↓
Formulário HTML (validação nativa: required, type="email", minlength)
        ↓
Envio (submit) ──► apenas navega para a página definida em "action"
        ↓
Nenhum dado é lido, enviado, processado ou salvo
```

**[INTERPRETAÇÃO]** Como os `<input>` não têm `name` e não há script, o navegador não envia os valores digitados. O envio apenas troca de página.

---

## 9. Dependências e tecnologias

| Tecnologia | Onde é usada | Evidência |
|---|---|---|
| HTML5 | As 3 páginas | `<!DOCTYPE html>`, `lang="pt-BR"`, elementos semânticos |
| CSS3 | `style.css` | Variáveis, Flexbox, Grid, media queries |
| **Google Fonts — Titillium Web** (externa) | As 3 páginas | `<link>` para `fonts.googleapis.com` e `fonts.gstatic.com` no `<head>`; usada pela variável `--fonte` |

**[IDENTIFICADO]** Não há frameworks, bibliotecas, CDNs de scripts, APIs, nem ferramentas de build visíveis nos arquivos.

---

## 10. Armazenamento e persistência

**[IDENTIFICADO]** **Não há persistência.** Sem JavaScript, não há `localStorage`, `sessionStorage`, cookies ou IndexedDB. Sem `name` nos campos e sem backend, também não há envio a servidor. Nenhum arquivo JSON ou banco de dados foi encontrado.

---

## 11. Interação entre componentes

```
index.html / login.html / cadastro.html
 ├── style.css
 │     └── fonte "Titillium Web" (declarada em --fonte; carregada pelo <link> dos HTML)
 ├── Google Fonts (externo, carregado no <head>)
 └── img/... (somente index.html; imagens entram via --img no CSS)
```

Relações entre páginas: ver o fluxo em 3.3.

---

## 12. Funcionalidades identificadas

| Funcionalidade | Onde | Como funciona |
|---|---|---|
| Menu de navegação por âncoras | `index.html` | Links `#inicio`, `#f1` etc. levam às seções (`scroll-behavior: smooth` e `scroll-padding-top: 80px` no CSS). |
| Destaque do link ativo | `style.css` | `:target` + `body:has(...)`. |
| Menu hambúrguer (≤ 850px) | `index.html` + `style.css` | Checkbox + `:checked`. |
| Cards de conteúdo | `index.html` | Dados escritos no HTML. |
| Cards com fallback de imagem | `.media` | Mostra o texto de `data-label` quando a imagem não carrega ou não existe. |
| Seleção de circuito por chips | `index.html` + `style.css` | Chip leva ao card (`#interlagos` etc.) e `:target` destaca a borda. |
| Calendário com 3 estados visuais | `index.html` + `style.css` | `--proxima` (vermelho), `--breve` (borda metálica), `--realizada` (sem estilo próprio). |
| Login (interface) | `login.html` | Campos obrigatórios, e-mail com validação nativa; envia para `index.html`. |
| Cadastro (interface) | `cadastro.html` | Campos obrigatórios, senha com mínimo de 8 caracteres; envia para `login.html`. |
| Layout responsivo | `style.css` | 3 breakpoints + `prefers-reduced-motion`. |

**Funcionalidades NÃO existentes (apesar de sugeridas pela interface):**

- Autenticação real e criação real de conta.
- "Esqueci minha senha" (`href="#"`, não leva a lugar nenhum).
- Redes sociais do rodapé (links `#`, marcados como fictícios em comentário).
- Conferência de "Senha" igual a "Confirmar senha": **não há mecanismo** para isso (sem JavaScript e sem `pattern`).

---

## 13. Regras de negócio

**[IDENTIFICADO]** O projeto não tem lógica de negócio. As únicas regras são validações nativas do navegador:

- Login: e-mail em formato válido e senha preenchidos.
- Cadastro: nome e e-mail preenchidos (e-mail válido); senha e confirmação com no mínimo 8 caracteres.
- Regra visual: borda laranja em campo preenchido e inválido.
- Regra visual do calendário: classe da etapa define cor/estado (ver 6.6).

---

## 14. Telas e interfaces

### `index.html`
Finalidade: apresentar a F1. Elementos: ver seção 5.1. Navegação: âncoras internas e `login.html` (botão no menu).

### `login.html`
Finalidade: tela de entrada (demonstração). Elementos: card centralizado com logo, título "Entrar", aviso, 2 campos e botão. Navegação: `index.html` (logo, envio e "Voltar ao site"), `cadastro.html`.

### `cadastro.html`
Finalidade: tela de criação de conta (demonstração). Elementos: card centralizado com logo, título "Criar conta", aviso, 4 campos e botão. Navegação: `login.html` (envio e "Entrar"), `index.html`.

---

## 15. Arquitetura identificada

**[IDENTIFICADO]** **Site estático de múltiplas páginas: HTML + CSS.** Sem JavaScript, sem backend, sem API e sem banco de dados. Uma única folha de estilos compartilhada.

---

## 16. Pontos importantes para manutenção

- **Arquivo central de estilos:** `style.css`. Cores e medidas ficam no bloco `:root` (bloco 2).
- **Ponto de entrada:** `index.html`. As telas de login e cadastro são acessadas pelo botão "Login" do menu.
- **Atualizar conteúdo:** os dados (carros, pilotos, equipes, circuitos, calendário, números do hero) estão escritos direto no HTML. Os comentários do `index.html` indicam onde editar.
- **Calendário:** datas aparecem como "DATA A CONFIRMAR"; o comentário do arquivo diz que datas e status são exemplos.
- **Dados da temporada:** os comentários do `index.html` pedem conferência em formula1.com antes de apresentar. **Este documento não verificou a correção desses dados.**
- **Imagens:** são carregadas por `--img` (CSS), não por `<img>`. Sem foto, aparece o texto de `data-label`.
- **Menu e destaque do link ativo** dependem de seletores `:has()`, `:target` e `:checked`. Qualquer mudança em IDs de seção ou na ordem `input → label → nav` do cabeçalho pode quebrar o menu.
- **Rodapé:** contém o texto "Desenvolvido por: [seu nome]" (campo ainda não preenchido) e links `#` marcados como fictícios.
- **Links que apontam para destinos genéricos:** "Ver detalhes →" dos carros leva a `#equipes`; "Ver circuito" dos circuitos leva a `#calendario`.

---

## 17. Limitações da documentação

- **[NÃO DETERMINADO]** Estrutura real de pastas do projeto (só 4 arquivos foram recebidos).
- **[NÃO DETERMINADO]** Se as 12 imagens referenciadas existem, e como são.
- **[NÃO DETERMINADO]** Como o site é publicado ou hospedado.
- **[NÃO DETERMINADO]** A correção dos dados da temporada 2026 (pilotos, equipes, números, resultados). Estão como foram escritos nos arquivos.
- **[NÃO DETERMINADO]** Aparência final no navegador (a análise foi feita lendo o código, sem renderizar a página).
- A fonte Titillium Web depende de acesso à internet para ser carregada.

---

## 18. Conclusão

**Pit Lane F1** é um site informativo estático e acadêmico sobre Fórmula 1, com 3 páginas (`index.html`, `login.html`, `cadastro.html`) e 1 folha de estilos (`style.css`). Apresenta carros, pilotos, equipes, circuitos e calendário, e tem telas de login e cadastro apenas de demonstração. Usa HTML5 e CSS3 (Flexbox, Grid, variáveis, `:target`, `:has()`, media queries), sem JavaScript, sem backend e sem persistência, com a fonte Titillium Web do Google Fonts como única dependência externa. O fluxo principal é: o usuário navega pelas seções do `index.html` e pode abrir login e cadastro, cujos envios apenas trocam de página.

# Clinivet Website Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Redesenhar o site estático da Clinivet com duas páginas: página principal de contatos e página de política de privacidade.

**Architecture:** Site HTML estático puro com CSS compartilhado em arquivo externo (`style.css`). Duas páginas: `index.html` (contatos, horários, serviços) e `politica.html` (resumo LGPD e link para PDF). Deploy automático via GitHub Actions já configurado.

**Tech Stack:** HTML5, CSS3, Google Fonts (Montserrat), Font Awesome 4.7 (ícones sociais)

---

## Estrutura de Arquivos

| Arquivo | Ação | Responsabilidade |
|---|---|---|
| `style.css` | Criar | Todos os estilos compartilhados entre as duas páginas |
| `index.html` | Reescrever | Página principal: hero, horários, endereço, contatos, serviços, rodapé |
| `politica.html` | Criar | Página de privacidade: header, resumo LGPD, botões PDF, rodapé |
| `.gitignore` | Modificar | Ignorar `.superpowers/` |

---

### Task 1: Criar `.gitignore` e o stylesheet compartilhado

**Files:**
- Modify: `.gitignore`
- Create: `style.css`

- [ ] **Step 1: Adicionar `.superpowers/` ao `.gitignore`**

Se `.gitignore` não existir, criar. Adicionar ao final:

```
.superpowers/
```

- [ ] **Step 2: Criar `style.css` com todos os estilos compartilhados**

```css
/* normalize.css v8.0.1 — MIT License — github.com/necolas/normalize.css */
html { line-height: 1.15; -webkit-text-size-adjust: 100%; }
body { margin: 0; }
main { display: block; }
h1 { font-size: 2em; margin: 0.67em 0; }
hr { box-sizing: content-box; height: 0; overflow: visible; }
a { background-color: transparent; }
img { border-style: none; }
button, input, optgroup, select, textarea { font-family: inherit; font-size: 100%; line-height: 1.15; margin: 0; }
button, input { overflow: visible; }
button, select { text-transform: none; }
button, [type="button"], [type="reset"], [type="submit"] { -webkit-appearance: button; }
[hidden] { display: none; }

/* Base */
*, *::before, *::after { box-sizing: border-box; }

body {
  font-family: "Montserrat", sans-serif;
  font-size: 16px;
  line-height: 1.5;
  background: #f5f5f5;
  color: #333;
}

a {
  text-decoration: none;
  transition: opacity 0.2s ease;
}

a:hover { opacity: 0.8; }

/* Hero */
.hero {
  background: #314230;
  padding: 40px 16px 28px;
  text-align: center;
}

.hero__logo {
  display: block;
  max-width: 320px;
  width: 100%;
  margin: 0 auto;
}

.hero__subtitle {
  color: rgba(255, 255, 255, 0.85);
  font-size: 13px;
  letter-spacing: 0.5px;
  margin: 12px 0 0;
}

/* Badge "Plantão 24h" */
.badge {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  background: rgba(144, 190, 68, 0.15);
  border-radius: 20px;
  padding: 4px 14px;
  margin-top: 10px;
}

.badge__dot {
  width: 7px;
  height: 7px;
  background: #90be44;
  border-radius: 50%;
  flex-shrink: 0;
}

.badge__text {
  color: #90be44;
  font-size: 11px;
  font-weight: 700;
}

/* Container */
.container {
  max-width: 640px;
  margin: 0 auto;
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

/* Card */
.card {
  background: white;
  border-radius: 8px;
  padding: 16px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.07);
}

.card__label {
  font-size: 11px;
  font-weight: 700;
  color: #90be44;
  text-transform: uppercase;
  letter-spacing: 0.6px;
  margin: 0 0 10px;
}

/* Linhas de contato */
.contact-rows {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.contact-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
}

.contact-row__label { color: #444; }

.contact-row__value { font-weight: 600; }

.contact-row__value--emergency { color: #c0392b; }

.contact-row__value--whatsapp { color: #25D366; }

.contact-row a { color: inherit; }

/* Separador */
.divider {
  height: 1px;
  background: #f0f0f0;
  margin: 4px 0;
}

/* Horário: badge inline */
.hours-badge {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  background: rgba(144, 190, 68, 0.1);
  border-radius: 20px;
  padding: 2px 10px;
}

.hours-badge__dot {
  width: 5px;
  height: 5px;
  background: #90be44;
  border-radius: 50%;
}

.hours-badge__text {
  font-size: 11px;
  font-weight: 700;
  color: #314230;
}

/* Pills de serviços */
.pills {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 12px;
}

.pill {
  background: #f0f7e0;
  border: 1px solid #c8e6a0;
  color: #314230;
  border-radius: 20px;
  padding: 4px 12px;
  font-size: 13px;
}

.instagram-link {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  font-size: 13px;
  color: #555;
}

.instagram-link__icon {
  width: 16px;
  height: 16px;
  border-radius: 4px;
  background: linear-gradient(135deg, #833ab4, #fd1d1d, #fcb045);
  flex-shrink: 0;
}

/* Botões de redes sociais */
.social-buttons {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.social-btn {
  display: inline-block;
  color: white;
  border-radius: 5px;
  padding: 8px 16px;
  font-size: 13px;
  font-weight: 600;
}

.social-btn--facebook { background: #1877F2; }

.social-btn--instagram {
  background: linear-gradient(135deg, #833ab4, #fd1d1d, #fcb045);
}

/* Links de documentos */
.doc-links {
  display: flex;
  gap: 8px;
}

.doc-link {
  flex: 1;
  border-radius: 6px;
  padding: 10px 8px;
  text-align: center;
  font-size: 13px;
}

.doc-link--primary {
  border: 1px solid #90be44;
  color: #314230;
}

.doc-link--secondary {
  border: 1px solid #ccc;
  color: #666;
}

/* Rodapé */
.footer {
  background: #314230;
  padding: 32px 16px 20px;
  text-align: center;
}

.footer__logo {
  display: block;
  max-width: 200px;
  width: 60%;
  margin: 0 auto 16px;
  opacity: 0.9;
}

.footer__copy {
  color: rgba(255, 255, 255, 0.4);
  font-size: 12px;
  margin: 0 0 8px;
}

.footer__tech {
  font-size: 11px;
  color: rgba(255, 255, 255, 0.3);
}

.footer__tech a {
  color: rgba(255, 255, 255, 0.45);
  text-decoration: underline;
}

/* Cabeçalho da página de política */
.page-header {
  background: #314230;
  padding: 14px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.page-header__back {
  color: rgba(255, 255, 255, 0.6);
  font-size: 13px;
}

.page-header__logo {
  height: 40px;
  display: block;
}

/* LGPD: lista de direitos */
.lgpd-rights {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.lgpd-rights li {
  display: flex;
  gap: 8px;
  font-size: 14px;
  color: #444;
}

.lgpd-rights__check {
  color: #90be44;
  font-weight: 700;
  flex-shrink: 0;
}

/* Botões da política */
.policy-buttons {
  display: flex;
  gap: 8px;
}

.btn {
  border-radius: 6px;
  padding: 12px 16px;
  text-align: center;
  font-size: 13px;
  font-weight: 700;
  display: block;
}

.btn--primary {
  background: #314230;
  color: white;
  flex: 2;
}

.btn--secondary {
  background: #90be44;
  color: white;
  flex: 1;
}

.policy-contact {
  font-size: 12px;
  color: #999;
  text-align: center;
  margin: 4px 0 0;
}

/* Responsivo */
@media (max-width: 480px) {
  .hero { padding: 32px 12px 20px; }
  .hero__logo { max-width: 240px; }
  .container { padding: 12px; }
  .doc-links { flex-direction: column; }
  .policy-buttons { flex-direction: column; }
}
```

- [ ] **Step 3: Verificar que o arquivo foi criado corretamente**

```bash
wc -l style.css
```

Esperado: mais de 150 linhas.

- [ ] **Step 4: Commitar**

```bash
git add .gitignore style.css
git commit -m "Add shared stylesheet and update gitignore"
```

---

### Task 2: Reescrever `index.html`

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Substituir o conteúdo completo de `index.html`**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Clinivet — Centro Clínico Veterinário</title>

  <meta name="author" content="Francisco Paiva Knebel">
  <meta name="description" content="Centro Clínico Veterinário em Ijuí, RS. Plantão 24h. Consultas, cirurgias, vacinação, internação e mais.">

  <meta property="og:title" content="Clinivet">
  <meta property="og:description" content="Centro Clínico Veterinário em Ijuí, RS. Plantão 24h.">
  <meta property="og:type" content="website">
  <meta property="og:image" content="https://clinivetijui.com.br/logo.png">
  <meta property="og:url" content="https://clinivetijui.com.br">
  <meta property="og:site_name" content="Clinivet">

  <link rel="dns-prefetch" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <header class="hero">
    <img class="hero__logo" src="logo.png" alt="Clinivet">
    <p class="hero__subtitle">Centro Clínico Veterinário Plantão 24h</p>
  </header>

  <main>
    <div class="container">

      <div class="card">
        <p class="card__label">Horário de Atendimento</p>
        <div class="contact-rows">
          <div class="contact-row">
            <span class="contact-row__label">Recepção: Seg a Sex</span>
            <span class="contact-row__value">7h30 às 19h</span>
          </div>
          <div class="contact-row">
            <span class="contact-row__label">Recepção: Sábado</span>
            <span class="contact-row__value">7h30 às 12h30</span>
          </div>
          <div class="divider"></div>
          <div class="contact-row">
            <span class="contact-row__label">Plantão</span>
            <span class="hours-badge">
              <span class="hours-badge__dot"></span>
              <span class="hours-badge__text">24 horas</span>
            </span>
          </div>
        </div>
      </div>

      <div class="card">
        <p class="card__label">Endereço</p>
        <address style="font-style: normal; font-size: 14px; color: #444; line-height: 1.6;">
          Rua 25 de Julho, 217, Centro<br>
          Ijuí, RS, 98700-000
        </address>
      </div>

      <div class="card">
        <p class="card__label">Contatos</p>
        <div class="contact-rows">
          <div class="contact-row">
            <span class="contact-row__label">Emergência</span>
            <span class="contact-row__value contact-row__value--emergency">
              <a href="tel:+5555992056809">(55) 99205-6809</a>
            </span>
          </div>
          <div class="contact-row">
            <span class="contact-row__label">Telefone</span>
            <span class="contact-row__value">
              <a href="tel:+555533322538">(55) 3332-2538</a>
            </span>
          </div>
          <div class="contact-row">
            <span class="contact-row__label contact-row__value--whatsapp">WhatsApp</span>
            <span class="contact-row__value contact-row__value--whatsapp">
              <a href="https://wa.me/5555981778017" target="_blank" rel="noopener">(55) 98177-8017</a>
            </span>
          </div>
        </div>
      </div>

      <div class="card">
        <p class="card__label">Serviços</p>
        <div class="pills">
          <span class="pill">Consultas</span>
          <span class="pill">Cirurgias</span>
          <span class="pill">Vacinação</span>
          <span class="pill">Internação</span>
          <span class="pill">Exames</span>
          <span class="pill">Banho e Tosa</span>
          <span class="pill">Emergência 24h</span>
        </div>
        <a class="instagram-link" href="https://www.instagram.com/clinivetijui/" target="_blank" rel="noopener">
          <span class="instagram-link__icon"></span>
          Ver mais no Instagram
        </a>
      </div>

      <div class="card">
        <p class="card__label">Redes Sociais</p>
        <div class="social-buttons">
          <a class="social-btn social-btn--facebook" href="https://www.facebook.com/clinivetijui/" target="_blank" rel="noopener">
            <i class="fa fa-facebook"></i> Facebook
          </a>
          <a class="social-btn social-btn--instagram" href="https://www.instagram.com/clinivetijui/" target="_blank" rel="noopener">
            <i class="fa fa-instagram"></i> Instagram
          </a>
        </div>
      </div>

      <div class="doc-links">
        <a class="doc-link doc-link--primary" href="politica.html">Política de Privacidade</a>
        <a class="doc-link doc-link--secondary" href="formulario.pdf" target="_blank" rel="noopener">Formulário de Cessão</a>
      </div>

    </div>
  </main>

  <footer class="footer">
    <img class="footer__logo" src="logo.png" alt="Clinivet">
    <p class="footer__copy">© 2026 Clinivet. Todos os direitos reservados.</p>
    <p class="footer__tech">
      <a href="https://knebel.inf.br" target="_blank" rel="noopener">Contato técnico</a>
    </p>
  </footer>

</body>
</html>
```

- [ ] **Step 2: Abrir no navegador e verificar visualmente**

```bash
xdg-open index.html
```

Verificar:
- Logo aparece no hero e no rodapé
- Subtítulo "Centro Clínico Veterinário Plantão 24h" visível
- Todos os cards aparecem com fundo branco e sombra
- Emergência em vermelho, WhatsApp em verde
- Pills de serviços com link do Instagram abaixo
- Link "Contato técnico" no rodapé aponta para knebel.inf.br

- [ ] **Step 3: Commitar**

```bash
git add index.html
git commit -m "Rewrite index.html with modern clean design"
```

---

### Task 3: Criar `politica.html`

**Files:**
- Create: `politica.html`

- [ ] **Step 1: Criar `politica.html`**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Política de Privacidade — Clinivet</title>

  <meta name="author" content="Francisco Paiva Knebel">
  <meta name="description" content="Política de Privacidade da Clinivet, Centro Clínico Veterinário em Ijuí, RS.">

  <meta property="og:title" content="Política de Privacidade — Clinivet">
  <meta property="og:description" content="Política de Privacidade da Clinivet, Centro Clínico Veterinário em Ijuí, RS.">
  <meta property="og:type" content="website">
  <meta property="og:image" content="https://clinivetijui.com.br/logo.png">
  <meta property="og:url" content="https://clinivetijui.com.br/politica.html">
  <meta property="og:site_name" content="Clinivet">

  <link rel="dns-prefetch" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <header class="page-header">
    <a class="page-header__back" href="index.html">&#8592; Voltar ao início</a>
    <img class="page-header__logo" src="logo.png" alt="Clinivet">
  </header>

  <main>
    <div class="container">

      <div class="card">
        <p class="card__label">Política de Privacidade</p>
        <p style="font-size: 14px; color: #555; line-height: 1.7; margin: 0 0 10px;">
          A Clinivet coleta dados pessoais exclusivamente para fins de atendimento veterinário e comunicação com tutores de animais.
        </p>
        <p style="font-size: 14px; color: #555; line-height: 1.7; margin: 0 0 10px;">
          As informações são tratadas em conformidade com a Lei Geral de Proteção de Dados (LGPD, Lei nº 13.709/2018).
        </p>
        <p style="font-size: 14px; color: #555; line-height: 1.7; margin: 0;">
          Para o documento completo, acesse o PDF abaixo.
        </p>
      </div>

      <div class="card">
        <p class="card__label">Seus Direitos (LGPD)</p>
        <ul class="lgpd-rights">
          <li><span class="lgpd-rights__check">✓</span> Acesso aos seus dados</li>
          <li><span class="lgpd-rights__check">✓</span> Correção de dados incorretos</li>
          <li><span class="lgpd-rights__check">✓</span> Solicitação de exclusão</li>
          <li><span class="lgpd-rights__check">✓</span> Portabilidade dos dados</li>
        </ul>
      </div>

      <div class="policy-buttons">
        <a class="btn btn--primary" href="politica.pdf" target="_blank" rel="noopener">
          Ver documento completo (PDF)
        </a>
        <a class="btn btn--secondary" href="formulario.pdf" target="_blank" rel="noopener">
          Formulário
        </a>
      </div>

      <p class="policy-contact">
        Para exercer seus direitos: (55) 3332-2538 ou (55) 98177-8017
      </p>

    </div>
  </main>

  <footer class="footer">
    <img class="footer__logo" src="logo.png" alt="Clinivet">
    <p class="footer__copy">© 2026 Clinivet. Todos os direitos reservados.</p>
    <p class="footer__tech">
      <a href="https://knebel.inf.br" target="_blank" rel="noopener">Contato técnico</a>
    </p>
  </footer>

</body>
</html>
```

- [ ] **Step 2: Abrir no navegador e verificar visualmente**

```bash
xdg-open politica.html
```

Verificar:
- Header escuro com link "Voltar ao início" e logo
- Cards com texto da política e lista de direitos LGPD com checks verdes
- Botão "Ver documento completo" em verde escuro, botão "Formulário" em verde claro
- Texto de contato discreto abaixo dos botões
- Logo grande no rodapé com "Contato técnico" linkado

- [ ] **Step 3: Verificar navegação entre páginas**

Em `index.html`, clicar em "Política de Privacidade" deve abrir `politica.html`.
Em `politica.html`, clicar em "Voltar ao início" deve voltar para `index.html`.

- [ ] **Step 4: Commitar**

```bash
git add politica.html
git commit -m "Add politica.html with LGPD summary and PDF links"
```

---

### Task 4: Verificação final e deploy

**Files:** nenhum arquivo novo

- [ ] **Step 1: Verificar responsividade em tela pequena**

Abrir as duas páginas no navegador, reduzir a janela para menos de 480px e verificar:
- `doc-links` empilha verticalmente
- `policy-buttons` empilha verticalmente
- Logo do hero não transborda

- [ ] **Step 2: Verificar todos os links externos**

| Link | Destino esperado |
|---|---|
| WhatsApp | `https://wa.me/5555981778017` |
| Facebook | `https://www.facebook.com/clinivetijui/` |
| Instagram | `https://www.instagram.com/clinivetijui/` |
| Serviços (Instagram) | `https://www.instagram.com/clinivetijui/` |
| PDF Política | `politica.pdf` (abre em nova aba) |
| PDF Formulário | `formulario.pdf` (abre em nova aba) |
| Contato técnico | `https://knebel.inf.br` (abre em nova aba) |

- [ ] **Step 3: Commitar qualquer ajuste final e fazer push**

```bash
git push origin main
```

O GitHub Actions (`.github/workflows/static.yml`) fará o deploy automático para GitHub Pages.

- [ ] **Step 4: Confirmar deploy bem-sucedido**

Acessar `https://clinivetijui.com.br` e verificar que o novo design está no ar.

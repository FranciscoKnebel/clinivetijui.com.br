# Redesign do Site Estático da Clinivet

**Data:** 2026-06-01  
**Status:** Aprovado

## Objetivo

Redesenhar o site estático da Clinivet (clinivetijui.com.br) para servir como página de divulgação de contatos e política de privacidade. O site atual é funcional mas carece de hierarquia visual e organização de informações.

## Estrutura de Páginas

Duas páginas HTML estáticas:

- `index.html` — página principal com todos os dados de contato, horários e serviços
- `politica.html` — página de política de privacidade com resumo LGPD e link para o PDF completo

## Design

**Paleta de cores** (mantida da identidade atual):
- Verde escuro: `#314230`
- Verde claro: `#90be44`
- Fundo de conteúdo: `#f5f5f5`
- Cards: branco com sombra suave

**Tipografia:** Montserrat (Google Fonts), já em uso

**Estilo:** Moderno e limpo — hero escuro com logo, conteúdo em cards brancos com sombra, container centralizado com `max-width`.

**Assets reutilizados:** `logo.png`, `politica.pdf`, `formulario.pdf`

## index.html — Conteúdo

### Hero
- Fundo `#314230`
- Logo `logo.png` centralizado e grande
- Subtítulo: "Centro Clínico Veterinário Plantão 24h"

### Cards de conteúdo (container `max-width: 640px`, centralizado)

**Horário de Atendimento**
- Recepção: Seg a Sex, 7h30 às 19h
- Recepção: Sábado, 7h30 às 12h30
- Plantão: 24 horas (badge verde animado)

**Endereço**
- Rua 25 de Julho, 217, Centro
- Ijuí, RS, 98700-000

**Contatos**
- Emergência: (55) 99205-6809 (destacado em vermelho)
- Telefone: (55) 3332-2538
- WhatsApp: (55) 98177-8017 (link `wa.me`, destaque verde)

**Serviços**
- Pills/tags em verde claro: Consultas, Cirurgias, Vacinação, Internação, Exames, Banho e Tosa, Emergência 24h
- Link "Ver mais no Instagram" abaixo das tags (href `https://www.instagram.com/clinivetijui/`, abre em nova aba)

**Redes Sociais**
- Botão Facebook: https://www.facebook.com/clinivetijui/
- Botão Instagram: https://www.instagram.com/clinivetijui/

**Links de documentos**
- Política de Privacidade (link para `politica.html`)
- Formulário de Cessão de Dados (link para `formulario.pdf`)

### Rodapé
- Logo grande centralizado (opacidade reduzida)
- "© 2026 Clinivet. Todos os direitos reservados."
- Link discreto: "Contato técnico: knebel.inf.br" (href `https://knebel.inf.br`, abre em nova aba)

## politica.html — Conteúdo

### Header
- Fundo `#314230`
- Link "Voltar ao início" (leva para `index.html`)
- Logo menor à direita

### Conteúdo (mesmo container centralizado)

**Política de Privacidade**
- Parágrafo explicando que a Clinivet coleta dados para atendimento veterinário
- Referência à LGPD (Lei nº 13.709/2018)
- Instrução para acessar o PDF completo

**Seus direitos (LGPD)**
- Acesso aos seus dados
- Correção de dados incorretos
- Solicitação de exclusão
- Portabilidade dos dados

**Botões**
- "Ver documento completo (PDF)" — link para `politica.pdf`
- "Formulário de Cessão" — link para `formulario.pdf`

**Contato para exercer direitos**
- Texto discreto: "(55) 3332-2538 ou (55) 98177-8017"

### Rodapé
- Mesmo rodapé do `index.html`

## Decisões Técnicas

- HTML estático puro, sem frameworks ou build steps
- CSS inline no `<style>` do `<head>` (padrão do projeto atual)
- Google Fonts: Montserrat (já referenciado)
- Font Awesome 4.7 para ícones sociais (já referenciado)
- Deploy automático via GitHub Actions para GitHub Pages (workflow existente em `.github/workflows/static.yml`)
- Nenhuma dependência nova

## Restrições

- Sem JavaScript além do estritamente necessário
- Sem travessões (usar vírgulas ou dois pontos como separador)
- Sem emojis de IA ou linguagem promocional excessiva
- Logo `logo.png` deve aparecer no hero e também grande no rodapé

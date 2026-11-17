# HyperAcess – Mapeamento Urbano Inclusivo

**SÃO PAULO E REGIÃO METROPOLITANA • DOCUMENTAÇÃO DE PROJETO E CÓDIGO**

**Curso:** Análise e Desenvolvimento de Sistemas / Ciência da Computação / Engenharia — UNICID (2026)

O HyperAcess é uma solução digital concebida para o mapeamento colaborativo de calçadas, sinalizações e barreiras urbanas voltada para pessoas com limitações visuais, auditivas, de mobilidade e idosos. O sistema visa garantir maior autonomia, segurança e agilidade no trânsito de pedestres, permitindo que a própria comunidade reporte obstáculos e que a plataforma calcule rotas acessíveis e emita alertas sonoros/visuais por GPS em tempo real.

## Integrantes do Grupo e Funções

| Integrante | RA / Turma | Função / Responsabilidade no Projeto |
|---|---|---|
| Lucas de Moraes Covelo | 47563923<br>2260030/N8-2 | Líder de Projeto & Arquiteto de Software: Definição do escopo, estrutura de navegação, arquitetura SPA e integração do sistema de geolocalização. |
| Pedro Henrique de Oliveira | 47487909<br>UNICID ADS | Desenvolvedor Front-End & Especialista WCAG: Implementação das diretrizes de acessibilidade (alto contraste, modo daltonismo, leitura audível e foco via teclado). |
| Marcos Vinicius Calixto Emerenciano | 47411996<br>UNICID ADS | Desenvolvedor Front-End & Engenharia de Dados: Desenvolvimento dos módulos de chamados, lógica de recomendação de rotas e integração com Leaflet.js. |
| Nathan Cauê Sanchez Martins | 47458984<br>UNICID ADS | Desenvolvedor Front-End & Módulos JavaScript: Implementação de armazenamento no `localStorage`, assistente virtual/chatbot e simuladores de feedback háptico e áudio. |

## Objetivos da Plataforma

- **Reduzir o tempo de locomoção:** Cálculo de trajetos inteligentes que contornam vias danificadas ou com barreiras físicas.
- **Mapear a infraestrutura deficitária:** Diagnóstico colaborativo em tempo real das barreiras arquitetônicas da cidade.
- **Garantir a qualidade e segurança no trânsito:** Prevenção de acidentes e quedas de pedestres vulneráveis.
- **Promover a inclusão social:** Aplicação rigorosa das diretrizes WCAG 2.1 para dar plena autonomia digital e urbana.

## Por que este projeto é vital em larga escala?

1. **Gestão Pública Inteligente (Crowdsourcing):** O acúmulo de relatos gera mapas de calor (heatmaps) permitindo que secretarias de obras priorizem a manutenção de calçadas onde o impacto social é mais severo.
2. **Cumprimento da Legislação e ODS da ONU:** Alinha a cidade à Lei Brasileira de Inclusão (Lei nº 13.146/2015), à NBR 9050 e aos Objetivos da ONU (ODS 11 - Cidades Sustentáveis, ODS 10 - Redução das Desigualdades e ODS 3 - Saúde e Bem-Estar).

## Evolução Técnica do Código: Versão Inicial vs. Versão Final

Abaixo apresentamos a comparação detalhada e prática entre a versão inicial estática (`Projeto em css.txt`) e a aplicação consolidada (`PROJETO FINAL CODIGO`).

| Código Inicial (Projeto em css.txt) | Código Final (PROJETO FINAL CODIGO) |
|---|---|
| Arquivo estático CSS/HTML com múltiplas páginas. | Aplicação SPA Dinâmica (Single Page Application) em único arquivo. |
| Estilização visual rígida e cores fixas sem variáveis. | Sistema de design baseado em CSS Custom Properties (`:root`). |
| Sem interatividade JavaScript ou resposta de hardware. | Leaflet.js + APIs nativas (Web Speech, Vibration, Geolocation). |
| Layout sem acessibilidade dedicada ou suporte a leitor. | Acessibilidade WCAG 2.1 (Alto Contraste, Modo Daltonismo e ARIA). |

## Comparações Práticas de Código (Antes vs. Depois)

### 1. Estilização e Temas Dinâmicos (CSS)

**Antes (Projeto em css.txt):** Estilos fixos sem suporte a alto contraste.

```css
/* Código antigo: Sem variáveis, exigia alterar múltiplos seletores */
body {
    background-color: #ffffff;
    color: #333333;
}

.botao-alerta {
    background-color: #ff0000;
    color: #ffffff;
}
```

**Depois (PROJETO FINAL CODIGO):** Sistema flexível com CSS Custom Properties.

```css
/* Código novo: Alteração de tema com 1 única classe no <html> */
:root {
    --bg-primary: #ffffff;
    --text-primary: #1e293b;
    --btn-danger: #ef4444;
}

html.alto-contraste {
    --bg-primary: #000000;
    --text-primary: #ffff00;
    --btn-danger: #ff0000;
}

body {
    background: var(--bg-primary);
    color: var(--text-primary);
}
```

### 2. Semântica e Acessibilidade (HTML5)

**Antes:** Divs genéricas sem informação visual ou audível.

```html
<!-- Código antigo -->
<div class="box" onclick="abrir()">
    <span>Reportar Buraco</span>
</div>
```

**Depois:** HTML5 Semântico com suporte a Leitores de Tela e Foco Teclado.

```html
<!-- Código novo: Acessível por voz, teclado e leitores de tela -->
<button class="btn-chamado" aria-label="Reportar buraco ou obstáculo na calçada">
    <span aria-hidden="true">⚠️</span>
    Reportar Buraco
</button>
```

### 3. Recursos Avançados e Web APIs (JavaScript)

**Antes:** Sem código JavaScript (Página puramente estática).

```javascript
/* O projeto inicial não contava com arquivos de script ou tratamento de eventos */
```

**Depois:** Síntese de Voz, Vibração Háptica e Geolocalização Nativas.

```javascript
// Código novo: Síntese de voz (Web Speech API) e Vibração (Vibration API)
function alertarObstaculo(mensagem) {
    // 1. Alerta audível para deficientes visuais
    if ('speechSynthesis' in window) {
        const fala = new SpeechSynthesisUtterance(mensagem);
        fala.lang = 'pt-BR';
        window.speechSynthesis.speak(fala);
    }

    // 2. Feedback por vibração no celular
    if ('vibrate' in navigator) {
        navigator.vibrate([200, 100, 200]); // Pulsos de alerta
    }
}

// 3. Persistência de preferências de acessibilidade
function salvarPreferencias(tema) {
    localStorage.setItem('hyperacess_tema', tema);
    document.documentElement.className = tema;
}
```

## Tecnologias Utilizadas na Solução Final

| Tecnologia | Camada | Descrição / Aplicação |
|---|---|---|
| HTML5 Semântico | Estruturação | Inclusão de marcos semânticos, atributos ARIA e suporte completo a leitores de tela. |
| CSS3 Moderno | Estilização | CSS Custom Properties (`:root`), Flexbox, Grid e regras de acessibilidade de alto contraste. |
| JavaScript (ES6+) | Lógica & DOM | Manipulação de estado, persistência em `localStorage` e assistente virtual. |
| Leaflet.js | Mapeamento | Renderização de mapas interativos, rotas e inclusão de pontos de obstáculo. |
| Web APIs Nativas | Integração Hardware | Web Speech API (síntese de voz), Vibration API (resposta tátil) e Geolocation API. |

---

**HyperAcess — Documentação Técnica**

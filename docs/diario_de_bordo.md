# Diário de Bordo — HyperAcess

**Projeto:** HyperAcess — Mapeamento Urbano Inclusivo de São Paulo e Grande ABC
**Disciplina:** Desenvolvimento Front-End — UNICID — 2º semestre de 2026
**Entrega:** AV A1 — 2ª entrega (projeto final), com apresentação marcada para 17/11/2026

| Integrante | RA / RGM | Papel no projeto |
|---|---|---|
| Lucas de Moraes Covelo | 47563923 | Coordenação, escopo, arquitetura, interface e documentação |
| Pedro Henrique de Oliveira | 47487909 | Acessibilidade, JavaScript, assistente virtual e voz |
| Marcos Vinicius Calixto Emerenciano | 47411996 | Layout responsivo, CSS, mapa de satélite e publicação |
| Nathan Caue Sanchez Martins | 47458984 | Front-End e módulos JavaScript: armazenamento no localStorage |

---

## Como usamos a Inteligência Artificial

O professor pediu que a gente usasse IA no projeto, mas sabendo o que ela estava fazendo. Por isso, usamos a IA (Claude) para melhorar o código e criar novas funções, sempre com uma regra: só entrava no site o que nós entendíamos e testávamos. Em várias etapas recusamos sugestões ou pedimos para refazer. Esses momentos estão registrados ao longo deste diário, em cada data.

---

## Outubro de 2026 — O começo do projeto

### 15/10/2026 — Criação do repositório

Nós começamos o projeto criando o repositório no GitHub. O Lucas fez o primeiro commit ("Initial commit"). Nesse dia, nosso grupo decidiu o tema: mapear calçadas danificadas, falta de rampas, piso tátil e sinalização, para ajudar pessoas com deficiência e idosos a se locomoverem com mais segurança em São Paulo.

### 16/10/2026 — Escopo do projeto

O Lucas escreveu o README com o escopo. Definimos:

- o problema;
- o público-alvo;
- o stakeholder principal (Prefeitura de São Paulo);
- os objetivos;
- a lista das 10 páginas que o site deveria ter.

Esse escopo virou a nossa referência para todas as etapas seguintes.

### 20/10/2026 — Primeira versão enviada

O Marcos enviou a primeira versão do site. Identificamos logo um problema: os arquivos subiram como `index.html.txt` e `pasta css/style.css.txt`. Com a extensão `.txt`, o navegador não abria nada como página.

### 21/10/2026 — Correção dos arquivos

O Lucas apagou o `index.html.txt` duplicado. Aprendemos que a extensão do arquivo faz toda a diferença na hora de publicar.

### 26/10/2026 — Entrega do MVP (1ª entrega)

O Marcos enviou o `index.html` e o `style.css` corretos, e entregamos o MVP. A página tinha:

- barra de acessibilidade;
- mapa do OpenStreetMap em iframe;
- cards de ocorrências;
- um formulário.

Depois da entrega, olhando com calma, identificamos a necessidade de melhorar vários pontos:

- o site tinha uma página só, com dois links no menu;
- os botões A+, A- e Alto Contraste não funcionavam, porque não tinham JavaScript;
- a validação do formulário só pintava a borda de vermelho, sem dizer qual era o erro;
- no celular, aparecia uma faixa amarela no topo, que era o link "Ir para o conteúdo";
- o CSS estava repetido em mais de um lugar.

### 27/10/2026 — O site vira uma página única (SPA)

O Pedro transformou o site em uma página única, com 10 seções trocadas por JavaScript. Também entraram um chatbot, leitura em voz alta e modo daltonismo. Foi a primeira vez que as 10 páginas do escopo apareceram no site.

Mais tarde percebemos que essa versão tinha problemas que precisaríamos corrigir:

- o chatbot pedia a chave da OpenAI e a guardava no navegador;
- alguns textos diziam "plataforma oficial" e outras coisas que não eram verdade.

---

## Novembro de 2026 — Evolução e ajustes

### 02/11 e 03/11/2026 — Ajustes na SPA

O Pedro e o Marcos fizeram várias atualizações no `index.html`. Ampliaram o mapa de satélite e incluíram as regiões do ABC. O Pedro também enviou a pasta "trabalho terça 3", com a versão "Portal Cidadão SP".

### 03/11/2026 — Responsividade para celular (com IA)

Notamos que o site não se ajustava bem ao celular. O Lucas pediu à IA:

> "Com base no escopo, preciso que faça alterações de modo que o site se ajuste automaticamente para ecrãs de tela de celular."

Fizemos algumas alterações a partir disso:

- media queries para telas de 768 px e 480 px;
- botões maiores, fáceis de tocar;
- campos com letra de 16 px, para o iPhone não dar zoom sozinho;
- correção da faixa amarela no topo do celular.

Testamos em várias larguras de tela, sem rolagem para o lado. Na mesma data, o Lucas também testou com a IA uma versão do site com as 10 páginas em arquivos separados.

### Início de novembro — Problema na publicação

Nesse período tivemos um susto: o site publicado abriu sem CSS e sem JavaScript, todo desconfigurado. Descobrimos que o código tinha sido enviado ao GitHub como um único arquivo de texto, sem extensão. Corrigimos enviando os arquivos reais na raiz do repositório. Foi o mesmo aprendizado de 20/10: o formato do arquivo importa.

### 05/11/2026 — Primeiro pacote da 2ª entrega (com IA)

O Lucas mandou para a IA o roteiro do professor e o código da versão "Portal Cidadão SP". Juntamos o melhor das versões e montamos um primeiro pacote de entrega, com documentação, slides e prints.

Nessa etapa, nosso grupo decidiu recusar duas sugestões que vinham da versão anterior:

- **Guardar a chave da OpenAI no navegador:** qualquer script da página conseguiria ler a chave. O assistente passou a responder só com JavaScript, por palavras-chave.
- **Textos "plataforma oficial" e "Google Maps Platform":** não eram verdade, então foram retirados.

### 06/11/2026 — Decisão pela SPA e melhorias (com IA)

Comparamos as versões, e nosso grupo decidiu manter a SPA como base. Era a versão que vínhamos desenvolvendo, e a troca de página era instantânea.

Pedimos à IA para melhorar o código "sem sair do padrão". Depois perguntamos se a ordem das páginas seguia exatamente o escopo. Fizemos as seguintes melhorias:

- **Navegação:** cada página ganhou endereço próprio (`#pag-1` a `#pag-10`), e o botão Voltar do navegador passou a funcionar.
- **Escopo:** as 10 páginas ficaram na ordem e com os nomes do escopo.
- **Celular:** menu em gaveta, com os botões de acessibilidade no topo.
- **Formulários:** mensagem de erro em cada campo e rascunho salvo automaticamente.
- **Itens de ONG:** notícias com filtro, voluntariado, apoio simulado, vídeo legendado, áudio e mapa em iframe.
- **Rotas e alertas:** rotas comparando 3 trajetos; alertas por bipe, voz, vibração e aviso visual.
- **Textos:** retiramos frases como "criptografia HTTPS ativa" e "WCAG AAA garantido", que não eram verdade.

### 07/11/2026 — Correções, documentação e requisitos a mais (com IA)

Revisando o site, identificamos que, no modo Alto Contraste, o botão "Registrar uma Ocorrência" ficava amarelo sobre amarelo, impossível de ler. Corrigimos para texto preto. Também ajustamos textos antigos, que ainda citavam "Alertas GPS" e a página "Contato".

Montamos o pacote completo da entrega:

- documentação na pasta `/docs`: escopo, diário de bordo, orçamento de hospedagem, testes, melhorias do MVP e uso de IA;
- regras de IA na pasta `.cursor/rules`;
- 14 slides, prints, `integrantes.txt` e `links.txt`;
- um passo a passo para os commits, a branch e o pull request.

Como queríamos ir além do pedido, adicionamos requisitos a mais:

- as 10 páginas em arquivos HTML separados;
- modo escuro;
- gráficos de estatísticas;
- funcionamento sem internet, com opção de instalar como aplicativo.

Aqui também recusamos sugestões:

- **Guardar o vídeo no cache para usar sem internet:** o player poderia travar.
- **Gráficos com uma biblioteca externa:** fizemos as barras em HTML e CSS, que funcionam sem internet.

### Entre 07/11 e 14/11/2026 — Nova versão do site (Lucas e Pedro)

Nesse período, o Lucas e o Pedro reformularam o site e criaram o arquivo `PROJETO_FINAL_CODIGO1`, que se tornou a nossa versão final. O Lucas refez a interface, com visual azul-marinho, e o site ganhou:

- mapa de satélite híbrido, no estilo Google Earth;
- vídeo demonstrativo animado, com narração e legendas;
- novo assistente de IA no chat.

A apresentação, que estava marcada para 09/11, foi remarcada para 17/11. Com isso, ganhamos tempo para continuar melhorando o site.

### 14/11/2026 — Acessibilidade, equipe, mapa e e-mail (com IA)

**Daltonismo e narração.** Identificamos a necessidade de melhorar o daltonismo e a narração por IA. Pedimos:

- **Daltonismo em três tipos:** Protanopia, Deuteranopia e Tritanopia. Cada clique no botão passa para o próximo tipo. Como a plataforma é azul, quase nada muda na protanopia e na deuteranopia; a maior mudança fica na tritanopia, onde o azul vira grafite com ciano.
- **Narração em um único botão:** antes era preciso clicar em "parar" depois de ativar. Agora um clique liga e outro desliga.
- **Mapa:** a IA só fala ao clicar num marcador se a narração estiver ligada.

**Uma resposta que pedimos para refazer.** A primeira versão dessas mudanças alterou muito mais do código do que tínhamos pedido. Não aceitamos: pedimos para voltar ao nosso arquivo original, no mesmo formato, e mexer só no que foi pedido. Esse foi um dos momentos em que mais aplicamos a orientação do professor de usar a IA sabendo o que ela está fazendo.

**Celular, equipe, mapa e contato.** No mesmo dia:

- **Celular:** verificamos o site de 320 a 768 px. Funcionou bem; só a lista de regiões do mapa passava da tela em celulares muito pequenos, e corrigimos.
- **Equipe:** colocamos o Nathan na tabela da página 2, no mesmo padrão dos outros integrantes. Ele estava no grupo desde o início, cuidando do armazenamento no localStorage. Corrigimos também a grafia do sobrenome para "Martins".
- **Mapa — marcação:** o usuário escolhe o sinalizador do defeito (B, R, P, S ou O) e toca no local exato. A marcação fica salva no navegador.
- **Mapa — regiões:** ao escolher uma região, a visão de satélite vai direto para ela, e aparece a lista de chamados abertos daquela região.
- **Contato:** o formulário passou a exigir um e-mail válido e a enviar a mensagem de verdade, com cópia para o usuário.

### 15/11/2026 — Perfil, ONGs e Fale Conosco (com IA)

Primeiro, confirmamos que o site usa localStorage e aprendemos a ver os dados: F12 › Application › Local Storage. Lá estão guardadas:

- as preferências de acessibilidade;
- o perfil;
- os chamados;
- o rascunho do formulário;
- as marcações do mapa.

Depois fizemos estas alterações:

- **Perfil (página 7):** novos campos de telefone e e-mail.
  - O telefone precisa ser de São Paulo (DDD 11 a 19), celular ou fixo, e é formatado enquanto a pessoa digita.
  - O e-mail precisa ser válido e de um provedor conhecido, como Gmail, Outlook ou Hotmail.
- **ONGs (página 9):** criamos uma área convidando ONGs a se unirem a nós por uma causa melhor. Ela tem duas opções: parceria para divulgar o site e apoio por transferência, com uma chave PIX. Preferimos não colocar dados bancários inventados: banco, agência e conta são enviados pela equipe quando alguém pedir.
- **Fale Conosco (página 10):**
  - Toda mensagem vai para o e-mail de suporte `suportehyperacess@gmail.com`.
  - O remetente é o e-mail cadastrado no Perfil; quem não tem e-mail cadastrado aparece como "Anônimo".
  - O e-mail chega com o protocolo da chamada, o tipo de mensagem (Sugestão de Melhoria, Denúncia e as outras opções) e a mensagem escrita.
- **Ditado por voz:** incluímos a opção de falar a mensagem pelo microfone do computador ou do celular.

### 16/11/2026 — Documentação do progresso

Reunimos todo o histórico do site em uma documentação e revisamos este diário de bordo, para mostrar com clareza como o projeto evoluiu do MVP até a versão final.

### 17/11/2026 — Apresentação (planejado)

Para a apresentação, ainda precisamos:

- [ ] Publicar a versão final no GitHub Pages.
- [ ] Ativar o envio de e-mail do FormSubmit em `suportehyperacess@gmail.com`.
- [ ] Confirmar a chave PIX da área de ONGs.
- [ ] Garantir os commits de todos os integrantes e o pull request.
- [ ] Fazer o teste final no celular e no computador antes de apresentar.

---

## O que aprendemos

| Dificuldade | Como resolvemos |
|---|---|
| Arquivos enviados como `.txt` ou sem extensão | Passamos a conferir a extensão e a estrutura de pastas antes de publicar |
| Botões de acessibilidade que não funcionavam | Adicionamos JavaScript e passamos a salvar as preferências no localStorage |
| Site difícil de usar no celular | Fizemos o layout responsivo e o menu em gaveta |
| Chave de API exposta no navegador | Fizemos um assistente que funciona sem chave |
| Textos que não eram verdade | Retiramos e colocamos avisos de projeto acadêmico |
| IA alterando mais do que pedimos | Pedimos para refazer, mexendo só no que foi solicitado |

A maior lição que tiramos é que acessibilidade precisa ser pensada desde o começo, e não acrescentada no fim. Também aprendemos que a IA ajuda muito quando sabemos exatamente o que pedir e conferimos o resultado antes de aceitar.

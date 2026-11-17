# Melhorias de acessibilidade, rotas, mapa e contato no HyperAcess

**Branch:** `versao-final` → `main`
**Arquivo alterado:** `index.html` (antes `PROJETO_FINAL_CODIGO1`)
**Tamanho da mudança:** 745 linhas adicionadas e 62 removidas (de 2.472 para 3.155 linhas)

## Resumo

Este PR sugere melhorias para a versão do site enviada em 14/11/2026. O visual, a estrutura e as 10 páginas continuam iguais. As mudanças corrigem funções que não respondiam, deixam a acessibilidade mais completa e fazem o formulário de contato enviar e-mails de verdade.

## Por que mudar

Testando a versão original, encontramos estes pontos:

- O botão **"Comparar 3 Trajetos"** (página 5) não tinha nenhum código ligado a ele: mudar a partida ou o destino não atualizava nada.
- O **Daltonismo** tinha um único modo, sem diferenciar os tipos de daltonismo.
- A **narração por IA** tinha comportamento confuso: depois de ligar, era preciso clicar em "parar", e o botão voltava a "Ouvir IA" sozinho.
- O **Fale Conosco** só mostrava "mensagem enviada" na tela, mas nenhum e-mail chegava a ninguém.
- O **mapa** não deixava o usuário marcar um problema, e trocar a região não levava a visão até ela.
- Faltavam o **quarto integrante** na equipe, **fontes oficiais** sobre o público do site e uma área para **ONGs**.
- No celular de 320 px, a lista de regiões do mapa passava da largura da tela.

## O que mudou

### Acessibilidade

- **Daltonismo em 3 tipos:** o botão agora troca entre Desligado, Protanopia, Deuteranopia e Tritanopia. A escolha fica salva no `localStorage` (`ha_daltonismo`).
  - Os marcadores do mapa, a legenda e o gráfico mudam de cor.
  - Na tritanopia, a interface também troca o azul por grafite e ciano.
  - Todas as cores têm contraste de pelo menos 4,5:1 com o texto branco.
- **Narração por IA em um botão só:** um clique liga, outro desliga e para a fala na hora (`iaVozAtiva`).
- **Fala no mapa e nas rotas:** só acontece com a narração ligada.

### Página 2 — Quem Somos

- Incluído o quarto integrante, Nathan Cauê Sanchez Martins (RGM 47458984), no mesmo padrão da tabela.
- O assistente de IA passa a citá-lo quando perguntam sobre a equipe.

### Página 3 — Mapa

- **Marcação manual:** o usuário escolhe o sinalizador (B, R, P, S, O) e toca no local do problema. Há também a opção "Marcar no centro do mapa". As marcações ficam salvas em `ha_marcacoes`.
- **Voo até a região:** ao escolher uma região, a visão de satélite vai direto para ela.
- **Chamados da região:** aparece a lista de chamados abertos naquela região.

### Página 5 — Rotas

- O comparador agora calcula 3 trajetos para qualquer partida e destino. Os danos são fictícios e pesam conforme o perfil (cadeirante, deficiência visual ou idoso).
- A tela mostra a **Rota Recomendada**, a **Rota Moderada** e a **Pior Rota**, cada uma com porcentagem de acessibilidade, tempo e distância.
- A mesma combinação de partida, destino e perfil dá sempre o mesmo resultado.
- Campos vazios ou iguais mostram um aviso, e o texto digitado é escapado antes de aparecer na tela.

### Página 7 — Perfil

- **Telefone:** só aceita número do estado de SP (DDD 11 a 19, celular ou fixo), formatado enquanto a pessoa digita.
- **E-mail:** só aceita endereço válido de provedores conhecidos (Gmail, Outlook, Hotmail etc.) ou institucional (.edu.br e .gov.br).
- O perfil salvo volta preenchido ao abrir a página.

### Página 9 — Ajuda

- Iframe com o vídeo oficial do IBGE sobre o envelhecimento da população (Censo 2022).
- Quadro de fontes oficiais:
  - pesquisa do IBGE sobre pessoas com deficiência;
  - notícia da Agência Brasil;
  - notícia da Agência IBGE.
- Área para ONGs: convite para parceria de divulgação e apoio por transferência, com botão para copiar a chave PIX.

### Página 10 — Fale Conosco

- As mensagens são enviadas de verdade para `suportehyperacess@gmail.com` pelo FormSubmit.
- O remetente é o e-mail do Perfil. Sem e-mail cadastrado, aparece "Anônimo".
- O e-mail chega com Protocolo (`HA-SUP-AAAAMMDD-NNNN`), Remetente, Tipo de mensagem, Nome e Mensagem.
- Novos tipos de mensagem: Sugestão de Melhoria e Denúncia.
- **Ditado por voz:** o microfone do computador ou do celular escreve a mensagem.

### Celular

- A lista de regiões do mapa não passa mais da largura da tela.
- Testado de 320 a 1366 px sem rolagem para o lado.

## Como testar

1. Abra o site pelo link do GitHub Pages. O e-mail e o microfone precisam de HTTPS.
2. **Daltonismo:** clique no botão várias vezes e veja as cores do mapa (página 3) e do gráfico (página 8) mudarem.
3. **Narração:** abra o chat, ligue a "Narração IA" e faça uma pergunta. Desligue e confira que ela para na hora.
4. **Rotas:** na página 5, troque a partida e o destino e clique em "Comparar 3 Trajetos". Os três cartões devem mudar.
5. **Mapa:** na página 3, escolha uma região e veja o mapa voar até ela. Depois escolha um sinalizador, clique em "Marcar no mapa" e toque num ponto.
6. **Perfil:** tente salvar `(21) 91234-5678` (deve recusar) e depois `(11) 91234-5678` (deve aceitar).
7. **Contato:** envie uma mensagem com e-mail no Perfil e outra sem. Confira em `suportehyperacess@gmail.com` se a segunda chega como "Anônimo".
8. **Ditado:** toque em "🎤 Falar a mensagem", fale uma frase e veja o texto aparecer.
9. **Celular:** abra no DevTools com 360 px de largura e navegue pelas 10 páginas.

## Pontos de atenção

- **FormSubmit:** no primeiro envio, chega um e-mail de ativação em `suportehyperacess@gmail.com`. É preciso clicar em "Activate" uma vez.
- **Chave PIX:** `suportehyperacess@gmail.com` precisa ser cadastrado como chave PIX no banco, ou trocado pela chave real da equipe.
- **Rotas:** os danos são fictícios, só para demonstração. O site avisa isso na tela.
- **Dados locais:** os dados do usuário ficam só no `localStorage` do aparelho, sem servidor.

## O que não mudou

- Identidade visual: cores, fontes, cartões e layout.
- As 10 páginas e o menu.
- O vídeo demonstrativo animado, os alertas da página 6 e o botão "Ouvir Página".

## Sugestões para um próximo PR

- [ ] Atualizar a pergunta 4 do FAQ, que ainda cita o botão antigo "Ouvir / Pausar IA".
- [ ] Remover os arquivos antigos do repositório: `style.css` e `pasta css/style.css.txt`.
- [ ] Rodar o W3C Validator e o Lighthouse no link publicado e registrar os resultados.
- [ ] Criar um banco de dados e login, para os chamados serem compartilhados entre usuários.

## Checklist

- [x] Mantém a identidade visual e as 10 páginas
- [x] Testado no computador e no celular (320 a 1366 px), sem erros de JavaScript
- [x] Verificação de HTML local sem problemas
- [x] Textos digitados pelo usuário escapados antes de aparecer na tela
- [x] Documentação atualizada (diário de bordo, histórico e guia de estudo do código)
- [ ] Revisado e aprovado por outro integrante

## 7.36 — Nova logo e ícones (25/11/2026)
- Logo nova (símbolo predominantemente branco, leve gradiente lilás, relevo e Liquid Glass) em: ícone do app (192/512), ícone recortável do Android (maskable), ícone do iPhone (apple-touch), favicons 32/48, notificações e a logo da tela Sobre. Nomes dos arquivos e manifesto iguais.
- Contraste medido (símbolo × fundo): 10,8→14,9:1 no ícone 512; 6,9→10,8:1 no maskable; 8,2→12,8:1 no apple-touch; 9,8→14,2:1 no favicon 48.
- O APK instalado guarda o ícone antigo: para o novo aparecer na tela inicial, gere um APK novo no PWABuilder (mesma chave) e reinstale. No PWA do navegador, remova o atalho e adicione de novo.

## 7.35 — Otimização: mascote carregado só quando necessário (25/11/2026)
- Com o Wolfin desligado, a Home deixa de baixar o pacote de imagens do mascote (≈690 KB → 0). Ao ligar o Wolfin, abrir a Loja ou ver WolfCoins, o pacote é baixado na hora, como antes. Nada muda na aparência, nas animações ou nos dados.
- Auditoria (sem alteração de código): cálculos, conciliação, backup/importação, armazenamento e PWA foram revisados e testados; navegação medida com 2.000 lançamentos fictícios (3 a 96 ms por aba) e sem vazamento de listeners.

## 7.34 — Conferir meu saldo, Home simplificada e mascote sem botão flutuante (24/11/2026)
- **Conferir meu saldo** (Home → ⓘ, ou Configurações → Contas e saldos): você informa o dinheiro que tem, a data e uma observação. O Wolfin guarda só um *ajuste de conferência* (não é receita, não é despesa, não muda os totais do mês nem apaga lançamento). Repetir o mesmo valor não duplica. Dá para corrigir ou desfazer a última conferência; o histórico fica guardado. Novas movimentações depois da data continuam alterando o saldo.
- O Wolfin não acessa o banco: o saldo depende do que você registra e informa.
- **Home**: só "Saldo atual" e "Saldo previsto até o fim do mês". O botão ⓘ mostra Recebido, Pago, A receber, A pagar, Origem do saldo e Histórico de conferências.
- Avisos: "Você possui dinheiro disponível, mas seus próximos compromissos podem ultrapassar esse valor." / "Seu saldo registrado está negativo. Confira suas movimentações." / "Você possui compromissos atrasados que precisam de atenção."
- **Mascote**: botão flutuante da sacola removido. Ligado: tocar no Wolfin abre a Loja. Desligado: só o texto, sem buracos. Chave e acesso à Loja em Configurações → "Wolfin, o mascote".
- Dados: novo campo opcional `recon` (lista de conferências). Backups antigos continuam abrindo (viram lista vazia).

## 7.30 a 7.33 — resumo (24/11/2026)
- 7.30: "Minha situação financeira" com 4 níveis e mascotes por nível.
- 7.31: chave do mascote só na Loja; "Jeito de falar" removido.
- 7.32: saldo atual × saldo previsto; regra da data de abertura; "Contas e saldos" em Configurações.
- 7.33: ícone da Loja com o mascote desligado (substituído na 7.34).
(Resumo refeito em 25/11/2026; os textos detalhados originais dessas quatro versões não foram preservados.)

## 7.29 — Identidade Midnight Violet + Liquid Glass (23/11/2026)
- **Intro removida:** sem animação/splash; o app vai direto para boas-vindas, login ou Home. Os vídeos `intro-lobo.*` saíram (pode apagá-los do GitHub). O service worker continua pronto para a nova intro.
- **Nova logo e ícones PWA:** `icon-192/512`, `icon-maskable-512` (símbolo isolado sobre fundo violeta, dentro da zona segura do Android), `apple-touch-icon`, `favicon-32/48` e a logo da tela Sobre. Cache do service worker subiu para a versão 7 para trocar a imagem antiga. **No Android, o ícone da tela inicial só muda se você remover o atalho e adicionar de novo.**
- **Paleta Midnight Violet** no lugar da Pérola (padrão para novos usuários); as outras 8 paletas continuam. Quem usava Pérola passa para Midnight Violet (a Pérola deixou de existir). Quem usa outra cor/tema não é alterado.
- **Tema escuro inicial** só para novos usuários (e a escolha segue disponível no início e em Configurações).
- **Novo mascote Padrão** (corpo inteiro + busto, em `wolfin-brasil.js`): estilo inicial, gratuito, 1º da Loja. Brasil e os demais continuam. Quem ainda estava no Brasil (o padrão antigo) vai uma única vez para o Padrão; depois a escolha é sempre respeitada.
- Gerador: `tests/tools/gerar_estilo_padrao.py`. Testes: `sem_intro_logo` reescrita (30 verificações), `tema_perola` agora cobre a Midnight Violet.

## 7.28 (correção) — Correção da tela em branco ao abrir (23/11/2026)
- **Bug:** depois de escolher um personagem na Loja (modo de testes libera todos), ao fechar e reabrir o app só aparecia o fundo, e recarregar não resolvia (o dado ficava salvo). Causa: `WF_ALL_FREE`/`WLOOKS`/`WF_STY` eram lidos na abertura antes de serem criados.
- **Correção:** essas constantes foram para o topo do script; `wcEnsure` aceita dados de WolfCoins corrompidos; a abertura não trava mais se a checagem de conquistas falhar.
- Testes novos: `wolfin_estilos` itens 20 e 21 (reabrir com estilo equipado e com dados corrompidos).

# Wolfin no GitHub Pages — notícias que se atualizam sozinhas

Com este pacote, o site fica num endereço próprio (`https://SEU-USUARIO.github.io/wallstreet/`) e o GitHub
busca as notícias sozinho a cada 3 horas, de graça. Você só faz isso uma vez.

## Versão 7.28 · Mascote na Home, Loja e WolfCoins
- **Cartão do mascote na Home:** busto à esquerda, sem círculo nem moldura, com a cabeça passando discretamente da borda de cima; texto dinâmico à direita e ícone de informações mantido. Usa o mascote escolhido. **Tocar no mascote abre a Loja** (selo de sacola e animação ao toque).
- **Versões "vendado" removidas** (imagens, opções e código). Só existem **corpo inteiro e busto** por estilo. **Árabe** agora completo (corpo inteiro + busto) e liberado.
- **Animações sutis** (CSS leve): respiração e leve inclinação do busto; fumaça no Tyler; brilho em correntes (Brasil, Cafetão, Tommy, CJ). Pausam fora da tela e respeitam movimento reduzido. Piscar/orelhas/cauda **não** são possíveis com imagens únicas (exigiriam camadas separadas) — só o Brasil tem camadas.
- **Configurações:** página secundária, sem barra inferior, cabeçalho fixo com botão Voltar (o Voltar do Android também funciona). O botão "Loja do Wolfin" saiu de lá.
- **Loja do Wolfin:** cabeçalho com Voltar, título e saldo; abas Personagens / Desbloqueados / Para desbloquear; cada cartão mostra prévia, nome, preço, estado (Disponível, Bloqueado, Desbloqueado, Equipado) e botão; seção "Ganhar WolfCoins" (desafios, conquistas e histórico).
- **WolfCoins:** conquista nova = +10; desafios (1ª receita, meta de economia, despesas com regularidade, tarefa concluída, primeiros compromissos) e desafio da semana; cada recompensa tem identificador único (sem duplicar), saldo/histórico persistem e entram no backup. Compra de personagem desconta o preço e registra no histórico.
- **Modo de testes:** constante única `WF_ALL_FREE=true` no index.html libera todos os personagens sem gastar moedas; desligar depois respeita o que foi comprado.
- Dados: `S.wc` já existia (n, tot, done, own, look, log); só ganhou novos identificadores em `done` e entradas no `log`.

## Versão 7.27 · Telas iniciais compactas
- **Boas-vindas:** Wolfin só em **busto** (usa o busto do estilo escolhido), com WOLFIN, slogan, título, mensagem, descrição curta, "Começar" e "Já tem conta? Entrar".
- **Como podemos te chamar? / Crie seu acesso / Proteger seus dados?:** sem mascote; ícone de vidro no lugar, título mais perto dos campos, menos espaços e botões logo abaixo do formulário. A tela de **Entrar** mantém o Wolfin que tampa os olhos ao ocultar a senha.
- Botão de tema deixou de ser fixo (rola junto e não sobrepõe o cartão); cartão com respiro no topo.
- Texto de segurança corrigido: dados criptografados neste aparelho (AES-GCM) e abrem com a senha **ou o código de recuperação**.
- Nada mudou em autenticação, criptografia, armazenamento, backups ou Home. Dados: sem mudanças.

## Versão 7.26 · Estilos do Wolfin
- **10 visuais** (Brasil, Shelby, Cafetão, Tommy, Meme, Kratos, Morgan, CJ, Tyler, Heisenberg) + **Árabe "Em breve"** (só tinha a imagem normal). Cada estilo tem 3 imagens: normal, mãos nos olhos e busto.
- **Tudo liberado por enquanto** (chave `WF_ALL_FREE` no index.html); a economia/preços em WolfCoins fica para depois.
- **Login/Criar acesso/boas-vindas:** Wolfin de corpo inteiro e maior; ao ocultar a senha ele troca para a imagem de mãos nos olhos. **Home:** avatar maior (64px) com o busto do estilo. Mais presença: estados vazios, tutorial (avatar 56px) e Loja com bustos.
- **Arquivos novos:** `wolfin-estilos.js` (9 estilos; carrega só quando necessário) e o trio do Brasil anexado em `wolfin-brasil.js`. Gerador: `tests/tools/gerar_wolfin_estilos.py`. `sw.js` versão 6.
- **Dados:** o visual escolhido continua em `S.wc.look` (já existia; agora aceita os novos ids) e é espelhado em `wallstreet.look` campo `w` para as telas de entrada. Backups e senhas continuam compatíveis.
- Os visuais não-Brasil são imagens estáticas (respiração leve); só o Brasil mantém piscar/falar. O aceno da tela inicial foi trocado por entrada suave.

## Versão 7.25 · Início reordenado e Wolfin animado
- Cadastro agora é: **tela inicial** (Wolfin acenando, breve explicação e botão **Começar** no meio, "Já tem conta? Entrar" embaixo) → **aparência** (etapa 1 de 3) → **nome** (2 de 3) → **senha** (3 de 3). Voltar percorre o mesmo caminho.
- Nas telas de **senha** e **login** o Wolfin aparece e **fecha os olhos** quando a senha está oculta; ao mostrar a senha ele abre os olhos e olha para baixo.
- Agora há **um único olho** em Criar acesso (e em Recuperar acesso): ele mostra/oculta a senha e a repetição ao mesmo tempo.
- Animações leves do mascote: entrada suave, aceno na tela inicial e expressões que variam sozinhas (desligam com "reduzir movimento").
- Sem mudança na estrutura de dados nem nos arquivos (continuam `index.html`, `sw.js`, `wolfin-brasil.js`, `tests.zip`).

## Versão 7.24 · Wolfin de volta, com WolfCoins
- O mascote **Wolfin (visual Brasil)** voltou: já vem liberado e em uso, sem comprar. Aparece na faixa de aviso da Home, nas boas-vindas, no tutorial, em Conquistas, em Avisos e em Ajustes. Piscar, respiração e cauda são animações leves em CSS (desligam com "reduzir movimento").
- Personalidade: tom **Malandro** (descolado, sarcástico) ou **Sereno**, escolha em Ajustes → Wolfin. Com saldo negativo ele sempre fala no tom acolhedor. Dá para esconder o mascote em Ajustes.
- **WolfCoins**: +10 por conquista e +1 por dia de visita (cada motivo só rende uma vez). **Loja do Wolfin** (Ajustes ou Conquistas): Brasil em uso; os outros visuais aparecem como "Em breve".
- Arquivos novos: `wolfin-brasil.js` (imagens do mascote) — precisa ser enviado junto com `index.html` e `sw.js`. Gerador: `tests/tools/gerar_wolfin_brasil.py`.
- Estrutura de dados: novo `S.wc` = `{n, tot, done, own, look, log}` e `S.pref.wf` = `{on, tone}` (criados só ao usar). Backups antigos continuam abrindo; chaves de armazenamento e senhas não mudaram.

## Versão 7.23 · Correção em Editar parcela
- Corrigido: ao marcar uma parcela pendente como **Pago**, mudar o mês e salvar sem data de pagamento, o 1º clique mostrava o erro mas já alterava a parcela; o 2º clique podia gravá-la como paga sem data. Agora **tudo é validado antes de alterar ou gravar**: sem data válida o pagamento novo é sempre bloqueado, e **Cancelar** após o erro deixa mês, vencimento, valor e status como estavam.
- Parcelas antigas já pagas sem data continuam editáveis (valor, mês) sem que o app invente data.
- Pagamento em mês diferente do vencimento continua entrando nos relatórios no mês do pagamento real. "Registrar pagamento" e o layout não mudaram. Sem mudança na estrutura de dados.

## Versão 7.22 · Redesign da Home (vidro nas cores do tema)
- Home refeita a partir da imagem de referência: cabeçalho com botões de vidro, busca, cartão de saldo azul iluminado com **Recebido** e **Pago**, aviso de saldo (toque abre Relatórios), atalhos Receita/Despesa/Guardar, Anotações, Cartões e Próximos compromissos.
- Todas as cores da Home seguem a cor do tema escolhido (nada de verde/vermelho fixos); a diferença entre receita e despesa fica nos ícones e textos.
- Informações secundárias ficaram em seções que abrem ao toque (nada foi removido): ⓘ no saldo (Guardado e dívidas, explicação) e "Mais informações" (receitas previstas, despesas fixas, caixinhas, dívidas, resumo do mês e Conquistas).
- O botão de olho (ocultar valores) agora fica **somente no cabeçalho da Home**; ocultar continua valendo no app todo.
- Barra inferior inalterada (6 abas). Nenhum mascote. Sem mudança nos dados, backups ou senhas.

## Versão 7.21 · Menu do perfil e visual de vidro restaurado
- **Ajustes saiu da barra inferior**: ficam 6 abas (Home, Receitas, Despesas, Dívidas, Caixinhas, Relat.), com o mesmo estilo de antes, distribuídas por igual.
- **A foto de perfil virou um botão**, só na Home (canto esquerdo); as outras abas não têm o botão. Ao tocar abre o menu com foto, nome e a situação da conta, e as opções **Meu perfil, Configurações, Aparência e temas, Privacidade e segurança, Backups**; cada uma abre a tela de Ajustes já existente, direto no cartão certo (sem páginas duplicadas). Tocar na foto dentro do menu troca/remove a foto.
- **Rodapé**: com senha ativada aparece **Sair da conta** (usa o mesmo bloqueio de "Bloquear agora"). Sem senha, aparece **Ativar proteção por senha**, porque não há sessão para encerrar.
- Fecha tocando fora, com Esc ou com o botão Voltar do Android (sem sair do app). Animação curta; respeita "reduzir movimento".
- **Vidro restaurado na Home**: o cartão de Saldo voltou a ser uma superfície de vidro azul (gradiente navy → azul profundo → azul vibrante, reflexos, borda luminosa, brilho interno), com cápsulas de vidro para Recebido/Pago/Guardado (ícones refinados). Receita/Despesa/Guardar viraram botões de vidro colorido (esmeralda, coral, azul) com ícones novos e efeito ao toque. Cartões, busca e avisos voltaram a usar o vidro original do app. Tudo usa as variáveis dos temas.
- O tutorial do primeiro acesso agora tem o passo "Seu perfil" (destaca a foto) no lugar de "Ajustes".
- Suba só **index.html** e **tests.zip** (sw.js e ícones não mudaram). Dados: nenhuma mudança de estrutura; chaves, backups e senhas continuam compatíveis.
- Limites: testado só em Chromium simulado (sem celular real nem TalkBack).

## Versão 7.20 · Home refinada (só visual)
- **Cabeçalho** mais baixo, com ícones de avisos, notícias e privacidade alinhados (alvos de 44 px, selo de avisos não lidos mantido) e **busca** mais baixa, sem brilhos.
- **Saldo disponível** continua sendo o destaque: gradiente azul mais discreto (usa a cor principal do tema), valor em fonte forte, "Recebido" e "Pago" lado a lado e a explicação do cálculo em texto menor. Nenhuma conta ou regra foi mudada.
- **Aviso financeiro compacto** (uma faixa): saldo negativo mostra "Seu saldo está negativo", uma orientação curta e "Ver detalhes ›" (abre Relatórios), sem repetir o valor. Os demais avisos (limites, contas atrasadas, dicas) usam a mesma faixa em tom neutro. O acesso às **Conquistas** virou um ícone de troféu discreto (n/N) na própria faixa.
- **Ações rápidas** Receita / Despesa / Guardar: três cartões lado a lado (verde, vermelho, azul do tema), logo abaixo do aviso. **Anotações** e **Cartões** ficaram mais baixos; Anotações mostra "N notas · N tarefas pendentes" (e vencidos/próximo lembrete).
- Menos reflexos no fundo, sombras suaves, raios de borda padronizados, barra inferior mais opaca (melhor leitura) e sombra mais leve no botão flutuante. Tudo usa as variáveis dos temas (claro/escuro e as paletas).
- Suba só **index.html** e **tests.zip** (sw.js e ícones não mudaram). Dados: nenhuma mudança de estrutura; chaves, backups e senhas continuam compatíveis.
- Limites: testado só em Chromium simulado (sem celular real nem TalkBack).

## Versão 7.19 · Mascotes removidos e foto própria no avatar
- **Removido o Wolfin (lobo) de todo o site**: Home, Ajustes, cadastro, tela de login, imagem do resumo do mês, frases e galeria de roupas. O cadastro agora tem 2 etapas (aparência → boas-vindas).
- **Novo avatar no canto superior esquerdo da Home**: toque nele para escolher uma foto do celular, ajustar (arrastar e zoom), trocar ou remover. Sem foto, aparece a inicial do seu nome.
- A foto é reduzida para 256×256 (JPEG) e fica **só neste aparelho**, dentro dos dados (`S.pref.ph`); vai junto nos backups que você exportar. Com senha ativada, ela fica criptografada junto com os outros dados e não aparece na tela de login.
- O cartão "Meu mascote" de Ajustes virou "Conquistas" (só o botão "Ver conquistas"). A conquista "Cara própria" agora é liberada ao colocar uma foto.
- O balão de dicas da Home continua, só que sem o desenho do mascote.
- Suba só **index.html** e **tests.zip** (sw.js não mudou). O arquivo ficou bem menor porque as imagens do lobo saíram.
- Dados: novo campo opcional `S.pref.ph` (texto "data:image/jpeg;base64,…"; valores inválidos ou maiores que 150 KB são descartados ao abrir/importar). Campos antigos (`pref.lv/lm/lp/mc`, `look.v`) ficam guardados sem uso, para os próximos mascotes. Chaves, backups e senhas continuam compatíveis.
- **Ícone do app com o lobo menor** (mais para dentro, como os outros ícones do celular): arquivos `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` e `apple-touch-icon.png` refeitos; `sw.js` passou para VERSAO '4' para o celular baixar os ícones novos. Para ver na tela inicial, remova o ícone antigo e adicione de novo pelo navegador.
- Limites: testado só em Chromium simulado, sem celular real, sem câmera/galeria reais. A intro em vídeo (com o lobo) e os ícones do app não foram alterados.

## Arquivos
| Arquivo | Para quê |
|---|---|
| `index.html` | O site Wolfin (já lê o `noticias.json`) |
| `manifest.webmanifest`, `sw.js` | Fazem o site ser instalável como app e abrir sem internet |
| `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png` | Ícone do app / atalho na tela inicial |
| `noticias.json` | Notícias (começa com a coleta de 05/11/2026; depois o robô atualiza) |
| `scripts/atualizar_noticias.py` | Busca os feeds RSS e gera o `noticias.json` |
| `.github/workflows/noticias.yml` | Manda o GitHub rodar o script a cada 3 horas |

## ⚠️ ANTES de começar: faça backup
Os dados do Wolfin ficam guardados **por endereço**. Ao abrir o site no endereço novo, ele começa vazio.
1. No site atual: **Ajustes → Exportar backup** e guarde o arquivo.
2. No site novo: **Ajustes → Importar backup**.

## Passo a passo (pode ser feito pelo navegador do celular; no Chrome, ative "Site para computador" se precisar)
1. Crie uma conta em github.com e toque em **New repository**. Nome: `wallstreet`. Marque **Public**. Toque em **Create repository**.
   (Público é necessário para o Pages gratuito; só o `index.html` e as notícias ficam visíveis — seus dados financeiros ficam apenas no seu aparelho.)
2. Em **Add file → Upload files**, envie `index.html` e `noticias.json`. Toque em **Commit changes**.
3. **Add file → Create new file**. No nome, digite exatamente `scripts/atualizar_noticias.py` (a barra cria a pasta).
   Cole o conteúdo do arquivo `atualizar_noticias.py` e toque em **Commit changes**.
4. **Add file → Create new file**. No nome, digite exatamente `.github/workflows/noticias.yml`.
   Cole o conteúdo do arquivo `noticias.yml` e toque em **Commit changes**.
5. **Settings → Pages**. Em *Build and deployment*, escolha **Deploy from a branch**, branch **main**, pasta **/ (root)**. **Save**.
6. Aba **Actions → Atualizar notícias → Run workflow** para rodar a primeira vez agora.
   (Se aparecer um botão pedindo para habilitar os workflows, aceite.)
7. Espere 1–2 minutos e abra `https://SEU-USUARIO.github.io/wallstreet/`. Em **Notícias** deve aparecer
   "Atualizadas automaticamente em dd/mm/aaaa às hh:mm".

## Como saber se está funcionando
- Aba **Actions**: cada execução verde = deu certo. Abra uma execução para ver o log (`ok Agência Brasil: 10 itens`, etc.).
- Linhas `FALHOU <fonte>` no log significam que **aquele** feed não respondeu ou mudou de endereço. Os outros continuam; o site nunca
  mostra notícia inventada. Se todos falharem, o `noticias.json` não é alterado e o site passa a avisar que está desatualizado.
- Se um endereço de feed mudou, edite a lista `FEEDS` no começo de `scripts/atualizar_noticias.py`.

## O que o site faz
- Abre o `noticias.json` do próprio site (sem chave de API, sem servidor seu).
- Guarda a última versão boa no aparelho: sem internet, mostra essa versão e avisa a data/hora real dela.
- Se a atualização tiver mais de 12 h, avisa que pode estar desatualizada. Se o arquivo vier quebrado ou com link não-https, ignora e avisa.

## Limites que você precisa saber
- **Fontes:** o script usa RSS de Agência Brasil, G1, InfoMoney, Banco Central e BBC News Brasil. **Reuters e Valor Econômico não
  oferecem RSS aberto**, então não entram. Os endereços dos feeds eu não consegui testar de dentro do meu ambiente (sem internet):
  o primeiro log do GitHub mostra quais funcionam.
- **Resumos:** são os que as próprias fontes publicam no feed (cortados em ~230 caracteres), com link para a matéria original.
- **Mundo:** BBC e G1 Mundo são filtrados por palavras de economia (juros, bolsa, dólar, Fed, inflação…), então pode haver dias com poucas notícias.
- **Pausa do GitHub:** o GitHub pode pausar tarefas agendadas após ~60 dias sem atividade no repositório. Se isso acontecer,
  é só entrar em Actions e tocar em *Run workflow* / reativar.
- **Atraso:** a atualização roda de 3 em 3 horas, então o site pode estar até ~3 h atrás da fonte.

## Ícone na tela inicial / instalar como app
Envie para o repositório (Add file → Upload files, na raiz, junto do `index.html`): `index.html`, `manifest.webmanifest`, `sw.js`,
`icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png`. Depois de ~1–2 min, abra o site, feche e abra de novo e,
no menu ⋮ do navegador, escolha **Instalar app** (ou **Adicionar à tela inicial**). Se já tinha um atalho antigo com a letra "G", apague-o e crie outro.
Depois de instalado, o app abre em tela cheia e, sem internet, abre com a última versão guardada.

## Segurança (usuário e senha)
- Na primeira abertura aparece "Proteger o Wolfin": crie usuário e senha. Os dados passam a ficar **criptografados (AES-256)** no aparelho e só abrem com a senha.
- O app mostra **um código de recuperação** (20 caracteres) **uma única vez**. Anote em papel ou guarde fora do celular. É a única forma de recuperar o acesso se esquecer a senha. **Não há recuperação por e-mail** (o site não tem servidor).
- Esqueceu a senha? Na tela de login toque em "Esqueceu a senha?", digite o código e crie uma nova senha (um novo código é gerado).
- Perdeu a senha **e** o código? Os dados não podem ser abertos por ninguém. Só o backup (arquivo exportado em Ajustes) salva. **Backups exportados não são criptografados** — guarde em local seguro.
- Ajustes → Segurança: bloquear agora, bloqueio automático (1, 5 ou 15 min fora do app, ou só ao fechar), alterar senha, gerar novo código, remover proteção.
- Para atualizar o site basta substituir o `index.html` no GitHub; os dados e a senha ficam no aparelho e não são afetados.

## Gastos por categoria e backup criptografado
- **Relatórios → Gastos por categoria:** barras por categoria no mês (escura = já pago, clara = previsto, traço = limite). Toque numa categoria para definir o limite mensal. Avisos: "Perto do limite" (80% do limite pago), "Vai passar do limite" (pago + a pagar ultrapassa) e "Passou do limite". Os avisos aparecem também na central de notificações e nas falas do mascote.
- **Ajustes → Exportar backup criptografado:** gera um arquivo que só abre com a senha que você escolher (diferente da senha de login). Importar funciona pelo mesmo botão "Importar backup". Sem a senha do backup ninguém recupera o arquivo.

## Lembrete semanal de backup
O app guarda a data do último backup exportado (comum ou criptografado). Depois de 7 dias sem backup, avisa na central de notificações, na fala do mascote e em Ajustes → Backup. Dá para mudar para "a cada 2 semanas" ou desligar em Ajustes → Backup → Lembrete de backup. Importar um backup também zera a contagem.

## Zerar dados, app em branco e lembretes
- **Ajustes → Zerar todos os dados:** apaga lançamentos, dívidas, parcelas, caixinhas e limites e deixa o app em branco (é preciso digitar ZERAR). Nome, tema, avatar e senha continuam.
- **O app agora abre em branco** em um aparelho novo (nenhum dado pessoal vem no código). Para trazer seus dados, use Ajustes → Importar backup.
- **Lembrete de backup:** todos os dias, toda semana, a cada 15 dias, todo mês ou desligado.

## Primeira abertura (boas-vindas)
Quem abre o link pela primeira vez vê a tela de boas-vindas: **Criar minha conta** (pergunta o nome, depois usuário e senha, com código de recuperação), **Já tenho uma conta** (importar um backup, comum ou criptografado) ou **Usar sem senha por enquanto**. A "conta" fica só no aparelho: para usar em outro aparelho, é preciso importar o backup.

## Minha situação financeira e Sobre
- **Relatórios → Minha situação financeira:** avalia a saúde financeira (Saudável, Estável, Atenção ou Crítica) com regras claras, usando receitas, despesas, saldo disponível, dívidas, parcelas e atrasos do mês. Mostra o porquê, o que está bem e o que fazer. É orientativa.
- **Ajustes → Sobre:** nome, slogan, criador, finalidade, avisos importantes e direitos autorais.

## Identidade visual (Minimal Glass + lobo)
Visual de vidro fosco nos temas claro e escuro, com o lobo como mascote e símbolo. Em Ajustes → Aparência há o "Efeito de vidro" (Completo ou Leve, mais rápido). Os ícones do app (icon-192.png, icon-512.png, icon-maskable-512.png, apple-touch-icon.png) foram renovados: envie os quatro junto com o index.html.

## Avatar de lobo e calculadora
O avatar agora é um lobo: 7 expressões, acessórios de cabeça (boné, cartola, coroa, gorro, fones) e de rosto (óculos escuros, óculos redondos, tapa-olho, cicatriz), 5 pelagens e 9 cores de fundo (Ajustes → Avatar). O botão flutuante da calculadora usa um ícone simples de calculadora. A voz da assistente foi removida.

## Central de Jogos (etapa 1)
Acesso pelo card "Central de Jogos" na Home. Jogos: Quiz financeiro, Verdadeiro ou falso, Desafio matemático e Decisão financeira (cada rodada tem 4 a 6 perguntas, com explicação a cada resposta). Há XP e níveis, moedas virtuais, desafios diários com baú, sequência de dias com bônus, 14 medalhas e dificuldade que se ajusta ao desempenho. Tudo é virtual (sem dinheiro real) e fica salvo junto com os seus dados (entra no backup). O "Sobreviva ao Mês" (simulador de 4 semanas com salário fictício) já está incluído; a Loja de recompensas (Central de Jogos → Loja) troca moedas virtuais por acessórios, pelagens e fundos novos do lobo e por 3 temas visuais (Ouro, Rosé e Grafite). Itens com cadeado também aparecem no editor de avatar e em Ajustes → Aparência.

## Mascote principal (Lobo 2D)
O mascote é o lobo ilustrado de terno branco, colete, gravata preta e relógio (a imagem de referência), embutido no app como 6 camadas WebP leves (corpo, cabeça, 2 orelhas, 2 olhos; ~43 KB no total). Aparece nas boas-vindas, no login, nas telas com senha e na dica da Home. Animações só com CSS: balanço sutil da cabeça, piscar, orelhas e olhar. Em todas as telas de bloqueio (boas-vindas, nome, login e senha) aparece o mesmo lobo: com a senha oculta ele fecha os olhos, e ao preencher usuário, nome ou senha visível ele olha para baixo. Os 10 avatares continuam independentes.

## Telas de bloqueio (boas-vindas e login)
Têm um botão de sol/lua no canto superior direito para alternar claro/escuro (a escolha fica salva). Dentro do app, o tema só muda em Ajustes. O olho da senha tem design de vidro, fecha com a senha oculta e, aberto, a pupila olha de um lado para o outro. Os 10 avatares são personagens 2D ilustrados (lobo, urso polar, pantera, tigre, raposa, lince, sapo, rinoceronte, coruja e touro).

## Anotações (no lugar da Central de Jogos)
O app não tem mais jogos, moedas, XP nem loja: todos os temas e paletas são livres. No lugar, a seção **Anotações** reúne três ferramentas, tudo salvo só no aparelho (e criptografado quando há senha): **Notas** (título e descrição, salvas automaticamente), **Lembretes** (data e horário, aviso do navegador quando permitido, concluir ou excluir, integrados ao sino de notificações) e **Tarefas** (listas personalizadas com itens marcáveis). Os avisos tocam enquanto o app está aberto; com o app fechado, o navegador não garante o aviso, e os lembretes vencidos aparecem no sino ao abrir.

## Avatares (10 ilustrações no mesmo estilo)
Os 10 avatares são ilustrações no estilo do lobo Alfa, recortadas e otimizadas (WebP, ~10 KB cada, embutidas no app): Alfa (lobo), Ártico (urso polar), Sombra (gato preto), Raio (tigre), Ruivo (raposa), Safira (lobo azul), Esmeralda (sapo), Cobre (cavalo), Névoa (coruja) e Samurai (panda vermelho). Todos no mesmo círculo azul-escuro, com o mesmo enquadramento.

## Versão 4.1: cartões, atalhos, aviso de versão e lembretes na agenda
- **Cartões de crédito** (Despesas → Cartões de crédito): nome, limite, dia de fechamento e vencimento; compras com parcelas; fatura por mês (aberta, fechada, atrasada ou paga); limite disponível. Só o pagamento da fatura entra no saldo. Há avisos de fatura perto do vencimento ou atrasada, e o card aparece na Home.
- **Atalhos do ícone** (segurar o ícone do app instalado): Nova despesa, Nova receita e Anotações (definidos em `manifest.webmanifest`).
- **Aviso de nova versão:** o app compara a versão (BUILD) do site publicado com a do aparelho e oferece "Atualizar agora" (os dados não são apagados). Para isso funcionar, a cada atualização o texto do BUILD no index.html precisa mudar; Ajustes → Sobre tem "Verificar atualização".
- **Lembrar de pagar:** botão ⏰ nas despesas e parcelas pendentes e na fatura do cartão; os lembretes podem ir para o Google Agenda ou para um arquivo .ics (que avisa mesmo com o app fechado).

## Estilos do mascote (versão 4.2)
Em Ajustes → Mascote: o lobo Executivo (terno branco) e 10 roupas (Jazz, Piloto, Rei, Detetive, Hacker, Chefão, Preso, Bêbado, Magnata e Férias). Cada estilo tem animações próprias (piscar, orelhas, balanço de cabeça no ritmo da personalidade e efeitos como notas musicais, fumaça, faíscas e "hic!") e falas próprias sobre dinheiro. A troca automática (a cada 3 horas, nunca repetindo o estilo anterior) vem DESLIGADA por padrão; a escolha manual fica gravada. As telas de login usam o mesmo estilo (com a senha oculta, o lobo fecha os olhos).

## Acabamento visual (versão 4.3)
Transições e animações leves (só transform e opacidade, todas curtas e finitas; paradas quando o Android está com "reduzir movimento"): entrada em sequência nas telas de boas-vindas e login; indicador que desliza sob a aba ativa da navegação; brilho rápido ao tocar nos botões (inclusive nas abas); barras de gráfico que crescem, anéis que entram, linhas de lista que aparecem em sequência, sino que balança ao entrar na Home quando há avisos e aviso rápido (toast) que sobe deslizando.

## Escolha do mascote no cadastro (versão 4.4)
Em "Criar minha conta" há uma etapa nova depois do nome: "Escolha seu mascote". Mostra os 11 estilos (Executivo, Jazz, Piloto, Rei, Detetive, Hacker, Chefão, Preso, Bêbado, Magnata e Férias) em grade com miniatura e nome; o lobo do topo muda na hora ao tocar. A escolha é salva na conta (junto com as preferências, criptografadas quando há senha) e espelhada para a tela de login, então aparece nos próximos acessos. Quem toca só em Continuar fica com o Executivo. "Usar sem senha" e "Já tenho uma conta" não têm a etapa (o estilo muda em Ajustes → Mascote).

## Tutorial do primeiro acesso (versão 4.5)
Depois de CRIAR uma conta nova ("Criar minha conta" ou "Usar sem senha"), o app mostra um passeio rápido de 8 passos (Seu painel, Lançamentos rápidos, Receitas, Despesas, Dívidas e Caixinhas, Relatórios, Ajustes e um final) com destaque na própria tela e um balão explicativo. "Pular" fica disponível o tempo todo (a tecla Esc também pula). Ao concluir ou pular, o app grava na conta (S.flags.tour) que o tutorial já foi visto e não o mostra de novo. Contas que já existem e backups importados NÃO veem o tutorial (o gatilho é só a criação de conta). Em Ajustes → Sobre há "Ver o tutorial" para rever quando quiser.

## Detetive corrigido (versão 4.6)
O estilo Detetive do mascote usa agora o PNG transparente enviado (chapéu, rosto, terno, distintivo, mão com o cigarro e a fumaça), embutido em WebP (~42 KB) na proporção do palco (1024×880), inteiro e sem cortes (só um esmaecido suave na cintura, onde a imagem original termina). Pálpebras e orelhas foram realinhadas ao novo desenho; a fumaça sai da ponta do cigarro (3 baforadas) e a brasa pulsa. O quadro do Detetive na Home e no login mostra o desenho completo; a miniatura em Ajustes e no cadastro é centrada no rosto.

## Tema Pérola e escolha de cor no cadastro (versão 4.7)
Nova paleta **Pérola** (#E8EDF5: fundo perolado com acento azul-ardósia legível; versão escura própria), primeira da lista em Ajustes → Aparência e padrão do site (aplicado já na primeira visita, sem piscar azul). O **Azul** e as demais cores continuam disponíveis. Em "Criar minha conta" há uma nova etapa depois do mascote: "Escolha a cor do seu tema" (9 cores + Claro/Escuro, com pré-visualização ao vivo, Pérola selecionada por padrão). A escolha é salva na conta e espelhada para a tela de login. Quem já usa o app mantém a cor que tem; "Usar sem senha" e "Já tenho uma conta" não passam pela etapa (troca em Ajustes).

## Situação financeira com cartões (versão 4.8)
A "Minha situação financeira" (Relatórios) agora considera os cartões de crédito, pela mesma lógica da tela Cartões (função `ccFin`, só leitura): faturas que vencem no mês entram nos compromissos e nas despesas do mês (pagas e pendentes); o saldo devedor dos cartões (faturas pendentes + parcelas futuras no cartão) entra em "Parcelas e faturas a pagar" e na capacidade de pagamento; fatura vencida e não paga conta como atraso. Pagamentos parciais reduzem o pendente e o saldo na mesma medida (sem contar duas vezes); pagar a mais nunca deixa pendente negativo. Sem cartões, o resultado e a tela são idênticos aos da versão anterior (verificado em 300 cenários). O saldo disponível, Home, Dívidas e Relatórios de fluxo (caixa) não mudaram.

## Validação dos pagamentos de fatura (versão 4.9)
Em Cartões → Pagar fatura: o valor não pode passar do que falta pagar (total da fatura − pagamentos anteriores); o formulário mostra o máximo e já vem preenchido com ele, e o limite é conferido de novo no momento de salvar. Valor acima, zero, negativo ou inválido mostram uma mensagem clara e nada é gravado. Fatura quitada não aceita novos pagamentos (o botão não aparece e a ação é bloqueada mesmo se acionada). Envios repetidos (clique duplo, Enter) gravam um único pagamento (trava de ~1 s e limite recalculado). Saldo, despesas pagas do mês, Situação financeira e histórico atualizam na mesma operação; desfazer um pagamento devolve o valor ao pendente. Dados antigos com pagamento acima da fatura são preservados (a fatura aparece como "Paga" e o pendente nunca fica negativo). O auxiliar de formulários passou a ignorar com segurança um segundo envio que chega depois de o formulário fechar.

## Salvamento seguro (versão 5.0)
No modo protegido, a gravação passou a ser uma fila única que sempre leva o estado mais recente: criptografa (chave capturada no momento de salvar), grava e confere lendo de volta. O aviso "Salvo ✓" (e os demais avisos emitidos durante a gravação) só aparece depois que isso termina com sucesso; se falhar, aparece "Não foi possível salvar os dados protegidos…" e o armazenamento continua com a versão anterior íntegra (a próxima gravação leva o estado completo). Fechar a página durante a gravação dispara o aviso do navegador. Quando outra janela/aba do app grava dados diferentes, esta página pede para recarregar e fica só leitura, para nunca sobrescrever dados novos com antigos; a tela de login usa sempre o cadastro protegido mais recente. Abrir o app não regrava dados que não mudaram. Criptografia e formato guardado inalterados. Limite: fechar de verdade no meio da gravação pode perder a última alteração (o armazenamento nunca fica corrompido).

## Cache do app (versão 5.1)
O `sw.js` agora identifica os caches como `wallstreet::<escopo>::v<versão>` (ex.: `wallstreet::/wallstreet/::v3`) e só cria, lê e apaga caches com essa identificação (mais o nome antigo `wallstreet-vN`). Caches de outros projetos do mesmo domínio (como o github.io, que é compartilhado) nunca são tocados, e o app só responde por arquivos da própria pasta. Instalação: o `index.html` é obrigatório (se falhar, a versão atual continua valendo e não sobra cache pela metade); ícones e manifesto são "melhor esforço". Ativação: só limpa as versões antigas se o cache novo está íntegro, e limpa de novo na primeira requisição (caso um worker antigo recrie algo). Rede primeiro revalidando sempre (não aparece arquivo velho nem do cache HTTP do navegador); se a rede falhar ou levar mais de 6 s, usa a cópia guardada. O botão "Atualizar agora" agora desregistra só o Service Worker deste app e apaga só os caches dele. Para trocar de versão do cache, mude `VERSAO` no `sw.js`. Dados financeiros (localStorage), criptografia e login não são tocados.

## Importação protegida de backups (versão 5.2)
Antes de importar, o arquivo é validado por inteiro numa cópia (estrutura, listas obrigatórias, tipos, valores em centavos, datas, cartões, versão dos dados, campos suspeitos, tamanho). Arquivos vazios, cortados, corrompidos, de outro app ou de versão mais nova são recusados com mensagem clara e os dados atuais não são tocados. O backup comum novo traz um selo de integridade (`__backup`, SHA-256): se o arquivo for alterado depois de exportado, a importação é recusada; backups antigos (sem selo) continuam aceitos, assim como os criptografados (criptografia inalterada). Antes de substituir, a confirmação mostra o resumo do backup e dos dados atuais e avisa de: menos registros que os atuais, mais antigo que o último backup, mesmo backup já importado, versão antiga. Backup igual aos dados atuais não é reimportado. Cliques repetidos e importações simultâneas são impedidos. A troca é atômica: se a gravação falhar (armazenamento cheio, criptografia, conferência, janela desatualizada), tudo volta como estava. A tela "Já tenho uma conta" usa a mesma validação. Não há cópia automática dos dados atuais antes de substituir: exporte um backup antes se quiser guardá-los.

## Segurança de acesso reforçada (versão 5.3)
Controle de tentativas de senha e de código de recuperação: a tentativa é contada ANTES de verificar (fechar a aba no meio não escapa; envios simultâneos não multiplicam palpites; tentativas com menos de ~1 s de intervalo são recusadas sem contar). Espera progressiva a partir da 3ª falha seguida: 15 s, 30 s, 1 min, 2 min, 5 min, 10 min, 15 min e depois sempre 30 min (teto: nunca bloqueia para sempre). Sem tentativas por 2 h a contagem cai; por 24 h volta a um nível leve; valor absurdo no controle vira no máximo 30 min; relógio voltado para trás também não passa de 30 min. O estado fica em 3 lugares independentes (localStorage, IndexedDB e Cache, usa-se o mais restritivo): apagar um não zera, e o apagado é restaurado. Durante a espera até a senha certa é recusada com a mesma resposta; as mensagens são genéricas. A recuperação por código tem contador próprio (não é travada pela espera da senha) e funciona como antes; qualquer acesso correto zera tudo. Criptografia (AES-256-GCM, PBKDF2), senhas, chaves e códigos de recuperação não foram alterados. Limites: quem apaga os 3 lugares ou adianta o relógio do aparelho pula a espera; e a espera não protege contra quem copia o arquivo criptografado e testa senhas fora do app (aí só valem a senha forte e o PBKDF2).

## Relatórios financeiros completos (versão 5.4)
A tela Relatórios ganhou 7 cartões novos abaixo da "Minha situação financeira" (os que já existiam continuam): Resumo do mês (recebido, pago, dívidas pagas, guardado, saldo inicial, resultado e saldo final), Indicadores do mês (positivo / atenção / crítico, com as mesmas regras da Situação financeira), Comprometimento da renda (contas, parcelas e faturas de cartão em % da renda prevista; pago, a pagar e vencido; dívidas pagas à parte), Despesas por categoria (participação em %), Despesas recorrentes (contas fixas, parcelamentos e compras parceladas no cartão), Evolução das dívidas (inicial, pago, restante e saldo devedor por mês) e Comparação mensal (dois meses à escolha). Tudo é calculado dos lançamentos reais, sem estimativas; no mês atual o total comprometido é igual ao da Situação financeira e o saldo final é igual ao saldo principal. Atenção: marcar uma parcela como paga NÃO reduz o saldo disponível (comportamento já existente); o resumo mostra "Parcelas deste mês já pagas" à parte. Backups que só diferem em tema/cor agora mostram a confirmação de importação.

## Acessibilidade e navegação (versão 5.5)
Janelas (formulários, confirmações, avatar, limites) agora são diálogos modais: título falado, foco entra e fica preso nelas, Esc fecha, o fundo fica inerte e o foco volta ao botão que abriu (ou ao título da tela). A calculadora flutuante abre por teclado/leitor de tela (antes só por toque de ponteiro). Anel de foco visível nos dois temas, link "Pular para o conteúdo", avisos (toast) e erros lidos sozinhos, 32 gráficos com descrição falada (valores escondidos também ficam escondidos), barras decorativas fora da leitura, botões de tema/cor com estado (aria-pressed), aba atual marcada (aria-current), cada tela anuncia o nome no título da página e leva o foco ao título, foco preservado ao redesenhar a tela. Áreas de toque de no mínimo 44 px (inclusive a barra inferior em telas de 320 px) e quatro textos pequenos com contraste ajustado. Redução de movimento do aparelho continua respeitada. Cálculos, dados, criptografia e login não foram alterados. Testado em emulação do Chromium (tamanhos de tela, Pixel 5, Galaxy S9+) e com teclado; não foi testado em aparelho físico nem com TalkBack. Um backup que só difere em tema, cor, mascote ou avatar agora mostra a confirmação de importação.

## Testes automatizados
A pasta `tests/` tem a estrutura de testes (veja `tests/README.md`) e `.github/workflows/tests.yml` roda tudo no GitHub a cada envio, com um job por área. Localmente: `pip install -r tests/requirements.txt`, `python -m playwright install chromium` e `python tests/run_all.py`. Usa só dados fictícios; não depende de nada do app em produção. Um envio com teste vermelho não deve ser publicado.

## Nova identidade: Wolfin (versão 6.0)
O aplicativo agora se chama **Wolfin** (título: "Wolfin – Controle Financeiro"; slogan: "Domine seu dinheiro."). O nome e o slogan aparecem nas telas de boas-vindas e login, no cartão principal da Home, na página Sobre, no título das abas, no tutorial, nos avisos e nos arquivos gerados (`wolfin-backup-AAAA-MM-DD.json`, `lembrete-wolfin.ics`). O manifesto PWA passa a ter nome "Wolfin – Controle Financeiro" e nome na tela inicial "Wolfin"; o `id`, o `start_url` e o `scope` não mudaram, então o app instalado continua o mesmo (o Android pode levar um tempo para atualizar o nome e o ícone na tela inicial).

**O que NÃO mudou, de propósito (compatibilidade):** o endereço do site e do repositório (`/wallstreet/`), as chaves de armazenamento no navegador (`wallstreet.*`), o prefixo dos caches do Service Worker (`wallstreet::`) e o marcador interno dos backups (`wallstreet-backup`). Por isso quem já usa o app **não perde dados, não precisa refazer a senha** e continua importando backups antigos. A logo (lobo) foi preservada.

**Marca:** a disponibilidade jurídica do nome "Wolfin" (registro de marca, domínio, Play Store) **não** foi verificada por esta mudança e deve ser validada à parte antes de qualquer publicação comercial.

## Intro animada (versão 6.3: vídeo com som, uma vez por sessão)
A intro em vídeo (cerca de 6 s, vertical) criada pelo dono do app aparece **uma vez por sessão**: na primeira abertura do site/app e de novo só quando se abre em outra aba/janela ou se fecha e reabre o app. **Recarregar não repete** (nem o recarregamento automático do app ao bloquear ou atualizar). Isso usa `sessionStorage` ("wolfin.intro"); não dá para detectar "saiu e voltou ao navegador" com precisão: se o navegador mantiver/restaurar a aba, a intro não reaparece. Sem `sessionStorage` (modo restrito) ela toca normalmente.

**Som:** o vídeo tem o áudio original (MP4: AAC; WebM: Opus). O app tenta tocar com som; navegadores costumam bloquear som automático (o Chrome tende a permitir em app instalado). Se bloquear, o vídeo toca **mudo** e aparece o botão "Toque para ativar o som" (liga o áudio sem pular a intro). Confirme que você tem os direitos de uso da música/efeitos do vídeo.

Arquivos: `intro-wolfin.mp4` (H.264+AAC, ~0,7 MB) e `intro-wolfin.webm` (VP9+Opus, ~0,8 MB), convertidos do original (1440×2560, 60 fps, 19,9 MB) para 720×1280, 30 fps. O navegador baixa só o formato que consegue tocar; o Service Worker guarda o MP4 já na instalação e serve os trechos (Range/206), então a intro em vídeo toca offline. Um toque (ou tecla) pula; em tela larga, com "reduzir movimento", ou se o vídeo não carregar em ~3 s, usa a **intro em CSS** (logo com reflexo e orelhas, nome e slogan, ~1,5 s; com movimento reduzido, estática por ~0,6 s). Para trocar o vídeo, gere os dois arquivos com os mesmos nomes (ou mude os nomes no script da intro e use nomes novos a cada versão para o cache não servir o antigo). Os testes (`tests/suites/intro_wolfin.py`) conferem formato, tamanho, áudio, margens do texto, som permitido/bloqueado, sessão e offline.

## Cor padrão e mascote (versão 6.3)
- **Cor padrão: Azul** (para combinar com a intro). As 9 cores continuam disponíveis em Ajustes → Aparência (Azul agora é a primeira; a Pérola continua como opção). Quem já escolheu uma cor mantém a escolha; o padrão vale para contas novas e primeiras visitas.
- **Troca automática de roupa do mascote: removida.** A roupa fica sempre a escolhida em Ajustes → Mascote. Dados/backups antigos com a troca ligada são aceitos: ela passa a desligada e a roupa atual é mantida (o campo `ma` continua nos backups só por compatibilidade).

## Mascotes oficiais (versão 7.0): mascote = avatar
O app tem **10 mascotes oficiais**, e o escolhido é também o **avatar** em todo o app (cabeçalho da Home, cartão do mascote, Ajustes, tela de login): Wolfin (Lobo, CEO, mascote principal), Leônidas (Leão, Rei), Don Vito (Raposa, Magnata), Oráculo (Coruja, Analista), Brutus (Touro, Investidor), Mako (Tubarão, Negociador), Bento (Castor, Planejador), Penny (Esquilo, Poupador), Nyx (Pantera, Hacker) e Elliot (Guaxinim, Detetive). Não existe mais seleção separada de avatar, nem as roupas do lobo, nem a troca automática de roupa.
- **Onde escolher:** na criação da conta (lista com imagem, nome, animal · função e descrição curta; o Wolfin aparece primeiro como "Principal", mas não é obrigatório) e em **Ajustes → Meu mascote** (ou tocando no avatar do cabeçalho).
- **Imagens:** PNG enviados pelo dono do app, convertidos para WebP (544 px, ≈ 406 KB no total) e **embutidos** no `index.html` (funcionam offline). O avatar é um recorte do rosto da mesma imagem. O script que gera os dados está em `tests/tools/gerar_mascotes.py` (precisa dos PNG originais).
- **Animações (só CSS, individuais por personagem):** piscar com pálpebras sobre o rosto (olhos fecham ao digitar a senha no login), movimento de cabeça e respiração próprios, orelhas (Wolfin, Don Vito, Brutus, Penny, Nyx, Elliot), brilhos (joias, correntes, moeda, abotoaduras), reflexo em óculos e lupa (Oráculo, Bento, Elliot), fumaça discreta (Brutus) e pulsação neon (Nyx). Com "reduzir movimento" tudo fica estático. Não foram implementados: movimento do chapéu/sobrancelhas do Don Vito, ajuste dos óculos do Oráculo, movimento da moeda da Penny e ajuste da lupa do Elliot.
- **Dados e migração:** o mascote fica em `pref.mc` (e em `wallstreet.look`, para a tela de login). Contas e backups antigos são migrados ao abrir/importar, **sem apagar nada** (os campos antigos `av` e `ms` continuam nos dados): avatar escolhido → lobo=Wolfin, gato preto=Nyx, tigre=Leônidas, raposa=Don Vito, coruja=Oráculo, panda-vermelho=Elliot; senão a roupa antiga → Rei=Leônidas, Detetive=Elliot, Hacker=Nyx, Magnata=Don Vito; sem correspondência → Wolfin. A conquista "Cara própria" agora é "escolha o seu mascote".

## Correções da auditoria final (versão 7.1)
- **Parcela paga desconta do saldo.** Marcar uma parcela como paga agora reduz o saldo disponível. O mês do caixa é a data do pagamento (`paidOn`); sem ela, o vencimento; sem ele, o mês da parcela. Antes, parcelas pagas eram "registradas à parte" e não alteravam o saldo (o saldo podia ficar superestimado). **Quem já tinha parcelas pagas vê o saldo diminuir uma vez**, com um aviso único mostrando o valor (marcador `flags.pqv`). Relatórios mostra "Inclui R$ X de parcelas pagas neste mês".
- **Rótulos:** Home "Receitas / Despesas / Diferença" (diferença = receitas − despesas do mês, sem caixinhas e dívidas); Despesas "Pagas (sem faturas de cartão)"; Relatórios "Resultado do mês (após dívidas e caixinhas)".
- **Desempenho:** os cálculos repetidos dentro de um único desenho de tela são reaproveitados (nada fica guardado depois). Home ≈ 31–49% mais rápida e Relatórios ≈ 17–24% (medido com dados fictícios). O cartão "Minha situação financeira" continua sendo o mais pesado (recomendação em aberto).
- **Senha mais forte** (criação da conta, troca de senha, recuperação e backup criptografado): mínimo de 10 caracteres; recusa senhas comuns, repetidas, em sequência e só numéricas com menos de 12 dígitos; indicador de força na criação. Contas existentes **não** são afetadas (o login não usa essa regra).
- **Política de conteúdo (CSP) e `referrer`:** o app só fala com o próprio site, sem plugins, sem `<base>`, formulários só para o próprio site, sem referrer. Vale só em http/https e nunca no modo de testes. Limites: os scripts do app continuam permitidos inline e o bloqueio de `eval` não foi confirmado.
- **Armazenamento persistente:** o app pede ao navegador, uma vez e em silêncio, para não apagar os dados.
- **Workflows:** ações do GitHub atualizadas para versões com Node 24 (checkout v6, setup-python v6, setup-node v6, upload-artifact v7, escolhidas por pesquisa, **confirme na primeira execução**). O workflow de notícias roda uma por vez, em servidor fixo, reconcilia com seus envios (`git pull --rebase`) e tenta o envio até 4 vezes.

### Privacidade: origem compartilhada no GitHub Pages (importante)
Todos os sites de `pauldavilafnc.github.io` compartilham o mesmo armazenamento do navegador. **Não publique outros projetos nesta conta**, porque eles poderiam ler os dados do Wolfin (especialmente no modo "sem senha"). Para isolar de verdade, use uma conta/organização ou domínio próprio para o Wolfin (o endereço muda e os dados do navegador são por endereço: restaure por backup exportado). No modo sem senha os dados ficam em texto simples no navegador e o backup comum também; prefira proteger com senha e exportar backup criptografado.

## Intro: som automático, sem botão (versão 7.2)
O botão "Toque para ativar o som" foi removido. A intro **tenta tocar com som sozinha**; se o navegador bloquear o som automático (a regra da maioria), ela toca **muda**, sem botão nem aviso. Um toque ainda pula a intro. **Nenhum site consegue forçar som automático**: quem decide é o navegador. O som costuma tocar automaticamente quando o Wolfin está **instalado como app** (tela inicial) e, em alguns navegadores, depois de permitir som/autoplay para o site nas configurações do navegador.

## Nova entrada: som da intro, 3 etapas, ENTRAR e senhas (versão 7.3)
- **Intro com controle de som.** Voltou um botão **discreto** (canto superior direito, só na intro em vídeo). A intro continua **tentando** tocar com som, mas **só se o navegador permitir**; se bloquear, toca muda e o botão mostra "som desligado" (tocar nele liga). Tocar no botão **não** pula a intro (tocar em qualquer outro lugar pula). Desligar o som fica lembrado em `wolfin.introsnd` (única chave nova; não é dado financeiro). Em movimento reduzido ou tela larga, a intro é em CSS, sem som e sem botão.
- **Quem ainda não tem conta vê 3 etapas** (cada uma com "Etapa N de 3"): **1. Escolha seu mascote** (os 10, com imagem, nome, animal · função e descrição; o Wolfin primeiro, "Principal"; é preciso escolher um para continuar) → **2. Escolha sua aparência** (claro/escuro + 9 cores, com prévia que muda na hora; Azul continua o padrão) → **3. Boas-vindas** (o mascote escolhido se apresenta e explica o app em frases curtas) → **nome** → **criar usuário e senha**. Nada é gravado até concluir a conta; ao concluir, mascote, cor, tema e nome vão para a conta e o mascote vira o avatar.
- **ENTRAR** aparece, pequeno, no centro embaixo, em **todas as 3 etapas**. Ele leva à tela de entrada (**Entrar na sua conta**). Como os dados ficam só no aparelho (sem servidor), em um aparelho novo "entrar" significa **importar o backup** da conta. Quem já tem conta neste aparelho **nunca vê as etapas**: cai direto no login.
- **"Usar sem senha por enquanto"** saiu da primeira tela e fica na tela de criar acesso.
- **Senhas:** "Senha" e "Repita a senha" (e, na recuperação, "Nova senha" e "Repita a nova senha") têm **cada uma o seu olho**, independentes, com nomes diferentes para leitores de tela.
- **Não mudou:** cálculos, relatórios, backups, armazenamento financeiro, criptografia, chaves `wallstreet.*`.

## Mini tutorial de backups (versão 7.4)
- **Aparece sozinho uma única vez por conta**, na primeira vez que a pessoa abre **Configurações**. São 5 etapas ilustradas (Seus dados merecem proteção → Crie sua cópia de segurança → Guarde em um lugar seguro → Recupere seus dados quando precisar → Backup feito, tranquilidade maior), com indicador "Etapa N de 5", Voltar/Próximo, Pular/fechar e botão **ENTENDI** no fim.
- **Pular ou fechar** mostra um aviso discreto lembrando da importância do backup. Concluir, pular ou fechar registra o tutorial como visto; ele não volta ao recarregar, sair ou entrar. O registro fica dentro da própria conta (junto das outras marcações da conta, e portanto também dentro dos backups).
- **Rever:** botão discreto **"Como fazer backup?"** dentro do cartão Backup de Configurações, sempre disponível.
- **Os textos descrevem só o que o app faz de verdade:** o app baixa um arquivo; **quem escolhe onde guardar é você** (nada é enviado sozinho para Drive ou outro serviço); importar **substitui** os dados atuais (não mescla); backup com senha exige guardar a senha; nunca compartilhe o arquivo nem a senha.
- **Não mudou:** exportação, criptografia, importação, restauração, dados financeiros, senhas, chaves `wallstreet.*`.
- Teste: `python3 tests/run_all.py --suite tutorial_backup` (78 verificações).

## Tela de escolha de mascotes (versão 7.5)
- **Grade de 3 colunas** (cartões compactos: imagem, nome e cargo; selecionado com borda azul e ✓). Em telas muito estreitas os textos diminuem um pouco para não cortar.
- **Só nome e cargo**: sem nome do animal nem descrição (Wolfin – CEO, Leônidas – Rei, Don Vito – Magnata, Oráculo – Analista, Brutus – Investidor, Mako – Negociador, Bento – Planejador, Penny – Poupadora, Nyx – Hacker, Elliot – Detetive). Em Ajustes → Meu mascote a lista completa continua igual.
- **"Já tem conta? Entrar"**: o botão grande ENTRAR fixo embaixo saiu; agora é um link de texto pequeno, com "Entrar" sublinhado, abaixo do Continuar (nas 3 etapas). Leva à tela de entrar na conta (importar backup).
- **Continuar** maior, azul, fixo na parte de baixo da tela enquanto se rola (cinza-azulado até escolher um mascote).
- **Gradiente preto inferior removido.**
- Teste: `python3 tests/run_all.py --suite mascotes_grade`.

## Ferramentas rápidas (versão 7.6)
- **Botão flutuante novo** (ícone de 3 blocos: calculadora, nota e tarefa), sempre **encaixado na borda esquerda ou direita**. Arraste: ele segue o dedo/mouse e, ao soltar, volta suavemente para a borda mais próxima (é assim que você escolhe o lado; pelo teclado, setas ←/→/↑/↓). Só se move na vertical dentro da área segura e **nunca cobre o menu inferior** (celular) ou o lateral (computador). A posição é lembrada (`wolfin.dock`, só posição).
- **Toque** → painel **FERRAMENTAS RÁPIDAS** com exatamente 3 opções: **Calculadora, Notas, Lista de tarefas**. Abre ao lado do botão, fecha pelo X, tocando fora, com Esc ou tocando no botão de novo.
- **Janelas independentes** (arrastáveis, minimizar e fechar, sempre dentro da tela, ficam abertas ao navegar entre páginas, trancam/fecham ao sair da conta): a **calculadora é a mesma de antes** (só ganhou o botão minimizar).
- **Notas:** usam **as mesmas notas das Anotações da Home** (`S.org.notes`), então não há duplicidade. Criar, editar, excluir (com confirmação), salvamento automático.
- **Tarefas:** checklist simples (adicionar, marcar/desmarcar, excluir; concluídas ficam riscadas e vão para o fim). Ficam numa lista chamada **"Tarefas rápidas"** dentro das listas de Anotações → Tarefas (`S.org.lists`, id `qk`). Ela só é criada quando você adiciona a primeira tarefa; nada é criado sozinho.
- **Armazenamento:** notas e tarefas ficam nos dados da conta (criptografados quando a conta tem senha, isolados por conta e incluídos nos backups como as demais anotações). Nenhum serviço externo. Lógica de backup, autenticação e dados financeiros não mudaram.
- Teste: `python3 tests/run_all.py --suite ferramentas_rapidas` (60 verificações).

## Novidades da versão 7.7
- **Aviso de backup (Home):** aparece um aviso discreto quando passam **30 dias ou mais** sem exportar um backup (ou 30 dias de uso sem nenhum backup), com **"Exportar agora"** (mesma exportação de sempre) e **"Depois"** (adia por 7 dias). Respeita o lembrete de backup de Configurações (desligado = nunca aparece). O adiamento fica em `S.flags.bkpSnz`.
- **Fixar notas:** pino em cada nota (lista da Home/Anotações, janela Notas das ferramentas rápidas e tela de edição). Fixadas ficam no topo; dentro de cada grupo, a mais recente primeiro. Guardado no campo `p` da nota (`S.org.notes`), incluído nos backups.
- **Busca única:** campo na Home que procura (sem diferenciar maiúsculas/acentos, mínimo 2 letras, todas as palavras) em lançamentos, notas e tarefas; resultados agrupados, tocar leva ao item. Não guarda nada e não usa internet.
- **Resumo do mês em imagem:** em Relatórios, escolha o mês e gere uma imagem 1080×1350 (PNG) com receitas, despesas, dívidas pagas, guardado, resultado e principais categorias (%). **Nunca inclui** descrições de lançamentos, nomes, notas ou tarefas. Opção "Ocultar valores em R$" (só porcentagens). Botões Salvar imagem e, quando o navegador permite, Compartilhar. Gerada no próprio aparelho; nada é enviado.
- **Não mudou:** chaves de armazenamento, backups, senhas, criptografia.
- Teste: `python3 tests/run_all.py --suite novidades_77` (62 verificações).
- **Correção (Sobre):** a logo no quadrado ao lado de "Verificar atualização" não aparecia (uma regra antiga escondia a imagem e o arquivo `icon-192.png` podia faltar no repositório). Agora a logo vai embutida no próprio `index.html`.

## Versão 7.8 — site mais leve
- **Vídeo da intro** recomprimido: MP4 737 KB → 372 KB; WebM 808 KB → 342 KB (mesma aparência).
- **Mascotes** em 400 px (antes 544 px): 416 KB → 345 KB. O `index.html` caiu de ~963 KB para ~868 KB.
- Ícones de 512 px **não** foram alterados (a compressão testada deixava faixas visíveis no fundo).
- Código não foi minificado nem separado em arquivos, de propósito: manter tudo em um `index.html` evita arquivo esquecido ao publicar pelo celular.
- Teste `mascotes` ajustado para o novo tamanho. Regressão: 31 suítes, todas passando.

## Mapa de calor de gastos (versão 7.9)
- **Onde:** em **Relatórios**, cartão **"Mapa de calor — Gastos por dia"** (depois de "Gastos por categoria"). E em **Relatórios → Gastos por categoria**: tocar numa categoria agora abre uma janela com o mapa **só daquela categoria** (e o botão **Definir limite**, que abre o formulário de limite de sempre).
- **Calendário:** um quadrado por dia (dia da semana correto; 28, 29, 30 ou 31 dias), com o número do dia e o total gasto (R$ abreviado: 205, 1,2k…). Setas ‹ › trocam o mês e tudo é recalculado.
- **Cores (azul):** sem gasto = neutro; 4 faixas do amarelo ao vermelho (v7.10). A faixa é calculada **entre os dias com gasto do próprio mês** (posição de cada dia no ranking, em 4 partes iguais): sem limites fixos e sem que um dia enorme "apague" os outros. Se só um dia tem gasto, ele fica na faixa 3.
- **Tocar num dia:** destaca o quadrado (contorno âmbar) e mostra embaixo a data por extenso, o total do dia, a quantidade e a lista (descrição, categoria, valor). Tocar numa despesa abre a edição que já existia; compra no cartão abre o cartão. Dia sem gasto: "Nenhum gasto registrado neste dia."
- **Indicadores:** total do mês, média por dia (mês atual: dividida pelos dias já passados), maior dia, comparação com o mês anterior (no mês atual compara o **mesmo período**; sem dados nos dois lados mostra "dados insuficientes") e uma observação automática sobre fim de semana × dias úteis (só com ≥ 5 dias com gasto, ≥ 3 fins de semana e ≥ 5 dias úteis no período, e diferença ≥ 10%; fala em gasto **por dia**).
- **O que conta como gasto (usa só os registros reais, sem criar nada):** despesas **marcadas como pagas** (no dia de vencimento delas; dia 31 em mês de 30 vai para o 30), **compras no cartão na data da compra** (parcelas nos meses seguintes, no mesmo dia da compra) e **parcelamentos pagos** (no dia do pagamento; só no mapa geral, pois parcelamentos não têm categoria). **Não contam:** receitas, despesas pendentes, valores zero, **pagamento de fatura** (para não duplicar as compras), dívidas e caixinhas. O Wolfin não tem estorno/cancelamento, então não há o que descontar.
- **Armazenamento:** nada novo é guardado. Tudo é calculado na hora a partir dos dados da conta (criptografados/isolados como sempre). Sem internet, sem serviços externos.
- Teste: `python3 tests/run_all.py --suite mapa_calor` (79 verificações).

## Versão 7.10 — avatares na cor do tema e mapa de calor quente
- **Avatares dos mascotes:** o fundo circular azul fixo foi removido. Agora vem de duas variáveis centrais (`--av1`/`--av2`, definidas uma vez no `:root`) calculadas a partir da cor principal escolhida em Ajustes (9 cores, claro e escuro). Vale para a Home, o seletor de mascotes, Ajustes → Trocar de mascote e a escolha do cadastro. O destaque do mascote selecionado também segue a cor do tema. As imagens dos mascotes não foram alteradas.
- **Mapa de calor:** escala quente — sem gasto neutro, 1 amarelo suave, 2 amarelo-alaranjado, 3 laranja, 4 vermelho (versões própria para claro e escuro). A legenda usa as mesmas classes. O dia selecionado tem contorno neutro (cor do texto do tema), sem confundir com a intensidade.
- **Regra do maior dia:** o dia de maior gasto do mês sempre fica na faixa vermelha (antes, com poucos dias com gasto, podia ficar laranja). O restante do cálculo de intensidade não mudou.
- Teste: `python3 tests/run_all.py --suite tema_avatares_calor` (60 verificações). Regressão completa: 33 suítes, 1416 verificações.

## Versão 7.11 — data real do pagamento das parcelas
- **Editar parcela** ganhou o campo **Data do pagamento** (calendário, qualquer data, passada ou futura), logo abaixo do vencimento. Só aparece quando o status é **Pago**; ao escolher Pago ele sugere hoje, mas dá para mudar. Em parcela já paga carrega a data guardada. Pago → Pendente apaga a data.
- O botão ✓ da lista de parcelas agora abre uma janelinha "Registrar pagamento" com a data (hoje por padrão) antes de confirmar. O botão ↺ volta para pendente e remove a data.
- Parcelas antigas pagas com data errada (ex.: 15/11/2026): abra a parcela, toque em **Editar** e escolha a data real. Nada é corrigido automaticamente; parcelas pagas sem data continuam sem data até você informar (a lista mostra "pago (data não registrada)").
- Vencimento (`due`) e pagamento (`paidOn`) são independentes. A parcela não tem "data de registro" guardada, então nada foi inventado.
- Mapa de calor, totais por dia, relatórios, saldo e comparações mensais já usavam `paidOn`; agora refletem a data que você corrigir. Sem duplicação (mesma lógica de antes).
- Estrutura de dados: **nenhuma chave nova** — `S.parc[i].paidOn` (AAAA-MM-DD) já existia. Backups e senhas continuam compatíveis.
- Teste novo: `tests/suites/parcelas_data_pagamento.py`.

## Versão 7.12 — vencimento fixo no parcelamento, pagamento por parcela
- **Vencimento**: definido uma vez no parcelamento (campo "Dia de vencimento", só o dia do mês). Cada parcela mostra o vencimento calculado (dia 31 em mês curto cai no último dia). Na edição da parcela agora aparece só o texto **Dia de vencimento: 05/06/2026**.
- **Exceção**: link discreto **Alterar só esta parcela** abre uma lista de dias; só aquela parcela muda (aparece "exceção desta parcela"). "Padrão do parcelamento" volta ao normal.
- **Pagamento**: continua o calendário completo individual (v7.11). Edição agora tem 1 calendário só. Ordem: Mês, vencimento, pagamento, valor, status.
- Dados: **nenhuma chave nova**. `S.parc[i].due` continua sendo gravado ao criar parcelas e guarda exceções/vencimentos antigos; parcelas antigas sem `due` apenas **exibem** o vencimento calculado (nada é gravado ou presumido). Parcelamento sem dia e parcela sem vencimento aparece "não definido".
- Ao mudar o dia do parcelamento, só parcelas **pendentes sem exceção** que tinham o vencimento padrão acompanham; pagas, exceções e parcelas sem data não mudam.
- Teste novo: `tests/suites/parcelas_vencimento_fixo.py`.

## Versão 7.13 — despesas fixas por dia do mês, variáveis por data
- **Fixa (todo mês)**: no lugar do calendário aparece **Dia do vencimento** (lista de 01 a 31). O dia se repete todo mês; em mês curto vale o último dia (31 → 28/29 em fevereiro, 30 em abril…). Ao editar, carrega o dia já configurado.
- **Variável**: mantém o calendário completo, com a data exata da despesa. Sem repetição.
- Trocar o tipo no formulário troca o campo na hora. Texto de ajuda abaixo: "Fixa: dia do vencimento, repetido todos os meses. Variável: data exata da despesa."
- **Mudar o dia de uma fixa** vale a partir do mês que você está vendo; os meses anteriores continuam com o dia que tinham (e os pagamentos já registrados não mudam).
- Dados: um campo opcional novo, `dh` (histórico de dias, só em despesas fixas que tiveram o dia alterado): lista `[mês, dia antigo]`. Despesas existentes não são alteradas. Receitas não mudaram.
- Teste novo: `tests/suites/despesas_fixa_variavel.py`.

## Versão 7.14 — sem intro, nova logo do lobo
- **Intro removida**: o app abre direto na tela de boas-vindas/login (sem vídeo, sem animação inicial, sem botão de som). Saíram o código, o estilo, o tratamento do vídeo no Service Worker e os arquivos `intro-wolfin.mp4` e `intro-wolfin.webm` (você pode apagá-los do repositório).
- **Nova logo** (a imagem do ícone enviada): ícone do app (192/512), ícone "maskable", ícone da tela inicial do iPhone (apple-touch-icon), favicons 32/48 e o quadradinho do "Sobre". Os nomes dos arquivos são os mesmos.
- Paletas de cores, temas e as outras telas não mudaram (as 64 regras de paleta são idênticas às da v7.13; as regras de contraste de `.pos` e do balão do mascote, que estavam na mesma linha de CSS da intro, foram mantidas).
- Nota: depois de atualizar, o ícone já instalado na tela inicial só troca quando o Android/iPhone renovar o atalho (às vezes é preciso remover e adicionar de novo à tela inicial).
- Teste novo: `tests/suites/sem_intro_logo.py` (a suíte `intro_wolfin` foi retirada).

## Versão 7.16 — intro em vídeo do lobo (a v7.15 foi substituída)
- A intro agora é o vídeo enviado (lobo + WOLFIN + "Controle seu dinheiro", ~3,9 s), em tela cheia. Começa **sem som** (o navegador exige); o **botão de som** (canto superior direito) liga e desliga, e a escolha fica lembrada (se você deixou ligado, tenta começar com som; se o navegador bloquear, toca mudo).
- **Transição suave**: nos últimos ~0,5 s a imagem desvanece (e o volume também) revelando o app por baixo, sem corte seco. Tocar na tela ou apertar uma tecla pula (com desvanecer rápido).
- **Mais leve, mesma qualidade**: o original tinha 3,4 MB; agora são `intro-lobo.mp4` (≈490 KB, H.264+AAC) e `intro-lobo.webm` (≈355 KB, reserva), ambos na resolução original 720x1280 (qualidade medida contra o original: PSNR ≈ 51 dB, ou seja, sem diferença visível).
- Uma vez por sessão; recarregar não repete. Com "reduzir movimento" no aparelho, vai direto ao app. Se o vídeo não carregar, a intro some sozinha (o app nunca fica preso). Funciona offline (o vídeo fica guardado no cache do app).
- Os arquivos `intro-lobo.mp4` e `intro-lobo.webm` precisam subir junto com `index.html` e `sw.js`.
- Teste novo: `tests/suites/intro_video.py` (35 verificações); a suíte `intro_minimalista` (v7.15) foi retirada.

## Versão 7.17 — acabamentos (auditoria de uso)
Só ajustes de uso; nenhuma função foi removida e **nenhum dado mudou de formato** (as contas e os backups continuam compatíveis).
- **Saldo da Home que fecha**: o cartão mostra Recebido, Pago e (quando houver) Guardado e dívidas do mês, mais a frase "Inclui R$ X de saldo inicial e de outros meses". Conta: anterior + recebido − pago − guardado/dívidas = saldo.
- **Calculadora/ferramentas rápidas**: começa no canto inferior direito, logo acima do menu, mais discreta (um pouco transparente). Uma dica "arraste este botão" aparece **uma única vez** por aparelho. Quem já tinha mudado o botão de lugar mantém a posição escolhida.
- **Home mais curta**: saiu a repetição de "Dívidas pendentes" e "Dinheiro guardado" (continuam nas seções logo abaixo) e a frase da marca dentro do saldo; "Este mês" (gráfico) foi para o fim.
- **Saudação curta**: "Bom dia/Boa tarde/Boa noite, Nome!".
- **Listas sem botões soltos**: em Receitas e Despesas, tocar na linha abre a edição, e **Excluir fica dentro da edição** (com a mesma confirmação). Parceladas, Dívidas e Caixinhas ganharam um ✎ no cabeçalho; ficam na tela só as ações do dia a dia (Pagar, Histórico, Guardar, Retirar…). O botão ✓/↺ continua marcando direto.
- **Despesas**: "Já pagas" e "Previstas no mês" (a nota sobre faturas de cartão só aparece se houver cartão); ordem Fixas → Variáveis → Parceladas.
- **Relatórios** (de ≈6.650 px para ≈2.960 px): "Indicadores do mês" e "Despesas por categoria" deixaram de repetir o que já existia — o que era único (dívidas vencidas, limites por categoria) foi para o bloco de contas do mês, e "Gastos por categoria" ficou como a lista de categorias. As seções extras ficaram recolhidas e lembram se estão abertas: Despesas que se repetem, Evolução das dívidas, Comparar dois meses, Mapa de calor, Gráficos do ano e Resumo para compartilhar. Um "?" explica o "Saldo no início do mês".
- **Ajustes**: ordem Backup → Segurança → Aparência → Mascote → Zerar → Sobre; paletas, vidro e animações ficam em "Cores, vidro e animações" (Claro/Escuro continuam à vista). O rodapé não mostra mais texto de desenvolvedor. "Meu mascote" ganhou o botão "Ver conquistas".
- **Conquistas**: mostra as conquistadas e as 3 próximas; as demais ficam em "Ver as outras N conquistas".
- **Fontes**: nada abaixo de 11 px (barra inferior, mapa de calor, eixos dos gráficos), exceto a barra inferior em telas de 320 px, que fica em 9 px para caber.
- Teste novo: `tests/suites/acabamentos_v717.py` (66 verificações). Regressão completa da v7.17: 1.570 verificações em 38 suítes, 0 falhas (Chromium simulado). Ajustados por mudança intencional: marca_wolfin, correcoes_auditoria, relatorios, acessibilidade, auditoria_geral, ferramentas_rapidas e as suítes que abrem o mapa de calor.

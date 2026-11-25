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


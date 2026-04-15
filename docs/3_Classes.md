
### 📌 Entidades do Domínio e Atributos

**1. Aluno** *(RF01, RF04, RF05, RF06, RF10)*
* idAluno
* nome
* cpf
* email
* telefone
* endereco
* rfid
* status

**2. Plano** *(RF01, RF02, RF04)*
* idPlano
* nome
* tipo
* valor
* ativo

**3. Pagamento** *(RF03, RF04, RF09)*
* idPagamento
* data
* valor
* formaPagamento
* status

**4. Acesso** *(RF05, RF09)*
* idAcesso
* dataHora
* autorizado

**5. Aula** *(RF06, RF07, RF09)*
* idAula
* nome
* horario
* capacidadeMaxima

**6. Agendamento** *(RF06, RF10)*
* idAgendamento
* dataReserva
* status

**7. Presenca** *(RF07)*
* idPresenca
* data
* presente

**8. AvaliacaoFisica** *(RF08, RF10)*
* idAvaliacao
* data
* peso
* imc
* percentualGordura
* observacoes
* anexo

**9. Notificacao** *(RF10)*
* idNotificacao
* tipo
* dataEnvio
* status
* mensagem

**10. Instrutor** *(RF07, RF08)*
* idInstrutor
* nome
* especialidade

**11. Recepcionista** *(RF01, RF03)*
* idRecepcionista
* nome

**12. Gerente** *(RF02, RF09)*
* idGerente
* nome

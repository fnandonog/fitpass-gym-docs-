# FitPass Gym Management - Modelagem do Sistema

Este repositório contém a modelagem de domínio e de casos de uso para o sistema FitPass, atendendo aos requisitos funcionais (RF01 a RF10).

---

## 1. Diagrama de Casos de Uso

Abaixo está o código PlantUML que modela as interações dos atores com o sistema:

```plantuml
@startuml
left to right direction

actor Aluno
actor Instrutor
actor Gerente
actor Recepcionista
actor "Sistema de Controle de Acesso" as Catraca

rectangle "FitPass Gym Management" {

  Aluno -- (Agendar aula)
  Aluno -- (Realizar pagamento online)
  Aluno -- (Visualizar horários de aula)

  Recepcionista -- (Cadastrar aluno)
  Recepcionista -- (Registrar pagamento presencial)

  Instrutor -- (Registrar presença)
  Instrutor -- (Registrar avaliação física)

  Gerente -- (Gerenciar planos)
  Gerente -- (Emitir relatórios gerenciais)

  Catraca -- (Validar acesso do aluno)

  (Validar acesso do aluno) ..> (Verificar regularidade do aluno) : <<include>>
  (Registrar pagamento presencial) ..> (Verificar regularidade do aluno) : <<include>>
  (Realizar pagamento online) ..> (Verificar regularidade do aluno) : <<include>>

  (Agendar aula) <.. (Enviar notificação) : <<extend>>
  (Registrar avaliação física) <.. (Enviar notificação) : <<extend>>
  (Registrar pagamento presencial) <.. (Enviar notificação) : <<extend>>
  (Realizar pagamento online) <.. (Enviar notificação) : <<extend>>
}
@enduml

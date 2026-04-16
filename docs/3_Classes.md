# 3. Modelagem de Classes

## 3.1. Esboço das Classes (Skeleton)
Estrutura inicial em código exigida para o domínio:

```java
class Aluno {}
class Plano {}
class Pagamento {}
class Acesso {}
class Aula {}
class Agendamento {}
class Presenca {}
class AvaliacaoFisica {}
class Notificacao {}

abstract class Funcionario {}
class Instrutor extends Funcionario {}
class Recepcionista extends Funcionario {}
class Gerente extends Funcionario {}
```

---

## 3.2. Dicionário de Dados e Atributos
Mapeamento das entidades com seus atributos baseados nos Requisitos Funcionais:

**Aluno** (RF01, RF04, RF05, RF06, RF10)
* idAluno, nome, cpf, email, telefone, endereco, rfid, status

**Plano** (RF01, RF02, RF04)
* idPlano, nome, tipo, valor, ativo

**Pagamento** (RF03, RF04, RF09)
* idPagamento, data, valor, formaPagamento, status

**Acesso** (RF05, RF09)
* idAcesso, dataHora, autorizado

**Aula** (RF06, RF07, RF09)
* idAula, nome, horario, capacidadeMaxima

**Agendamento** (RF06, RF10)
* idAgendamento, dataReserva, status

**Presenca** (RF07)
* idPresenca, data, presente

**AvaliacaoFisica** (RF08, RF10)
* idAvaliacao, data, peso, imc, percentualGordura, observacoes, anexo

**Notificacao** (RF10)
* idNotificacao, tipo, dataEnvio, status, mensagem

**Instrutor** (RF07, RF08)
* idInstrutor, nome, especialidade

**Recepcionista** (RF01, RF03)
* idRecepcionista, nome

**Gerente** (RF02, RF09)
* idGerente, nome

---

## 3.3. Diagrama de Classes do Domínio
*Abaixo está a representação visual do relacionamento entre as classes, gerada via Mermaid.*

```mermaid
classDiagram
    class Aluno {
        -String idAluno
        -String nome
        -String cpf
        -String email
        -String telefone
        -String endereco
        -String rfid
        -String status
    }

    class Plano {
        -String idPlano
        -String nome
        -String tipo
        -double valor
        -boolean ativo
    }

    class Pagamento {
        -String idPagamento
        -Date data
        -double valor
        -String formaPagamento
        -String status
    }

    class Acesso {
        -String idAcesso
        -Date dataHora
        -boolean autorizado
    }

    class Aula {
        -String idAula
        -String nome
        -String horario
        -int capacidadeMaxima
    }

    class Agendamento {
        -String idAgendamento
        -Date dataReserva
        -String status
    }

    class Presenca {
        -String idPresenca
        -Date data
        -boolean presente
    }

    class AvaliacaoFisica {
        -String idAvaliacao
        -Date data
        -double peso
        -double imc
        -double percentualGordura
        -String observacoes
        -String anexo
    }

    class Notificacao {
        -String idNotificacao
        -String tipo
        -Date dataEnvio
        -String status
        -String mensagem
    }

    class Funcionario {
        <<abstract>>
        -String nome
    }
    
    class Instrutor {
        -String idInstrutor
        -String especialidade
    }
    
    class Recepcionista {
        -String idRecepcionista
    }
    
    class Gerente {
        -String idGerente
    }

    %% Heranças
    Funcionario <|-- Instrutor
    Funcionario <|-- Recepcionista
    Funcionario <|-- Gerente

    %% Relacionamentos
    Aluno "1" -- "0..*" Plano : contrata
    Aluno "1" -- "1..*" Pagamento : realiza
    Aluno "1" -- "0..*" Acesso : possui
    Aluno "1" -- "0..*" Agendamento : faz
    Aluno "1" -- "0..*" AvaliacaoFisica : recebe
    Aluno "1" -- "0..*" Notificacao : recebe
    
    Agendamento "0..*" -- "1" Aula : pertence
    Aula "1" -- "1" Instrutor : ministrada por
    Aula "1" -- "0..*" Presenca : gera
    
    Instrutor "1" -- "0..*" AvaliacaoFisica : realiza
    
    Recepcionista "1" -- "0..*" Pagamento : processa
    Gerente "1" -- "0..*" Plano : gerencia
```
```

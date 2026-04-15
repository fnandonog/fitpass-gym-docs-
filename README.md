# Diagrama de Classes - FitPass Gym Management

Este é o diagrama de domínio do sistema da academia, baseado nos requisitos funcionais solicitados.

```mermaid
classDiagram
    class Pessoa {
        <<abstract>>
        -String nome
        -String cpf
        -String email
        -String telefone
    }

    class Aluno {
        -String rfid
        -String endereco
        -boolean inadimplente
        +verificarRegularidade()
    }

    class Funcionario {
        <<abstract>>
        -String matricula
    }

    class Instrutor {
        -String cref
        +registrarPresenca()
        +registrarAvaliacao()
    }

    class Gerente {
        +gerarRelatorioInadimplencia()
        +gerarRelatoriosAtivos()
        +gerarRelatorioOcupacao()
    }

    class Plano {
        -String nome
        -String tipoPlano
        -double valorMensal
        -boolean ativo
    }

    class Contrato {
        -Date dataInicio
        -Date dataFim
        -boolean ativo
    }

    class Pagamento {
        -double valor
        -Date dataVencimento
        -Date dataPagamento
        -String metodoPagamento
        -String status
    }

    class Aula {
        -String modalidade
        -Date dataHora
        -int vagasTotais
        -int vagasDisponiveis
    }

    class Agendamento {
        -Date dataReserva
        -boolean presencaConfirmada
    }

    class AvaliacaoFisica {
        -Date data
        -double peso
        -double imc
        -double percentualGordura
        -String caminhoArquivoAnexo
    }

    class Acesso {
        -Date dataHora
        -boolean liberado
        -String motivoBloqueio
    }

    class Notificacao {
        -String tipo
        -String mensagem
        -Date dataEnvio
    }

    Pessoa <|-- Aluno
    Pessoa <|-- Funcionario
    Funcionario <|-- Instrutor
    Funcionario <|-- Gerente

    Aluno "1" -- "0..*" Contrato : assina
    Plano "1" -- "0..*" Contrato : contem
    Contrato "1" -- "1..*" Pagamento : gera

    Aluno "1" -- "0..*" Acesso : realiza
    Aluno "1" -- "0..*" Notificacao : recebe

    Aluno "1" -- "0..*" Agendamento : faz
    Aula "1" -- "0..*" Agendamento : possui
    Instrutor "1" -- "0..*" Aula : ministra

    Aluno "1" -- "0..*" AvaliacaoFisica : submetido
    Instrutor "1" -- "0..*" AvaliacaoFisica : realiza

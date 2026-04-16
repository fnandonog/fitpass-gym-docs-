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

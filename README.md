# Atividade Teórica: Regra de Negócio no BD versus na Aplicação

**Aluno(s):** Pietro Gonzaga, , Nome3
**Turma:** Banco de Dados 2026
**Data:** ../../2026
**Repositório Git:** https://github.com/usuario/atividade-bd

## Resumo Executivo

Breve descrição do tema e da posição adotada pelo grupo.

## 1. Desenvolvimento Teórico

### 1.1 O que é regra de negócio?
Por definição, regra de negócio é uma diretriz, política ou restrição que define como processos devem ocorrer dentro de uma empresa
para garantir eficiência, segurança e conformidade. Em termos simples, é como uma empresa deve realizar suas atividades dentro da lei e de forma organizada.

Seus tipos de regras de negócios incluem:
1. Controle de Dados e Integridade (garante a informação seja útil, verdadeira e confiável).
   Ex.: Nenhum cliente pode ser cadastrado sem um CPF ou CNPJ válido.
2. Operações de Vendas (define os limites de atuação da equipe comercial e protege a margem de lucro).
   Ex.: Um vendedor só pode conceder até 10% de desconto a um cliente.
3. Estoque e Logística (garante que não falte estoque).
   Ex.: Caso o estoque de uma empresa chegue à uma certa quantidade, digamos 20, é fornecido, automaticamente, uma ordem de compra ao fornecedor.
4. RH e Financeiro (garante conformidade com leis trabalhistas e contratos).
   Ex.: Um empregado não pode solicitar férias com menos de 12 meses de empresa. 

### 1.2 Regras no banco de dados
1. Constraints
   - CHECK: Determina uma condição que precisa ser verdadeira para que o registro seja aceito.
     vantagem: A regra é garantida pelo próprio banco, independentemente da aplicação.
     desvantagem: Se a regra for muito complexa, pode ser difícil ou impossível de representá-la apenas como CHECK.
   - Foreign Key: Estabelece uma relação entre tabelas.
     vantagem: Impede a referência a registros inexistentes.
     limitação: Dificulta alterações e exclusões quando existem muitos relacionamentos.
   - UNIQUE: Garante que nenhum valor seja repetido.
     vantagem: Impede duplicidades diretamente no Banco.
     limitação: Aumenta o custo de armazenamento e a manutenção de índices.
2. Triggers: São executados automaticamente quando ocorre determinado evento.
   - vantagens: Automatizam tarefas, podem criar logs de criação e funcionam quando os dados são alterados por diferentes aplicações.
   - limitações: Pode dificultar a manutenção e a identificação de erros.
3. Stored Procedures: Conjunto de instruções armazenamento armazenado no banco de dados.
   - vantagens: Reutilização de código, centralização de operações, limitação direta à tabelas, redução da quantidade de SQL enviada pela aplicação.
4. Transações ACID: Representa 4 propriedades:
   1. Atomicidade: A transação acontece por completo ou não acontece.
   2. Consistência: A transação deve manter o banco em um estado válido.
   3. Isolamento: Transações simultâneas não devem interferir indevidamente umas nas outras.
   4. Durabilidade: Depois de confirmada, a alteração deve permanecer mesmo em caso de falha.
   - vantagem: Evita situações em que apenas parte de uma operação é realizada.
   - limitação: Maior consumo de recursos e redução de desempenho em determinadas situações. 


### 1.3 Regras na aplicação
1. Validação de entradas: Verificam se os dados fornecidos são válidos antes de serem utilizados.
   - vantagem: Impede que dados incorretos cheguem ao banco, permite apresentar mensagem de erro ao usuário e ajuda na prevenção de dados maliciosos.
   - limitação: A validação na aplicação não substitui as restrições do banco de dados.
2. Camadas de serviço: Fica entre a interface da aplicação e o acesso aos dados.
   - vantagens: Centraliza as regras de negócios, facilita testes e manutenção e separa responsabilidades.
   - limitações: Aumenta a complexidade do projeto e adiciona uma camada à arquitetura.
3. Frameworks: Fornece estruturas e ferramentas prontas para facilitar o desenvolvimento da aplicação.
   - vantagens: Acelera o desenvolvimento, ajuda a padronizar a estrutura do sistema e fornece soluções já testada para problemas comuns.
   - limitações: Pode haver dependência de uma tecnologia específica, atualizações podem exigir alterações no sistema e o dev precisa entender como o framework                      funciona.

### 1.4 Comparativo BD x Aplicação
1. Banco de Dados
   - consistência: Mais forte;
   - segurança: Proteção dos dados;
   - performance: Boa para integridade dos dados;
   - manutenção: Centralizada, mas pode ser complexa;
   - portabilidade: Pode depender do SGBD;
   - controle central da regra: Muito alto.
2. Aplicação
   - consistência: Depende da implementação;
   - segurança: Controle de acesso e usuários
   - performance: Boa para processamentos e validações
   - manutenção: Geralmente mais flexível
   - portabilidade: Geralmente maior
   - controle central: Depende da arquitetura

### 1.5 Análise crítica: qual a melhor opção?
O Banco de Dados é mais indicado para regras que precisam garantir integridade e consistência de dados.
A Aplicação é mais adequada para regras de negócio, validação complexa e lógica de processamento.
O ideal é o uso de forma híbrida: uma parte com o Banco de Dados, a outra, Aplicação.

## 2. Exemplos e Casos
1. Regra no Banco de Dados
   
Uma loja possui essas regras:
- O preço do produto deve ser maior que zero.
- A quantidade vendida deve ser maior que zero.
- Um pedido só pode existir para um cliente cadastrado.
- Um item do pedido só pode fazer referência a um produto existente.
- O e-mail do cliente não pode ser duplicado.

Digamos que alguém tente cadastrar o valor "-500", o Postgre vai negar, pois o preço deve ser maior que zero.
Da mesma forma, caso alguém tente criar um pedido para um cliente inexistente, pois a FK exige que o cliente exista.

2. Regra na Aplicação

Agora, digamos que um cliente só possa efetuar um pedido, caso o valor total da compra passe de R$ 20,00.
Nesse caso, a Aplicação vai verificar se a solicitação faz sentido para o negócio e o BD garante que os dados armazenados respeitem as regras de identidade.

## 3. Referências

Fontes consultadas: Material do curso (Int. a Banco de Dados) e ChatGPT. 

## 4. Conclusões

Uma boa solução é dividir as tarefas. Vimos que o BD é recomendável para certas coisas e a Aplicação para outras. Isso, também, serve não apenas para o mundo de Banco de Dados, mas para toda a programação e as profissões, vida acadêmica e social no geral. Um modo de agir, pensar ou executar nem sempre vai ser a única solução para certo problema. Por isso, o ideal é combinar soluções diferentes, como vimos nesse trabalho.

## Link do Repositório Git

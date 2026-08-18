# Atividade Teórica: Regra de Negócio no BD versus na Aplicação

**Aluno(s):** Nome1, Nome2, Nome3
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
Validação de entradas, camadas de serviço, frameworks — vantagens e limitações.

### 1.4 Comparativo BD x Aplicação
Tabela comparativa: consistência, segurança, performance, manutenção,
portabilidade, controle central da regra.

### 1.5 Análise crítica: qual a melhor opção?
Posição fundamentada do grupo e condições em que cada abordagem se aplica.

## 2. Exemplos e Casos

Exemplo em PostgreSQL (regra no BD) e exemplo de validação na aplicação
(pseudocódigo ou código). Um caso real: sistema de vendas, clínica ou biblioteca.

## 3. Referências

Fontes consultadas (livros, artigos, documentação oficial do PostgreSQL, materiais do curso).

## 4. Conclusões

Aprendizados, reflexões e principais pontos observados pelo grupo.

## Link do Repositório Git

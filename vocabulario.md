Nome: Eduardo C. Ceretta

1) No seu github pessoal, criar um repositório de banco de dados (caso ainda não exista) e dentro dele um arquivo chamado vocabulario.md. Nele preencher o significado das expressões abaixo, mantendo o texto ordenado:
 - sistema gerenciador de banco de dados:
    SGBD é um sistema que gerencia banco de dados, é responsável por acessar, organizar, e proteger as informações contidas no banco, além de tirar a responsabilidade do usuário.
	
 - restrições em banco de dados
    As principais são chaves primarias, integridade referêncial (chaves estrangeiras), triggers, restrições exclusivas, restrições de verificação e restrição nulo.
	
 - modelo relacional
   É um conjunto de informações armazenados em tabelas, que se conectam entre si. Esses relacionamentos entre as tabelas, são conexões lógicas que conectam com base nas suas interações.
   
	- modelagem conceitual
    Descreve as principais entidades e os relacionamentos entre elas, para que seja mais fácil de compreender pelas partes envolvidas no projeto.
   
	- modelagem lógica
   É uma versão mais elaborada do modelo conceitual, representa detalhadamente restrições, nomes de entidades e seus relacionamentos para que possam ser implementados em qualquer plataforma
   
	- modelagem física
    Mostra o design real do banco, são feitas as tabelas e determinadas restrições como cheves primárias e estrangeiras.
   
	- linguagem SQL
  linguagem projetada para acessar as informações no banco de dados, fazer a manipulação dos dados, fazer update e deletar dados.
   
	- Data Definition Language (DDL)
    É ma subconjunto de SQL para criar e modificar objetos no banco de dados, como tabelas, usuariose indices.
   
	- Data Manipulation Language (DML)
    Linguagem usada para adicionar, deletar e modificar os dados no banco.
   
	- Boas práticas em modelagem de banco de dados
    Criação de restrições, deixar somente uma chave primária em cada tabela, verificar o banco para que não haja redundância de informações, utilizar nomes que expressem o significado de cada tabela para melhor legibilidade do código.

Todos os clientes armazenados no sistema:

select *
from cliente
order by nome;

Exiba os veículos que tenham final 3 no número da placa

select *
from veiculo
where placa like '%3'; 

Mostre os clientes que residem no RS e que não possuam telefone

select * 
from cliente
where uf_cnh = 'RS' 
and telefone is null;

Exiba o código dos clientes que alugaram veículos por mais de 90 dias.

select cliente.id_cliente
from cliente
inner join contrato_aluguel
on contrato_aluguel.id_cliente = cliente.id_cliente
where contrato_aluguel.duracao > 90;

Quantos veículos há cadastrados no sistema
select count(*)
from veiculo;

Mostre o veículo alugado por Alexandre Zamberlan.

select veiculo.*
from veiculo
inner join contrato_aluguel
on veiculo.id_veiculo = contrato_aluguel.id_veiculo
inner join cliente
on contrato_aluguel.id_cliente = cliente.id_cliente
where cliente.nome = 'Alexandre Zamberlan';

Mostre os clientes e os escritórios associados no contrato de aluguel.

select distinct cliente.nome, escritorio.nome
from contrato_aluguel
inner join cliente
on cliente.id_cliente  = contrato_aluguel.id_cliente
inner join escritorio
on contrato_aluguel.id_escritorio = escritorio.id_escritorio;

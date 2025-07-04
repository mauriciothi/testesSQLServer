# DBA Challenge 20240802


## Introdução

Nesse desafio trabalharemos utilizando a base de dados da empresa Bike Stores Inc com o objetivo de obter métricas relevantes para equipe de Marketing e Comercial.

Com isso, teremos que trabalhar com várioas consultas utilizando conceitos como `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `GROUP BY` e `COUNT`.

### Antes de começar
 
- O projeto deve utilizar a Linguagem específica na avaliação. Por exempo: SQL, T-SQL, PL/SQL e PSQL;
- Considere como deadline da avaliação a partir do início do teste. Caso tenha sido convidado a realizar o teste e não seja possível concluir dentro deste período, avise a pessoa que o convidou para receber instruções sobre o que fazer.
- Documentar todo o processo de investigação para o desenvolvimento da atividade (README.md no seu repositório); os resultados destas tarefas são tão importantes do que o seu processo de pensamento e decisões à medida que as completa, por isso tente documentar e apresentar os seus hipóteses e decisões na medida do possível.
 
 

## O projeto

- Criar as consultas utilizando a linguagem escolhida;
- Entregar o código gerado do Teste.

### Modelo de Dados:

Para entender o modelo, revisar o diagrama a seguir:

![<img src="samples/model.png" height="500" alt="Modelo" title="Modelo"/>](samples/model.png)


## Selects

Construir as seguintes consultas:

- Listar todos Clientes que não tenham realizado uma compra;
select a.*
from customers a
where not exists ( select *  
                   from orders b
                   where b.customer_id  a.customer_id )

  
- Listar os Produtos que não tenham sido comprados
select a.
from products a
where not exists ( select *
                   from order_items b
                   where b.product_id = a.product_id )

  
- Listar os Produtos sem Estoque;
select a.
from  products a
inner join stocks b
on b.product_id = a.product_id
where b.quantity = 0 

  
- Agrupar a quantidade de vendas que uma determinada Marca por Loja.
select c.brand_id,
       a.store_id,
       count(a.order_id) as quantidade
from orders a
inner join orders_item b
on b.order_id = a.order_id
inner join products c
on c.product_id  b.product_id
group by c.brand_id, a.store_id


- Listar os Funcionarios que não estejam relacionados a um Pedido.
select a.*
from staffs a
where not exists ( select *
                   from order_id b
                   where b.staff_id = a.staff_id )


## Readme do Repositório

- Deve conter o título do projeto
- Uma descrição sobre o projeto em frase
- Deve conter uma lista com linguagem, framework e/ou tecnologias usadas
- Como instalar e usar o projeto (instruções)
- Não esqueça o [.gitignore](https://www.toptal.com/developers/gitignore)
- Se está usando github pessoal, referencie que é um challenge by coodesh:  

>  This is a challenge by [Coodesh](https://coodesh.com/)

## Finalização e Instruções para a Apresentação

1. Adicione o link do repositório com a sua solução no teste
2. Verifique se o Readme está bom e faça o commit final em seu repositório;
3. Envie e aguarde as instruções para seguir. Caso o teste tenha apresentação de vídeo, dentro da tela de entrega será possível gravar após adicionar o link do repositório. Sucesso e boa sorte. =)


## Suporte

Para tirar dúvidas sobre o processo envie uma mensagem diretamente a um especialista no chat da plataforma. 

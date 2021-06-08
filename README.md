# Repositorio All For One

# Proposta.

Eesse projeto é uma série de desafios com diferentes níveis de complexidade que devem ser resolvidos cada um em seu arquivo próprio.

# Instruções para restaurar o banco de dados `Northwind`

### Caso queira testar as queries na sua maquina é preciso ter o banco de dados `Northwind` para isso siga as seguintes instruções.

1. Faça o download do arquivo de backup [aqui](northwind.sql) clicando em "Raw", depois clicando com botão direito e selecionando "Salvar como" para salvar o arquivo em seu computador.
2. Abra o arquivo com algum editor de texto, e selecione todo o conteúdo do arquivo usando `CTRL-A`.
3. Abra o MySQL Workbench.
4. Abra uma nova janela de query e cole dentro dela todo o conteúdo do arquivo `northwind.sql`.
5. Selecione todo o código com o atalho `CTRL-A` e depois clique no icone de trovão para executar a query.

    ![Restaurando o banco Northwind](images/restore_northwind.png)
6. Aguarde alguns segundos (espere em torno de 30 segundos antes de tentar fazer algo).
7. Clique no botão apontado na imagem a seguir para atualizar a listagem de banco de dados.

    ![Tabelas do banco Northwind](images/refresh_databases.png)
7. Verifique se o banco restaurado possui todas as seguintes tabelas:

    ![Tabelas do banco Northwind](images/northwind.png)
8. Clique com botão direito em cada tabela e selecione "Select Rows" e certifique-se que todas as tabelas possuem registros. Caso tenha alguma faltando, faça o passo a seguir. Caso contrário, pode ir para próxima seção.
9. Caso existam tabelas faltando, drope o banco de dados, clicando com o botão direito em cima do banco de dados northwind e selecionando "Drop Schema", e refaça os passos novamente, dessa vez aguardando um tempo maior quando executar o script de restauração.

    ![Drop Schema](images/drop_database.png)

---

## Implementações técnicas

Para executar localmente os testes, é preciso escrever o seguinte no seu terminal:
```sh
MYSQL_USER=<SEU_NOME_DE_PESSOA_USUARIA> MYSQL_PASSWORD=<SUA SENHA> HOSTNAME=<NOME_DO_HOST> npm test
```

Ou seja, suponha que para poder acessar a base de dados feita neste projeto você tenha `root` como seu nome de pessoa usuária, `password` como senha e `localhost` como host. Logo, você executaria:
```sh
MYSQL_USER=root MYSQL_PASSWORD=password HOSTNAME=localhost npm test
```

Usando o exemplo anterior de base, suponha que você não tenha setado uma senha para `root`. Neste caso, você executaria:
```sh
MYSQL_USER=root MYSQL_PASSWORD= HOSTNAME=localhost npm test
  ```
---
# As queries presentes no repositorio cumprem os seguintes comportamentos:

1. Exibe apenas os nomes do produtos na tabela `products`.
2. Exibe os dados de todas as colunas da tabela `products`.
3. Exibe os valores da coluna que representa a primary key da tabela `products`.
4. Conta quantos registros existem em `product_name` de `products`.
5. Exibe os dados da tabela `products` a partir do quarto registro até o décimo terceiro, incluindo tanto um quanto o outro sem o uso de `where` e `order by`.
6. Exibe os dados das colunas `product_name` e `id` da tabela `products` de maneira que os resultados estejam em ordem alfabética dos nomes.
7. Mostra apenas os ids dos 5 últimos registros da tabela `products` (a ordernação é baseada na coluna `id`).
8. Faz uma consulta que retorna três colunas. Na primeira coluna, exibe a soma de `5 + 6` (essa soma é ser realizada pelo SQL). Na segunda coluna tem a palavra "de". E por fim, na terceira coluna, exibe a soma de `2 + 8` (essa soma é realizada pelo SQL). A primeira coluna é chamada de "A", a segunda coluna é chamada "Trybe" e a terceira coluna é chamada "eh". Não é usado colunas pre-existentes, apenas as que foram criadas na hora.

---

## filtragem de dados

9. Mostra todos os valores de `notes` da tabela `purchase_orders` que não são nulos.
10. Mostra todos os dados da tabela `purchase_orders` em ordem decrescente ordenados por `created_by` em que o `created_by` é maior ou igual a 3. E como critério de desempate para a ordenação, ordena também os resultados pelo `id` de forma crescente.
11. Exibe os dados de `notes` da tabela `purchase_orders` em que seu valor de "Purchase generated based on Order" está entre 30 e 39, incluindo tanto o valor de 30 quanto de 39.
12. Mostra as `submitted_date` de `purchase_orders` em que a `submitted_date` é do dia 26 de abril de 2006.
13. Mostra o `supplier_id` das `purchase_orders` em que o `supplier_id` seja 1 ou 3.
14. Mostra os `supplier_id` da `purchase_orders` em que o `supplier_id` seja de 1 a 3, incluindo tanto o 1 quanto o 3.
15. Mostra somente as horas (sem os minutos e os segundos) da `submitted_date` de todos registros de `purchase_orders`. Essa coluna é chamada de `submitted_hour`.
16. exibe a `submitted_date` das `purchase_orders` que estão entre `2006-01-26 00:00:00` e `2006-03-31 23:59:59`.
17. Mostra os registros das colunas `id` e `supplier_id` das `purchase_orders` em que os `supplier_id` sejam tanto 1, ou 3, ou 5, ou 7.
18. Mostra todos os registros de `purchase_orders` que tem o `supplier_id` igual a 3 e `status_id` igual a 2.
19. Mostra quantos pedidos foram feitos na tabela `orders` pelo `employee_id` igual a 5 ou 6, e que foram enviados através do método `shipper_id` igual a 2? a coluna é chamada de orders_count.

---

## manipulação de tabelas

20. Adiciona ao `order_details` uma linha com os seguintes dados: `order_id`: 69, `product_id`: 80, `quantity`: 15.0000, `unit_price`: 15.0000, `discount`: 0, `status_id`: 2, `date_allocated`: NULL, `purchase_order_id`: NULL e `inventory_id`: 129. Obs.: o `id` é incrementado automaticamente.
21. Adiciona, com um único `INSERT`, duas linhas ao `order_details` com os mesmos dados. Esses dados são novamente `order_id`: 69, `product_id`: 80, `quantity`: 15.0000, `unit_price`: 15.0000, `discount`: 0, `status_id`: 2, `date_allocated`: NULL, `purchase_order_id`: NULL e `inventory_id`: 129 (o `ìd` é incrementado automaticamente).
22. Atualiza os dados de `discount` do `order_details` para 15.
23. Atualiza os dados de `discount` da tabela `order_details` para 30 cuja `unit_price` é menor que 10.0000.
24. Atualiza os dados de `discount` da tabela `order_details` para 45 cuja `unit_price` é maior que 10.0000 e o id é um número entre 30 a 40.
25. Deleta todos os dados em que a `unit_price` da tabela `order_details` é menor que 10.0000.
26. Deleta todos os dados em que a `unit_price` da tabela `order_details` é maior que 10.0000.
27. Deleta todos os dados da tabela `order_details`.

---


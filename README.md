
📖 Livraria Saber - Modelagem de Banco de Dados MySQL
Este projeto contém o dump de um banco de dados MySQL chamado livraria_saber, modelado para um sistema de gestão de uma livraria que também comercializa itens de papelaria.

O banco de dados foi desenvolvido e testado utilizando o MySQL Workbench 8.0 e o MySQL Server 8.0.44.

🗄️ Estrutura do Banco de Dados (Schema)
O schema livraria_saber é composto pelas seguintes tabelas:

autor: Armazena informações sobre os autores dos livros.

editora: Armazena informações sobre as editoras dos livros.

livro: Contém os dados dos livros, incluindo o preço e a quantidade em estoque, com uma chave estrangeira para a tabela editora.

livro_autor: Tabela de associação N:M (muitos-para-muitos) que relaciona livro com autor, permitindo que um livro tenha vários autores e um autor tenha vários livros.

fornecedor: Armazena dados dos fornecedores dos itens de papelaria.

papelaria: Contém os dados dos itens de papelaria, incluindo preço e estoque, com uma chave estrangeira para a tabela fornecedor.

cliente: Armazena o cadastro dos clientes da livraria.

vendedor: Contém o cadastro dos vendedores/colaboradores.

venda: Armazena informações sobre cada transação de venda, incluindo data, valor total, forma de pagamento e chaves estrangeiras para cliente e vendedor.

item_venda: Tabela de detalhes para cada venda, listando os itens vendidos (livros ou papelaria), suas quantidades e o preço unitário. Possui uma restrição (CHECK) para garantir que cada item_venda se refira a apenas um livro ou apenas um item de papelaria.

💾 Arquivos SQL Inclusos
Os arquivos SQL fornecidos contêm as instruções CREATE TABLE e INSERT INTO para popular as tabelas, sendo a estrutura completa e dados de exemplo (Dumping Data).

Nome do Arquivo	Conteúdo Principal
Livraria_s.sql	O dump completo do banco de dados, incluindo todas as tabelas e dados.
livraria_saber_autor.sql	Definição da tabela autor e seus dados.
livraria_saber_cliente.sql	Definição da tabela cliente e seus dados.
livraria_saber_editora.sql	Definição da tabela editora e seus dados.
livraria_saber_fornecedor.sql	Definição da tabela fornecedor e seus dados.
livraria_saber_item_venda.sql	Definição da tabela item_venda e seus dados.
livraria_saber_livro.sql	Definição da tabela livro e seus dados.
livraria_saber_livro_autor.sql	Definição da tabela livro_autor e seus dados.
livraria_saber_papelaria.sql	Definição da tabela papelaria e seus dados.
⚙️ Como Utilizar
Para utilizar este banco de dados:

Instale o MySQL Server (versão 8.0 ou compatível).

Crie o Schema (Banco de Dados) chamado livraria_saber em seu servidor MySQL.

SQL
CREATE DATABASE livraria_saber;
USE livraria_saber;
Importe o Dump Completo:

Abra o arquivo Livraria_s.sql em um cliente MySQL (como o MySQL Workbench).

Execute todo o conteúdo do arquivo. Isso criará todas as tabelas e inserirá os dados de exemplo.

📝 Exemplos de Consultas (SQL)
Aqui estão alguns exemplos de consultas que podem ser executadas no banco de dados:

Descrição da Consulta	Comando SQL (Exemplo)
Consultar o nome do livro e sua editora.	SELECT l.titulo, e.nome AS editora FROM livro l JOIN editora e ON l.id_editora = e.id_editora;
Listar todos os itens e a quantidade vendida em uma venda específica (Ex: Venda 1).	SELECT l.titulo, p.nome, iv.quantidade FROM item_venda iv LEFT JOIN livro l ON iv.id_livro = l.id_livro LEFT JOIN papelaria p ON iv.id_papelaria = p.id_papelaria WHERE iv.id_venda = 1;
Encontrar todos os livros de um autor específico (Ex: Elena Castro).	SELECT l.titulo FROM livro l JOIN livro_autor la ON l.id_livro = la.id_livro JOIN autor a ON la.id_autor = a.id_autor WHERE a.nome = 'Elena Castro';

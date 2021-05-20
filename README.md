# Desafio javascript


##  Introdução:

Nesse desafio desenvolvemos um programa em Javascript com propósito de fazer um cadastro de CPF e Nome. Com o botão adicionar, esses dados foram inseridos a uma tabela. Essa tabela somente aceita valores não repetidos, tanto na parte do Nome como a de CPF. Em cada linha desta tabela ha um botão para remover dados inseridos caso seja necessário. Durante o desenvolvimento do desafio tivemos muitas dúvidas que foram todas resolvidas dentro da própria equipe, e isso gerou uma grande cooperação e aumento o espirito de equipe entre os envolvidos. O desafio foi de grande valia, pois uniu a teoria e a prática a respeito dos conceitos da linguagem Javascript.


    

## Comentários dos códigos:

![img](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSLY_EV9R41Cit_VOkZF7Ssj3w8hhlPirwEpw&usqp=CAU)   

HTML:


**O código HTML abaixo ele mostra a construção de dois campos que é Nome e CPF. Esses elementos serão inseridos dentro de uma tabela apos de clicar no botão Adicionar .**


	<head>
		<title>Desafio</title>
	</head>

	<body>
		<h2>Desafio Javascript</h2>
		<p>
			CPF: <input type="number" id="txtCPF" name="txtName" maxlength="11" />
			NOME: <input type="text" id="txtNome" name="txtNome" />
			<input type="button" id="buttonAdicionar" value="Adicionar" onclick="AdicionarLinha()" />
		</p>

		<table id="tabelaClientes" name="tabelaClientes" border="1">
			<tr>
				<td><strong>CPF</strong></td>
				<td><strong>NOME</strong></td>
				<td><strong>REMOVER</strong></td>
			</tr>
		</table>
	</body>
  

 
 ![img](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSsiT6IVZqxwjYFgAdhl8PeiYtcAo7mTAOEqg&usqp=CAU)     
 
   Javascript:
    
  **Nessa linha de código o ocorrido é que o var arrayTabela que sera responsável por inserir os dados tanto Cpf como Nome dentro da tabela. E a função de AdicionarLinha() ela sera capaz de verificar se esses dados que vão ser inseridos na tabela se estão combinando com as regras e caso sim serão adicinados **

  `var arrayTabela = [];`
  
  `function AdicionarLinha() { `
  
  **Essas variáveis tanto CPF como Nome vão receber valores. E esse if ele é responsável por verificar se o valor digitado em algum dos campos é vazio.**

    var cpf = document.getElementById("txtCPF").value;
    var nome = document.getElementById("txtNome").value;
      
    if (nome.trim() == "" || cpf == "") {
	             window.alert("Insira um valor possivel!");
	}
 
 **Com a criação da variável jaValidou que so é acionada no caso do valor ser falso (false). Caso o contrario eles serão inseridos normalmente**  
  		
        else {

				var tabela =
				{
					"id": arrayTabela.length,
					"nome": nome,
					"cpf": cpf
				}

				arrayTabela.push(tabela);
			
				var jaValidou = false;
        
 **Esse código ele serve para validar se não há na tabela nenhum valor igual aos valores que serão inseridos caso tiver ele da uma mensagem de alerta mostrando que ja existe esse valor.**
  
  
    for (let i = 0; i < (arrayTabela.length - 1); i++) {
					var cpfTabela = tabela.cpf;
					var cpfArray = arrayTabela[i].cpf;
					var nomeTabela = tabela.nome;
					var nomeArray = arrayTabela[i].nome;

					if (cpfTabela == cpfArray) {
						jaValidou = true;
						window.alert("Ja existe um nome com esse CPF cadastrado!");
						arrayTabela.pop();
						break;
					}

					if (nomeTabela == nomeArray) {
						jaValidou = true;
						window.alert("Ja existe um nome como esse cadastrado!");
						arrayTabela.pop();
					}
          
 **Depois de ter inserido algum valor dos campos CPF ou Nome que ja consta existente na tabela ele não sera inserido e aparecerá uma mensagem de alerta e limpara  os valores did=gitados nesses campos. E dpois sera construida uma tabela depois de uma validação e finalizará com a função AdicionarLinha.**
 
       
  
    if (!jaValidou) {
					document.getElementById("txtNome").value = "";
					document.getElementById("txtCPF").value = "";
				}
    
    document.getElementById("tabelaClientes").innerHTML = constroiTabela();
          			}
		}
        
**Essa função é acionada quando a nesssecidade de remover alguma linha através do "ID" dentro do array ou da tabela e ao clicar no botão "remover" a linha sera removida dentro da tabela.**
  
    function RemoverLinha(idLinha) {
			arrayTabela.splice(idLinha, 1);
			document.getElementById("linhaRemover" + idLinha).remove();
			document.getElementById("tabelaClientes").innerHTML = constroiTabela();
		}
    
  			
**E no final temos a função constroiTabela() que é criada atraves do vetor arrayTabela e o for para pegar cada item no array e trazer para tabela.**
		
    function constroiTabela() {
			var tabelaScript =  "<tr>" +
									"<td>" +
										"<strong>" +
											"CPF" +
										"</strong>" +
									"</td>" +
									"<td>" +
										"<strong>" +
											"NOME" +
										"</strong>" +
									"</td>" +
									"<td>" +
										"<strong>" +
											"REMOVER" +
										"<strong>" +
									"</td>" +
								"</tr>";

			for (let i = 0; i < arrayTabela.length; i++) {
				tabelaScript += "<tr id='linhaRemover" + i + "'>" +
									"<td>" +
										arrayTabela[i].cpf +
									"</td>" +
									"<td>" +
										arrayTabela[i].nome +
									"</td>" +
									"<td>" +
										"<input type='button' id='buttonRemover" + i + "' value='Remover' onclick='RemoverLinha(" + i + ")' />" +
									"</td>"
								"</tr>";
			}

			return tabelaScript;
		}



			

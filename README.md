

   # Desafio javascript



## Introdução:

    

## Comentários dos códigos:

![img](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSLY_EV9R41Cit_VOkZF7Ssj3w8hhlPirwEpw&usqp=CAU)   

HTML:


**Esse código é o HMTL da página e nele mostra a criação duas caixas com nome e cpf para receber valores e tem tambem um botão de "adicionar".**


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
    
  **Esse array foi ele guarda os os dados seja o nome ou cpf que serão digitados nas caixas.**

  `var arrayTabela = [];`
  
  **A função AdicionarLinha() vai validar se os dados digitados nas caixas se estão de acordo com as regras e depois vai  adicionar na tabela.**

  `function AdicionarLinha() { `
  
  **A var cpf vai receber o cpf digitado e a var nome vai receber o nome.**

    var cpf = document.getElementById("txtCPF").value;
		var nome = document.getElementById("txtNome").value;
      
  **Esse if ele valida se algum dos valores digitados é vazio .**

  		if (nome.trim() == "" || cpf == "") {
				window.alert("Insira um valor possivel!");
			}
 
 **Caso os valores digitados nas caixas forem validos é criado um objeto com os dados recebidos e é criada a variável jaValidou para apagar os dados escritos se o valor for verdadeiro (true).**
  		
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
          
 ** Depois ter inserido um valor que ja existe na tabela e dar a mensagem de alerta muda os valores dos campos para o vazio.**
       
  
    if (jaValidou) {
					document.getElementById("txtNome").value = "";
					document.getElementById("txtCPF").value = "";
				}
          
 **Sera construida uma tabela depois da validção e finaliza a função AdicionarLinha .**

  	document.getElementById("tabelaClientes").innerHTML = constroiTabela();
          			}
		}
        
**Essa função é acionada quando a nesssecidade de remover alguma linha através do "ID" dentro do array ou da tabela e ao clicar no botão "remover".
  
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



			

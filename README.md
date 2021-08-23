# Popup-validation

Implementação bem simples da biblioteca.

Para maiores informações acesse a documentação no link: [popup-validation](https://github.com/AntonLapshin/popup-validation)

1. Crie um arquivo `html` e na mesma pasta execute o comando:  
```
    npm install popup-validation --save
```
2. Copie e cole o código abaixo no arquivo `html`:
```html
<!DOCTYPE html>
<html lang="pt-br">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Popup Validation</title>
  <!-- Adicionar estilo após executar o npm -->
  <link href="node_modules/popup-validation/bin/validation.min.css" rel="stylesheet">
  <style>
    header {
      text-align: center;
    }

    form {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    label,
    button {
      margin-top: 10px;
    }
  </style>
</head>

<body>
  <header>
    <h1>Popup-validation</h1>
  </header>
  <form>
    <!-- Adicionar  classe="validate" e data-validate="" com as regras-->
    <label for="name">Nome</label>
    <input class="validate" type="text" name="name" id="name" data-validate="required">

    <label for="email">E-mail</label>
    <input class="validate" type="text" name="email" id="email" data-validate="required,email">

    <label for="numero">Apenas números</label>
    <input class="validate" type="text" name="numero" id="numero" data-validate="required,integer">

    <button>Enviar</button>
  </form>

  <!-- Adicionar script após executar o (npm install popup-validation --save) -->
  <script src="node_modules/popup-validation/bin/validation.min.js"></script>

  <script>
    validation.init("form"); // iniciar a validação no form

    // Função para validar o último campo
    function validaInteiro(input) {
      const regEx = /^\d+$/; // Expressão regular para inteiros
      if (input.value === "" || regEx.test(input.value)) {
        return true;
      }
      return false;
    }

    // Aplicação da regra
    validation.rules["integer"] = {
      message: "Digite um número inteiro",
      method: validaInteiro
    }
  </script>
</body>

</html>
```
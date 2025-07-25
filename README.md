<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Ficha de Registro Simples</title>
<style>
  body { font-family: Arial, sans-serif; background: #f8f9fa; padding: 20px; }
  form { background: #fff; padding: 20px; border-radius: 8px; max-width: 600px; margin: auto; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
  label { display: block; margin-top: 10px; font-weight: bold; }
  input { width: 100%; padding: 8px; margin-top: 5px; box-sizing: border-box; border-radius: 4px; border: 1px solid #ccc; }
  button { background: #007bff; color: white; padding: 12px; border: none; cursor: pointer; width: 100%; font-size: 16px; border-radius: 6px; margin-top: 10px; }
  button:hover { background: #0056b3; }
</style>
</head>
<body>
<h1>Ficha de Registro Simples</h1>
<form id="registroForm">
  <label>Nome do Trabalhador:</label>
  <input type="text" name="Nome do Trabalhador" required />
  <label>Nome do Pai:</label>
  <input type="text" name="Nome do Pai" />
  <label>Nome da Mãe:</label>
  <input type="text" name="Nome da Mãe" />
  <label>CPF:</label>
  <input type="text" name="CPF" required />
  <label>PIS:</label>
  <input type="text" name="PIS" />
  <label>Filiação:</label>
  <input type="text" name="Filiação" />
  <label>Cidade de nascimento:</label>
  <input type="text" name="Cidade de nascimento" />
  <label>Data de nascimento:</label>
  <input type="date" name="Data de nascimento" />
  <label>Estado Civil:</label>
  <input type="text" name="Estado Civil" />
  <label>Endereço:</label>
  <input type="text" name="Endereço" />
  <label>Bairro:</label>
  <input type="text" name="Bairro" />
  <label>Cidade/UF:</label>
  <input type="text" name="Cidade/UF" />
  <label>CEP:</label>
  <input type="text" name="CEP" />
  <label>Telefone:</label>
  <input type="text" name="Telefone" />
  <label>Escolaridade:</label>
  <input type="text" name="Escolaridade" />
  <button type="submit">Salvar Registro</button>
</form>
<script>
const scriptURL = '[SUA_URL_DO_APPS_SCRIPT](https://docs.google.com/spreadsheets/d/1npVdNpCK9C5BarjWZssZSTko9ysiNQr-ny99_m8fSLQ/edit?gid=1534807958#gid=1534807958)';
const form = document.getElementById('registroForm');
form.addEventListener('submit', e => {
  e.preventDefault();
  const formData = new FormData(form);
  const jsonData = {};
  formData.forEach((value, key) => { jsonData[key] = value; });
  fetch(scriptURL, { method: 'POST', body: JSON.stringify(jsonData), headers: { 'Content-Type': 'application/json' } })
    .then(response => response.text())
    .then(result => { alert(result); form.reset(); })
    .catch(error => alert('Erro: ' + error));
});
</script>
</body>
</html>

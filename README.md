# Conversor De Moeda
Este é um projeto de conversor de moedas desenvolvido com HTML, CSS e JavaScript. Ele permite a conversão de valores entre Reais (BRL), Dólares (USD) e Euros (EUR), utilizando taxas de câmbio fixas definidas no código JavaScript.

## Estrutura do Projeto

### 1. HTML (Estrutura e Conteúdo)

O arquivo `index.html` define a estrutura da interface, exibindo campos de entrada, seleção de moedas e botões de ação.
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <title>Conversor De Moedas</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="stylesheet" type="text/css" href="main.css" />
</head>
<body>
    <!-- Seção da Imagem -->
    <div id="imagemV">
        <img src="undraw_bitcoin_re_urgq.svg" alt="Imagem ilustrativa de moeda digital">
    </div>

    <!-- Seção do Formulário -->
    <div id="form">
        <h1 style="text-align: center;">Conversor De Moedas</h1>
        <div id="input-box">
            <form onsubmit="converter(); return false;">
                <div id="texts">
                    <label for="valor">Valor</label>
                    <input required type="number" id="valor" />
                </div>
                <div id="texts">
                    <label for="Damoeda">De</label>
                    <select id="Damoeda">
                        <option value="BRL">Reais (BRL)</option>
                        <option value="USD">Dólar (USD)</option>
                        <option value="EUR">Euros (EUR)</option>
                    </select>
                </div>
                <div id="texts">
                    <label for="Paramoeda">Para</label>
                    <select id="Paramoeda">
                        <option value="BRL">Reais (BRL)</option>
                        <option value="USD">Dólar (USD)</option>
                        <option value="EUR">Euros (EUR)</option>
                    </select>
                </div>
                <h2 id="Resultado"></h2>
                <div id="button-continue">
                    <button type="submit">Converter</button>
                </div>
                <div id="limpar">
                    <button type="button" onclick="document.getElementById('valor').value=''">Limpar</button>
                </div>
            </form>
        </div>
    </div>

    <script src="main.js"></script>
</body>
</html>
````
### Descrição do HTML
Imagem: 
O elemento `<div id="imagemV">` exibe uma imagem ilustrativa de moeda digital.

Formulário: O formulário recebe o valor a ser convertido, a moeda de origem e a moeda de destino.

Botões: O botão "Converter" aciona a função `converter()` e o botão "Limpar" redefine o campo de valor.

Resultado: O elemento  `<h2 id="Resultado">` exibe o valor convertido.

## JavaScript (Lógica de Conversão)
````javascript 
document.getElementById('form').addEventListener('submit', function(event) {
    event.preventDefault();

    // Obter valores de entrada do usuário
    const valor = parseFloat(document.getElementById('valor').value);
    const daMoeda = document.getElementById('Damoeda').value;
    const paraMoeda = document.getElementById('Paramoeda').value;

    // Taxas de câmbio fixas
    const exchangeRates = {
        USD: { BRL: 5.70, EUR: 0.93, USD: 1 },
        BRL: { USD: 0.18, EUR: 0.16, BRL: 1 },
        EUR: { USD: 1.08, BRL: 6.16, EUR: 1 },
    };

    // Verificar se a conversão é necessária
    if (daMoeda === paraMoeda) {
        document.getElementById('Resultado').innerText = `O valor é o mesmo: ${valor.toFixed(2)} ${paraMoeda}`;
        return;
    }

    // Calcular valor convertido
    const taxaConversao = exchangeRates[daMoeda][paraMoeda];
    const valorConvertido = valor * taxaConversao;

    // Exibir o resultado
    document.getElementById('Resultado').innerText = `Resultado: ${valorConvertido.toFixed(2)} ${paraMoeda}`;
});
````
### Descrição do JavaScript
Captura de Evento: O evento `submit` chama a função de conversão ao enviar o formulário.

Obtenção de Dados: Extrai o valor a ser convertido, a moeda de origem e a moeda de destino.

Taxas de Câmbio Fixas: Define taxas de conversão fixas entre as moedas disponíveis.

Verificação de Conversão: Se a moeda de origem e a moeda de destino forem as mesmas, exibe uma mensagem indicando que o valor não muda.

Cálculo da Conversão: Multiplica o valor pela taxa de conversão para obter o valor convertido.

Exibição do Resultado: Mostra o valor convertido no elemento `<h2 id="Resultado">.`

## CSS (Estilização)
O arquivo main.css contém a estilização do layout, organização e alinhamento dos elementos do formulário.

![](captura.jpeg)

## Instruções para Executar o Projeto
1. Salve todos os arquivos (index.html, main.js, main.css) no mesmo diretório.
2. Abra o arquivo index.html em um navegador para visualizar o Conversor de Moedas.
3. Insira o valor, selecione as moedas de origem e destino, e clique em "Converter" para ver o resultado.

![](Gravando%202024-11-01%20080222.gif)

## Recursos Futuros
Possíveis melhorias incluem:

* Obter taxas de câmbio em tempo real via API de câmbio.
* Adicionar suporte a mais moedas para conversão.



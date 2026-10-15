
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teste de Protótipo</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f4f8;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 600px;
            margin: auto;
            background: white;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 4px 10px #cccccc;
        }

        h1 {
            color: #2563eb;
            text-align: center;
        }

        p {
            color: #444;
        }

        .pergunta {
            margin: 20px 0;
        }

        textarea {
            width: 100%;
            height: 60px;
            padding: 8px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 6px;
        }

        button {
            width: 100%;
            background-color: #2563eb;
            color: white;
            padding: 12px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 16px;
        }

        button:hover {
            background-color: #1d4ed8;
        }
    </style>
</head>

<body>
    <div class="container">
        <h1>Teste do Protótipo</h1>

        <p>
            Responda às perguntas abaixo para ajudar
            a melhorar nosso aplicativo.
        </p>

        <form id="formulario">
            <div class="pergunta">
                <label>1. Você entendeu para que serve o aplicativo?</label>
                <textarea required></textarea>
            </div>

            <div class="pergunta">
                <label>2. O aplicativo resolve um problema? Qual?</label>
                <textarea required></textarea>
            </div>

            <div class="pergunta">
                <label>3. A tela está organizada e fácil de entender?</label>
                <textarea required></textarea>
            </div>

            <div class="pergunta">
                <label>4. Você saberia utilizar o aplicativo sozinho?</label>
                <textarea required></textarea>
            </div>

            <div class="pergunta">
                <label>5. O que você mudaria para melhorar o aplicativo?</label>
                <textarea required></textarea>
            </div>

            <button type="submit">Enviar respostas</button>
        </form>

        <p id="mensagem"></p>
    </div>

    <script>
        document.getElementById("formulario")
            .addEventListener("submit", function(event) {
                event.preventDefault();

                const respostas = [...this.querySelectorAll("textarea")]
                    .map((campo, indice) =>
                        `${indice + 1}. ${campo.value}`
                    );

                const arquivo = new Blob(
                    [respostas.join("\n\n")],
                    { type: "text/plain;charset=utf-8" }
                );

                const link = document.createElement("a");
                link.href = URL.createObjectURL(arquivo);
                link.download = "respostas_do_teste.txt";
                link.click();

                URL.revokeObjectURL(link.href);

                document.getElementById("mensagem").textContent =
                    "Respostas salvas em um arquivo de texto!";
            });
    </script>
</body>
</html>

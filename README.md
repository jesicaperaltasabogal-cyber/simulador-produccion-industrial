<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Simulador de Producción - Ingeniería Industrial</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f6f9;
            margin: 0;
            padding: 0;
        }

        header {
            background: #003366;
            color: white;
            padding: 20px;
            text-align: center;
        }

        main {
            max-width: 600px;
            margin: 30px auto;
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }

        h2 {
            text-align: center;
            color: #003366;
        }

        label {
            display: block;
            margin-top: 15px;
            font-weight: bold;
        }

        input {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        button {
            width: 100%;
            margin-top: 20px;
            padding: 12px;
            background: #007bff;
            color: white;
            border: none;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background: #0056b3;
        }

        .resultado {
            margin-top: 25px;
            padding: 15px;
            background: #e9f5ff;
            border-left: 5px solid #007bff;
        }

        footer {
            text-align: center;
            margin-top: 30px;
            color: gray;
            font-size: 14px;
        }
    </style>
</head>
<body>

<header>
    <h1>Simulador de Procesos Industriales</h1>
    <p>Ingeniería Industrial</p>
</header>

<main>
    <h2>Datos del Proceso</h2>

    <label>Producción diaria (unidades):</label>
    <input type="number" id="produccion">

    <label>Demanda diaria (unidades):</label>
    <input type="number" id="demanda">

    <label>Inventario inicial (unidades):</label>
    <input type="number" id="inventario">

    <button onclick="simular()">Simular Proceso</button>

    <div class="resultado" id="resultado"></div>
</main>

<footer>
    Aplicación académica – Ingeniería Industrial
</footer>

<script>
    function simular() {
        let produccion = parseInt(document.getElementById("produccion").value);
        let demanda = parseInt(document.getElementById("demanda").value);
        let inventarioInicial = parseInt(document.getElementById("inventario").value);

        if (isNaN(produccion) || isNaN(demanda) || isNaN(inventarioInicial)) {
            alert("Por favor ingrese todos los valores.");
            return;
        }

        let inventarioFinal = inventarioInicial + produccion - demanda;
        let mensaje = "";

        if (inventarioFinal > 0) {
            mensaje = "Exceso de inventario. Se recomienda reducir producción.";
        } else if (inventarioFinal < 0) {
            mensaje = "Déficit de inventario. Se recomienda aumentar producción.";
        } else {
            mensaje = "Producción óptima. Inventario equilibrado.";
        }

        document.getElementById("resultado").innerHTML = `
            <strong>Inventario Final:</strong> ${inventarioFinal} unidades <br><br>
            <strong>Análisis:</strong> ${mensaje}
        `;
    }
</script>

</body>
</html>

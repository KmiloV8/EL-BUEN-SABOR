<template>
<head>
    <title>Haz Tu Pedido</title>
</head>
<body>
    <h1>¡Que Deseas Ordenar!</h1>
    <div id="whatToPrint">
    <form>
        <fieldset>

            <legend>Pedido</legend>
            <p>
                <label>Nombre del Producto</label>
                <input type="text" name="nombre-producto" size="30px" placeholder="Ingrese el nombre del producto">
            </p>
            <p>
                <label>Medio de Pago</label>
                <select name="Medio de pago">
                    <option value="0"></option>
                    <option value="">Consignación(Nequi)</option>
                    <option value="">Efectivo</option>
                </select>
            </p>
            
            <h6>si desea agregar un adicional ingrese que desea (si no quiere un adicional puede omitir este espacio) 
            </h6>
            <p>
                <label>Adicional</label>
                <input type="text" name="nombre-producto" size="30px" placeholder="Ingrese el adicional">
            </p>
            <hr>
            <legend>Datos Personales</legend>
            <p>
                <label>Nombres y Apellidos</label>
                <input type="text" name="nombre" size="30px" placeholder="Nombre(s) y apellidos">
            </p>
            
            <p>
                <label>N° de Telefono</label>
                <input type="text" name="n°-documento" size="30px" placeholder="Número de telefono">
            </p>
            <p>
                <label>Fecha Del Pedido</label>
                <input type="DATE" name="fecha-n">
            </p>
            <p>
                <label>Dirección</label>
                <input type="text" name="direccion" size="30px" placeholder="Dirección de residencia">
            </p>
            <a @click="generatePDF()" id="downloadButton">Descargar Pedido</a>
        </fieldset>        
    </form>    
</div>
</body>
</template>

<script>
import jsPDF from 'jspdf'
import html2canvas from 'jspdf-html2canvas'
export default{
data(){
return {

}},
    methods:{
generatePDF(){
    document.getElementById("downloadButton").innetHTML ="Descargando tu pedido";
    //descargando

    var downloading = document.getElementById("whatToPrint");
    var doc = new jsPDF('1','pt');
    
    html2canvas(downloading,{
        //allowTaint: true,
        //useCORS: true,
        width: 550
    }).then((canvas) => {
        doc.addImage(canvas.toDataURL("image/png"), 'PNG', 5, 5, 500, 500);
    });
    //fin de la descarga
   
   
}
}}
</script>

<style scoped>
form{
    width: 800px;
    height: auto;
    margin:auto;
    background-color: rgba(227, 167, 55, 0.823);
    border-radius: 30px;
    border-style: solid;
    border-width: 2px;
}
h1{
    font-family: arial black;
    text-align: center;
    cursor:default;
    color:rgb(22, 15, 9);
}
h2{
    font-family:Arial, Helvetica, sans-serif;
    font-size:36px;
    color: black;
    text-align: center;
}
h6{
    color:rgb(102, 102, 102);
    text-align: center;
    margin-left: 100px;
    margin-right: 100px;
}
legend{
    text-align: center;
    font-family: Arial, Helvetica, sans-serif;
}
p{
    text-align: center;
}
input{
    border-radius: 10px;
    border-style: none;
    font-family: "Poppins", sans-serif;
    margin:10px;
    padding: 10px;
}
#whatToPrint{
    padding: 10px;
}
a{
    background-color: #f4b41a;
    border-color: #f4b41a;
    color:white;
    padding:15px;
    text-decoration: none;
    margin: auto;
    border-radius: 15px;
    border-style:solid;
    border-color: rgb(24, 13, 2);  
    border-width: 1.8px;   
    cursor:pointer;          
}
a:hover{
    color: #FFF;
  background-color: #1EAEDB;
  border-color: #1EAEDB;
}
</style>
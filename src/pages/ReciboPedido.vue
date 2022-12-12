<template>
<head>
    <title>Haz Tu Pedido</title>
</head>
<body>
    <h1>¡Realiza Tu Pedido Con Nosotros!</h1>
    <h2>Formulario Para Diligenciar Tu Pedido</h2>
    <h6><br/>Recuerda que para diligenciar tu pedido debes conocer los soguientes datos del producto
        <br/>que deseas adquirir: Nombre del producto,Código del producto(el cual se muestra debajo de la imagen 
        <br/>de cada producto), Tipo de madera, Medio de pago, TIpo de tela, Color y tipo de pintura.
    </h6>
    <div id="whatToPrint">
    <form>
        <fieldset>

            <legend>Datos del Producto</legend>
            <p>
                <label>Codigo del Producto</label>
                <input type="text" name="codigo" size="30px" placeholder="Ingrese el código del producto">
            </p>
            <p>
                <label>Nombre del Producto</label>
                <input type="text" name="nombre-producto" size="30px" placeholder="Ingrese el nombre del producto">
            </p>
            <h6>Si el tipo de madera que buscas no se encuentra dentro de las opciones, por favor escoge la opción(Otro..cual) 
                y digítalo en la barra de texto que está al lado.
            </h6>
            <p>
                <label>Tipo de Madera</label>
                <select name="Tipo de madera">
                    <option value="0"></option>
                    <option value="">opción 1</option>
                    <option value="">opción 2</option>
                    <option value="">opción 3</option>
                    <option value="">opción 4</option>
                    <option value="">Otro...cual
                        <input type="text" name="otra madera" size="20px">
                    </option>
                </select>
            </p>
            <h6>Para realizar el pago de tu pedido, debes ponerte en contacto con el administrador vía whatsapp o por 
                llamada telefónica, a continuación te dejamos su contacto(SE PIDE AMABLEMENTE QUE SOLO SE CONTACTE CON
                EL VENDEDOR EN CASO DE SOLICITAR INFORMACIÓN ACERCA DE UN PRODUCTO O UN PEDIDO): 3174816178
            </h6>
            <p>
                <label>Medio de Pago</label>
                <select name="Medio de pago">
                    <option value="0"></option>
                    <option value="">Transferencia</option>
                    <option value="">Consignación(Nequi)</option>
                    <option value="">Efectivo</option>
                </select>
            </p>
            <p>
                <label>Tipo de Tela</label>
                <select name="Tipo de tela">
                    <option value="0"></option>
                    <option value="">Opción 1</option>
                    <option value="">Opción 2</option>
                    <option value="">Opción 3</option>
                    <option value="">Otro...cual
                        <input type="text" name="otra tela" size="20px">
                    </option>
                </select>
            </p>
            <legend>Datos Personales</legend>
            <p>
                <label>Nombres y Apellidos</label>
                <input type="text" name="nombre" size="30px" placeholder="Nombre(s) y apellidos">
            </p>
            <p>
                <label>Tipo de Documento</label>
                <select name="documento de identidad">
                    <option value="">Cédula de ciudadanía</option>
                    <option value="">Tarjeta de identidad</option>
                    <option value="">Cédula de extranjería</option>
                </select>
            </p>
            <p>
                <label>N° de Documento</label>
                <input type="text" name="n°-documento" size="30px" placeholder="Número de documento">
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
    background-color: rgba(247, 180, 45, 0.269);
    border-radius: 30px;
    border-style: solid;
    border-width: 2px;
}
h1{
    font-family: arial black;
    text-align: center;
    cursor:default;
    color:rgb(150, 128, 110);
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
    background-color: rgb(135, 101, 70);
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
    background-color: rgb(111, 76, 43);
}
</style>
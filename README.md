//DECLARAR CONSTANTES
const productos = [
    {nombre: "Leche", precio: 50},
     {nombre: "Pan", precio: 100},
     {nombre:"Carne", precio:150}
    ]
let carrito = []

 
let comprar = prompt ("Desea comprar algo?Ingrese SI/NO")
// PRIMER BUCLE WHILE 
while (comprar !="SI" && comprar !="NO"){
   alert ("Ingrese SI/NO")
   comprar = prompt ("Desea comprar algo?Ingrese SI/NO")    
   
}
   //CONDICION CON FUNCION DE MOSTRAR TODOS LOS PRODUCTOS DISPONIBLES
   if (comprar =="SI"){
       alert ("Productos disponibles: ")
       let mostrarProductos = productos.map((productos) => `${productos.nombre} ${productos.precio} $`);
       alert (mostrarProductos.join(" - ")) 
}      else if (comprar =="NO"){
   alert ("Gracias, vuelva prontos")
}


//BUCLE AGREGAR PRODUCTOS AL CARRITO, DEFINIR PRECIOS
while (comprar !="NO"){
        let productos = prompt ("Agrega Leche, Pan, o Carne a tu carrito!")
        let precio = 0
        if (productos=="Leche"|| productos=="Pan" || productos=="Carne"){
           switch (productos) {
            
            case "Leche":
            precio = 50            
            break;
            
            case "Pan":
            precio = 100
            break
            
            case "Carne":
            precio = 150
            break;
            
            default:
                break;
           } 
           let unidades = Number (prompt ("Cuantas unidades desea?"))

           carrito.push ({productos, unidades, precio})
           
        } else {
            alert ("No tenemos ese producto")
        }
//BUCLE PARA AGREGAR MÁS PRODUCTOS AL CARRITO  
        comprar = prompt ("Desea seguir con su compra?SI/NO")
        while (comprar !="SI"){
                alert ("¡Gracias por su compra!")
                carrito.forEach((carritoFinal)=>{
                    console.log (`producto: ${carritoFinal.productos}, unidades:${carritoFinal.unidades}, total a pagar ${carritoFinal.precio * carritoFinal.unidades}$`)
                })
                break;  
        }
}
// SUMA TOTAL DEL CARRITO USANDO METODO REDUCE 
const total = carrito.reduce ((acc, el) => acc + el.precio * el.unidades, 0)
alert (`El total a pagar por su compra es : ${ total } $`)

alert ("Su compra ha sido exitosa")

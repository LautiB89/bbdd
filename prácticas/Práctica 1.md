

### Ejercicio 1.1
#TODO Hacer el DER
#### MR
Póliza(idPoliza, idCliente)
- PK = {idPoliza}
- CK = {idPoliza}
- FK = {idCliente}
Cliente(idCliente, nombre)
- PK = {idCliente}
- CK = {idCliente}
- FK = {}
Auto(patente, idPoliza)
- PK = {patente}
- CK = {patente}
- FK = {idPoliza}
Pago(fechaVto, fechaPago, idPoliza)
- PK = {{fechaVto, idPoliza}}
- CK = {{fechaVto, idPoliza}}
- FK = {idPoliza}
Accidente(fecha, patente)
- PK = {{fecha, patente}}
- CK = {{fecha, patente}}
- FK = {patente}

### Ejercicio 1.2
- Suponemos que cada auto tiene un único cliente asociado
- Cada poliza puede cubrir multiples autos y está asociada al cliente dueño

```mermaid
erDiagram
	CLIENTE {
		string DNI PK ""  
		string NOMBRE  ""  
		string APELIDO  ""  
		string DIRECCION  ""  
		string Fecha_de_nacimiento  ""  
	}

	PRODUCTO {
		string CODIGO PK ""  
		string NOMBRE  ""  
		int PRECIO  ""  
	}

	PROVEEDOR {
		string CUIT PK ""  
		string NOMBRE  ""  
		string DIRECCION  ""  
	}

	CLIENTE}|--o{PRODUCTO:"compra"
	PROVEEDOR||--|{PRODUCTO:"provee"

```

### Ejercicio 1.3
```mermaid
erDiagram
	CAMIONERO {
		string DNI  
		string NOMBRE  
		string APELLIDO  
		int TELEFONO  
		string DIRECCION  
		int SALARIO  
		string POBLACION  
	}

	PAQUETE {
		string CODIGO  
		string DESCRIPCION  
		string DESTINATARIO  
	}

	CAMION {
		string MATRICULA  
		string MODELO  
		string TIPO  
		string POTENCIA  
	}

	PROVINCIA {
		string CODIGO  
		string NOMBRE  
	}

	CAMIONERO}|--|{CAMION:"maneja"
	CAMIONERO||--|{PAQUETE:"entrega"
	PAQUETE}|--o|PROVINCIA:"destinado"
```
### Ejercicio 1.4


---
title: Definición de APIs
weight: 2
---

## Objetivos

Este documento define las interfaces entre los diferentes sub-sistemas del TP Final.


## Ministerio de Desarrollo Productivo 📋
* **Esquemas de Datos**
	- Reportes
	
		```typescript
			const reporteSchema = new Schema<IReport>({
  				infoEmpresa: {
    				type: Schema.Types.ObjectId,
   					 ref: "Business",
 				 },
  				listaRegistro: {
   					 type: [
      					{
        					type: Schema.Types.ObjectId,
        					ref: "Products",
     					 },
   					 ],
  				},
  				date_upload : {
      				type : Date,
      				default : Date.now()
  				},
  				day_limit : {
      				type : Number,
      				default : 10
  				},
  				periodo: {
   					 year: {
      					type: String,
      					require: true,
      					trim: true,
    			},
    					month: {
						  type: String,
      					require: true,
      					trim: true,
    			},
  			},
			});
		```
	- Empresas 
	
	```typescript
		const businessSchema = new Schema<IBusiness>({
  			cuit: {
   				 type: Number,
    				require: true,
    				trim: true,
  			},
  			razon_social: {
    			type: String,
    			require: true,
    			trim: true,
  			},
 			 report: {
   				 type: [
      				{
        				type: Schema.Types.ObjectId,
        				ref: "Report",
     				 },
    			],
  			},
		});
	```
	- Productos 
	
	```typescript
	  	const productsSchema = new Schema<IProduct>({
    		denominacion: {
      			type: String,
      			require: true,
      			trim: true,
   		 },
    		codigo_ean: {
      			type: Number,
      			require: true,
      			trim: true,
    		},
    		precio_unidad: {
      			type: Number,
      			require: true,
      			trim: true,
    		},
    		unidad_medida: {
      			type: String,
      			require: true,
      			trim: true,
    		},
    		cantidad_prod: {
      			type: Number,
      			require: true,
      			trim: true,
    		},
    		cantidad_vend: {
        			type: Number,
        			require: true,
        			trim: true,
      		},
      		report: {
        			type: Schema.Types.ObjectId,
        			ref: "Report",
      		}
  		});
	```
	- Usuarios Empresas 
	
	```typescript
		const userBusinessSchema = new Schema<IUserBusiness> ({
    			cuit : {
        				type : Number,
        				unique : true,
        				trim: true,
        				require: true,
        				min : [11, 'El CUIT debe tener 11 digitos']
    			},
    			razon_social : {
        				type : String,
        				require : true,
        				trim: true,
    			},
    			industria : {
        				type: String,
        				require: true,
        				trim: true,
    			},
    			email : {
        				type : String,
        				unique : true,
        				require : true,
        				trim: true,
    			},
    			tel : {
        				type : Number,
        				unique :true,
        				require : true,
        				trim : true,
    			},
    			ciudad : {
        				type : String,
        				require : true,
        				trim : true,
    			},
    			password : {
        				type : String,
        				require : true,
        				trim : true,
        				minLength : [6, '¡La constraseña debe tener al menos 6 caracteres!']
    			}
			})
	```
	
- **Rutas**
	_En esta primera entrega solo trabajaremos de forma local, debido a esto se especifican las siguientes rutas_
	- Rutas para manipular reportes, todas estas rutas deben llevar en el Header de la petición el token de validación.
	
		- Obtengo todos los reportes asociados a la empresa autenticada.
				GET localhost:3000/api/reports
		- Cargo un reporte asociado a la empresa autenticada.
				POST localhost:3000/api/reports
		- Actualizo un reporte asociado a la empresa autenticada, se considera solo que se envian nuevos productos. Se pasa por parametro el id del reporte.
				PUT localhost:3000/api/reports/:_id
		- Elimino un reporte asociado a la empresa autenticada. Se pasa por parametro el id del reporte.
				DELETE localhost:3000/api/reports/:_id
	- Rutas para manipular la autenticación de empresas, estas rutas devuelven en el Header el token de autenticación necesario para acceder a las rutas arriba mencionadas. 
	
		- Registro una empresa
				POST localhost:3000/api/signup
		- Autentica una empresa
				POST localhost:3000/api/login
				
- **Ejemplo**

	- De la petición POST a `localhost:3000/api/signup`
	
		```json
{
    		"cuit" : 20391791199,
    		"razon_social" : "SANCOR SA",
    		"industria" : "Lacteos",
    		"email" : "sancor@gmail.com", 
    		"tel" : 3624771222,
    		"ciudad" : "Resistencia",
    		"password" : "sancorelmejor"
		}
```
	- De la petición POST a `localhost:3000/api/login`
	
	```json
{
    		"email" : "sancor@gmail.com",
    		"password" : "sancorelmejor"
}
```
	- De la petición POST a `localhost:3000/api/reports`
	
	```json
		{
  			"infoEmpresa": {
    				"cuit": 20391791199,
    				"razon_social" : "SANCOR SA"
  					},
  			"listaRegistro": [
    				{
      				"denominacion" : "Yogurt",
      				"codigo_ean": 9523113131251,
      				"precio_unidad": 1,
      				"unidad_medida": "Lt",
      				"cantidad_prod": 2,
      				"cantidad_vend": 1
   				 }, 
    				{
      				"denominacion" : "Yogurt",
      				"codigo_ean": 9217131934313,
      				"precio_unidad": 1,
      				"unidad_medida": "Lt",
      				"cantidad_prod": 2,
      				"cantidad_vend": 1
    			}
  			],
  			"periodo": {
    				"year": "2021",
    				"month": "12"
  			}
		}
```
- **Algunas validaciones importantes que deben tener los datos enviados.**
	- CUIT de 11 digitos.
	- PASSWORD de 6 digitos como minimo.
	- CODIGO EAN de 13 digitos.
	- EMAIL debe tener el formato correcto. example@gmail.com

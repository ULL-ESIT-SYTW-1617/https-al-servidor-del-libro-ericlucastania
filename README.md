#Práctica: GitHub API

## Descripción

El objetivo de esta práctica es poder conectarse al libro mediante el uso del protocolo https. Para 
ello se ha cambiado la funcionalidad del plugin del iaas de manera que, cuando se despliegue en dicho servidor,
se debería acceder a la url con el siguiente formato:

[https://10.6.128.159:8080](https://10.6.128.159:8080)

pero poniendo la ip de tu servidor.



## Pasos a ejecutar 

**1. Instala nuestro paquete de forma global**

```npm install -g gitbook-start-elt```


**2. Ejecuta el binario para el render del template**
	
Tienes la opción de crear el repositorio o la opción de no crearlo:
	
	
**Crear repositorio**
* Si quieres que te cree un repositorio en Github tienes que poner la opción --repo
	
   ```gitbook-start --dir Carpeta --repo```

Cuando ejecutes el paso anterior si no es la primera vez que lo haces te pedirá el usuario y 
		contraseña de github.Si introduces los datos correctamente te pedirá que introduzcas el nombre que quieres ponerle al repo,
		Ahora se desplegará el libro en github:
				
**Ejemplo de uso:**
				
				
![](https://4.bp.blogspot.com/-tZyZ4yGuI9A/WCxV2cB2ktI/AAAAAAAAAAg/I2tzZnB7FL4Nld6OQRs2NYG-SRwa9kIuwCLcB/s1600/repo.PNG)
				
Una vez que se te creado el repo ya puedes trabajar en él,ya no tendrás que poner más el 
			usuario y contraseña gracias a que se te generó un token para evitar que cada vez que quieras 
				crear un repo te pida tus credenciales.
				El token que se genera se guarda en el ./gitbook-start/config.json un lugar seguro para que no pueda acceder nadie
				que no seas tu.	
				
La siguiente función es la que se utiliza para guardar el token que se obtiene
```javascript
    auth().then(function (resolve, reject) {
					fs.mkdirSync(directorioHome + '/.gitbook-start');
					var pac = directorioHome + '/.gitbook-start/';
					fs.writeFile(pac + 'config.json', JSON.stringify(json), function (err) {
						if (err) throw err;
						else resolviendo(console.log("guardando el json correctamente.."));

					});
				});
```


**3. Entra en la carpeta**

 ```cd Carpeta```


## PLUGINS

**1. Instala el plugin forma global**

```npm install -g PLUGIN```

**2. Ejecuta el plugin que desees, asegúrate de estar dentro de la carpeta**


```gitbook-start -d PLUGIN``` !! También puedes usar la opción --deploy


**3. Ejecuta el gulp creado**

```gulp deploy-plugin```



## Correción 

En el archivo /bin/octonode.js utilizamos la función ghme.info para obtener el email y nombre del usuario
y guardarlo en el pck.json

```javascript

    ghme.info((err, data, headers) => {
    	pck.email = data.email;
    	pck.author = data.name;
    }
    
```

### Ejemplo del package.json con el nombre del usuario e email 
 A continuación se muestra de como quedaría el package.json del usuario una vez obtenido los datos de email 
y el nombre del usuario de la función ghme.info() sería el siguiente:

  ``` 
     "email": "alu0100785265@ull.edu.es",
     "author": "José Lucas"
     
  ```

## Explicación

Cunado se ejecuta el gitbook-start -d PLUGIN se te lanzará el initialize del módulo,
el initialize crea una tarea en el gulp para realizar el deploy. Además de guardarte el paquete
elegido en el package.json.

## Opciones

    gitbook-start [OPTIONS]
        --dir nombre_del_directorio a crear gitbook-start --dir miDirectorio
        -a autor del libro a crear node gitbook-star -a AutorDelLibro
        -e email del autor del libro node gitbook-star -e eric.ramos.suarez@gmail.com
        -r repositorio github contra el que se va a trabajar -r nameRepo
        -v muestra la version del paquete gitbook-start -v
        -h muestra ayuda sobre las opciones disponibles
        --repo opción que te permite crear un repositorio en GitHub


## Enlaces interesantes 
 
* [NPM](https://www.npmjs.com/package/gitbook-start-elt)
* [Repositorio de la práctica](https://github.com/ULL-ESIT-SYTW-1617/https-al-servidor-del-libro-ericlucastania)
* [Descripción de la tarea campus](https://crguezl.github.io/ull-esit-1617/practicas/practicassl.html)
* [PLUGIN IAAS](https://github.com/ULL-ESIT-SYTW-1617/gitbook-start-iaas-ull-es-ericlucastania)
* [NPM PLUGIN IAAS](https://www.npmjs.com/package/gitbook-start-plugin-iass-ull-es-ericlucastania)



## Componentes del grupo de trabajo

* [Eric Ramos](https://github.com/alu0100786330)
* [Lucas Ruiz](https://github.com/alu0100785265)
* [Tania González](https://github.com/tania77)



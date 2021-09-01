# Curso de Github Actions de Udemy
###### Fuente: https://www.udemy.com/course/github-actions/
## ¿Que es GitHub Actions?
Github action es una herramienta que permite automatizar el flujo de trabajo (***workflow***) para el desarrollo de un producto software. Escribiendo tareas individuales, llamadas ***actions***, y combinarlas para crear un ***workflow*** personalizado.
### ¿Que son los Workflows?
Los ***workflow*** son procesos automaticos personalizados que se pueden configurar en un repositorio de GitHub para construir, probar, empaquetar, publicar o desplegar dicho proyecto.

El ***workflow*** inicia a ejecutarse cuando ocurre un evento previamente definido en el workflow. Acontinuación estan los eventos que su ejecución:
* Push
* Pull Request (open, merged)
* Issue (create, close,...)
* Eventos programados
* Eventos externos

Cuando alguno de estos eventos ocurre, se inicia una maquina (***Runner***) por cada ***job*** que se tenga configurado en el workflow. Cada job, se tiene varios ***steps***, donde cada ***step***  realiza una tarea ***task***. Los jobs se pueden correr de manera paralela o dependientes uno de otro. 
### Runner
Un Runner es una maquina con la aplicación de GitHub Actions runner instalada. Este runner es responsable de ejecutar los jobs cada vez que un evento ocurre y tambien de motrar los resultados. Estos runner pueden ser alojados por GitHub (GitHub-hosted Runner) o sel alojados en nuestras propias maquina ()
#### GitHub-hosted Runner
Los GitHub-hosted Runner son maquinas virtuales proveidas por GitHub y pueden tener SO (Linux, Windows y MacOS) on unos recursos especificos, mas detalle mirar (aqui)[https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners] 

Github tiene pre-instaladas diferentes herramientas deacuerdo a los requerimientos como pueden ser Android SDK o XCode o lenguajes como python o java y herramientas genericas como curl o git.

#### Selft-hosted Runner
Los Selft-hosted Runner son maquinas que admnnistramos nostros mismos. Esto nos da mas control de los requerimientos de hardware para jobs mas grandes.
## Breve introducción a formato YAML
Los workflow estan escritos en formato **YAML**. YAML format es una forma de serialización de datos similar a JSON. Para tene mas claro como se esctrctura estos archivos vamos a compararlos con un archivo **JSON** para ellos vamos a usar el plugin de visual estudio [*YAML to JSON*](https://marketplace.visualstudio.com/items?itemName=ahebrank.yaml2json). 
### Definición de un objeto
Para definir un para llave/valor se ingresa el `key` `:` un espacio sencillo y el `value`. Si se requieren varios pares llave valor estos deben mantener la misma identación dentro.
###### Ejemplo en YAML
        key: value
        number: 2.1
        scapedValue: "adasfsaf:Fdsfa"
        boolean: true
###### Ejemplo en JSON
        {
            "key": "value",
            "number": 2.1,
            "scapedValue": "adasfsaf:Fdsfa",
            "boolean": true
        }
### Objeto dentro de otro objeto
Para asignar un objeto como valor se debe seguir asinar el `key`, `:` un salto de linea y la identación debe ser de **cuatro espacios mas**.
###### Ejemplo en YAML
        keyObject: 
            child1: value
            child2: value
            childObject: 
                childChild: value
###### Ejemplo en JSON
        {
            "keyObject": {
                "child1": "value",
                "child2": "value",
                "childObject": {
                    "childChild": "value"
                }
            }
        }
### Arrays en YAML
Para definir un array usa el caracter pre definido `-`, un espacio y el item del array
###### Ejemplo en YAML
        array: 
            - item1
            - item2
            - itemKye: value
            - itemObject:
                  key: value
                  key: value
            - item3
              
###### Ejemplo en JSON
    {
      "array": [
        "item1",
        "item2",
        {
          "itemKye": "value"
        },
        {
          "itemObject": {
            "key": "value",
            "key2": "value"
          }
        },
        "item3"
      ]
    }
### Textos Largos
Para el caso de los textos largos YAML define dos opciones, usando el caracte `>` o usando el caracter `|`. en el caso de `>` los saltos de linea dentro del texto no se leen, el el caso de `|` si se leen.
###### Ejemplo en YAML
    longText: >
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
        Ut euismod consequat nisi. Proin eleifend eget mauris vel facilisis. 
        Praesent metus nunc, ullamcorper eget molestie et, lacinia id ante. 
        Phasellus tristique ultricies laoreet.
    longTextMultiline: |
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
        Ut euismod consequat nisi. Proin eleifend eget mauris vel facilisis. 
        Praesent metus nunc, ullamcorper eget molestie et, lacinia id ante. 
        Phasellus tristique ultricies laoreet.      
###### Ejemplo en JSON
    {
        "longText": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut euismod consequat nisi. Proin eleifend eget mauris vel facilisis.  Praesent metus nunc, ullamcorper eget molestie et, lacinia id ante.  Phasellus tristique ultricies laoreet.\n",
        "longTextMultiline": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. \nUt euismod consequat nisi. Proin eleifend eget mauris vel facilisis. \nPraesent metus nunc, ullamcorper eget molestie et, lacinia id ante. \nPhasellus tristique ultricies laoreet.\n"
    }
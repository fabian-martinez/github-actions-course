# Curso de Github Actions de Udemy
###### Fuente: https://www.udemy.com/course/github-actions/
## ¿Que es GitHub Actions?
Github action es una herramienta que permite automatizar el flujo de trabajo (***workflow***) para el desarrollo de un producto software. Escribiendo tareas individuales, llamadas ***actions***, y combinarlas para crear un ***workflow*** personalizado.
## ¿Que son los Workflows?
Los ***workflow*** son procesos automaticos personalizados que se pueden configurar en un repositorio de GitHub para construir, probar, empaquetar, publicar o desplegar dicho proyecto.

El workflow inicia a ejecutarse cuando ocurre un evento previamente definido en el workflow. Acontinuación estan los eventos que su ejecución:
* Push
* Pull Request (open, merged)
* Issue (create, close,...)
* Eventos programados
* Eventos externos

Cuando alguno de estos eventos ocurre, se inicia una maquina (***Runner***) por cada ***job*** que se tenga configurado en el workflow. Para cada job, se define un monton de ***steps*** donde cada uno realiza una tarea ***task***. Los jobs se pueden correr de manera paralela o dependientes uno de otro. 
## Runner
Un Runner es una maquina con la aplicación de GitHub Actions runner instalada. Este runner es responsable de ejecutar los jobs cada vez que un evento ocurre y tambien de motrar los resultados. Estos runner pueden ser alojados por GitHub (GitHub-hosted Runner) o sel alojados en nuestras propias maquina ()
### GitHub-hosted Runner
Los GitHub-hosted Runner son maquinas virtuales proveidas por GitHub y pueden tener SO (Linux, Windows y MacOS) on unos recursos especificos, mas detalle mirar (aqui)[https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners] 

Github tiene pre-instaladas diferentes herramientas deacuerdo a los requerimientos como pueden ser Android SDK o XCode o lenguajes como python o java y herramientas genericas como curl o git.

### Selft-hosted Runner
Los Selft-hosted Runner son maquinas que admnnistramos nostros mismos. Esto nos da mas control de los requerimientos de hardware para jobs mas grandes.


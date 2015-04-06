
# Indice para la generación de documentación avanzada y despliegue en github #

1. Instalar **git for windows** [http://git-scm.com/](http://git-scm.com/)
1. Crear un repositorio en github que se llame ***pruebas*** en github.com
1. clonar el proyectoWeb  del repositorio cursoMaven
1. Borrar las referencias a git (`git rm -rf`)
1. Modificar el pom añadiendo los plugins y sus propiedades tal y como aparece en [https://github.com/mike-ensor/clickconcepts-master-pom](https://github.com/mike-ensor/clickconcepts-master-pom)
	1. **CUIDADO:** Es necesario actualizar la versión de `maven-site-plugin`a la **3.3** y crear la sección `<reporting>`
	2. **NOTA II:** Es necesario en el `compiler-plugin`y en `javadoc-plugin` poner el `<encoding>`a *ISO-8859-1*
1. Crear los ficheros *pmd.xml y checkstyle.xml*
1. Crear una** clave ssh **e incluirla en el **ssh-agent** tal y como aparece en la documentación de github. [https://help.github.com/articles/generating-ssh-keys/](https://help.github.com/articles/generating-ssh-keys/)
	1. Opciones de trabajo con SSH [http://www.vilecha.com/hellguest/ssh_agent.asp](http://www.vilecha.com/hellguest/ssh_agent.asp)
1. Crear un `branch` nuevo en el respositorio _pruebas_ que se llame **gh-pages**
2. Generar la documentación inicialmente en **local** con:

		mvn clean verify site

1. Tras mostrar la documentación lanzar el comando:

		mvn clean site:site scm-publish:publish-scm 

1. También se puede mostrar un simulacro de ejecución sin despliegue con:

		mvn clean site:site scm-publish:publish-scm -Dscmpublish.dryRun=true

1. Cuando funcione cambiar el _skin_ a **fluido**. Para ello hay que crear un directorio **site**

		/src/site
	
	1. Y dentro	incluir el fichero **site.xml**
	2. Dependiendo del estilo de documentación hay que configurar un directorio u otro dentro de site con la plantilla web a utilizar [http://maven.apache.org/doxia/references/](http://maven.apache.org/doxia/references/)
	3. Crear también el directorio `/src/site/resources/imgs/` donde incluir los logotipos

La localización de la documentación se encuentra en:

[http://dpalomar.github.io/pruebas/index.html](http://dpalomar.github.io/pruebas/index.html)

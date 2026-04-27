# SmartData - Final Project - Top 100 Distritos con más extorsiones en el Perú

Proyecto final de Data Engineering con Azure Databricks de SmartData. Este proyecto presenta, a través de un análisis minucioso, __los 100 distritos con más casos de extorisión denunciados en el Perú en los últimos 5 años (desde 2021 hasta setiembre de 2025)__. Hola, mi nombre es Cristian, soy Ingeniero de Sistemas y debido a la realidad que atraviesa nuestro país respecto a la seguridad ciudadana, me vi en la necesidad de buscar fuentes de datos y armar este proyecto para mostrarte cuáles son los 100 distritos con más casos de extorsión. La extorsión se ha convertido en más que u que día a día nos mantiene tensos y que queremos que pare ya. Este no solo es un proyecto, es una muestra de la realidad de nuestro país para poder reflexionar c:

## Pasos para replicar este proyecto

1. El proyecto está hecho en Azure Databricks, por ende debes tener una cuenta de Azure. Puede ser gratis. Para ello, ve al siguiente link: https://azure.microsoft.com/es-mx/pricing/purchase-options/azure-account
2. Dentro de Azure, realizar el setup de los servicios que necesitaremos, para ello, seguiremos los pasos del siguiente manual: https://www.notion.so/Unit-Catalog-1ca71e129a518042a734c49a459d7646. De tener alguna duda, no dudes contactame por correo o por Linkedin: cristianjhair2000@gmail.com | https://www.linkedin.com/in/crisjhatin/
3. En el datalake de Azure, crear los siguientes containers:
  - raw
  - bronze
  - silver
  - golden
  - catalog
4. Agregar los datasets de esta repo en el container _raw_.
5. En el paso 2 ya se creó un servicio de Azure Databricks. Crear uno adicional para que simule el ambiente productivo. IMPORTANTE: Ambos serv. tienen que estar en una misma región.
6. Hasta el momento tenemos dos servicios de A. Databricks: 
- El primero, que se creó en el paso 2 y que simulará el ambiente de desarrollo.
- El segundo, creado en el paso anterior y que simulará el ambiente de producción. 
7. Ir al servicio de Azure Databricks productivo y crear cluster __cluster_SD__. Tendrá que tener dicho nombre para que después sea referenciado en el .yml. Aquí hay un ejemplo de cómo crear un cluster: ...
7. Ir al servicio de A. Databricks desarrollo y añadir Git Credential, ya que, para poder hacer push desde A. Databricks hacia un servicio externo como Github, necesitamos añadir nuestra credencial Git en Databricks. Por ello, en nuestro Databricks ir a __Settings>Linked accounts>Git integrations__ y completar los campos debidos:
8. Con ello, ya tenemos todos nuestros servicios listos para clonar esta repo.
9. Crea un repo en Github y luego la clonas en tu A. Databricks desarrollo. Para ello, dentro de A. Databricks ir a __Workspace>Create>Git folder__  y pegar el link de tu repo.
10. En Github, crea una rama llamada __construccion__.
11. De la misma forma, ahora clona esta repo también en tu A. Databricks desarrollo
12. En A. Databricks desarrollo, entra a tu repo y cambia al a rama __construccion__. Luego, traslada el contenido de mi repo al tuyo.
13. Por último, crear secrets en __Github__: Son necesarios para la ejecución del workflow del .yml. Para ello, ir a __repo>Settings>Secrets and variables>Actions>New repository secret__ y crear los siguientes 4 secrets:
- DATABRICKS_ORIGIN_HOST: Secret en GitHub que tiene como valor el link del Databricks dev hasta el .net.
- DATABRICKS_ORIGIN_TOKEN: Secret en GitHub que tiene como valor el token de Databricks de dev.
- DATABRICKS_DEST_HOST: Similar al primer item pero del Databricks prod.
- DATABRICKS_DEST_TOKEN: Similar al segundo item, pero del Databricks prod.

### Crear Access token en Databricks (DATABRICKS_ORIGIN_TOKEN y DATABRICKS_DEST_TOKEN)

En Databricks, ir a la siguiente ruta: __settings>developer>manage>generate new token__ y completar los siguientes campos en la ventana emergente:
- Name: GitHub
- lifetime: 30 days
- all-apis

Se creará un token en A. Databricks Dev y otro en A. Databricks Prod.




# <h1 align=center> **PROYECTO INDIVIDUAL Nº1** </h1>

## **Introducción al proyecto.**
Este proyecto consiste en la creacion de una api que nos permita acceder a una base de datos referida a peliculas de diversas plataformas de streaming por medio de cuatro consultas predeterminadas. Para permitir su fácil utilización todo ello se realizo dentro de un entorno de Docker. 

## **Modo de utilización.**

Luego de clonar el repositorio, realizar los siguientes comandos:

* docker build -t myimage .
* docker run -d --name mycontainer -p 80:80 myimage

Luego podra utilizar la api accediendo a http://localhost:80/docs 

## **Etapas del proyecto.**

<hr>  

#### **Analisis Exploratorio de Datos (EDA)**

Lo primero que cabe mencionar es que nuestros datos provienen de cuatro archivos diferentes, uno por cada plataforma de streaming. Estos se encuentran disponibles en la carpeta Datasets.

Lo relativo al analisis exploratorio  lo podemos encontrar en el archivo EDA.ipynb. Se eligió utilizar Jupyter Notebook por que nos permitio hacer el analisis mas sencillo y segmentado.
El primer paso fue ingestar los cuatro achivos en diferentes dataframes, analizarlos por separado y luego aplicando los cambios necesarios se concatenaron en un mismo dataframe.

Luego de ello, se analizaron duplicados, valores faltantes, se buscaron errores de carga y se uso Profile Report.

#### **Extracción, transformación y carga de los datos (ETL).**

El proceso de Etl lo encontramos en la carpeta y archivo con el mismo nombre. Luego de la ingesta de los datos se agrego una columna con el nombre de la correspondiente plataforma, por ejemplo "netflix". 
Luego se trasladaron valores mal ingestados de la columna "rating" a la columna "duration. A continuación, se concatenaron los cuatro dataframes, se separo la columna duration en una columna con valores INT y otra con los respectivos String.
No se eliminaron las columnas que no se usan, porque en los terminos del trabajo no se especifico (desde un punto de vista teorico) si estas debían ser utilizadas en el futuro o por otras personas y por ello se decidió conservarlas.
Por ultimo se guardo la información resultante en el archivo  Database. Se eligió sqlite porque dada su simpleza nos pareció el mas adecuado para el proyecto.
#### **Creacion de la API y entorno de Docker**
Se realiazo una app y para ello se utilizaron las librerias de uvicorn y fastapi. 
En cuanto a la Api, la encontramos en la carpeta con el mismo nombre. Esta utiliza diferentes métodos (get, post, delete y put) en la carpeta routes y en los archivos users y movies. Se conecta a dos bases de datos una de sqlite y la otra de MySql en la carpeta config y el archivo db.py. Para facilitar su funcionamiento tambien se creo la tabla users desde el archivo users.py en la carpeta models y la clase User desde el archivo user.py en la carpeta schemas.
Por último, el proyecto cuenta con los archivos Dockerfile y requirements para crear la imagen y permitir su sencilla utilizacion por otras personas. 

## **Herramientas utilizadas.**

* Vs Code.
* Python( pandas, numpy, sqlalchemy, fastapy).
* Jupyter Notebook.
* Docker.
* Sqlite.

Autor: Nadia Obando

Familia: Magnoliaceae
# Tema: Relacion evolutiva del gen rbcL en Magnoliaceae
![alt text](https://jeppastradgard.se/wp-content/uploads/2024/12/PTM023_Little-Gem-Magnolia-.jpg)
# Programas a utilizar:
* Muscle (muscle3.8.31_i86linux64): alinear
* IQ-TREE (iqtree/2.2.2.6): Contruir el arbol filogenetico
* Figtree: Visualizar arbol 
# Propósito del proyecto
* El estudio de la filogenia y las relaciones evolutivas en la familia Magnoliaceae, un grupo basal de plantas con más de 100 millones de años dentro del clado Magnoliidae, es fundamental para entender su historia y diversidad.
* Estos avances ayudan a clarificar la evolución, diversidad y taxonomía de esta familia, además de apoyar la conservación de sus especies, muchas de las cuales son endémicas y ecológicamente importantes.
* Git Bash es fundamental para gestionar y reproducir los datos y análisis computacionales que permiten reconstruir las relaciones evolutivas por lo que esta herramienta es de gran ayuda en el estudio del gen rbcL ya que implica trabajar con grandes conjuntos de secuencias genéticas, ejecutar software especializado para alineamientos, construir árboles filogenéticos y manejar versiones de datos y scripts de análisis. 
# Requisitos para ejecutar el programa
* Instalación de Git Bash en el sistema operativo Windows (de ser el caso) y que los comandos sean ejecutables.
* Ingreso a hoffman y la carpeta personal de Nombre NadiaOT
* Instalación de herramientas bioinformáticas como:iqtree/2.2.2.6 
# Resumen de lo que se va hacer
Abrir Git Bash, entrar a Hoffman y navegar a la carpeta en donde estan todos los archivos, ejecutar Muscle para alinear las secuencias, ejecutar IQ-TREE para construir el árbol filogenético y abrir el archivo creado en Abre FigTree.
# Data
Las secuencias del gen se encuentran en la carpeta  dentro de NadiaOT
# Comandos
* ssh dechavez@hoffman2.idre.ucla.edu
* Leptailurus01&
* qrsh -l h_rt=4:00:00,h_vmem=30G -pe shared 4
* cd $SCRATCH/
* cd Bioinformatica-PUCE/
* cd RediseBio/
* cd NadiaOT/
* cd TrabajoFinal/
* cd 
* grep "rpl10" Orthologs.IDS.txt
*  ./datasets download gene symbol rpl10 --ortholog Magnoliaceae --filename rpl10_Magnoliaceae.zip
*  unzip rpl10_Magnolia.zip
*  nano rna.fna #Crear un espacio en el archivo con enter y borrar este mismo espacio, esto se hace para que se detecte que hubo un cambio y guarde, ademas se debe cambiar el nombre a rpl10.fna
*  cd rpl10/Magnoliaceae
*  cp ../muscle3.8.31_i86linux64 .
*  cp ../rpl10.fna .
  * /muscle3.8.31_i86linux64 -in rna.fna -out muscle_rna.fna -maxiters 1 -diags #(opcion 1)
  * for filename in *.fasta
>do
>./muscle3.8.31_i86linux64 -in $filename -out musscle_$filename
>done (Opcion 2)
* module load iqtree/2.2.2.6 
* iqtree2
* for filename in musscle_*
>do
>iqtree2 -s $filename
>done
* scp dechavez@hoffman2.idre.ucla.edu: “la direccion exacta del documento” ./ #(en otra terminal)
* Leptailurus01&

# Resultados
Se visuliza una filogenia del gen rpl10 en Fig tree, aqui se va poder ver  un árbol filogenético que muestra cómo se agrupan y diferencian las especies de Magnoliaceae según las secuencias de rpl10, con ramas que reflejan el grado de similitud y nodos con soporte estadístico.

# Tema: Relación evolutiva del gen rbcL en Magnoliaceae

Autor: Nadia Obando

Familia: Magnoliaceae

![alt text](https://jeppastradgard.se/wp-content/uploads/2024/12/PTM023_Little-Gem-Magnolia-.jpg)
# Propósito del proyecto
* El estudio de la filogenia y las relaciones evolutivas en la familia Magnoliaceae, un grupo basal de plantas con más de 100 millones de años dentro del clado Magnoliidae (Grupo de Filogenia de las Angiospermas, 2009), es fundamental para entender su historia y diversidad.
* La filogenia de la familia Magnoliaceae utilizando secuencias del gen rbcL nos ayudara a evaluar las relaciones evolutivas entre sus géneros y especies. El gen rbcL, que codifica la subunidad grande de la enzima RuBisCO involucrada en la fotosíntesis, es un marcador molecular comúnmente empleado en estudios sistemáticos por su conservación y utilidad para resolver relaciones evolutivas a nivel familiar y supraespecífico (Li & Conran, 2003;Zhao et al., 2023).
* A través del análisis filogenético basado en este gen, se busca:
  
  Identificar patrones de divergencia genética dentro de la familia.
  
  Comparar los agrupamientos filogenéticos con las clasificaciones taxonómicas tradicionales.
  
  Contribuir al entendimiento de la evolución temprana de las angiospermas, dado el carácter basal de Magnoliaceae dentro del clado de las dicotiledóneas ya que esta familia representa un grupo de gran relevancia evolutiva debido a su antigüedad, esta característica la convierte en un elemento fundamental para el estudio de la evolución y ecología de las plantas con flores (Grupo de Filogenia de las Angiospermas, 2009).
  
* Este enfoque filogenético también puede servir como base para futuros estudios de biogeografía, conservación y evolución morfológica dentro del grupo ademas de que nos ayudan a clarificar la evolución, diversidad y taxonomía de esta familia, además de apoyar la conservación de sus especies, muchas de las cuales son endémicas y ecológicamente importantes.
* Git Bash es fundamental para gestionar y reproducir los datos y análisis computacionales que permiten reconstruir las relaciones evolutivas por lo que esta herramienta es de gran ayuda en el estudio del gen rbcL ya que implica trabajar con grandes conjuntos de secuencias genéticas, ejecutar software especializado para alineamientos, construir árboles filogenéticos y manejar versiones de datos y scripts de análisis.

# Programas a utilizar:
* Muscle (muscle3.8.31_i86linux64): realiza alineamientos múltiples de secuencias de ADN, ARN o proteínas.
  
  Este  programa bioinformático ya esta instaldo dentro de la carpeta
  
* IQ-TREE (iqtree/2.2.2.6): Construye árboles filogenéticos mediante máxima verosimilitud.
  
  Este programa lo vamos instalar directamnete en git bash con module load.
  
* Figtree: visualizar árboles filogenéticos
  
  Descargar la versión adecuada para tu sistema operativo en: http://tree.bio.ed.ac.uk/software/figtree/
  
  FigTree está desarrollado en Java, así que asegúrate de tener instalada una versión de esta: https://www.java.com/es/download/
  
* Atom: Editor de texto de código abierto
  
  Descargar el editor de texto en: https://atom-editor.cc/
  
# Requisitos para ejecutar el programa
* Instalación de Git Bash en el sistema operativo Windows (de ser el caso) y que los comandos sean ejecutables.
* Tener acceso a hoffman y a la carpeta personal de Nombre NadiaOT
* Instalación de herramientas bioinformáticas. 
# Resumen de lo que se va hacer
Abrir Git Bash, entrar a Hoffman y navegar a la carpeta en donde estan todos los archivos, ejecutar Muscle para alinear las secuencias, ejecutar IQ-TREE para construir el árbol filogenético y abrir el archivo creado en FigTree.
# Data
Las secuencias del gen se encuentran en la carpeta  dentro de NadiaOT
# ¿Cómo utilizar los comandos paso a paso?
* Ingresar a Hoffman
  
  ssh dechavez@hoffman2.idre.ucla.edu
  
  Leptailurus01&
  
* Pedir almacenamiento
  
  qrsh -l h_rt=4:00:00,h_vmem=30G -pe shared 4
  
* Ingresar a la carpeta
  
  cd $SCRATCH/
  
  cd Bioinformatica-PUCE/
  
  cd RediseBio/
  
  cd NadiaOT/
  
  cd TrabajoFinal/
  
* Buscar y descargar el gen
  
  En caso de utilizar genes genes ortólogos utilizar Orthologs.IDS.
  
  grep "rpl10" Orthologs.IDS.txt #En caso de utilizar orthologs (Grep nos sirve para saber si el gen dentro de Orthologs.IDS.)
  
  ./datasets download gene symbol rpl10 --ortholog Magnoliaceae --filename rpl10_Magnoliaceae.zip (Descargar los genes)
  
  En este caso el gen rbcL no se encuentra en Orthologs.IDS., entonces utilizaremos el siguiente comando para obtener los genes de la familia Magnoliaceae
  
  /u/scratch/d/dechavez/Bioinformatica-PUCE/MastBio/edirect/esearch -db nuccore -query "rbcL [GENE] AND Magnoliaceae[ORGN]" | efetch -format fasta > Gen_rbcL_Magnoliaceae.zip
  
* Descomprimir el gen
  
  unzip rpl10_Magnolia.zip
  
  nano rna.fna #Crear un espacio en el archivo con enter y borrar este mismo espacio, esto se hace para que se detecte que hubo un cambio y guarde, ademas se debe cambiar el nombre a rpl10.fna
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
* pwd #(en offman para saber en que lugar estoy localizado y se obtendra la direccion exata deol documento)
* scp dechavez@hoffman2.idre.ucla.edu: “la direccion exacta del documento” ./ #(en otra terminal)
* Leptailurus01&

# Resultados
*Se visuliza una filogenia del gen rpl10 en Fig tree, aqui se va poder ver  un árbol filogenético que muestra cómo se agrupan y diferencian las especies de Magnoliaceae según las secuencias de rpl10, con ramas que reflejan el grado de similitud y nodos con soporte estadístico.
# Bibliografía
* Grupo de Filogenia de las Angiospermas. (2009). Actualización de la clasificación del Grupo de Filogenia de las Angiospermas para los órdenes y familias de plantas con flores: APG III. Botanical Journal of the Linnean Society , 161 (2), 105-121.
* Li, J., y Conran, JG (2003). Relaciones filogenéticas en la subfamilia Magnoliaceae. Magnolioideae: un análisis cladístico morfológico. Sistemática y evolución de plantas , 242 , 33-47.
* Zhao, J., Chen, H., Li, G., Jumaturti, M. A., Yao, X., & Hu, Y. (2023). Phylogenetics Study to Compare Chloroplast Genomes in Four Magnoliaceae Species. Current issues in molecular biology, 45(11), 9234–9251. https://doi.org/10.3390/cimb45110578


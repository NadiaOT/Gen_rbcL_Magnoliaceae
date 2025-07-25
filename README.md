# Relación evolutiva del gen ycf68 en Magnoliaceae

Autor: Nadia Obando

![alt text](https://jeppastradgard.se/wp-content/uploads/2024/12/PTM023_Little-Gem-Magnolia-.jpg)
# Propósito del proyecto
* El estudio de la filogenia y las relaciones evolutivas en la familia Magnoliaceae, un grupo basal de plantas con más de 100 millones de años dentro del clado Magnoliidae (Grupo de Filogenia de las Angiospermas, 2009), es fundamental para entender su historia y diversidad.
  
* La filogenia de la familia Magnoliaceae utilizando secuencias del gen rbcL nos ayudara a evaluar las relaciones evolutivas entre sus géneros y especies. La familia presenta alrededor de 350 especies reconocidas mundialmente con una gran diversidad morfológica y ecológica considerable (Castañeda, 2015), pero aún existen relaciones evolutivas poco claras entre sus linajes. El uso de nuevos marcadores moleculares, como el gen plastidial ycf68, podría ayudar a resolver nodos filogenéticos no resueltos y mejorar la comprensión de su historia evolutiva, además la diferencia de marcadores moleculares más habituales como matK o rbcL, el gen ycf68 ha sido poco explorado en estudios filogenéticos, lo que convierte a este trabajo en una oportunidad para diversificar los genes empleados en la sistemática de plantas.(Tian, Han, Chen & Wang, 2018;Gallego Zaragoza, 2016).
  
* Este trabajo busca:

Generar una filogenia más sólida que puede contribuir a una mejor delimitación de especies y géneros, aspecto crucial en grupos como las Magnolias, que poseen un alto valor ecológico.

  Contribuir al entendimiento de la evolución temprana de las angiospermas, dado el carácter basal de Magnoliaceae dentro del clado de las dicotiledóneas ya que esta familia representa un grupo de gran relevancia evolutiva debido a su antigüedad, esta característica la convierte en un elemento fundamental para el estudio de la evolución y ecología de las plantas con flores (Grupo de Filogenia de las Angiospermas, 2009).
  
* Este enfoque filogenético también puede servir como base para futuros estudios de biogeografía, conservación y evolución morfológica dentro del grupo ademas de que nos ayudan a clarificar la evolución, diversidad y taxonomía de esta familia, además de apoyar la conservación de sus especies, muchas de las cuales son endémicas y ecológicamente importantes.
* Git Bash es fundamental para gestionar y reproducir los datos y análisis computacionales que permiten reconstruir las relaciones evolutivas por lo que esta herramienta es de gran ayuda en el estudio del gen rbcL ya que implica trabajar con grandes conjuntos de secuencias genéticas, ejecutar software especializado para alineamientos, construir árboles filogenéticos y manejar versiones de datos y scripts de análisis.

# Programas a utilizar:
* Muscle (muscle3.8.31_i86linux64): realiza alineamientos múltiples de secuencias de ADN, ARN o proteínas.
  
  Este  programa bioinformático ya esta instalado dentro de la carpeta
  
* IQ-TREE (iqtree/2.2.2.6): Construye árboles filogenéticos mediante máxima verosimilitud.
  
  Este programa lo vamos instalar directamnete en git bash con module load.
  
* Figtree: visualizar árboles filogenéticos
  
  Descargar la versión adecuada para tu sistema operativo en: http://tree.bio.ed.ac.uk/software/figtree/
  
  FigTree está desarrollado en Java, así que asegúrate de tener instalada una versión de esta: https://www.java.com/es/download/
  
* Atom: Editor de texto de código abierto
  
  Descargar el editor de texto en: https://atom-editor.cc/
  
# Requisitos para ejecutar el programa
* Instalación de Git Bash https://gitforwindows.org/ en el sistema operativo Windows (de ser el caso) y que los comandos sean ejecutables.
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
  
  qrsh -l h_rt=6:00:00,h_vmem=60G -pe shared 4
  
* Ingresar a la carpeta
  
  cd $SCRATCH/
  
  cd Bioinformatica-PUCE/
  
  cd RediseBio/
  
  cd NadiaOT/
  
  cd Magnoliaceae/
  
* Buscar y descargar el gen
  
  En caso de utilizar genes ortólogos utilizar Orthologs.IDS.
  
  grep "ycf68" Orthologs.IDS.txt (Grep nos sirve para saber si el gen dentro de Orthologs.IDS.)
  
  ./datasets download gene symbol ycf68 --ortholog Magnoliaceae --filename ycf68_Magnoliaceae.zip (Descargar los genes)
  
  En este caso el gen ycf68 no se encuentra en Orthologs.IDS., entonces utilizaremos el siguiente comando para obtener los genes de la familia Magnoliaceae
  
  Opción 1: Esta opción selecciona solo genes ortólogos (es mas especifica)

  /u/scratch/d/dechavez/Bioinformatica-PUCE/MastBio/edirect/esearch -db nuccore -query "ycf68 [GENE] AND Magnoliaceae[ORGN]" | efetch -format fasta > ycf68_Magnoliaceae.fasta (En este caso se utilizo este comando)

  Opción 2: Esta en cambio es una opción mas general

  esearch -db nucleotide -query "Magnoliaceae[Organism] AND ycf68[Gene]" | efetch -format fasta > ycf68_Magnoliaceae.fasta 

  Nota: En caso de tener el documento comprimido utilizar este comando para descomprimir: unzip "Nombre del documento"

* Descargar el gen en nuestro ordenador para editar el texto en Atom:

  pwd (en Hoffman para saber en que lugar estoy localizado y se obtendra la dirección exacta del archivo)
  
  scp dechavez@hoffman2.idre.ucla.edu:“la direccion exacta del archivo” ./ (en otra terminal)
  
  Contraseña: Leptailurus01&

* Ingresar a Atom y abrir el archivo descargado, realizar los cambios necesarios y guardar con un nuevo nombre
  
 Find: (>\w+)\.\d\s+(\w+)\s+(\w+).*

 Replace: $1_$2_$3
 
 En este caso el nuevo archivo se llama "ycf68_MagnoliaceaeAtm.fasta"
 
* Subir el archivo a Hoffman

En otra terminal desde el escritorio:

scp ycf68_MagnoliaceaeAtm.fasta dechavez@hoffman2.idre.ucla.edu:"Direccion exacta en el lugar en el que se desea subir a Hoffman"

Contraseña: Leptailurus01&

* Ejecutar muscle para el alineamiento

Opcion 1: 

./muscle3.8.31_i86linux64 -in ycf68_MagnoliaceaeAtm.fasta -out ycf68_MagnoliaceaeAtm.fasta.muscle -maxiters 1 -diags 

Opcion 2: 

  Nota: Si el alineamiento se demora mucho tiempo debido a la cantidad de secuencias debe correr Header.sh (Aqui estan los comandos para que se haga el alineamiento, ante srealizar cambios de acuerdo a su archivo)

Para correr Header.sh deber hacer lo siguiente: 

   qsub Header.sh
  
   myjobs

 Nota: Si deseas ver los comandos que hay en este archivo realizar el siguiente comando:

  cat Header.sh (Ver la información)

  nano Header.sh (Realizar cambios)


* Ejecutar IQTREE

  module load iqtree/2.2.2.6 

  iqtree2

   for filename in *.fasta.muscle
do
    iqtree2 -s "$filename" -m MFP -bb 1000 -nt AUTO
done


* Descargar el archivo que termine en .treefile en nuestra computadora ( En este caso ycf68_MagnoliaceaeAt.fasta.muscle.treefile)
  
  pwd (en Hoffman para saber en que lugar estoy localizado y se obtendra la direccion exacta)
  
  scp dechavez@hoffman2.idre.ucla.edu:“la direccion exacta del archivo” ./ (en otra terminal)
  
  Contraseña: Leptailurus01&

* Abrir el archivo en Fig tree para visualizar el árbol 

# Resultados

Se visuliza una filogenia del gen ycf68 en Fig tree. El análisis incluyó representantes de varias especies del género Magnolia, obteniendo un árbol filogenético que revela agrupamientos coherentes con relaciones taxonómicas previamente propuestas. Por ejemplo as secuencias de Magnolia maudiae (NC_047409 y MK831950) se agrupan juntas, formando un clado consistente, por otro lado Magnolia virginiana, una especie americana, se agrupa más cercanamente a especies asiáticas como Magnolia macclurei, lo cual podría reflejar un patrón evolutivo conservado en el gen ycf68 o posibles relaciones más complejas entre distintos linajes, ademas  Magnolia chapensis (NC_053737 y MT44723) aparecen como un clado bien definido, lo que indica una alta similitud entre ambas secuencias, posiblemente  ensamblajes de la misma especie.

Los resultados obtenidos indican que el gen ycf68 presenta un nivel de variación adecuado para inferir relaciones evolutivas. Sin embargo, también se observaron casos en los que su capacidad de resolución resulta limitada o poco clara pero podría desempeñar un papel útil como marcador complementario, particularmente en análisis filogenéticos que integran múltiples genes.

# Carpeta de Magnoliaceae dentro de NadiaOT

Cosas importantes que vamos encontrar en esta carpeta: 

Data: Las secuencias del gen

ycf68_Magnoliaceae.fasta: Secuencia descargada

ycf68_MagnoliaceaeAtm.fasta: Secuencia modificada en ATOM

ycf68_MagnoliaceaeAtm.fasta.muscle: Secuencia alineada

Data_IQtree: Resultados de la filogenia 

Scripts_Filogenia_Magnoliaceae: Scripts para realizar el trabajo

 muscle3.8.31_i86linux64: Programa 

# Bibliografía

* Gallego Zaragoza, A. (2016). Secuenciación, ensamblaje de novo y anotación del genoma del cloroplasto del ajo (Allium sativum). https://dspace.umh.es/handle/11000/3562
  
* Grupo de Filogenia de las Angiospermas. (2009). Actualización de la clasificación del Grupo de Filogenia de las Angiospermas para los órdenes y familias de plantas con flores: APG III. Botanical Journal of the Linnean Society , 161 (2), 105-121.
  
* CASTAÑEDA, Á. J. P. (2015). Taxonomía y conservación de la familia Magnoliaceae en el Ecuador (Doctoral dissertation, PONTIFICIA UNIVERSIDAD CATÓLICA DEL ECUADOR). https://repositorio.puce.edu.ec/items/fbcad69c-efe2-4270-87a0-e7c5d048d0d6
  
* Tian, N., Han, L., Chen, C. y Wang, Z. (2018). Secuencia completa del genoma del cloroplasto de Epipremnum aureum y su análisis comparativo entre ocho especies de Araceae. PLoS One , 13 (3), e0192956. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0192956 
  

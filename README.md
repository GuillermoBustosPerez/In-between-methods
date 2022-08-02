### Note for Reviewers

The present repository contains all data and code of employed for the
development of the present article.  
Please note that this is a private repository intended for reviewers
only. If the article is accepted for publication the present repository
will be made public and published in Zenodo (<https://zenodo.org/>)
under a DOI.

Other examples of published data:

-   Bustos-Pérez, G., Baena, J., 2021. Predicting Flake Mass: A View
    from Machine Learning. Lithic Technology 46, 130–142.
    <https://doi.org/10.1080/01977261.2021.1881267>  
-   Link to Zenodo repository:
    <https://zenodo.org/record/4603149#.YmZzKdpBwdU>

### Repository data

**Journal:**

-   Journal of Lithic Studies

**Authors:**:

-   Guillermo Busto-Pérez<sup>1, 2, 3</sup>  
-   Javier Baena<sup>1</sup>  
-   Manuel Vaquero<sup>2, 3</sup>

<sup>1</sup>Universidad Autónoma de Madrid. Departamento de Prehistoria
y Arqueología, Campus de Cantoblanco, 28049 Madrid, Spain. Email:
<guillermo.willbustos@gmail.com>; <javier.baena@uam.es>  
<sup>2</sup>Institut Català de Paleoecologia Humana i Evolució Social
(IPHES-CERCA), Zona Educacional 4, Campus Sescelades URV (Edifici W3),
43007 Tarragona, Spain.  
<sup>3</sup>Universitat Rovira i Virgili, Departament d’Història i
Història de l’Art, Avinguda de Catalunya 35, 43002 Tarragona, Spain

**Corresponding Author**:

-   Guillermo Bustos-Pérez  
-   <guillermo.willbustos@gmail.com>

**Article title:**

-   What lies in between: Levallois, Discoid and intermediate methods

**Abstract**  
The production of lithic artefacts is usually associated to different
knapping methods. Resulting flakes present metric and technological
features representative of the flaking method from which they were
detached. However, lithic production is a dynamic process where discrete
methods can be blurred, with features varying along the process. An
intermediate knapping method between discoidal and Levallois is commonly
referred under an umbrella of terms, presenting a wide geographical and
chronological distribution along the Early and Middle Palaeolithic.
Because this intermediate knapping method presents features from both
discoidal and Levallois knapping methods, this raises the question of up
to what point flakes from the three knapping methods can be
differentiated between each other and the directionality of confusions.
An experimental assemblage of flakes detached from the three methods is
employed along with attribute analysis and Machine Learning models to
identify the knapping method from which the flakes were detached. On a
general level results provide an excellent ability to differentiate
between the three knapping methods when a Support Vector Machine with
polynomial kernel is employed. Results also outline the singularity of
flakes detached from Levallois reduction sequences with an outstanding
value of identification, and being rare that they are erroneously
attributed to any of the other two knapping methods. Confusion between
discoidal and Hierarchical Discoid products is more common, although a
good value of identification is achieved for discoidal flakes and an
acceptable value is achieved in the case of Hierarchical Discoid flakes.
This shows the potential applicability of machine learning models in
combination with attribute analysis for the identification of these
knapping methods among flakes.

**Key words**: lithic technology; experimental archaeology; Levallois;
Discoid; Machine Learning; Middle Paleolithic

**Extended abstarct (in spanish)**  
La producción de lascas se asocia a diferentes métodos de talla. Las
lascas resultantes presentan características métricas y atributos que
son representativos del método de talla del que se han producido. Sin
embargo, la talla lítica es un proceso dinámico en el que los métodos de
talla definidos pueden verse entremezclados debido a adaptaciones a las
características volumétricas y de calidad de la materia prima,
diferentes fases a lo largo del proceso de reducción, aspectos
cronoculturales, etc. Esto da lugar a que las características de los
productos de talla varíen a lo largo del proceso de reducción. Bajo
diferentes términos es común encontrar alusiones a un método de talla
intermedio entre el discoide y el Levallois, presentando una amplia
distribución geográfica y cronológica a lo largo del Paleolítico Medio y
el Paleolítico Medio inicial. La concepción de este método de talla,
referido en el presente documento como Discoide Jerárquico, posee
características intermedias entre el Levallois (jerarquización de
superficies no intercambiables o un plano de talla paralelo a la
intersección de ambas superficies) y el discoide (ausencia de
preparación de talones, planos de talla secantes en la fase inicial de
talla), surgiendo la duda de hasta qué se pueden diferenciar los
productos de lascado de los tres métodos y sobre la direccionalidad de
las confusiones.

El presente trabajo emplea un conjunto experimental de lascas
procedentes de los tres métodos de talla (77 del método de talla
discoide, 73 del Levallois y 72 del Discoide Jerárquico). Sobre este
conjunto experimental de lascas se realiza un análisis métrico y de
atributos, y sobre los datos procedentes de este análisis se entrenan
diez algoritmos de aprendizaje automático con el objetivo de determinar
hasta qué punto es posible diferenciar el método de talla. Para evaluar
los algoritmos de aprendizaje automático se tiene en cuenta la precisión
general de los modelos, pero también los efectos del uso de umbrales de
probabilidad en la identificación de los métodos de talla. El uso de
umbrales de probabilidad permite optimizar el ratio de positivos
verdaderos y positivos falsos para cada umbral de decisión y de ahí
extraer el “área bajo la curva” (AUC en inglés) como valor de avaluación
de un modelo.

De los diez algoritmos de aprendizaje automático, una máquina de vector
soporte con kernel polinomial presenta los mejores resultados en la
identificación de los tres métodos de talla, proporcionando unos
resultados excelentes a la hora de diferenciar entre los tres métodos a
nivel general (0.667 precisión, 0.824 AUC). Considerando individualmente
cada método de talla, los resultados subrayan el carácter singular de
las lascas procedentes de secuencias de reducción Levallois ya que
obtienen una identificación excepcionalmente buena (AUC de 0.91), siendo
su procedencia raramente atribuida a cualquiera de los otros dos
métodos. La confusión entre productos procedentes de secuencias de talla
discoide y el Discoide Jerárquico es más común, aunque se alcanza una
identificación excelente en el caso de los productos procedentes de
reducciones discoides (AUC de 0.82) y una identificación aceptable en el
caso los productos procedentes del Discoide Jerárquico (AUC de 0.73).

Estos resultados muestran el potencial de combinar modelos de
aprendizaje automático con análisis de atributos sobre lascas para la
identificación de métodos de talla. Su uso puede servir de gran ayuda en
la identificación de métodos de talla en lascas. Sin embargo, su uso
requiere de una evaluación previa de los conjuntos líticos para
determinar posibles métodos de talla existentes, uso diferencial de las
materias primas, y evaluación de las cadenas operativas presentes.

**Palabras clave**: tecnología lítica; arqueología experimental;
Levallois; Discoid; Paleolítico Medio; Aprendizaje Automático

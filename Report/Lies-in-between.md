# What lies in between: Levallois, discoid and intermediate methods

Guillermo Bustos-Pérez $^{1,2,3}$, Javier Baena $^{1}$, Manuel Vaquero
$^{2,3}$

$^1$ Universidad Autónoma de Madrid. Departamento de Prehistoria y
Arqueología, Campus de Cantoblanco, 28049 Madrid, Spain  
$^2$ Institut Català de Paleoecologia Humana i Evolució Social (IPHES),
Zona Educacional 4, Campus Sescelades URV (Edifici W3), 43007 Tarragona,
Spain  
$^3$ Universitat Rovira i Virgili, Departament d’Història i Història de
l’Art, Avinguda de Catalunya 35, 43002 Tarragona, Spain

<div align="justify">

**Abstract**  
Lithic artefacts are usually associated with the different knapping
methods used in their production. Flakes exhibit metric and
technological features representative of the flaking method used to
detach them. However, lithic production is a dynamic process in which
discrete methods can be blurred, and in which features can vary
throughout the process. An intermediate knapping method between the
discoid and Levallois is commonly referred to under an umbrella of terms
(the present research uses the term hierarchical discoid), and is
associated with a broad geographical and chronological distribution
throughout the Early and Middle Palaeolithic. This intermediate knapping
strategy exhibits features of both the discoid and Levallois knapping
methods, raising the question of the extent to which flakes from the
three knapping methods can be differentiated and, when one is mistaken
for another, the direction of confusion. An experimental assemblage of
flakes detached by means of the three methods was used along with an
attribute analysis and machine learning models in an effort to identify
the knapping methods employed. In general, our results were able to very
effectively differentiate between the three knapping methods when a
support vector machine with polynomial kernel was used. Our results also
underscored the singularity of flakes detached by means of Levallois
reduction sequences, which yielded outstanding identification values,
and were rarely erroneously attributed to either of the other two
knapping methods studied. Mistaking the products of the discoid and
hierarchical discoid methods was the most common direction of confusion,
although a good identification value was achieved for discoid flakes and
an acceptable value for hierarchical discoid flakes. This shows the
potential applicability of machine learning models in combination with
attribute analysis for the identification of these knapping methods
among flakes.

**Keywords:** lithic technology; experimental archaeology; Levallois;
discoid; Middle Palaeolithic; machine learning

**Extended abstract**  
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

## 1. Introduction

The Middle Palaeolithic in western Europe is characterised by the
increase in and diversification of prepared core knapping methods,
resulting in flake-dominated assemblages ([Kuhn
2013](#ref-kuhn_roots_2013)). These flake-dominated assemblages are the
result of a wide number of production methods including Levallois
([Boëda 1994](#ref-boeda_concept_1994); [Boëda
1995b](#ref-dibble_levallois:_1995); [Boëda *et al.*
1990](#ref-boeda_identification_1990)), discoid ([Boëda
1993](#ref-boeda_debitage_1993); [Boëda
1995a](#ref-boeda_caracteristiques_1995)), the *système par surface de
débitage alterné* or SSDA ([Forestier
1993](#ref-forestier_clactonien:_1993); [Ohel *et al.*
1979](#ref-ohel_clactonian_1979)), Quina ([Bourguignon
1996](#ref-bourguignon_conception_1996); [Bourguignon
1997](#ref-bourguignon_mousterien_1997)), different laminar production
systems ([Boëda 1990](#ref-farizy_surface_1990); [Révillon & Tuffreau
1994](#ref-revillon_les_1994)), and the Kombewa ([Newcomer &
Hivernel-Guerre 1974](#ref-newcomer_nucleus_1974); [Tixier & Turq
1999](#ref-tixier_kombewa_1999)) among several others. This abundance of
different production methods results in a highly diversified material
culture in which flakes exhibit great morphological variability. Flakes
often retain morphologies and attributes characteristic of the knapping
method used to detach them, facilitating the identification of those
methods. However, flakes also often present overlapping attributes and
morphologies as a result of the high internal variability of the methods
used and the fact that flakes with similar functional properties can be
produced via different methods Kuhn ([2013](#ref-kuhn_roots_2013)).Due
to their extensive geographical and chronological distribution, the
Levallois and discoid constitute important sources of cultural
variability in the Middle Palaeolithic of western Europe.

Boëda ([1994](#ref-boeda_concept_1994);
[1995b](#ref-dibble_levallois:_1995)) establishes six characteristics
that define the Levallois knapping strategy from a technological
perspective:

1)  The volume of the core is conceived in two convex asymmetric
    surfaces.  
2)  These two surfaces are hierarchical and are not interchangeable.
    They retain their role of either striking or debitage (or
    exploitation) surface throughout the entire reduction process.  
3)  The distal and lateral convexities of the debitage surface are
    maintained to obtain predetermined flakes.  
4)  The plane of fracture of the predetermined products is parallel to
    the intersection of the two surfaces.  
5)  The striking platform is perpendicular to the overhang (the core
    edge, at the intersection between the two core surfaces).  
6)  The technique employed during the knapping process is direct
    percussion with a hard hammer.

Depending on the organisation of the debitage surface, Levallois cores
are usually classified as a preferential method (in which a single
predetermined Levallois flake is obtained from the debitage surface) or
as recurrent methods (in which several predetermined flakes are produced
from the debitage surface) with removals being either unidirectional,
bidirectional or centripetal ([Boëda
1995b](#ref-dibble_levallois:_1995); [Boëda *et al.*
1990](#ref-boeda_identification_1990); [Delagnes
1995](#ref-dibble_variability_1995); [Delagnes & Meignen
2006](#ref-hovers_diversity_2006)).

Because of its early recognition in the XIX century ([Mortillet 1885:
pp.:235–236](#ref-mortillet_prehistorique_1885)), its association with
the cognitive abilities of planning and predetermination ([Boëda
1994](#ref-boeda_concept_1994); [Pelegrin
2009](#ref-pelegrin_cognition_2009)), and its use for the definition of
cultural facies ([Bordes 1961a](#ref-bordes_mousterian_1961); [Bordes
1953](#ref-bordes_levalloisien_1953)) and lithic technocomplexes
([Delagnes *et al.* 2007](#ref-vandermeersch_les_2007); [Faivre *et al.*
2017](#ref-faivre_late_2017)), Levallois flaking technology is
considered a trademark of the Middle Palaeolithic. The emergence of the
Levallois method has been observed from MIS 12 to MIS 9, with several
sites yielding artefacts characteristic of this knapping strategy
([Carmignani *et al.* 2017](#ref-carmignani_technological_2017);
[Hérisson *et al.* 2016](#ref-herisson_emergence_2016); [Moncel *et al.*
2020](#ref-moncel_early_2020); [Soriano & Villa
2017](#ref-soriano_early_2017); [White & Ashton
2003](#ref-white_lower_2003)). However, the Levallois is clearly
generalised and identified from MIS 8 onwards, covering an extensive
geographical area throughout western Europe ([Delagnes *et al.*
2007](#ref-vandermeersch_les_2007); [Delagnes & Meignen
2006](#ref-hovers_diversity_2006); [Faivre *et al.*
2017](#ref-faivre_late_2017); [Geneste
1990](#ref-geneste_developpement_1990)).The extensive geographical area
and long temporal span of the Levallois creates additional layers of
variability which can result from raw material constraints, synchronic
variability as a result of different site functionalities, chronological
trends in the development of methods, or shifts in the technological
organisation of groups. It is also important to highlight the explicit
recognition of Levallois cores after MIS 8, while a multitude of terms
were employed to define previous hierarchical knapping strategies and
their possible coexistence with Acheulean technocomplexes ([Moncel *et
al.* 2020](#ref-moncel_early_2020); [Santonja *et al.*
2016](#ref-santonja_coexistence_2016); [Hérisson *et al.*
2016](#ref-herisson_emergence_2016); [Rosenberg-Yefet *et al.*
2022](#ref-rosenberg-yefet_lower_2022); [White & Ashton
2003](#ref-white_lower_2003); [Scott & Ashton
2011](#ref-scott_early_2011)).

Boëda ([1993](#ref-boeda_debitage_1993);
[1994](#ref-boeda_concept_1994);
[1995a](#ref-boeda_caracteristiques_1995)), also establishes six
technological criteria defining the discoid method:

1)  The volume of the core is conceived as two oblique asymmetric convex
    surfaces delimited by an intersection plane.  
2)  These two surfaces are not hierarchical as it is possible to
    alternate the roles of the percussion and exploitation surfaces.  
3)  The peripheral convexity of the debitage surface is managed to
    control lateral and distal extractions, thus allowing for a certain
    degree of predetermination.  
4)  Striking surfaces are oriented so that the core edge is
    perpendicular to the predetermined products.  
5)  The planes of extraction of the products are secant.  
6)  The technique employed is direct percussion with a hard hammer.

Technological analyses of Middle Palaeolithic assemblages have gradually
led to the identification of a variability of modalities within discoid
core knapping ([Bourguignon & Turq 2003](#ref-peresani_chaine_2003);
[Locht 2003](#ref-peresani_industrie_2003); [Terradas
2003](#ref-terradas_discoid_2003); [Locht
2003](#ref-peresani_industrie_2003)). This has resulted in *sensu
stricto* and a *sensu lato* conceptualisations of the discoid knapping
system ([Faivre *et al.* 2017](#ref-faivre_late_2017); [Mourre
2003](#ref-peresani_discoiou_2003); [Thiébaut
2013](#ref-thiebaut_discoid_2013)). The *sensu stricto* hmethod closely
corresponds to the definition established by Boëda
([1993](#ref-boeda_debitage_1993)) described above, for which core edge
flakes and pseudo-Levallois points are the most common products. *The
sensu lato* discoid encompasses a greater range of products (although
centripetal flakes are more common) as a result of higher variability in
the organisation of percussion and exploitation surfaces ([Terradas
2003](#ref-terradas_discoid_2003)).

One of the variants of the *sensu lato* discoid conceptualisation
resembles the Levallois knapping strategy (Figure 1). Several common
characteristics have been defined for this method:

1)  The core volume is conceived as two hierarchical asymmetric
    surfaces: the percussion surface and the exploitation surface (this
    feature is shared with the Levallois).  
2)  Preparation of the percussion surface is absent or partial, without
    encompassing the complete periphery of the core. This may be because
    the characteristics of the raw material present an adequate
    morphology or because it requires minimal preparation.  
3)  Despite the hierarchical nature of the two surfaces, flakes detached
    from the debitage surface present a secant relationship towards the
    plane of intersection. Soriano and Villa
    ([2017](#ref-soriano_early_2017)) point out that Levallois products
    usually present an external platform angle (EPA) of between 80º and
    85º, while products from non-Levallois hierarchical methods present
    an EPA relationship of between 70º and 85º. However, this
    relationship can change over the course of the core’s reduction with
    the final flakes being sub-parallel to the plane of fracture
    ([Slimak 1998](#ref-slimak_variabilite_1998)).  
4)  Products from the hierarchical discoid method tend to be symmetrical
    towards the knapping direction and thin, and the ventral and dorsal
    surfaces present a subparallel relationship. Again, these are common
    traits in Levallois products as well.

![Schematic representation of the knapping methods, surfaces and
platform preparation](Article%20Figures/Variability%20L%20D%20HD.png)

Strategies evidenced at several sites fit into the discoid knapping
variation described above, and its resemblance to the Levallois has been
previously noted in several Middle and early Middle Palaeolithic
assemblages ([Casanova i Martí *et al.*
2009](#ref-casanova_i_marti_strategies_2009);
[2014](#ref-casanova_debitage_2014); [Jaubert
1993](#ref-jaubert_gisement_1993); [Peresani
1998](#ref-peresani_variabilite_1998); [Slimak
1998](#ref-slimak_variabilite_1998); [2003](#ref-peresani_les_2003);
[Soriano & Villa 2017](#ref-soriano_early_2017)). However, it is
important to consider that a variety of different terms have been
employed due to the broad geographical and chronological span of the
method. For Middle Palaeolithic sites, the identification of this method
usually focuses on its shared features with the Levallois and discoid
methods and thus, its intermediate nature.

Jaubert ([1993](#ref-jaubert_gisement_1993)), at Mauran, noted the
hierarchical nature of the production system and its resemblance to
exhausted recurrent centripetal Levallois cores. However, he pointed out
that the secant planes of detachment were not as parallel as in the
Levallois. Slimak ([1998](#ref-slimak_variabilite_1998);
[2003](#ref-peresani_les_2003)), at Champ Grand, also noted the
similarities of residual cores with recurrent centripetal Levallois
debitage. At Estret de Tragó, Casanova i Martí et al.
([2009](#ref-casanova_i_marti_strategies_2009);
[2014](#ref-casanova_debitage_2014))) noted the presence of products and
knapping methods which shared features of the Levallois and discoid
methods, and proposed including the hierarchical discoid and Levallois
recurrent centripetal strategies within a single hierarchical bifacial
centripetal class. Peresani ([1998](#ref-peresani_variabilite_1998)) at
Fumane cave, documented the presence of debitage products with features
(reduced thickness, debitage angle, and centripetal organisation of
scars also subparallel to the ventral surface) which would correspond to
parallel-plane debitage. Baena et al.,
([2005](#ref-montes_barquin_paleoecologiy_2005)) indicated the presence
of the hierarchical discoid method throughout the Esquilleu cave
sequence as a secondary and primary knapping method.

![Distribution of sites referenced in the text base map obtained from:
<https://maps-for-free.com/>)](Article%20Figures/Mapa.png)

As mentioned earlier, for Middle Palaeolithic sites, the identity of
this knapping method is focused on its intermediate nature, as something
between the discoid method and the recurrent centripetal Levallois.
However, at early Middle Palaeolithic sites, the identification of this
method usually focuses on its shared features with the Levallois, as a
method that preceded the gradual emergence of the Levallois. For
example, Carmignani *et al.*
([2017](#ref-carmignani_technological_2017)) used the term “centripetal
with parallel planes”, noting the resemblance of some features to those
of the Levallois at the sites of Payre and Bau de l’Aubesier. Soriano &
Villa ([2017](#ref-soriano_early_2017)) at Guado San Nicola, used the
term “non-Levallois debitage with hierarchised surfaces”, noting its
similarity to the Levallois, but also its distinctiveness, due to the
absence of preparation and management of convexities and the lack of
platform preparation. For Cuesta de la Bajada Santonja *et al.*
([2016](#ref-santonja_coexistence_2016)) differentiate between Levallois
cores and cores of centripetal character with preferential surfaces
(which are simply referred to as centripetal). Lombera-Hermida *et al.*
([2020](#ref-de_lombera-hermida_dawn_2020)) record the presence of
“predetermined hierarchical centripetal” cores in different raw
materials in TD10.1 at Atapuerca, and note the differences to and
coexistence with classical discoid and Levallois knapping methods. The
use of terms alluding to the hierarchical and centripetal nature of this
method is not limited to European sites; the term “hierarchical bifacial
centripetal” was used to refer to the Oldowan industries of Peninj
([Torre *et al.* 2003](#ref-de_la_torre_oldowan_2003)).

The technological criteria for identifying production systems are
clearly visible on cores. However, a high degree of uncertainty remains
when examining flakes, as the technological criteria are less evident or
absent ([Hovers 2009](#ref-hovers_lithic_2009)). Another underlying
cause is the fluid and continuous nature of lithic knapping and
reduction which can blur differences between apparently clear-cut
methods. Additionally, variations can result from adaptations to raw
materials (different knapping methods applied to different raw materials
in the same archaeological level), the initial morphology of the raw
material, the knappers expertise and stage in the learning process
and/or circumstantial events and restrictions. This adds up to an
absence of discrete categories that are blurred by the underlying
existence of a wide variety of lithic expressions. The attribution of
flakes to a knapping method tends to be based on observed features
compared with experimental collections, the context given from the
knapping methods observed in the cores of the assemblage (although cores
in an assemblage do not necessarily represent all knapping methods),
and, importantly, the experience of the analyst. ([Hovers
2009](#ref-hovers_lithic_2009); [Perpère
1986](#ref-perpere_apport_1986); [Bisson
2000](#ref-bisson_nineteenth_2000)) Perpère
([1986](#ref-perpere_apport_1986); [1989](#ref-perpere_les_1989)) have
illustrated that using a dual classification category of Levallois or
non-Levallois results in 30% disagreement among researchers. However, it
is important to note that Perpère’s work
([1986](#ref-perpere_apport_1986); [1989](#ref-perpere_les_1989))
anticipates Boëda’s volumetric and technological criteria (Boëda
([1994](#ref-boeda_concept_1994)); Boëda
([1995b](#ref-dibble_levallois:_1995)); Boëda *et al.*
([1990](#ref-boeda_identification_1990))) which have contributed to
decreasing the degree of disagreement in the identification of the
Levallois. Another example of classification discrepancy comes from the
type counts conducted by Dibble and Tuffreau at the Biache Saint-Bass
site, in which Levallois flakes represented 46.08% of the assemblage in
one list and 27.29% in the other ([Dibble
1995](#ref-dibble_biache_1995)).

Thus, a strong argument can be made for the difficulty of attributing
knapping methods to flakes. This difficulty increases due to the
existence of intermediate methods such as the hierarchical discoid,
whose technological characteristics fall between the *sensu stricto*
discoid and the Levallois. This work uses products experimentally
knapped using the Levallois, discoid, and hierarchical discoid methods
and a machine learning approach to address this problem. Our results
provide insight into the classification accuracy for each knapping
method, variable importance, and the directions of confusion between
methods.

### 1.2 Introduction: loading packages and data

The following lines of code load packages employed for the development
of the present study. Packages employed are: tidyverse ([Wickham *et
al.* 2019](#ref-wickham_welcome_2019)), caret ([Kuhn
2008](#ref-kuhn_building_2008)) and pROC ([Robin *et al.*
2011](#ref-robin_proc_2011)).

Please note that all data necessary for the development of the present
study along with the original Machine Learning models is freely
available at the corresponding repository. This script loads an *.RData*
file which contains a tibble with clean data and established factors.
Additionally a *.csv* file containing the same data is available.

The following line of code loads the above mentioned packages.

``` r
# Load libraries
library(tidyverse); library(caret); library(pROC)
```

The following lines of code load and shows the *.RData* file containing
the data employed for the analysis.

``` r
# Load the data
load("Data/Data.RData")

# Print first ten rows and first ten columns
print(ML_Data[1:10, 1:10])
```

    ## # A tibble: 10 × 10
    ##    Artifact_ID Core       Class Knapp…¹ Frag_…² Compl…³ Length Width Lamin…⁴ MeanT…⁵
    ##    <chr>       <chr>      <fct> <chr>   <chr>   <chr>    <dbl> <dbl>   <dbl>   <dbl>
    ##  1 Disc_08_01  Discoid_08 D     Full P… C       Y         40.4  31.4   1.29     4.67
    ##  2 Disc_08_02  Discoid_08 D     Full P… C       Y         42.2  41.6   1.01    10.7 
    ##  3 Disc_08_03  Discoid_08 D     Full P… C       Y         28.9  38.5   0.751    9.17
    ##  4 Disc_08_04  Discoid_08 D     Full P… C       Y         58.6  39.4   1.49    12.0 
    ##  5 Disc_08_05  Discoid_08 D     Full P… C       Y         41    35.1   1.17    11.3 
    ##  6 Disc_08_06  Discoid_08 D     Full P… C       Y         40.2  28     1.44    11.9 
    ##  7 Disc_08_07  Discoid_08 D     Full P… C       Y         36.8  30.7   1.20     8.4 
    ##  8 Disc_08_08  Discoid_08 D     Full P… C       Y         41.7  28.4   1.47     6.93
    ##  9 Disc_08_09  Discoid_08 D     Full P… C       Y         46.7  27.8   1.68     6.67
    ## 10 Disc_08_10  Discoid_08 D     Full P… C       Y         49.2  23.1   2.13     7.73
    ## # … with abbreviated variable names ¹​Knapping_Phase, ²​Frag_Cat, ³​Complete,
    ## #   ⁴​Laminar_Index, ⁵​MeanThick

``` r
# Print first ten rows and last 5 columns
print(ML_Data[1:10, ncol(ML_Data)-5:ncol(ML_Data)])
```

    ## # A tibble: 10 × 32
    ##    Flake_Type Trans…¹ Termi…² Long_…³ No_Sc…⁴ Corte…⁵ Cortex Plat_…⁶ Plat_…⁷ Flake…⁸
    ##    <chr>      <chr>   <chr>     <dbl>   <dbl>   <dbl>  <dbl> <chr>   <chr>     <dbl>
    ##  1 Backed Fl… Trapez… Feather       0       2       5      5 L       RT       165.  
    ##  2 Flake      Triang… Feather       0       3       5      5 L       CX         5.56
    ##  3 Flake      Trapez… Feather       0       3       5      5 D       BF         5.28
    ##  4 Flake      Triang… Feather       0       4       5      5 L       CX        69.8 
    ##  5 Backed Fl… Triang… Feather       0       3       5      5 L       RT        23.7 
    ##  6 Backed Fl… Triang… Feather       0       3       5      5 L       RT        29.1 
    ##  7 Backed Fl… Triang… Feather       0       2       5      5 L       RT        32.2 
    ##  8 Flake      Triang… Feather       2       2       2      4 L       CC        10.8 
    ##  9 Backed Fl… Triang… Feather       0       2       5      5 L       CX        20.1 
    ## 10 Flake      Triang… Feather       0       3       5      5 L       RT        22.9 
    ## # … with 22 more variables: Plat_Width <dbl>, Plat_Depth <dbl>, Surface.Plat <dbl>,
    ## #   Curvature <dbl>, Weight <dbl>, CVThick <dbl>, SDThick <dbl>,
    ## #   Angle_Lat_Marg <dbl>, Surf_Thick <dbl>, Surf_Area <dbl>, CarenIndex <dbl>,
    ## #   Max_Thick <dbl>, MeanThick <dbl>, Laminar_Index <dbl>, Width <dbl>,
    ## #   Length <dbl>, Complete <chr>, Frag_Cat <chr>, Knapping_Phase <chr>,
    ## #   Class <fct>, Core <chr>, Artifact_ID <chr>, and abbreviated variable names
    ## #   ¹​Trans_Section, ²​Termination_type, ³​Long_Ridges, ⁴​No_Scars, ⁵​Cortex_Loc, …

## 2. Methods

An attribute analysis was performed on an experimental assemblage of
flakes detached by means of the Levallois, discoid and hierarchical
discoid reduction sequences. Supervised machine learning models were
trained on the resulting dataset to identify the knapping method by
which each flake was detached.

### 2.1 Experimental assemblage

The experimental assemblage consists of 222 experimentally knapped
products resulting from Levallois, discoid and hierarchical discoid
reduction sequences. It was knapped by two of the authors (JB and GBP),
one of the whom (JB) is considered a high-level expert, while the second
(GBP) is considered an intermediate-high knapper. The Levallois ([Boëda
1993](#ref-boeda_debitage_1993); [1994](#ref-boeda_concept_1994);
[1995b](#ref-dibble_levallois:_1995); [Boëda *et al.*
1990](#ref-boeda_identification_1990)) products belonged to the
preferential and recurrent centripetal modalities. The hierarchical
discoid cores were knapped in accordance with previous technological
descriptions, with no platform preparation, with centripetal scar
direction (although some opportunistic preferential flakes were
obtained), and without deliberate management of convexities. The
discoid. The discoid ([Boëda 1993](#ref-boeda_debitage_1993); [Thiébaut
2013](#ref-thiebaut_discoid_2013); [Terradas
2003](#ref-terradas_discoid_2003)) products belonged to the *sensu
stricto* conceptualisation in which both surfaces are bifacially
knapped. With the Levallois and hierarchical discoid methods, only
products from the debitage surface were included (flakes detached from
the percussion surface were excluded from analysis). Because discoid
knapping alternates the role of the percussion and debitage surfaces,
all products were included. In all three cases, products from all stages
of reduction were included (decortication, management of convexities,
full production). To be sure of the surface to which each flake belonged
and the completeness of each sequence, products were separated
accordingly during the knapping sequence and, when that was not
possible, cores and flakes were refitted. Only complete products were
included, and all of the knapping sequences were carried out on
different types of flint.

![Experimental cores from which flakes included in the present study
were detached. Their technological defining features are
outlined)](Article%20Figures/Three%20methods.png)

![Sample of experimental materials included in this study. 1-5): flakes
from Levallois preferential and recurrent centripetal reduction
sequences; 6-9) flakes from discoidal reduction sequences; 10-12) flakes
from Hierarchical Discoid reduction sequences. (Photographs by M. D.
Guillén)](Article%20Figures/Experimental%20materials.jpg)

As previously noticed ([Eren *et al.* 2008](#ref-eren_are_2008)), the
discoid system was the most productive, generating the highest number of
flakes with the lowest number of cores. The flake counts for the
Levallois and hierarchical discoid methods were similar per core and
lower than those from the discoid cores. This was expected since only
flakes from the production surface were included. It is important to
note that this resulted in a very well-balanced dataset in which the sum
of the products from each of the three classes was close to 33.33%. The
distribution of the amount of cortex was similar across the knapping
methods studied. In all cases, the sum of non-cortical flakes and flakes
with residual cortex were similarly distributed among the three knapping
strategies and made up the majority of flakes (near 60% in all three
categories). A visual exploratory analysis of the assemblage using a
scatter plot with Bagolini’s categories ([Bagolini
1968](#ref-bagolini_ricerche_1968)) showed that most of the flakes fall
into the ‘normal’ and ‘big’ size categories, with hierarchical discoid
flakes being slightly larger than flakes produced by means of discoid or
Levallois reduction sequences. Additionally, most of the flakes from all
three methods fall into the categories of ‘elongated flakes’, ‘normal
flakes’ and ‘wide flakes’ in terms of their length to width ratios.

``` r
# Get number of cores and flakes (and their percentage) per class
ML_Data %>% group_by(Class) %>% 
  summarise(
    Cores = n_distinct(Core),
    Flakes = n(),
    Percent = (Flakes/222)*100)
```

    ## # A tibble: 3 × 4
    ##   Class Cores Flakes Percent
    ##   <fct> <int>  <int>   <dbl>
    ## 1 L         4     73    32.9
    ## 2 D         3     77    34.7
    ## 3 HD        7     72    32.4

``` r
# Cortex per class
ML_Data %>%
  group_by(Class, Cortex) %>% 
  summarise(N = n()) %>% 
  mutate(Percentage = (N/sum(N))*100) %>% 
  
  ggplot(aes(Class, Percentage, fill = factor(Cortex))) +
  geom_bar(stat = "identity") +
  ylab("Percentage of flakes") +
  ggsci::scale_fill_d3(name = "Amount of cortex", 
                       labels = c("100%", "<100% — >50%", "50% — >10%", "10% — >0%", "0%" )) +
  scale_x_discrete(labels = c("Levallois", "Discoid", "Hierar. Discoid")) +
  
  geom_text(aes(label = (Percentage) %>% round(2)),
            position = position_stack(0.5)) +
  theme_classic() +
  guides(fill = guide_legend(title.position = "top", nrow = 1)) +
  theme(
    axis.text = element_text(color = "black"),
    axis.title.x = element_blank(),
    legend.position = "bottom",
    legend.title = element_text(size = 10, color = "black"),
    legend.text = element_text(size = 9, color = "black"))
```

    ## `summarise()` has grouped output by 'Class'. You can override using the `.groups`
    ## argument.

![](H:\02CAMP~1\03ARTI~1\00GITH~1\2022~1.04I\IN-BET~1\Report\LIES-I~1/figure-gfm/Cortex%20per%20knapping%20method-1.png)<!-- -->

``` r
# Bagolini scatter plot
ML_Data %>% 
  ggplot(aes(Width, Length), color = Class) +
  geom_segment(x = 40, y = 0, xend = 0, yend = 40, color = "gray48") +
  geom_segment(x = 60, y = 0, xend = 0, yend = 60, color = "gray48") +
  geom_segment(x = 80, y = 0, xend = 0, yend = 80, color = "gray48") +
  
  geom_segment(x = 0, y = 0, xend = 115, yend = 115, color = "gray48") +
  
  geom_segment(x = 0, y = 0, xend = (115/6), yend = 115, color = "gray48") +
  geom_segment(x = 0, y = 0, xend = (115/3), yend = 115, color = "gray48") +
  geom_segment(x = 0, y = 0, xend = (115/2), yend = 115, color = "gray48") +
  geom_segment(x = 0, y = 0, xend = (115/1.5), yend = 115, color = "gray48") +
  geom_segment(x = 0, y = 0, xend = (115/0.75), yend = 115, color = "gray48") +
  geom_segment(x = 0, y = 0, xend = (115/0.5), yend = 115, color = "gray48") +
  geom_segment(x = 0, y = 0, xend = 115, yend = (115/2), color = "gray48") +
  
  annotate("text", x = 0, y = 114, adj = 0, 
           label = "Very thin blade", size = 2.5) +
  annotate("text", x = 20, y = 114, adj = 0, 
           label = "Thin blade", size = 2.5) +
  annotate("text", x = 43, y = 114, adj = 0, 
           label = "Blade", size = 2.5) +
  annotate("text", x = 58, y = 114, adj = 0, 
           label = "Elongated flake", size = 2.5) +
  annotate("text", x = 85, y = 114, adj = 0, 
           label = "Flake", size = 2.5) +
  annotate("text", x = 114, y = 100, adj = 0, 
           label = "Wide\nflake", size = 2.5) +
  annotate("text", x = 114, y = 70, adj = 0, 
           label = "Very\nwide\nflake", size = 2.5) +
  annotate("text", x = 114, y = 25, adj = 0, 
           label = "Wider\nflake", size = 2.5) +
  
  annotate("text", x = 20, y = 1, adj = 0, 
           label = "Micro", size = 2.5) +
  annotate("text", x = 47, y = 1, adj = 0, 
           label = "Small", size = 2.5) +
  annotate("text", x = 65, y = 1, adj = 0, 
           label = "Normal", size = 2.5) +
  annotate("text", x = 85, y = 1, adj = 0, 
           label = "Big", size = 2.5) +
  
  geom_point(aes(color = Class), size = 2, alpha = 0.75) +
  scale_x_continuous(breaks = seq(0, 115, 5), lim = c(0, 115)) +
  scale_y_continuous(breaks = seq(0, 115, 5), lim = c(0, 115)) +
  ylab("Length (mm)") +
  xlab("Width (mm)") +
  theme_light() +
  ggsci::scale_color_aaas(labels = c('Levallois', 'Discoid',
                                     'Hierarchical Discoid')) +
  labs(color = "Class") +
  stat_ellipse(aes(color = Class)) +
  guides(color = guide_legend(nrow = 1, title.position = "left")) +
  theme(axis.title = element_text(size = 9, color = "black", face = "bold"),
        axis.text = element_text(size = 7.5, color = "black"),
        legend.position = "bottom") +
  coord_fixed() 
```

![](H:\02CAMP~1\03ARTI~1\00GITH~1\2022~1.04I\IN-BET~1\Report\LIES-I~1/figure-gfm/Bagolini%20scatter%20plot-1.png)<!-- -->

### 2.2 Attribute analysis

Attribute analyses were performed for each flake. The variables and
indexes listed below were recorded and calculated. Measurements were
recorded in mm. Some of the measurements recorded were used in the
calculation of additional variables. For example, angle height and
maximum flake length were used to calculate flake curvature; width
measurements (at 25% and 75% length) were used to calculate the angle of
the lateral margins; and thickness measurements were used to calculate
the average and standard deviation of thickness. Other variables, such
as technological length and width (or the above-mentioned width
measurements) were also used to calculate ratios (the elongation and
carination index), but their use would introduce a size dependence
factor in the training of the models. Therefore, the variables employed
in the machine learning model training are underlined. The variables
considered were:

- Degree of fracture ([Hiscock 2002](#ref-hiscock_quantifying_2002)):
  complete, proximal fragment, mesial fragment, distal fragment,
  marginal fragment and longitudinal fragment. Only complete flakes were
  further analysed.  
- Technological length: measured along the axis perpendicular to the
  striking platform ([Andrefsky 2005](#ref-barker_lithics_2005)).  
- Technological width: measured along the axis perpendicular to the
  technological width ([Andrefsky 2005](#ref-barker_lithics_2005)).  
- Width measured at the 25% length of the flake ([Eren & Lycett
  2012](#ref-eren_why_2012)).  
- Width at the 75% length of the flake ([Eren & Lycett
  2012](#ref-eren_why_2012)).  
- Thickness at the 25% length of the flake ([Eren & Lycett
  2012](#ref-eren_why_2012)).  
- Thickness at the 50% length of the flake ([Eren & Lycett
  2012](#ref-eren_why_2012)).  
- Thickness at the 75% length of the flake ([Eren & Lycett
  2012](#ref-eren_why_2012)).  
- Maximum flake length.  
- **Maximum thickness**  
- **Average thickness**: the average from the three previous measures of
  thickness.  
- **Standard deviation of thickness**.  
- Angle height ([Andrefsky 2005](#ref-barker_lithics_2005)): the height
  of the flake including its curvature.  
- Geometric morphology of the platform as per Muller & Clarkson
  ([2016](#ref-muller_new_2016)): rectangle, triangle, rhombus,
  trapezoid, and ellipse.  
- Measurement “x”, “y” and “z” of the platform according to previous
  geometric morphologies ([Muller & Clarkson
  2016](#ref-muller_new_2016)).  
- **Platform surface**: calculated using previous geometric morphologies
  and measurements of x, y and z as in Muller & Clarkson
  ([2016](#ref-muller_new_2016)).  
- **Platform depth**: which can correspond to the measurement of y or z
  depending on the geometric morphology of the platform.  
- **Platform width**: which can correspond to the measurement of x or y
  depending on the geometric morphology of the platform.

![Left: common measures and attributes taken for the analysis of a
flake. Right: calculation of flake curvature following Andrefsky
([2005](#ref-barker_lithics_2005))](Article%20Figures/Measures.png)

- **Profile of the platform**: absence of platform, concave, straight,
  convex, biangular and *chapeau de gendarme*.  
- **Preparation of the platform**: no platform, cortical, plain,
  dihedral, a pans and prepared (facetted).  
- **External Platform Angle (EPA)** measured in degrees with a manual
  goniometer.  
- **Internal Platform Angle (IPA)** measured in degrees with a manual
  goniometer.  
- **Relative amount of cortex present at the dorsal face**: recorded
  according to its extension on the dorsal surface of the flake
  ([Andrefsky 2005](#ref-barker_lithics_2005)): cortical (100% cortex),
  more than 50% of cortex (excluding cortical flakes), less than 50% of
  cortex (excluding the following categories), residual presence (\<10%
  and excluding non-cortical flakes), and no cortex.  
- **Cortex location**: slightly modified from Marwick
  ([2008](#ref-marwick_what_2008)), with categories being primary
  (dorsal surface completely covered by cortex), crescent (cortex
  located in one of the laterals usually with a crescent shaped form)
  distal (located at the opposite end of the percussion platform),
  central (inner part of the flake), and tertiary (no cortex).  
- **Number of dorsal scars with length more than 5 mm**\*.  
- **Number of longitudinal ridges**: individual ridges starting at the
  platform and reaching the distal part of the flake.  
- **Transversal section**: triangular, right-angled triangle,
  trapezoidal, rectangular trapezoid shape and ovular.  
- **Termination type of the flake**: feather, hinge, step or plunging
  following Cotterell & Kamminga
  ([1987](#ref-cotterell_formation_1987)).

![Geometric morphologies employed to measure platform surface, depth and
width following Muller & Clarkson
([2016](#ref-muller_new_2016))](Article%20Figures/Platform%20Measures.png)

- **Simplified technological category of flakes**: flake, backed flake
  (including core edge flake), and pseudo-Levallois point.  
- Weight in grams (precision of 0.01).  
- **Elongation index**: the quotient of technological length divided by
  technological width ([Laplace 1968](#ref-laplace_recherches_1968)).  
- **Carenated index**: the quotient of length or width (the one with the
  lowest value) divided by the maximum thicknesses ([Laplace
  1968](#ref-laplace_recherches_1968)).  
- **Angle of the lateral margins**: describes the relationship between
  the two lateral edges of a flake. Flakes with expanding edges (wider
  in the distal part) will have negative values, contracting or pointed
  (wider in the proximal part than in the distal part) artefacts will
  have positive values, and rectangular artefacts (similar proximal and
  distal width) will have values near 0 ([Clarkson
  2007](#ref-clarkson_lithics_2007): 37). The angle of the lateral
  margins is calculated by multiplying by two the value of the reverse
  tangent of proximal width minus distal with, and dividing the result
  by two times the maximum length ([Clarkson
  2007](#ref-clarkson_lithics_2007): 38)  
- **Flake curvature**: measured in degrees and calculated as described
  in Andrefsky ([2005](#ref-barker_lithics_2005)). Flakes presenting a
  180º curvature are perfectly straight flakes, while decreasing values
  indicate an increase in curvature.  
- **Surface area of the flake**: the product of flake technological
  width multiplied by its length ([Dibble
  1989](#ref-mellars_implications_1989)).  
- **Ratio of surface area against thickness**: surface area of the flake
  divided by average thickness.  
- **Ratio of surface area against platform surface**: the quotient of
  the surface area divided by platform area.

### 2.3 Machine learning models

The following ten machine learning models were tested for their ability
to differentiate between backed flakes extracted from the two surfaces
of the core using each knapping method:

- **Linear Discriminant Analysis (LDA)**: reduces dimensionality for the
  purpose of maximising the separation between classes while decision
  boundaries divide the predictor range into regions ([Fisher
  1936](#ref-fisher_use_1936); [James *et al.*
  2013](#ref-james_introduction_2013)).  
- **K-nearest neighbor (KNN)**: classifies cases by assigning the class
  of similar known cases. The ‘k’ in KNN refers to the number of cases
  (neighbours) to consider when assigning a class, which must be found
  by testing different values. Given that KNN uses distance metrics to
  compute nearest neighbours and that each variable is in different
  scales, the data must be scaled and centred prior to fitting the model
  ([Cover & Hart 1967](#ref-cover_nearest_1967); [Lantz
  2019](#ref-lantz_machine_2019)).  
- **Logistic Regression**: eessentially adapts continuous regression
  predictions to categorical outcomes ([Cramer
  2004](#ref-cramer_early_2004); [Walker & Duncan
  1967](#ref-walker_estimation_1967)).  
- **Decision tree with C5.0 algorithm**: algorithm: an improvement on
  decision trees for classification ([Quinlan
  1996](#ref-quinlan_improved_1996); [Quinlan
  2014](#ref-quinlan_c4_2014)).  
- **Random Forest**: made of decision trees. Each tree is grown from a
  random sample of the data and variables, allowing for each tree to
  grow differently and to better reflect the complexity of the data
  ([Breiman 2001](#ref-breiman_random_2001)).  
- **Generalized Boosted Model** ([Greenwell *et al.*
  2019](#ref-greenwell_package_2019); [Ridgeway
  2007](#ref-ridgeway_generalized_2007)) implements the gradient boosted
  machine ([Friedman 2001](#ref-friedman_greedy_2001); [Friedman
  2002](#ref-friedman_stochastic_2002)) making it possible to detect
  learning deficiencies and increase model accuracy for a set of random
  forests.  
- **Supported Vector Machines (SVM)**: fit hyperplanes into a
  multidimensional space with the objective of creating homogeneous
  partitions ([Cortes & Vapnik 1995](#ref-cortes_support-vector_1995);
  [Frey & Slate 1991](#ref-frey_letter_1991)). The present study tests
  SVM with linear, radial and polynomial kernels.  
- **Artificial Neural Network (ANN)** with multi-layer perception, it
  uses a series of hidden layers and error backpropagation for model
  training ([Rumelhart *et al.* 1986](#ref-rumelhart_learning_1986)).

### 2.4 Machine learning evaluation

All models were evaluated by means of a 10x50 k-fold cross validation
(10 folds and 50 cycles). Accuracy and area under the curve (AUC) were
used as measurements of overall performance for the selection of the
best model. ‘Accuracy’ measures the model’s correct predictions against
the overall cases provided to the model and can range from 0 to 1. The
accuracy of a random classifier is 1/k (k being the number of classes).
For the present study, the random classifier had an accuracy of 0.33.

The AUC is a measure of performance derived from the receiver operating
characteristic (ROC) curve. The ROC curve is used to evaluate the ratio
of detected true positives while avoiding false positives ([Bradley
1997](#ref-bradley_use_1997); [Spackman
1989](#ref-spackman_signal_1989)). The ROC curve makes it possible to
visually analyse model performance and calculate the AUC, which ranges
from 1 (perfect classifier) to 0.5 (random classifier). The ROC and AUC
are commonly applied in two-class problems and their extension to
multiclass problems is usually done through pairwise analysis. In the
case of the ROC curve, individual curves of each class are plotted using
the previously mentioned “one vs all” approach. The present study tested
10 different models with a three-class classification problem which
would involve a total of 30 different ROC curves (10 per class in each
model). In this paper, we have provided only the three ROC curves of the
best model.

The AUC ranges of values are usually interpreted as follows: 1 to 0.9:
outstanding; 0.9 to 0.8: excellent or good; 0.8 to 0.7: acceptable or
fair; 0.7 to 0.6: poor; and 0.6 to 0.5: no discrimination ([Lantz
2019](#ref-lantz_machine_2019)). When analysing lithic materials, the
use of thresholds to guarantee true positives and avoid false positives
is of special interest. The use of decision thresholds and derived
measures of accuracy (ROC curve and AUC) can be especially useful in
lithic analysis since it is expected that products from initial
reduction stages are morphologically similar, independent of the
knapping method. These products are expected to show a greater mixture
between methods and have lower probability values. The use of thresholds
better indicates the accuracy of a model considering these probability
values.

This study was conducted using an R version 4.1.1 in IDE RStudio version
2021.09.0 ([R. C. Team 2019](#ref-r_core_team_r_2019); [Rs. Team
2019](#ref-rstudio_team_rstudio_2019)). The data and graphs were managed
using the tidyverse v.1.3.2 package ([Wickham *et al.*
2019](#ref-wickham_welcome_2019)). The LDA and KNN were trained with the
MASS (Modern Applied Statistics with S) v.7.3.58.1 package ([Venables &
Ripley 2002](#ref-venables_modern_2002)). The random forest was trained
using the ranger v.0.14.1 package ([Wright & Ziegler
2017](#ref-wright_ranger_2017)). The SVM was trained using the e1071
v.1.7.12 package ([Karatzoglou *et al.*
2006](#ref-karatzoglou_support_2006); [Karatzoglou *et al.*
2004](#ref-karatzoglou_kernlab_2004)). The RSNNS v.0.4.14 (Stuttgart
Neural Network Simulator) package ([Bergmeir & Benítez
2012](#ref-bergmeir_neural_2012)) was used to train the multi-layer ANN
with backpropagation. The k-fold cross validation of all models,
precision metrics, and confusion matrix were obtained using the caret
v.6.0.93 package ([Kuhn 2008](#ref-kuhn_building_2008)). Machine
learning models also provide insights into variable importance for
classification. The caret package was used to extract variable
importance after each k-fold cross validation (see supplementary
information). ROC curves and AUC values are obtained using the package
pROC v.1.18.0 ([Robin *et al.* 2011](#ref-robin_proc_2011)).

#### 2.4.1 Preprocessing for model training

Prior to the training the models it is necessary to remove a series of
variables such as “Artifact_ID”, “Core”, “Complete”, etc. These
variables are employed to ensure the quality of the dataset, but are not
employed in model training.

``` r
# Remove unwanted columns
ML_Data <- ML_Data %>% 
  select(-c(Artifact_ID, Core, Complete, Frag_Cat, Knapping_Phase,
         Length, Width, Weight))

# Select character columns and cortex location
x <- colnames(ML_Data %>% 
                select_if(is.character) %>% 
                select(Plat_Prof:Flake_Type))

x <- append(x, "Cortex_Loc")

# Only one CG platform. Make into convex
ML_Data$Plat_Prof[ML_Data$Plat_Prof == "CG"] <- "CX"

# Dummy coding of qualitatuve variables
ML_Data <- fastDummies::dummy_cols(
  ML_Data, 
  select_columns = c(x),
  remove_first_dummy = TRUE,
  remove_selected_columns = TRUE)
```

#### 2.4.2 Training of the models

The following code sets up 50 cycles of a 10 fold cross validation.
Additionally, the final class probabilities for each case are saved.

``` r
# Set validation
trControl <- trainControl(method  = "repeatedcv",
                          verboseIter = TRUE,
                          number  = 10,
                          repeats = 50,
                          savePredictions = "final",
                          classProbs = TRUE)
```

The following code trains all the above mentioned models.

``` r
# LDA Model
set.seed(123)
LDA_Model <- train(Class ~., 
                   ML_Data,
                   method = "lda",
                   trControl = trControl,
                   preProc = c("center", "scale"),
                   metric = "Accuracy",
                   importance = 'impurity')

# KNN model
set.seed(123)
KNN_Model <- train(Class ~., 
                   ML_Data,
                   method = "knn",
                   preProc = c("center", "scale"),
                   trControl = trControl,
                   tuneGrid   = expand.grid(k = 2:30),
                   metric = "Accuracy")

# Logistic regression
set.seed(123)
Log_Reg <- train(Class ~., 
                 ML_Data,
                 method = "glmnet",
                 family = 'multinom',
                 preProcess = c("center","scale"),
                 trControl = trControl,
                 metric = "Accuracy",
                 importance = 'impurity')

# C5.0 model
set.seed(123)
C50_Mod <- train(Class ~., 
                 ML_Data,
                 method = "C5.0",
                 trControl = trControl,
                 metric = "Accuracy",
                 importance = 'impurity')


# Random Forest 
best_tune <- data.frame(
  mtry = numeric(0),
  Num_Trees = numeric(0),
  Split_Rule = character(0),
  Precision = numeric(0),
  Node.Size = numeric(0))

my_seq <- seq(350, 700, 25)

set.seed(123)
for (x in my_seq){
  
  RF_Model <- train(Class ~., 
                    ML_Data,
                    method = "ranger",
                    trControl = trControl,
                    tuneGrid =
                      expand.grid(.mtry = seq(1, 10, 1),
                                  .min.node.size = seq(1, 6, 1),
                                  .splitrule = c("gini", "extratrees")),
                    metric = "Accuracy",
                    importance = 'impurity')

  Bst_R <- data.frame(
    mtry = RF_Model$bestTune[[1]],
    Num_Trees = x,
    Split_Rule = RF_Model$bestTune[[2]],
    Precision = max(RF_Model$results[[4]]),
    Node.Size = RF_Model$bestTune[[3]]
  )
  
  best_tune <- rbind(best_tune, Bst_R)
  Bst_R <- c()
}

# Best tune 
set.seed(123)
RF_Model <- train(
  frmla,
  PCA_Coord,
  method = "ranger",
  trControl = trControl,
  tuneGrid = expand.grid(
    .mtry = 40,
    .min.node.size = 1,
    .splitrule = "extratrees"),
  num.trees = 550,
  metric = "Accuracy",
  importance = 'impurity')

# GBM
set.seed(123)
Boost_Tree <- train(Class ~., 
                    ML_Data,
                    method = "gbm",
                    trControl = trControl,
                    metric = "Accuracy",
                    tuneGrid = 
                      expand.grid(
                      n.trees = seq(from = 300, to = 700, by = 50),
                      interaction.depth = seq(from = 1, to = 10, length.out = 5),
                      shrinkage = 0.1,
                      n.minobsinnode = as.integer(seq(1, 10, length = 5))))

# SVM linear 
set.seed(123)
SVM_Linear <- train(Class ~., 
                    ML_Data,
                    method = "svmLinear",
                    preProcess = c("center","scale"),
                    trControl = trControl,
                    tuneGrid = expand.grid(C = seq(0.01, 3, length = 20)),
                    metric = "Accuracy",
                    importance = 'impurity')

# SVM Radial 
set.seed(123)
SVM_Radial <- train(Class ~., 
                    ML_Data, 
                    method = "svmRadial",
                    preProcess = c("center","scale"),
                    trControl = trControl,
                    tuneGrid = 
                      expand.grid(C = seq(0.01, 3, length = 20),
                                  sigma = seq(0.0001, 1, length = 20)),
                    metric = "Accuracy",
                    importance = 'impurity')

# SVM Poly 
set.seed(123)
SVM_Poly <- train(Class ~., 
                    ML_Data,
                  method = "svmPoly",
                  preProcess = c("center","scale"),
                  trControl = trControl,
                  metric = "Accuracy",
                  tuneGrid = 
                    expand.grid(C = seq(0.01, 3, length = 15),
                                scale = seq(0.001, 1, length = 15),
                                degree = as.integer(seq(1, 3, 1))),
                  importance = 'impurity')

# ANN
set.seed(123)
mlp_Mod = train(Class ~., 
                ML_Data,
                method = "mlpML", 
                preProc =  c('center', 'scale'),
                trControl = trControl,
                tuneGrid = 
                  expand.grid(
                    layer1 = c(1:8),
                    layer2 = c(0:8),
                    layer3 = c(0:8)))
```

## 3. Data results

All of the models presented a general accuracy of above 0.6 and far
above the random classifier (0.33). The overall model performance
indicated that SVM with polynomial kernel provided the best
classification metrics for both accuracy and AUC. SVM with polynomial
kernel had the best overall accuracy value (0.667) and the best AUC
(0.824), an excellent or good value. The SVM with polynomial kernel
accuracy value was closely followed by the random forest (0.666) and
logistic regression (0.662). The gradient boosting machine model and ANN
presented the lowest accuracy values (0.613 and 0.614, respectively).
The random forest also presented the second highest AUC value (0.816)
followed by SVM with radial kernel (0.815), both values were excellent
or good. Again, ANN and the generalised boosted model presented the
lowest AUC values (0.772 and 0.795 respectively), although both values
can be considered acceptable or fair.

``` r
# Model performance (accuracy and AUC)
data.frame(
  Model = c("LDA", "KNN", "Log. Reg", "C5.0", "Ran. Forest",
            "Boost. Tree", "SVML", "SVMR", "SVMP", "ANN"),
  Accuracy = rbind(
    round(confusionMatrix(LDA_Model$pred$obs, LDA_Model$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(KNN_Model$pred$obs, KNN_Model$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(Log_Reg$pred$obs, Log_Reg$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(C50_Mod$pred$obs, C50_Mod$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(RF_Final$pred$obs, RF_Final$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(Boost_Tree$pred$obs, Boost_Tree$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(SVM_Linear$pred$obs, SVM_Linear$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(SVM_Radial$pred$obs, SVM_Radial$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(SVM_Poly$pred$obs, SVM_Poly$pred$pred)$overall['Accuracy'], 3),
    round(confusionMatrix(mlp_Mod$pred$obs, mlp_Mod$pred$pred)$overall['Accuracy'], 3)),
  AUC = rbind(
    round(pROC::multiclass.roc(LDA_Model$pred$obs, LDA_Model$pred[,4:6])$auc[[1]],3),
    round(pROC::multiclass.roc(KNN_Model$pred$obs, KNN_Model$pred[,4:6])$auc[[1]],3),
    round(pROC::multiclass.roc(Log_Reg$pred$obs, Log_Reg$pred[,6:8])$auc[[1]],3),
    round(pROC::multiclass.roc(C50_Mod$pred$obs, C50_Mod$pred[,7:9])$auc[[1]],3),
    round(pROC::multiclass.roc(RF_Final$pred$obs, RF_Final$pred[,6:8])$auc[[1]],3),
    round(pROC::multiclass.roc(Boost_Tree$pred$obs, Boost_Tree$pred[,8:10])$auc[[1]],3),
    round(pROC::multiclass.roc(SVM_Linear$pred$obs, SVM_Linear$pred[,4:6])$auc[[1]],3),
    round(pROC::multiclass.roc(SVM_Radial$pred$obs, SVM_Radial$pred[,5:7])$auc[[1]],3),
    round(pROC::multiclass.roc(SVM_Poly$pred$obs, SVM_Poly$pred[,6:8])$auc[[1]],3),
    round(pROC::multiclass.roc(mlp_Mod$pred$obs, mlp_Mod$pred[,6:8])$auc[[1]],3)
  ))
```

    ##          Model Accuracy   AUC
    ## 1          LDA    0.629 0.807
    ## 2          KNN    0.655 0.806
    ## 3     Log. Reg    0.662 0.813
    ## 4         C5.0    0.625 0.799
    ## 5  Ran. Forest    0.666 0.816
    ## 6  Boost. Tree    0.613 0.795
    ## 7         SVML    0.637 0.805
    ## 8         SVMR    0.655 0.815
    ## 9         SVMP    0.667 0.824
    ## 10         ANN    0.614 0.772

``` r
# Performance metrics of SVMP
SVMP.Performance <- data.frame(confusionMatrix(SVM_Poly$pred$pred, SVM_Poly$pred$obs)[[4]])
SVMP.Performance %>% 
  select(Sensitivity, Specificity, Precision, F1, Prevalence, Balanced.Accuracy) %>% 
  mutate(Class = c("Levallois", "Discoidal", "Hierar. Disc."))
```

    ##           Sensitivity Specificity Precision        F1 Prevalence Balanced.Accuracy
    ## Class: L    0.7827397   0.9115436 0.8125711 0.7973765  0.3288288         0.8471417
    ## Class: D    0.6561039   0.8026207 0.6383624 0.6471116  0.3468468         0.7293623
    ## Class: HD   0.5616667   0.7860000 0.5574855 0.5595683  0.3243243         0.6738333
    ##                   Class
    ## Class: L      Levallois
    ## Class: D      Discoidal
    ## Class: HD Hierar. Disc.

Classification metrics per class, confusion matrix and ROC along with
AUCs of SVM with polynomial kernel exhibited marked differences between
knapping methods (Figure 9). In all cases, classification metric values
were higher than the no-information ratio (prevalence) of each class
(0.329 for Levallois, 0.347 for discoid and 0.324 for hierarchical
discoid). In general, SVM with polynomial kernel best identified
products obtained from Levallois preferential and recurrent centripetal
reduction sequences. This resulted in a notably high value of
sensitivity (0.783) along with a high value of general performance (F1
value of 0.797), and an outstanding AUC value (0.91). While it was
slightly more common to erroneously identify Levallois products as
hierarchical discoid products (12.44%) than to erroneously identify them
as discoid products (9.29%), both values were notably low.

``` r
# ROC and AUC of each model
MC.ROC <- SVM_Poly$pred %>% 
  select(pred, obs, L, D, HD) %>% 
  mutate(
    LvsAll = case_when(obs == "D" ~ "Rest", 
                       obs == "HD" ~ "Rest", 
                       obs == "L" ~ "L"),
    DvsAll = case_when(obs == "D" ~ "D", 
                       obs == "HD" ~ "Rest", 
                       obs == "L" ~ "Rest"),
    HDvsAll = case_when(obs == "D" ~ "Rest", 
                       obs == "HD" ~ "HD", 
                       obs == "L" ~ "Rest"))

x <- roc(MC.ROC$LvsAll, MC.ROC$L)
SVMP.ROCs <- data.frame(
  Sensi = x$sensitivities,
  Speci = x$specificities,
  Class = "Levallois")

x <- roc(MC.ROC$DvsAll, MC.ROC$D)
temp <- data.frame(
  Sensi = x$sensitivities,
  Speci = x$specificities,
  Class = "Discoidal")
SVMP.ROCs <- rbind(SVMP.ROCs, temp)

x <- roc(MC.ROC$HDvsAll, MC.ROC$HD)
temp <- data.frame(
  Sensi = x$sensitivities,
  Speci = x$specificities,
  Class = "Hierar. Disc.")
SVMP.ROCs <- rbind(SVMP.ROCs, temp)

#Set factors (otherwise legend will not correspond)
SVMP.ROCs$Class <- factor(SVMP.ROCs$Class, 
                         levels = c(
                           "Levallois", 
                           "Discoidal",
                           "Hierar. Disc."))


# Plot the three ROC's and AUC's in legend
SVMP.ROCs %>% 
  ggplot(aes(Speci, Sensi, color = Class)) +
  geom_line(size = 1.01) +
  scale_x_continuous(trans = "reverse") +
  ggsci::scale_color_aaas(
    labels = c(paste0("Levallois ", "(AUC = ", round(auc(MC.ROC$LvsAll, MC.ROC$L)[[1]],2), ")"),
               paste0("Discoidal ", "(AUC = ", round(auc(MC.ROC$DvsAll, MC.ROC$D)[[1]],2), ")"),
               paste0("Hierar. Disc. ", "(AUC = ", round(auc(MC.ROC$HDvsAll, MC.ROC$HD)[[1]], 2), ")"))) +
  coord_fixed() +
  theme_light() +
  xlab("Specificities") +
  ylab("Sensitivities") +
  geom_abline(intercept = 1, slope = 1) +
  theme(
    legend.title = element_text(color = "black", face = "bold", size = 9),
    legend.text = element_text(color = "black", size = 8),  
    axis.text = element_text(color = "black", size = 10),
    axis.title = element_text(color = "black", size = 11, face = "bold"))
```

![](H:\02CAMP~1\03ARTI~1\00GITH~1\2022~1.04I\IN-BET~1\Report\LIES-I~1/figure-gfm/ROC%20and%20AUC%20of%20each%20class-1.png)<!-- -->

``` r
## Confusion matrix of SVMP 
# Obtain from caret and reshape
SVM_Poly.Confx <- confusionMatrix(SVM_Poly)$table
SVM_Poly.Confx <- reshape2::melt(SVM_Poly.Confx)

# Normalize the data
SVM_Poly.Confx <- SVM_Poly.Confx %>% mutate(
  value = case_when(
    Reference == "L" ~ (value/sum(confusionMatrix(SVM_Poly)$table[1:3]))*100,
    Reference == "D" ~ (value/sum(confusionMatrix(SVM_Poly)$table[4:6])*100),
    Reference == "HD" ~ (value/sum(confusionMatrix(SVM_Poly)$table[7:9])*100),
  )
)

# Set factors and labels of reference and prediction
SVM_Poly.Confx$Prediction <- factor(SVM_Poly.Confx$Prediction, 
                                    levels = c("HD", "D", "L"),
                                    labels =  c(
                                      "Hierar. Disc.", "Discoid", "Levallois"))
SVM_Poly.Confx$Reference <- factor(SVM_Poly.Confx$Reference, 
                                   levels = c("L", "D", "HD"),
                                   labels = c(
                                     "Levallois", "Discoid", "Hierar. Disc."))

# Plot confusion matrix
SVM_Poly.Confx %>% 
  ggplot(aes(Reference, Prediction, fill = value)) + 
  geom_tile(alpha = 0.75) +
  geom_text(aes(label = round(value, 2)), size = 3) +
  scale_fill_gradient(low = "white", high = "blue")  +
  scale_x_discrete(position = "top") +
  theme_bw() +
  coord_fixed() +
  theme(legend.position = "none",
        axis.title = element_text(size = 8, color = "black", face = "bold"),
        axis.text = element_text(size = 7.5, color = "black"),
        title = element_text(size = 8, color = "black", face = "bold"))
```

![](H:\02CAMP~1\03ARTI~1\00GITH~1\2022~1.04I\IN-BET~1\Report\LIES-I~1/figure-gfm/Confusion%20Matrix-1.png)<!-- -->

Products from discoid bifacial reduction sequences were the second best
identified by the SVM with polynomial kernel. While a notable confusion
occurred between discoid and hierarchical discoid products, the F1
general performance value (0.647) was still quite high, and the AUC
value was found to be excellent or good (0.82). The confusion matrix
(Figure 7) shows that the erroneous identification of products from
discoid reduction sequences is due to confusion with products resulting
from the hierarchical discoid method (29.9%), while their
misclassification as Levallois is residual (4.49%). Hierarchical discoid
products yielded the lowest values of classification metrics. The
general performance metric F1 had a value of 0.56 and relatively low
values of sensitivity (0.562) and precision (0.557). Despite these
relatively low values, the AUC for the hierarchical discoid products was
still acceptable or fair (0.73), which indicates that the application of
decision thresholds can support and improve the identification of
products from hierarchical discoid reduction sequences. These low
classification metrics were clearly related to the SVM with polynomial
kernel mistaking hierarchical discoid products as discoid products,
along with a residual although notable confusion with Levallois products
(13.5%).

The importance of the discriminating variables differed for each
knapping method. Figure 10 presents the discriminating variables whose
importance values exceeded 50 for each knapping method. For Levallois
products, the most important discriminating variables related to ratios
of flake size to thickness (the carination index was the most important,
and the flake surface to thickness ratio was also considered highly
important), thickness (mean and maximum thickness), and platform angle
(with IPA having a slightly higher value than EPA). Qualitative
attributes such as type of platform were also considered important for
the discrimination of Levallois products. Plain and prepared platforms
had importance values of 72.19 and 71.19, respectively. The selection of
variables for the identification of discoid products was similar to
those for Levallois, although with differences in the order of
importance. As with the Levallois, the carination index was considered
the most important variable, while both measures of platform angle (IPA
and EPA) were considered the second and third most important variables.
Similar to the Levallois products, measures of thickness and platform
type were also considered important in the identification of discoid
products.

Discriminating hierarchical discoid products proved to be more complex,
with none of the variables reaching the maximum value. The SVM with
polynomial kernel model considered thickness measurements (maximum and
mean thickness) along with platform angle measurements (EPA and IPA) as
the most important variables for the discrimination of hierarchical
discoid products. The carination index was considered a much less
important measurement (value of 77.18) compared to its importance for
the identification of Levallois and discoid products.

An additional variable which ranked slightly above the importance value
threshold is the standard deviation of thickness. Standard deviation of
thickness presented importance values of 57.25 for Levallois and discoid
products, and 55.01 for hierarchical discoid products. Thus, although it
is not a key variable for discrimination, differences can be observed in
the thickness variations between products of the different knapping
methods. For both Levallois and discoid products, the IPA was a slightly
better discriminatory variable than EPA. For hierarchical discoid
products, the EPA had a slightly higher (81.31) discriminatory value
than IPA (81.17). This indicates that IPA tends to be a better
discriminating variable for the identification of knapping methods.

``` r
## Variable importance
# Data frame of PC importance
tibble(
  Variable = rownames(varImp(SVM_Poly, sale = TRUE)$importance),
  Importance.L = varImp(SVM_Poly, sale = TRUE)$importance[, 1],
  Importance.D = varImp(SVM_Poly, sale = TRUE)$importance[, 2],
  Importance.HD = varImp(SVM_Poly, sale = TRUE)$importance[, 3]) %>% 
  
  mutate(Variable = c(
    "Elong. Index", "Mean Thick.", "Max. Thick.", "Caren. Index", "Surf. Area",
    "Surf to Thick", "Angle Lat. Marg.", "Thick. SD", "CV Thick.", "Curvature",
    "Plat. Surface", "Plat. Depth", "Plat. Width", "Flake Surf. to Plat",
    "Cortex", "No of Scars", "No of Long Ridges", "EPA", "IPA", "X to W ratio", 
    "IE to PS", "Surf. to Proximal Width", "CC Platform", "Cx Platform",
    "Straight Plat.", "Dihed. Plat.", "Plain Platform", "Prep. Plat.",   
    "Hinge Ter.", "Plunging Term.", "Trap. Section","Trap. Asy. Section",
    "Tri. Sect.", "Trian. Assym", "Flake", "pL-p", "Crescent Cortex",
    "Distal Cortex", "Center Cortex", "0% Cortex")) %>% 
  
  pivot_longer(cols = Importance.L:Importance.HD,
               names_to = "Importance.Per.Class",
               values_to = "Values") %>% 
  filter(Values > 50) %>% 
  
  ggplot(aes(Variable, Values, fill = Values)) +
  geom_bar(stat= "identity", position = "dodge") +
  theme_light() +
  facet_wrap(~ factor(Importance.Per.Class, 
                       levels = c("Importance.L", 
                                  "Importance.D", 
                                  "Importance.HD"),
                      labels = c(
                        "Levallois",
                        "Discoidal", 
                        "Hierar. Disc.")),
             scale = "free", 
             ncol = 3) +
  scale_fill_gradient(low = "red", high = "blue") +
  guides(fill = "none") +
  xlab(NULL) +
  coord_flip() +
  geom_text(aes(label = round(Values, 2)), 
            position = position_stack(vjust = 0.5), size = 2) +
  theme(
    axis.text.y = element_text(color = "black", size = 7),
    axis.text.x = element_text(color = "black", size = 7, angle = 0),
    axis.title.x = element_text(color = "black", size = 9),
    axis.title.y = element_text(color = "black", size = 9),
    strip.text = element_text(color = "black", face = "bold", size = 9),
    strip.background = element_rect(fill = "white", colour = "black", size = 1))
```

![](H:\02CAMP~1\03ARTI~1\00GITH~1\2022~1.04I\IN-BET~1\Report\LIES-I~1/figure-gfm/Variable%20importance-1.png)<!-- -->

The analysis of class probabilities based on the reduction sequence and
amount of cortex revealed a series of tendencies. Products detached by
means of Levallois reduction sequences had the highest mean probability
(0.657) of belonging to their true class, independent of cortex amount.
This high average can be clearly related to the F1 and AUC measurements.
Products detached using Levallois reduction sequences showed a clear
tendency: as the cortex amount decreased, the probability of correctly
being identified as Levallois increased. This resulted in increased
average values of correctly being identified as Levallois: products with
100% cortical flakes had an average of 0.558, \> 50% cortex an average
of 0.572, \< 50% cortex an average of 0.717 and flakes with residual
cortex an average of 0.726. A decrease in the average value (0.686) was
observed in the case of flakes with no cortex. This decrease in the mean
value can be attributed to the fact that this was the most abundant
category and included a long tail in the distribution of values as a
result of flakes with low probability values of belonging to Levallois
reduction sequences. Nevertheless, most of the Levallois reduction
sequence flakes were concentrated above a 0.75 probability value.

``` r
## Compute class probs according to cortex amount ####
# Get probabilities
Cortex.Class <- as.data.frame(SVM_Poly$pred[,4:9]) %>% 
  group_by(rowIndex) %>% 
  summarise(
    L = mean(L),
    D = mean(D),
    HD = mean(HD)) 

# Left join
ML_Data$rowID <- 1:nrow(ML_Data)

Cortex.Class <- left_join(Cortex.Class, ML_Data,
          by = c("rowIndex" = "rowID"))

# Get values for true class 
Cortex.Class %>% mutate(
  True.Class.Val = case_when(
    Class == "L" ~ L,
    Class == "D" ~ D,
    Class == "HD" ~ HD
  )) %>% 
# and plot
  ggplot(aes(factor(Cortex), True.Class.Val, fill = factor(Cortex))) +
  facet_wrap(~ factor(Class,
                      labels = 
                        c("Levallois", "Discoidal", "Hierar. Disc."))) +
  geom_violin(alpha = 0.4) +
  geom_boxplot(alpha = 0.9, width = 0.25) +
  ggsci::scale_fill_nejm(
    name = "Cortex amount",
    labels = c(
      "100% Cortical", ">50% Cortical", "<50% Cortical",
      "~10% Cortical", "No Cortex")) +
  ylab("Predicted probability") +
  xlab("Amount of cortex") +
  scale_x_discrete(labels = c("100%", ">50%", "<50%", "~10%", "0%")) +
  geom_jitter(width = 0.15, alpha = 0.9, size = 0.9, shape = 23, aes(fill = factor(Cortex))) +
  theme_light() +
  guides(fill = guide_legend(title.position = "top", nrow = 1)) + 
  theme(
    legend.position = "none",
    strip.text = element_text(color = "black", face = "bold", size = 9),
    strip.background = element_rect(fill = "white", colour = "black", size = 1),
    axis.text = element_text(color = "black", size = 7),
    axis.title = element_text(color = "black", size = 9))
```

![](H:\02CAMP~1\03ARTI~1\00GITH~1\2022~1.04I\IN-BET~1\Report\LIES-I~1/figure-gfm/Cortex%20and%20class%20probabilities-1.png)<!-- -->

Products detached from discoid reduction sequences had the second
highest average of belonging to their class without considering cortex
amount (0.508). As with Levallois products, as the cortex amount
decreased, the probability of correctly being attributed to discoid
reduction sequences increased. However, this increase was not as marked
or clear as for Levallois products. The 100% cortical flakes had an
average of 0.456, \> 50% cortical flakes an average of 0.45, \< 50%
cortical an average of 0.512, residual cortical flakes an average of
0.486, and non-cortical flakes an average of 0.538. Again, the
distribution of non-cortical flakes presented a long tail of low values,
although most of the flakes were concentrated above the 0.5 value.

No clear pattern in the probability distribution of values was observed
for the hierarchical discoid flakes. Flakes produced by means of the
hierarchical discoid method presented the lowest average probability
value of correctly being assigned to their true class (0.456) as
expected from the corresponding F1 and AUC values. Flakes with less than
50% cortex and residual cortical flakes had the highest probability
averages of correctly being identified as hierarchical discoid flakes
(0.554 with less than 50% cortex, and 0.524 with only a residual
presence of cortex). However, their low number should be taken into
consideration. Non-cortical flakes exhibited the lowest average of
probability value (0.432) with a wide range of distribution of
probability values, which indicates the difficulty of differentiating
even advanced reduction products from hierarchical discoid knapping
sequences.

## 4. Discussion

An analysis of machine learning model performance metrics (accuracy and
AUC) found that SVM with polynomial kernel is the best model for
differentiating between the three knapping strategies studied. SVM with
polynomial kernel provided a general excellent or good AUC value (0.824)
and notable accuracy 0.667. However, depending on the knapping strategy,
notable differences were found in per-class classification metrics and
AUCs. Our results also provide insight into variable importance, showing
that measures of flake surface in relation to thickness (carination
index and ratio of flake surface to thickness), angle of detachment (IPA
and EPA), and thickness (mean and maximum thickness) are key
considerations in the discrimination of knapping methods. In general, we
found that corticality affects the ability of the model to determine the
knapping method by which the flakes were detached. We detected a general
trend: as the amount of cortex diminishes, it becomes easier for the
model to identify the knapping method by which the flake was detached.
However, again, this trend exhibited marked differences between knapping
methods. It was very clear in the case of products detached from
Levallois reduction sequences but not so evident for products detached
by means of hierarchical discoid reduction sequences.

Flakes detached from Levallois reduction sequences yielded the best
identification values, with an individual outstanding AUC (0.91) and
high general performance metrics, such as the F1 score (0.797). These
results underscore the singularity of products obtained from Levallois
preferential and recurrent centripetal reduction sequences and the
unlikelihood of confusing them with flakes detached by means of either
discoid or hierarchical discoid reduction sequences.

Interpreting the relationship between the discoid and hierarchical
discoid methods is more complex. The individual AUC for the
identification of discoid flakes offered an excellent or good value
(0.82) along with a relatively good F1 score (0.647). These values were
not the result of over-predicting the discoid class (35.65% of the
assemblage was predicted to be discoid against an actual 34.7%), but
rather due to very limited confusion with Levallois products (only 4.49%
of cases). As previously mentioned, although the identification of
flakes detached by means of hierarchical discoid reduction sequences
presented a relatively low F1 score (0.56), it did have an acceptable or
fair AUC (0.73). These results indicate the ability of the model to
differentiate between the products of the two strategies, reinforcing
the notion that they are two different individual technical systems.
However, the evaluation of directions of confusion showed that the SVM
with polynomial kernel commonly misidentified products from both
knapping methods. This can be interpreted as evidence of a very close
relationship between the two technical systems.

The relationships between the Levallois, discoid and hierarchical
discoid knapping methods have been previously noted by different
authors. Lenoir & Turq ([1995](#ref-dibble_recurrent_1995)) proposed the
use of the term ‘recurrent centripetal’ to include both discoid debitage
and recurrent centripetal Levallois, and that Levallois (*sensu
stricto*) should be limited to preferential and recurrent lineal
modalities. Similarly, Casanova *et al.*
([2014](#ref-casanova_debitage_2014)) proposed including Levallois
recurrent centripetal and hierarchical discoid modalities within the
‘bifacial centripetal hierarchical’ category. In the present study, the
combined use of attribute analysis and machine learning models
effectively separated flakes obtained from Levallois recurrent
centripetal and preferential sequences from those obtained from
hierarchical discoid sequences. A limited percentage of hierarchical
discoid products were identified as coming from Levallois recurrent and
preferential reduction sequences (13.5%) and the confusion in the
opposite direction was less common (12.44). Thus, these results do not
support grouping Levallois recurrent centripetal and hierarchical
discoid into the same category, as the products from these two
approaches seem to be easily differentiated. Mourre
([2003](#ref-peresani_discoiou_2003)) situated the hierarchical discoid
knapping method at the margins of the discoid group, given the specific
characteristics of the two techniques. At the same time, Levallois
recurrent centripetal modality ([Mourre
2003](#ref-peresani_discoiou_2003)) was placed within the Levallois
group, but also overlapping with the discoid and hierarchical discoid
knapping methods. The results of this study offer a point of agreement
and a point of disagreement with this interpretation of the
relationships between the three knapping methods. As point of
disagreement, the very limited misidentification of discoid and
Levallois products does not support the notion of an overlap between
these two methods. This high level of separation between Levallois
recurrent centripetal and discoid products is also supported by previous
studies that used attribute analysis and machine learning models
([González-Molina *et al.*
2020](#ref-gonzalez-molina_distinguishing_2020)). As point of agreement,
the notable confusion in the identification of discoid and hierarchical
discoid products supports the proposal that the two methods belong to
centripetal debitage systems, although our results indicate that a
notable level of separation between products from the two systems can be
achieved.

Archer *et al.* ([2021](#ref-archer_quantifying_2021)) uused 3D
geometric morphometrics for the identification of three distinct
knapping methods (laminar, discoid and Levallois) and indicated a
general success rate of between 73% and 77%, with Levallois flakes
exhibiting the highest identification rate (87%) and discoid flakes the
lowest (40%). The overall higher precision reached by Archer *et al.*
([2021](#ref-archer_quantifying_2021)) was also expected in this study,
as we included two classes which are commonly considered to belong to
the same family and difficult to differentiate (discoid and hierarchical
discoid) instead of three discrete knapping methods. However, their
results for the identification of discoid products contrast with the
results of the present study, which yielded notably higher values of
sensitivity (0.656) and F1 (0.647) for discoid products. Again, it is
important to consider that these moderate values resulted from the
inclusion of a closely related strategy (hierarchical discoid) and that
confusion with Levallois flakes was minimal. González-Molina *et al.*
([2020](#ref-gonzalez-molina_distinguishing_2020)) presented a balanced
dataset of discoid and Levallois recurrent centripetal flakes and tested
a series of machine learning algorithms for classification, and found
that random forest provided the best results. González-Molina *et al.*
([2020](#ref-gonzalez-molina_distinguishing_2020)) reported 90%
precision for the model when the technological classification variable
was included for flakes. As they correctly state ([González-Molina *et
al.* 2020](#ref-gonzalez-molina_distinguishing_2020)), this variable
depends completely on the researcher. Several researchers have called
attention to the subjective nature of using the classification
“Levallois flake” or the inclusion of the category of “Atypical
Levallois flake” ([Debénath & Dibble 1994](#ref-debenath_handbook_1994);
[Hovers 2009](#ref-hovers_lithic_2009)). González-Molina *et al.*
([2020](#ref-gonzalez-molina_distinguishing_2020)) additionally provided
a random forest model without the technological classification feature
which had a precision rate of 80%. In this model, the first five
variables were related to flake width. However, aspects of flake width
and length can be influenced by initial core and nodule size or by the
process of retouch ([Shott & Seeman 2017](#ref-shott_use_2017)), making
them a less desirable variable for the identification of knapping
methods.

SVM with polynomial kernel selected variables for knapping method
classification already noted in previous studies ([Bourguignon
1997](#ref-bourguignon_mousterien_1997); [Carmignani *et al.*
2017](#ref-carmignani_technological_2017); [González-Molina *et al.*
2020](#ref-gonzalez-molina_distinguishing_2020); [Mourre
2003](#ref-peresani_discoiou_2003); [Slimak
2003](#ref-peresani_les_2003)). The carination index ([Laplace
1968](#ref-laplace_recherches_1968)) was considered the most important
variable for the discrimination of discoid and Levallois products, and
also considered notably important for the identification of flakes
detached by means of hierarchical discoid reduction sequences. Although
thickness measurements are metric variables, they are less subject to
variations due to initial nodule and core size or retouch. Previous
researchers have highlighted the importance of blank thickness for the
differentiation of knapping methods and have shown that Levallois blanks
tend to be thinner and more regular than flakes from discoid production
systems ([Boëda 1994](#ref-boeda_concept_1994); [Boëda
1995b](#ref-dibble_levallois:_1995); [Bourguignon
1997](#ref-bourguignon_mousterien_1997); [González-Molina *et al.*
2020](#ref-gonzalez-molina_distinguishing_2020); [Lenoir & Turq
1995](#ref-dibble_recurrent_1995); [Mourre
2003](#ref-peresani_discoiou_2003); [Slimak
2003](#ref-peresani_les_2003); [Terradas
2003](#ref-terradas_discoid_2003)).

Internal platform angle (IPA) is considered a slightly more important
feature than the external platform angle (EPA) for the determination of
knapping methods. Previous studies have called attention to the
importance of angular relations between the platform and dorsal or
ventral surfaces for the discrimination of knapping methods ([Boëda
1993](#ref-boeda_debitage_1993); [Boëda
1995b](#ref-dibble_levallois:_1995); [Kelly
1954](#ref-kelly_contribution_1954); [Lenoir & Turq
1995](#ref-dibble_recurrent_1995); [Terradas
2003](#ref-terradas_discoid_2003); [Soriano & Villa
2017](#ref-soriano_early_2017)). In the experimental sample used in this
study, Levallois products had IPAs with lower values than those of
discoid or hierarchical discoid products, despite the inclusion of
cortical elements. Problems with the manual recording of IPA and EPA
related to the general morphology of flakes have been acknowledged by
other authors ([Davis & Shea 1998](#ref-davis_quantifying_1998); [Dibble
& Pelcin 1995](#ref-dibble_effect_1995)); however, our research
emphasises its importance for the determination of knapping methods.

This study highlights the type of platform (prepared and plain
platforms) as a key variable for the differentiation of knapping
methods. Previous studies have also pinpointed the importance of
platform preparation for the differentiation of knapping strategies
([Lenoir & Turq 1995](#ref-dibble_recurrent_1995)). Although this seems
to be a significant feature, it is important to consider that platforms
vary widely in the archaeological record. For example, Levallois
products commonly exhibit plain platforms ([Bordes
1961b](#ref-bordes_typologie_1961)). Additionally, platform preparation
can be related to the knapping style and preferences of the individual
knapper, with different knappers producing very similar products with
different platform preparation ([Driscoll & García-Rojas
2014](#ref-driscoll_their_2014)). Mean thickness of the blank was
considered as a key feature by the random forest algorithm, as did the
other algorithms tested, along with maximum thickness for the
differentiation of knapping methods.

The present study did not include other flaking strategies common in
western Europe during the Middle and early Middle Palaeolithic, such as
Quina and SSDA ([Bourguignon 1997](#ref-bourguignon_mousterien_1997);
[Forestier 1993](#ref-forestier_clactonien:_1993)). Although in western
Europe the coexistence of Levallois and discoid knapping methods with
other knapping methods in the same archaeological levels is a subject of
debate ([Faivre *et al.* 2017](#ref-faivre_late_2017); [Grimaldi &
Santaniello 2014](#ref-grimaldi_new_2014); [Marciani *et al.*
2020](#ref-marciani_lithic_2020); [Ríos-Garaizar
2017](#ref-rios-garaizar_new_2017)), the present research can be
considered for assemblages where Levallois and discoid and hierarchical
discoid knapping strategies coexist. Thus, the examination and
evaluation of the chaîne opératoire along with the assemblage context
and integrity are fundamental for the study of lithic technology
([Soressi & Geneste 2011](#ref-soressi_history_2011)). The chaîne
opératoire and assemblage context should be considered prior to the
application of machine learning models for the identification of
knapping methods.

## 5. Conclusions

The present study used attribute analysis to identify three knapping
methods (Levallois, discoid, and hierarchical discoid) in flakes
produced with those methods. A secondary objective was to evaluate the
degree of confusion between Levallois recurrent centripetal and
hierarchical discoid flakes. This secondary objective is relevant since
several sites report similar reduction strategies under an umbrella of
terms (recurrent centripetal debitage, non-Levallois debitage with
hierarchised surfaces, hierarchical bifacial centripetal, centripetal
character with preferential surfaces, hierarchical centripetal), which
are here grouped under the term hierarchical discoid.  
Results from the best machine learning model (SVM with polynomial
kernel) indicate that flakes from Levallois recurrent centripetal
reduction sequences are highly distinguishable from those of
hierarchical discoid reduction sequences. This underscores the
singularity of the Levallois reduction strategy, even in its recurrent
centripetal modality. Despite some confusion in the identification of
flakes detached from discoid and hierarchical discoid reduction
sequences, a notable degree of separation can be achieved. This can be
considered an indication that the two strategies are separate reduction
strategies with their own singularities, while also falling under the
umbrella of centripetal strategies.  
This study also employed ROC curves and AUCs to identify knapping
strategies among flakes. The use of AUCs as a metric of model
performance should be taken into consideration in lithic studies that
employ machine learning models. This is because they make use of
decision thresholds which will sort between ambiguous flakes (such as
the ones belonging to initial reduction sequences) and diagnostic flakes
(such as the ones from full production). Finally, it is important to
highlight that these results illustrate the applicability of machine
learning models (along with the present dataset) to contexts of the
archaeological record in which these reduction strategies are present.

## Acknowledgements

The authors wish to thank the editor and the two anonymous reviewers for
their comments and suggestions. This research has been possible thanks
to the Program for the Requalification of the University System
Margarita Salas (CA1/RSUE/2021-00743) financed through the Spanish
“Recovery, Transformation and Resilience Plan” and managed from the
Ministry of Universities (Ministerio de Universidades) and the
Autonomous University of Madrid (Universidad Autónoma de Madrid). This
article is the result of the research project PID2019-103987GB-C33, “En
los limites de la diversidad: comportamiento Neandertal en el centro y
sur de la Penisula Iberica” financed by Agencia Estatal de Investigación
(AEI) and Fondo Europeo de Desarrollo Regional (FEDER). This study was
also supported by project PID2019-103987GB-C31 from the Spanish Ministry
of Science and Innovation (MICINN). Development of the experimentation
and analysis of the materials were undertaken at the Laboratory of
Experimental Archaeology (Universidad Autónoma de Madrid). The research
technical support of Maria Dolors Guillén was supported by the Spanish
Ministry of Science and Innovation through the “María de Maeztu”
excellence accreditation (CEX2019-000945-M).

</div>

## References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-barker_lithics_2005" class="csl-entry">

Andrefsky, W. 2005, *Lithics Macroscopic Approaches to Analysis*,
Second., (G. Barker, Ed.), Cambridge, Cambridge University Press.

</div>

<div id="ref-archer_quantifying_2021" class="csl-entry">

Archer, W., Djakovic, I., Brenet, M., Bourguignon, L., Presnyakova, D.,
Schlager, S., Soressi, M. & McPherron, S.P. 2021, Quantifying
differences in hominin flaking technologies with 3D shape analysis,
*Journal of Human Evolution*, 150: 102912.
doi:[10.1016/j.jhevol.2020.102912](https://doi.org/10.1016/j.jhevol.2020.102912)

</div>

<div id="ref-montes_barquin_paleoecologiy_2005" class="csl-entry">

Baena, J., Carrión, E., Ruiz, B., Ellwood, B., Sesé, C., Yravedra, J.,
Jordá, J., Uzquiano, P., Velázquez, R., Manzano, I., Sanchez-Marco, A. &
Hernández, F. 2005, Paleoecología y comportamiento humano durante el
Pleistoceno Superior en la comarca de Liébana: La secuencia de la Cueva
de El Esquilleu (Occidente de Cantabria, España), In: *Neandertales
Cantábricos. Estado de la Cuestión* (R. Montes Barquín, Ed.),
Monografías., Santander, Museo de Altamira: p. 461–487.

</div>

<div id="ref-bagolini_ricerche_1968" class="csl-entry">

Bagolini, B. 1968, Ricerche sulle dimensioni dei manufatti litici
preistorici non ritoccati, *Annali dell’Università di Ferrara : nuova
serie*, 1(10): 195–219.

</div>

<div id="ref-bergmeir_neural_2012" class="csl-entry">

Bergmeir, C. & Benítez, J.M. 2012, Neural Networks in R using the
Stuttgart Neural Network Simulator: RSNNS, *Journal of Statistical
Software*, 46(7).
doi:[10.18637/jss.v046.i07](https://doi.org/10.18637/jss.v046.i07)

</div>

<div id="ref-bisson_nineteenth_2000" class="csl-entry">

Bisson, M.S. 2000, Nineteenth Century Tools for Twenty-First Century
Archaeology? Why the Middle Paleolithic Typology of François Bordes Must
Be Replaced, *Journal of Archaeological Method and Theory*, 7(1): 1–48.
doi:[1072-5369/00/0300-0001
\$18.00/0](https://doi.org/1072-5369/00/0300-0001 $18.00/0)

</div>

<div id="ref-boeda_caracteristiques_1995" class="csl-entry">

Boëda, E. 1995a, Caractéristiques techniques des chaînes opératoires
lithiques des niveaux micoquiens de Külna (Tchécoslovaquie), *Paléo*, 1:
57–72.
doi:[10.3406/pal.1995.1380](https://doi.org/10.3406/pal.1995.1380)

</div>

<div id="ref-farizy_surface_1990" class="csl-entry">

Boëda, E. 1990, De la surface au volume. Analyse des concetions des
débitages Levallois et laminaire, In: *Paleolithique moyen recent et
Paleolithique superieur ancien en Europe. Ruptures et transitions:
Examen critique des documents archéologiques* (C. Farizy, Ed.), Mémoires
du Musée de Préhistoire d’Ile-de-France., Nemours, A.P.R.A.I.F.: p.
63–68.

</div>

<div id="ref-boeda_concept_1994" class="csl-entry">

Boëda, E. 1994, *Le concept Levallois: Variabilité des méthodes*, CNRS.

</div>

<div id="ref-boeda_debitage_1993" class="csl-entry">

Boëda, E. 1993, Le débitage discoïde et le débitage Levallois récurrent
centripède, *Bulletin de la Société Préhistorique Française*, 90(6):
392–404.
doi:[10.3406/bspf.1993.9669](https://doi.org/10.3406/bspf.1993.9669)

</div>

<div id="ref-dibble_levallois:_1995" class="csl-entry">

Boëda, E. 1995b, Levallois: A Volumetric Construction, Methods, A
Technique, In: *The Definition and Interpretation of Levallois
Technology* (H. L. Dibble & O. Bar-Yosef, Eds.), Monographs in World
Archaeology., Madison, Wisconsin, Prehistory Press: p. 41–68.

</div>

<div id="ref-boeda_identification_1990" class="csl-entry">

Boëda, E., Geneste, J.-M. & Meignen, L. 1990, Identification de chaînes
opératoires lithiques du Paléolithique ancien et moyen, *Paléo*, 2:
43–80.

</div>

<div id="ref-bordes_levalloisien_1953" class="csl-entry">

Bordes, F. 1953, Levalloisien et Moustérien, *Bulletin de la Société
préhistorique de France*, 50(4): 226–235.
doi:[10.3406/bspf.1953.3035](https://doi.org/10.3406/bspf.1953.3035)

</div>

<div id="ref-bordes_mousterian_1961" class="csl-entry">

Bordes, F. 1961a, Mousterian Cultures in France, *Science*, 134(3482):
803–810.

</div>

<div id="ref-bordes_typologie_1961" class="csl-entry">

Bordes, F. 1961b, *Typologie du Paléolithique ancien et moyen*,
Bordeaux, CNRS Editions.

</div>

<div id="ref-bourguignon_conception_1996" class="csl-entry">

Bourguignon, L. 1996, La conception du debitage Quina, *Quaternaria
Nova*, 6: 149–166.

</div>

<div id="ref-bourguignon_mousterien_1997" class="csl-entry">

Bourguignon, L. 1997, *Le Moustérien de type Quina: Nouvelle Définition
d’une entité technique*, PhD thesis, Nanterre, Université de Paris X -
Nanterre.

</div>

<div id="ref-peresani_chaine_2003" class="csl-entry">

Bourguignon, L. & Turq, A. 2003, Une chaîne opératoire de débitage
discoïde sur éclat du Moustérien à denticulés aquitain: Les exemples de
Champ Bossuet et de Combre Grenal c.14, In: *Discoid Lithic Technology.
Advances and Implications* (M. Peresani, Ed.), BAR International
Series., Oxford: p. 131–152.

</div>

<div id="ref-bradley_use_1997" class="csl-entry">

Bradley, A.P. 1997, The use of the area under the ROC curve in the
evaluation of machine learning algorithms, *Pattern recognition*, 30(7):
1145–1159.

</div>

<div id="ref-breiman_random_2001" class="csl-entry">

Breiman, L. 2001, Random Forests, *Machine Learning*, 45(1): 5–32.
doi:[10.1023/A:1010933404324](https://doi.org/10.1023/A:1010933404324)

</div>

<div id="ref-carmignani_technological_2017" class="csl-entry">

Carmignani, L., Moncel, M.-H., Fernandes, P. & Wilson, L. 2017,
Technological variability during the Early Middle Palaeolithic in
Western Europe. Reduction systems and predetermined products at the Bau
de l’Aubesier and Payre (South-East France), *PLoS ONE*, 12(6):
e0178550.
doi:[10.1371/journal.pone.0178550](https://doi.org/10.1371/journal.pone.0178550)

</div>

<div id="ref-casanova_i_marti_strategies_2009" class="csl-entry">

Casanova i Martí, J., Martínez Moreno, J., Mora Torcal, R. & Torre, I.
de la 2009, Stratégies techniques dans le Paléolithique Moyen du sud-est
des Pyrénées, *L’Anthropologie*, 113: 313–340.
doi:[10.1016/j.anthro.2009.04.004](https://doi.org/10.1016/j.anthro.2009.04.004)

</div>

<div id="ref-casanova_debitage_2014" class="csl-entry">

Casanova, J., Roda Gilabert, X., Martínez-Moreno, J. & Mora, R. 2014,
Débitage, façonnage et diversité des systèmes techniques du Moustérien à
Tragó (Pré-Pyrénées de Lleida, Catalogne), In: *Transitions, ruptures et
continuité en Préhistoire* (J. Jaubert, N. Fourment & P. Depaepe, Eds.),
Paris, Société Préhistorique Française: p. 139–154.

</div>

<div id="ref-clarkson_lithics_2007" class="csl-entry">

Clarkson, C. 2007, *Lithics in the Land of the Lightning Brothers: The
Archaeology of Wardaman Country, Northern Territory*, Canberra, The
Australian National University Press.

</div>

<div id="ref-cortes_support-vector_1995" class="csl-entry">

Cortes, C. & Vapnik, V. 1995, Support-vector networks, *Machine
learning*, 20(3): 273–297.

</div>

<div id="ref-cotterell_formation_1987" class="csl-entry">

Cotterell, B. & Kamminga, J. 1987, The Formation of Flakes, *American
Antiquity*, 52(4): 675–708.

</div>

<div id="ref-cover_nearest_1967" class="csl-entry">

Cover, T. & Hart, P. 1967, Nearest neighbor pattern classification,
*IEEE Transactions on Information Theory*, 13(1): 21–27.
doi:[10.1109/TIT.1967.1053964](https://doi.org/10.1109/TIT.1967.1053964)

</div>

<div id="ref-cramer_early_2004" class="csl-entry">

Cramer, J.S. 2004, The early origins of the logit model, *Studies in
History and Philosophy of Science Part C: Studies in History and
Philosophy of Biological and Biomedical Sciences*, 35(4): 613–626.
doi:[10.1016/j.shpsc.2004.09.003](https://doi.org/10.1016/j.shpsc.2004.09.003)

</div>

<div id="ref-davis_quantifying_1998" class="csl-entry">

Davis, Z.J. & Shea, J.J. 1998, Quantifying lithic curation: An
experimental test of Dibble and Pelcin’s original flake-tool mass
predictor, *Journal of Archaeological Science*, 25(7): 603–610.

</div>

<div id="ref-debenath_handbook_1994" class="csl-entry">

Debénath, A. & Dibble, H.L. 1994, *Handbook of Paleolithic Typology*,
University of Pennsylvania Press.

</div>

<div id="ref-dibble_variability_1995" class="csl-entry">

Delagnes, A. 1995, Variability within Uniformity: Three Levels of
Variability within the Levallois System, In: *The Definition and
Interpretation of Levallois Technology* (H. L. Dibble & O. Bar-Yosef,
Eds.), Monographs in World Archaeology., Madison, Wisconsin, Prehistory
Press: p. 201–211.

</div>

<div id="ref-vandermeersch_les_2007" class="csl-entry">

Delagnes, A., Jaubert, J. & Meignen, L. 2007, Les technocomplexes du
paléolithique moyen en Europe occidentale dans leur cadre diachronique
et géographique, In: *Les Neandertaliens. Biologie et Cultures* (B.
Vandermeersch & B. Maureille, Eds.), Documents préhistoriques., Paris,
Editions du Comité des Travaux Historiques et Scientifiques: p. 213–229.

</div>

<div id="ref-hovers_diversity_2006" class="csl-entry">

Delagnes, A. & Meignen, L. 2006, Diversity of Lithic Production Systems
During the Middle Paleolithic in France. Are There Any Chronological
Trends?, In: *Transitions Before the Transition Evolution and Stability
in the Middle Paleolithic and Middle Stone Age* (E. Hovers, S. L. Kuhn &
M. Jochim, Eds.), Springer: p. 85–107.

</div>

<div id="ref-dibble_biache_1995" class="csl-entry">

Dibble, H.L. 1995, Biache Saint-Vaast, Level IIA: A comparison of
analytical approaches, In: *The definition and interpretation of
Levallois technology* (H. L. Dibble & O. Bar-Yosef, Eds.), Monographs in
World Archaeology., Prehistory Press: p. 93–116.

</div>

<div id="ref-mellars_implications_1989" class="csl-entry">

Dibble, H.L. 1989, The Implications of Stone Tool Types for the Presence
of Language During the Lower and Middle Palaeolithic, In: *The Human
Revolution: Behavioural and Biological Perspectives on the Origins of
Modem Humans* (P. Mellars & C. Stringer, Eds.), Edinburgh, Edinburgh
University Press: p. 415–432.

</div>

<div id="ref-dibble_effect_1995" class="csl-entry">

Dibble, H.L. & Pelcin, A. 1995, The Effect of Hammer Mass and Velocity
on Flake Mass, *Journal of Archaeological Science*, 22(3): 429–439.
doi:[10.1006/jasc.1995.0042](https://doi.org/10.1006/jasc.1995.0042)

</div>

<div id="ref-driscoll_their_2014" class="csl-entry">

Driscoll, K. & García-Rojas, M. 2014, Their lips are sealed: Identifying
hard stone, soft stone, and antler hammer direct percussion in
Palaeolithic prismatic blade production, *Journal of Archaeological
Science*, 47: 134–141.
doi:[10.1016/j.jas.2014.04.008](https://doi.org/10.1016/j.jas.2014.04.008)

</div>

<div id="ref-eren_are_2008" class="csl-entry">

Eren, M.I., Greenspan, A. & Garth Sampson, C. 2008, Are Upper
Paleolithic blade cores more productive than Middle Paleolithic
discoidal cores? A replication experiment, *Journal of Human Evolution*,
55: 952–961.
doi:[10.1016/j.jhevol.2008.07.009](https://doi.org/10.1016/j.jhevol.2008.07.009)

</div>

<div id="ref-eren_why_2012" class="csl-entry">

Eren, M.I. & Lycett, S.J. 2012, Why Levallois? A Morphometric Comparison
of Experimental “Preferential” Levallois Flakes versus Debitage Flakes,
*PLoS ONE*, 7(1): e29273.
doi:[10.1371/journal.pone.0029273](https://doi.org/10.1371/journal.pone.0029273)

</div>

<div id="ref-faivre_late_2017" class="csl-entry">

Faivre, G.-P., Gravina, B., Bourguignon, L., Discamps, E. & Turq, A.
2017, Late Middle Palaeolithic lithic technocomplexes (MIS 5-3) in the
northeastern Aquitaine Basin: Advances and challenges, *Quaternary
International*, 433: 116–131.
doi:[10.1016/j.quaint.2016.02.060](https://doi.org/10.1016/j.quaint.2016.02.060)

</div>

<div id="ref-fisher_use_1936" class="csl-entry">

Fisher, R.A. 1936, The use of multiple measurements in taxonomic
problems, *Annals of Eugenics*, 7: 179–188.

</div>

<div id="ref-forestier_clactonien:_1993" class="csl-entry">

Forestier, H. 1993, Le Clactonien: Mise en application d’une nouvelle
méthode de débitage s’inscrivant dans la variabilité des systèmes de
production lithique du Paléolithique ancien, *Paléo*, 5(1): 53–82.
doi:[10.3406/pal.1993.1104](https://doi.org/10.3406/pal.1993.1104)

</div>

<div id="ref-frey_letter_1991" class="csl-entry">

Frey, P.W. & Slate, D.J. 1991, Letter recognition using Holland-style
adaptive classifiers, *Machine learning*, 6(2): 161–182.

</div>

<div id="ref-friedman_greedy_2001" class="csl-entry">

Friedman, J.H. 2001, [Greedy function approximation: A gradient boosting
machine](https://www.jstor.org/stable/2699986), *Annals of statistics*,
29(5): 1189–1232.

</div>

<div id="ref-friedman_stochastic_2002" class="csl-entry">

Friedman, J.H. 2002, Stochastic gradient boosting, *Computational
Statistics & Data Analysis*, 38(4): 367–378.
doi:[10.1016/S0167-9473(01)00065-2](https://doi.org/10.1016/S0167-9473(01)00065-2)

</div>

<div id="ref-geneste_developpement_1990" class="csl-entry">

Geneste, J.-M. 1990, Développement des systèmes de production lithique
au cours du Paléolithique moyen en Aquitaine septentrionale, In:
*Paléolithique Moyen Récent et Paléolithique Supérieur Ancien en Europe*
(C. Farizy, Ed.), Mémoires du Musée de Préhistoire d’Ile-de-France.,
Nemours, APRAIF: p. 203–214.

</div>

<div id="ref-gonzalez-molina_distinguishing_2020" class="csl-entry">

González-Molina, I., Jiménez-García, B., Maíllo-Fernández, J.-M.,
Baquedano, E. & Domínguez-Rodrigo, M. 2020, Distinguishing Discoid and
Centripetal Levallois methods through machine learning P. De Smedt, Ed.,
*PLOS ONE*, 15(12): e0244288.
doi:[10.1371/journal.pone.0244288](https://doi.org/10.1371/journal.pone.0244288)

</div>

<div id="ref-greenwell_package_2019" class="csl-entry">

Greenwell, B., Boehmke, B., Cunningham, J., Developers, G.B.M. &
Greenwell, M.B. 2019, Package “gbm,” *R package version*, 2(5).

</div>

<div id="ref-grimaldi_new_2014" class="csl-entry">

Grimaldi, S. & Santaniello, F. 2014, New insights into Final Mousterian
lithic production in western Italy, *Quaternary International*, 350:
116–129.
doi:[10.1016/j.quaint.2014.03.057](https://doi.org/10.1016/j.quaint.2014.03.057)

</div>

<div id="ref-herisson_emergence_2016" class="csl-entry">

Hérisson, D., Brenet, M., Cliquet, D., Moncel, M.-H., Richter, J.,
Scott, B., Van Baelen, A., Di Modica, K., De Loecker, D., Ashton, N.,
Bourguignon, L., Delagnes, A., Faivre, J.-P., Folgado-Lopez, M., Locht,
J.-L., Pope, M., Raynal, J.-P., Roebroeks, W., Santagata, C., Turq, A. &
Van Peer, P. 2016, The emergence of the Middle Palaeolithic in
north-western Europe and its southern fringes, *Quaternary
International*, 411: 233–283.
doi:[10.1016/j.quaint.2016.02.049](https://doi.org/10.1016/j.quaint.2016.02.049)

</div>

<div id="ref-hiscock_quantifying_2002" class="csl-entry">

Hiscock, P. 2002, Quantifying the Size of Artefact Assemblages, *Journal
of Archaeological Science*, 29: 251–258.
doi:[10.1006/jasc.2001.0705](https://doi.org/10.1006/jasc.2001.0705)

</div>

<div id="ref-hovers_lithic_2009" class="csl-entry">

Hovers, E. 2009, *The lithic assemblages of Qafzeh Cave*, New york,
Oxford University Press.

</div>

<div id="ref-james_introduction_2013" class="csl-entry">

James, G., Witten, D., Hastie, T. & Tibshirani, R. 2013, *An
Introduction to Statistical Learning with Applications in R*, Second
Edition., Springer.

</div>

<div id="ref-jaubert_gisement_1993" class="csl-entry">

Jaubert, J. 1993, Le gisement paléolithique moyen de Mauran
(Haute-Garonne) : Techno-économie des industries lithiques, *Bulletin de
la Société préhistorique française*, 90(5): 328–335.
doi:[10.3406/bspf.1993.9642](https://doi.org/10.3406/bspf.1993.9642)

</div>

<div id="ref-karatzoglou_support_2006" class="csl-entry">

Karatzoglou, A., Meyer, D. & Hornik, K. 2006, Support Vector Machines in
R, *Journal of Statistical Software*, 15: 1–28.
doi:[10.18637/jss.v015.i09](https://doi.org/10.18637/jss.v015.i09)

</div>

<div id="ref-karatzoglou_kernlab_2004" class="csl-entry">

Karatzoglou, A., Smola, A., Hornik, K. & Zeileis, A. 2004, Kernlab - An
S4 Package for Kernel Methods in R, *Journal of Statistical Software*,
11: 1–20.
doi:[10.18637/jss.v011.i09](https://doi.org/10.18637/jss.v011.i09)

</div>

<div id="ref-kelly_contribution_1954" class="csl-entry">

Kelly, H. 1954, Contribution à l’étude de la technique de la taille
levalloisienne, *Bulletin de la Société Préhistorique Française*,
51(3-4): 149–169.
doi:[10.3406/bspf.1954.3077](https://doi.org/10.3406/bspf.1954.3077)

</div>

<div id="ref-kuhn_building_2008" class="csl-entry">

Kuhn, M. 2008, Building Predictive Models in R using the caret Package,
*Journal of Statistical Software*, 28(5).
doi:[10.18637/jss.v028.i05](https://doi.org/10.18637/jss.v028.i05)

</div>

<div id="ref-kuhn_roots_2013" class="csl-entry">

Kuhn, S.L. 2013, Roots of the Middle Paleolithic in Eurasia, *Current
Anthropology*, 54(S8): S255–S268.
doi:[10.1086/673529](https://doi.org/10.1086/673529)

</div>

<div id="ref-lantz_machine_2019" class="csl-entry">

Lantz, B. 2019, *Machine learning with R: Expert techniques for
predictive modeling*, Packt publishing ltd.

</div>

<div id="ref-laplace_recherches_1968" class="csl-entry">

Laplace, G. 1968, Recherches de typologie analytique 1968, *Origini*,
II: 7–64.

</div>

<div id="ref-dibble_recurrent_1995" class="csl-entry">

Lenoir, M. & Turq, A. 1995, Recurrent Centripetal Debitage (Levallois
and Discoidal): Continuity or Discontinuity?, In: *The definition and
interpretation of Levallois Technology* (H. L. Dibble & O. Bar-Yosef,
Eds.), Monographs in World Archaeology., Madison, Wisconsin, Prehistory
Press: p. 249–256.

</div>

<div id="ref-peresani_industrie_2003" class="csl-entry">

Locht, J.-L. 2003, L’industrie lithique du gisement de Beauvais (Oise,
France): Objectifs et variabilité du débitage discoïde, In: *Discoid
Lithic Technology: Advances and Implications* (M. Peresani, Ed.), BAR
International Series., Oxford, Archaeopress: p. 193–209.

</div>

<div id="ref-de_lombera-hermida_dawn_2020" class="csl-entry">

Lombera-Hermida, A. de, Rodríguez-Álvarez, X.P., Mosquera, M., Ollé, A.,
García-Medrano, P., Pedergnana, A., Terradillos-Bernal, M.,
López-Ortega, E., Bargalló, A., Rodríguez-Hidalgo, A., Saladié, P.,
Bermúdez de Castro, J.M. & Carbonell, E. 2020, The dawn of the Middle
Paleolithic in Atapuerca: The lithic assemblage of TD10.1 from Gran
Dolina, *Journal of Human Evolution*, 145: 102812.
doi:[10.1016/j.jhevol.2020.102812](https://doi.org/10.1016/j.jhevol.2020.102812)

</div>

<div id="ref-marciani_lithic_2020" class="csl-entry">

Marciani, G., Ronchitelli, A., Arrighi, S., Badino, F., Bortolini, E.,
Boscato, P., Boschin, F., Crezzini, J., Delpiano, D., Falcucci, A.,
Figus, C., Lugli, F., Oxilia, G., Romandini, M., Riel-Salvatore, J.,
Negrino, F., Peresani, M., Spinapolice, E.E., Moroni, A. & Benazzi, S.
2020, Lithic techno-complexes in Italy from 50 to 39 thousand years BP:
An overview of lithic technological changes across the Middle-Upper
Palaeolithic boundary, *Quaternary International*, 551: 123–149.
doi:[10.1016/j.quaint.2019.11.005](https://doi.org/10.1016/j.quaint.2019.11.005)

</div>

<div id="ref-marwick_what_2008" class="csl-entry">

Marwick, B. 2008, What attributes are important for the measurement of
assemblage reduction intensity? Results from an experimental stone
artefact assemblage with relevance to the Hoabinhian of mainland
Southeast Asia, *Journal of Archaeological Science*, 35(5): 1189–1200.
doi:[10.1016/j.jas.2007.08.007](https://doi.org/10.1016/j.jas.2007.08.007)

</div>

<div id="ref-moncel_early_2020" class="csl-entry">

Moncel, M.-H., Ashton, N., Arzarello, M., Fontana, F., Lamotte, A.,
Scott, B., Muttillo, B., Berruti, G., Nenzioni, G. & Tuffreau, A. 2020,
Early Levallois core technology between marine isotope stage 12 and 9 in
Western Europe, *Journal of human evolution*, 139: 102735.
doi:[doi.org/10.1016/j.jhevol.2019.102735](https://doi.org/doi.org/10.1016/j.jhevol.2019.102735)

</div>

<div id="ref-mortillet_prehistorique_1885" class="csl-entry">

Mortillet, G. de 1885, *Le préhistorique. Antiquité de l’homme*,
Deuxième Édition., París, Bibliothèque des Sciences Contemporaines., 658
p.

</div>

<div id="ref-peresani_discoiou_2003" class="csl-entry">

Mourre, V. 2003, Discoïde ou pas Discoïde? Réflexions sur la pertinence
des critères techniques définissant le débitage discoïde, In: *Discoid
Lithic Technology. Advances and Implications* (M. Peresani, Ed.), BAR
International Series., Oxford, Archaeopress: p. 1–17.

</div>

<div id="ref-muller_new_2016" class="csl-entry">

Muller, A. & Clarkson, C. 2016, A new method for accurately and
precisely measuring flake platform area, *Journal of Archaeological
Science: Reports*, 8: 178–186.
doi:[10.1016/j.jasrep.2016.06.015](https://doi.org/10.1016/j.jasrep.2016.06.015)

</div>

<div id="ref-newcomer_nucleus_1974" class="csl-entry">

Newcomer, M.H. & Hivernel-Guerre, F. 1974, Nucléus sur éclat:
Technologie et utilisation par différentes cultures préhistoriques,
*Bulletin de la Société Préhistorique Française*, 71(4): 119–128.
doi:[10.3406/bspf.1974.8308](https://doi.org/10.3406/bspf.1974.8308)

</div>

<div id="ref-ohel_clactonian_1979" class="csl-entry">

Ohel, M.Y., Bhattacharya, D.K., Bordes, F., Cahen, D., Callow, P.,
Collins, D., Katz, P.R., Narr, K.J., Newcomer, M.H., Pappu, R.S., Roe,
D.A., Singer, R. & Wymer, J.J. 1979, [The Clactonian: An Independent
Complex or an Integral Part of the Acheulean? \[And Comments and
Reply\]](http://www.jstor.org/stable/2741680), *Current Anthropology*,
20(4): 685–726.

</div>

<div id="ref-pelegrin_cognition_2009" class="csl-entry">

Pelegrin, J. 2009, Cognition and the emergence of language: A
contribution from lithic technology, In: *Cognitive Archaeology and
Human Evolution* (S. A. de Beaune, F. L. Coolidge & T. Wynn, Eds.), New
York, Cambridge University Press: p. 95–108.

</div>

<div id="ref-peresani_variabilite_1998" class="csl-entry">

Peresani, M. 1998, La variabilité du débitage discoïde dans la grotte de
Fumane (Italie du Nord)/The variability of discoid production at the
grotte de Fumane, *Paléo*, 10: 123–146.
doi:[10.3406/pal.1998.1133](https://doi.org/10.3406/pal.1998.1133)

</div>

<div id="ref-perpere_apport_1986" class="csl-entry">

Perpère, M. 1986, Apport de la typométrie à la définition des éclats
Levallois : L’exemple d’Ault, *Bulletin de la Société préhistorique
française*, 83(4): 115–118.
doi:[10.3406/bspf.1986.8743](https://doi.org/10.3406/bspf.1986.8743)

</div>

<div id="ref-perpere_les_1989" class="csl-entry">

Perpère, M. 1989, Les frontiéres du débitage Levallois: Typométrie des
éclats, *L’Anthropologie*, 95(4): 837–850.

</div>

<div id="ref-quinlan_c4_2014" class="csl-entry">

Quinlan, J.R. 2014, *C4. 5: Programs for machine learning*, Elsevier.

</div>

<div id="ref-quinlan_improved_1996" class="csl-entry">

Quinlan, J.R. 1996, Improved Use of Continuous Attributes in C4.5,
*Journal of Artificial Intelligence Research*, 4: 77–90.
doi:[10.1613/jair.279](https://doi.org/10.1613/jair.279)

</div>

<div id="ref-revillon_les_1994" class="csl-entry">

Révillon, S. & Tuffreau, A. (Eds.) 1994, *Les industries laminaires au
Paléolithique moyen*, Paris, CNRS Editions.

</div>

<div id="ref-ridgeway_generalized_2007" class="csl-entry">

Ridgeway, G. 2007, [Generalized Boosted Models: A guide to the gbm
package](http://CRAN.R-project.org/package=gbm), *R package vignette*,
2007.

</div>

<div id="ref-rios-garaizar_new_2017" class="csl-entry">

Ríos-Garaizar, J. 2017, A new chronological and technological synthesis
for Late Middle Paleolithic of the Eastern Cantabrian Region,
*Quaternary International*, 433: 50–63.
doi:[10.1016/j.quaint.2016.02.020](https://doi.org/10.1016/j.quaint.2016.02.020)

</div>

<div id="ref-robin_proc_2011" class="csl-entry">

Robin, X., Turck, N., Hainard, A., Tiberti, N., Lisacek, F., Sanchez,
J.-C. & Müller, M. 2011, <span class="nocase">pROC</span>: An
open-source package for R and S+ to analyze and compare ROC curves, *BMC
bioinformatics*, 12(1): 1–8.

</div>

<div id="ref-rosenberg-yefet_lower_2022" class="csl-entry">

Rosenberg-Yefet, T., Shemer, M. & Barkai, R. 2022, Lower Paleolithic
Winds of Change: Prepared Core Technologies and the Onset of the
Levallois Method in the Levantine Late Acheulian, *Frontiers in Earth
Science*, 10: 847358.
doi:[10.3389/feart.2022.847358](https://doi.org/10.3389/feart.2022.847358)

</div>

<div id="ref-rumelhart_learning_1986" class="csl-entry">

Rumelhart, D.E., Hinton, G.E. & Williams, R.J. 1986, Learning
representations by back-propagating errors, *Nature*, 323(6088):
533–536.

</div>

<div id="ref-santonja_coexistence_2016" class="csl-entry">

Santonja, M., Pérez-González, A., Panera, J., Rubio-Jara, S. &
Méndez-Quintas, E. 2016, The coexistence of acheulean and ancient middle
palaeolithic techno-complexes in the middle pleistocene of the iberian
peninsula, *Quaternary International*, 411: 367–377.
doi:[10.1016/j.quaint.2015.04.056](https://doi.org/10.1016/j.quaint.2015.04.056)

</div>

<div id="ref-scott_early_2011" class="csl-entry">

Scott, B. & Ashton, N. 2011, The early middle Palaeolithic: The European
context, In: *The ancient human occupation of Britain* (N. Ashton, S.
Lewis & C. Stringer, Eds.), Developments in Quaternary Science., Oxford,
Elsevier: p. 91–112.

</div>

<div id="ref-shott_use_2017" class="csl-entry">

Shott, M.J. & Seeman, M.F. 2017, Use and multifactorial reconciliation
of uniface reduction measures: A pilot study at the Nobles Pond
Paleoindian site, *American Antiquity*, 82(4): 723–741.
doi:[10.1017/aaq.2017.40](https://doi.org/10.1017/aaq.2017.40)

</div>

<div id="ref-slimak_variabilite_1998" class="csl-entry">

Slimak, L. 1998, La variabilité des débitages discoïdes au Paléolithique
moyen: Diversité des méthodes et unité d’un concept. L’exemple des
gisements de la Baume Néron (Soyons, Ardèche) et du Champ Grand
(Saint-Maurice-sur-Loire, Loire), *Préhistoire Anthropologie
Méditerranéennes*, 7: 75–88.

</div>

<div id="ref-peresani_les_2003" class="csl-entry">

Slimak, L. 2003, Les Debitages discoïdes mousteriens: Evaluation d’un
concept technologique, In: *Discoid Lithic Technology. Advances and
Implications* (M. Peresani, Ed.), BAR International Series., Oxford,
Archaeopress: p. 33–65.

</div>

<div id="ref-soressi_history_2011" class="csl-entry">

Soressi, M. & Geneste, J.-M. 2011, The History and Efficacy of the
Chaîne Opératoire Approach to Lithic Analysis: Studying Techniques to
Reveal Past Societies in an Evolutionary Perspective,
*PaleoAnthropology*, 2011: 334–350.
doi:[10.4207/PA.2011.ART63](https://doi.org/10.4207/PA.2011.ART63)

</div>

<div id="ref-soriano_early_2017" class="csl-entry">

Soriano, S. & Villa, P. 2017, Early Levallois and the beginning of the
Middle Paleolithic in central Italy M. D. Petraglia, Ed., *PLOS ONE*,
12(10): e0186082.
doi:[10.1371/journal.pone.0186082](https://doi.org/10.1371/journal.pone.0186082)

</div>

<div id="ref-spackman_signal_1989" class="csl-entry">

Spackman, K.A. 1989, Signal detection theory: Valuable tools for
evaluating inductive learning, In: *Proceedings of the sixth
international workshop on Machine learning*, Elsevier: p. 160–163.

</div>

<div id="ref-r_core_team_r_2019" class="csl-entry">

Team, R.C. 2019, [R: A language and environment for statistical
computing](https://www.R-project.org/).

</div>

<div id="ref-rstudio_team_rstudio_2019" class="csl-entry">

Team, Rs. 2019, [RStudio: Integrated Development for
R](http://www.rstudio.com/).

</div>

<div id="ref-terradas_discoid_2003" class="csl-entry">

Terradas, X. 2003, Discoid flaking method: Conception and technological
variability, In: *Discoid Lithic Technology. Advances and Implications*
(M. Peresani, Ed.), BAR International Series., Oxford, Archaeopress: p.
19–32.

</div>

<div id="ref-thiebaut_discoid_2013" class="csl-entry">

Thiébaut, C. 2013, Discoid debitage stricto sensu: A method adapted to
highly mobile Middle Paleolithic groups?, *P@lethnology*, Varia.

</div>

<div id="ref-tixier_kombewa_1999" class="csl-entry">

Tixier, J. & Turq, A. 1999, Kombewa et alii, *Paléo*, 11: 135–143.
doi:[10.3406/pal.1999.1174](https://doi.org/10.3406/pal.1999.1174)

</div>

<div id="ref-de_la_torre_oldowan_2003" class="csl-entry">

Torre, I. de la, Mora, R., Domínguez-Rodrigo, M., Luque, L. de & Alcalá,
L. 2003, The Oldowan industry of Peninj and its bearing on the
reconstruction of the technological skills of LowerPleistocene hominids,
*Journal of Human Evolution*, 44(2): 203–224.
doi:[10.1016/S0047-2484(02)00206-3](https://doi.org/10.1016/S0047-2484(02)00206-3)

</div>

<div id="ref-venables_modern_2002" class="csl-entry">

Venables, W.N. & Ripley, B.D. 2002, *[Modern applied statistics with
S](https://www.stats.ox.ac.uk/pub/MASS4/)*, Fourth Edition., New York,
Springer.

</div>

<div id="ref-walker_estimation_1967" class="csl-entry">

Walker, S.H. & Duncan, D.B. 1967, Estimation of the Probability of an
Event as a Function of Several Independent Variables, *Biometrika*,
54(1/2): 167–179. doi:[10.2307/2333860](https://doi.org/10.2307/2333860)

</div>

<div id="ref-white_lower_2003" class="csl-entry">

White, M. & Ashton, N. 2003, Lower Palaeolithic Core Technology and the
Origins of the Levallois Method in North-Western Europe, *Current
Anthropology*, 44(4): 598–609.

</div>

<div id="ref-wickham_welcome_2019" class="csl-entry">

Wickham, H., Averick, M., Bryan, J., Chang, W., McGowan, L., François,
R., Grolemund, G., Hayes, A., Henry, L., Hester, J., Kuhn, M., Pedersen,
T., Miller, E., Bache, S., Müller, K., Ooms, J., Robinson, D., Seidel,
D., Spinu, V., Takahashi, K., Vaughan, D., Wilke, C., Woo, K. & Yutani,
H. 2019, Welcome to the Tidyverse, *Journal of Open Source Software*,
4(43): 1686.
doi:[10.21105/joss.01686](https://doi.org/10.21105/joss.01686)

</div>

<div id="ref-wright_ranger_2017" class="csl-entry">

Wright, M.N. & Ziegler, A. 2017, Ranger: A Fast Implementation of Random
Forests for High Dimensional Data in C++ and R, *Journal of Statistical
Software*, 77: 1–17.
doi:[10.18637/jss.v077.i01](https://doi.org/10.18637/jss.v077.i01)

</div>

</div>

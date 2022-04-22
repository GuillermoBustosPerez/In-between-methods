# Between methods: Levallois, Discoid and what falls in between

Guillermo Bustos-Pérez<sup>1, 2</sup>, Javier Baena<sup>1</sup>, Manuel
Vaquero<sup>2, 3</sup>

<sup>1</sup>Universidad Autónoma de Madrid. Departamento de Prehistoria
y Arqueología, Campus de Cantoblanco, 28049 Madrid, Spain  
<sup>2</sup>Institut Català de Paleoecologia Humana i Evolució Social
(IPHES), Zona Educacional 4, Campus Sescelades URV (Edifici W3), 43007
Tarragona, Spain  
<sup>3</sup>Àrea de Prehistoria, Universitat Rovira i Virgili (URV),
Avinguda de Catalunya 35, 43002 Tarragona, Spain

**Abstract**  
The production of lithic artefacts is usually associated to different
knapping methods. Resulting flakes present metric and technological
features representative of the flaking method from which they were
detached. However, lithic production is a dynamic process where discrete
methods can be blurred with features varying along the process. An
intermediate knapping method between discoidal and Levallois is commonly
referred under an umbrella of terms, presenting a wide geographical and
chronological distribution along the Early and Middle Palaeolithic.
Since this intermediate knapping method presents features from both
discoidal and Levallois knapping methods, this raises the question of up
to what point flakes from the three knapping methods can be
differentiated between each other and the directionality of confusions.
An experimental assemblage of flakes detached from the three methods is
employed along with attribute analysis and Machine Learning models to
identify the knapping method from which flakes were detached. On a
general level results provide excellent/good ability to differentiate
between the three knapping when a Support Vector Machine with polynomial
kernel is employed. Results also outline the singularity of flakes
detached from Levallois reduction sequences with an outstanding value of
identification, and being rare that they are erroneously attributed to
any of the other two knapping methods. Confusion between discoidal and
Hierarchical Discoid products is more common, although an excellent/good
value of identification is achieved for discoidal flakes and an
acceptable/fair value is achieved in the case of Hierarchical Discoid
flakes. This shows the potential applicability of machine learning
models in combination with attribute analysis for the identification of
these knapping methods among flakes.

**Keywords:** lithic technology; experimental archaeology; Levallois;
Discoid; Machine Learning

## 1. Introduction

The Middle Paleolithic in Western Europe is characterized by the
increase and diversification of prepared core knapping methods,
resulting in flake-dominated assemblages ([Kuhn,
2013](#ref-kuhn_roots_2013)). These flake dominated assemblages are the
result of a wide number of production methods which includes Levallois
([Boëda, 1995a](#ref-dibble_levallois:_1995),
[1994](#ref-boeda_concept_1994); [Boëda et al.,
1990](#ref-boeda_identification_1990)), Discoid ([Boëda,
1995b](#ref-boeda_caracteristiques_1995),
[1993](#ref-boeda_debitage_1993)), SSDA ([Forestier,
1993](#ref-forestier_clactonien:_1993); [Ohel et al.,
1979](#ref-ohel_clactonian_1979)), Quina ([Bourguignon,
1997](#ref-bourguignon_mousterien_1997),
[1996](#ref-bourguignon_conception_1996)), different laminar production
systems ([Boëda, 1990](#ref-farizy_surface_1990); [Révillon and
Tuffreau, 1994](#ref-revillon_les_1994)), Kombewa ([Newcomer and
Hivernel-Guerre, 1974](#ref-newcomer_nucleus_1974); [Tixier and Turq,
1999](#ref-tixier_kombewa_1999)) among several others. The abundance of
different production methods results in a highly diversified material
culture were flakes present a wide morphological variability. Flakes
often retain morphologies and attributes characteristic of the knapping
method from which they were detached, allowing for its identification.
However, flakes often present overlapping attributes and morphologies as
a result of the high internal variability of the methods and the ability
for obtaining flakes with similar functional properties through
different methods [Kuhn](#ref-kuhn_roots_2013)
([2013](#ref-kuhn_roots_2013)). Due to their wide geographical and
chronological extension, Levallois and Discoid constitute an important
source of cultural variability of the Middle Paleolithic from Western
Europe.

Boëda ([1995a](#ref-dibble_levallois:_1995),
[1994](#ref-boeda_concept_1994)) establishes six characteristics
defining the Levallois knapping strategy from a technological point of
view:

1.  The volume of the core is conceived in two convex asymmetric
    surfaces.  
2.  These two surfaces are hierarchical and are not interchangeable.
    They maintain their role of striking and debitage (or exploitation)
    surface respectively along the whole reduction process.  
3.  The distal and lateral convexities of the debitage surface are
    maintained to obtain predetermined flakes.  
4.  The plane of fracture of the predetermined products is parallel to
    the intersection between both surfaces.  
5.  The striking platform is perpendicular to the overhang (the core
    edge, at the intersection between the two core surfaces).  
6.  The technique employed during the knapping process is the direct
    percussion with hard hammer.  

-   Depending on the organization of the debitage surface Levallois
    cores are usually classified into preferential method (were a single
    predetermined Levallois flake is obtained from the debitage surface)
    or recurrent methods (were several predetermined flakes are produced
    from the debitage surface) with removals being either
    unidirectional, bidirectional or centripetal ([Boëda,
    1995a](#ref-dibble_levallois:_1995); [Boëda et al.,
    1990](#ref-boeda_identification_1990); [Delagnes,
    1995](#ref-dibble_variability_1995); [Delagnes and Meignen,
    2006](#ref-hovers_diversity_2006)).

Because of its early recognition in the XIX century ([Boucher de
Perthes, 1857](#ref-boucher_de_perthes_antiquites_1857)), its
association with cognitive abilities of planning and predetermination
([Boëda, 1994](#ref-boeda_concept_1994); [Pelegrin,
2009](#ref-pelegrin_cognition_2009)), and its use for the definition of
cultural facies ([Bordes, 1961a](#ref-bordes_mousterian_1961),
[1961b](#ref-bordes_typologie_1961)) and lithic technocomplexes
([Delagnes et al., 2007](#ref-vandermeersch_les_2007); [Faivre et al.,
2017](#ref-faivre_late_2017)), the Levallois flaking technology is
considered a trademark of the Middle Paleolithic. Levallois is clearly
identified from MIS8 onwards covering a wide geographical distribution
throughout Western Europe. The long geographical and temporary span of
Levallois adds additional layers of variability which can result from
raw material constraints, synchronic variability as a result of
different site functionality, chronological trends in development of
methods or shifts in the technological organization of groups. Attention
is also called on the explicit recognition of Levallois cores after MIS
8, while a multitude of terms is employed to define previous
hierarchical knapping strategies and its possible coexistence with
Acheulean technocomplexes ([Moncel et al.,
2020](#ref-moncel_early_2020); [Santonja et al.,
2016](#ref-santonja_coexistence_2016)).

Boëda ([1995b](#ref-boeda_caracteristiques_1995),
[1994](#ref-boeda_concept_1994), [1993](#ref-boeda_debitage_1993)), also
establishes six technological criteria defining the Discoid method:

1.  The volume of the core is conceived as two oblique asymmetric convex
    surfaces delimited by an intersection plane.  
2.  These two surfaces are not hierarchical being possible to alternate
    the roles of percussion and exploitation surfaces.  
3.  The peripheral convexity of the debitage surface is managed to
    control lateral and distal extractions thus allowing for a degree of
    predetermination  
4.  Striking surfaces are oriented in a way that the core edge is
    perpendicular to the predetermined products  
5.  The planes of extraction of the products are secant  
6.  The technique employed is the direct percussion with hard hammer.

Technological analysis of Middle Paleolithic assemblages has gradually
led to identify a variability of modalities within the discoidal core
knapping ([Bourguignon and Turq, 2003](#ref-peresani_chaine_2003);
[Locht, 2003](#ref-peresani_industrie_2003),
[2003](#ref-peresani_industrie_2003); [Terradas,
2003](#ref-terradas_discoid_2003)). This has resulted in *sensu stricto*
and a *sensu lato* conceptualizations of the Discoid knapping system
([Faivre et al., 2017](#ref-faivre_late_2017); [Mourre,
2003](#ref-peresani_discoiou_2003); [Thiébaut,
2013](#ref-thiebaut_discoid_2013)). The *sensu stricto* highly
corresponds to Boëda’s ([1993](#ref-boeda_debitage_1993)) above
mentioned definition, where core edge flakes and pseudo-Levallois points
are the most common products. *The sensu lato* Discoid encompasses a
larger range of products (although centripetal flakes are more common)
as a result of higher variability in the organization of percussion and
exploitation surfaces ([Terradas, 2003](#ref-terradas_discoid_2003)).

One of the variants from the Discoid *sensu lato* conceptualization
resembles Levallois knapping strategy (Figure 1). Some common
characteristics outlined for this method are:  
1) The core volume is conceived as two hierarchical asymmetric surfaces:
the percussion surface and the exploitation surface (this is a common
feature with Levallois).  
2) Preparation of the percussion surface is absent or it is partial,
without encompassing the complete periphery of the core. This can be a
result of raw material characteristics presenting an adequate morphology
or because it is achieved with minimal preparation.  
3) Despite the hierarchical nature of both surfaces flakes detached from
the debitage surface present a secant relationship towards the plane of
intersection. Soriano and Villa ([2017](#ref-soriano_early_2017)) call
attention that Levallois products usually present an external platform
angle (EPA) between 80º and 85º, while products from non-Levallois
hierarchical methods present an EPA relationship between 70 and 85º.
However, this relationship can change along the core’s reduction with
final flakes being sub-parallel to the plane of fracture ([Slimak,
1998](#ref-slimak_variabilite_1998)).  
4) Products from Hierarchical Discoid are usually symmetrical towards
the knapping direction, are thin, and the ventral and dorsal surfaces
present a subparallel relation. Again, these are common traits with
Levallois products.

![Schematic representation of the knapping methods, surfaces and
platform preparation](Article%20Figures/Variability%20L%20D%20HD.png)

Strategies from several sites can be considered to fit the above
mentioned variation of Discoid knapping method and its resemblance to
the Levallois method has been previously noted for several Middle and
Early Middle Paleolithic assemblages ([Casanova i Martí et al.,
2009](#ref-casanova_i_marti_strategies_2009);
[2014](#ref-casanova_debitage_2014); [Jaubert,
1993](#ref-jaubert_gisement_1993); [Peresani,
1998](#ref-peresani_variabilite_1998); [2003](#ref-peresani_les_2003),
[1998](#ref-slimak_variabilite_1998); [Soriano and Villa,
2017](#ref-soriano_early_2017)). However, it is important to consider
that given the wide geographical and chronological span (Figure 2),
different terms are employed. For Middle Paleolithic sites, the identity
of this method usually focuses on the shared features with Levallois and
Discoid and thus, its intermediate nature.

Jaubert ([1993](#ref-jaubert_gisement_1993)) at Mauran notes the
hierarchical nature of the production system and its resemblance to
exhausted recurrent centripetal Levallois cores. However, he points out
the secant planes of detachment not so parallel as Levallois as a
differentiation. Slimak ([2003](#ref-peresani_les_2003),
[1998](#ref-slimak_variabilite_1998)) at Champ Grand also notes the
similarities of residual cores with recurrent centripetal Levallois
debitage. Casanova i Martí et al.
([2009](#ref-casanova_i_marti_strategies_2009);
[2014](#ref-casanova_debitage_2014)) ) notes for Estret de Tragó the
presence of products and knapping methods which share features of
Levallois and Discoid, and proposes to include Hierarchical Discoid and
Levallois recurrent centripetal strategies into the Hierarchical
bifacial centripetal class. Peresani
([1998](#ref-peresani_variabilite_1998)) for Fumane cave notes the
presence of debitage products with features (reduced thickness, debitage
angle, and centripetal organization of scars also subparallel to the
ventral surface) which would correspond to parallel planes debitage.
Baena et al., ([2005](#ref-montes_barquin_paleoecologiy_2005)) indicate
the presence of hierarchical Discoid along the sequence of Esquilleu
cave as secondary and primary knapping method.

![Distribution of sites referenced in the text base map obtained from:
<https://maps-for-free.com/>)](Article%20Figures/Mapa.png)

As previously mentioned, for Middle Paleolithic sites, the identity of
this knapping method is focused on its intermediate nature between
Discoid and recurrent centripetal Levallois. However, Early Middle
Paleolithic sites usually focus its identity in the shared features with
Levallois as preceding the gradual emergence of the later. For example,
[Carmignani et al.](#ref-carmignani_technological_2017)
([2017](#ref-carmignani_technological_2017)) for Payre and Bau de
l’Aubesier use the term centripetal with parallel planes noting the
resemblance of features with Levallois. [Soriano and
Villa](#ref-soriano_early_2017) ([2017](#ref-soriano_early_2017)) for
Guado San Nicola use the term non-Levallois debitage with hierarchized
surfaces noting its similarity with Levallois but also its
distinctiveness due to the absence of convexity preparation/management
and platform preparation. For Cuesta de la Bajada [Santonja et
al.](#ref-santonja_coexistence_2016)
([2016](#ref-santonja_coexistence_2016)) differentiate between Levallois
cores and cores of centripetal character with preferential surfaces
(which are simply referred as centripetal). [Lombera-Hermida et
al.](#ref-de_lombera-hermida_dawn_2020)
([2020](#ref-de_lombera-hermida_dawn_2020)) cite the presence of
predetermined hierarchical centripetal cores in different raw materials
for TD10.1 at Atapuerca and note their difference and coexistence with
classical discoidal and Levallois knapping methods.

The technological criteria for identifying production systems are highly
visible on cores. However, a high degree of uncertainty remains in
flakes since these technological criteria are less visible or they are
absent ([Hovers, 2009](#ref-hovers_lithic_2009)). Another underlying
cause is the fluid and continuous nature of lithic knapping and
reduction which can blur differences between apparent clear cut methods.
Additionally, variations can result from adaptations to raw material
(different knapping methods applied to different raw materials in a same
archaeological level), raw material initial morphology, knappers
expertise and learning process, or circumstantial events and
restrictions. This adds up to an absence of discrete categories that are
blurred by the underlying existence of a wide variety of lithic
expressions. Attributing flakes to a knapping method usually remains a
result of observed features compared with experimental collections,
context given from knapping methods observed in the cores of the
assemblage (although cores in an assemblage do not necessarily represent
all knapping methods), and where the experience of the analyst has an
important weight ([Hovers, 2009](#ref-hovers_lithic_2009); [Perpère,
1986](#ref-perpere_apport_1986)). [Perpère](#ref-perpere_les_1989)
([1989](#ref-perpere_les_1989)); -[Perpère](#ref-perpere_apport_1986)
([1986](#ref-perpere_apport_1986))

``` r
library(tidyverse)
```

``` r
# Load the data
load("Data/Data.RData")
```

``` r
# Head the data
knitr::kable(ML_Data[1:10,])
```

| Artifact_ID | Core       | Class | Knapping_Phase  | Frag_Cat | Complete | Length | Width | Laminar_Index | MeanThick | Max_Thick | CarenIndex | Surf_Area | Surf_Thick | Angle_Lat_Marg |   SDThick |   CVThick | Weight | Curvature | Surface.Plat | Plat_Depth | Plat_Width | FlakeSurf_Plat | Plat_Prof | Plat_Prep | Cortex | Cortex_Loc | No_Scars | Long_Ridges | Termination_type | Trans_Section          | Flake_Type   | EPA | IPA | X_W\_rat |     IL_PS | Surf_ProxW |
|:------------|:-----------|:------|:----------------|:---------|:---------|-------:|------:|--------------:|----------:|----------:|-----------:|----------:|-----------:|---------------:|----------:|----------:|-------:|----------:|-------------:|-----------:|-----------:|---------------:|:----------|:----------|-------:|-----------:|---------:|------------:|:-----------------|:-----------------------|:-------------|----:|----:|---------:|----------:|-----------:|
| Disc_08_01  | Discoid_08 | D     | Full Production | C        | Y        |   40.4 |  31.4 |     1.2866242 |  4.666667 |       7.1 |   4.422535 |   1268.56 |  271.83429 |     -15.432218 | 1.8263503 | 0.3913608 |   7.20 |  175.6010 |       7.6800 |        2.4 |        6.4 |     165.177083 | RT        | L         |      5 |          5 |        2 |           0 | Feather          | Trapezoidal_Asymmetric | Backed Flake |  76 | 120 | 3.140625 | 0.1675292 |  2.6171875 |
| Disc_08_02  | Discoid_08 | D     | Full Production | C        | Y        |   42.2 |  41.6 |     1.0144231 | 10.666667 |      13.0 |   3.200000 |   1755.52 |  164.58000 |       8.618919 | 2.3213980 | 0.2176311 |  23.03 |  174.8621 |     316.0000 |        7.9 |       40.0 |       5.555443 | CX        | L         |      5 |          5 |        3 |           0 | Feather          | Triangular             | Flake        |  77 | 119 | 1.027500 | 0.0032102 |  0.1300633 |
| Disc_08_03  | Discoid_08 | D     | Full Production | C        | Y        |   28.9 |  38.5 |     0.7506494 |  9.166667 |      12.7 |   2.275591 |   1112.65 |  121.38000 |       1.432320 | 2.8581268 | 0.3117957 |  11.82 |  180.0000 |     210.6250 |       12.5 |       33.7 |       5.282611 | BF        | D         |      5 |          5 |        3 |           0 | Feather          | Trapezoidal            | Flake        |  54 | 112 | 1.035608 | 0.0035639 |  0.1656973 |
| Disc_08_04  | Discoid_08 | D     | Full Production | C        | Y        |   58.6 |  39.4 |     1.4873096 | 11.966667 |      16.6 |   2.373494 |   2308.84 |  192.93928 |      -5.958859 | 4.1152832 | 0.3438955 |  23.87 |  173.7362 |      33.0600 |        5.7 |       11.6 |      69.837870 | CX        | L         |      5 |          5 |        4 |           0 | Feather          | Triangular             | Flake        |  60 | 114 | 2.094828 | 0.0449882 |  0.7350272 |
| Disc_08_05  | Discoid_08 | D     | Full Production | C        | Y        |   41.0 |  35.1 |     1.1680912 | 11.333333 |      15.4 |   2.279221 |   1439.10 |  126.97941 |      10.125487 | 3.5264083 | 0.3111537 |  14.04 |  177.7746 |      60.8000 |        4.0 |       15.2 |      23.669408 | RT        | L         |      5 |          5 |        3 |           0 | Feather          | Triangular_Asymmetric  | Backed Flake |  56 | 115 | 1.993421 | 0.0192120 |  0.4983553 |
| Disc_08_06  | Discoid_08 | D     | Full Production | C        | Y        |   40.2 |  28.0 |     1.4357143 | 11.933333 |      13.5 |   2.074074 |   1125.60 |   94.32402 |       3.893609 | 1.7441967 | 0.1461617 |  10.27 |  176.4807 |      38.7200 |        6.4 |       12.1 |      29.070248 | RT        | L         |      5 |          5 |        3 |           0 | Feather          | Triangular_Asymmetric  | Backed Flake |  83 |  98 | 1.685950 | 0.0370794 |  0.5268595 |
| Disc_08_07  | Discoid_08 | D     | Full Production | C        | Y        |   36.8 |  30.7 |     1.1986971 |  8.400000 |      10.5 |   2.923809 |   1129.76 |  134.49524 |      -0.155695 | 2.2375582 | 0.2663760 |   9.82 |  168.1249 |      35.0900 |        5.8 |       12.1 |      32.196067 | RT        | L         |      5 |          5 |        2 |           0 | Feather          | Triangular_Asymmetric  | Backed Flake |  75 | 120 | 2.314050 | 0.0341606 |  0.7979481 |
| Disc_08_08  | Discoid_08 | D     | Full Production | C        | Y        |   41.7 |  28.4 |     1.4683099 |  6.933333 |       9.3 |   3.053763 |   1184.28 |  170.80962 |       8.229818 | 1.9601587 | 0.2827152 |   9.74 |  178.3511 |     109.5159 |        8.3 |       16.8 |      10.813770 | CC        | L         |      4 |          2 |        2 |           2 | Feather          | Triangular             | Flake        |  70 | 105 | 1.678571 | 0.0134073 |  0.2574968 |
| Disc_08_09  | Discoid_08 | D     | Full Production | C        | Y        |   46.7 |  27.8 |     1.6798561 |  6.666667 |       7.1 |   3.915493 |   1298.26 |  194.73900 |       7.106838 | 0.6128259 | 0.0919239 |  10.28 |  170.6550 |      64.6100 |        7.1 |       18.2 |      20.093794 | CX        | L         |      5 |          5 |        2 |           0 | Feather          | Triangular_Asymmetric  | Backed Flake |  85 |  91 | 1.527473 | 0.0259999 |  0.4302740 |
| Disc_08_10  | Discoid_08 | D     | Full Production | C        | Y        |   49.2 |  23.1 |     2.1298701 |  7.733333 |      10.1 |   2.287129 |   1136.52 |  146.96379 |      -2.677974 | 2.2005050 | 0.2845481 |   8.65 |  170.6630 |      49.5800 |        7.4 |       13.4 |      22.922953 | RT        | L         |      5 |          5 |        3 |           0 | Feather          | Triangular             | Flake        |  77 | 110 | 1.358209 | 0.0429583 |  0.3670835 |

## 2. Methods

The present study uses attribute analysis on an experimental assemblage
of flakes detached from Levallois, discoidal and Hierarchical Discoid
reduction sequences. Supervised Machine Learning models are trained on
the resulting dataset to identify the knapping method from which each
flake was detached.

### 2.1 Experimental assemblage

The experimental assemblage consists of 222 experimentally knapped
flakes belonging to Levallois, Discoid and Hierarchical Discoid
reduction sequences. The experimental assemblage was knapped by two of
the authors (JB and GBP). One of the authors (JB) is considered a high
level expert while the second (GBP) is considered an intermediate-high
knapper.

## References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-montes_barquin_paleoecologiy_2005" class="csl-entry">

Baena, J., Carrión, E., Ruiz, B., Ellwood, B., Sesé, C., Yravedra, J.,
Jordá, J., Uzquiano, P., Velázquez, R., Manzano, I., Sanchez-Marco, A.,
Hernández, F., 2005. Paleoecología y comportamiento humano durante el
Pleistoceno Superior en la comarca de Liébana: La secuencia de la Cueva
de El Esquilleu (Occidente de Cantabria, España), in: Montes Barquín, R.
(Ed.), Neandertales Cantábricos. Estado de La Cuestión, Monografías.
Museo de Altamira, Santander, pp. 461–487.

</div>

<div id="ref-dibble_levallois:_1995" class="csl-entry">

Boëda, E., 1995a. Levallois: A Volumetric Construction, Methods, A
Technique, in: Dibble, H.L., Bar-Yosef, O. (Eds.), The Definition and
Interpretation of Levallois Technology, Monographs in World Archaeology.
Prehistory Press, Madison, Wisconsin, pp. 41–68.

</div>

<div id="ref-boeda_caracteristiques_1995" class="csl-entry">

Boëda, E., 1995b. Caractéristiques techniques des chaînes opératoires
lithiques des niveaux micoquiens de Külna (Tchécoslovaquie). Paléo 1,
57–72. <https://doi.org/10.3406/pal.1995.1380>

</div>

<div id="ref-boeda_concept_1994" class="csl-entry">

Boëda, E., 1994. Le concept Levallois: Variabilité des méthodes, CNRS
éditions. CNRS.

</div>

<div id="ref-boeda_debitage_1993" class="csl-entry">

Boëda, E., 1993. Le débitage discoïde et le débitage Levallois récurrent
centripède. Bulletin de la Société Préhistorique Française 90, 392–404.
<https://doi.org/10.3406/bspf.1993.9669>

</div>

<div id="ref-farizy_surface_1990" class="csl-entry">

Boëda, E., 1990. De la surface au volume. Analyse des concetions des
débitages Levallois et laminaire, in: Farizy, C. (Ed.), Paleolithique
Moyen Recent Et Paleolithique Superieur Ancien En Europe. Ruptures Et
Transitions: Examen Critique Des Documents Archéologiques, Mémoires Du
Musée de Préhistoire d’Ile-de-France. A.P.R.A.I.F., Nemours, pp. 63–68.

</div>

<div id="ref-boeda_identification_1990" class="csl-entry">

Boëda, E., Geneste, J.-M., Meignen, L., 1990. Identification de chaînes
opératoires lithiques du Paléolithique ancien et moyen. Paléo 2, 43–80.

</div>

<div id="ref-bordes_mousterian_1961" class="csl-entry">

Bordes, F., 1961a. Mousterian Cultures in France. Science 134, 803–810.

</div>

<div id="ref-bordes_typologie_1961" class="csl-entry">

Bordes, F., 1961b. Typologie du Paléolithique ancien et moyen,
Publications de l’institut de préhistoire de l’université de Bordeaux.
CNRS Editions, Bordeaux.

</div>

<div id="ref-boucher_de_perthes_antiquites_1857" class="csl-entry">

Boucher de Perthes, J., 1857. Antiquités celtiques et antédiluviennes
II. Treuttel et Wurtz, Paris, France.

</div>

<div id="ref-bourguignon_mousterien_1997" class="csl-entry">

Bourguignon, L., 1997. Le Moustérien de type Quina: Nouvelle Définition
d’une entité technique (PhD thesis). Université de Paris X - Nanterre,
Nanterre.

</div>

<div id="ref-bourguignon_conception_1996" class="csl-entry">

Bourguignon, L., 1996. La conception du debitage Quina. Quaternaria Nova
6, 149–166.

</div>

<div id="ref-peresani_chaine_2003" class="csl-entry">

Bourguignon, L., Turq, A., 2003. Une chaîne opératoire de débitage
discoïde sur éclat du Moustérien à denticulés aquitain: Les exemples de
Champ Bossuet et de Combre Grenal c.14, in: Peresani, M. (Ed.), Discoid
Lithic Technology. Advances and Implications, BAR International Series.
Oxford, pp. 131–152.

</div>

<div id="ref-carmignani_technological_2017" class="csl-entry">

Carmignani, L., Moncel, M.-H., Fernandes, P., Wilson, L., 2017.
Technological variability during the Early Middle Palaeolithic in
Western Europe. Reduction systems and predetermined products at the Bau
de l’Aubesier and Payre (South-East France). PLoS ONE 12, e0178550.
<https://doi.org/10.1371/journal.pone.0178550>

</div>

<div id="ref-casanova_i_marti_strategies_2009" class="csl-entry">

Casanova i Martí, J., Martínez Moreno, J., Mora Torcal, R., Torre, I. de
la, 2009. Stratégies techniques dans le Paléolithique Moyen du sud-est
des Pyrénées. L’Anthropologie 113, 313–340.
<https://doi.org/10.1016/j.anthro.2009.04.004>

</div>

<div id="ref-casanova_debitage_2014" class="csl-entry">

Casanova, J., Roda Gilabert, X., Martínez-Moreno, J., Mora, R., 2014.
Débitage, façonnage et diversité des systèmes techniques du Moustérien à
Tragó (Pré-Pyrénées de Lleida, Catalogne), in: Jaubert, J., Fourment,
N., Depaepe, P. (Eds.), Transitions, Ruptures Et Continuité En
Préhistoire. Société Préhistorique Française, Paris, pp. 139–154.

</div>

<div id="ref-dibble_variability_1995" class="csl-entry">

Delagnes, A., 1995. Variability within Uniformity: Three Levels of
Variability within the Levallois System, in: Dibble, H.L., Bar-Yosef, O.
(Eds.), The Definition and Interpretation of Levallois Technology,
Monographs in World Archaeology. Prehistory Press, Madison, Wisconsin,
pp. 201–211.

</div>

<div id="ref-vandermeersch_les_2007" class="csl-entry">

Delagnes, A., Jaubert, J., Meignen, L., 2007. Les technocomplexes du
paléolithique moyen en Europe occidentale dans leur cadre diachronique
et géographique, in: Vandermeersch, B., Maureille, B. (Eds.), Les
Neandertaliens. Biologie Et Cultures, Documents Préhistoriques. Editions
du Comité des Travaux Historiques et Scientifiques, Paris, pp. 213–229.

</div>

<div id="ref-hovers_diversity_2006" class="csl-entry">

Delagnes, A., Meignen, L., 2006. Diversity of Lithic Production Systems
During the Middle Paleolithic in France. Are There Any Chronological
Trends?, in: Hovers, E., Kuhn, S.L., Jochim, M. (Eds.), Transitions
Before the Transition Evolution and Stability in the Middle Paleolithic
and Middle Stone Age. Springer, pp. 85–107.

</div>

<div id="ref-faivre_late_2017" class="csl-entry">

Faivre, G.-P., Gravina, B., Bourguignon, L., Discamps, E., Turq, A.,
2017. Late Middle Palaeolithic lithic technocomplexes (MIS 5-3) in the
northeastern Aquitaine Basin: Advances and challenges. Quaternary
International 433, 116–131.
<https://doi.org/10.1016/j.quaint.2016.02.060>

</div>

<div id="ref-forestier_clactonien:_1993" class="csl-entry">

Forestier, H., 1993. Le Clactonien: Mise en application d’une nouvelle
méthode de débitage s’inscrivant dans la variabilité des systèmes de
production lithique du Paléolithique ancien. Paléo 5, 53–82.
<https://doi.org/10.3406/pal.1993.1104>

</div>

<div id="ref-hovers_lithic_2009" class="csl-entry">

Hovers, E., 2009. The lithic assemblages of Qafzeh Cave, Human
Evolutiion Series. Oxford University Press, New york.

</div>

<div id="ref-jaubert_gisement_1993" class="csl-entry">

Jaubert, J., 1993. Le gisement paléolithique moyen de Mauran
(Haute-Garonne) : Techno-économie des industries lithiques. Bulletin de
la Société préhistorique française 90, 328–335.
<https://doi.org/10.3406/bspf.1993.9642>

</div>

<div id="ref-kuhn_roots_2013" class="csl-entry">

Kuhn, S.L., 2013. Roots of the Middle Paleolithic in Eurasia. Current
Anthropology 54, S255–S268. <https://doi.org/10.1086/673529>

</div>

<div id="ref-peresani_industrie_2003" class="csl-entry">

Locht, J.-L., 2003. L’industrie lithique du gisement de Beauvais (Oise,
France): Objectifs et variabilité du débitage discoïde, in: Peresani, M.
(Ed.), Discoid Lithic Technology: Advances and Implications, BAR
International Series. Archaeopress, Oxford, pp. 193–209.

</div>

<div id="ref-de_lombera-hermida_dawn_2020" class="csl-entry">

Lombera-Hermida, A. de, Rodríguez-Álvarez, X.P., Mosquera, M., Ollé, A.,
García-Medrano, P., Pedergnana, A., Terradillos-Bernal, M.,
López-Ortega, E., Bargalló, A., Rodríguez-Hidalgo, A., Saladié, P.,
Bermúdez de Castro, J.M., Carbonell, E., 2020. The dawn of the Middle
Paleolithic in Atapuerca: The lithic assemblage of TD10.1 from Gran
Dolina. Journal of Human Evolution 145, 102812.
<https://doi.org/10.1016/j.jhevol.2020.102812>

</div>

<div id="ref-moncel_early_2020" class="csl-entry">

Moncel, M.-H., Ashton, N., Arzarello, M., Fontana, F., Lamotte, A.,
Scott, B., Muttillo, B., Berruti, G., Nenzioni, G., Tuffreau, A., 2020.
Early Levallois core technology between marine isotope stage 12 and 9 in
Western Europe. Journal of human evolution 139, 102735.
<https://doi.org/doi.org/10.1016/j.jhevol.2019.102735>

</div>

<div id="ref-peresani_discoiou_2003" class="csl-entry">

Mourre, V., 2003. Discoïde ou pas Discoïde? Réflexions sur la pertinence
des critères techniques définissant le débitage discoïde, in: Peresani,
M. (Ed.), Discoid Lithic Technology. Advances and Implications, BAR
International Series. Archaeopress, Oxford, pp. 1–17.

</div>

<div id="ref-newcomer_nucleus_1974" class="csl-entry">

Newcomer, M.H., Hivernel-Guerre, F., 1974. Nucléus sur éclat:
Technologie et utilisation par différentes cultures préhistoriques.
Bulletin de la Société Préhistorique Française 71, 119–128.
<https://doi.org/10.3406/bspf.1974.8308>

</div>

<div id="ref-ohel_clactonian_1979" class="csl-entry">

Ohel, M.Y., Bhattacharya, D.K., Bordes, F., Cahen, D., Callow, P.,
Collins, D., Katz, P.R., Narr, K.J., Newcomer, M.H., Pappu, R.S., Roe,
D.A., Singer, R., Wymer, J.J., 1979. The Clactonian: An Independent
Complex or an Integral Part of the Acheulean? \[And Comments and
Reply\]. Current Anthropology 20, 685–726.

</div>

<div id="ref-pelegrin_cognition_2009" class="csl-entry">

Pelegrin, J., 2009. Cognition and the emergence of language: A
contribution from lithic technology, in: Beaune, S.A. de, Coolidge,
F.L., Wynn, T. (Eds.), Cognitive Archaeology and Human Evolution.
Cambridge University Press, New York, pp. 95–108.

</div>

<div id="ref-peresani_variabilite_1998" class="csl-entry">

Peresani, M., 1998. La variabilité du débitage discoïde dans la grotte
de Fumane (Italie du Nord)/The variability of discoid production at the
grotte de Fumane. Paléo 10, 123–146.
<https://doi.org/10.3406/pal.1998.1133>

</div>

<div id="ref-perpere_les_1989" class="csl-entry">

Perpère, M., 1989. Les frontiéres du débitage Levallois: Typométrie des
éclats. L’Anthropologie 95, 837–850.

</div>

<div id="ref-perpere_apport_1986" class="csl-entry">

Perpère, M., 1986. Apport de la typométrie à la définition des éclats
Levallois : L’exemple d’Ault. Bulletin de la Société préhistorique
française 83, 115–118. <https://doi.org/10.3406/bspf.1986.8743>

</div>

<div id="ref-revillon_les_1994" class="csl-entry">

Révillon, S., Tuffreau, A. (Eds.), 1994. Les industries laminaires au
Paléolithique moyen, Dossier De Documentation Archéologique. CNRS
Editions, Paris.

</div>

<div id="ref-santonja_coexistence_2016" class="csl-entry">

Santonja, M., Pérez-González, A., Panera, J., Rubio-Jara, S.,
Méndez-Quintas, E., 2016. The coexistence of Acheulean and Ancient
Middle Palaeolithic techno-complexes in the Middle Pleistocene of the
Iberian Peninsula. Quaternary International 411, 367–377.

</div>

<div id="ref-peresani_les_2003" class="csl-entry">

Slimak, L., 2003. Les Debitages discoïdes mousteriens: Evaluation d’un
concept technologique, in: Peresani, M. (Ed.), Discoid Lithic
Technology. Advances and Implications, BAR International Series.
Archaeopress, Oxford, pp. 33–65.

</div>

<div id="ref-slimak_variabilite_1998" class="csl-entry">

Slimak, L., 1998. La variabilité des débitages discoïdes au
Paléolithique moyen: Diversité des méthodes et unité d’un concept.
L’exemple des gisements de la Baume Néron (Soyons, Ardèche) et du Champ
Grand (Saint-Maurice-sur-Loire, Loire). Préhistoire Anthropologie
Méditerranéennes 7, 75–88.

</div>

<div id="ref-soriano_early_2017" class="csl-entry">

Soriano, S., Villa, P., 2017. Early Levallois and the beginning of the
Middle Paleolithic in central Italy. PLOS ONE 12, e0186082.
<https://doi.org/10.1371/journal.pone.0186082>

</div>

<div id="ref-terradas_discoid_2003" class="csl-entry">

Terradas, X., 2003. Discoid flaking method: Conception and technological
variability, in: Peresani, M. (Ed.), Discoid Lithic Technology. Advances
and Implications, BAR International Series. Archaeopress, Oxford, pp.
19–32.

</div>

<div id="ref-thiebaut_discoid_2013" class="csl-entry">

Thiébaut, C., 2013. Discoid debitage stricto sensu: A method adapted to
highly mobile Middle Paleolithic groups? P@lethnology Varia.

</div>

<div id="ref-tixier_kombewa_1999" class="csl-entry">

Tixier, J., Turq, A., 1999. Kombewa et alii. Paléo 11, 135–143.
<https://doi.org/10.3406/pal.1999.1174>

</div>

</div>

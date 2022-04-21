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
exploitation surfaces ([Terradas](#ref-terradas_discoid_2003)
([2003](#ref-terradas_discoid_2003))).

    library(tidyverse)

    # Load the data
    load("Data/Data.RData")

    # Head the data
    knitr::kable(ML_Data[1:10,])

<table>
<colgroup>
<col style="width: 3%" />
<col style="width: 2%" />
<col style="width: 1%" />
<col style="width: 4%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 1%" />
<col style="width: 1%" />
<col style="width: 3%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 3%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 1%" />
<col style="width: 2%" />
<col style="width: 3%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 3%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 1%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 3%" />
<col style="width: 4%" />
<col style="width: 5%" />
<col style="width: 3%" />
<col style="width: 1%" />
<col style="width: 1%" />
<col style="width: 2%" />
<col style="width: 2%" />
<col style="width: 2%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Artifact_ID</th>
<th style="text-align: left;">Core</th>
<th style="text-align: left;">Class</th>
<th style="text-align: left;">Knapping_Phase</th>
<th style="text-align: left;">Frag_Cat</th>
<th style="text-align: left;">Complete</th>
<th style="text-align: right;">Length</th>
<th style="text-align: right;">Width</th>
<th style="text-align: right;">Laminar_Index</th>
<th style="text-align: right;">MeanThick</th>
<th style="text-align: right;">Max_Thick</th>
<th style="text-align: right;">CarenIndex</th>
<th style="text-align: right;">Surf_Area</th>
<th style="text-align: right;">Surf_Thick</th>
<th style="text-align: right;">Angle_Lat_Marg</th>
<th style="text-align: right;">SDThick</th>
<th style="text-align: right;">CVThick</th>
<th style="text-align: right;">Weight</th>
<th style="text-align: right;">Curvature</th>
<th style="text-align: right;">Surface.Plat</th>
<th style="text-align: right;">Plat_Depth</th>
<th style="text-align: right;">Plat_Width</th>
<th style="text-align: right;">FlakeSurf_Plat</th>
<th style="text-align: left;">Plat_Prof</th>
<th style="text-align: left;">Plat_Prep</th>
<th style="text-align: right;">Cortex</th>
<th style="text-align: right;">Cortex_Loc</th>
<th style="text-align: right;">No_Scars</th>
<th style="text-align: right;">Long_Ridges</th>
<th style="text-align: left;">Termination_type</th>
<th style="text-align: left;">Trans_Section</th>
<th style="text-align: left;">Flake_Type</th>
<th style="text-align: right;">EPA</th>
<th style="text-align: right;">IPA</th>
<th style="text-align: right;">X_W_rat</th>
<th style="text-align: right;">IL_PS</th>
<th style="text-align: right;">Surf_ProxW</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Disc_08_01</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">40.4</td>
<td style="text-align: right;">31.4</td>
<td style="text-align: right;">1.2866242</td>
<td style="text-align: right;">4.666667</td>
<td style="text-align: right;">7.1</td>
<td style="text-align: right;">4.422535</td>
<td style="text-align: right;">1268.56</td>
<td style="text-align: right;">271.83429</td>
<td style="text-align: right;">-15.432218</td>
<td style="text-align: right;">1.8263503</td>
<td style="text-align: right;">0.3913608</td>
<td style="text-align: right;">7.20</td>
<td style="text-align: right;">175.6010</td>
<td style="text-align: right;">7.6800</td>
<td style="text-align: right;">2.4</td>
<td style="text-align: right;">6.4</td>
<td style="text-align: right;">165.177083</td>
<td style="text-align: left;">RT</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">2</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Trapezoidal_Asymmetric</td>
<td style="text-align: left;">Backed Flake</td>
<td style="text-align: right;">76</td>
<td style="text-align: right;">120</td>
<td style="text-align: right;">3.140625</td>
<td style="text-align: right;">0.1675292</td>
<td style="text-align: right;">2.6171875</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_02</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">42.2</td>
<td style="text-align: right;">41.6</td>
<td style="text-align: right;">1.0144231</td>
<td style="text-align: right;">10.666667</td>
<td style="text-align: right;">13.0</td>
<td style="text-align: right;">3.200000</td>
<td style="text-align: right;">1755.52</td>
<td style="text-align: right;">164.58000</td>
<td style="text-align: right;">8.618919</td>
<td style="text-align: right;">2.3213980</td>
<td style="text-align: right;">0.2176311</td>
<td style="text-align: right;">23.03</td>
<td style="text-align: right;">174.8621</td>
<td style="text-align: right;">316.0000</td>
<td style="text-align: right;">7.9</td>
<td style="text-align: right;">40.0</td>
<td style="text-align: right;">5.555443</td>
<td style="text-align: left;">CX</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">3</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Triangular</td>
<td style="text-align: left;">Flake</td>
<td style="text-align: right;">77</td>
<td style="text-align: right;">119</td>
<td style="text-align: right;">1.027500</td>
<td style="text-align: right;">0.0032102</td>
<td style="text-align: right;">0.1300633</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_03</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">28.9</td>
<td style="text-align: right;">38.5</td>
<td style="text-align: right;">0.7506494</td>
<td style="text-align: right;">9.166667</td>
<td style="text-align: right;">12.7</td>
<td style="text-align: right;">2.275591</td>
<td style="text-align: right;">1112.65</td>
<td style="text-align: right;">121.38000</td>
<td style="text-align: right;">1.432320</td>
<td style="text-align: right;">2.8581268</td>
<td style="text-align: right;">0.3117957</td>
<td style="text-align: right;">11.82</td>
<td style="text-align: right;">180.0000</td>
<td style="text-align: right;">210.6250</td>
<td style="text-align: right;">12.5</td>
<td style="text-align: right;">33.7</td>
<td style="text-align: right;">5.282611</td>
<td style="text-align: left;">BF</td>
<td style="text-align: left;">D</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">3</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Trapezoidal</td>
<td style="text-align: left;">Flake</td>
<td style="text-align: right;">54</td>
<td style="text-align: right;">112</td>
<td style="text-align: right;">1.035608</td>
<td style="text-align: right;">0.0035639</td>
<td style="text-align: right;">0.1656973</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_04</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">58.6</td>
<td style="text-align: right;">39.4</td>
<td style="text-align: right;">1.4873096</td>
<td style="text-align: right;">11.966667</td>
<td style="text-align: right;">16.6</td>
<td style="text-align: right;">2.373494</td>
<td style="text-align: right;">2308.84</td>
<td style="text-align: right;">192.93928</td>
<td style="text-align: right;">-5.958859</td>
<td style="text-align: right;">4.1152832</td>
<td style="text-align: right;">0.3438955</td>
<td style="text-align: right;">23.87</td>
<td style="text-align: right;">173.7362</td>
<td style="text-align: right;">33.0600</td>
<td style="text-align: right;">5.7</td>
<td style="text-align: right;">11.6</td>
<td style="text-align: right;">69.837870</td>
<td style="text-align: left;">CX</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">4</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Triangular</td>
<td style="text-align: left;">Flake</td>
<td style="text-align: right;">60</td>
<td style="text-align: right;">114</td>
<td style="text-align: right;">2.094828</td>
<td style="text-align: right;">0.0449882</td>
<td style="text-align: right;">0.7350272</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_05</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">41.0</td>
<td style="text-align: right;">35.1</td>
<td style="text-align: right;">1.1680912</td>
<td style="text-align: right;">11.333333</td>
<td style="text-align: right;">15.4</td>
<td style="text-align: right;">2.279221</td>
<td style="text-align: right;">1439.10</td>
<td style="text-align: right;">126.97941</td>
<td style="text-align: right;">10.125487</td>
<td style="text-align: right;">3.5264083</td>
<td style="text-align: right;">0.3111537</td>
<td style="text-align: right;">14.04</td>
<td style="text-align: right;">177.7746</td>
<td style="text-align: right;">60.8000</td>
<td style="text-align: right;">4.0</td>
<td style="text-align: right;">15.2</td>
<td style="text-align: right;">23.669408</td>
<td style="text-align: left;">RT</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">3</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Triangular_Asymmetric</td>
<td style="text-align: left;">Backed Flake</td>
<td style="text-align: right;">56</td>
<td style="text-align: right;">115</td>
<td style="text-align: right;">1.993421</td>
<td style="text-align: right;">0.0192120</td>
<td style="text-align: right;">0.4983553</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_06</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">40.2</td>
<td style="text-align: right;">28.0</td>
<td style="text-align: right;">1.4357143</td>
<td style="text-align: right;">11.933333</td>
<td style="text-align: right;">13.5</td>
<td style="text-align: right;">2.074074</td>
<td style="text-align: right;">1125.60</td>
<td style="text-align: right;">94.32402</td>
<td style="text-align: right;">3.893609</td>
<td style="text-align: right;">1.7441967</td>
<td style="text-align: right;">0.1461617</td>
<td style="text-align: right;">10.27</td>
<td style="text-align: right;">176.4807</td>
<td style="text-align: right;">38.7200</td>
<td style="text-align: right;">6.4</td>
<td style="text-align: right;">12.1</td>
<td style="text-align: right;">29.070248</td>
<td style="text-align: left;">RT</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">3</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Triangular_Asymmetric</td>
<td style="text-align: left;">Backed Flake</td>
<td style="text-align: right;">83</td>
<td style="text-align: right;">98</td>
<td style="text-align: right;">1.685950</td>
<td style="text-align: right;">0.0370794</td>
<td style="text-align: right;">0.5268595</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_07</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">36.8</td>
<td style="text-align: right;">30.7</td>
<td style="text-align: right;">1.1986971</td>
<td style="text-align: right;">8.400000</td>
<td style="text-align: right;">10.5</td>
<td style="text-align: right;">2.923809</td>
<td style="text-align: right;">1129.76</td>
<td style="text-align: right;">134.49524</td>
<td style="text-align: right;">-0.155695</td>
<td style="text-align: right;">2.2375582</td>
<td style="text-align: right;">0.2663760</td>
<td style="text-align: right;">9.82</td>
<td style="text-align: right;">168.1249</td>
<td style="text-align: right;">35.0900</td>
<td style="text-align: right;">5.8</td>
<td style="text-align: right;">12.1</td>
<td style="text-align: right;">32.196067</td>
<td style="text-align: left;">RT</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">2</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Triangular_Asymmetric</td>
<td style="text-align: left;">Backed Flake</td>
<td style="text-align: right;">75</td>
<td style="text-align: right;">120</td>
<td style="text-align: right;">2.314050</td>
<td style="text-align: right;">0.0341606</td>
<td style="text-align: right;">0.7979481</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_08</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">41.7</td>
<td style="text-align: right;">28.4</td>
<td style="text-align: right;">1.4683099</td>
<td style="text-align: right;">6.933333</td>
<td style="text-align: right;">9.3</td>
<td style="text-align: right;">3.053763</td>
<td style="text-align: right;">1184.28</td>
<td style="text-align: right;">170.80962</td>
<td style="text-align: right;">8.229818</td>
<td style="text-align: right;">1.9601587</td>
<td style="text-align: right;">0.2827152</td>
<td style="text-align: right;">9.74</td>
<td style="text-align: right;">178.3511</td>
<td style="text-align: right;">109.5159</td>
<td style="text-align: right;">8.3</td>
<td style="text-align: right;">16.8</td>
<td style="text-align: right;">10.813770</td>
<td style="text-align: left;">CC</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">4</td>
<td style="text-align: right;">2</td>
<td style="text-align: right;">2</td>
<td style="text-align: right;">2</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Triangular</td>
<td style="text-align: left;">Flake</td>
<td style="text-align: right;">70</td>
<td style="text-align: right;">105</td>
<td style="text-align: right;">1.678571</td>
<td style="text-align: right;">0.0134073</td>
<td style="text-align: right;">0.2574968</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_09</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.7</td>
<td style="text-align: right;">27.8</td>
<td style="text-align: right;">1.6798561</td>
<td style="text-align: right;">6.666667</td>
<td style="text-align: right;">7.1</td>
<td style="text-align: right;">3.915493</td>
<td style="text-align: right;">1298.26</td>
<td style="text-align: right;">194.73900</td>
<td style="text-align: right;">7.106838</td>
<td style="text-align: right;">0.6128259</td>
<td style="text-align: right;">0.0919239</td>
<td style="text-align: right;">10.28</td>
<td style="text-align: right;">170.6550</td>
<td style="text-align: right;">64.6100</td>
<td style="text-align: right;">7.1</td>
<td style="text-align: right;">18.2</td>
<td style="text-align: right;">20.093794</td>
<td style="text-align: left;">CX</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">2</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Triangular_Asymmetric</td>
<td style="text-align: left;">Backed Flake</td>
<td style="text-align: right;">85</td>
<td style="text-align: right;">91</td>
<td style="text-align: right;">1.527473</td>
<td style="text-align: right;">0.0259999</td>
<td style="text-align: right;">0.4302740</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_10</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">49.2</td>
<td style="text-align: right;">23.1</td>
<td style="text-align: right;">2.1298701</td>
<td style="text-align: right;">7.733333</td>
<td style="text-align: right;">10.1</td>
<td style="text-align: right;">2.287129</td>
<td style="text-align: right;">1136.52</td>
<td style="text-align: right;">146.96379</td>
<td style="text-align: right;">-2.677974</td>
<td style="text-align: right;">2.2005050</td>
<td style="text-align: right;">0.2845481</td>
<td style="text-align: right;">8.65</td>
<td style="text-align: right;">170.6630</td>
<td style="text-align: right;">49.5800</td>
<td style="text-align: right;">7.4</td>
<td style="text-align: right;">13.4</td>
<td style="text-align: right;">22.922953</td>
<td style="text-align: left;">RT</td>
<td style="text-align: left;">L</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">5</td>
<td style="text-align: right;">3</td>
<td style="text-align: right;">0</td>
<td style="text-align: left;">Feather</td>
<td style="text-align: left;">Triangular</td>
<td style="text-align: left;">Flake</td>
<td style="text-align: right;">77</td>
<td style="text-align: right;">110</td>
<td style="text-align: right;">1.358209</td>
<td style="text-align: right;">0.0429583</td>
<td style="text-align: right;">0.3670835</td>
</tr>
</tbody>
</table>

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

Boëda, E., 1995a. Levallois: A Volumetric Construction, Methods, A
Technique, in: Dibble, H.L., Bar-Yosef, O. (Eds.), The Definition and
Interpretation of Levallois Technology, Monographs in World Archaeology.
Prehistory Press, Madison, Wisconsin, pp. 41–68.

Boëda, E., 1995b. Caractéristiques techniques des chaînes opératoires
lithiques des niveaux micoquiens de Külna (Tchécoslovaquie). Paléo 1,
57–72. <https://doi.org/10.3406/pal.1995.1380>

Boëda, E., 1994. Le concept Levallois: Variabilité des méthodes, CNRS
éditions. CNRS.

Boëda, E., 1993. Le débitage discoïde et le débitage Levallois récurrent
centripède. Bulletin de la Société Préhistorique Française 90, 392–404.
<https://doi.org/10.3406/bspf.1993.9669>

Boëda, E., 1990. De la surface au volume. Analyse des concetions des
débitages Levallois et laminaire, in: Farizy, C. (Ed.), Paleolithique
Moyen Recent Et Paleolithique Superieur Ancien En Europe. Ruptures Et
Transitions: Examen Critique Des Documents Archéologiques, Mémoires Du
Musée de Préhistoire d’Ile-de-France. A.P.R.A.I.F., Nemours, pp. 63–68.

Boëda, E., Geneste, J.-M., Meignen, L., 1990. Identification de chaînes
opératoires lithiques du Paléolithique ancien et moyen. Paléo 2, 43–80.

Bordes, F., 1961a. Mousterian Cultures in France. Science 134, 803–810.

Bordes, F., 1961b. Typologie du Paléolithique ancien et moyen,
Publications de l’institut de préhistoire de l’université de Bordeaux.
CNRS Editions, Bordeaux.

Boucher de Perthes, J., 1857. Antiquités celtiques et antédiluviennes
II. Treuttel et Wurtz, Paris, France.

Bourguignon, L., 1997. Le Moustérien de type Quina: Nouvelle Définition
d’une entité technique (PhD thesis). Université de Paris X - Nanterre,
Nanterre.

Bourguignon, L., 1996. La conception du debitage Quina. Quaternaria Nova
6, 149–166.

Bourguignon, L., Turq, A., 2003. Une chaîne opératoire de débitage
discoïde sur éclat du Moustérien à denticulés aquitain: Les exemples de
Champ Bossuet et de Combre Grenal c.14, in: Peresani, M. (Ed.), Discoid
Lithic Technology. Advances and Implications, BAR International Series.
Oxford, pp. 131–152.

Delagnes, A., 1995. Variability within Uniformity: Three Levels of
Variability within the Levallois System, in: Dibble, H.L., Bar-Yosef, O.
(Eds.), The Definition and Interpretation of Levallois Technology,
Monographs in World Archaeology. Prehistory Press, Madison, Wisconsin,
pp. 201–211.

Delagnes, A., Jaubert, J., Meignen, L., 2007. Les technocomplexes du
paléolithique moyen en Europe occidentale dans leur cadre diachronique
et géographique, in: Vandermeersch, B., Maureille, B. (Eds.), Les
Neandertaliens. Biologie Et Cultures, Documents Préhistoriques. Editions
du Comité des Travaux Historiques et Scientifiques, Paris, pp. 213–229.

Delagnes, A., Meignen, L., 2006. Diversity of Lithic Production Systems
During the Middle Paleolithic in France. Are There Any Chronological
Trends?, in: Hovers, E., Kuhn, S.L., Jochim, M. (Eds.), Transitions
Before the Transition Evolution and Stability in the Middle Paleolithic
and Middle Stone Age. Springer, pp. 85–107.

Faivre, G.-P., Gravina, B., Bourguignon, L., Discamps, E., Turq, A.,
2017. Late Middle Palaeolithic lithic technocomplexes (MIS 5-3) in the
northeastern Aquitaine Basin: Advances and challenges. Quaternary
International 433, 116–131.
<https://doi.org/10.1016/j.quaint.2016.02.060>

Forestier, H., 1993. Le Clactonien: Mise en application d’une nouvelle
méthode de débitage s’inscrivant dans la variabilité des systèmes de
production lithique du Paléolithique ancien. Paléo 5, 53–82.
<https://doi.org/10.3406/pal.1993.1104>

Kuhn, S.L., 2013. Roots of the Middle Paleolithic in Eurasia. Current
Anthropology 54, S255–S268. <https://doi.org/10.1086/673529>

Locht, J.-L., 2003. L’industrie lithique du gisement de Beauvais (Oise,
France): Objectifs et variabilité du débitage discoïde, in: Peresani, M.
(Ed.), Discoid Lithic Technology: Advances and Implications, BAR
International Series. Archaeopress, Oxford, pp. 193–209.

Moncel, M.-H., Ashton, N., Arzarello, M., Fontana, F., Lamotte, A.,
Scott, B., Muttillo, B., Berruti, G., Nenzioni, G., Tuffreau, A., 2020.
Early Levallois core technology between marine isotope stage 12 and 9 in
Western Europe. Journal of human evolution 139, 102735.
<https://doi.org/doi.org/10.1016/j.jhevol.2019.102735>

Mourre, V., 2003. Discoïde ou pas Discoïde? Réflexions sur la pertinence
des critères techniques définissant le débitage discoïde, in: Peresani,
M. (Ed.), Discoid Lithic Technology. Advances and Implications, BAR
International Series. Archaeopress, Oxford, pp. 1–17.

Newcomer, M.H., Hivernel-Guerre, F., 1974. Nucléus sur éclat:
Technologie et utilisation par différentes cultures préhistoriques.
Bulletin de la Société Préhistorique Française 71, 119–128.
<https://doi.org/10.3406/bspf.1974.8308>

Ohel, M.Y., Bhattacharya, D.K., Bordes, F., Cahen, D., Callow, P.,
Collins, D., Katz, P.R., Narr, K.J., Newcomer, M.H., Pappu, R.S., Roe,
D.A., Singer, R., Wymer, J.J., 1979. The Clactonian: An Independent
Complex or an Integral Part of the Acheulean? \[And Comments and
Reply\]. Current Anthropology 20, 685–726.

Pelegrin, J., 2009. Cognition and the emergence of language: A
contribution from lithic technology, in: Beaune, S.A. de, Coolidge,
F.L., Wynn, T. (Eds.), Cognitive Archaeology and Human Evolution.
Cambridge University Press, New York, pp. 95–108.

Révillon, S., Tuffreau, A. (Eds.), 1994. Les industries laminaires au
Paléolithique moyen, Dossier De Documentation Archéologique. CNRS
Editions, Paris.

Santonja, M., Pérez-González, A., Panera, J., Rubio-Jara, S.,
Méndez-Quintas, E., 2016. The coexistence of Acheulean and Ancient
Middle Palaeolithic techno-complexes in the Middle Pleistocene of the
Iberian Peninsula. Quaternary International 411, 367–377.

Terradas, X., 2003. Discoid flaking method: Conception and technological
variability, in: Peresani, M. (Ed.), Discoid Lithic Technology. Advances
and Implications, BAR International Series. Archaeopress, Oxford, pp.
19–32.

Thiébaut, C., 2013. Discoid debitage stricto sensu: A method adapted to
highly mobile Middle Paleolithic groups? P@lethnology Varia.

Tixier, J., Turq, A., 1999. Kombewa et alii. Paléo 11, 135–143.
<https://doi.org/10.3406/pal.1999.1174>

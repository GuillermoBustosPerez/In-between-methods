# In between methods: Levallois, Discoid and intermediate

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
2013](#ref-kuhn_roots_2013))

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

Kuhn, S.L., 2013. Roots of the Middle Paleolithic in Eurasia. Current
Anthropology 54, S255–S268. <https://doi.org/10.1086/673529>

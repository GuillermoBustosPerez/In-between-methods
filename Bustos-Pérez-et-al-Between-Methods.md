# In between methods: Levallois, Discoid and intermediate

Guillermo Bustos-Pérez<sup>1, 2</sup>, Javier Baena<sup>1</sup> 1,
Manuel Vaquero<sup>2, 3</sup>

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
any of the other of the two knapping methods. Confusion between
discoidal and Hierarchical Discoid products is more common, although an
excellent/good value of identification is achieved for discoidal flakes
and an acceptable/fair value is achieved in the case of Hierarchical
Discoid flakes. This shows the potential applicability of machine
learning models in combination with attribute analysis for the
identification of these knapping methods among flakes.

**Keywords:** lithic technology; experimental archaeology; Levallois;
Discoid; Machine Learning

### Introduction

    library(tidyverse)

    # Load the data
    load("Data/Data.RData")

    # Head the data
    knitr::kable(ML_Data[1:10])

<table style="width:100%;">
<colgroup>
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 5%" />
<col style="width: 19%" />
<col style="width: 8%" />
<col style="width: 8%" />
<col style="width: 6%" />
<col style="width: 5%" />
<col style="width: 13%" />
<col style="width: 9%" />
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
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_11</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">31.6</td>
<td style="text-align: right;">27.2</td>
<td style="text-align: right;">1.1617647</td>
<td style="text-align: right;">8.733333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_12</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">67.5</td>
<td style="text-align: right;">36.6</td>
<td style="text-align: right;">1.8442623</td>
<td style="text-align: right;">8.366667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_13</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">63.0</td>
<td style="text-align: right;">36.1</td>
<td style="text-align: right;">1.7451524</td>
<td style="text-align: right;">9.166667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_14</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">52.7</td>
<td style="text-align: right;">45.8</td>
<td style="text-align: right;">1.1506550</td>
<td style="text-align: right;">9.766667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_15</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">52.8</td>
<td style="text-align: right;">39.0</td>
<td style="text-align: right;">1.3538462</td>
<td style="text-align: right;">10.700000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_16</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">58.2</td>
<td style="text-align: right;">33.7</td>
<td style="text-align: right;">1.7270030</td>
<td style="text-align: right;">10.533333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_17</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">58.9</td>
<td style="text-align: right;">46.5</td>
<td style="text-align: right;">1.2666667</td>
<td style="text-align: right;">13.233333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_18</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">37.9</td>
<td style="text-align: right;">21.7</td>
<td style="text-align: right;">1.7465438</td>
<td style="text-align: right;">5.800000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_19</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.9</td>
<td style="text-align: right;">33.7</td>
<td style="text-align: right;">1.3916914</td>
<td style="text-align: right;">9.633333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_20</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">53.8</td>
<td style="text-align: right;">33.4</td>
<td style="text-align: right;">1.6107784</td>
<td style="text-align: right;">10.000000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_21</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.2</td>
<td style="text-align: right;">38.9</td>
<td style="text-align: right;">1.1876607</td>
<td style="text-align: right;">7.100000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_22</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">37.0</td>
<td style="text-align: right;">24.8</td>
<td style="text-align: right;">1.4919355</td>
<td style="text-align: right;">4.566667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_23</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">65.2</td>
<td style="text-align: right;">54.9</td>
<td style="text-align: right;">1.1876138</td>
<td style="text-align: right;">11.133333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_24</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">47.7</td>
<td style="text-align: right;">47.1</td>
<td style="text-align: right;">1.0127389</td>
<td style="text-align: right;">5.866667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_25</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">32.2</td>
<td style="text-align: right;">31.9</td>
<td style="text-align: right;">1.0094044</td>
<td style="text-align: right;">4.966667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_08_26</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">47.8</td>
<td style="text-align: right;">55.7</td>
<td style="text-align: right;">0.8581688</td>
<td style="text-align: right;">14.833333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_08_27</td>
<td style="text-align: left;">Discoid_08</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">35.2</td>
<td style="text-align: right;">31.2</td>
<td style="text-align: right;">1.1282051</td>
<td style="text-align: right;">4.533333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_01</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">35.0</td>
<td style="text-align: right;">27.3</td>
<td style="text-align: right;">1.2820513</td>
<td style="text-align: right;">8.266667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_02</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.3</td>
<td style="text-align: right;">45.0</td>
<td style="text-align: right;">1.0288889</td>
<td style="text-align: right;">8.166667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_03</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">42.9</td>
<td style="text-align: right;">46.8</td>
<td style="text-align: right;">0.9166667</td>
<td style="text-align: right;">9.733333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_04</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">42.8</td>
<td style="text-align: right;">41.4</td>
<td style="text-align: right;">1.0338164</td>
<td style="text-align: right;">7.533333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_05</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">36.7</td>
<td style="text-align: right;">38.1</td>
<td style="text-align: right;">0.9632546</td>
<td style="text-align: right;">7.433333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_06</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">41.9</td>
<td style="text-align: right;">31.8</td>
<td style="text-align: right;">1.3176101</td>
<td style="text-align: right;">7.733333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_07</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">50.1</td>
<td style="text-align: right;">41.1</td>
<td style="text-align: right;">1.2189781</td>
<td style="text-align: right;">10.433333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_08</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">43.6</td>
<td style="text-align: right;">39.4</td>
<td style="text-align: right;">1.1065990</td>
<td style="text-align: right;">9.233333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_09</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">49.8</td>
<td style="text-align: right;">44.6</td>
<td style="text-align: right;">1.1165919</td>
<td style="text-align: right;">9.400000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_11</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">37.5</td>
<td style="text-align: right;">25.8</td>
<td style="text-align: right;">1.4534884</td>
<td style="text-align: right;">8.033333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_12</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">53.8</td>
<td style="text-align: right;">39.9</td>
<td style="text-align: right;">1.3483709</td>
<td style="text-align: right;">5.833333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_13</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">62.9</td>
<td style="text-align: right;">33.0</td>
<td style="text-align: right;">1.9060606</td>
<td style="text-align: right;">10.100000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_14</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">60.5</td>
<td style="text-align: right;">51.5</td>
<td style="text-align: right;">1.1747573</td>
<td style="text-align: right;">10.900000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_15</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">62.4</td>
<td style="text-align: right;">38.3</td>
<td style="text-align: right;">1.6292428</td>
<td style="text-align: right;">9.133333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_16</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">61.4</td>
<td style="text-align: right;">33.6</td>
<td style="text-align: right;">1.8273810</td>
<td style="text-align: right;">10.333333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_18</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">47.3</td>
<td style="text-align: right;">36.4</td>
<td style="text-align: right;">1.2994505</td>
<td style="text-align: right;">9.933333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_19</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">56.1</td>
<td style="text-align: right;">43.2</td>
<td style="text-align: right;">1.2986111</td>
<td style="text-align: right;">12.066667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_09_20</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">33.6</td>
<td style="text-align: right;">21.0</td>
<td style="text-align: right;">1.6000000</td>
<td style="text-align: right;">8.733333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_09_21</td>
<td style="text-align: left;">Discoid_09</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.5</td>
<td style="text-align: right;">57.7</td>
<td style="text-align: right;">0.8058925</td>
<td style="text-align: right;">15.266667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_01</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">31.4</td>
<td style="text-align: right;">38.1</td>
<td style="text-align: right;">0.8241470</td>
<td style="text-align: right;">8.766667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_02</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">58.2</td>
<td style="text-align: right;">47.5</td>
<td style="text-align: right;">1.2252632</td>
<td style="text-align: right;">7.433333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_03</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">34.1</td>
<td style="text-align: right;">28.0</td>
<td style="text-align: right;">1.2178571</td>
<td style="text-align: right;">4.233333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_04</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">45.3</td>
<td style="text-align: right;">60.9</td>
<td style="text-align: right;">0.7438424</td>
<td style="text-align: right;">11.033333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_05</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">67.9</td>
<td style="text-align: right;">43.5</td>
<td style="text-align: right;">1.5609195</td>
<td style="text-align: right;">14.333333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_06</td>
<td style="text-align: left;">Dis_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">57.7</td>
<td style="text-align: right;">48.2</td>
<td style="text-align: right;">1.1970954</td>
<td style="text-align: right;">10.000000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_07</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">52.0</td>
<td style="text-align: right;">48.2</td>
<td style="text-align: right;">1.0788382</td>
<td style="text-align: right;">14.000000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_08</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">47.5</td>
<td style="text-align: right;">49.2</td>
<td style="text-align: right;">0.9654472</td>
<td style="text-align: right;">21.166667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_09</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">58.2</td>
<td style="text-align: right;">39.2</td>
<td style="text-align: right;">1.4846939</td>
<td style="text-align: right;">12.300000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_10</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">52.2</td>
<td style="text-align: right;">34.2</td>
<td style="text-align: right;">1.5263158</td>
<td style="text-align: right;">9.800000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_11</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">59.7</td>
<td style="text-align: right;">58.3</td>
<td style="text-align: right;">1.0240137</td>
<td style="text-align: right;">13.700000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_12</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">61.8</td>
<td style="text-align: right;">46.5</td>
<td style="text-align: right;">1.3290323</td>
<td style="text-align: right;">18.100000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_13</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">37.4</td>
<td style="text-align: right;">31.0</td>
<td style="text-align: right;">1.2064516</td>
<td style="text-align: right;">5.433333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_14</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">59.5</td>
<td style="text-align: right;">29.8</td>
<td style="text-align: right;">1.9966443</td>
<td style="text-align: right;">8.900000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_15</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">64.6</td>
<td style="text-align: right;">83.3</td>
<td style="text-align: right;">0.7755102</td>
<td style="text-align: right;">31.233333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_17</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">64.3</td>
<td style="text-align: right;">38.7</td>
<td style="text-align: right;">1.6614987</td>
<td style="text-align: right;">11.466667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_18</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">49.8</td>
<td style="text-align: right;">62.0</td>
<td style="text-align: right;">0.8032258</td>
<td style="text-align: right;">12.066667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_19</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">28.1</td>
<td style="text-align: right;">28.2</td>
<td style="text-align: right;">0.9964539</td>
<td style="text-align: right;">3.100000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_20</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">39.1</td>
<td style="text-align: right;">43.7</td>
<td style="text-align: right;">0.8947368</td>
<td style="text-align: right;">9.733333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_21</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">73.7</td>
<td style="text-align: right;">114.4</td>
<td style="text-align: right;">0.6442308</td>
<td style="text-align: right;">24.066667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_22</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">72.6</td>
<td style="text-align: right;">55.2</td>
<td style="text-align: right;">1.3152174</td>
<td style="text-align: right;">15.300000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_23</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">51.8</td>
<td style="text-align: right;">33.8</td>
<td style="text-align: right;">1.5325444</td>
<td style="text-align: right;">6.233333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_24</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">29.6</td>
<td style="text-align: right;">31.3</td>
<td style="text-align: right;">0.9456869</td>
<td style="text-align: right;">5.766667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_25</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">36.5</td>
<td style="text-align: right;">35.4</td>
<td style="text-align: right;">1.0310734</td>
<td style="text-align: right;">5.366667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_26</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">47.5</td>
<td style="text-align: right;">28.9</td>
<td style="text-align: right;">1.6435986</td>
<td style="text-align: right;">17.033333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_27</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">90.8</td>
<td style="text-align: right;">46.3</td>
<td style="text-align: right;">1.9611231</td>
<td style="text-align: right;">19.033333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_28</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">16.1</td>
<td style="text-align: right;">36.4</td>
<td style="text-align: right;">0.4423077</td>
<td style="text-align: right;">4.533333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_29</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">107.8</td>
<td style="text-align: right;">81.3</td>
<td style="text-align: right;">1.3259533</td>
<td style="text-align: right;">20.733333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_30</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">58.9</td>
<td style="text-align: right;">67.0</td>
<td style="text-align: right;">0.8791045</td>
<td style="text-align: right;">14.733333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Disc_10_31</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">27.1</td>
<td style="text-align: right;">28.4</td>
<td style="text-align: right;">0.9542254</td>
<td style="text-align: right;">5.300000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Disc_10_33</td>
<td style="text-align: left;">Disc_10</td>
<td style="text-align: left;">D</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">39.2</td>
<td style="text-align: right;">27.6</td>
<td style="text-align: right;">1.4202899</td>
<td style="text-align: right;">4.866667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_01_01</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">65.2</td>
<td style="text-align: right;">39.4</td>
<td style="text-align: right;">1.6548223</td>
<td style="text-align: right;">15.233333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_01_02</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">41.7</td>
<td style="text-align: right;">50.0</td>
<td style="text-align: right;">0.8340000</td>
<td style="text-align: right;">9.600000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_01_03</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">39.9</td>
<td style="text-align: right;">27.4</td>
<td style="text-align: right;">1.4562044</td>
<td style="text-align: right;">5.100000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_01_04</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">73.5</td>
<td style="text-align: right;">57.9</td>
<td style="text-align: right;">1.2694301</td>
<td style="text-align: right;">15.333333</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_01_05</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">48.9</td>
<td style="text-align: right;">33.8</td>
<td style="text-align: right;">1.4467456</td>
<td style="text-align: right;">10.166667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_01_06</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">50.5</td>
<td style="text-align: right;">37.4</td>
<td style="text-align: right;">1.3502674</td>
<td style="text-align: right;">5.700000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_01_07</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">64.9</td>
<td style="text-align: right;">42.2</td>
<td style="text-align: right;">1.5379147</td>
<td style="text-align: right;">15.400000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_01_09</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">37.5</td>
<td style="text-align: right;">69.7</td>
<td style="text-align: right;">0.5380201</td>
<td style="text-align: right;">8.966667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_01_10</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">56.5</td>
<td style="text-align: right;">32.5</td>
<td style="text-align: right;">1.7384615</td>
<td style="text-align: right;">10.866667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_01_11</td>
<td style="text-align: left;">H_Discoid_1</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">91.2</td>
<td style="text-align: right;">55.3</td>
<td style="text-align: right;">1.6491863</td>
<td style="text-align: right;">13.600000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_02_04</td>
<td style="text-align: left;">H_Discoid_2</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">67.0</td>
<td style="text-align: right;">48.7</td>
<td style="text-align: right;">1.3757700</td>
<td style="text-align: right;">6.566667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_02_05</td>
<td style="text-align: left;">H_Discoid_2</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">44.9</td>
<td style="text-align: right;">54.0</td>
<td style="text-align: right;">0.8314815</td>
<td style="text-align: right;">12.100000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_02_06</td>
<td style="text-align: left;">H_Discoid_2</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">62.5</td>
<td style="text-align: right;">59.8</td>
<td style="text-align: right;">1.0451505</td>
<td style="text-align: right;">10.933333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_02_07</td>
<td style="text-align: left;">H_Discoid_2</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.7</td>
<td style="text-align: right;">44.0</td>
<td style="text-align: right;">1.0613636</td>
<td style="text-align: right;">6.666667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_02_08</td>
<td style="text-align: left;">H_Discoid_2</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.1</td>
<td style="text-align: right;">28.2</td>
<td style="text-align: right;">1.6347518</td>
<td style="text-align: right;">7.233333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_02_09</td>
<td style="text-align: left;">H_Discoid_2</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">61.5</td>
<td style="text-align: right;">56.5</td>
<td style="text-align: right;">1.0884956</td>
<td style="text-align: right;">10.000000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_02_10</td>
<td style="text-align: left;">H_Discoid_2</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">71.1</td>
<td style="text-align: right;">50.8</td>
<td style="text-align: right;">1.3996063</td>
<td style="text-align: right;">9.433333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_03_01</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">74.0</td>
<td style="text-align: right;">44.5</td>
<td style="text-align: right;">1.6629213</td>
<td style="text-align: right;">12.700000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_03_02</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">69.8</td>
<td style="text-align: right;">45.2</td>
<td style="text-align: right;">1.5442478</td>
<td style="text-align: right;">9.766667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_03_03</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">83.0</td>
<td style="text-align: right;">41.7</td>
<td style="text-align: right;">1.9904077</td>
<td style="text-align: right;">12.466667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_03_04</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">74.1</td>
<td style="text-align: right;">45.0</td>
<td style="text-align: right;">1.6466667</td>
<td style="text-align: right;">6.966667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_03_05</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">40.4</td>
<td style="text-align: right;">42.7</td>
<td style="text-align: right;">0.9461358</td>
<td style="text-align: right;">4.200000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_03_06</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">47.2</td>
<td style="text-align: right;">48.0</td>
<td style="text-align: right;">0.9833333</td>
<td style="text-align: right;">15.033333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_03_07</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">45.0</td>
<td style="text-align: right;">40.0</td>
<td style="text-align: right;">1.1250000</td>
<td style="text-align: right;">5.966667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_03_08</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">74.2</td>
<td style="text-align: right;">43.8</td>
<td style="text-align: right;">1.6940639</td>
<td style="text-align: right;">7.166667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_03_09</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">60.8</td>
<td style="text-align: right;">58.5</td>
<td style="text-align: right;">1.0393162</td>
<td style="text-align: right;">7.833333</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_03_10</td>
<td style="text-align: left;">H_Discoid_3</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">50.6</td>
<td style="text-align: right;">54.3</td>
<td style="text-align: right;">0.9318600</td>
<td style="text-align: right;">13.333333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_04_01</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">66.8</td>
<td style="text-align: right;">40.8</td>
<td style="text-align: right;">1.6372549</td>
<td style="text-align: right;">9.400000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_04_02</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">84.4</td>
<td style="text-align: right;">46.0</td>
<td style="text-align: right;">1.8347826</td>
<td style="text-align: right;">15.133333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_04_03</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">39.6</td>
<td style="text-align: right;">48.5</td>
<td style="text-align: right;">0.8164948</td>
<td style="text-align: right;">13.000000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_04_04</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">49.8</td>
<td style="text-align: right;">38.1</td>
<td style="text-align: right;">1.3070866</td>
<td style="text-align: right;">5.833333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_04_05</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">59.7</td>
<td style="text-align: right;">38.2</td>
<td style="text-align: right;">1.5628272</td>
<td style="text-align: right;">6.566667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_04_06</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">81.7</td>
<td style="text-align: right;">49.1</td>
<td style="text-align: right;">1.6639511</td>
<td style="text-align: right;">14.666667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_04_07</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">86.6</td>
<td style="text-align: right;">84.5</td>
<td style="text-align: right;">1.0248521</td>
<td style="text-align: right;">10.833333</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_04_08</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">51.4</td>
<td style="text-align: right;">36.8</td>
<td style="text-align: right;">1.3967391</td>
<td style="text-align: right;">11.266667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_04_09</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">82.1</td>
<td style="text-align: right;">54.2</td>
<td style="text-align: right;">1.5147601</td>
<td style="text-align: right;">12.566667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_04_10</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">52.8</td>
<td style="text-align: right;">42.8</td>
<td style="text-align: right;">1.2336449</td>
<td style="text-align: right;">8.100000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_04_11</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">81.0</td>
<td style="text-align: right;">65.4</td>
<td style="text-align: right;">1.2385321</td>
<td style="text-align: right;">19.866667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_04_12</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">56.4</td>
<td style="text-align: right;">31.7</td>
<td style="text-align: right;">1.7791798</td>
<td style="text-align: right;">10.166667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_04_13</td>
<td style="text-align: left;">H_Discoid_4</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">50.5</td>
<td style="text-align: right;">21.1</td>
<td style="text-align: right;">2.3933649</td>
<td style="text-align: right;">7.633333</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_05_01</td>
<td style="text-align: left;">H_Discoid_5</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">72.3</td>
<td style="text-align: right;">51.7</td>
<td style="text-align: right;">1.3984526</td>
<td style="text-align: right;">13.600000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_05_02</td>
<td style="text-align: left;">H_Discoid_5</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">47.8</td>
<td style="text-align: right;">70.2</td>
<td style="text-align: right;">0.6809117</td>
<td style="text-align: right;">10.433333</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_05_03</td>
<td style="text-align: left;">H_Discoid_5</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">68.0</td>
<td style="text-align: right;">34.0</td>
<td style="text-align: right;">2.0000000</td>
<td style="text-align: right;">13.433333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_05_04</td>
<td style="text-align: left;">H_Discoid_5</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">45.5</td>
<td style="text-align: right;">76.0</td>
<td style="text-align: right;">0.5986842</td>
<td style="text-align: right;">9.800000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_05_05</td>
<td style="text-align: left;">H_Discoid_5</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">66.6</td>
<td style="text-align: right;">38.4</td>
<td style="text-align: right;">1.7343750</td>
<td style="text-align: right;">11.466667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_05_06</td>
<td style="text-align: left;">H_Discoid_5</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">57.2</td>
<td style="text-align: right;">74.6</td>
<td style="text-align: right;">0.7667560</td>
<td style="text-align: right;">12.900000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_05_07</td>
<td style="text-align: left;">H_Discoid_5</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">56.5</td>
<td style="text-align: right;">57.2</td>
<td style="text-align: right;">0.9877622</td>
<td style="text-align: right;">11.000000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_05_08</td>
<td style="text-align: left;">H_Discoid_5</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">63.3</td>
<td style="text-align: right;">61.0</td>
<td style="text-align: right;">1.0377049</td>
<td style="text-align: right;">16.933333</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_06_01</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">40.7</td>
<td style="text-align: right;">45.0</td>
<td style="text-align: right;">0.9044444</td>
<td style="text-align: right;">10.900000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_06_02</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">47.4</td>
<td style="text-align: right;">42.3</td>
<td style="text-align: right;">1.1205674</td>
<td style="text-align: right;">10.733333</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_06_03</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">49.7</td>
<td style="text-align: right;">36.0</td>
<td style="text-align: right;">1.3805556</td>
<td style="text-align: right;">16.266667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_06_04</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">33.2</td>
<td style="text-align: right;">43.2</td>
<td style="text-align: right;">0.7685185</td>
<td style="text-align: right;">6.800000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_06_05</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">66.2</td>
<td style="text-align: right;">40.2</td>
<td style="text-align: right;">1.6467662</td>
<td style="text-align: right;">17.666667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_06_06</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.0</td>
<td style="text-align: right;">46.7</td>
<td style="text-align: right;">0.9850107</td>
<td style="text-align: right;">8.566667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_06_07</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">77.5</td>
<td style="text-align: right;">34.3</td>
<td style="text-align: right;">2.2594752</td>
<td style="text-align: right;">9.933333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_06_08</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">66.4</td>
<td style="text-align: right;">42.4</td>
<td style="text-align: right;">1.5660377</td>
<td style="text-align: right;">10.866667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_06_09</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">42.1</td>
<td style="text-align: right;">37.2</td>
<td style="text-align: right;">1.1317204</td>
<td style="text-align: right;">9.933333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_06_10</td>
<td style="text-align: left;">H_Discoid_6</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">91.0</td>
<td style="text-align: right;">61.5</td>
<td style="text-align: right;">1.4796748</td>
<td style="text-align: right;">17.066667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_07_01</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">61.2</td>
<td style="text-align: right;">32.5</td>
<td style="text-align: right;">1.8830769</td>
<td style="text-align: right;">10.700000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_07_02</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">31.3</td>
<td style="text-align: right;">42.6</td>
<td style="text-align: right;">0.7347418</td>
<td style="text-align: right;">3.266667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_07_03</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">44.9</td>
<td style="text-align: right;">25.5</td>
<td style="text-align: right;">1.7607843</td>
<td style="text-align: right;">4.500000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_07_04</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">56.3</td>
<td style="text-align: right;">36.4</td>
<td style="text-align: right;">1.5467033</td>
<td style="text-align: right;">9.500000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_07_05</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">61.5</td>
<td style="text-align: right;">25.6</td>
<td style="text-align: right;">2.4023438</td>
<td style="text-align: right;">11.200000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_07_06</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">74.1</td>
<td style="text-align: right;">63.2</td>
<td style="text-align: right;">1.1724684</td>
<td style="text-align: right;">12.866667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_07_07</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">41.1</td>
<td style="text-align: right;">49.4</td>
<td style="text-align: right;">0.8319838</td>
<td style="text-align: right;">5.000000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_07_08</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">36.7</td>
<td style="text-align: right;">37.3</td>
<td style="text-align: right;">0.9839142</td>
<td style="text-align: right;">7.266667</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_07_09</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">62.3</td>
<td style="text-align: right;">39.2</td>
<td style="text-align: right;">1.5892857</td>
<td style="text-align: right;">9.866667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_07_10</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">75.8</td>
<td style="text-align: right;">41.1</td>
<td style="text-align: right;">1.8442822</td>
<td style="text-align: right;">19.600000</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_07_11</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">38.2</td>
<td style="text-align: right;">34.4</td>
<td style="text-align: right;">1.1104651</td>
<td style="text-align: right;">8.566667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_07_12</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">49.8</td>
<td style="text-align: right;">39.2</td>
<td style="text-align: right;">1.2704082</td>
<td style="text-align: right;">5.333333</td>
</tr>
<tr class="even">
<td style="text-align: left;">HD_07_13</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">58.9</td>
<td style="text-align: right;">37.9</td>
<td style="text-align: right;">1.5540897</td>
<td style="text-align: right;">6.500000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">HD_07_14</td>
<td style="text-align: left;">H_Discoid_7</td>
<td style="text-align: left;">HD</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">78.8</td>
<td style="text-align: right;">82.4</td>
<td style="text-align: right;">0.9563107</td>
<td style="text-align: right;">17.566667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_01</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Preferential flake</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">63.1</td>
<td style="text-align: right;">37.9</td>
<td style="text-align: right;">1.6649077</td>
<td style="text-align: right;">5.100000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_02</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">46.4</td>
<td style="text-align: right;">31.3</td>
<td style="text-align: right;">1.4824281</td>
<td style="text-align: right;">5.533333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_04</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">31.5</td>
<td style="text-align: right;">34.8</td>
<td style="text-align: right;">0.9051724</td>
<td style="text-align: right;">4.533333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_05</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">44.2</td>
<td style="text-align: right;">35.4</td>
<td style="text-align: right;">1.2485876</td>
<td style="text-align: right;">3.900000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_06</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">39.5</td>
<td style="text-align: right;">44.1</td>
<td style="text-align: right;">0.8956916</td>
<td style="text-align: right;">4.866667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_07</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">27.4</td>
<td style="text-align: right;">31.5</td>
<td style="text-align: right;">0.8698413</td>
<td style="text-align: right;">2.900000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_08</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">33.2</td>
<td style="text-align: right;">26.4</td>
<td style="text-align: right;">1.2575758</td>
<td style="text-align: right;">1.800000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_09</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">42.1</td>
<td style="text-align: right;">36.7</td>
<td style="text-align: right;">1.1471390</td>
<td style="text-align: right;">7.766667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_10</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">41.5</td>
<td style="text-align: right;">41.3</td>
<td style="text-align: right;">1.0048426</td>
<td style="text-align: right;">6.233333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_11</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">44.6</td>
<td style="text-align: right;">37.3</td>
<td style="text-align: right;">1.1957105</td>
<td style="text-align: right;">3.333333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_12</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">31.9</td>
<td style="text-align: right;">33.5</td>
<td style="text-align: right;">0.9522388</td>
<td style="text-align: right;">4.900000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_13</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">33.0</td>
<td style="text-align: right;">36.1</td>
<td style="text-align: right;">0.9141274</td>
<td style="text-align: right;">6.033333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_14</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">33.8</td>
<td style="text-align: right;">32.1</td>
<td style="text-align: right;">1.0529595</td>
<td style="text-align: right;">7.000000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_15</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">29.9</td>
<td style="text-align: right;">38.0</td>
<td style="text-align: right;">0.7868421</td>
<td style="text-align: right;">5.366667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_16</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">38.2</td>
<td style="text-align: right;">42.6</td>
<td style="text-align: right;">0.8967136</td>
<td style="text-align: right;">7.400000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_17</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">35.4</td>
<td style="text-align: right;">45.2</td>
<td style="text-align: right;">0.7831858</td>
<td style="text-align: right;">7.133333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_18</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">42.4</td>
<td style="text-align: right;">44.0</td>
<td style="text-align: right;">0.9636364</td>
<td style="text-align: right;">5.666667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_19</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">54.6</td>
<td style="text-align: right;">31.8</td>
<td style="text-align: right;">1.7169811</td>
<td style="text-align: right;">4.200000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_20</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">45.9</td>
<td style="text-align: right;">38.7</td>
<td style="text-align: right;">1.1860465</td>
<td style="text-align: right;">5.066667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_21</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">35.7</td>
<td style="text-align: right;">44.0</td>
<td style="text-align: right;">0.8113636</td>
<td style="text-align: right;">4.433333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_22</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">34.2</td>
<td style="text-align: right;">35.0</td>
<td style="text-align: right;">0.9771429</td>
<td style="text-align: right;">5.466667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_23</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">49.0</td>
<td style="text-align: right;">32.2</td>
<td style="text-align: right;">1.5217391</td>
<td style="text-align: right;">3.066667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_24</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">44.7</td>
<td style="text-align: right;">28.1</td>
<td style="text-align: right;">1.5907473</td>
<td style="text-align: right;">3.400000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_25</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">33.4</td>
<td style="text-align: right;">22.7</td>
<td style="text-align: right;">1.4713656</td>
<td style="text-align: right;">3.000000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_26</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">25.5</td>
<td style="text-align: right;">27.6</td>
<td style="text-align: right;">0.9239130</td>
<td style="text-align: right;">4.366667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_27</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">24.3</td>
<td style="text-align: right;">27.6</td>
<td style="text-align: right;">0.8804348</td>
<td style="text-align: right;">3.766667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_28</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">27.7</td>
<td style="text-align: right;">31.2</td>
<td style="text-align: right;">0.8878205</td>
<td style="text-align: right;">7.533333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_04_29</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">36.3</td>
<td style="text-align: right;">32.0</td>
<td style="text-align: right;">1.1343750</td>
<td style="text-align: right;">6.100000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_04_30</td>
<td style="text-align: left;">Lev_04</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">C</td>
<td style="text-align: left;">Y</td>
<td style="text-align: right;">29.9</td>
<td style="text-align: right;">33.5</td>
<td style="text-align: right;">0.8925373</td>
<td style="text-align: right;">4.966667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_12_01</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">79.7</td>
<td style="text-align: right;">58.0</td>
<td style="text-align: right;">1.3741379</td>
<td style="text-align: right;">7.000000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_12_02</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">44.4</td>
<td style="text-align: right;">50.0</td>
<td style="text-align: right;">0.8880000</td>
<td style="text-align: right;">9.133333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_12_03</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">83.7</td>
<td style="text-align: right;">50.0</td>
<td style="text-align: right;">1.6740000</td>
<td style="text-align: right;">6.466667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_12_05</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">55.2</td>
<td style="text-align: right;">55.1</td>
<td style="text-align: right;">1.0018149</td>
<td style="text-align: right;">9.500000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_12_06</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">64.9</td>
<td style="text-align: right;">63.4</td>
<td style="text-align: right;">1.0236593</td>
<td style="text-align: right;">10.066667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_12_07</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">42.0</td>
<td style="text-align: right;">49.1</td>
<td style="text-align: right;">0.8553971</td>
<td style="text-align: right;">6.300000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_12_08</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">53.0</td>
<td style="text-align: right;">61.3</td>
<td style="text-align: right;">0.8646003</td>
<td style="text-align: right;">14.100000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_12_09</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">53.3</td>
<td style="text-align: right;">47.9</td>
<td style="text-align: right;">1.1127349</td>
<td style="text-align: right;">12.600000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_12_11</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">46.8</td>
<td style="text-align: right;">49.6</td>
<td style="text-align: right;">0.9435484</td>
<td style="text-align: right;">7.333333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_12_12</td>
<td style="text-align: left;">Lev_12</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">105.5</td>
<td style="text-align: right;">48.0</td>
<td style="text-align: right;">2.1979167</td>
<td style="text-align: right;">10.566667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_01</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">21.7</td>
<td style="text-align: right;">42.1</td>
<td style="text-align: right;">0.5154394</td>
<td style="text-align: right;">3.133333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_02</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">41.5</td>
<td style="text-align: right;">39.4</td>
<td style="text-align: right;">1.0532995</td>
<td style="text-align: right;">4.800000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_03</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">31.7</td>
<td style="text-align: right;">41.6</td>
<td style="text-align: right;">0.7620192</td>
<td style="text-align: right;">5.133333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_04</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">22.5</td>
<td style="text-align: right;">21.7</td>
<td style="text-align: right;">1.0368664</td>
<td style="text-align: right;">4.066667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_05</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">28.4</td>
<td style="text-align: right;">38.2</td>
<td style="text-align: right;">0.7434555</td>
<td style="text-align: right;">5.066667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_06</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">38.8</td>
<td style="text-align: right;">53.1</td>
<td style="text-align: right;">0.7306968</td>
<td style="text-align: right;">5.533333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_07</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">52.1</td>
<td style="text-align: right;">39.0</td>
<td style="text-align: right;">1.3358974</td>
<td style="text-align: right;">4.666667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_08</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">53.4</td>
<td style="text-align: right;">55.0</td>
<td style="text-align: right;">0.9709091</td>
<td style="text-align: right;">6.466667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_09</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">42.9</td>
<td style="text-align: right;">40.1</td>
<td style="text-align: right;">1.0698254</td>
<td style="text-align: right;">5.833333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_10</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">52.4</td>
<td style="text-align: right;">47.7</td>
<td style="text-align: right;">1.0985325</td>
<td style="text-align: right;">5.900000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_11</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">41.2</td>
<td style="text-align: right;">25.4</td>
<td style="text-align: right;">1.6220472</td>
<td style="text-align: right;">4.766667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_12</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">61.3</td>
<td style="text-align: right;">48.6</td>
<td style="text-align: right;">1.2613169</td>
<td style="text-align: right;">5.666667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_13</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">40.4</td>
<td style="text-align: right;">23.9</td>
<td style="text-align: right;">1.6903766</td>
<td style="text-align: right;">4.266667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_14</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">42.9</td>
<td style="text-align: right;">55.6</td>
<td style="text-align: right;">0.7715827</td>
<td style="text-align: right;">5.733333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_15</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">23.4</td>
<td style="text-align: right;">27.0</td>
<td style="text-align: right;">0.8666667</td>
<td style="text-align: right;">3.633333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_16</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">54.4</td>
<td style="text-align: right;">45.3</td>
<td style="text-align: right;">1.2008830</td>
<td style="text-align: right;">10.400000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_17</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">41.6</td>
<td style="text-align: right;">44.0</td>
<td style="text-align: right;">0.9454545</td>
<td style="text-align: right;">7.300000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_18</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">18.6</td>
<td style="text-align: right;">19.6</td>
<td style="text-align: right;">0.9489796</td>
<td style="text-align: right;">1.733333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_19</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">58.8</td>
<td style="text-align: right;">31.4</td>
<td style="text-align: right;">1.8726115</td>
<td style="text-align: right;">11.866667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_15_21</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">67.8</td>
<td style="text-align: right;">40.8</td>
<td style="text-align: right;">1.6617647</td>
<td style="text-align: right;">6.300000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_15_22</td>
<td style="text-align: left;">Lev_15</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">76.0</td>
<td style="text-align: right;">50.9</td>
<td style="text-align: right;">1.4931238</td>
<td style="text-align: right;">9.466667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_17_01</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">57.2</td>
<td style="text-align: right;">68.5</td>
<td style="text-align: right;">0.8350365</td>
<td style="text-align: right;">12.166667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_17_03</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">62.0</td>
<td style="text-align: right;">43.9</td>
<td style="text-align: right;">1.4123007</td>
<td style="text-align: right;">5.900000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_17_04</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">68.9</td>
<td style="text-align: right;">41.3</td>
<td style="text-align: right;">1.6682809</td>
<td style="text-align: right;">10.600000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_17_05</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">38.8</td>
<td style="text-align: right;">59.8</td>
<td style="text-align: right;">0.6488294</td>
<td style="text-align: right;">9.066667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_17_06</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">69.0</td>
<td style="text-align: right;">80.0</td>
<td style="text-align: right;">0.8625000</td>
<td style="text-align: right;">15.166667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_17_08</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">38.6</td>
<td style="text-align: right;">57.8</td>
<td style="text-align: right;">0.6678201</td>
<td style="text-align: right;">6.066667</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_17_09</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">49.6</td>
<td style="text-align: right;">48.4</td>
<td style="text-align: right;">1.0247934</td>
<td style="text-align: right;">10.866667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_17_10</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">53.0</td>
<td style="text-align: right;">51.8</td>
<td style="text-align: right;">1.0231660</td>
<td style="text-align: right;">7.800000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_17_11</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">53.9</td>
<td style="text-align: right;">64.3</td>
<td style="text-align: right;">0.8382582</td>
<td style="text-align: right;">12.633333</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_17_12</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Decortication</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">82.6</td>
<td style="text-align: right;">72.6</td>
<td style="text-align: right;">1.1377410</td>
<td style="text-align: right;">12.933333</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_17_13</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">34.1</td>
<td style="text-align: right;">32.0</td>
<td style="text-align: right;">1.0656250</td>
<td style="text-align: right;">8.866667</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Lev_17_14</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Full Production</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">30.8</td>
<td style="text-align: right;">45.8</td>
<td style="text-align: right;">0.6724891</td>
<td style="text-align: right;">7.600000</td>
</tr>
<tr class="even">
<td style="text-align: left;">Lev_17_15</td>
<td style="text-align: left;">Lev_17</td>
<td style="text-align: left;">L</td>
<td style="text-align: left;">Prep. Explo. Surface</td>
<td style="text-align: left;">Complete</td>
<td style="text-align: left;">Yes</td>
<td style="text-align: right;">31.5</td>
<td style="text-align: right;">66.7</td>
<td style="text-align: right;">0.4722639</td>
<td style="text-align: right;">6.933333</td>
</tr>
</tbody>
</table>

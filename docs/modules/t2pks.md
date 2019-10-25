## Module description

The `t2pks` module predicts PKS type II biosynthetic gene cluster details.

### Starter units

The following starter units are detected:

* 2-methylbutyryl-CoA
* acetyl-CoA
* anthraniloyl-CoA
* aziridinyl-CoA
* benzoyl-CoA
* butyryl-CoA
* hexadienyl-CoA
* hexanoyl-CoA
* isobutyryl-CoA
* malonamyl-CoA
* propionyl-CoA


### Malonyl elongation steps

Based on chain length factor classification, the module predicts the number of
malonyl elongation steps.

### Product class

Based on both the number of malonyl elongations and the detected cyclases, one
or more product classes are predicted.

The following product classes are detected:

* angucycline
* anthracycline
* aureolic acid
* benzoisochromanequinone
* pentangular polyphenol
* tetracenomycin
* tetracycline


### Product molecular weight

Product molecular weights are predicted for all combinations of starter units
and elongation steps, and modified based on the tailoring enzymes identified in
the cluster.


## Glossary of PKS type II specific terms

<dl>
  <dt id="CLF">CLF</dt>
  <dd>chain length factor
    <dl>
    <dt id="CLF_7">CLF_7</dt>
    <dd>extending by 7 units</dd>
    <dt id="CLF_8|9">CLF_8|9</dt>
    <dd>extending by 8 or 9 units</dd>
    <dt id="CLF_11|12">CLF_11|12</dt>
    <dd>extending by 11 or 12 units</dd>
    </dl>
  </dd>
  <dt id="AT">AT</dt>
  <dd>acetyl transferase</dd>
  <dt id="CYC">CYC</dt>
  <dd>cyclase
    <dl>
      <dt id="CYC_C7-C12">CYC_C7-C12</dt>
      <dd>connecting carbons 7 and 12</dd>
      <dt id="CYC_C5-C14">CYC_C5-C14</dt>
      <dd>connecting carbons 5 and 14</dd>
      <dt id="CYC_C5-C14/C3-C16">CYC_C5-C14/C3-C16</dt>
      <dd>connecting carbons 5 or 3 and 14 or 16, respectively</dd>
      <dt id="CYC_C1-C18|C2-C19">CYC_C1-C18|C2-C19</dt>
      <dd>connecting carbons 1 or 2 and 18 or 19, respectively</dd>
      <dt id="CYC_C2-C19">CYC_C2-C19</dt>
      <dd>connecting carbons 2 and 19</dd>
      <dt id="CYC_C5-C18">CYC_C5-C18</dt>
      <dd>connecting carbons 5 and 18</dd>
      <dt id="CYC_C4-C17/C2-C19">CYC_C4-C17/C2-C19</dt>
      <dd>connecting carbons 4 or 2 and 17 or 19, respectively</dd>
      <dt id="CYC_C4-C21/C2-C23|C2-C19">CYC_C4-C21/C2-C23|C2-C19</dt>
      <dd>connecting carbons 4 or 2 and 21, 23, or 19, respectively</dd>
      <dt id="CYC_C9-C14">CYC_C9-C14</dt>
      <dd>connecting carbons 9 and 14</dd>
    </dl>
  </dd>
  <dt id="KSIII">KSIII</dt>
  <dd>Non-acetate starter unit ketosynthase III</dd>
  <dt id="ACP">ACP</dt>
  <dd>acetyl carrier protein</dd>
  <dt id="KR">KR</dt>
  <dd>ketoreductase
    <dl>
    <dt id="KR_C9">KR_C9</dt>
    <dd>reducing carbon 9</dd>
    <dt id="KR_C11">KR_C11</dt>
    <dd>reducing carbon 11</dd>
    <dt id="KR_C15">KR_C15</dt>
    <dd>reducing carbon 15</dd>
    <dt id="KR_C17">KR_C17</dt>
    <dd>reducing carbon 17</dd>
    <dt id="KR_C19">KR_C19</dt>
    <dd>reducing carbon 19</dd>
    </dl>
  </dd>
  <dt id="KS">KS</dt>
  <dd>ketosynthase</dd>
  <dt id="OXY">OXY</dt>
  <dd>oxygenase</dd>
  <dt id="GT">GT</dt>
  <dd>glycosyltransferase</dd>
  <dt id="MET">MET</dt>
  <dd>methyltransferase
    <dl>
    <dt id="MET_carboxy_O">MET_carboxy_O</dt>
    <dd>carboxyl O-methyltransferase</dd>
    <dt id="MET_C2O|C2N">MET_C2O|C2N</dt>
    <dd>O- or N-methyltransferase acting on the oxygen or nitrogen at carbon 2, respectively</dd>
    <dt id="MET_C6|C8">MET_C6|C8</dt>
    <dd>methyltransferase acting at carbon 6 or 8</dd>
    <dt id="MET_C9O">MET_C9O</dt>
    <dd>O-methyltransferase acting on the oxygen at carbon 9</dd>
    <dt id="MET_C10">MET_C10</dt>
    <dd>methyltransferase acting at carbon 10</dd>
    <dt id="MET_C11O">MET_C11O</dt>
    <dd>O-methyltransferase acting on the oxygen at carbon 11</dd>
    <dt id="MET_C13O|C17O">MET_C13O|C17O</dt>
    <dd>O-methyltransferase acting on the oxygen at carbon 13 or 17</dd>
    <dt id="MET_C18O">MET_C18O</dt>
    <dd>O-methyltransferase acting on the oxygen at carbon 18</dd>
    </dl>
  </dd>
  <dt id="DIMER">DIMER</dt>
  <dd>dimerase</dd>
  <dt id="LIG">LIG</dt>
  <dd>ligase</dd>
  <dt id="HAL">HAL</dt>
  <dd>halogenase</dd>
  <dt id="AMIN">AMIN</dt>
  <dd>aminase</dd>
  <dt id="AMID">AMID</dt>
  <dd>amidase</dd>
</dl>

#Cluster Types

antiSMASH uses some abbreviations internally to refer to the different
types of secondary metabolite clusters, a short explanation of the different
types can be found below:

###Current Types
|Label|Description|Added|Last updated|
|-----|-----------|:---:|:----------:|
|<span id="t1pks">T1PKS</span>|Type I PKS (Polyketide synthase)|&lt;= 3.0|&lt;= 3.0|
|<span id="t2pks">T2PKS</span>|Type II PKS|&lt;= 3.0|5.0|
|<span id="t2pks">T3PKS</span>|Type III PKS|&lt;= 3.0|&lt;= 3.0|
|<span id="transatpks"><span id="transat-pks">transAT-PKS</span></span>|Trans-AT PKS|&lt;= 3.0|5.0|
|<span id="ppys-ks"><span id="ppysks">PpyS-KS</span></span>|PPY-like pyrone cluster|4.2|4.2|
|<span id="hgle-ks"><span id="hgleks">hglE-KS</span></span>|heterocyst glycolipid synthase-like PKS|5.0|5.0|
|<span id="pks-like">PKS-like</span>|Other types of PKS cluster|5.0|5.0|
|<span id="arylpolyene">arylpolyene</span>|Aryl polyene cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="resorcinol">resorcinol</span>|Resorcinol cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="ladderane">ladderane</span>|Ladderane cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="pufa">PUFA</span>|Polyunsaturated fatty acid cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="nrps">nrps</span>|Nonribosomal peptide synthetase cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="nrps-like"><span id="nrpsfragment">nrps-like</span></span>|NRPS-like fragment|5.0|5.0|
|<span id="terpene">terpene</span>|Terpene|&lt;= 3.0|4.1|
|<span id="lantipeptide"><span id="lanthipeptide">lanthipeptide</span></span>|Lanthipeptide cluster|4.2|5.0|
|<span id="bacteriocin">bacteriocin</span>|Bacteriocin or other unspecified ribosomally synthesised and post-translationally modified peptide product (RiPP) cluster|4.1|5.0|
|<span id="betalactone">betalactone</span>|beta-lactone containing protease inhibitor|5.0|5.0|
|<span id="thiopeptide">thiopeptide</span>|Thiopeptide cluster|4.2|5.0|
|<span id="linaridin">linaridin</span>|Linaridin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="cyanobactin">cyanobactin</span>|Cyanobactin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="glycocin">glycocin</span>|Glycocin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="lap">LAP</span>|Linear azol(in)e-containing peptides|&lt;= 3.0|5.0|
|<span id="lassopeptide">lassopeptide</span>|Lasso peptide cluster|&lt;= 3.0|5.0|
|<span id="sactipeptide">sactipeptide</span>|Sactipeptide cluster|&lt;= 3.0|4.0|
|<span id="bottromycin">bottromycin</span>|Bottromycin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="head_to_tail">head_to_tail</span>|Head-to-tail cyclised (subtilosin-like) cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="microviridin">microviridin</span>|Microviridin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="proteusin">proteusin</span>|Proteusin cluster|&lt;= 3.0|&lt;= 3.0 |
|<span id="blactam">blactam</span>|&beta;-lactam cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="amglyccycl">amglyccycl</span>|Aminoglycoside/aminocyclitol cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="aminocoumarin">aminocoumarin</span>|Aminocoumarin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="siderophore">siderophore</span>|Siderophore cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="ectoine">ectoine</span>|Ectoine cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="butyrolactone">butyrolactone</span>|Butyrolactone cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="indole">indole</span>|Indole cluster|&lt;= 3.0|4.0|
|<span id="nucleoside">nucleoside</span>|Nucleoside cluster|&lt;= 3.0|5.0|
|<span id="phosphoglycolipid">phosphoglycolipid</span>|Phosphoglycolipid cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="melanin">melanin</span>|Melanin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="oligosaccharide">oligosaccharide</span>|Oligosaccharide cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="furan">furan</span>|Furan cluster|&lt;= 3.0|5.0|
|<span id="hserlactone">hserlactone</span>|Homoserine lactone cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="phenazine">phenazine</span>|Phenazine cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="phosphonate">phosphonate</span>|Phosphonate cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="fused">fused</span>|Pheganomycin-style protein ligase-containing cluster|4.0|4.0|
|<span id="pbde">PBDE</span>|Polybrominated diphenyl ether cluster|4.1|4.1|
|<span id="acyl_amino_acids">acyl_amino_acids</span>|N-acyl amino acid cluster|4.0|4.1|
|<span id="RaS-RiPP">RaS-RiPP</span>|Streptide-like thioether-bond RiPPs|5.0|5.0|
|<span id="fungal-RiPP">fungal-RiPP</span>|Fungal RiPP with POP or UstH peptidase types and a modification|5.0|5.0|
|<span id="other">other</span>|Cluster containing a secondary metabolite-related protein that does not fit into any other category|4.0|5.0|
|<span id="cf_saccharide">cf_saccharide</span>|Possible saccharide cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="cf_fatty_acid">cf_fatty_acid</span>|Possible fatty acid cluster|&lt;= 3.0|4.2|

###Obsolete/Previous Types
|Label|Description|Added|Removed|Notes|
|-----|-----------|:---:|:-----:|-----|
|<span id="otherks">otherks</span>|Other types of PKS cluster|&lt;= 3.0|5.0|Split into *PKS-like* and *hglE-KS*|
|<span id="microcin">microcin</span>|Microcin cluster|&lt;= 3.0|5.0|Merged into *lasso peptide*|
|<span id="cf_putative">cf_putative</span>|Putative cluster of unknown type identified with the ClusterFinder algorithm|&lt;= 3.0|5.0|These predictions are now subregions, not clusters|


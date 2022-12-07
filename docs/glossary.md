#Cluster Types

antiSMASH uses some abbreviations internally to refer to the different
types of secondary metabolite clusters, a short explanation of the different
types can be found below:

###Current Types
|Label|Description|Added|Last updated|
|-----|-----------|:---:|:----------:|
|<span id="2dos">2dos</span>|2-deoxy-streptamine aminoglycoside|7.0|7.0|
|<span id="acyl_amino_acids">acyl_amino_acids</span>|N-acyl amino acid cluster|4.0|4.1|
|<span id="aminocoumarin">aminocoumarin</span>|Aminocoumarin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="amglyccycl">amglyccycl</span>|Aminoglycoside/aminocyclitol cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="arylpolyene">arylpolyene</span>|Aryl polyene cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="betalactone">betalactone</span>|beta-lactone containing protease inhibitor|5.0|5.0|
|<span id="blactam">blactam</span>|&beta;-lactam cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="bottromycin">bottromycin</span>|Bottromycin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="butyrolactone">butyrolactone</span>|Butyrolactone cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="cdps">CDPS</span>|tRNA-dependent cyclodipeptide synthases|5.0|5.0|
|<span id="crocagin">crocagin</span>|Crocagin-like cluster|7.0|7.0|
|<span id="cyanobactin">cyanobactin</span>|Cyanobactins like patellamide (AY986476)|&lt;= 3.0|7.0|
|<span id="cyclic-lactone-autoinducer">cyclic-lactone-autoinducer</span>|agrD-like cyclic lactone autoinducer peptides (AF001782)|6.0|6.0|
|<span id="ectoine">ectoine</span>|Ectoine cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="epipeptide">epipeptide</span>|D-amino-acid containing RiPPs such as yydF (D78193)|6.0|6.0|
|<span id="fatty_acid">fatty_acid</span>|Fatty acid cluster (loose strictness, likely from primary metabolism)|&lt;= 3.0|4.2|
|<span id="furan">furan</span>|Furan cluster|&lt;= 3.0|5.0|
|<span id="fungal-ripp">fungal-RiPP</span>|Fungal RiPP with POP or UstH peptidase types and a modification|5.0|5.0|
|<span id="fungal-ripp-like">fungal-RiPP-like</span>|Fungal RiPP-like clusters|7.0|7.0|
|<span id="glycocin">glycocin</span>|Glycocin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="guanidinotides">guanidinotides</span>|Pheganomycin-style protein ligase-containing cluster|4.0|6.0|
|<span id="halogenated">halogenated</span>|Cluster containing a halogenase and thus potentially generating a halogenated product|5.0|5.0|
|<span id="hgle-ks"><span id="hgleks">hglE-KS</span></span>|heterocyst glycolipid synthase-like PKS|5.0|5.0|
|<span id="hserlactone">hserlactone</span>|Homoserine lactone cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="indole">indole</span>|Indole cluster|&lt;= 3.0|4.0|
|<span id="lap">LAP</span>|Linear azol(in)e-containing peptides|&lt;= 3.0|6.0|
|<span id="ladderane">ladderane</span>|Ladderane cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="lanthipeptide-class-i">lanthipeptide class I</span>|Class I lanthipeptide clusters like nisin|4.2|6.0|
|<span id="lanthipeptide-class-ii">lanthipeptide class II</span>|Class II lanthipeptide clusters like mutacin II (U40620)|4.2|6.0|
|<span id="lanthipeptide-class-iii">lanthipeptide class III</span>|Class III lanthipeptide clusters like labyrinthopeptin (FN178622)|4.2|6.0|
|<span id="lanthipeptide-class-iv">lanthipeptide class IV</span>|Class IV lanthipeptide clusters like venezuelin (HQ328852)|4.2|6.0|
|<span id="lanthipeptide-class-v">lanthipeptide class V</span>|Glycosylated lanthipeptide/linaridin hybrids like MT210103|5.1|6.0|
|<span id="lassopeptide">lassopeptide</span>|Lasso peptide cluster|&lt;= 3.0|5.0|
|<span id="linaridin">linaridin</span>|Linear arid peptide such as cypemycin (HQ148718) and salinipeptin (MG788286)|&lt;= 3.0|&lt;= 3.0|
|<span id="lipolanthine">lipolanthine</span>|Lanthipeptide class containing N-terminal fatty acids such as MG673929|5.0|5.0|
|<span id="melanin">melanin</span>|Melanin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="microviridin">microviridin</span>|Microviridin cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="mycosporine-like">mycosporine-like</span>|Molecules containing mycosporine-like amino acid|7.0|7.0|
|<span id="naggn">NAGGN</span>|N-acetylglutaminylglutamine amide|5.0|5.0|
|<span id="napaa">NAPAA</span>|non-alpha poly-amino acids like e-Polylysin|6.0|7.0|
|<span id="nrps">nrps</span>|Non-ribosomal peptide synthetase cluster|&lt;= 3.0|6.0|
|<span id="nrps-like"><span id="nrpsfragment">nrps-like</span></span>|NRPS-like fragment|5.0|5.0|
|<span id="nrp-metallophore">NRP-metallophore</span>|Non-ribosomal peptide metallophores|7.0|7.0|
|<span id="nrp-independent-siderophore">NRPS-independent-siderophore</span>|IucA/IucC-like siderophores (*siderophores* prior to 7.0)|7.0|7.0|
|<span id="nucleoside">nucleoside</span>|Nucleoside cluster|&lt;= 3.0|5.0|
|<span id="oligosaccharide">oligosaccharide</span>|Oligosaccharide cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="other">other</span>|Cluster containing a secondary metabolite-related protein that does not fit into any other category|4.0|5.0|
|<span id="pbde">PBDE</span>|Polybrominated diphenyl ether cluster|4.1|4.1|
|<span id="phenazine">phenazine</span>|Phenazine cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="phosphoglycolipid">phosphoglycolipid</span>|Phosphoglycolipid cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="phosphonate">phosphonate</span>|Phosphonate cluster|&lt;= 3.0|7.0|
|<span id="phosphonate-like">phosphonate-like</span>|Phosphonate-like cluster (prior to 7.0 this was the phosphonate rule)|7.0|7.0|
|<span id="pks-like">PKS-like</span>|Other types of PKS cluster|5.0|5.0|
|<span id="ppys-ks"><span id="ppysks">PpyS-KS</span></span>|PPY-like pyrone cluster|4.2|4.2|
|<span id="proteusin">proteusin</span>|Proteusin cluster|&lt;= 3.0|&lt;= 3.0 |
|<span id="pufa">PUFA</span>|Polyunsaturated fatty acid cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="pyrrolidine">pyrrolidine</span>|Pyrrolidines like described in BGC0001510|6.0|6.0|
|<span id="ranthipeptide">ranthipeptide</span>|Cys-rich peptides (aka. SCIFF: six Cys in fourty-five) like in CP001581:3481278-3502939|6.0|6.0|
|<span id="ras-ripp">RaS-RiPP</span>|Streptide-like thioether-bond RiPPs|5.0|5.0|
|<span id="redox-cofactor">redox-cofactor</span>|Redox-cofactors such as PQQ (NC_021985:1458906-1494876)|6.0|6.0|
|<span id="resorcinol">resorcinol</span>|Resorcinol cluster|&lt;= 3.0|&lt;= 3.0|
|<span id="ripp-like">RiPP-like</span>|Other unspecified ribosomally synthesised and post-translationally modified peptide product (RiPP) cluster|4.1|6.0|
|<span id="rre-containing">RRE-containing</span>|RRE-element containing cluster|6.0|6.0|
|<span id="saccharide">saccharide</span>|Saccharide cluster (loose strictness, likely from primary metabolism)|&lt;= 3.0|&lt;= 3.0|
|<span id="sactipeptide">sactipeptide</span>|Sactipeptide cluster|&lt;= 3.0|6.0|
|<span id="spliceotide">spliceotide</span>|RiPPs containing plpX type spliceases (NZ_KB235920:17899-42115)|6.0|6.0|
|<span id="t1pks">T1PKS</span>|Type I PKS (Polyketide synthase)|&lt;= 3.0|&lt;= 3.0|
|<span id="t2pks">T2PKS</span>|Type II PKS|&lt;= 3.0|5.0|
|<span id="t3pks">T3PKS</span>|Type III PKS|&lt;= 3.0|&lt;= 3.0|
|<span id="terpene">terpene</span>|Terpene|&lt;= 3.0|4.1|
|<span id="thioamitides">thioamitides</span>|Thioamitide RiPPs as found in JOBF01000011|5.1|6.0|
|<span id="thioamide-nrp">thioamide-NRP</span>|Thioamide-containing non-ribosomal peptide|5.0|5.0|
|<span id="thiopeptide">thiopeptide</span>|Thiopeptide cluster|4.2|5.0|
|<span id="transatpks"><span id="transat-pks">transAT-PKS</span></span>|Trans-AT PKS|&lt;= 3.0|5.0|
|<span id="transatpks-like"><span id="transat-pks-like">transAT-PKS-like</span></span>|Trans-AT PKS fragment, with trans-AT domain not found|&lt;= 5.0|5.0|
|<span id="tropodithietic-acid">tropodithietic-acid</span>|Tropodithietic acid cluster|5.0|5.0|



###Obsolete/Previous Types

|Label|Description|Added|Removed|Notes|
|-----|-----------|:---:|:-----:|-----|
|<span id="siderophore">siderophore</span>|Siderophore cluster|&lt;= 3.0|7.0|Renamed to *NRPS-independent-siderophore*|
|<span id="bacteriocin">bacteriocin</span>|Bacteriocin or other unspecified ribosomally synthesised and post-translationally modified peptide product (RiPP) cluster|4.1|6.0|Renamed to *RiPP-like*|
|<span id="fused">fused</span>|Pheganomycin-style protein ligase-containing cluster|4.0|6.0|Renamed to *guanidinotides*|
|<span id="head_to_tail">head_to_tail</span>|Head-to-tail cyclised (subtilosin-like) cluster|&lt;= 3.0|6.0|Merged into *sactipeptides*|
|<span id="lanthidin">lanthidin</span>|Glycosylated lanthipeptide/linaridin hybrids like MT210103|5.1|6.0|Renamed to *lanthipeptide class V*|
|<span id="lantipeptide"><span id="lanthipeptide">lanthipeptide</span></span>|Lanthipeptides|4.2|6.0|Split into subclasses, e.g. *lanthipeptide class I*|
|<span id="tfua-related">TfuA-related</span>|TfuA-related RiPPs|5.1|6.0|Renamed to *thioamitides*|
|<span id="otherks">otherks</span>|Other types of PKS cluster|&lt;= 3.0|5.0|Split into *PKS-like* and *hglE-KS*|
|<span id="microcin">microcin</span>|Microcin cluster|&lt;= 3.0|5.0|Merged into *lasso peptide*|
|<span id="cf_saccharide">cf_saccharide</span>|Possible saccharide cluster|&lt;= 3.0|5.0|Renamed to *saccharide*|
|<span id="cf_fatty_acid">cf_fatty_acid</span>|Possible fatty acid cluster|&lt;= 3.0|5.0|Renamed to *fatty_acid*|
|<span id="cf_putative">cf_putative</span>|Putative cluster of unknown type identified with the ClusterFinder algorithm|&lt;= 3.0|5.0|These predictions are now subregions, not clusters|


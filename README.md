
<!-- README.md is generated from README.Rmd. Please edit that file -->

# gtex_tissue_palette

<!-- badges: start -->
<!-- badges: end -->

The goal of gtex_tissue_palette is to provide a tab-delimited table of
GTEx tissue labels, associated colour HEX and RGB codes.

Data wrangled from the Broad Institute files [gene expression by
tissue](https://github.com/broadinstitute/gtex-public/blob/master/scripts/gene_expression_by_tissue.py)
and
[colors.json](https://raw.githubusercontent.com/broadinstitute/gtex-viz/7cfffd65f19fbcad216a0df3325cfd89e40d6952/boxplot/dev/colors.json)

``` r
library(tidyverse)
```

## Read data

``` r

setwd('~/Git/gtex_tissue_palette/')
gtx_tissue_col <- read_rds('gtex_tissue_col_hex.Rds')
```

``` r

gtx_tissue_col %>% arrange(desc(tissue_paste)) %>% tidyExt::print_all()
#> # A tibble: 56 × 7
#>    tissue_paste                      tissu…¹ smts  smtd  tissu…² tissu…³ tissu…⁴
#>    <fct>                             <fct>   <fct> <fct> <fct>   <fct>   <fct>  
#>  1 Adipose_Subcutaneous              Adipos… Adip… Subc… ADPSBQ  #FFA54F 255165…
#>  2 Adipose_Visceral_Omentum          Adipos… Adip… Visc… ADPVSC  #EE9A00 2381540
#>  3 Adrenal_Gland                     Adrena… Adre… Adre… ADRNLG  #8FBC8F 143188…
#>  4 Artery_Aorta                      Artery… Arte… Aorta ARTAORT #8B1C62 1392898
#>  5 Artery_Coronary                   Artery… Arte… Coro… ARTCRN  #EE6A50 238106…
#>  6 Artery_Femoral                    Artery… Arte… Femo… ARTFMR  #FF4500 255690 
#>  7 Artery_Tibial                     Artery… Arte… Tibi… ARTTBL  #FF0000 25500  
#>  8 Bladder                           Bladder Blad… Blad… BLDDER  #CDB79E 205183…
#>  9 Brain_Amygdala                    Brain … Brain Amyg… BRNAMY  #EEEE00 2382380
#> 10 Brain_Anterior_cingulate_cortex_… Brain … Brain Ante… BRNACC  #EEEE00 2382380
#> 11 Brain_Caudate_basal_ganglia       Brain … Brain Caud… BRNCDT  #EEEE00 2382380
#> 12 Brain_Cerebellar_Hemisphere       Brain … Brain Cere… BRNCHB  #EEEE00 2382380
#> 13 Brain_Cerebellum                  Brain … Brain Cere… BRNCHA  #EEEE00 2382380
#> 14 Brain_Cortex                      Brain … Brain Cort… BRNCTXA #EEEE00 2382380
#> 15 Brain_Frontal_Cortex_BA9          Brain … Brain Fron… BRNCTXB #EEEE00 2382380
#> 16 Brain_Hippocampus                 Brain … Brain Hipp… BRNHPP  #EEEE00 2382380
#> 17 Brain_Hypothalamus                Brain … Brain Hypo… BRNHPT  #EEEE00 2382380
#> 18 Brain_Nucleus_accumbens_basal_ga… Brain … Brain Nucl… BRNNCC  #EEEE00 2382380
#> 19 Brain_Putamen_basal_ganglia       Brain … Brain Puta… BRNPTM  #EEEE00 2382380
#> 20 Brain_Spinal_cord_cervical_c-1)   Brain … Brain Spin… BRNSPC  #EEEE00 2382380
#> 21 Brain_Substantia_nigra            Brain … Brain Subs… BRNSNG  #EEEE00 2382380
#> 22 Breast_Mammary_Tissue             Breast… Brea… Mamm… BREAST  #00CDCD 0205205
#> 23 Cells_EBV-transformed_lymphocytes Cells … Cells EBV   LCL     #EE82EE 238130…
#> 24 Cells_Transformed_fibroblasts     Cells … Cells Tran… FIBRBLS #9AC0CD 154192…
#> 25 Cervix_Ectocervix                 Cervix… Cerv… Ecto… CVXECT  #EED5D2 238213…
#> 26 Cervix_Endocervix                 Cervix… Cerv… Endo… CVSEND  #EED5D2 238213…
#> 27 Colon_Sigmoid                     Colon … Colon Sigm… CLNSGM  #CDB79E 205183…
#> 28 Colon_Transverse                  Colon … Colon Tran… CLNTRN  #EEC591 238197…
#> 29 Esophagus_Gastroesophageal_Junct… Esopha… Esop… Gast… ESPGEJ  #8B7355 139115…
#> 30 Esophagus_Mucosa                  Esopha… Esop… Muco… ESPMCS  #8B7355 139115…
#> 31 Esophagus_Muscularis              Esopha… Esop… Musc… ESPMSL  #CDAA7D 205170…
#> 32 Fallopian_Tube                    Fallop… Fall… Fall… FLLPNT  #EED5D2 238213…
#> 33 Heart_Atrial_Appendage            Heart … Heart Atri… HRTAA   #B452CD 180822…
#> 34 Heart_Left_Ventricle              Heart … Heart Left… HRTLV   #7A378B 122551…
#> 35 Kidney_Cortex                     Kidney… Kidn… Cort… KDNCTX  #CDB79E 205183…
#> 36 Kidney_Medulla                    Kidney… Kidn… Medu… KDNMDL  #CDB79E 205183…
#> 37 Liver                             Liver   Liver Liver LIVER   #CDB79E 205183…
#> 38 Lung                              Lung    Lung  Lung  LUNG    #9ACD32 154205…
#> 39 Minor_Salivary_Gland              Minor … Mino… Mino… SLVRYG  #CDB79E 205183…
#> 40 Muscle_Skeletal                   Muscle… Musc… Skel… MSCLSK  #7A67EE 122103…
#> 41 Nerve_Tibial                      Nerve … Nerve Tibi… NERVET  #FFD700 2552150
#> 42 Ovary                             Ovary   Ovary Ovary OVARY   #FFB6C1 255182…
#> 43 Pancreas                          Pancre… Panc… Panc… PNCREAS #CD9B1D 205155…
#> 44 Pituitary                         Pituit… Pitu… Pitu… PTTARY  #B4EEB4 180238…
#> 45 Prostate                          Prosta… Pros… Pros… PRSTTE  #D9D9D9 217217…
#> 46 Retina                            Retina  Reti… Reti… RETINA  #FBFB00 2512510
#> 47 Skin_Not_Sun_Exposed_Suprapubic   Skin -… Skin  Not … SKINNS  #3A5FCD 5895205
#> 48 Skin_Sun_Exposed_Lower_leg        Skin -… Skin  Sun … SKINS   #1E90FF 301442…
#> 49 Small_Intestine_Terminal_Ileum    Small … Smal… Term… SNTTRM  #CDB79E 205183…
#> 50 Spleen                            Spleen  Sple… Sple… SPLEEN  #CDB79E 205183…
#> 51 Stomach                           Stomach Stom… Stom… STMACH  #FFD39B 255211…
#> 52 Testis                            Testis  Test… Test… TESTIS  #A6A6A6 166166…
#> 53 Thyroid                           Thyroid Thyr… Thyr… THYROID #008B45 013969 
#> 54 Uterus                            Uterus  Uter… Uter… UTERUS  #EED5D2 238213…
#> 55 Vagina                            Vagina  Vagi… Vagi… VAGINA  #EED5D2 238213…
#> 56 Whole_Blood                       Whole … Whol… Whol… WHLBLD  #FF00FF 2550255
#> # … with abbreviated variable names ¹​tissue_hr, ²​tissue_abbrv,
#> #   ³​tissue_color_hex, ⁴​tissue_color_rgb
```

Note
[**gtex_tissue_col_hex.tsv**](https://github.com/bansell/gtex_tissue_palette/blob/main/gtex_tissue_col_hex.tsv)
is also provided. Note this does not preserve the factor order for
plotting.

To enforce the alphabetical order on the vertical axis if using
gtex_tissue_col_hex.tsv:

``` r
gtx_tissue_col <- gtx_tissue_col %>% 
  arrange(desc(tissue_paste)) %>%
   mutate(across(.fns=~fct_inorder(.)))
  
```

## Plot the palette

``` r

gtx_tissue_col %>% 
  ggplot(aes(y=tissue_hr,x="",fill=tissue_color_hex)) + 
  geom_tile(col='white',lwd=0.75,show.legend = F,cex=5) +
  geom_text(aes(label=tissue_color_hex),cex=3) +
  scale_fill_identity()+ theme_classic() + xlab('') + ylab('')
```

<img src="README_files/figure-gfm/unnamed-chunk-7-1.png" width="100%" height="175%" />

<!-- devtools::build_readme()  -->

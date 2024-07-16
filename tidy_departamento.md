Poblacion \| departamento
================
LL

# librerias

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

# TIDY

## Especifico: amazonas

``` r
amazonas_masculino <- read.xlsx("poblacion/departamentos/inei_departamentos_bol25 2/amazonas.xlsx", sheet = "AMAZONAS M", startRow = 4)
amazonas_femenino <- read.xlsx("poblacion/departamentos/inei_departamentos_bol25 2/amazonas.xlsx", sheet = "AMAZONAS F", startRow = 4)
levels(as.factor(amazonas_masculino$Edad))
```

    ##  [1] " 10-14"                                                  
    ##  [2] " 15-19"                                                  
    ##  [3] " 20-24"                                                  
    ##  [4] " 25-29"                                                  
    ##  [5] " 30-34"                                                  
    ##  [6] " 35-39"                                                  
    ##  [7] " 40-44"                                                  
    ##  [8] " 45-49"                                                  
    ##  [9] " 5-9"                                                    
    ## [10] " 50-54"                                                  
    ## [11] " 55-59"                                                  
    ## [12] " 60-64"                                                  
    ## [13] " 65-69"                                                  
    ## [14] " 70-74"                                                  
    ## [15] " 75-79"                                                  
    ## [16] " 80 y +"                                                 
    ## [17] "0"                                                       
    ## [18] "0-4"                                                     
    ## [19] "1"                                                       
    ## [20] "10"                                                      
    ## [21] "11"                                                      
    ## [22] "12"                                                      
    ## [23] "13"                                                      
    ## [24] "14"                                                      
    ## [25] "15"                                                      
    ## [26] "16"                                                      
    ## [27] "17"                                                      
    ## [28] "18"                                                      
    ## [29] "19"                                                      
    ## [30] "2"                                                       
    ## [31] "20"                                                      
    ## [32] "21"                                                      
    ## [33] "22"                                                      
    ## [34] "23"                                                      
    ## [35] "24"                                                      
    ## [36] "25"                                                      
    ## [37] "26"                                                      
    ## [38] "27"                                                      
    ## [39] "28"                                                      
    ## [40] "29"                                                      
    ## [41] "3"                                                       
    ## [42] "30"                                                      
    ## [43] "31"                                                      
    ## [44] "32"                                                      
    ## [45] "33"                                                      
    ## [46] "34"                                                      
    ## [47] "35"                                                      
    ## [48] "36"                                                      
    ## [49] "37"                                                      
    ## [50] "38"                                                      
    ## [51] "39"                                                      
    ## [52] "4"                                                       
    ## [53] "40"                                                      
    ## [54] "41"                                                      
    ## [55] "42"                                                      
    ## [56] "43"                                                      
    ## [57] "44"                                                      
    ## [58] "45"                                                      
    ## [59] "46"                                                      
    ## [60] "47"                                                      
    ## [61] "48"                                                      
    ## [62] "49"                                                      
    ## [63] "5"                                                       
    ## [64] "50"                                                      
    ## [65] "51"                                                      
    ## [66] "52"                                                      
    ## [67] "53"                                                      
    ## [68] "54"                                                      
    ## [69] "55"                                                      
    ## [70] "56"                                                      
    ## [71] "57"                                                      
    ## [72] "58"                                                      
    ## [73] "59"                                                      
    ## [74] "6"                                                       
    ## [75] "60"                                                      
    ## [76] "61"                                                      
    ## [77] "62"                                                      
    ## [78] "63"                                                      
    ## [79] "64"                                                      
    ## [80] "65"                                                      
    ## [81] "66"                                                      
    ## [82] "67"                                                      
    ## [83] "68"                                                      
    ## [84] "69"                                                      
    ## [85] "7"                                                       
    ## [86] "70"                                                      
    ## [87] "71"                                                      
    ## [88] "72"                                                      
    ## [89] "73"                                                      
    ## [90] "74"                                                      
    ## [91] "75"                                                      
    ## [92] "76"                                                      
    ## [93] "77"                                                      
    ## [94] "78"                                                      
    ## [95] "79"                                                      
    ## [96] "8"                                                       
    ## [97] "9"                                                       
    ## [98] "Fuente: Instituto nacional de Estadística e Informática."
    ## [99] "TOTAL"

``` r
# mantener valores puntuales de edad...0:79 y 80 y +
amazonas_masculino1 <- amazonas_masculino %>% 
    filter(Edad %in% c("0", "1", "2", "3", "4", 
        "5", "6", "7", "8", "9", "10", "11", "12", 
            "13", "14", "15", "16", "17", "18", "19", 
                "20", "21", "22", "23", "24", "25", "26", 
                    "27", "28", "29", "30", "31", "32", "33", 
                        "34", "35", "36", "37", "38", "39", "40", 
                            "41", "42", "43", "44", "45", "46", "47", 
                                "48", "49", "50", "51", "52", "53", "54", 
                                    "55", "56", "57", "58", "59", "60", "61", 
                                        "62", "63", "64", "65", "66", "67", "68", 
                                            "69", "70", "71", "72", "73", "74", "75", 
                                                "76", "77", "78", "79", " 80 y +"))
#femenino
amazonas_femenino1 <- amazonas_femenino %>% 
    filter(Edad %in% c("0", "1", "2", "3", "4", 
        "5", "6", "7", "8", "9", "10", "11", "12", 
            "13", "14", "15", "16", "17", "18", "19", 
                "20", "21", "22", "23", "24", "25", "26", 
                    "27", "28", "29", "30", "31", "32", "33", 
                        "34", "35", "36", "37", "38", "39", "40", 
                            "41", "42", "43", "44", "45", "46", "47", 
                                "48", "49", "50", "51", "52", "53", "54", 
                                    "55", "56", "57", "58", "59", "60", "61", 
                                        "62", "63", "64", "65", "66", "67", "68", 
                                            "69", "70", "71", "72", "73", "74", "75", 
                                                "76", "77", "78", "79", " 80 y +"))

# valores missings
missing_amazonas_masculino1 <- amazonas_masculino1 %>%
    summarise_all(~ sum(is.na(.))) %>%
    pivot_longer(everything(), names_to = "variable", values_to = "n")
missing_amazonas_masculino1
```

    ## # A tibble: 37 × 2
    ##    variable     n
    ##    <chr>    <int>
    ##  1 Edad         0
    ##  2 1995         0
    ##  3 1996         0
    ##  4 1997         0
    ##  5 1998         0
    ##  6 1999         0
    ##  7 2000         0
    ##  8 2001         0
    ##  9 2002         0
    ## 10 2003         0
    ## # ℹ 27 more rows

``` r
# columnas de años a observaciones y añadir var sexo
amazonas_masculino2 <- amazonas_masculino1 %>%
    pivot_longer(-Edad, names_to = "año", values_to = "poblacion")
amazonas_masculino2$sexo <- "masculino"

amazonas_femenino2 <- amazonas_femenino1 %>%
    pivot_longer(-Edad, names_to = "año", values_to = "poblacion")
amazonas_femenino2$sexo <- "femenino"

# unir femenino y masculino añadiendo variable masculino y femenino
amazonas <- amazonas_masculino2 %>%
    bind_rows(amazonas_femenino2)
write.xlsx(amazonas, "amazonas_sexo_edad2.xlsx")
```

# Funcion

``` r
procesar_datos <- function(file_path, sheets) {
    datos_masculino <- read.xlsx(file_path, sheet = sheets$masculino, startRow = 4)
    datos_femenino <- read.xlsx(file_path, sheet = sheets$femenino, startRow = 4)

    edades <- as.character(0:79)
    edades <- c(edades, " 80 y +")

    datos_masculino1 <- datos_masculino %>% filter(Edad %in% edades)
    datos_femenino1 <- datos_femenino %>% filter(Edad %in% edades)

    # add sexo | columnas a filas años
    datos_masculino2 <- datos_masculino1 %>%
        pivot_longer(-Edad, names_to = "año", values_to = "poblacion") %>%
        mutate(sexo = "masculino")

    datos_femenino2 <- datos_femenino1 %>%
        pivot_longer(-Edad, names_to = "año", values_to = "poblacion") %>%
        mutate(sexo = "femenino")

    # Join
    datos_final <- bind_rows(datos_masculino2, datos_femenino2)
    write.xlsx(datos_final, paste0(gsub(".xlsx", "", basename(file_path)), "_sexo_edad.xlsx"))

    return(datos_final)
}
```

# Aplicar a departamentos

``` r
# 1. AMAZONAS
sheets <- list(masculino = "AMAZONAS M", femenino = "AMAZONAS F")
amazonas <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/amazonas.xlsx", sheets)
amazonas$departamento <- "amazonas"

# 2. ANCASH
sheets <- list(masculino = "ÁNCASH M", femenino = "ÁNCASH F")
ancash <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/ancash.xlsx", sheets)
ancash$departamento <- "ancash"

# 3. APURIMAC
sheets <- list(masculino = "APURÍMAC M", femenino = "APURÍMAC F")
apurimac <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/apurimac.xlsx", sheets)
apurimac$departamento <- "apurimac"

# 4 AREQUIPA
sheets <- list(masculino = "AREQUIPA M", femenino = "AREQUIPA F")
arequipa <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/arequipa.xlsx", sheets)
arequipa$departamento <- "arequipa"

# 5 AYACUCHO
sheets <- list(masculino = "AYACUCHO M", femenino = "AYACUCHO F")
ayacucho <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/ayacucho.xlsx", sheets)
ayacucho$departamento <- "ayacucho"

# 6 CAJAMARCA
sheets <- list(masculino = "CAJAMARCA M", femenino = "CAJAMARCA F")
cajamarca <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/cajamarca.xlsx", sheets)
cajamarca$departamento <- "cajamarca"

# 7 CALLAO
sheets <- list(masculino = "PROV. DEL CALLAO M", femenino = "PROV. DEL CALLAO F")
callao <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/provincia_callao.xlsx", sheets)
callao$departamento <- "callao"

# 8 CUSCO
sheets <- list(masculino = "CUSCO M", femenino = "CUSCO F")
cusco <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/cusco.xlsx", sheets)
cusco$departamento <- "cusco"

# 9 HUANCAVELICA
sheets <- list(masculino = "HUANCAVELICA M", femenino = "HUANCAVELICA F")
huancavelica <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/huancavelica.xlsx", sheets)
huancavelica$departamento <- "huancavelica"

# 10. HUÁNUCO
sheets <- list(masculino = "HUÁNUCO M", femenino = "HUÁNUCO F")
huanuco <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/huanuco.xlsx", sheets)
huanuco$departamento <- "huanuco"

# 11. ICA
sheets <- list(masculino = "ICA M", femenino = "ICA F")
ica <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/ica.xlsx", sheets)
ica$departamento <- "ica"


# 12. JUNÍN
sheets <- list(masculino = "JUNÍN M", femenino = "JUNÍN F")
junin <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/junin.xlsx", sheets)
junin$departamento <- "junin"

# 13. LA LIBERTAD
sheets <- list(masculino = "LA LIBERTAD M", femenino = "LA LIBERTAD F")
lalibertad <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/lalibertad.xlsx", sheets)
lalibertad$departamento <- "la libertad" 

# 14. LAMBAYEQUE
sheets <- list(masculino = "LAMBAYEQUE M", femenino = "LAMBAYEQUE F")
lambayeque <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/lambayeque.xlsx", sheets)
lambayeque$departamento <- "lambayeque"

# 15. LIMA  
sheets <- list(masculino = "LIMA M", femenino = "LIMA F")
lima <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/lima.xlsx", sheets)
lima$departamento <- "lima"

# 16. LORETO
sheets <- list(masculino = "LORETO M", femenino = "LORETO F")
loreto <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/loreto.xlsx", sheets)
loreto$departamento <- "loreto"

# 17. MADRE DE DIOS
sheets <- list(masculino = "MADRE DE DIOS M", femenino = "MADRE DE DIOS F")
madrededios <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/madrededios.xlsx", sheets)
madrededios$departamento <- "madre de dios"

# 18. MOQUEGUA
sheets <- list(masculino = "MOQUEGUA M", femenino = "MOQUEGUA F")
moquegua <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/moquegua.xlsx", sheets)
moquegua$departamento <- "moquegua"

# 19. PASCO
sheets <- list(masculino = "PASCO M", femenino = "PASCO F")
pasco <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/pasco.xlsx", sheets)
pasco$departamento <- "pasco"

# 20. PIURA
sheets <- list(masculino = "PIURA M", femenino = "PIURA F")
piura <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/piura.xlsx", sheets)
piura$departamento <- "piura"

# 21. PUNO
sheets <- list(masculino = "PUNO M", femenino = "PUNO F")
puno <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/puno.xlsx", sheets)
puno$departamento <- "puno"

# 22. SAN MARTÍN
sheets <- list(masculino = "SAN MARTIN M", femenino = "SAN MARTIN F")
sanmartin <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/sanmartin.xlsx", sheets)
sanmartin$departamento <- "san martin"

# 23. TACNA
sheets <- list(masculino = "TACNA M", femenino = "TACNA F")
tacna <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/tacna.xlsx", sheets)
tacna$departamento <- "tacna"

# 24. TUMBES
sheets <- list(masculino = "TUMBES M", femenino = "TUMBES F")
tumbes <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/tumbes.xlsx", sheets)
tumbes$departamento <- "tumbes"

# 25. UCAYALI
sheets <- list(masculino = "UCAYALI M", femenino = "UCAYALI F")
ucayali <- procesar_datos("poblacion/departamentos/inei_departamentos_bol25 2/ucayali.xlsx", sheets)
ucayali$departamento <- "ucayali"

# join data
poblacion <- bind_rows(amazonas, ancash, apurimac, arequipa, ayacucho, cajamarca, 
    callao, cusco, huancavelica, huanuco, ica, junin, lalibertad, lambayeque, lima, 
        loreto, madrededios, moquegua, pasco, piura, puno, sanmartin, tacna, tumbes, ucayali)
```

# crear xlsx

``` r
write.xlsx(poblacion, "poblacion_regiones_1995_2030.xlsx")
```

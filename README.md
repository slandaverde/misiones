# Cálculo Misiones 

## ÍNDICE
  - [1. Quick Start](#1-quick-start)
  - [2. Misiones](#2-misiones)
  - [3. Archivos](#3-archivos)
  - [4. Tableau Prep](#4-tableau-prep)
  - [5. Archivo Misiones](#5-archivo-misiones)


## 1. Quick Start
Reminders de los cambios necesarios para correr el flujo:


Archivos
- Actualizar los archivos en la carpeta DATA y CORP CSTMR
  - TIGO MEDIA: 
     - Cambiar el archivo (Que quede solo la tabla)
   - Cartera X Producto
     - Hacer copia de archivo en carpeta DATA
     - Sacar sábana y hacer pivot con "Cd-Cod Producto-Sum of Rvn Usd Amount". Ponerle como nombre a la hoja: Carteraxproducto
Tableau Prep Flow:
- GESTOR
  - El monto tiene como nombre el tipo de cambio. Cambiarlo en el flow para que corra
- TIGO MEDIA
    - El monto tiene como nombre el tipo de cambio. Cambiarlo en el flow para que corra
    - Llenar en el flujo el AÑO-MES-DÍA
- WD
  - Revisar la lista de "group" para que se esté tomando todo lo que sea WD
- CLOUD
  - Revisar que todo lo que esté en la lista "group" sea Cloud
- Archivo Consolidado
  - Calcular:
    - MOVIL
      - Filtrar: Producto TB > CIN / VPN y HANDSET
      - Valores: RGU
    - SOLUCIONES
      - Filtrar: SOLUCION > SOLUCION
      - Valores: $ (Monto)
    - TEL.FIJA
      - Filtrar: Producto TB > TELEFONIA FIJA
      - Valores: $ (Monto)
    - CROSS NEW
      - Filtrar: CROSS NEW > CROSS SELL
      - Hacer un count if por Ejecutivo y sumarle los clientes "New"
    - FIJOS
      - Filtrar: Producto Global > FIJO
      - Valores: RGU
    - CCC (Clientes con compra)
      - Valores: NITs
  
  **DESPUES DEL OUTPUT AGREGAR MEMOS MANUALMENTE**




## 2. Misiones
 El cálculo de misiones se refiere al cálculo y medición del alcance de ciertas métricas que deben alcanzar a los ejecutivos. Dependiendo del segmento al que pertenecen, las misiones varían tanto en enfoque como en monto. 
 
 La información requerida para el cálculo de misiones proviene del cierre de ventas de cada mes compartida por Juan Perez. Actualmente, se debe entregar el cálculo de misioens a más tardar el *12 de cada mes* al departamento de comisiones (vmvillagran@tigo.com.gt).  


 
## 3. Archivos
Los archivos requeridos para el cálculo de misiones son:

|No| Archivo | Actualización | Fuente | Ubicación|
|--| --- | --- | --- | ----|
|1| As-400 y Navega al 31 **MES - AÑO**| Mensual | Cierre | Documentos\3. Misiones\Flow_Misiones\Data|
|2| COMISIONES BUSSINES **MES - AÑO**, TIGO MEDIA | Mensual | Cierre | Documentos\3. Misiones\Flow_Misiones\Data|
|3| DM Gestor **MES - AÑO** | Mensual | Cierre | Documentos\3. Misiones\Flow_Misiones\Data|
|4| Cartera por producto **MES - AÑO**| Mensual | SG | Documentos\3. Misiones\Flow_Misiones\Data|
|5| Corp Customer **MES - AÑO**| Mensual | SG | Documentos\12. Corp Customer\ **AÑO** \ **MES**|
 


   1. As-400 y Navega al 31 **XX** 2019 - FINAL
     
           Las hojas del archivo que son útiles para el cálculo de misiones son: 
            - AS400 Y NP ENE 15
            - PTT SEPTIEMBRE 14
            - POS al SEPI 14
            - SFM SEPTIEMBRE 14
            - Resumen x Ejecutivo (Extraer los MEMOS)

        Nota: Ninguna hoja necesita cambios para que el flujo corra.

     
  1. COMISIONES BUSSINES **XX** 2019, TIGO MEDIA
   
          El archivo viene con columnas y filas vacías antes de la tabla. 
     ![TM RAW](https://github.com/slandaverde/misiones/blob/master/TIGO_MEDIA_RAW.png)

         Para que el flujo funcione, se deben quitar las filas vacías y además de quitar las columnas vacías, se debe dejar solo las columnas funcionales (a partir de la columna X)


     ![TM US](https://github.com/slandaverde/misiones/blob/master/TIGO_MEDIA_USE.png)
     
        

  2. DM Gestor **XX**

         La hoja del archivo que se ultiliza en el flow es: BASE

  3. Cartera por producto **XX** 
   
         Hay que colocar una copia de la cartera por producto en la carpeta DATA. El archivo trae una pivot que hay que expandir para obtener la tabla:
         
        ![CarteraxProd](https://github.com/slandaverde/misiones/blob/master/CARTERA_X_PRODUCTO.png)
        
        ![TablaFact](https://github.com/slandaverde/misiones/blob/master/TABLA_FACTURACION.png  )
     
             
         Después hacer una pivot con: 
         |Business Cd|Cod Producto|Sum of Rvn Usd Amount|
         Ponerle como nombre a la hoja *Carteraxproducto*

       ![CarteraxProdfinal](https://github.com/slandaverde/misiones/blob/master/Carteraxproductofinal.png)
         
  4. Corp Customer **XX** 
  
   
          La hoja del archivo que se ultiliza en el flow es: CORP_CSTMR

## 4. Tableau Prep
Se creó un flow de tableau prep para automatizar el cálculo de la tabla para el cálulo de misiones. Para que el archivo corra sin problema se deben tomar en cuenta los siguientes puntos:

1. PARTE I: UNIR VENTA AS400, PTT, SFM, POS <br/>
   - A PTT, POS y SFM colocar
     - Producto TB: PTT, POS y SFM (Según corresponda)
     - Producto Global: VAS 
     - SOLUCION: SOLUCION
   - Añadir RGU = 1 
   - Se deben aplicar los filtros: 
      - BS UN CD = CORPORATE
      - DISTRIBUIDOR AS400 = 
        - CANALES TIGO BUSINESS
        - CLAUDIA ZAPETA
        - EQUIPO GAMA
        - GENERAL TERRITORY NEWSALES
        - NAVEGAPLUS
        - PYMES
        - SERVICE ACCOUNT ORGANIC SALES
        - SIEBEL
        - SINERGIAS Y TELEVENTAS TIGO BUSINSES
      - Solo líneas con estructura comercial (EJEC-COORD-GER)
      - Se deben tomar los montos en USD.
     
    ![PI](https://github.com/slandaverde/misiones/blob/master/TPREP_PARTE_I.png)

  
2. PARTE II: AGREGAR GESTOR Y TIGO MEDIA
   - GESTOR 
     - Renombrar la columna con tipo de cambio a Monto
     - Agregar
       - Producto TB: CIN / VPN
       - Producto Global: MOVIL 
       - SOLUCION: MOVIL
     - Renombrar campos para que coincidan con otras tablas para unirlas
     - Se deben aplicar los filtros:
         - COMENTARIOS = PROCEDE
         - STATUS =  UPGRADE 
   - TIGO MEDIA
     - Renombrar la columna con tipo de cambio a Monto
     - Renombrar campos para que coincidan con otras tablas para unirlas
     - Agregar
       - Producto TB: TIGO MEDIA
       - Producto Global: VAS 
       - SOLUCION: SOLUCION        

   ![PII](https://github.com/slandaverde/misiones/blob/master/TPREP_PARTE_II.png)

3. PARTE III: AGREGAR CÓDIGO TIGO BUSINESS
   - Buscar por **código cliente**
     - CORP_CSTMR
       - Separar por sistema (AS400 - NP Y SIEBEL)
       - Hacer tabla con cod cliente y COD TB
     - DATA
       -  Separar por sistema (AS400 - NP)
   - Buscar por **nombre cliente**
       - CORP_CSTMR
         - Hacer tabla con nombre del cliente y COD TB
       - DATA
         - Separar las líneas con COD TB y las que no
         - Unir solo las que no tienen código TB por nombre cliente
   - Buscar por **NIT**
      - CORP_CSTMR
         - Hacer tabla con NIT y COD TB
         - Excluir los NITS que sean CF
       - DATA
         - Separar las líneas con COD TB y las que no
         - Unir solo las que no tienen código TB por nombre cliente
   - Volver a unir las tablas

    ![PIII](https://github.com/slandaverde/misiones/blob/master/TPREP_PARTE_III.png)

4. PARTE IV: RGUs TIGO STAR, REVISIÓN DE CLOUD Y WD
   - Separar productos a revisar
     - TIGO STAR
       - Calcular RGUs por ANEXO (1/Cantidad de RGU)
     - WD
       - Filtrar por columna "Nombre de Venta FIJOS":
         - ANTIVIRUS
         - FIREWALL ADMINISTRADO
         - EQUIPOS DE SEGURIDAD
         - INSTALACION
         - LICENCIAS DE SEGURIDAD
         - SERVICIOS PROFESIONALES 
     - CLOUD 
       - Filtrar por columna "Nombre de Venta FIJOS":
         - CLOUD GOOGLE
         - CLOUD GOOGLE / NOC
         - CLOUD MICROSOFT O365
         - CLOUD MICROSOFT O365 / NOC
         - CLOUD OTROS SERVICIOS (MENSUALES)
         - CLOUD OTROS SERVICIOS (MENSUALES) / NOC
         - CLOUD PLUS
         - CLOUD PRO-M PLUS
         - CLOUD PRO-M SUPER
         - CLOUD SERVICIOS INT / NOC
         - CLOUD SUPER

    ![PIV](https://github.com/slandaverde/misiones/blob/master/TPREP_PARTE_IV.png)

5. PARTE V: Agregar MEMOS, Cálculo CROSS NEW, y eliminar duplicados
     - Incluir MEMOS
       - De la hoja Resumen X Ejecutivo sacar los memos y agregar la información de cada columna
     - Calcular la columna CROSS NEW
       - Cruzar la cartera por producto con DATA por COD TB y PROD TB
       - Criterios:
         - CROSS SELL: Facturación = 0
         - UPSELL: Facturación > 0
         - NEW SELL: No tiene COD TB
    - Por seguridad se hace un aggregate para quitar duplicados (lo mejor es revisar que hayan la misma cantidad de líneas al inicio del flujo con el final)
 
    ![PV](https://github.com/slandaverde/misiones/blob/master/TPREP_PARTE_V.png)


## 5. Archivo Misiones

Con el output de Tableau Prep hacer:

- MOVIL
  - Filtrar: Producto TB > CIN / VPN y HANDSET
  - Valores: RGU 

|Gerente|Coordinador|Vendedor|Producto TB|
|-|-|-|-| 
 <br/>

   ![MOVIL](https://github.com/slandaverde/misiones/blob/master/FINAL_MOVIL.png)

- SOLUCIONES
  - Filtrar: SOLUCION > SOLUCION
  - Valores: $ (Monto)    

|Gerente|Coordinador|Vendedor|Producto TB|
|-|-|-|-|
<br/>

   - Hacer tabla para la estructura:

|TEL. FIJA|SOL. + TEL. |SOL SIN WD|
|-|-|-|
<br/> 

   ![SOL](https://github.com/slandaverde/misiones/blob/master/FINAL_SOLUCIONES.png)
- TEL.FIJA
  - Filtrar: Producto TB > TELEFONIA FIJA
  - Valores: $ (Monto)

|Gerente|Coordinador|Vendedor|Producto TB|
|-|-|-|-| 
  <br/>

  ![TF](https://github.com/slandaverde/misiones/blob/master/FINAL_TEL_FIJA.png)


- CROSS NEW
  - Filtrar: CROSS NEW > CROSS SELL  

|Gerente|Coordinador|Vendedor|Cod TB|
|-|-|-|-| 
<br/>
   - Hacer un count if por Ejecutivo y sumarle los clientes "New"

  ![cross](https://github.com/slandaverde/misiones/blob/master/FINAL_CROSS.png)

- FIJOS
  -  Filtrar: Producto Global > FIJO
  - Valores: RGU  

|Gerente|Coordinador|Vendedor|Producto TB|
|-|-|-|-| 
<br/>

  ![F](https://github.com/slandaverde/misiones/blob/master/FINAL_FIJOS.png)
- CCC
  - Valores: NITs  

|Gerente|Coordinador|Vendedor|Count NIT|
|-|-|-|-|
<br/>

  ![ccc](https://github.com/slandaverde/misiones/blob/master/FINAL_CCC.png)

# Cálculo Misiones 

## ÍNDICE
1. Misiones
2. Archivos
3. Tableau Prep
4. Notas


## 1. Misiones
 El cálculo de misiones se refiere al cálculo y medición del alcance de ciertas métricas que deben alcanzar a los ejecutivos. Dependiendo del segmento al que pertenecen, las misiones varían tanto en enfoque como en monto. 
 
 La información requerida para el cálculo de misiones proviene del cierre de ventas de cada mes compartida por Erick Marroquín. Actualmente, se debe entregar el cálculo de misioens a más tardar el 12 de cada mes al departamento de comisiones (vmvillagran@tigo.com.gt).  


 
## 2. Archivos
Los archivos requeridos para el cálculo de misiones son:

  1. As-400 y Navega al 31 **XX** 2019 - FINAL
   
    Las hojas del archivo que son útiles para el cálculo de misiones son. 
       - AS400 Y NP ENE 15
       - PTT SEPTIEMBRE 14
       - POS al SEPI 14
       - SFM SEPTIEMBRE 14
       - Resumen x Ejecutivo (Extraer los MEMOS)


      Se deben aplicar los filtros: 
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
      - SOLO LÍNEAS CON ESTRUCTURA COMERCIAL (EJEC-COORD-GER)

    Se deben tomar los montos en USD. 



  2. COMISIONES BUSSINES **XX** 2019, TIGO MEDIA
  3. DM Gestor **XX**19
   
    Las hoja del archivo que es útil para el cálculo de misiones es: 
       - BASE
    
    Se deben aplicar los filtros: 
      - COMENTARIOS = PROCEDE
      - STATUS =  UPGRADE   

   
  4. Cartera por producto **XX**19  
    
  5. Corp Customer **XX**2019


XX = El mes correspondiente al cierre




## 3. Tableau Prep
Se creó un flow de tableau prep para automatizar el cálculo de la tabla para el cálulo de misiones. Para que el archivo corra sin problema se deben tomar en cuenta los siguientes puntos:





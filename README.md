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
      |-|-|-|-| 
  <br/>

   - Hacer tabla para la estructura:
     |TEL. FIJA|SOL. + TEL. |SOL SIN WD|
     |-|-|-|
     |-|-|-| 
  <br/> 

   ![SOL](https://github.com/slandaverde/misiones/blob/master/FINAL_SOLUCIONES.png)
- TEL.FIJA
  - Filtrar: Producto TB > TELEFONIA FIJA
  - Valores: $ (Monto)
      |Gerente|Coordinador|Vendedor|Producto TB|
      |-|-|-|-| 
      |-|-|-|-|
  <br/>

  ![TF](https://github.com/slandaverde/misiones/blob/master/FINAL_TEL_FIJA.png)


- CROSS NEW
  - Filtrar: CROSS NEW > CROSS SELL  
    |Gerente|Coordinador|Vendedor|Cod TB|
    |-|-|-|-| 
    |-|-|-|-|
    <br/>
   - Hacer un count if por Ejecutivo y sumarle los clientes "New"

  ![cross](https://github.com/slandaverde/misiones/blob/master/FINAL_CROSS.png)

- FIJOS
  -  Filtrar: Producto Global > FIJO
  - Valores: RGU  
    |Gerente|Coordinador|Vendedor|Producto TB|
    |-|-|-|-| 
    |-|-|-|-|
  <br/>

  ![F](https://github.com/slandaverde/misiones/blob/master/FINAL_FIJOS.png)
- CCC
  - Valores: NITs  
    |Gerente|Coordinador|Vendedor|Count NIT|
    |-|-|-|-|
    |-|-|-|-| 
  <br/>

  ![ccc](https://github.com/slandaverde/misiones/blob/master/FINAL_CCC.png)

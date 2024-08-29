# Práctica 1. Carga y transformación de datos en Power Query
Dentro de esta práctica nos conectaremos a una base de datos SQL Server que contiene diferentes tablas que buscamos transformar para posteriormente cargarlas. Iniciaremos conectándonos a diferentes fuentes de datos, posteriormente, visualizaremos los datos de origen utilizando Power Query y haremos uso de las características de generación de perfiles de datos en Power Query para asegurarnos de que los datos estén listos para su transformación y análisis.

## Objetivo de la práctica:
Al finalizar la práctica, serás capaz de:

- Realizar conexiones a diferentes fuentes de datos.
- Tener una vista previa de los datos de origen.
- Utilizar características de generación de perfiles de datos.
- Aplicar varias transformaciones comunes.
- Cargar datos a Excel.

## Duración aproximada:
- 120 minutos.


## Instrucciones: 


### Tarea 1. Obtención de datos de SQL Server

- Paso 1.	Inicia la aplicación de Excel en tu computadora.

- Paso 2.	En la cinta superior de Excel, haz clic en la pestaña **"Datos"** para acceder a las herramientas de gestión de datos.

- Paso 3.	Dentro de la pestaña **"Datos"**, busca el grupo **"Obtener y Transformar Datos"**.

- Paso 4.	Da clic en el botón **"Obtener Datos"**.

- Paso 5.	En el menú desplegable, selecciona **“Iniciar el Editor de Power Query”**:

    ![img](./images/imgT1P4.png) 

- Paso 6. En la nueva ventana del Editor de Power Query, en la pestaña de **“Inicio”**, busca el grupo **“Nueva consulta”**.

- Paso 7. Selecciona **“Nuevo Origen” > “Bases de datos” > “SQL Server”**:

    ![img](./images/imgT1P7.png) 

- Paso 8.	En la nueva ventana sólo debes ingresar la información del servidor y luego selecciona **“Aceptar”**:

    ![img](./images/imgT1P8.png) 

- Paso 9. En el panel Navegador, expande la base de datos **AdventureWorksDW2020** y selecciona la opción **"Seleccionar varios elementos"** en la parte superior para poder elegir varias tablas al mismo tiempo.

- Paso 10. Para importar los datos de la tabla, selecciona la casilla de verificación situada junto a las siguientes tablas. Finalmente, selecciona **Aceptar**:

        • DimEmployee
        • DimProduct
        • DimReseller
        • DimSalesTerritory
        • FactResellerSales

    ![img](./images/imgT1P10.png) 

Ahora se ha conectado a seis tablas de una base de datos de SQL Server.

### Tarea 2. Vista previa de datos en Power Query Editor

Esta tarea te permite revisar y generar perfiles de los datos. Esto ayuda a determinar cómo limpiar y transformar los datos más adelante. De igual forma revisarás las tablas de dimensiones con el prefijo "Dim" y las tablas de hechos con el prefijo "Fact".

- Paso 1. En la ventana Editor de Power Query, a la izquierda, observa el panel **Consultas**. El panel Consultas contiene una consulta para cada tabla que has seleccionado:

    ![img](./images/imgT2P1.png) 

- Paso 2. Selecciona la primera consulta: **DimEmployee**.

- Paso 3. En la esquina inferior izquierda de la barra de estado, se proporcionan algunas estadísticas de la tabla, la tabla tiene 33 columnas y 296 filas:

    ![img](./images/imgT2P3.png) 

- Paso 4. En el panel de **Vista previa de datos**, desplázate horizontalmente para revisar todas las columnas. Observa que las últimas cinco columnas contienen vínculos de tabla o valor.

  >  *-- Estas cinco columnas representan relaciones con otras tablas de la base de datos. Se pueden utilizar para unir tablas.--*

- Paso 5. Para evaluar la calidad de la columna, en la pestaña **Vista** de la cinta de opciones, desde el grupo **Vista previa de datos**, activa **Calidad de la columna**. La característica de calidad de columna permite determinar fácilmente el porcentaje de valores válidos, de error o vacíos que se encuentran en las columnas.

    ![img](./images/imgT2P5.png) 

- Paso 6. Observa que la columna **Posición** tiene un 94% de filas vacías (nulas).

    ![img](./images/imgT2P6.png) 

- Paso 7. Para evaluar la distribución de columnas, en la pestaña **Vista** de la cinta de opciones, desde el grupo **Vista previa de datos**, activa **Distribución de columnas**.

- Paso 8. Vuelve a revisar la columna **Posición** y observa que hay cuatro valores distintos y un valor único.

- Paso 9. Revisa la distribución de columnas de la columna **EmployeeKey**: hay 296 valores distintos y 296 valores únicos.

    ![img](./images/imgT2P9.png) 

- Paso 10. En el panel **Consultas**, selecciona la consulta **DimProduct**. 
   > *La tabla contiene una fila por producto vendido por la empresa.*

- Paso 11. En el panel **Consultas**, selecciona la consulta **DimReseller**.
    >*La tabla contiene una fila por revendedor. Los revendedores venden, distribuyen o agregan valor a los productos de Adventure Works*.

- Paso 12. Para ver los valores de columna, en la pestaña **Vista** de la cinta de opciones, desde el grupo **Vista previa de datos**, activa **Perfil de columna**.

- Paso 13. Selecciona el encabezado de la columna **BusinessType** y observa el nuevo panel debajo del panel de vista previa de datos. Revisa las estadísticas de columna y la distribución de valores en el panel de vista previa de datos.

    > *Observa el problema de la calidad de los datos: hay dos etiquetas para warehouse (Warehouse y Ware House mal escrito)*.

    ![img](./images/imgT2P13.png) 

- Paso 14. Coloca el cursor sobre la barra de **Ware House** y observa que hay cinco filas con este valor.

- Paso 15. En el panel **Consultas**, selecciona la consulta **FactResellerSales**.
    >*La tabla contiene una fila por línea de pedido de ventas: un pedido de ventas contiene uno o varios elementos de línea*.

- Paso 16. Revisa la calidad de la columna **TotalProductCost** y observa que el 8% de las filas están vacías.
    >*La falta de valores de columna es un problema de calidad de los datos*.

    ![img](./images/imgT2P17.png) 

### Tarea 3. Obtención de datos de un archivo CSV

- Paso 1. Para agregar una nueva consulta, en la ventana **Editor de Power Query**, en la pestaña de la cinta de opciones **Inicio**, en el grupo **Nueva consulta**, selecciona la flecha abajo **Nuevo origen** y, a continuación, selecciona **Texto/CSV**.

    ![img](./images/imgT3P1.png) 

- Paso 2. Navega hasta el archivo de **> ResellerSalesTargets.csv** *(Este se encuentra en una carpeta del escritorio)*.  Selecciona **Importar**.

- Paso 3. En la ventana **ResellerSalesTargets.csv**, revisa los datos de vista previa. Selecciona **Aceptar**.

- Paso 4. En el panel **Consultas**, observa la adición de la consulta **ResellerSalesTargets**.

- Paso 5. Ten en cuenta que ninguna columna contiene valores vacíos. Cuando no hay un objetivo de ventas mensual, se almacena un guión en su lugar.

- Paso 6. Revisa los íconos de cada encabezado de columna, a la izquierda del nombre de la columna. Los íconos representan el tipo de datos de la columna. **123** es un número entero y **ABC** es un texto.

- Paso 7. Repite los pasos para crear una consulta basada en el archivo **ColorFormats.csv**.
    >*El archivo CSV ColorFormats contiene una fila por color de producto. Cada fila registra los códigos HEX para formatear los colores de fondo y fuente*.

    Ahora deberías tener dos nuevas consultas, **ResellerSalesTargets** y **ColorFormats**.

    ![img](./images/imgT3P7.png) 

### Tarea 4. Configurar la consulta del Salesperson

- Paso 1. En el panel **Consultas**, selecciona la consulta **DimEmployee**

- Paso 2. Para cambiar el nombre de la consulta, en el panel **Configuración de consulta (ubicado a la derecha)**, en el cuadro **Nombre**, reemplaza el texto por **Salesperson** y, a continuación, presiona **Enter**. Posteriormente, comprueba que el nombre se ha actualizado en el panel **Consultas**.

- Paso 3. Para localizar una columna específica, en la pestaña de la cinta de opciones **Inicio**, en la sección de **Administrar columnas**, selecciona la flecha abajo de **Elegir columnas** y, a continuación, selecciona **Ir a columna**.

    ![img](./images/imgT4P3.png) 

- Paso 4. Busca la columna **SalesPersonFlag** y, a continuación, filtra la columna para seleccionar sólo **Salespeople** (es decir, **TRUE**) y haz clic en **Aceptar**.

    ![img](./images/imgT4P4.png) 

- Paso 5. En el panel derecho de la **Configuración de consulta**, en la lista **Pasos aplicados**, observa que se agregó el paso **Filas filtradas**.

    >*Cada transformación que se crea da como resultado un paso aplicado. Es posible editar o eliminar pasos. También es posible seleccionar un paso para obtener una vista previa de los resultados de la consulta en esa etapa de la transformación de la consulta*.

    ![img](./images/imgT4P5.png) 

- Paso 6. Para quitar columnas, en la pestaña de **Inicio**, selecciona el grupo **Administrar columnas**, selecciona el ícono **Elegir columnas**.

- Paso 7. En la ventana **Elegir columnas**, para desmarcar todas las columnas, desactiva el elemento **(Seleccionar todas las columnas)**.

- Paso 8. Para incluir columnas, marca las seis columnas siguientes:

        • EmployeeKey
        • EmployeeNationalIDAlternateKey
        • FirstName
        • LastName
        • Title
        • EmailAddress


- Paso 9. En la lista **Pasos aplicados**, observa la adición de otro paso de consulta.

    ![img](./images/imgT4P9.png) 

- Paso 10. Para crear una columna de nombre único, selecciona primero el encabezado de la columna **FirstName**. Mientras presionas la tecla **Ctrl**, selecciona la columna **LastName**.

    ![img](./images/imgT4P10.png) 

- Paso 11. Haz clic con el botón derecho en cualquiera de los encabezados de columna seleccionados, a continuación, en el menú, selecciona **Combinar columnas**.

    >*Muchas transformaciones comunes se pueden aplicar haciendo clic con el botón derecho en el encabezado de la columna y, a continuación, eligiéndolas en el menú. Sin emabrgo, ten en cuenta que hay más transformaciones disponibles en la cinta de opciones superior*.

- Paso 12. En la ventana **Combinar columnas**, en la lista desplegable **Separador**, selecciona **Espacio**.

- Paso 13. En el cuadro **Nuevo nombre de columna**, reemplaza el texto por **Salesperson**.

    ![img](./images/imgT4P13.png) 

- Paso 14. Para cambiar el nombre de la columna **EmployeeNationalIDAlternateKey**, haz doble clic en el encabezado de la columna **EmployeeNationalIDAlternateKey** y reemplaza el texto por **EmployeeID** y, a continuación, presiona **Aceptar**.

- Paso 15. Usa los pasos anteriores para cambiar el nombre de la columna **EmailAddress** a **UPN**.

    >*UPN es un acrónimo de nombre principal de usuario*.

- Paso 16. En la parte inferior izquierda, en la barra de estado, comprueba que la consulta tenga 5 columnas y 18 filas.

    ![img](./images/imgT4P16.png) 

- Paso 17. En el panel Consultas, selecciona la consulta **DimEmployeeSalesTerritory**.
- Paso 18. En el panel **Configuración de consultas**, cambia el nombre de la consulta a **SalespersonRegion**.
- Paso 19. Para quitar las dos últimas columnas, primero selecciona el encabezado de columna **DimEmployee** y luego, con **Ctrl**, selecciona el encabezado de la columna **DimSalesTerritory**.
- Paso 20. Con las dos columnas seleccionadas, haz clic con el botón derecho y selecciona **Quitar columnas**.

    ![img](./images/imgT5P4.png)  

- Paso 21. En la barra de estado, comprueba que la consulta tiene 2 columnas y 39 filas.
    ![img](./images/imgT5P5.png)  

### Tarea 5. Configurar la consulta del Product

- Paso 1. Selecciona la consulta **DimProduct** y cambia el nombre de la consulta a **Product**.

- Paso 2. Busca la columna **FinishedGoodsFlag** y, a continuación, filtra la columna para recuperar los productos que son productos terminados (es decir, **TRUE**).

    ![img](./images/imgT6P2.png)  

- Paso 3. Elimina todas las columnas, excepto las siguientes:

        • ProductKey (Clave de producto)
        • EnglishProductName
        • StandardCost
        • Color
        • DimProductSubcategory

    ![img](./images/imgT6P3.png)  

- Paso 4. Observa que la columna **DimProductSubcategory** representa una tabla relacionada (contiene vínculos).

- Paso 5. En el encabezado de la columna **DimProductSubcategory**, a la derecha del nombre de la columna, selecciona el botón **expandir**.

- Paso 6.Consulta la lista completa de columnas y, a continuación, selecciona la casilla **"Seleccionar todas las columnas"** para anular la selección de todas las columnas.

- Paso 7. Selecciona **EnglishProductSubcategoryName** y **DimProductCategory**, y desactiva la casilla **Usar el nombre de la columna original como prefijo** antes de seleccionar **Aceptar**.

    ![img](./images/imgT6P5.png)  

- Paso 8. Observa que la transformación dio como resultado la adición de dos columnas y que se ha quitado la columna **DimProductSubcategory**.

- Paso 9. Expanda la columna **DimProductCategory** y, a continuación, introduce solo la columna **EnglishProductCategoryName**.

    ![img](./images/imgT6P8.png)  

- Paso 10. Cambia el nombre de las siguientes cuatro columnas:

        • EnglishProductName a Product
        • StandardCost a Standard Cost (incluir un espacio)
        • EnglishProductSubcategoryNombre a Subcategory
        • EnglishProductCategoryName a Category 

- Paso 11. En la barra de estado, comprueba que la consulta tenga 6 columnas y 397 filas.

    ![img](./images/imgT6P11.png) 

### Tarea 6. Configurar la consulta de Reseller

- Paso 1. Selecciona la consulta **DimReseller** y cambia el nombre a **Reseller**.
- Paso 2. Elimina todas las columnas, excepto las siguientes:

        • ResellerKey
        • BusinessType
        • ResellerName
        • Dimgeography

    ![img](./images/imgT7P2.png) 
- Paso 3.Expande la columna **Dimgeography** para incluir **sólo** las tres columnas siguientes:

        • City
        • StateProvinceName
        • EnglishCountryRegionName

    ![img](./images/imgT7P3.png) 

- Paso 4. En el encabezado de la columna **Business Type**, selecciona la flecha abajo y, a continuación, revisa los distintos valores de columna y observa los dos valores **Warehouse** y **Ware house**.

- Paso 5. Haz clic con el botón derecho en el encabezado de la columna **Business Type** y, a continuación, selecciona **Reemplazar valores**.

- Paso 6. En la ventana **Reemplazar valores**, configura los siguientes valores:

    >• En el cuadro **Value to Find**, escribe **Ware house** <br>
    >• En el cuadro **Replace With**, escribe **Warehouse**

    ![img](./images/imgT7P6.png) 

- Paso 7. Cambia el nombre de las siguientes cuatro columnas:

    >• **BusinessType** a **Business Type** (incluir un espacio) <br>
    >• **ResellerName** a **Reseller** <br>
    >• **StateProvinceName** a **State-Province** <br>
    >• **EnglishCountryRegionName** a **Country-Region** <br>

- Paso 8. En la barra de estado, comprueba que la consulta tenga 6 columnas y 701 filas.

    ![img](./images/imgT7P9.png)  

### Tarea 7. Configurar la consulta de Region

- Paso 1. Selecciona la consulta **DimSalesTerritory** y cambia el nombre de la consulta a **Region**.

- Paso 2. Aplica un filtro a la columna **SalesTerritoryAlternateKey** para quitar el valor **0** (cero).

    >• Esto eliminará una fila.

- Paso 3. Elimina todas las columnas, excepto las siguientes:

        • SalesTerritoryKey
        • SalesTerritoryRegion
        • SalesTerritoryCountry
        • SalesTerritoryGroup

- Paso 4. Cambia el nombre de las siguientes tres columnas:

    >• SalesTerritoryRegion a **Region** <br>
    >• SalesTerritoryCountry a **Country**<br>
    >• SalesTerritoryGroup a **Group**<br>


- Paso 5. En la barra de estado, comprueba que la consulta tiene 4 columnas y 10 filas.

    ![img](./images/imgT8P6.png)  

### Tarea 8. Configurar la consulta de Sales

- Paso 1. Selecciona la consulta **FactResellerSales** y cámbiale el nombre a **Sales**.

- Paso 2. Elimina todas las columnas, excepto las siguientes:

        • SalesOrderNumber
        • OrderDate
        • ProductKey
        • ResellerKey
        • EmployeeKey
        • SalesTerritoryKey
        • OrderQuantity
        • UnitPrice
        • TotalProductCost
        • SalesAmount
        • DimProduct

- Paso 3. Expande la columna **DimProduct**, desactiva todas las columnas y, a continuación, incluye sólo la columna **StandardCost**.

- Paso 4. Para crear una columna personalizada, en la pestaña **Agregar columna**, en el grupo **General**, selecciona **Columna personalizada**.

    ![img](./images/imgT9P4.png) 

- Paso 5. En la ventana **Columna personalizada**, en el cuadro **Nuevo nombre de columna**, reemplaza el texto por **Cost**.

- Paso 6. En el cuadro **Fórmula de columna personalizada**, escribe la siguiente expresión (después del símbolo igual a) y, a continuación, guarda la nueva columna:

    >if [TotalProductCost] = null then [OrderQuantity] * [StandardCost] else [TotalProductCost] <br>

   *Esta expresión comprueba si falta el valor de TotalProductCost. Si falta, genera un valor multiplicando el valor de OrderQuantity por el valor de StandardCost; de lo contrario, usa el valor TotalProductCost existente*.
    ![img](./images/imgT9P6.png) 


- Paso 7. Elimina las dos columnas siguientes:

        • TotalProductCost
        • StandardCost

- Paso 8. Cambia el nombre de las tres columnas siguientes:

        • OrderQuantity a Quantity
        • UnitPrice a Unit Price (incluye un espacio)
        • SalesAmount a Sales 

    ![img](./images/imgT9P8.png) 
 

- Paso 9. Para modificar el tipo de datos de columna, en el encabezado de columna **Quantity**, a la izquierda del nombre de la columna, selecciona el ícono **1,2** y, a continuación, selecciona **Número entero**.

    >*Es importante configurar el tipo de datos correcto. Cuando la columna contiene un valor numérico, también es importante elegir el tipo correcto si se espera realizar cálculos matemáticos.*

    ![img](./images/imgT9P9.png) 

- Paso 10. Modifica los siguientes tres tipos de datos de columna a **Número decimal**.

    >*El tipo de datos de número decimal permite 19 dígitos y permite una mayor precisión para evitar errores de redondeo. Es importante usar el tipo de número decimal para los valores financieros o las tasas (como los tipos de cambio)*.

        • Unit Price
        • Sales
        • Cost

- Paso 11. En la barra de estado, comprueba que la consulta tiene **10 columnas y 999+ filas**. Se cargará un máximo de 1000 filas como datos de vista previa para cada consulta.

    ![img](./images/imgT9P11.png) 

### Tarea 9. Configurar la consulta de Targets

- Paso 1. Selecciona la consulta **ResellerSalesTargets** y cambia el nombre a **Targets**.

- Paso 2. Para anular la dinamización de las columnas de 12 meses (**M01-M12**), primero selecciona varias veces los encabezados de columna **Year** y **EmployeeID**.

- Paso 3. Haz clic con el botón derecho en cualquiera de los encabezados de columna seleccionados y, a continuación, en el menú contextual, selecciona **Anular dinamización de otras columnas**.

    ![img](./images/imgT10P3.png) 

- Paso 4. Observa que los nombres de las columnas ahora aparecen en la columna **Atributo** y los valores aparecen en la columna **Valor**.

    ![img](./images/imgT10P4.png) 

- Paso 5. Aplica un filtro a la columna **Valor** para eliminar los valores de guion (-).

    >*Es posible que recuerdes que el caracter de guion se utilizó en el archivo CSV de origen para representar cero (0).*

- Paso 6. Cambia el nombre de las dos columnas siguientes:

    >• **Atributo** a **MonthNumber** (no hay espacio) <br>
    • **Valor** a **Target** 

- Paso 7. Para preparar los valores de la columna **MonthNumber**, haz clic con el botón derecho en el encabezado de la columna **MonthNumber** y, a continuación, selecciona **Reemplazar valores**.

- Paso 8. En la ventana **Reemplazar valores**, en el cuadro **Valor para buscar**, escribe **M** y deja vacío el valor **Reemplazar con**.

    ![img](./images/imgT10P8.png) 

- Paso 9. Modifica el tipo de datos de la columna **MonthNumber** a **Número entero**.

- Paso 10. En la pestaña de la cinta **Agregar columna**, en el grupo **General**, selecciona el ícono **Columna de ejemplos**.

    ![img](./images/imgT10P10.png) 

- Paso 11. Observa que la primera fila es para el año **2017** y el mes número **7**.

- Paso 12. En la columna **Columna1**, en la primera celda de la cuadrícula, comienza a escribir **7/1/2017** y, a continuación, presiona **Aceptar**.

    ![img](./images/imgT10P12.png) 

- Paso 13. Observa que las celdas de la cuadrícula se actualizan con los valores previstos.

- Paso 14. Para cambiar el nombre de la nueva columna, haz doble clic en el encabezado de la columna **Combinada** y cambia el nombre de la columna a **TargetMonth**.

- Paso 15. Elimina las siguientes columnas:

        • Year
        • MonthNumber

- Paso 16. Modifica los siguientes tipos de datos de columna:

    >• **Target** como número decimal <br>
     • **TargetMonth** como Date


- Paso 17. Para multiplicar los valores de **Target** por 1000, selecciona el encabezado de la columna de **Target** y, a continuación, en la pestaña de la cinta **Transformar**, dentro del grupo **Columna de número**, selecciona **Estándar** y, para finalizar, selecciona **Multiplicar**.

- Paso 18. En la ventana **Multiplicar**, en el cuadro **Valor**, escribe **1000** y selecciona **Aceptar**.

    ![img](./images/imgT10P16.png) 

 - Paso 19. En la barra de estado, comprueba que la consulta tenga 3 columnas y 809 filas.

    ![img](./images/imgT10P18.png) 

### Tarea 10. Configuración de la consulta ColorFormats 

 - Paso 1. Selecciona la consulta **ColorFormats** y observa que la primera fila contiene los nombres de columna.

 - Paso 2. En la pestaña **Inicio** de la cinta de opciones, dentro del grupo **Transformar**, selecciona **Usar primera fila como encabezados**.

     ![img](./images/imgT11P2.png) 

- Paso 3. En la barra de estado, comprueba que la consulta tiene 3 columnas y 10 filas.

     ![img](./images/imgT11P3.png) 

### Tarea 11. Actualizar la consulta del Product 

- Paso 1. Selecciona la consulta **Product**.

- Paso 2. Para combinar la consulta **ColorFormats**, en la pestaña de la cinta de opciones **Inicio**, selecciona la flecha abajo **Combinar** y, a continuación, selecciona **Combinar consultas**.

     ![img](./images/imgT12P2.png)

    >*La combinación de consultas permite integrar datos, en este caso, de diferentes fuentes de datos (SQL Server y un archivo CSV)*.

- Paso 3. En la ventana **Combinar**, en la cuadrícula Consulta **Product**, selecciona el encabezado de columna **Color**.

     ![img](./images/imgT12P3.png)

- Paso 4. Debajo de la cuadrícula Consulta de **Product**, en la lista desplegable, selecciona la consulta **ColorFormats**.

     ![img](./images/imgT12P4.png)

- Paso 5. En la cuadrícula de consulta **ColorFormats**, selecciona el encabezado de la columna **Color**.

     ![img](./images/imgT12P5.png)

- Paso 6. En la ventana **Combinar**, utiliza el Tipo de combinación predeterminado, manteniendo la selección de **Externa izquierda** y selecciona **Aceptar**.

- Paso 7. Expande la columna **ColorFormats** para incluir las dos columnas siguientes:

    >• Background Color Format <br>
    >• Font Color Format

     ![img](./images/imgT12P6.png)

- Paso 8. En la barra de estado, comprueba que la consulta ahora tenga 8 columnas y 397 filas.

     ![img](./images/imgT12P7.png)

### Resultado final:

![img](./images/imgR1.png)


- Paso 1. Selecciona **Cerrar y cargar en** para cargar los datos en Excel. 

- Paso 2. En la ventana de **Importar datos**, selecciona únicamente **Crear unicamente la conexión** 

- Paso 3. Da clic sobre **Agregar estos datos al Modelo de datos** y luego en **Aceptar**.

    ![img](./images/imgR3.png)

Ahora puedes ver la vista de **Excel**, con el panel de **Consultas y conexiones** a la derecha, observa las 7 tablas cargadas en el modelo de datos.

![img](./images/imgR4.png)

## Laboratorio completo.

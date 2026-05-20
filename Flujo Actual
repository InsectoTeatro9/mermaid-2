```mermaid
flowchart TD
    Start([Inicio: Cálculo de Booking de Ventas]) --> Access[Ingresar a 'El Gestor'<br>Sincroniza códigos de proyecto desde Softland]
    
    Access --> Step1[1. Filtrar Órdenes de Venta<br>Desde inicio del año actual hasta hoy]
    
    A --> Step2[2. Exportar a Excel<br>Limpiar y dejar solo las 10 columnas clave]
    
    B --> Step4[4. Conversión de Moneda<br>Calcular manualmente valor en UF/Dólar a CLP]
    
    Step4 --> Step5[5. Desglosar Código de Negocio<br>Identificar: Razón Social, Área, Correlativo y Categorías]
    
    Step5 --> Step6{6. Determinar Tipo de Cuenta}
    Step6 -- Profundidad --> AM_Prof[Asignar Gerente de Cuenta<br>según el Cliente]
    Step6 -- Cobertura --> AM_Cob[Abrir detalle del negocio<br>para identificar Gerente de Cuenta]
    
    AM_Prof --> Step7[7. Temporalidad<br>Agregar campo de Mes y Cuartil/Trimestre]
    AM_Cob --> Step7
    
    Step7 --> Step8{8. ¿Es Venta Interempresa?<br>Ej: Acanto vende a Vadco}
    Step8 -- Sí --> DeleteInter[Eliminar del cálculo la venta interempresa<br>Se borra el registro con menor correlativo N]
    Step8 -- No --> Step9{9. ¿Hay Venta VTA posterior<br>a un negocio Preliminar?}
    
    DeleteInter --> Step9
    
    Step9 -- Sí --> AdjustPrelim[Revisar detalle de la venta<br>Definir montos correctos a considerar]
    Step9 -- No --> FinalDB[Base de Datos de Booking Consolidada]
    AdjustPrelim --> FinalDB
    
    FinalDB --> Context([Fin: Análisis y KPIs<br>- Comparación con metas de Gerentes<br>- % por Cuenta, Área, Categoría y Sub-categoría])
```
    %% Estilos visuales opcionales para claridad
    style Start fill:#f9f,stroke:#333,stroke-width:2px
    style Context fill:#bbf,stroke:#333,stroke-width:2px
    style Step6 fill:#ffeb3b,stroke:#333,stroke-width:1px
    style Step8 fill:#ffeb3b,stroke:#333,stroke-width:1px
    style Step9 fill:#ffeb3b,stroke:#333,stroke-width:1px

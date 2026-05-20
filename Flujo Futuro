```mermaid
flowchart TD
    Start([Inicio: Orquestador de Booking Automatizado]) --> API_Extract[1 y 2. Extracción vía API de El Gestor<br>Filtro automático: Año actual hasta Hoy<br>Extrae solo las 10 columnas clave desde Softland]
    
    API_Extract --> API_Currency[4. Conversión Monetaria Automática<br>Consulta API externa o interna para obtener<br>valor histórico de USD/UF a la Fecha de Emisión]
    
    API_Currency --> Auto_Parse[5. Desglose de Código de Negocio por Regex<br>Formato: Empresa-AREA+N-CAT-SUB<br>Mapea Razones Sociales AC/TKN y Áreas EMP/VAD/OPE]
    
    Auto_Parse --> API_CRM[6. Enriquecimiento de Gerente de Cuenta<br>Cruce por API con CRM o El Gestor<br>Aplica regla por Tipo de Cuenta: Profundidad o Cobertura]
    
    API_CRM --> Auto_Time[7. Cálculo de Temporalidad<br>Calcula automáticamente Mes y Cuartil/Trimestre<br>basado en la Fecha de Emisión]
    
    Auto_Time --> Filter_Inter[8. Algoritmo de Detección Interempresa<br>Filtra proveedores Acanto/Teknos y ejecuta<br>Match de correlativos secuenciales N vs N+1]
    
    Filter_Inter --> Ctrl_Inter{¿Se detectó<br>Venta Interempresa?}
    Ctrl_Inter -->|Sí: Match N y N+1| Del_Inter[Eliminar automáticamente registro N<br>Conserva solo venta de Razón Social a Terceros]
    Ctrl_Inter -->|No| Filter_Prelim[9. Módulo de Identificación de Preliminares]
    
    Del_Inter --> Filter_Prelim
    
    Filter_Prelim --> Ctrl_Duplicado{¿Sistema detecta intento de<br>doble ingreso por Código de Negocio<br>Preliminar anterior vs Venta posterior?}
    Ctrl_Duplicado -->|Sí: Bloquear Doble Ingreso| Reject_VTA[Filtrar y Rechazar Registro Venta VTA<br>Mantener solo el valor del Preliminar original<br>según su Fecha de Emisión histórica]
    Ctrl_Duplicado -->|No| DB_Final[(Base de Datos Consolidada)]
    
    Reject_VTA --> DB_Final
    
    DB_Final --> Dashboards([Fin: BI & Dashboards en Tiempo Real<br>- Cumplimiento de metas de Gerentes de Cuenta<br>- Análisis por Cuenta, Área, Categoría y Sub-categoría])
  ```
    %% Estilos de infraestructura para tus programadores
    style Start fill:#f8bbd0,stroke:#c2185b,stroke-width:2px
    style Dashboards fill:#f8bbd0,stroke:#c2185b,stroke-width:2px
    
    style API_Extract fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px
    style API_Currency fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px
    style Auto_Parse fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px
    style API_CRM fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px
    style Auto_Time fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px
    
    style Ctrl_Inter fill:#fff9c4,stroke:#fbc02d,stroke-width:2px
    style Ctrl_Duplicado fill:#fff9c4,stroke:#fbc02d,stroke-width:2px
    
    style Del_Inter fill:#e8f5e9,stroke:#4caf50,stroke-width:1px
    style Reject_VTA fill:#e8f5e9,stroke:#4caf50,stroke-width:1px
    style DB_Final fill:#e8f5e9,stroke:#4caf50,stroke-width:2px



   

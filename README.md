# icils-multilevel

## Muy importante!

Al final hay un plan resumido que indica más o menos un paso a paso. Para llevar esto a cabo necesitamos buscar y seleccionar manually las variables de interés para cada base de datos, pero para no abrumarnos lo mejor sería ir seleccionando paso por paso, a medida que necesitemos.

**Pregunta(?):** *¿La disponibilidad de recursos TIC en la escuela (Nivel 2) predice mayores niveles de CIL en los estudiantes (Nivel 1), controlando factores individuales y escolares? ¿Este efecto de los recursos escolares (Nivel 2) es más fuerte en países con menor infraestructura TIC nacional (Nivel 3), sugiriendo una compensación?*

Necesitamos variables de los tres niveles y de diferentes archivos de datos ICILS 2023, además de posiblemente datos externos (para el nivel de país sobre todo).

**Nivel 1: Estudiante (Datos principalmente del archivo BSG - Student)**

-   **Variables Esenciales de Identificación y Diseño:**
    -   `IDCNTRY`: Identificador numérico del país (clave Nivel 3).
    -   `IDSCHOOL`: Identificador de la escuela (clave Nivel 2).
    -   `IDSTUD`: Identificador único del estudiante.
    -   `TOTWGTS`: Peso final del estudiante (para análisis descriptivos y potencialmente en MLM, según el método).
    -   `JKZONES`, `JKREPS`: Variables para la estimación de varianza Jackknife (necesarias para errores estándar correctos).
    -   `SRWGT1` - `SRWGT75`: Pesos replicados Jackknife (usados internamente por software o para cálculo manual).
-   **Variable Dependiente (Outcome):**
    -   **Alfabetización Computacional e Informacional (CIL):**
        -   **Variables:** `PV1CIL`, `PV2CIL`, `PV3CIL`, `PV4CIL`, `PV5CIL` (Valores Plausibles, usar los 5 conjuntamente).
-   **Variables de Control del Estudiante (Predictores/Covariables Nivel 1):**
    -   **Estatus Socioeconómico (SES):**
        -   **Recomendado:** `NISB` (Índice Internacional de Contexto Socioeconómico, derivado - Sup. 3, p. 313).
        -   **Alternativa/Componentes:** `S_HISEI` (ISEI más alto padres), `S_HISCED` (ISCED más alto padres), `S_HOMLIT` (libros/recursos en casa) (Índices simples derivados - Sup. 3, pp. 310-313).
    -   **Género:**
        -   **Variable:** `S_SEX` (Variable derivada - Sup. 3, p. 309).
        -   **¡Atención!** Probablemente **requiere el archivo de uso restringido (RUF)** ya que `IS3G02` (su fuente) suele estar suprimida en el archivo público (PUF) (Guía Principal, Tabla 2.9, p. 23).
    -   **Acceso y Experiencia TIC:**
        -   `S_INTNET`: Acceso a internet en casa (Derivado - Sup. 3, p. 313).
        -   `S_EXCOMP`: Experiencia en años usando computadoras (Derivado - Sup. 3, p. 314).
    -   **Actitudes / Autoeficacia / Interés TIC (Priorizar escalas derivadas - Sup. 3, pp. 316-318):**
        -   `S_GENEFF`: Autoeficacia para tareas TIC generales.
        -   `S_ICTPOSS`: Percepciones positivas sobre TIC y aprendizaje.
        -   `S_ICTFUT`: Expectativas/interés futuro en TIC.
        -   *(Opcional según teoría):* `S_SPECEFF` (Autoeficacia específica), `S_ICTPOSG` (Visión social positiva), `S_ICTNEG` (Visión negativa).
    -   **(Opcional) Contexto Demográfico/Cultural:**
        -   `S_IMMIG` o `S_IMMBGR`: Estatus migratorio (Derivado - Sup. 3, p. 309-310).
        -   `S_TLANG`: Lengua hablada en casa (Derivado - Sup. 3, p. 310).
    -   **(Opcional) Otros Controles:**
        -   `S_AGE`: Edad del estudiante (Derivado - Sup. 3, p. 309).
        -   `S_ISCED`: Expectativas educativas del estudiante (Derivado - Sup. 3, p. 309).
        -   `S_ICTSTUD`: Si estudia materias TIC formalmente (Derivado - Sup. 3, p. 314).
        -   `S_ACMULT`: Multitasking académico-media (Derivado - Sup. 3, p. 320). Podría ser relevante para entender patrones de uso.

*Nota: Para las variables de control, priorizar el uso de las escalas derivadas (listadas en el Suplemento 3) es generalmente preferible por su mayor fiabilidad psicométrica. Consultar el Codebook y el Suplemento 3 es esencial para entender la construcción y codificación exacta de cada variable.*

**Nivel 2: Escuela (Datos principalmente del archivo BCG - School & ICT Coordinator)**

1.  **Predictor Principal: Recursos TIC de la Escuela:** Información probablemente del cuestionario del Coordinador TIC (variables `II...` o `IC...`) o del Director (variables `IP...`).
    -   **Dispositivos:**
        -   Ratio de estudiantes por computador disponible para la enseñanza. (Podría requerir calcularlo usando `P_NUMTAR` y una variable sobre número de dispositivos `II...` o `IC...`).
        -   Disponibilidad y tipo de dispositivos (celus, tablets) para uso estudiantil (`II...`, `IC...`).
        -   Antigüedad o percepción de la actualización de los equipos (`II...`, `IC...`).
    -   **Conectividad:**
        -   Velocidad o tipo de conexión a internet en la escuela (`II...`, `IC...`).
        -   Percepción de la suficiencia/fiabilidad del ancho de banda (`II...`, `IC...`).
        -   Cobertura WiFi en aulas u otras áreas (`II...`, `IC...`).
    -   **Soporte Técnico:**
        -   Existencia de personal dedicado al soporte TIC (`II...`, `IC...`).
        -   Percepción de la adecuación/rapidez del soporte (`II...`, `IC...`).
    -   **Índice Compuesto (MUY RECOMENDADO):** Es muy probable que IEA haya creado uno o más índices que resumen los recursos TIC o la infraestructura TIC de la escuela. Busca en el Suplemento 3 nombres como `ICTINFRA`, `ICTRES`, `TECHSUPP` o similares derivados de las preguntas al director o coordinador TIC. Usar estos índices es preferible a variables individuales.
2.  **Variables de Control de la Escuela:** Otros factores escolares que pueden influir.
    -   **Tipo de Escuela:** Pública o privada (`IP3G06A`, o el índice derivado `P_PRIV`).
    -   **Ubicación:** Urbana, suburbana, rural (ej. `IP3G05`).
    -   **Tamaño de la Escuela:** Número total de estudiantes (`P_NUMSTD`) o del grado objetivo (`P_NUMTAR`). (Nota: Pueden estar categorizadas en el archivo público - PUF, Tabla 2.8).
    -   **Contexto SES de la Escuela:**
        -   **Ideal:** Promedio del SES de los estudiantes de la escuela (requiere agregar datos del Nivel 1 al Nivel 2).
        -   **Alternativa:** Percepción del director sobre el nivel socioeconómico del alumnado (ej. `IP3G06BA`, `IP3G06BB`).
    -   *(Opcional)*: Énfasis del director en TIC, clima escolar relacionado con TIC (buscar índices derivados).

**Nivel 3: País (Externos)**

1.  **Variable Moderadora: Infraestructura TIC Nacional:** Mide el nivel general de desarrollo y acceso a las TIC en el país.
    -   **Opción 1: Desde el archivo NCS:**
        -   Buscar en el cuestionario de contexto nacional (Suplemento 1 o 2) preguntas dirigidas al Coordinador Nacional sobre políticas de inversión en TIC, penetración nacional de banda ancha, estrategias digitales nacionales. Los nombres de variables probablemente empiecen por `NC...`. *Precaución:* Estas variables pueden ser cualitativas o muy generales.
    -   **Opción 2: Datos Externos (A menudo más cuantitativos y estandarizados):**
        -   **ITU (Unión Internacional de Telecomunicaciones):**
            -   **ICT Development Index (IDI):** Índice compuesto muy utilizado.
            -   Porcentaje de hogares con acceso a internet.
            -   Suscripciones a banda ancha móvil por cada 100 habitantes.
            -   Suscripciones a banda ancha fija por cada 100 habitantes.
        -   **Banco Mundial (World Bank):** Indicadores similares a los de ITU.
        -   **Foro Económico Mundial (WEF):** Networked Readiness Index (NRI) o sus componentes relacionados con infraestructura y acceso.
        -   *Acción:* Vamos a necesitar buscar estos datos para los países participantes en ICILS 2023 para un año cercano (idealmente 2022 o 2023). Luego, hay que crear un pequeño archivo con el identificador del país (`IDCNTRY` o `CNTRY`) y el valor del indicador elegido, para fusionarlo con tus datos ICILS en el modelo multinivel.
2.  **(Opcional) Variables de Control del País:** Otros factores nacionales que podrían influir.
    -   **Riqueza del País:** PIB per cápita (dato externo).
    -   **Nivel de Desarrollo:** Índice de Desarrollo Humano (IDH) (dato externo).
    -   **Gasto en Educación:** Porcentaje del PIB destinado a educación (dato externo).

**Resumen del Plan:**

1.  **Archivo Base:** Empezamos con el archivo de estudiantes (BSG).
2.  **Fusionar Nivel 2:** Usamos el IEA IDB Analyzer o un proceso manual para añadir las variables escolares seleccionadas (Recursos TIC - idealmente un índice, controles escolares) del archivo BCG al archivo BSG, usando `IDCNTRY` e `IDSCHOOL` como claves.
3.  **Fusionar Nivel 3:** Añadir la variable de infraestructura TIC nacional (y controles de país si usas) al archivo resultante. Esto se hace usando `IDCNTRY` como clave.
4.  **Modelo:** Especificamos un modelo multinivel de 3 niveles con:
    -   Nivel 1: Estudiantes (con PVs de CIL como dependiente, y controles individuales).
    -   Nivel 2: Escuelas (con índice de Recursos TIC y controles escolares).
    -   Nivel 3: Países (con índice de Infraestructura TIC Nacional y controles nacionales).
5.  **Interacción Clave:** Incluir en el modelo el término de interacción entre la variable de Recursos TIC de la Escuela (Nivel 2) y la variable de Infraestructura TIC Nacional (Nivel 3) para probar si el efecto de los recursos escolares depende del contexto nacional.

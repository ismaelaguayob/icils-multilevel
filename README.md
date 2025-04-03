# icils-multilevel

Varias ideas de preguntas de investigación posibles, agrupadas por temas, utilizando variables probablemente disponibles (según la descripción del User Guide y suplementos habituales de IEA):

**A. Enfoque en Equidad (Factores Socioeconómicos y de Género):**

1.  **Pregunta Central:** ¿En qué medida las diferencias en Alfabetización Computacional e Informacional (CIL) entre estudiantes (Nivel 1) se explican por características del estudiante (Nivel 1), de la escuela (Nivel 2) y del país (Nivel 3)?
    *   *(Desglose):* ¿Cuál es la partición de la varianza en CIL entre los niveles de estudiante, escuela y país?
2.  **Interacción SES x Escuela x País:** ¿La relación entre el estatus socioeconómico del estudiante (SES, Nivel 1, derivado de variables como libros en casa, educación parental) y su CIL (Nivel 1) varía entre escuelas (Nivel 2)? Más importante aún, ¿esta variación *entre escuelas* (la pendiente aleatoria SES->CIL) difiere sistemáticamente entre países (Nivel 3), quizás dependiendo del nivel de desigualdad económica del país (Nivel 3, externo) o de las políticas de equidad educativa (Nivel 3, NCS)?
3.  **Interacción Género x Escuela x País:** ¿La brecha de género en el pensamiento computacional (CT, Nivel 1) varía entre escuelas (Nivel 2)? ¿Esta variación *entre escuelas* está relacionada con características escolares como la proporción de profesoras de STEM (agregado Nivel 2) o con políticas nacionales de igualdad de género en la educación (Nivel 3, NCS o externo)?
4.  **Composición Escolar y País:** ¿El efecto del SES promedio de la escuela (Nivel 2, agregado) sobre el CIL del estudiante (Nivel 1) es significativo después de controlar el SES individual (Nivel 1)? ¿Este efecto contextual de la escuela (Nivel 2) varía entre países (Nivel 3) y se relaciona con el grado de segregación escolar del sistema educativo nacional (Nivel 3)?

**B. Enfoque en Recursos y Prácticas Escolares:**

5.  **Recursos Escolares y País:** ¿La disponibilidad de recursos TIC en la escuela (dispositivos, conectividad, soporte técnico, Nivel 2, variables IC/II) predice mayores niveles de CIL en los estudiantes (Nivel 1), controlando factores individuales y escolares? ¿Este efecto de los recursos escolares (Nivel 2) es más fuerte en países con menor infraestructura TIC nacional (Nivel 3, externo o NCS), sugiriendo una compensación?
6.  **Políticas Escolares, Clima y País:** ¿Las políticas escolares sobre seguridad en línea y uso responsable de TIC (Nivel 2, variables IC/IP) se asocian con mayores actitudes positivas hacia las TIC (Nivel 1) o mayor CIL (Nivel 1)? ¿La fortaleza de esta asociación (Nivel 2) depende del énfasis nacional en la educación digital ciudadana (Nivel 3, NCS)?
7.  **Liderazgo Escolar y País:** ¿El énfasis del director/a en el uso pedagógico de las TIC (Nivel 2, variables IP) se relaciona con un mayor uso de TIC para el aprendizaje por parte de los estudiantes (Nivel 1) o mayor CIL (Nivel 1)? ¿Esta relación (Nivel 2) varía entre países (Nivel 3) en función de la autonomía escolar para definir el currículum (Nivel 3, NCS)?
8.  **Prácticas Docentes (Agregadas) y País:** ¿Las escuelas donde los profesores (agregado Nivel 2, desde BTG) reportan mayor autoeficacia en el uso de TIC para la enseñanza o participan más en desarrollo profesional sobre TIC, tienen estudiantes con mayor CIL (Nivel 1)? ¿Esta relación (Nivel 2) es más fuerte en países donde la formación inicial docente en TIC es menos robusta (Nivel 3, NCS)?

**C. Enfoque en Actitudes y Uso de TIC:**

9.  **Autoeficacia, Uso y Contexto Nacional:** ¿La relación entre la autoeficacia del estudiante en CIL (Nivel 1, escala derivada) y su rendimiento en CIL (Nivel 1) es moderada por el tipo de uso que hace de las TIC (tareas escolares vs. ocio, Nivel 1)? ¿El país (Nivel 3) modera esta relación, quizás a través de diferencias culturales en la valoración de las habilidades digitales (Nivel 3)?
10. **Actitudes Escolares y País:** ¿El "clima TIC" de la escuela (Nivel 2, agregado de percepciones de estudiantes o profesores sobre la importancia/integración de las TIC) se asocia con actitudes más positivas de los estudiantes hacia las TIC (Nivel 1)? ¿Esta asociación (Nivel 2) depende de si el currículum nacional integra formalmente la CIL (Nivel 3, NCS)?

**D. Enfoque en Pensamiento Computacional (CT):**

11. **Factores Predictivos de CT a Tres Niveles:** Similar a la pregunta 1, pero para CT: ¿Qué proporción de la varianza en el rendimiento de CT (Nivel 1) se encuentra a nivel de estudiante, escuela y país? ¿Qué predictores a cada nivel (e.g., interés del estudiante en programación (L1), disponibilidad de actividades extracurriculares de CT en la escuela (L2), inclusión de CT en el currículum nacional (L3)) son significativos?
12. **Relación CIL-CT y Contexto Nacional:** ¿La correlación entre el rendimiento en CIL y CT a nivel de estudiante (Nivel 1) varía entre escuelas (Nivel 2)? ¿Varía también entre países (Nivel 3)? ¿Podría esta variación a nivel nacional (Nivel 3) relacionarse con cómo se enseñan ambas competencias (integradas vs. separadas) según las políticas nacionales (Nivel 3, NCS)?

**Consideraciones Clave para la Investigación de 3 Niveles:**

*   **Disponibilidad de Variables:** Verifica cuidadosamente qué variables están disponibles y son comparables entre países en los archivos BSG, BCG, BTG y, especialmente, en el NCS (National Context Survey), que suele ser más limitado. Puede que necesites complementar con datos externos para el Nivel 3 (e.g., PIB per cápita, Índice de Desarrollo Humano, Índice de Disponibilidad de Redes).
*   **Número de Unidades:** Necesitas un número suficiente de países (Nivel 3) y escuelas (Nivel 2) dentro de cada país para que los modelos sean estables, especialmente si incluyes interacciones complejas o pendientes aleatorias. ICILS 2023 tiene 34 países + 1 benchmarking, lo cual es un buen punto de partida para el Nivel 3. El número de escuelas por país varía.
*   **Complejidad Estadística:** Los modelos de tres niveles son más complejos de especificar, estimar e interpretar. Presta especial atención a cómo manejas los pesos muestrales (la guía del usuario da pistas, pero puede requerir consulta especializada para 3 niveles) y la estimación de errores estándar con JRR y PVs. El IEA IDB Analyzer podría simplificar esto si soporta modelos de 3 niveles (necesitarías verificar su documentación específica para esta funcionalidad).
*   **Teoría:** Asegúrate de que tus preguntas e interacciones estén bien fundamentadas teóricamente. ¿Por qué esperarías que una relación a nivel de estudiante varíe entre escuelas o países de una manera específica?

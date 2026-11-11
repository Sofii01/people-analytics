# Autodiagnóstico de madurez en People Analytics

Documento funcional para construir la primera configuración del motor reutilizable de autodiagnóstico.

**Estado:** borrador para revisión  
**Responsable funcional:** Sofía Britos  
**Célula:** A · People Analytics  
**Tarea principal:** T-003  
**Versión de prueba prevista:** 20/11/2026  
**Versión final prevista:** 26/11/2026

## 1. Objetivo

Permitir que una persona ubique a su organización en uno de cuatro niveles de madurez en People Analytics, entienda por qué obtuvo ese resultado y reciba recomendaciones iniciales para avanzar.

El autodiagnóstico no es un examen ni una calificación del alumno. Es una herramienta de orientación para usar al inicio del curso y volver a utilizar durante el taller de la sesión 7.

## 2. Responsabilidades

| Rol | Responsabilidad |
|---|---|
| Sofía Britos | Definir el flujo, la lógica funcional, la integración, las pruebas funcionales y el seguimiento de la entrega |
| Gonzalo H. | Diseñar la experiencia y las pantallas para celular |
| Gonzalo M. | Implementar las pantallas y componentes del frontend |
| Anabelle Alberto | Redactar y revisar preguntas, niveles y recomendaciones |
| Naomi Aguilar / Francisco Núñez | Validar el contenido y el modelo de madurez |
| Valentino Bongiorno | Publicar la herramienta y mantener un link estable |

## 3. Flujo de la herramienta

1. **Bienvenida**
   - Título y propósito.
   - Explicación de que no es una evaluación.
   - Tiempo estimado.
   - Aviso de uso anónimo.
   - Botón “Comenzar”.

2. **Preguntas**
   - Una pregunta por pantalla.
   - Cuatro opciones de respuesta.
   - Avance visible, por ejemplo: “Pregunta 3 de 10”.
   - No permitir avanzar sin seleccionar una opción.
   - Permitir volver a la pregunta anterior.

3. **Cálculo**
   - Cada opción tiene un valor de 1 a 4.
   - Se calcula el promedio de las respuestas.
   - El promedio se transforma en un nivel de madurez.

4. **Resultado**
   - Nivel obtenido.
   - Nombre del nivel.
   - Explicación en lenguaje simple.
   - Principales fortalezas o capacidades presentes.
   - Brechas prioritarias.
   - Recomendaciones prácticas.

5. **Invitación final**
   - Preguntar: “¿Te serviría usar esta herramienta en tu empresa?”.
   - Respuestas: “Sí”, “Tal vez” o “No”.
   - Solicitar contacto solo de manera opcional y con consentimiento explícito.

## 4. Modelo de madurez

Estos niveles son una propuesta inicial tomada de la ficha del curso. Deben validarse con Francisco Núñez antes de cerrar el contenido.

| Nivel | Nombre provisorio | Descripción |
|---|---|---|
| 1 | Registros operativos | La organización registra información básica y produce reportes manuales o aislados. |
| 2 | Análisis histórico | Existen KPIs definidos, dashboards y análisis de lo que ya ocurrió. |
| 3 | Analítica predictiva | Se utilizan modelos estadísticos o de machine learning para anticipar situaciones de RR.HH. |
| 4 | Decisiones integradas al negocio | Las predicciones se conectan con recomendaciones, ROI y decisiones estratégicas. |

## 5. Regla de cálculo provisoria

Cada alternativa tiene un puntaje:

- alternativa correspondiente al nivel 1: `1`;
- alternativa correspondiente al nivel 2: `2`;
- alternativa correspondiente al nivel 3: `3`;
- alternativa correspondiente al nivel 4: `4`.

Se calcula el promedio de todos los puntajes:

```text
promedio = suma de puntajes / cantidad de preguntas respondidas
```

Rangos iniciales sugeridos:

| Promedio | Resultado |
|---|---|
| 1,00 a 1,74 | Nivel 1 |
| 1,75 a 2,49 | Nivel 2 |
| 2,50 a 3,24 | Nivel 3 |
| 3,25 a 4,00 | Nivel 4 |

Estos rangos son técnicos y provisorios. El equipo de contenido debe confirmar si representan correctamente el modelo pedagógico.

## 6. Preguntas multiple choice propuestas

Estas preguntas son un primer borrador para discutir y validar. En la versión de la herramienta, cada pregunta debería mostrar únicamente el texto y las opciones; los puntajes no deben ser visibles para el alumno.

### Pregunta 1 · Disponibilidad de datos

¿Cómo se encuentra actualmente la información de RR.HH. en tu organización?

- A. Está dispersa, se registra manualmente o no siempre está disponible. **Puntaje: 1**
- B. Está centralizada en algunos sistemas y permite generar reportes periódicos. **Puntaje: 2**
- C. Está integrada y preparada para realizar análisis estadísticos o predictivos. **Puntaje: 3**
- D. Está integrada con información del negocio y se utiliza para orientar decisiones. **Puntaje: 4**

### Pregunta 2 · Indicadores utilizados

¿Qué tipo de indicadores utiliza principalmente el área de RR.HH.?

- A. Cantidad de personas, ausentismo, altas, bajas u otros datos operativos. **Puntaje: 1**
- B. KPIs definidos y revisados periódicamente mediante reportes o dashboards. **Puntaje: 2**
- C. Indicadores que permiten anticipar rotación, desempeño u otros resultados. **Puntaje: 3**
- D. Indicadores de RR.HH. conectados con resultados financieros y estratégicos. **Puntaje: 4**

### Pregunta 3 · Forma de reportar

¿Cómo se preparan los informes de RR.HH.?

- A. Se arman manualmente cuando alguien los solicita. **Puntaje: 1**
- B. Existen informes periódicos con una estructura definida. **Puntaje: 2**
- C. Se complementan con análisis de causas, tendencias y probabilidades. **Puntaje: 3**
- D. Incluyen recomendaciones concretas para decidir y hacer seguimiento del impacto. **Puntaje: 4**

### Pregunta 4 · Rotación de personal

¿Cómo aborda la organización el riesgo de perder personas clave?

- A. Lo analiza principalmente después de que la persona se va. **Puntaje: 1**
- B. Revisa la rotación histórica y sus principales características. **Puntaje: 2**
- C. Utiliza modelos o señales para identificar posibles casos de fuga. **Puntaje: 3**
- D. Combina predicción, acciones de retención y medición del impacto de esas acciones. **Puntaje: 4**

### Pregunta 5 · Calidad de los datos

¿Cómo se controla la calidad de los datos de RR.HH.?

- A. No existe un control sistemático o depende de cada persona. **Puntaje: 1**
- B. Se revisan errores y faltantes antes de preparar los reportes. **Puntaje: 2**
- C. Existen procesos de limpieza, validación y preparación para modelos. **Puntaje: 3**
- D. Hay gobierno de datos, responsables definidos y controles vinculados al negocio. **Puntaje: 4**

### Pregunta 6 · Uso de herramientas

¿Qué herramientas se utilizan para analizar información de personas?

- A. Planillas y registros independientes. **Puntaje: 1**
- B. Dashboards o herramientas de BI para consultar información histórica. **Puntaje: 2**
- C. Herramientas estadísticas o de machine learning. **Puntaje: 3**
- D. Una combinación integrada de BI, analítica avanzada y recomendaciones para la gestión. **Puntaje: 4**

### Pregunta 7 · Relación con el negocio

¿Cómo se vincula People Analytics con las prioridades de la organización?

- A. Principalmente responde pedidos administrativos del área de RR.HH. **Puntaje: 1**
- B. Muestra tendencias que ayudan a revisar la gestión del área. **Puntaje: 2**
- C. Ayuda a anticipar problemas relevantes para la organización. **Puntaje: 3**
- D. Participa en decisiones estratégicas y demuestra impacto o ROI. **Puntaje: 4**

### Pregunta 8 · Recomendaciones

¿Qué ocurre después de analizar los datos?

- A. Se informa el resultado, pero no hay una acción definida. **Puntaje: 1**
- B. Se identifican tendencias y se proponen acciones generales. **Puntaje: 2**
- C. Se priorizan acciones según riesgos o probabilidades estimadas. **Puntaje: 3**
- D. Se implementan recomendaciones, se mide su impacto y se ajustan las decisiones. **Puntaje: 4**

### Pregunta 9 · Capacidades del equipo

¿Qué capacidades tiene el equipo para trabajar con People Analytics?

- A. Principalmente capacidades operativas de registro y reporte. **Puntaje: 1**
- B. Capacidad para construir KPIs, dashboards y análisis descriptivos. **Puntaje: 2**
- C. Capacidad para desarrollar o interpretar modelos predictivos. **Puntaje: 3**
- D. Capacidad para conectar analítica, estrategia, cambio y resultados del negocio. **Puntaje: 4**

### Pregunta 10 · Toma de decisiones

¿Cómo se utilizan los resultados de People Analytics?

- A. Como información de consulta o respaldo de decisiones ya tomadas. **Puntaje: 1**
- B. Para revisar el desempeño pasado y detectar tendencias. **Puntaje: 2**
- C. Para anticipar escenarios y decidir dónde intervenir. **Puntaje: 3**
- D. Para tomar decisiones, asignar recursos y evaluar el resultado de las intervenciones. **Puntaje: 4**

## 7. Criterios de aceptación

La versión de prueba se considera funcional cuando:

- se puede comenzar y completar el cuestionario desde un celular;
- se responde una pregunta por vez;
- no se puede avanzar sin responder;
- se puede volver a una pregunta anterior;
- el cálculo devuelve un nivel válido entre 1 y 4;
- el resultado explica el nivel y muestra recomendaciones;
- se puede reiniciar el cuestionario;
- la invitación final aparece al completar el diagnóstico;
- no se solicitan datos personales para ver el resultado;
- los datos de prueba no contienen nombres reales de alumnos o empresas.

## 8. Casos de prueba funcionales

| Caso | Acción | Resultado esperado |
|---|---|---|
| CP-01 | Completar todas las respuestas con puntaje 1 | Se obtiene nivel 1 |
| CP-02 | Completar todas las respuestas con puntaje 2 | Se obtiene nivel 2 |
| CP-03 | Completar todas las respuestas con puntaje 3 | Se obtiene nivel 3 |
| CP-04 | Completar todas las respuestas con puntaje 4 | Se obtiene nivel 4 |
| CP-05 | Intentar avanzar sin responder | La aplicación solicita seleccionar una opción |
| CP-06 | Volver y cambiar una respuesta | El resultado se recalcula correctamente |
| CP-07 | Recargar durante el cuestionario | Se define si se conserva o se pierde el progreso; debe documentarse |
| CP-08 | Completar desde una pantalla pequeña | No hay texto cortado ni botones inaccesibles |
| CP-09 | Elegir “Sí” en la invitación sin dejar contacto | Se registra el interés sin obligar a informar datos |
| CP-10 | No aceptar la invitación | El resultado sigue disponible y el diagnóstico termina normalmente |

## 9. Datos y privacidad

Para la primera versión se deben guardar solamente datos necesarios para validar el uso:

- tipo de diagnóstico;
- fecha y hora de inicio y finalización;
- respuestas o puntajes;
- nivel obtenido;
- respuesta a la invitación comercial;
- contacto únicamente si la persona lo deja voluntariamente y acepta ser contactada.

No se deben guardar nombres, empresas, correos ni otros datos identificables como requisito para realizar el diagnóstico.

Los resultados que se muestren al grupo deben ser agregados, por ejemplo: cantidad de respuestas por nivel o promedio general. Nunca se deben mostrar resultados individuales con nombre.

## 10. Decisiones pendientes

Antes de cerrar la versión final, el equipo debe resolver:

1. ¿Francisco Núñez confirma los cuatro niveles propuestos?
2. ¿Las diez preguntas son suficientes o se debe reducir o ampliar el cuestionario?
3. ¿El resultado se calcula con promedio simple o algunas preguntas tienen mayor peso?
4. ¿El alumno responde pensando en su organización, en su área o en su propia experiencia?
5. ¿Se permite reiniciar el diagnóstico o editar respuestas antes de enviarlo?
6. ¿Qué recomendaciones concretas corresponden a cada nivel?
7. ¿Qué información anónima se mostrará en la sesión 7?
8. ¿Qué contacto se solicita y qué texto de consentimiento debe acompañarlo?

## 11. Próximo paso de implementación

1. Validar este documento con Anabelle y Gonzalo M.
2. Confirmar con Naomi o Francisco el modelo de niveles.
3. Pasar a Gonzalo H. el flujo para el diseño visual.
4. Pasar a Gonzalo M. los componentes y comportamientos esperados.
5. Implementar primero el cálculo con datos ficticios.
6. Probar los casos CP-01 a CP-06 antes de conectar una base de datos.

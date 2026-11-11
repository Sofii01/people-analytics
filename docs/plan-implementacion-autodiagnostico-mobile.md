# Plan de implementación · Autodiagnóstico People Analytics Mobile

## 1. Enfoque

La primera versión será una **app web mobile-first**: se abre desde un link en el celular, sin instalar nada y sin requerir una cuenta.

Como mejora posterior podrá convertirse en una PWA instalable, pero para la prueba del 20/11 y la versión final del 26/11 no se necesita publicar en App Store ni Play Store.

El objetivo del MVP es que una persona pueda completar el diagnóstico desde su celular, recibir un resultado comprensible y dejar una señal opcional de interés comercial.

## 2. Objetivo técnico del MVP

La app debe permitir:

- acceder desde un link público;
- leer una breve introducción;
- responder un cuestionario multiple choice;
- avanzar y retroceder entre preguntas;
- ver el progreso;
- calcular uno de cuatro niveles;
- recibir explicación y recomendaciones;
- responder la invitación final;
- guardar resultados anónimos;
- funcionar correctamente en celulares pequeños y medianos.

## 3. Stack recomendado

| Necesidad | Tecnología |
|---|---|
| Interfaz | React + TypeScript |
| Build y desarrollo local | Vite |
| Estilos | CSS mobile-first; Tailwind opcional si el equipo ya lo conoce |
| Lógica de cálculo | TypeScript sin dependencia de la interfaz |
| Persistencia | Supabase |
| Pruebas unitarias | Vitest |
| Pruebas en navegador | Playwright, si hay tiempo |
| Publicación | Netlify o Vercel |
| Control de versiones | GitHub |

No se necesita backend propio ni inteligencia artificial para la primera versión.

## 4. Estructura del proyecto

```text
app/
├─ public/
│  ├─ favicon.svg
│  └─ manifest.webmanifest          # opcional para PWA
├─ src/
│  ├─ components/
│  │  ├─ WelcomeScreen.tsx
│  │  ├─ QuestionScreen.tsx
│  │  ├─ AnswerOption.tsx
│  │  ├─ ProgressBar.tsx
│  │  ├─ ResultScreen.tsx
│  │  ├─ RecommendationList.tsx
│  │  └─ BusinessInvitation.tsx
│  ├─ config/
│  │  └─ peopleAnalytics.ts
│  ├─ domain/
│  │  ├─ types.ts
│  │  ├─ calculateLevel.ts
│  │  └─ calculateResult.ts
│  ├─ services/
│  │  ├─ resultsRepository.ts
│  │  └─ supabaseClient.ts
│  ├─ styles/
│  │  ├─ variables.css
│  │  ├─ global.css
│  │  └─ mobile.css
│  ├─ App.tsx
│  └─ main.tsx
├─ tests/
│  ├─ calculateLevel.test.ts
│  ├─ calculateResult.test.ts
│  └─ questionnaire-flow.test.tsx
├─ .env.example
├─ README.md
├─ package.json
└─ vite.config.ts
```

## 5. Principios de diseño mobile-first

### Pantalla

- Diseñar primero para un ancho de 360 px.
- Usar una sola columna.
- Evitar tablas, menús laterales y elementos pequeños.
- Mantener el contenido principal dentro de un ancho cómodo de lectura.
- Usar márgenes laterales de al menos 16 px.

### Interacción

- Cada opción debe ser un botón o tarjeta grande, no un checkbox pequeño.
- El área táctil mínima recomendada es de aproximadamente 44 px de alto.
- Separar visualmente las opciones para evitar toques accidentales.
- Mostrar claramente cuál opción fue seleccionada.
- El botón principal debe estar siempre visible sin desplazamientos innecesarios.

### Texto

- Una pregunta por pantalla.
- No mostrar más de cuatro opciones largas al mismo tiempo si obliga a demasiado scroll.
- Usar títulos breves y lenguaje claro.
- Evitar depender solamente del color para indicar selección o error.

### Estados

La interfaz debe contemplar:

- carga inicial;
- pregunta sin responder;
- respuesta seleccionada;
- error al guardar;
- resultado listo;
- reinicio del diagnóstico;
- falta de conexión al enviar el resultado.

## 6. Flujo funcional

```text
Bienvenida
    ↓
Pregunta 1
    ↓
Pregunta 2 ... Pregunta N
    ↓
Procesar respuestas
    ↓
Resultado y recomendaciones
    ↓
Invitación comercial opcional
    ↓
Confirmación y cierre
```

### Bienvenida

Debe incluir:

- nombre del autodiagnóstico;
- propósito;
- aclaración de que no es una evaluación;
- tiempo estimado;
- aviso de anonimato;
- botón “Comenzar”.

### Preguntas

Debe incluir:

- número de pregunta;
- progreso;
- texto de la pregunta;
- cuatro alternativas;
- botón “Continuar”;
- botón “Anterior” desde la segunda pregunta.

### Resultado

Debe incluir:

- nivel obtenido;
- nombre del nivel;
- explicación de qué significa;
- fortalezas;
- brechas;
- entre tres y cinco recomendaciones prácticas;
- botón para reiniciar o finalizar.

### Invitación final

Debe preguntar si la persona usaría la herramienta en su empresa.

El contacto debe ser opcional. La persona debe poder finalizar sin entregar nombre, correo ni empresa.

## 7. Arquitectura funcional

La configuración de People Analytics no debe quedar mezclada con los componentes visuales.

```text
peopleAnalytics.ts
        ↓
App / QuestionScreen
        ↓
respuestas del usuario
        ↓
calculateLevel.ts
        ↓
calculateResult.ts
        ↓
ResultScreen
        ↓
resultsRepository.ts
```

La futura configuración de RR.HH. 4.0 debería poder reemplazar `peopleAnalytics.ts` sin duplicar el motor ni las pantallas.

## 8. Fases de implementación

### Fase 0 · Preparación

**Responsable principal:** Sofía  
**Apoyo:** Gonzalo M. y Valentino

- Crear el repositorio GitHub.
- Crear la carpeta `app`.
- Inicializar React + TypeScript + Vite.
- Definir cómo se ejecuta el proyecto localmente.
- Agregar un README técnico.
- Confirmar la versión de Node y el gestor de paquetes.

**Salida:** proyecto vacío que inicia localmente con un comando.

### Fase 1 · Modelo y lógica

**Responsable principal:** Sofía  
**Apoyo:** Anabelle

- Definir tipos de preguntas, respuestas, niveles y recomendaciones.
- Cargar preguntas ficticias o el primer borrador.
- Implementar cálculo de promedio y nivel.
- Implementar resultado por nivel.
- Crear pruebas para los cuatro niveles.

**Salida:** motor que recibe respuestas y devuelve un resultado correcto sin depender de la interfaz.

### Fase 2 · Prototipo mobile

**Responsable:** Gonzalo H. para diseño; Gonzalo M. para desarrollo  
**Coordinación funcional:** Sofía

- Implementar bienvenida.
- Implementar una pregunta por pantalla.
- Implementar progreso.
- Implementar selección y navegación.
- Implementar resultado.
- Usar contenido de ejemplo hasta validar las preguntas finales.

**Salida:** flujo completo navegable desde un celular, sin base de datos.

### Fase 3 · Integración funcional

**Responsable principal:** Sofía  
**Apoyo:** Gonzalo M.

- Conectar las preguntas reales.
- Conectar el cálculo con el resultado visual.
- Agregar recomendaciones por nivel.
- Agregar reinicio.
- Agregar validaciones de respuestas.
- Incorporar la invitación final de T-024.

**Salida:** versión de prueba completa.

### Fase 4 · Persistencia anónima

**Responsable:** Sofía con apoyo de Valentino o Gonzalo M.**

- Crear proyecto de Supabase.
- Crear tablas para sesiones, respuestas y señal de interés.
- Activar Row Level Security.
- Guardar únicamente información necesaria.
- No pedir cuenta para completar el diagnóstico.
- Probar que no se puedan consultar resultados individuales desde la app pública.

**Salida:** resultados y métricas básicas guardados de manera anónima.

### Fase 5 · Pruebas mobile

**Responsable:** Gonzalo H. y Gonzalo M.  
**Coordinación:** Sofía

Probar como mínimo en:

- un celular Android pequeño;
- un celular Android mediano;
- un iPhone o simulador equivalente;
- Chrome;
- Safari o navegador equivalente.

Revisar:

- texto cortado;
- botones difíciles de tocar;
- scroll excesivo;
- orientación vertical;
- pérdida de progreso;
- conexión lenta;
- respuestas extremas;
- finalización sin contacto.

**Salida:** lista de errores corregidos y versión candidata para publicar.

### Fase 6 · Publicación

**Responsable:** Valentino  
**Apoyo:** Sofía

- Configurar el build de producción.
- Publicar en Netlify o Vercel.
- Probar el link desde un celular sin estar conectado al entorno local.
- Verificar que no haya datos de prueba visibles.
- Compartir la URL con el equipo.
- Mantener una URL estable para el curso.

**Salida:** link público para la prueba y para el curso.

## 9. Plan de entregas

| Entrega | Contenido | Fecha |
|---|---|---|
| Base técnica | Repositorio y app ejecutable | Lo antes posible |
| Motor | Tipos, cálculo y pruebas | Antes del prototipo visual |
| Prototipo mobile | Flujo completo sin persistencia | Antes del 20/11 |
| Versión de prueba | Preguntas, niveles, recomendaciones e invitación | 20/11/2026 |
| Ajustes | Correcciones después de probar con 3 a 5 personas | 24–25/11/2026 |
| Versión final | Publicada y estable | 26/11/2026 |
| Uso en curso | Diagnóstico disponible para alumnos | 29/11/2026 |

## 10. Criterios técnicos de aceptación

La app está lista para la prueba cuando:

- se inicia con `npm run dev`;
- se puede completar con una sola mano en un celular;
- funciona sin login;
- no se rompe al volver a una pregunta;
- no permite avanzar sin respuesta;
- calcula correctamente los cuatro niveles;
- muestra recomendaciones distintas según el resultado;
- permite finalizar sin dejar contacto;
- no expone claves secretas en el frontend;
- registra errores de guardado sin bloquear toda la experiencia;
- funciona con conexión móvil normal;
- el link publicado abre directamente la aplicación.

## 11. Orden recomendado para Sofía

1. Confirmar con el equipo que este será el alcance del MVP.
2. Crear el repositorio o pedirle a Valentino acceso al repositorio compartido.
3. Crear la especificación de datos y la regla de cálculo.
4. Entregarle a Gonzalo M. los comportamientos esperados de cada pantalla.
5. Cargar preguntas provisionales para que el equipo pueda probar el flujo.
6. Validar niveles, preguntas y recomendaciones con Anabelle y Francisco.
7. Revisar funcionalmente el prototipo en un celular.
8. Conectar el guardado anónimo.
9. Coordinar la prueba con 3 a 5 personas.
10. Registrar errores, priorizar correcciones y aprobar la versión final.

## 12. Decisiones que no deben bloquear el MVP

Estas mejoras pueden quedar para una segunda etapa:

- aplicación nativa;
- login de alumnos;
- dashboard administrativo;
- comparación entre empresas;
- exportación a PDF;
- integración con Power BI;
- recomendaciones generadas por IA;
- modo offline completo;
- personalización visual avanzada.

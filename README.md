<div align="center">

# Neural Ghost

**Ciberinteligencia, OSINT profundo e IA aplicada a la seguridad**

Compañía española de ciberseguridad e inteligencia de fuentes abiertas.
Plataforma propia, modelo de lenguaje propio, operación propia.

[![Ubicación](https://img.shields.io/badge/Castellón-España-0b3d2e?style=flat-square)](#)
[![CNAE](https://img.shields.io/badge/CNAE-62.20-1f6feb?style=flat-square)](#)
[![Contacto](https://img.shields.io/badge/neural%40neural--ghost.com-informe-24292f?style=flat-square&logo=maildotru&logoColor=white)](mailto:neural@neural-ghost.com)
[![Seguridad](https://img.shields.io/badge/divulgación-coordinada-8957e5?style=flat-square)](https://github.com/jmpicon/jmpicon/blob/HEAD/SECURITY.md)

</div>

---

## Qué hacemos

Investigamos lo que una organización expone sin saberlo, y lo convertimos en
decisiones. No vendemos un panel: entregamos hallazgos verificados, con su
procedencia y su nivel de confianza declarado.

El trabajo se apoya en una plataforma construida en casa —motor de
investigación, modelo de lenguaje especializado y automatización de operación—
porque los productos generalistas no llegan a las capas donde está la
información que importa: filtraciones de credenciales, foros cerrados, redes
anónimas, infraestructura olvidada, suplantaciones de marca en preparación.

### Cuatro líneas de trabajo

| | Línea | En qué consiste |
|:--:|---|---|
| 🔍 | **Inteligencia de amenazas** | Vigilancia continua de la exposición de una organización: credenciales filtradas, menciones en foros y canales cerrados, infraestructura publicada por error, dominios que imitan la marca. Entrega periódica con hallazgos accionables. |
| 🛡️ | **Superficie de exposición** | Reconocimiento pasivo de todo lo que la organización presenta a internet, incluido lo que ya no recuerda que tiene. Inventario, priorización por explotabilidad real y plan de reducción. |
| 🧭 | **Dirección de seguridad externalizada** | Función de responsable de seguridad para organizaciones que necesitan criterio y gobierno sin plantilla propia: política, respuesta a incidentes, relación con proveedores, cumplimiento. |
| 🎓 | **Formación y capacitación** | Programas de ciberseguridad para formación profesional y empresa: puesta en producción segura, hacking ético, incidentes, seguridad de sistemas de IA. |

---

## La plataforma

### GhostNet · motor de investigación

El núcleo. Un servicio de investigación con **380 puntos de acceso** que
orquesta reconocimiento, correlación y enriquecimiento sobre múltiples capas de
información, y devuelve hallazgos normalizados y exportables a los formatos
estándar de la industria.

```
                    ┌──────────────────────────────────────┐
   corporativo ───▶ │                                      │
   infraestructura ▶│           GhostNet                   │──▶ hallazgos
   filtraciones ───▶│   correlación · enriquecimiento      │    normalizados
   redes anónimas ─▶│   grafo de entidades · trazabilidad  │──▶ export estándar
   canales cerrados▶│                                      │──▶ informe
   cadena de bloques│                                      │
                    └──────────────┬───────────────────────┘
                                   │
                        DarkForensic-7B · análisis
```

**Principios de diseño, que son también los que se aplican al análisis:**

- **Un resultado vacío no es un resultado limpio.** Un contador a cero con una
  petición fallida detrás se marca como *no verificable*, nunca como *sin
  hallazgos*. Es la distinción que separa un informe de una lista de deseos.
- **La existencia se verifica por contenido.** Un código de respuesta correcto
  no prueba que el recurso exista: muchos servidores devuelven una portada
  genérica ante cualquier petición.
- **Un hallazgo sin procedencia no es un hallazgo.** Cada dato lleva su origen,
  su marca temporal y el método con el que se obtuvo.
- **La cobertura se declara con números.** «Revisado» no es una respuesta;
  «revisados 34 de 41 activos, 7 no accesibles por X» sí lo es. Una nota de
  riesgo calculada sobre cobertura insuficiente se marca como no concluyente en
  lugar de presentarse como conclusión.

### DarkForensic-7B · modelo de lenguaje propio

Modelo especializado en inteligencia de amenazas **en español**, ajustado sobre
corpus del dominio. Publicado y ejecutable en infraestructura propia, sin que el
material del cliente salga hacia servicios de terceros.

Existe por una razón concreta: en un análisis de seguridad, el material que se
procesa es precisamente el que no debe atravesar la API de otra compañía.

### Componentes

| Componente | Qué resuelve | Estado |
|---|---|---|
| **GhostNet** | Motor de investigación y correlación | Producción |
| **DarkForensic-7B** | Modelo de lenguaje de dominio, en español | Publicado |
| **NGX Exposure Score** | Nota de exposición sobre nueve vectores, con grado A–F y **cobertura declarada**: por debajo del umbral, el resultado se emite como no concluyente | Producción |
| **GhostShield** | Agentes de detección y verificación con reglas deterministas | Producción |
| **Chainscope** | Análisis forense de cadena de bloques: trazado, contrapartes, origen de fondos | Producción |
| **SOC Cockpit** | Consola de operación y vigilancia continua | Producción |
| **RansomWatch** | Vigilancia de publicaciones de extorsión con foco en España, Europa y América Latina | Producción |
| **NG-Estructura** | Verificación de integridad de entregables con sellado de tiempo acreditado y árbol de Merkle | Producción |
| **NG-Custodia** | Cadena de custodia de hallazgos: sellado, salado por hallazgo y verificación independiente | Producción |
| **GhostWire** | Mensajería anónima sobre red cebolla, cifrada extremo a extremo | Público · AGPL |

---

## Ingeniería

La plataforma no es un conjunto de guiones. Es infraestructura operada con las
prácticas que se le exigirían a cualquier proveedor de seguridad serio.

### Stack

`Python 3.11+` · `FastAPI` · `Go` · `PostgreSQL` + `pgvector` · `Docker` ·
`systemd` · `Caddy` · `GitHub Actions` · redes anónimas para la capa de
investigación

### Operación

- **Autonomía por defecto.** Los procesos periódicos se ejecutan solos y solo
  notifican lo crítico. Un sistema que exige atención constante no está
  terminado.
- **Fallo ruidoso.** Un detector permanentemente en estado de error está
  apagado, aunque su cuadro de mando siga en verde. El código de salida dice si
  el detector se ejecutó, no si encontró algo. Los monitores avisan de su propio
  fallo, no solo del fallo que vigilan.
- **Restauración probada.** Una copia de seguridad que no se ha restaurado
  nunca no es una copia de seguridad. Se verifica restaurando.
- **Configuración declarativa.** El estado de la infraestructura está descrito
  en un repositorio, y el repositorio no contiene ni un secreto.

### Seguridad del ciclo de desarrollo

Cada repositorio de la plataforma pasa por la misma cadena, y los controles
bloquean la integración en lugar de limitarse a informar. Los gates previos al
commit se ejecutan en la máquina de desarrollo; los de integración, en cada
cambio propuesto:

| Etapa | Control |
|---|---|
| Antes del commit | Detección de secretos · gate de confidencialidad y datos personales · formato y lint |
| En cada cambio | Análisis estático con reglas propias · análisis de dependencias · tests con cobertura |
| En cada compilación | Inventario de componentes (SBOM, CycloneDX) · análisis de vulnerabilidades · análisis de la imagen |
| Al publicar | Firma sin claves con identidad federada · atestación de procedencia · inventario firmado adjunto |
| Continuo | Actualización automática de dependencias · alertas de vulnerabilidad · reanálisis programado · permisos mínimos del token de integración |

Las reglas de análisis estático propias no son buenas prácticas genéricas: cada
una existe porque el fallo correspondiente ya ocurrió en producción y se
convirtió en una regla para que no vuelva. Entre ellas, la que detecta
credenciales viajando en la línea de dirección de una petición —donde acaban
copiadas en cualquier mensaje de error que se registre.

---

## Repositorios públicos

| Repositorio | Qué es | Licencia |
|---|---|---|
| [**ghostwire**](https://github.com/jmpicon/ghostwire) | Mensajería anónima sobre red cebolla, cifrada extremo a extremo. Go. | AGPL-3.0 |
| [**flipper-academy**](https://github.com/jmpicon/flipper-academy) | Plataforma educativa española de hardware hacking ético | — |
| [**SecuAI-jmpicon**](https://github.com/jmpicon/SecuAI-jmpicon) | Curso de securización de sistemas de inteligencia artificial | — |
| [**PPS-jmpicon**](https://github.com/jmpicon/PPS-jmpicon) | Plataforma docente de puesta en producción segura | — |
| [**Cuantica**](https://github.com/jmpicon/Cuantica) | Material de aprendizaje en computación cuántica | — |

Los repositorios de la plataforma son privados: contienen metodología de
investigación y material sujeto a acuerdos de confidencialidad.

---

## Quién

**José Picón Giménez** — fundador y administrador único.

Desarrollador con foco en inteligencia artificial y ciberseguridad. Profesor de
ciclo formativo de grado superior en ciberseguridad. Once años de experiencia
previa en Londres, donde llegó a la dirección de operaciones de centro antes de
volver a la ingeniería.

Construye lo que opera: el motor, el modelo, la infraestructura y los controles
que los vigilan.

---

## Trabajemos juntos

Si tu organización necesita saber qué expone, qué se está preparando contra
ella, o necesita criterio de seguridad sin montar un departamento:

📧 **neural@neural-ghost.com**

Para reportar un fallo de seguridad en cualquiera de estos repositorios o
servicios, consulta la [política de divulgación](https://github.com/jmpicon/jmpicon/blob/HEAD/SECURITY.md).
No abras un issue público.

<div align="center">
<sub>

**NEURAL GHOST, S.L.U.** · NIF B93935252 · Culla, Castellón, España
CNAE 62.20 — Actividades de consultoría informática

</sub>
</div>

# Respuestas · Laboratorio 4
Alumno: [20221943]
Presupuesto: [ ] min  Métrica DORA: [ ]

## Parte 1 · Diagnóstico
### Defecto 1
- Job y etapa: unit, en npm run test:unit
- Problema que causa en el pipeline: solo se cuenta con cobertura de wallet.js y util.js, no de los demás archivos .js como db.js y handler.js
- Link al commit: https://github.com/lalvitesg/INF384-LAB4-20221943/commit/d16e5d2f0b1fa57ce31ef7e0b2e05bbfa0356901
- Corrección (una o más: mover de etapa / dejar como informativo / eliminar / ajustar configuración / modificar tests): Dejar como informativo
- Evidencia (dato observado, con link al run o fragmento de la salida local): https://github.com/lalvitesg/INF384-LAB4-20221943/actions/runs/40963203202
### Defecto 2
- Job y etapa: integration, npm run test:integration
- Problema que causa en el pipeline: se usa DB_PATH: /tmp/wallet.db y no se limpia antes de cada ejecución; además la base se comparte entre pruebas.
- Link al commit: https://github.com/lalvitesg/INF384-LAB4-20221943/commit/e85f08f814740c5f5a5c21208632749aeb30575b
- Corrección (una o más: mover de etapa / dejar como informativo / eliminar / ajustar configuración / modificar tests): Dejar como informativo
- Evidencia (dato observado, con link al run o fragmento de la salida local): https://github.com/lalvitesg/INF384-LAB4-20221943/actions/runs/40963055370
### Defecto 3
- Job y etapa: sast, semgrep scan
- Problema que causa en el pipeline: eja fuera otros puntos relevantes del repo (configuración, tests, dependencias, infraestructura), por lo que se pueden escapar vulnerabilidades o hallazgos de seguridad. Es un falso negativo: “no lo detecta aunque exista”.
- Link al commit: https://github.com/lalvitesg/INF384-LAB4-20221943/commit/852e9dba8d64fe174525f46240674c2894bf26bc 
- Corrección (una o más: mover de etapa / dejar como informativo / eliminar / ajustar configuración / modificar tests): Modificar tests
- Evidencia (dato observado, con link al run o fragmento de la salida local): https://github.com/lalvitesg/INF384-LAB4-20221943/actions/runs/40962323619
### Defecto 4
- Job y etapa: build-push, en Push
- Problema que causa en el pipeline: el paso de Trivy genera un warning con ::warning y no hace exit 1; el job sigue y empuja la imagen.
- Link al commit: https://github.com/lalvitesg/INF384-LAB4-20221943/commit/f474eaefa8a796c6d1104b5dfb2d74e4c8da273b
- Corrección (una o más: mover de etapa / dejar como informativo / eliminar / ajustar configuración / modificar tests): Modificar tests
- Evidencia (dato observado, con link al run o fragmento de la salida local): https://github.com/lalvitesg/INF384-LAB4-20221943/actions/runs/40964057011
### Defecto 5
- Job y etapa: smoke, URL
- Problema que causa en el pipeline: smoke, e2e y load dependen de build-push, no de deploy, por lo que validan un URL que puede ser la versión anterior o incluso no estar actualizada.
- Link al commit: https://github.com/lalvitesg/INF384-LAB4-20221943/commit/4e6fe13c9bbaae1d20d15b598be90611620fbdc3
- Corrección (una o más: mover de etapa / dejar como informativo / eliminar / ajustar configuración / modificar tests): Ajustar configuración
- Evidencia (dato observado, con link al run o fragmento de la salida local): https://github.com/lalvitesg/INF384-LAB4-20221943/actions/runs/40961363746

## Parte 2 · Implementación
- Link al run en verde en main: 
- Link al pull request:
- Defecto de la aplicación introducido (archivo y descripción):
- Job que debería detenerlo:
- Link al run fallido:

## Parte 3 · Decisión bajo restricción
Link al run medido:

| Job | Duración (min:seg) |
|---|---|
| unit | |
| integration | |
| sast | |
| sca | |
| build-push | |
| deploy | |
| smoke | |
| e2e | |
| load | |
| **Total** | |

Resultado de load en ese run:
| Métrica | Valor |
|---|---|
| p90 | |
| p95 | |
| Máximo | |
| Tasa de error | |
| Requests por segundo | |

Conclusión sobre el comportamiento bajo carga:

SLO propuesto (percentil, valor, ventana) y justificación:

SLA propuesto y diferencia con el SLO:

Cambios para cumplir el presupuesto:
| Cambio | Job | Minutos recuperados |
|---|---|---|

Total resultante: [ ] min
Link al run en main con los cambios:

Riesgo aceptado (defecto de la aplicación concreto y efecto en la métrica DORA asignada):

Decisión sobre sast (se queda / se mueve a otra etapa o evento / informativo) y razón:

## Declaración de uso de IA
Herramientas usadas y para qué:

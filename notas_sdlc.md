Resumen de Seguridad en el Ciclo de Vida del Software (SDLC)

Este repositorio contiene los apuntes clave sobre los conceptos de seguridad integrados en el pipeline de desarrollo.

1. Postura de Seguridad y SSDLC

El SSDLC (Secure SDLC) implica integrar seguridad en todas las fases del ciclo de vida.

Análisis de brechas: Entender qué políticas existen y qué tan efectivas son.

Iniciativas (SSI): Establecer objetivos medibles.

Entrenamiento: Capacitar al equipo antes de introducir herramientas nuevas.

Procesos del SSDLC

Planning: Realizar Risk Assessment (Identificación de riesgos).

Design: Aplicar Threat Modelling (¿Qué podría salir mal?).

Development: Code Scanning (SAST).

Operations: Security Assessments (Penetration Testing).

2. Evaluación de Riesgos (Risk Assessment)

Cualitativo: Clasificación en niveles (Bajo, Medio, Alto). Fórmula: Severidad x Probabilidad.

Cuantitativo: Uso de valores numéricos para medir el impacto financiero o crítico.

3. Modelado de Amenazas (Threat Modelling)

Estructuras para identificar amenazas en la fase de diseño:

STRIDE (Microsoft): Basado en la tríada CIA (Spoofing, Tampering, Repudiation, Information Disclosure, DoS, Elevation of Privilege).

DREAD: Sistema de puntuación para priorizar riesgos (Daño, Reproducibilidad, Explotabilidad, Usuarios, Descubribilidad).

PASTA: Enfoque estratégico que alinea los riesgos técnicos con los objetivos de negocio.

4. Análisis de Código (SAST, DAST, IAST)

SAST (Caja Blanca): Analiza código fuente sin ejecutarlo. Se usa al inicio.

DAST (Caja Negra): Analiza la aplicación en ejecución. Se usa en etapas finales.

IAST (Caja Gris): Combina el análisis del código con el comportamiento en ejecución.

RASP: Protección activa dentro de la aplicación en producción.

5. Gestión de Dependencias

Internas: Creadas por la organización.

Externas: Librerías públicas (ej. jQuery, paquetes de PyPi).

Lección clave: La gestión de dependencias es crítica. El caso Log4Shell (2021) demostró cómo una pequeña librería vulnerable puede comprometer toda una infraestructura.

6. Pipeline CI/CD

Orquestadores: Controlan los builds.

Agentes: Ejecutan las tareas.

Seguridad: Nunca compartir agentes entre entornos de DESARROLLO (DEV) y PRODUCCIÓN (PROD) para evitar inyección de código malicioso.

7. Entornos (Environments)

DEV: Seguridad débil, mayor agilidad.

UAT: Pruebas de aceptación del usuario.

PreProd: Réplica de producción.

PROD: Seguridad máxima.

Riesgo: Developer bypasses (ej. saltarse 2FA en DEV) nunca deben llegar a PROD.

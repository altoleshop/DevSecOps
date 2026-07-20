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

---

### Resumen: La Historia de Git

Git no nació de un plan corporativo, sino de una **necesidad técnica y un conflicto**.

* **El problema:** Antes de 2005, el kernel de Linux usaba una herramienta llamada **BitKeeper** para gestionar el desarrollo distribuido. Sin embargo, debido a desacuerdos entre el creador de BitKeeper y la comunidad de Linux, estos últimos perdieron el acceso a la herramienta.
* **La solución:** Linus Torvalds, el creador de Linux, no quiso volver a métodos antiguos (parches manuales) y decidió crear su propio **DVCS** (Sistema de Control de Versiones Distribuido).
* **El resultado:** En abril de 2005, se lanzó la primera versión de **Git**.

**¿Por qué Git cambió el mundo del desarrollo?**

1. **Distribuido:** A diferencia de los sistemas centralizados, cada desarrollador tiene una copia completa del historial.
2. **Rendimiento:** Está optimizado para gestionar proyectos masivos (como el mismo kernel de Linux).
3. **Integridad:** Utiliza **hashing** (criptografía) para asegurar que el código y su historial no hayan sido alterados, lo cual es vital para la seguridad.
4. **Colaboración:** Permite que miles de personas trabajen en un mismo proyecto sin sobrescribirse los cambios.

**En conclusión:** Git fue la respuesta a un problema de escalabilidad. Hoy en día es el estándar de oro no solo por su eficiencia, sino por la seguridad que ofrece al verificar la integridad de los datos mediante hashes.
---

### Resumen: Conceptos de Control de Versiones

El control de versiones es la columna vertebral de la seguridad en el código fuente, ya que permite rastrear quién hizo qué cambios, cuándo los hizo y mantener un historial completo por si algo sale mal.

**¿Cómo funciona?**

* **Repositorio:** Es la "base de datos" central que guarda todo el historial del proyecto.
* **Working Copy (Copia de trabajo):** Es la copia local donde el desarrollador realiza cambios. Esta permite trabajar de forma aislada sin afectar al resto del equipo hasta que se decida "enviar" los cambios.
* **Commit:** Es la acción de guardar tus cambios en el repositorio, consolidando las mejoras en el historial.

**Diferencias fundamentales:**

* **Centralizado (como Subversion):** Hay un solo repositorio central. Cuando haces un cambio, todos lo ven de inmediato. Si el servidor central cae, el trabajo se detiene.
* **Distribuido (como Git o Mercurial):** Cada desarrollador tiene su propio repositorio completo en su computadora. Esto lo hace mucho más rápido, resistente ante errores y permite trabajar sin conexión, sincronizando los cambios (*push*) a un repositorio central solo cuando es necesario.

**En conclusión:** Aunque los sistemas distribuidos como Git tienen una curva de aprendizaje un poco más compleja, son el estándar de la industria hoy en día por su robustez y rendimiento. Para un ingeniero de DevSecOps, entender que el código "vive" en múltiples lugares (local y central) es vital para asegurar que la trazabilidad sea correcta en todo el pipeline.

---

### Resumen: VCS en la Nube (GitHub y GitLab)

El control de versiones en la nube ha transformado el desarrollo de software, permitiendo que equipos distribuidos colaboren en tiempo real. Las dos plataformas líderes mencionadas son **GitHub** y **GitLab**.

* **GitHub:**
* Es el servicio más antiguo y dominante del mercado.
* Su gran potencia actual reside en **GitHub Actions**, que permite crear flujos de trabajo (*workflows*) automatizados para CI/CD directamente en la plataforma (compilar, testear, desplegar contenedores, etc.).


* **GitLab:**
* Se promociona como una solución "todo en uno" (*all-in-one*).
* Su gran diferencia es que integra capacidades de DevOps de forma nativa (CI/CD, registro de contenedores, despliegue a Kubernetes).
* Utiliza **"Runners"** (agentes) para ejecutar los trabajos de forma paralela o secuencial, eliminando la necesidad de integraciones con terceros.



**En conclusión:**
Ambas plataformas ofrecen mucho más que solo almacenamiento de código; son motores de automatización. Mientras que GitHub es el gigante de la colaboración abierta, GitLab destaca por ofrecer un ecosistema de DevOps integrado desde el primer día. En DevSecOps, saber configurar los *Actions* de GitHub o los *Runners* de GitLab es una habilidad básica para asegurar que el código no solo se guarde, sino que se pruebe y despliegue de forma segura automáticamente.


---

### Resumen: Higiene de Credenciales y Secretos

La gestión de secretos (API keys, contraseñas, tokens) es uno de los pilares de la seguridad en pipelines de CI/CD. Los errores humanos en este ámbito son la causa de innumerables brechas de seguridad.

**Mejores Prácticas:**

* **Principio de menor privilegio:** Solo los procesos o usuarios estrictamente necesarios deben tener acceso a ciertas credenciales.
* **Rotación:** No mantengas secretos estáticos por siempre; cámbialos periódicamente.
* **Limpieza de artefactos:** Asegúrate de que los secretos no queden "pegados" en capas de imágenes de contenedores, logs de consola o binarios.
* **Variables de entorno:** Son una excelente práctica para evitar el *hardcoding* (escribir credenciales directamente en el código fuente). Sin embargo, **el resumen es claro:** usar variables de entorno ayuda, pero **no es una solución mágica**. Si el entorno se ve comprometido, las variables también lo estarán.

**La Solución Real:**

* El uso de un **Secrets Manager** (como HashiCorp Vault, AWS Secrets Manager o Azure Key Vault) es el estándar profesional. Estas herramientas no solo almacenan secretos de forma cifrada, sino que proporcionan mecanismos de auditoría, control de acceso y rotación automática que superan con creces el simple uso de variables de entorno.

**En conclusión:** La seguridad no es una configuración única, sino un proceso. Incluso con las mejores herramientas, la higiene de credenciales depende de una disciplina constante para evitar que los secretos se filtren en logs, repositorios o artefactos.

---

### Resumen: Git y el modelo de ramificación

Esta sección es fundamental para entender cómo Git gestiona el trabajo paralelo. A diferencia de otros sistemas que almacenan diferencias, Git utiliza **instantáneas (snapshots)** del contenido, lo que lo hace extremadamente eficiente.

**Conceptos clave:**

* **Ramificación (Branching):** Es la capacidad de crear líneas de trabajo independientes. Esto permite que los desarrolladores trabajen en nuevas funciones sin alterar la rama principal (`main`), evitando conflictos y permitiendo la experimentación.
* **Flujo de trabajo básico:**
1. `git clone`: Descargas una copia local del repositorio.
2. `git add`: Envías tus cambios a la "área de preparación" (*staging area*).
3. `git commit`: Guardas esos cambios en el historial local con una descripción.
4. `git push`: Subes tus cambios locales al repositorio remoto (`origin`).



**Por qué importa para DevSecOps:**

* El uso correcto de ramas (*branches*) permite integrar pruebas de seguridad antes de fusionar (*merge*) código nuevo a la rama principal.
* Entender que `origin` es el punto de referencia remoto te ayuda a evitar errores críticos al desplegar código, asegurándote de que estás subiendo cambios a la fuente correcta y no sobrescribiendo el trabajo de otros.

**En conclusión:** El modelo de ramas de Git es ligero y potente. Dominar estos comandos no solo es necesario para desarrollar, sino que es la base para construir pipelines donde el código se prueba y verifica de forma aislada antes de llegar a producción.


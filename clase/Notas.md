# Registro de Trabajo en Clase - Taller 4

## Fecha de la sesión

17 de marzo de 2026

---

# Integrantes presentes

- David Santiago Medina (davidmebu@unisabana.edu.co)  
- Santiago Navarro (santiagonacu@unisabana.edu.co)  
- Jacobo Pacheco (jacobopama@unisabana.edu.co)  
- Juan Diego Martínez (juandmaes@unisabana.edu.co)  

---

# Actividades realizadas en clase

Durante la sesión de clase el equipo analizó el caso base **RedExpress**, el cual describe una plataforma logística que gestiona el rastreo de paquetes mediante una aplicación móvil y una plataforma web. A partir de este caso se discutió cómo podría estructurarse la infraestructura tecnológica necesaria para soportar las operaciones del sistema.

Inicialmente se discutieron los componentes principales de la arquitectura, identificando los elementos que intervienen desde que un usuario realiza una solicitud hasta que el sistema procesa la información y responde. Se identificaron componentes clave como:

- Clientes (aplicación móvil y plataforma web)
- Balanceador de carga
- API Gateway
- Servicios centrales del sistema
- Servidores regionales
- Centros de distribución
- Base de datos principal
- Sistemas de monitoreo y alertas

El equipo decidió modelar una **arquitectura híbrida**, en la que parte del sistema se encuentra desplegado en la nube mientras que algunos componentes operativos se distribuyen regionalmente para mejorar el rendimiento y reducir la latencia en diferentes zonas geográficas.

También se discutió la necesidad de incluir componentes de **monitoreo y observabilidad**, con el fin de detectar fallos en el sistema y garantizar la disponibilidad de la plataforma.

### Decisiones de modelado tomadas

Durante el modelado se tomaron las siguientes decisiones:

- Utilizar un **Load Balancer** para distribuir el tráfico de los usuarios.
- Incorporar un **API Gateway** como punto de entrada para las solicitudes del sistema.
- Separar la lógica del sistema en **servicios centrales**, como:
  - procesamiento de rutas
  - rastreo de paquetes
  - notificaciones
- Incluir **servidores regionales** para mejorar el procesamiento logístico.
- Centralizar los datos en una **base de datos principal**.
- Implementar un sistema de **monitoreo y alertas** para supervisar el estado del sistema.

### Herramientas utilizadas

Para el desarrollo del modelo preliminar se utilizaron las siguientes herramientas y métodos de trabajo:

- Discusión y análisis en grupo para definir los componentes de la arquitectura.
- Un primer **boceto conceptual generado con apoyo de inteligencia artificial**, el cual sirvió como punto de partida para visualizar una posible arquitectura inicial.
- A partir de este primer modelo, el equipo realizó **ajustes, modificaciones y ampliaciones basadas en el análisis propio del caso**.
- Modelado y refinamiento del diagrama utilizando **Eraser.io**, donde se incorporaron los componentes finales y las relaciones entre los diferentes elementos de la infraestructura.

Este proceso permitió construir un diagrama más completo y ajustado a las necesidades del sistema descrito en el caso.

### Avance alcanzado durante la sesión

Durante la sesión se logró:

- Identificar los componentes principales de la infraestructura
- Diseñar el **boceto preliminar del mapa de infraestructura**
- Identificar posibles **zonas sensibles de carga y disponibilidad**
- Definir la estructura general del sistema

---

# Boceto inicial del modelo

El equipo realizó un primer modelo de la arquitectura de infraestructura utilizando **Eraser.io**, en el cual se representan los principales componentes del sistema RedExpress y sus relaciones.

El diagrama incluye:

- Clientes (Web y Mobile)
- Servicios en la nube
- Servicios centrales del sistema
- Servidores regionales
- Centros de distribución
- Base de datos
- Sistemas de monitoreo

---

# Tareas definidas para complementar el taller

Para completar la entrega final del taller, el equipo definió las siguientes responsabilidades:

| Tarea | Responsable | Fecha estimada |
|------|------|------|
| Modelado final del diagrama de infraestructura en Eraser.io | Santiago Medina y Santiago Navarro | 18/03 |
| Redacción del informe de diagnóstico técnico | Juan Diego Martínez | 19/03 |
| Investigación sobre buenas prácticas de arquitectura de infraestructura | Jacobo Pacheco | 19/03 |

---

Este documento resume el trabajo colaborativo realizado durante la sesión del **Taller 4** en el curso **Arquitectura Empresarial (AREM)** de la **Universidad de La Sabana**.

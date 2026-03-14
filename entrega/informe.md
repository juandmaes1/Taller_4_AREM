# Análisis de Zonas Sensibles – Infraestructura RedExpress

# Integrantes del equipo

- David Santiago Medina (davidmebu@unisabana.edu.co)
- Santiago Navarro (santiagonacu@unisabana.edu.co)
- Jacobo Pacheco (jacobopama@unisabana.edu.co)
- Juan Diego Martínez (juandmaes@unisabana.edu.co)

## Identificación de zonas sensibles de carga, disponibilidad, monitoreo y redundancia

A partir del mapa de infraestructura modelado para RedExpress, se identificaron diferentes zonas críticas dentro del sistema que podrían representar riesgos en términos de rendimiento, disponibilidad y resiliencia. Estas zonas se clasifican según su impacto en la carga del sistema, la disponibilidad del servicio, el monitoreo de la plataforma y los mecanismos de redundancia.

---

# 1. Zona sensible de carga

### Componentes afectados

- Load Balancer  
- API Gateway  
- Package Tracking Service  
- Primary Database  

### Análisis

Estos componentes reciben la mayor cantidad de solicitudes del sistema, ya que todos los usuarios de la **Web Platform** y la **Mobile App** deben pasar por estas capas para realizar operaciones como consultar el estado de un paquete o registrar un envío.

Durante periodos de alta demanda (por ejemplo **campañas promocionales o temporadas como Navidad**), el servicio de **Package Tracking** puede recibir un gran volumen de consultas simultáneas.

### Riesgos identificados

- Saturación del API Gateway  
- Sobrecarga del servicio de rastreo de paquetes  
- Alto número de consultas concurrentes hacia la base de datos

### Posibles mejoras

- Implementar **Auto Scaling** en los servicios en la nube
- Incorporar **sistemas de caché (por ejemplo Redis)** para consultas frecuentes
- Escalar horizontalmente los servicios críticos

---

# 2. Zona sensible de disponibilidad

### Componentes afectados

- API Gateway  
- Core Services  
- Primary Database  

### Análisis

Estos componentes son esenciales para el funcionamiento de toda la plataforma. Si alguno de ellos deja de funcionar, los usuarios no podrán acceder a los servicios principales del sistema.

Por ejemplo:

- Si el **API Gateway** falla, las solicitudes de los usuarios no podrán llegar a los servicios internos.
- Si la **Primary Database** falla, el sistema no podrá acceder a la información de paquetes, rutas o estados.

### Riesgos identificados

- Puntos únicos de falla en componentes críticos
- Interrupción total del servicio en caso de caída

### Posibles mejoras

- Implementar **múltiples instancias del API Gateway**
- Utilizar **bases de datos con alta disponibilidad**
- Implementar mecanismos de **failover automático**

---

# 3. Zona sensible de monitoreo

### Componentes afectados

- CloudWatch  
- Alerting  
- Alerting System  

### Análisis

El sistema de monitoreo permite detectar problemas de rendimiento o fallos en la infraestructura. En la arquitectura propuesta se incluyen herramientas de monitoreo y alertas, lo cual es fundamental para mantener la estabilidad de la plataforma.

Sin embargo, si el monitoreo no cubre todos los servicios o no mide métricas relevantes, podrían presentarse problemas que no se detecten a tiempo.

### Riesgos identificados

- Falta de visibilidad sobre fallos en microservicios
- Dificultad para detectar degradaciones de rendimiento
- Retrasos en la detección de incidentes

### Posibles mejoras

- Implementar **dashboards de monitoreo de métricas**
- Analizar **latencia y tiempos de respuesta**
- Implementar **trazabilidad distribuida entre servicios**

---

# 4. Zona sensible de redundancia

### Componentes afectados

- Primary Database  
- Regional Servers  
- Core Services  

### Análisis

La redundancia permite que el sistema continúe funcionando incluso si alguno de sus componentes falla. En el diagrama se observa una **Primary Database centralizada**, lo que podría representar un riesgo si no existe replicación o respaldo.

Los **Regional Servers** ayudan a distribuir la carga geográfica, pero si uno de ellos falla podría afectar el procesamiento de rutas o la operación logística en una región específica.

### Riesgos identificados

- Dependencia de una única base de datos
- Posible interrupción de servicios regionales
- Falta de redundancia en algunos servicios críticos

### Posibles mejoras

- Implementar **replicación de bases de datos**
- Desplegar servicios en **múltiples regiones**
- Implementar **failover automático**
- Utilizar arquitecturas **multi-zona o multi-región**

---

# Conclusión

El análisis de la infraestructura de RedExpress permite identificar varias zonas críticas relacionadas con la carga del sistema, la disponibilidad de los servicios, los mecanismos de monitoreo y la redundancia de los componentes. Los puntos más sensibles se encuentran en la capa de acceso (Load Balancer y API Gateway), los servicios centrales de procesamiento y la base de datos principal.

Para mejorar la resiliencia y escalabilidad del sistema se recomienda implementar estrategias como **autoescalamiento de servicios, replicación de bases de datos, sistemas de caché y herramientas avanzadas de monitoreo**, lo cual permitiría garantizar una mayor disponibilidad y rendimiento de la plataforma.

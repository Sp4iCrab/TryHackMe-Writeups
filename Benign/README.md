# TryHackMe: Benign - Blue Team Write-up

**Plataforma:** TryHackMe  
**Categoría:** Blue Team / SOC / Análisis de Logs  
**Dificultad:** Media 
**Enfoque:** Investigación de Ejecución de Procesos con Splunk  

---

## Visión General

Este repositorio contiene la documentación y resolución técnica de la máquina **Benign** de TryHackMe, el escenario plantea que un cliente reportó una potencial ejecución de proceso sospechosa en un host del departamento de HR, confirmada por el uso de herramientas de recolección de información de red y tareas programadas, con acceso únicamente a logs de ejecución de procesos (EventID 4688), el objetivo es usar **Splunk** para reconstruir la cadena de ataque, qué pasó, cómo y quién lo hizo.

🔗 **Puedes ver el proceso completo aquí:**  
[Ver documento con imágenes](Benign.md)

---

## Herramientas Utilizadas

* **Splunk:** Consulta y filtrado de logs de Windows (`index=win_eventlogs`, EventID 4688) mediante campos como `Username`, `CommandLine` y `HostName`, incluyendo el uso del comando `rare` para detectar comandos poco frecuentes.
* **Análisis de LOLBins:** Identificación de binarios legítimos de Windows (Living off the Land Binaries) reutilizados con fines maliciosos.

---

## Resumen del Análisis

Incluye:
- Conteo de logs disponibles desde marzo de 2022 mediante filtrado por rango de fechas en Splunk.
- Detección de una cuenta de usuario impostora suplantando a un empleado legítimo mediante análisis del campo `Username`.
- Identificación del usuario de HR que ejecutó una scheduled task sospechosa vía `schtasks.exe`.
- Uso del comando `rare` sobre `CommandLine` para aislar eventos poco comunes y detectar el uso de un LOLBIN.
- Identificación del usuario, quien utilizó un LOLBIN para descargar un payload desde un servicio de terceros.
- Determinación de la fecha de ejecución del binario y del archivo dejado en el host durante la fase de post-explotación.
- Obtención de la flag final accediendo a la URL del servidor C2, donde se alojaba un archivo de texto con la flag.
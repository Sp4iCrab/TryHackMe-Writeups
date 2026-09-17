# TryHackMe: ItsyBitsy - Blue Team Write-up

**Plataforma:** TryHackMe  
**Categoría:** Blue Team / SOC / Análisis de Logs  
**Dificultad:** Fácil  
**Enfoque:** Investigación de Alertas y Análisis de Logs en Elastic

---

## Visión General

Este repositorio contiene la documentación y resolución técnica de la máquina **ItsyBitsy** de TryHackMe, el objetivo principal de este laboratorio es asumir el rol de un analista de SOC investigando una alerta sobre una posible comunicación C2, analizando logs en la plataforma Elastic para identificar al host comprometido, la herramienta legítima abusada por el atacante y el servidor C2 utilizado.

🔗 **Puedes ver el proceso completo aquí:**  
[Ver documento con imágenes](ItsyBitsy.md)

---

## Herramientas Utilizadas

* **Elastic (Elastik):** Plataforma de análisis y consulta de logs (Kibana) utilizada para filtrar por rango de tiempo, `source_Ip` y `user_agents`.
* **Análisis de campos de logs:** Identificación de patrones anómalos mediante comparación de user agents y actividad por IP.

---

## Resumen del Análisis

Incluye:
- Conteo de eventos totales en el rango de tiempo de marzo 2022 mediante filtro de fechas.
- Identificación de la IP sospechosa comparando el campo `user_agents`, descartando tráfico legítimo (Mozilla) y detectando el uso de **Bitsadmin**, un binario legítimo de Windows utilizado de forma anómala.
- Identificación de **Bitsadmin** como el binario "living off the land" empleado por el atacante para descargar archivos desde el servidor C2.
- Descubrimiento de **Pastebin** como el servicio de intercambio de archivos usado como servidor C2.
- Obtención de la URL completa del C2 (`pastebin.com/yTg0Ah6a`) y del archivo accedido desde este.
- Extracción del contenido del archivo `secret.txt`, el cual contiene la flag final del desafío.
# TryHackMe: Shadow Trace - Blue Team Write-up

**Plataforma:** TryHackMe  
**Categoría:** Blue Team / Malware Analysis  
**Dificultad:** Fácil  
**Enfoque:** Análisis Estático y Análisis de Alertas  

---

## Visión General

Este repositorio contiene la documentación y resolución técnica de la máquina **Shadow Trace** de TryHackMe, el objetivo principal de este laboratorio de *Blue Team* es analizar un binario sospechoso mediante técnicas de análisis estático y decodificación de artefactos para identificar Indicadores de Compromiso (IOCs) y responder a incidentes de seguridad.

🔗 **Puedes ver el proceso completo aquí:**  
[Ver documento con imagenes](TryHackMe-ShadowTrace.md) 


---

## Herramientas Utilizadas

* **Pestudio:** Inspección de la estructura PE, secciones de *Imports*, *Libraries* y metadatos del ejecutable de Windows.
* **Strings & Findstr:** Extracción directa de cadenas de texto y subdominios desde la consola de comandos.
* **CyberChef:** Desofuscación de datos mediante recetas `From Base64` y `From Charcode`.
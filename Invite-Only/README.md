# TryHackMe: Invite Only - Threat Intelligence Write-up

**Plataforma:** TryHackMe  
**Categoría:** Blue Team / Threat Intelligence  
**Dificultad:** Fácil  
**Enfoque:** Análisis de IOCs, Threat Intelligence y Reportes de Malware  

---

## Visión General

Este repositorio contiene la documentación y resolución técnica de la máquina **Invite Only** de TryHackMe, el objetivo principal de este laboratorio es asumir el rol de un analista de Nivel 1 (L1) y aplicar técnicas de inteligencia de amenazas para investigar una IP y un hash SHA256 marcados como maliciosos, utilizando tanto una herramienta offline ("TryDetectThis2.0") como VirusTotal, hasta llegar al reporte original de la campaña de malware asociada.

🔗 **Puedes ver el proceso completo aquí:**  
[Ver documento con imágenes](Invite-Only.md)

---

## Artefactos del Desafío

* **Flagged IP:** `101[.]99[.]76[.]120`
* **Flagged SHA256 hash:** `5d0509f68a9b7c415a726be75a078180e3f02e59866f193b0a99eee8e39c874f`

---

## Herramientas Utilizadas

* **TryDetectThis2.0:** Herramienta offline tipo VirusTotal proporcionada por el desafío para la inteligencia de amenazas inicial.
* **VirusTotal:** Consulta de reportes de hashes e IPs, relaciones (execution parents, dropped files, contacted IPs/domains) y sección de comunidad.
* **Google / OSINT:** Búsqueda del reporte original donde se documentaron los IOCs de la campaña.

---

## Resumen del Análisis

Incluye:
- Identificación del archivo y tipo asociado al hash marcado (`syshelpers.exe`, WIN32 EXE).
- Análisis de relaciones (execution parents, archivos dejados/empaquetados) mediante TryDetectThis2.0.
- Uso de VirusTotal al no encontrar resultados sobre la IP en la herramienta offline.
- Identificación de la familia de malware que interconecta los archivos comunicados por la IP.
- Localización del reporte original de la campaña.
- Identificación de la herramienta de robo de cookies (**ChromeKatz**), la técnica de phishing (**ClickFix**) y la plataforma usada para redireccionar a servidores maliciosos (**Discord**).
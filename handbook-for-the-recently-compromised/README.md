Handbook for the Recently Compromised — TryHackMe
https://tryhackme.com/room/handbookfortherecentlycompromised

metadatos: MITRE ATT&CK, Terminal, cyberchef, evtx_dump. Enfoque: Windows Forensics / Log Analysis (.evtx) Herramientas: evtx_dump, CyberChef, MITRE ATT&CK, Terminal

mision: Una estación de trabajo Windows ha sido marcada por actividad inusual. Examine sus registros de eventos, siga la secuencia de acciones sospechosas y descubra cómo se vio comprometido el host. Se le han proporcionado registros de eventos de Windows recopilados de una estación de trabajo bajo investigación. Revise la actividad registrada, identifique los eventos asociados con la intrusión y cree una línea de tiempo que explique lo que hizo el atacante en el host.

prueba aportada: Registros de eventos de Windows (.evtx)

Objetivos:

Identificar la evidencia más temprana de actividad sospechosa.
Conecte eventos relacionados y reconstruya la línea de tiempo del ataque.
Vincular las acciones observadas con las relevantes. MITRE ATT&CK.
Establecer lo que logró el atacante en la estación de trabajo.
NOTA DEL ANALISTA: Comience con las marcas de tiempo y luego compare las cuentas, los procesos y los comandos involucrados. Un acontecimiento aislado puede parecer normal; los eventos a su alrededor pueden contar una historia diferente.

pregunta finales:

Una utilidad confiable de Windows descargó un script de segunda etapa en el host. El comando que llamó a la utilidad ocultó su nombre con un comodín. ¿Cuál es el nombre completo del ejecutable de la utilidad?
¿De qué URL completa recuperó la utilidad el script de la segunda etapa?
¿Qué subtécnica de MITRE ATT&CK describe el abuso del host de secuencias de comandos de Windows que ejecutó el archivo adjunto inicial??
¿Qué subtécnica MITRE ATT&CK describe el mecanismo de persistencia que configuró el intruso??
What is the flag?
pasos: 1 y 2. usando la herramienta "evtx_dump" ejecuté y abrí el archivo "Microsoft-Windows- Sysmon%4Operational.evtx" y "PowerShell-Operational.evtx" donde conseguí el nombre oculto de la utilidad descargado por windows y el link de donde se descargó.

3.con MITRE ATT&CK supe la subtecnica "System Binary Proxy Execution" ya que abarca el abuso de binarios firmados y legítimos del sistema operativo para ejecutar código/scripts de forma proxy. La sub-técnica "respuesta pregunta 3" corresponde a Mshta (o el abuso de utilidades del sistema/proxy execution en el flujo de ejecución inicial observado en el reto).

4.Corresponde a Scheduled Task/Job: Scheduled Task: es una función del sistema operativo (especialmente en Windows) que ejecuta programas, comandos o scripts de forma automática a una hora específica, de manera recurrente o al ocurrir un evento.

Al localizar la cadena codificada correspondiente a la flag durante el análisis, la procesé en CyberChef aplicando la operación From Base64 para decodificarla y obtener el valor final.

# Mr. Phisher challenge — TryHackMe
https://tryhackme.com/room/mrphisher

**Categoría:** Malware Analysis / Phishing / Reverse Engineering básico
**Herramientas:** LibreOffice / editor de macros VBA, Python, Terminal

Escenario:
"Recibí un correo electrónico sospechoso con un archivo adjunto de aspecto muy extraño. Sigue pidiéndome que "habilite macros". ¿Cuáles son esos?"

pregunta del challenge:
"Descubra la bandera en el archivo adjunto del correo electrónico!"


pasos:
1)al abrir la maquina virtual nos coneseguimos 2 archivos, un documento word y un ZIP. 
Al abrir el word nos sale este mensaje:

<img width="690" height="273" alt="image" src="https://github.com/user-attachments/assets/ec60ac6b-b6e1-4985-bc4a-bea424dc6d5b" />

---

y esta imagen:

<img width="722" height="557" alt="image" src="https://github.com/user-attachments/assets/4c29b67d-c7f0-4133-933a-697da34675db" />

---

2)fuí a tools/macros/edit macros
para luego conseguirme este codigo en modulos:

<img width="1221" height="190" alt="image" src="https://github.com/user-attachments/assets/3e8951c9-dcdb-4f91-bb5a-a4a576318057" />

---

3)me guié de otra pagina para pasar el codigo vb a python:
<img width="1629" height="1115" alt="image" src="https://github.com/user-attachments/assets/7d459737-7b9a-445c-bb67-ac0fb090720b" />

---

resultado:
def format_string() -> str:
    a = [102, 109, 99, 100, 127, 100, 53, 62, 105, 57, 61, 106, 62, 62, 55, 110,
         113, 114, 118, 39, 36, 118, 47, 35, 32, 125, 34, 46, 46, 124, 43, 124,
         25, 71, 26, 71, 21, 88]
    b = ""
    # VBA loop variable "1" is invalid; the loop logic uses "i", so it is translated as the index.
    for i in range(len(a)):
        b += chr(a[i] ^ i)
    return b


def main() -> None:
    print(format_string())


if __name__ == "__main__":
    main()
    
---

4)por ultimo fuí a la terminal a crear un touch en .py y coloqué el codigo, al ejecutarlo obtuve la bandera.


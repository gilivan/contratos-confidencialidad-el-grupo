# Generador de Acuerdos de Confidencialidad — El Grupo

Aplicación web para generar automáticamente acuerdos de confidencialidad (NDA) en formato Word, con los datos de **PÉREZ Y VILLA S.A.S** o **FIERA S.A.S** como empresa contratante.

## Funcionalidades

- Selección de razón social contratante (Pérez y Villa S.A.S o Fiera S.A.S)
- Formulario para ingresar los datos del contratista
- Generación automática del documento `.docx` listo para firmar
- Fecha de firma escrita en letras (español colombiano)

## Instalación local

### Requisitos

- Python 3.10 o superior

### Pasos

```bash
# 1. Clonar el repositorio
git clone https://github.com/TU_USUARIO/contratos-el-grupo.git
cd contratos-el-grupo

# 2. Crear entorno virtual (recomendado)
python -m venv venv
source venv/bin/activate   # En Windows: venv\Scripts\activate

# 3. Instalar dependencias
pip install -r requirements.txt

# 4. Ejecutar la app
python app.py
```

Abrir en el navegador: [http://localhost:8000](http://localhost:8000)

## Despliegue en Render.com

1. Crear cuenta en [render.com](https://render.com) (plan gratuito disponible)
2. Conectar tu repositorio de GitHub
3. Seleccionar **"New Web Service"**
4. Render detectará automáticamente el `render.yaml` y configurará todo
5. Hacer clic en **"Deploy"**

## Estructura del proyecto

```
contratos-el-grupo/
├── app.py                          # Backend FastAPI
├── requirements.txt                # Dependencias Python
├── render.yaml                     # Configuración Render.com
├── .gitignore
├── README.md
├── doc_templates/
│   └── plantilla_acuerdo_confidencialidad.docx   # Plantilla Word
└── static/
    └── index.html                  # Formulario web
```

## Variables de la plantilla

| Variable en el .docx | Origen |
|---|---|
| `{NOMBRE EMPRESA CONTRATANTE}` | Pre-configurado según empresa seleccionada |
| `{NIT EMPRESA CONTRATANTE}` | Pre-configurado según empresa seleccionada |
| `{NOMBRE EMPRESA CONTRATISTA}` | Ingresado por el usuario |
| `{NIT EMPRESA CONTRATISTA}` | Ingresado por el usuario |
| `{NOMBRE REPRESENTANTE LEGAL CONTRATISTA}` | Ingresado por el usuario |
| `{CEDULA REPRESTANTE LEGAL EMPRESA CONTRATISTA}` | Ingresado por el usuario |
| `{DIRECCIÓN EMPRESA CONTRATISTA}` | Ingresado por el usuario |
| `{TELEFONO REPRESENTANTE LEGAL CONTRATISTA}` | Ingresado por el usuario |
| `{DIRECCIÓN REPRESENTANTE LEGAL CONTRATISTA}` | Ingresado por el usuario |
| `{CORREO ELECTRÓNICO REPRESENTANTE LEGAL CONTRATISTA}` | Ingresado por el usuario |
| `{FECHA DE FIRMA}` | Ingresado por el usuario (se escribe en letras) |

## Actualizar datos de El Grupo

Para modificar los datos de las empresas contratantes o del contacto, editar en `app.py`:

```python
EMPRESAS_CONTRATANTE = {
    "perez_villa": {
        "nombre": "PÉREZ Y VILLA S.A.S",
        "nit": "890.926.395-8",
    },
    "fiera": {
        "nombre": "FIERA S.A.S.",
        "nit": "900.072.392-5",
    }
}
```

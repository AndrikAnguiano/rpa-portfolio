# Descarga automática de Constancias de Situación Fiscal (CSF)

**Tecnología:** Power Automate

## Problema
Los contadores descargaban manualmente, cada mes, la Constancia de Situación Fiscal de cada cliente desde el portal del SAT, y además creaban a mano las carpetas por año para organizarlas. Es una tarea repetitiva, lenta y propensa a errores cuando se manejan muchos clientes.

## Solución
Flujo que recorre una carpeta de clientes, accede al portal del SAT con la e.firma de cada cliente, descarga su constancia y la guarda organizada automáticamente por año, sin crear carpetas manualmente.

## Cómo funciona
1. Lee la carpeta principal de clientes, que contiene una carpeta por cliente con sus archivos .cer y .key
2. Para cada cliente, accede al portal del SAT con su e.firma
3. Descarga la Constancia de Situación Fiscal
4. Dentro de la carpeta del cliente, crea (si no existe) la carpeta **CSF** y dentro una carpeta con el **año actual**
5. Guarda la constancia con el nombre **Cliente-Mes**

## Estructura de carpetas resultante
Clientes/
├── Cliente A/
│   ├── certificado.cer
│   ├── llave.key
│   └── CSF/
│       ├── 2025/
│       │   ├── Cliente A-Noviembre.pdf
│       │   └── Cliente A-Diciembre.pdf
│       └── 2026/
│           └── Cliente A-Enero.pdf
└── Cliente B/
    └── ...

Cada mes y cada año se organizan solos: el flujo crea las carpetas que falten y nombra los archivos automáticamente.

## Manejo de errores
- Reintentos automáticos ante fallas de acceso o descarga
- Si un cliente falla, el flujo registra el error y continúa con los demás
- [Notificación / reporte de los clientes con error]

## Resultado
- Presentado a contadores como solución para su operación mensual
- Elimina la descarga manual y la creación de carpetas mes con mes y año con año
- [Tiempo ahorrado: de 10 minutos por cliente a 1 minuto]

## Capturas
![Flujo en Power Automate](images/flujo.png)

*Los archivos de e.firma y los datos de clientes no se incluyen en este repositorio por seguridad.*

# JAC Conveyor Studio

Configurador de bandas transportadoras con visor 3D y generación paramétrica de piezas y ensambles en SOLIDWORKS. Versión publicada: **5.24.0.0**.

## Ejecutar en otra PC

1. Descarga [JAC-CONVEYOR-STUDIO-5.24.0.0-Windows.zip](JAC-CONVEYOR-STUDIO-5.24.0.0-Windows.zip). En la página del archivo utiliza **Download raw**.
2. Extrae **todo** el ZIP en una carpeta local.
3. Abre la carpeta extraída y ejecuta `INSTALAR.cmd`. Instala para tu usuario y crea accesos directos, sin requerir administrador. También puedes abrir `PerfilBandas.exe` directamente desde esa carpeta.
4. Abre **JAC Conveyor Studio** desde el acceso directo.

El paquete incluye el ejecutable compilado, las dos DLL de interoperabilidad, catálogo de bandas, catálogos de chumaceras y sprockets con sus modelos y mallas, recursos del visor, modelos de soportes, manuales e instalador. Conserva la estructura de carpetas. Para actualizar, guarda tus proyectos y cierra la aplicación antes de ejecutar el instalador; conserva los catálogos existentes.

## Requisitos

- Windows 10/11 de 64 bits; .NET Framework 4.8 recomendado.
- El configurador y visor funcionan sin abrir SOLIDWORKS. La GPU se utiliza si el controlador OpenGL lo permite; existe renderizado CPU como alternativa.
- Para generar archivos `.SLDPRT` y `.SLDASM` necesitas **SOLIDWORKS instalado y con licencia**. El código utiliza la API de SOLIDWORKS 2026; no se ha certificado con versiones anteriores. Configura sus plantillas predeterminadas de pieza y ensamble. Las DLL incluidas no sustituyen la instalación de SOLIDWORKS.

## Código fuente y compilación

Descarga y extrae [JAC-CONVEYOR-STUDIO-5.24.0.0-Fuentes.zip](JAC-CONVEYOR-STUDIO-5.24.0.0-Fuentes.zip). Incluye `src`, `assets`, `lib`, `macros`, `tools`, documentación, catálogos y ejecutables, con sus carpetas originales. No requiere Visual Studio para usar el script de compilación en Windows:

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\build.ps1
```

El script compila las fuentes C# en `outputs\PerfilBandas.exe`, copia las DLL y genera el acceso de la raíz. Ejecuta `ABRIR_JAC_BANDAS.cmd` o `PerfilBandas.exe`. Para crear otro paquete instalable:

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\tools\Package-JAC.ps1
```

Las carpetas de piezas se resuelven desde la ubicación de la aplicación o del proyecto fuente; esta publicación no depende de la unidad ni de las rutas del equipo original.

## Verificación de la publicación

Se compiló esta versión desde las fuentes incluidas, se comprobó la instalación en una carpeta independiente y se verificaron sus recursos y catálogos. Consulta `SHA256SUMS.txt` para comprobar ambos ZIP. La generación CAD requiere una prueba en la instalación de SOLIDWORKS de la PC destino.

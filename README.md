# Silva-Portfolio

Este es un portafolio creado por mí en Svelte junto con Vite. Principalmente está orientado a no directamente mostrar una lista de todas las cosas si no que manejarlo como un sistema de menú's. 

## Instalación

Este proyecto maneja sus paquetes por medio de pnpm, si no lo posees y tienes node.js tienes que ejecutar este comando en PowerShell con permisos de administrador

```bash
corepack enable
```
Además está hecho con el empaquetador Vite, por lo que una vez activado pnpm, tienes que ejecutar el siguiente comando en la carpeta del proyecto para instalar las dependencias:
```bash
pnpm install
```
Una vez instalado, para iniciar un servidor de desarrollo:
```bash
pnpm run dev
```
O para construir una versión de producción
```bash
pnpm run build
```
## Aspectos a destacar
Svelte utiliza estilos dentro de cada archivo en el que se especifica el lenguaje, debido a que compila todo como un solo JavaScript (en caso de usar SPA), entonces solo se genera un solo JS y un solo CSS al construirse.

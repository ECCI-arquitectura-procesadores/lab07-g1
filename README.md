[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19661057&assignment_repo_type=AssignmentRepo)
# lab07 - Procesador

## Integrantes
hollmal
mario alexis buitrago
## Documentación
implementa un System-on-Chip (SoC) completo basado en el procesador PicoRV32, integrando hardware en Verilog y firmware en C, dirigido a FPGA. A continuación, se explica cómo está estructurado y se desarrolla este proyecto aclarndo que tuvimos incovenientes para poder hacer funcionar el codigo por problemas  de licencia lo cual no nos permitio ver toda la implementacion.

 se requirio SoC en este proyecto y se compone por los siguientes bloques funcionales:

PicoRV32: Núcleo RISC-V de 32 bits, escrito en Verilog.
Memoria ROM (progmem.v): Contiene el firmware embebido que el procesador ejecutará al arrancar.
Memoria RAM: Para almacenamiento temporal de datos.
UART: Canal de comunicación serie con el PC.
GPIO (LEDs): Usados como salida visual simple del estado o acciones del firmware.

La estrutura que abarca tanto el diseño de hardware como la compilación de firmware y la integración final en la FPGA.

El código fuente del firmware está escrito en C para lo cual fue requerido el simulador de icaros, y es compilador utilizando el toolchain riscv32-unknown-elf-gcc. Este paso genera un archivo .bin que contiene el código máquina que la CPU ejecutará.

Con el firmware ya convertido en un módulo Verilog (progmem.v), se ejecuta el flujo de síntesis usando la herramienta Intel Quartus. Este proceso toma todos los archivos Verilog (CPU, memoria, UART, etc.) y genera el bitstream necesario para programar la FPGA.
Todo el flujo anterior, genera memoria ROM en Verilog, síntesis y empaquetado del bitstream— está automatizado mediante un archivo Makefile incluido en el repositorio. Esto permite:
Compilar firmware con un solo comando (make).
Ejecutar todo el flujo de hardware (make build TARGET=max10).
Evitar el uso manual del entorno gráfico de Quartus.


## Evidencias
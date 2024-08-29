
# Conceptos de Sistemas Operativos

## 1. Tipos de Kernel y sus diferencias

### Kernel Monolítico
Tipo de kernel donde todos los servicios del sistema operativo, como la gestión de procesos, memoria, dispositivos, etc., se ejecutan en modo kernel. Esto significa que todo el código del kernel opera en el mismo espacio de direcciones. Aunque este enfoque puede proporcionar un rendimiento más alto debido a la menor necesidad de cambios de contexto, también significa que cualquier error en un módulo del kernel puede comprometer la estabilidad de todo el sistema.

### Microkernel
 Minimiza el número de funciones que se ejecutan en modo kernel. Solo se incluyen las funcionalidades básicas, como la gestión de la comunicación entre procesos y la gestión básica de memoria. Otros servicios como el manejo de archivos, el manejo de dispositivos, y los sistemas de red se ejecutan en modo de usuario, como procesos separados. Aunque los microkernels pueden ofrecer mejor modularidad y seguridad, pueden ser menos eficientes debido a la sobrecarga de la comunicación entre procesos.

### Kernel Híbrido
 Combina elementos de los kernels monolíticos y microkernels. Mantiene un núcleo monolítico con algunas funciones del sistema operativo, pero también permite que otros servicios se ejecuten en modo de usuario, como en un microkernel. Esto intenta ofrecer un equilibrio entre la eficiencia y la modularidad.

### Nanokernel
 Es una versión extremadamente minimalista de un kernel. Sus funcionalidades son aún más reducidas que las de un microkernel, enfocándose únicamente en la gestión más básica del hardware y delegando casi todas las demás funciones a software de nivel superior.

### Exokernel
Este se encarga únicamente de proporcionar los mecanismos básicos para la multiplexación del hardware, dejando las decisiones políticas a nivel de la aplicación. Esto permite a las aplicaciones tener más control sobre el hardware, a costa de una mayor complejidad en el desarrollo de aplicaciones.

## 2. User Mode vs Kernel Mode

Los sistemas operativos modernos operan en dos modos diferentes:

- **Modo Usuario (User Mode):** En este modo, el código que se ejecuta tiene acceso limitado a la memoria y no puede ejecutar operaciones que interfieran directamente con el hardware. La mayoría de las aplicaciones y procesos de usuario funcionan en este modo, lo que ayuda a proteger el sistema de posibles fallos en las aplicaciones.

- **Modo Kernel (Kernel Mode):** Permite que el código se ejecute con acceso completo al hardware y a toda la memoria del sistema. El código que se ejecuta en modo kernel puede realizar operaciones críticas como la gestión de dispositivos, la planificación de procesos y la gestión de la memoria. Sin embargo, debido a que tiene acceso total, los errores en este modo pueden ser catastróficos para el sistema.

La principal diferencia entre ambos modos es el nivel de acceso a los recursos del sistema. El modo kernel tiene privilegios elevados, mientras que el modo usuario tiene privilegios restringidos.

## 3. Interrupciones vs Traps

### Interrupciones
 Es una señal enviada al procesador por un dispositivo externo o una condición interna que requiere la atención inmediata del sistema operativo. Las interrupciones pueden ser de hardware (como una solicitud de entrada/salida de un dispositivo) o de software (como una petición del sistema operativo para realizar una acción específica). El sistema operativo responde a las interrupciones pausando la tarea actual y ejecutando un manejador de interrupciones para atender la situación.

### Traps
Instrucción especial en el código que genera una interrupción software intencionada. Las traps son utilizadas principalmente para cambiar del modo usuario al modo kernel, permitiendo que un programa de usuario solicite servicios del sistema operativo, como operaciones de E/S o gestión de memoria. Las traps también se utilizan para manejar excepciones, como errores de división por cero o violaciones de acceso a la memoria.

### Diferencias clave
- Las **interrupciones** son señales externas al flujo del programa que pueden ser generadas por dispositivos de hardware o por el propio sistema operativo para manejar eventos asíncronos.
- Los **traps** son generados intencionalmente por el código en ejecución para solicitar un servicio del sistema operativo o para manejar condiciones excepcionales.
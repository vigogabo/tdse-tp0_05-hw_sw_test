Example: tdse-tp0_05-hw_sw_test

 Description:
 Bare Metal - Event-Triggered Systems (ETS)
 App - retarget_printf_to_Console
 Project for STM32 Project (STM32CubeIDE Version: 1.7.0)

  SystemCoreClock     => 64MHz (15.625nS)
  SysTick Rate Hertz  => 1000 ticks per second (1mS)

  app.c (app.h)
   Endless loops, which execute tasks with fixed computing time. This 
   sequential execution is only deviated from when an interrupt event occurs.

  task_a.c (task_a.h) 
   Blocking Code

  task_b.c (task_b.h)
   Non-Blocking Code

  task_c.c (task_c.h)
   Update by Time Code

  logger.h (logger.c)
   Utilities for Retarget "printf" to Console

  dwt.h
   Utilities for Mesure "clock cycle" and "execution time" of code
  
  Special connection requirements:
   There are no special connection requirements for this example.

Build procedures:
Visit the Getting started with STM32: STM32 step-by-step at 
"https://wiki.st.com/stm32mcu/wiki/STM32StepByStep:Getting_started_with_STM32_:_STM32_step_by_step"
to get started building STM32 Projects.

15:28:20 **** Incremental Build of configuration Debug for project tdse-tp0_05-hw_sw_test ****
make -j4 all 
arm-none-eabi-size  tdse-tp0_05-hw_sw_test.elf 
   text	   data	    bss	    dec	    hex	filename
  14172	    180	   2244	  16596	   40d4	tdse-tp0_05-hw_sw_test.elf
Finished building: default.size.stdout
 

15:28:21 Build Finished. 0 errors, 0 warnings. (took 664ms)

Descripción del Código:
SystemClock_Config: Configura el reloj del sistema.
check_button: Lee el estado del botón conectado al pin PA0. Si el botón está presionado y ha pasado el tiempo de debounce (50 ms), se incrementa el contador de presiones de botón.
Debounce Software: Se implementa un mecanismo de debounce para evitar registrar múltiples presiones debido al rebote del botón.
Principios del Código No Bloqueante:
Manejo de Entradas: El código revisa constantemente el estado del botón sin detener la ejecución del programa.
Debounce No Bloqueante: Se utiliza un mecanismo de debounce basado en tiempo, que permite evitar lecturas falsas sin bloquear el flujo del programa.
Flujo Continuo: El programa sigue ejecutando otras tareas mientras monitorea el estado del botón.
Este enfoque es útil cuando se quiere manejar entradas físicas, como botones, de manera eficiente en un sistema embebido sin interferir con otras operaciones en curso.
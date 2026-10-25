# NEON RIDERS — Duelo online de motos

Proyecto web para una carrera de motos entre dos jugadores desde dispositivos distintos.

## Tecnologías
- HTML, CSS y JavaScript
- Canvas 2D para dibujar la pista en perspectiva, las motos, los obstáculos y el HUD
- Supabase Realtime Broadcast para sincronizar la carrera entre dos navegadores
- Vercel para publicación web estática

## Cómo jugar
1. Abre la página en el primer dispositivo y pulsa **Crear sala nueva**.
2. Comparte el código que aparece con el segundo jugador.
3. En el segundo dispositivo, abre la misma página, introduce el código y pulsa **Unirse**.
4. El jugador 1 inicia la carrera.
5. Jugador 1: **W** acelera y **A/D** giran. Jugador 2: **flecha arriba** acelera y **flechas izquierda/derecha** giran.
6. Completa tres vueltas. Puedes reiniciar la carrera para una revancha.

## Arquitectura
La aplicación es estática y utiliza el cliente oficial de Supabase JS desde CDN. Cada sala se comunica mediante un canal Broadcast de Supabase Realtime; el estado de cada piloto se transmite mientras corre. No hay servidor propio ni tabla SQL requerida para el prototipo.

## Configuración
El archivo `index.html` incluye la URL del proyecto Supabase y una clave publicable (`sb_publishable_...`). Las claves publicables están diseñadas para usarse en el navegador; nunca debe ponerse una clave secreta o `service_role` en este archivo.

El modo de salas usa canales públicos para que dos jugadores puedan entrar con un código sin crear cuentas. Esto es apropiado solo para una demostración de aula: no debe considerarse un sistema competitivo seguro, porque un usuario podría intentar suplantar estados o unirse a un canal conocido.

## Publicar en Vercel
Importa el repositorio `Jhonn16ax/proyecto` en Vercel. Al ser una página estática con `index.html` en la raíz, no necesita comando de build ni dependencias de Node. Después de conectar el repositorio, cada push a `main` podrá generar un nuevo despliegue.

## Alcance y limitaciones
- Es un prototipo de carreras con gráficos Canvas 2D y perspectiva simulada; no utiliza un motor 3D real.
- Los dos pilotos se sincronizan entre navegadores mediante Supabase Realtime.
- La calidad de la conexión depende de internet y de la disponibilidad de Supabase.
- El juego todavía no incluye cuentas de usuario, validación autoritativa del ganador, ranking persistente ni antitrampas.

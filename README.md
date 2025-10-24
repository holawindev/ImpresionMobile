# 🧩 HolaWindev Labs – Impresión Mobile

**ESC/POS en Android con WinDev Mobile.**

Este repositorio acompaña el contenido del canal **HolaWindev** y documenta un enfoque **simple y controlado** para imprimir en impresoras térmicas vía **Bluetooth** desde **WinDev Mobile**. Está pensado para que puedas adaptarlo a tu app sin dependencias raras.

---

## 🎯 Objetivo

- Demostrar **impresión directa ESC/POS** en Android.
- Mantener el control: abrir conexión, enviar bytes y cerrar.
- Evitar componentes externos y “magia negra”.

> Nota: Este repo prioriza **claridad** sobre “packaging”. No pretende ser un framework universal; es una base educativa para partir.

---

## 📦 Alcance

- Conexión Bluetooth clásica (SPP) a una impresora térmica.
- Envío de comandos ESC/POS (texto, feed, corte — si la impresora lo soporta).
- Ejemplos de **formateo básico** (alineación, negrita, tamaño, QR si aplica).
- Manejo de **errores comunes** (no emparejada, fuera de rango, buffer lleno).

> Las secuencias ESC/POS pueden variar por modelo. Verificá el manual de tu impresora si algún comando no responde.

---

## ⚙️ Requisitos

- **WinDev Mobile 2024 o superior** (probado con versiones recientes).
- **Android 8+** con Bluetooth habilitado.
- Impresora térmica **compatible ESC/POS** (cualquier marca común suele funcionar).
- Permisos Android declarados según tu versión (ej.: `BLUETOOTH_CONNECT`, `BLUETOOTH_SCAN`).

> Ajustá los permisos y el `targetSdk` según tu proyecto. No se incluye un `AndroidManifest.xml` específico en este repo para no interferir con tu setup.

---

## 🚀 Uso básico (guía general)

1. **Emparejá** tu impresora desde Android (Ajustes del teléfono).
2. En tu app **obtené el nombre/MAC** del dispositivo Bluetooth objetivo.
3. **Abrí el socket** serie (SPP) y **enviá** los bytes ESC/POS necesarios.
4. **Cerrá** la conexión con manejo de errores/timeout.

> El envío de bytes varía según tu estrategia. Podés armar un módulo mínimo de “PrinterService” con funciones como `Open()`, `Write(bytes)`, `Close()` y mantenerlo desacoplado del resto de la app.

---

## 🧪 Pruebas recomendadas

- **Smoke test:** imprimir una línea simple `"Hola ESC/POS"`.
- **Feed:** algunos “line feeds” para verificar el buffer.
- **Formato:** una línea centrada, negrita y tamaño doble.
- **Código QR / código de barras:** solo si tu impresora lo soporta.
- **Corte:** si la impresora tiene cortador, enviá el comando correspondiente (no todas lo tienen).

---

## 📁 Estructura del proyecto

WinDev Mobile gestiona internamente la estructura del proyecto.
Por eso **no es necesario crear carpetas manualmente** como en otros lenguajes: el propio IDE genera todo lo que necesita.

Las partes más relevantes que vas a encontrar son:

```
/ImpresionMobile.wdp # Proyecto principal de WinDev Mobile
/Windows/ # Ventanas y componentes visuales
/Classes/ # Clases WLanguage (Bluetooth, ESC/POS, etc.)
/Procedures/ # Procedimientos globales o utilitarios
/Layouts/ # Diseño adaptativo (si aplica)
/Android/ # Archivos específicos del target Android
README.md
LICENSE.md
```

Si abrís el `.WDP` en WinDev Mobile, el entorno reconstruye la jerarquía automáticamente.
No borres ni renombres estas carpetas fuera del IDE para evitar referencias rotas.

> Este repositorio está pensado para **exploración y aprendizaje**: podés importar las clases o procedimientos que necesites en tu propio proyecto sin copiar toda la estructura.

---

## 🤝 Contribuciones

- Correcciones, mejoras y ejemplos concretos son bienvenidos.
- Evitá “mega frameworks”; mantené el enfoque **didáctico y minimalista**.
- Si tu aporte depende de una librería externa, explicá por qué es necesaria.

Para proponer cambios: **fork → branch → PR** con una descripción clara del problema y la solución.

---

## 🗺️ Roadmap (corto)

- [ ] Ejemplo mínimo de conexión + texto.
- [ ] Tabla de comandos ESC/POS más usados (negrita, tamaño, subrayado, centrado).
- [ ] Ejemplo de QR (si la impresora lo soporta).
- [ ] Sección “Problemas comunes” con mensajes de error reales.
- [ ] Guía de permisos Android por versión (12/13/14).

> Marcá con ✅ lo que ya esté en tu copia. Este README no afirma la existencia de archivos que no estén en tu repo.

---

## 🎥 Video relacionado

Cuando esté publicado, se linkea acá el tutorial del canal:
**YouTube:** https://youtube.com/@HolaWindev

---

## 🔗 Comunidad

- **Discord HolaWindev:** https://discord.gg/9xDAJ6ugQr
- **Sitio:** https://holawindev.com

---

## 🧾 Licencia

Este proyecto está bajo **CC BY-NC-SA 4.0**.
Podés usarlo y adaptarlo con fines no comerciales, manteniendo la atribución y la misma licencia.

Ver: `LICENSE.md`

---

## 👤 Autor

**Juan Barbat**
📧 juan@barbat.dev
🌐 https://barbat.dev

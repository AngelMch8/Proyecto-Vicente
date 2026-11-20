# GALLOTRACK — versión inicial 0.1

Aplicación web progresiva (PWA) en español, preparada para empaquetarse como aplicación Android con Capacitor.

## Incluye
- Panel de control y estadísticas calculadas desde los registros.
- Alta, edición, búsqueda y expediente de gallos/gallinas.
- Identificador único para cada animal y lector QR con cámara en navegadores compatibles con `BarcodeDetector` (el QR debe contener el código del animal).
- Registro de alimentación, horarios y observaciones.
- Registro de salud, síntomas, tratamientos y revisiones.
- Genealogía y eventos reproductivos.
- Configuración de perímetro geográfico y registro de identificadores de rastreadores.
- Exportación e importación de respaldo JSON.
- Persistencia local en el dispositivo y caché PWA.

## Limitaciones importantes de esta versión
- El módulo GPS no recibe posiciones reales de gallos. El GPS del teléfono solo puede proporcionar la ubicación del teléfono. Para rastreo individual se necesita hardware GPS/IoT por animal, conectividad y la API/protocolo del fabricante. El módulo deja preparado el registro del dispositivo y el perímetro, sin inventar ubicaciones.
- Las alertas automáticas de salida requieren integrar telemetría real, un servicio backend y notificaciones push/Android.
- No hay diagnóstico veterinario automático. Se registran observaciones; la evaluación clínica corresponde a un veterinario.
- No se confirma fecundación por registrar una monta. Debe verificarse con ovoscopia u otro método adecuado.
- Los datos se guardan localmente; no existe sincronización entre dispositivos ni inicio de sesión.

## Probar en computadora o celular
Servir la carpeta `www` con un servidor HTTP local. Para instalar como PWA se requiere HTTPS (o localhost). Abre `www/index.html` para una prueba rápida, aunque algunas funciones como cámara, geolocalización y service worker requieren HTTPS/localhost.

## Empaquetar como APK (requiere Android Studio, Android SDK y JDK)
1. Instala Node.js LTS y Android Studio.
2. En esta carpeta ejecuta:
   ```bash
   npm install
   npx cap add android
   npx cap sync android
   npx cap open android
   ```
3. En Android Studio configura el SDK y compila: **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
4. El APK de depuración se genera normalmente en `android/app/build/outputs/apk/debug/app-debug.apk`.

Para actualizaciones web posteriores: `npx cap sync android` y vuelve a compilar.

## GPS real: información necesaria para la siguiente etapa
Para integrar los rastreadores, se necesita marca/modelo, tipo de conectividad (SIM/LTE-M/NB-IoT/LoRa/Bluetooth), documentación de API o protocolo, formato de coordenadas y frecuencia de reporte. La selección del hardware debe considerar peso, autonomía, resistencia al agua, seguridad y bienestar del animal.

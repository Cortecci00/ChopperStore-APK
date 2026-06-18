# ChopperStore APK

App móvil de ChopperStore (marketplace de skins de CS2) para Android, generada con [Capacitor](https://capacitorjs.com) envolviendo la misma app Angular 18 del [Website de ChopperStore](https://github.com/Cortecci00/ChopperStore).

Consume la misma API REST (ASP.NET Core 8) que el Website. No tiene lógica propia: es el mismo frontend Angular empaquetado como app nativa Android.

## Requisitos

- Node.js + npm
- Android Studio (con Android SDK y un emulador o dispositivo físico)
- JDK 17+ (Android Studio trae uno embebido en `Android Studio/jbr`)

## Desarrollo

```bash
npm install
ng build                  # genera dist/angular18/browser
npx cap sync android       # copia el build web al proyecto Android
npx cap run android        # lo corre en emulador/dispositivo
```

## Generar el .apk firmado

```bash
npx cap open android
# En Android Studio: Build > Generate Signed Bundle / APK
```

## Configuración del backend

La URL del backend se define en `src/environments/environment.prod.ts` (usada en builds de producción, que es lo que consume la app empaquetada). Debe apuntar siempre a una URL pública HTTPS, nunca a `localhost` (el WebView de la app corre en el dispositivo, no en la PC).

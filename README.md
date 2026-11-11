# GOGO Admin

Panel de administración de GOGO Food: restaurantes, pedidos, usuarios, retiros, reembolsos, promociones, reseñas y soporte.

Las pantallas (`lib/main.dart`, `lib/screens/admin/`, `lib/theme/`) viven aquí. Los servicios, modelos y la configuración vienen del paquete compartido **`gogo_core`**, que está en [fercadi-delivery/packages/gogo_core](https://github.com/Angel43837/fercadi-delivery/tree/dev/packages/gogo_core) y se usa fijado a un tag (`ref:` en `pubspec.yaml`).

**Un arreglo en `supabase_service.dart`, `auth_service.dart`, modelos o `core/` se hace en gogo_core, no aquí.** Para traerlo: cambia `ref:` al tag nuevo (`gogo-core-vX.Y.Z`), `flutter pub get`, prueba y commit. Detalle en el README de gogo_core.

## Correr

Pruebas (Supabase `ymztoayxzewghbethahv`):

```bash
flutter pub get
flutter run --dart-define-from-file=pruebas.dart-define.json
```

Producción (GOGO Food, `dlukaxbcyetcdbdjjgct`): pasa `SUPABASE_URL` y `SUPABASE_ANON_KEY` de producción con `--dart-define`. Sin ellos, Admin apunta a Pruebas por default (`gogo_core/core/constants.dart`) y no ve lo que pasa en la app real.

## Builds

- Android: `flutter build apk --release` (applicationId `com.fercadi.admin`)
- iOS: `flutter build ios --release` (bundle `com.fercadi.admin`)
- Web: `flutter build web --release`

Solo entra `admin@fercadi.com` o una cuenta con `app_metadata.role = 'admin'`; los permisos reales los aplica la base de datos (RLS), no la app.

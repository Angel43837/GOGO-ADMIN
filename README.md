# GOGO Admin

Panel de administración de GOGO Food: restaurantes, pedidos, usuarios, retiros, reembolsos, promociones, reseñas y soporte.

Extraído de [fercadi-delivery](https://github.com/Angel43837/fercadi-delivery) (`lib/main_admin.dart` + `lib/screens/admin/`), igual que se hizo con [gogo-flota](https://github.com/Angel43837/gogo-flota). Trae copiados completos los servicios compartidos (`supabase_service.dart`, `auth_service.dart`, modelos, `core/`), así que incluyen métodos que Admin no usa.

**Ojo:** esos servicios son una copia. Un arreglo en `supabase_service.dart` del repo de la app NO llega aquí solo: hay que copiarlo a mano.

## Correr

Pruebas (Supabase `ymztoayxzewghbethahv`):

```bash
flutter pub get
flutter run --dart-define-from-file=pruebas.dart-define.json
```

Producción (GOGO Food, `dlukaxbcyetcdbdjjgct`): pasa `SUPABASE_URL` y `SUPABASE_ANON_KEY` de producción con `--dart-define`. Sin ellos, Admin apunta a Pruebas por default (`lib/core/constants.dart`) y no ve lo que pasa en la app real.

## Builds

- Android: `flutter build apk --release` (applicationId `com.fercadi.admin`)
- iOS: `flutter build ios --release` (bundle `com.fercadi.admin`)
- Web: `flutter build web --release`

Solo entra `admin@fercadi.com` o una cuenta con `app_metadata.role = 'admin'`; los permisos reales los aplica la base de datos (RLS), no la app.

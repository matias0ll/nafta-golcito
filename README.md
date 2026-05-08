# Nafta Golcito — Setup

## Archivos
- `index.html` — la app completa
- `manifest.json` — para que se pueda instalar en el celu

## Cómo publicar (GitHub Pages, gratis)

1. Creá una cuenta en github.com si no tenés
2. Creá un repositorio nuevo llamado `nafta-golcito` (público)
3. Subí los dos archivos (`index.html` y `manifest.json`)
4. Andá a Settings → Pages → Source: Deploy from branch → main → / (root)
5. En unos minutos la app va a estar en: `https://TU_USUARIO.github.io/nafta-golcito`

## Cómo instalar en el celu

### Android (Chrome):
1. Abrí la URL en Chrome
2. Menú (⋮) → "Agregar a pantalla de inicio"

### iPhone (Safari):
1. Abrí la URL en Safari
2. Botón compartir → "Agregar a pantalla de inicio"

## Primer uso

1. Abrí la app → no hay usuarios todavía
2. Ir directo a Firebase Console → Firestore → agregar manualmente:
   - Colección: `usuarios`
   - Documento: (auto-id)
   - Campos: `nombre: "Mati"`, `pin: "1234"`, `admin: true`
3. Repetir para cada hermano (con admin: false)
4. También agregar los viajes recurrentes desde la app (Config → Agregar viaje recurrente)

## Reglas de Firestore (seguridad básica)

En Firebase Console → Firestore → Reglas, pegá esto:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

(Para producción se puede refinar más, pero para uso familiar está bien así)

# Producción: seguridad y flujos

Además de ejecutar `0001_oasis_schema.sql`, añade estas políticas según roles y expón únicamente funciones RPC/Edge Functions para pedidos, cambios de estado, giro y canje. Nunca concedas INSERT público sobre `orders`, `roulette_spins` o `prize_redemptions`.

El backend de Next incluye endpoints de referencia bajo `app/api/`. Requiere las variables de `.env.example`, en especial `SUPABASE_SERVICE_ROLE_KEY` que permanece únicamente en el servidor. El login usa Supabase Auth y guarda un token httpOnly de 8 horas.

## QR

Cada mesa recibe `public_token` aleatorio generado por PostgreSQL. Su enlace es `NEXT_PUBLIC_SITE_URL/menu?table=TOKEN`. Para imprimirlo, usa cualquier generador QR SVG/PNG local desde el panel una vez se conecte Supabase; el token no expone el ID interno de la mesa.

## Antes de publicar

- Crear el usuario inicial en Supabase Auth y asignarle `staff_profiles.role = 'admin'` desde SQL Editor seguro.
- Configurar URL de redirección/Auth y dominio real.
- Aplicar RLS completas y probar con cuentas `staff` y `admin`.
- Activar rate limiting/WAF (Vercel o proxy) para los endpoints.

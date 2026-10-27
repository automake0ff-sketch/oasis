# Oasis Shisha Lounge

Carta digital y flujo de pedido para Oasis Shisha Lounge, Sevilla Este. Incluye una interfaz mobile-first inspirada en una carta nocturna de lounge, carrito local para demostración, seguimiento de pedidos y flujo de fidelidad con ruleta o rasca y gana tras confirmar el cobro.

## Requisitos

- Node.js 20 o superior
- npm
- Para persistencia y acceso de personal: proyecto Supabase

## Desarrollo

```bash
npm install
Copy-Item .env.example .env.local
npm run dev
```

Next elige automáticamente un puerto libre. Abre la URL que muestre la terminal.

## Configuración Supabase

Completa `.env.local` con el proyecto y las claves Supabase. La `SUPABASE_SERVICE_ROLE_KEY` es solo de servidor y jamás debe publicarse. Ejecuta `supabase/migrations/0001_oasis_schema.sql` en el SQL Editor de Supabase.

Crea el usuario inicial desde Supabase Auth y asígnale un perfil `admin` en `staff_profiles` desde una sesión administrativa segura. Consulta `docs-production.md` para los flujos pendientes y políticas antes de uso real.

## Estado actual

El escaparate, carrito, pedido, activación simulada del premio y juegos son una demostración local, con datos guardados en el navegador. El endpoint de login usa Supabase Auth; los endpoints de pedidos, mesas y ruleta requieren las variables y el esquema configurado.

El panel `/staff` representa únicamente el flujo de demostración de cobro/activación. Para operar en el negocio, hay que conectarlo a una sesión de personal protegida, lector de QR y función transaccional de activación. No usar las credenciales de demo para operar con clientes ni publicar la demo como una integración de pedidos ya conectada.

## Variables

Ver `.env.example`. Nunca añadas `.env.local`, claves privadas, tokens o secretos al repositorio.

# Spotify Stats

Spotify Stats es una web para ver tus estadisticas personales de Spotify: artistas top, canciones top, generos, reproducciones recientes, minutos acumulados por artista, cancion y album, comparativas entre periodos y una tarjeta exportable tipo Wrapped.

Web publicada:

```
https://nestoree.github.io/spotify_stats/
```

## Como funciona la web

La web funciona completamente en tu navegador:

- Te conectas con Spotify usando OAuth con PKCE.
- Spotify te devuelve un token temporal de lectura.
- La web usa ese token para pedir datos a la API publica de Spotify.
- Los datos se pintan directamente en el navegador.
- No hay base de datos externa ni servidor guardando informacion.

La app muestra:

- Tus artistas top.
- Tus canciones top.
- Tus generos mas repetidos.
- Tus ultimas reproducciones.
- Minutos acumulados por artista, cancion y album.
- Comparativa entre `4 semanas`, `6 meses` y `todo el tiempo`.
- Vista por pestañas: `TODO`, `ARTISTAS`, `CANCIONES` y `ALBUMES`.
- Exportacion de una imagen PNG con resumen de tus estadisticas.

## Historial y minutos acumulados

Spotify no entrega minutos historicos reales por artista, cancion o album desde la Web API.

Por eso esta web crea su propio historial local:

1. Cada vez que entras, lee tus ultimas reproducciones de Spotify.
2. Guarda las reproducciones nuevas en `localStorage`.
3. Evita duplicados usando la fecha de reproduccion y la cancion.
4. Calcula minutos acumulados sumando la duracion de las canciones guardadas.

Esto significa que los minutos acumulados empiezan a contar desde que usas la web. Si borras los datos del navegador, tambien puedes perder ese historial local.

## Usar la web

Abre la web:

```
https://nestoree.github.io/spotify_stats/
```

Pulsa **Conectar con Spotify** e inicia sesion en la pagina oficial de Spotify.

## Seguridad y privacidad

- El **Client ID no es secreto**.
- No pegues ni publiques nunca un **Client Secret**.
- Esta web no necesita Client Secret porque usa OAuth con PKCE.
- Los tokens de Spotify se guardan solo en el navegador del usuario.
- El historial acumulado se guarda solo en `localStorage`.
- La web no sube tu historial a ningun servidor.

## Permisos que pide Spotify

La web pide permisos de solo lectura para:

- Leer tus artistas y canciones top.
- Leer tus ultimas reproducciones.
- Leer que estas escuchando ahora.
- Leer datos basicos de tu perfil.

No puede modificar playlists, seguir artistas, borrar canciones ni cambiar tu cuenta.

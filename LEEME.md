# POLE Studios — web lista para subir

Esta carpeta es la web completa. No hay que instalar ni compilar nada:
es HTML y archivos sueltos, así que funciona en cualquier hosting.

```
index.html          → la web entera (30 KB)
assets/             → logo, vídeo, fotos de las prendas, favicon
vercel.json         → hace que las fotos y el vídeo se cacheen (carga más rápido)
```

Para verla en tu Mac antes de subirla: doble clic en `index.html`.

---

## 1. Subirla a Vercel

La forma más rápida, sin instalar nada:

1. Entra en **https://vercel.com/drop**
2. Arrastra esta carpeta (`polestudios-web`) entera a la página.
3. Ponle nombre al proyecto (por ejemplo `polestudios`) y pulsa **Deploy**.

En un minuto te da una dirección tipo `polestudios.vercel.app` que ya funciona.

> Ojo: cada vez que arrastras la carpeta a Vercel Drop se crea un proyecto
> **nuevo**. Si más adelante quieres actualizar la web sin cambiar de proyecto,
> usa la opción de la terminal:
>
> ```
> npm i -g vercel
> cd ruta/a/polestudios-web
> vercel          # la primera vez: te pide login y datos del proyecto
> vercel --prod   # las siguientes veces, para publicar cambios
> ```

---

## 2. Conectar tu dominio polestudios.com

### En Vercel

1. Abre tu proyecto → pestaña **Settings** → **Domains** (menú lateral).
2. Pulsa **Add Domain**, escribe `polestudios.com` y confirma.
   Te ofrecerá añadir también `www.polestudios.com`: acéptalo.
3. Vercel te mostrará una tarjeta con **los valores exactos** que tienes que
   copiar. Déjala abierta, la necesitas en el paso siguiente.

**Importante:** copia los valores de TU pantalla. Vercel ya no usa una única
IP para todos: cada proyecto puede tener la suya, y el CNAME de `www` es
distinto en cada proyecto. No copies valores de tutoriales de internet ni de
este archivo, porque no funcionarán.

Verás algo con esta forma (los valores serán otros):

| Tipo  | Nombre | Valor                                    |
|-------|--------|------------------------------------------|
| A     | `@`    | la IP que te muestre Vercel              |
| CNAME | `www`  | el destino `....vercel-dns-XXX.com` tuyo |

### En Hostinger

1. Entra en hPanel → **Dominios** → elige `polestudios.com`.
2. Ve a **DNS / Nameservers** → **Editor de zona DNS**.
3. Deja los nameservers de Hostinger como están (es lo más sencillo) y añade
   los dos registros que te dio Vercel:
   - Registro **A**, nombre `@`, apuntando a la IP de Vercel.
   - Registro **CNAME**, nombre `www`, apuntando al destino de Vercel.
4. Si ya existía un registro A en `@` apuntando a otro sitio, bórralo o edítalo
   (no puede haber dos).

### Después

- El cambio suele verse en minutos, aunque oficialmente puede tardar hasta
  24–48 horas. Puedes comprobarlo en **whatsmydns.net**.
- El candado de seguridad (HTTPS) lo pone Vercel solo, en cuanto detecta que el
  dominio ya apunta a él. No tienes que hacer nada ni pagar por el certificado.

---

## 3. Cambiar cosas de la web

Casi todo está en `index.html`. Lo que más te puede interesar:

- **Texto de la cinta de arriba:** busca `Pedidos DM` y `New clothes soon`.
- **Número de WhatsApp:** busca `wa.me/34688825797`. Cambia el número y, si
  quieres, el texto que va detrás de `?text=`.
- **Texto del popup:** busca `Are you ready?`.
- **Las prendas:** hacia el final del archivo hay una lista `var PRODUCTS = [`
  con el nombre, la descripción y las tallas de cada una. Para añadir una
  prenda nueva, copia uno de los bloques, cámbiale los datos, ponle un `id`
  que no esté usado y guarda su foto en `assets/`.

Si prefieres no tocar el código, dímelo y te lo cambio yo.

---

## Y el panel de administración, ¿qué?

El panel para añadir y borrar ropa (el del archivo `catalogo-pole-web.zip`)
**no funciona en Vercel**: necesita guardar la base de datos y las fotos que
subes, y Vercel no permite guardar archivos — borra todo en cada visita.

Tienes dos caminos:

1. **El sencillo:** usas esta web estática en polestudios.com, y cuando quieras
   añadir o quitar prendas me lo pides y te dejo el archivo actualizado.
2. **El completo:** si quieres el panel funcionando en internet, hay que usar un
   hosting que sí guarde archivos (Railway o Render, por ejemplo, tienen plan
   gratuito). Dímelo y te lo preparo.

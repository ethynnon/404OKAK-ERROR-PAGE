# OKAK 404 Error Page

A minimalist animated 404 error page featuring the OKAK cat character.

> Made with vibe-coding. Not production-perfect, but production-ready.

![Preview](https://i.ibb.co/rKLSrRMP/4-DC435-DC-6-CEB-4696-AE33-D1-DD6-F61-FF92.png)

## Features

- Smooth entrance animations
- Dark theme
- Responsive (desktop & mobile)
- No dependencies — pure HTML + CSS

## Installation

### Nginx

1. Place the files in your server directory
2. Add to your `server` block in `nginx.conf`:

```nginx
error_page 400 404 500 502 /error.html;
location = /error.html {
    root /var/www/html/errorpage;
}
```

3. Restart Nginx: `nginx -s reload`

---

### Caddy

1. Place the files in `/srv/error_pages/okak/` (or any path you prefer)
2. Add to your `Caddyfile` inside the site block:

```caddy
handle /assets/* {
    root * /srv/error_pages/okak
    file_server
}

handle_errors {
    root * /srv/error_pages/okak
    rewrite * /error.html
    file_server
}
```

3. Reload Caddy: `caddy reload` or `docker compose restart caddy`

---

## Notes

- Mobile adaptation is functional but minimal
- Asset paths in `error.html` must be relative (no `errorpage/` prefix)
- For SPA setups (React/Vue): this page will only show on server-level errors (502, container down), not client-side routing misses

## Credits

- Original character & design — [pluralplay](https://github.com/pluralplay)
- OKAK cat — the real hero of this page

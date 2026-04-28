# 📧 Envío de Correo Transaccional con Brevo API

> **Documentación oficial:** [https://developers.brevo.com/reference/sendtransacemail](https://developers.brevo.com/reference/sendtransacemail)
>
> **Plantilla HTML del correo:** [`index.html`](./index.html)

---

## ¿Qué es esto?

Este ejemplo muestra cómo enviar un correo electrónico usando la **API REST de Brevo** (anteriormente Sendinblue) mediante una petición `curl`. No requiere ningún servidor SMTP configurado — solo una API Key y conexión a internet.

---

## Requisitos

- Cuenta gratuita en [Brevo](https://www.brevo.com)
- Tu **API Key** (disponible en *Configuración → API Keys*)
- `curl` instalado en tu sistema

---

## Comando de ejemplo

```bash
curl --request POST \
  --url https://api.brevo.com/v3/smtp/email \
  --header 'accept: application/json' \
  --header 'api-key: TU_API_KEY' \
  --header 'content-type: application/json' \
  --data '{
    "sender": {
      "email": "noreply@tudominio.com",
      "name": "Tu Empresa"
    },
    "to": [
      {
        "email": "destinatario@correo.com",
        "name": "Nombre Destinatario"
      }
    ],
    "subject": "Ofertas exclusivas para ti",
    "htmlContent": "<h1>Hola!</h1><p>Este es el cuerpo del correo en HTML.</p>"
  }'
```

---

## Descripción de los parámetros

| Campo           | Descripción                                                         |
|-----------------|---------------------------------------------------------------------|
| `api-key`       | Tu clave de API de Brevo. Reemplaza `TU_API_KEY` con la tuya real. |
| `sender.email`  | Correo remitente (debe estar verificado en Brevo).                  |
| `sender.name`   | Nombre visible del remitente en el cliente de correo.               |
| `to`            | Lista de destinatarios (puedes agregar más objetos al arreglo).     |
| `subject`       | Asunto del correo.                                                  |
| `htmlContent`   | Cuerpo del correo en formato HTML.                                  |

---

## Ejemplo con plantilla HTML completa

El archivo [`index.html`](./index.html) de este repositorio contiene la plantilla completa con diseño profesional:

- Soporte para **modo oscuro** (`prefers-color-scheme: dark`)
- Fuente **Inter** vía Google Fonts
- **Código promocional** y fecha de vigencia
- **Botón CTA** con diseño dorado
- **Pie de página** con enlace para cancelar suscripción

Para enviarla, copia el contenido de `index.html`, minifícalo (elimina saltos de línea) y colócalo en el campo `htmlContent`:

```bash
curl --request POST \
  --url https://api.brevo.com/v3/smtp/email \
  --header 'accept: application/json' \
  --header 'api-key: TU_API_KEY' \
  --header 'content-type: application/json' \
  --data '{
    "sender": {
      "email": "noreply@tudominio.com",
      "name": "Tu Empresa"
    },
    "to": [
      {
        "email": "destinatario@correo.com",
        "name": "Nombre Destinatario"
      }
    ],
    "subject": "Ofertas exclusivas para ti",
    "htmlContent": "<!-- contenido minificado de index.html -->"
  }'
```

---

## Respuesta esperada

Si la petición es exitosa, Brevo responde con `HTTP 201` y un JSON similar a:

```json
{
  "messageId": "<202504281234.abc123@smtp-relay.mailin.fr>"
}
```

Si hay un error (API Key incorrecta, remitente no verificado, etc.), la respuesta incluirá un código de error y descripción.

---

## Notas

- El correo remitente **debe estar verificado** en tu cuenta de Brevo antes de usarlo.
- El plan gratuito permite hasta **300 correos por día**.
- Nunca expongas tu `api-key` en repositorios públicos. Usa variables de entorno o un gestor de secretos.
- Para envíos masivos o con plantillas dinámicas, consulta la [documentación completa de la API](https://developers.brevo.com/reference/sendtransacemail).

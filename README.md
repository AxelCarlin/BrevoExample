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

El archivo [`index.html`](./index.html) contiene la versión indentada y comentada de la plantilla. El siguiente comando es el equivalente listo para ejecutarse — el HTML va minificado (sin saltos de línea) directamente en `htmlContent`:

```bash
curl --request POST \
  --url https://api.brevo.com/v3/smtp/email \
  --header 'accept: application/json' \
  --header 'api-key: TU_API_KEY' \
  --header 'content-type: application/json' \
  --data '{"sender":{"email":"noreply@nexsmart.com.mx","name":"NexSmart"},"to":[{"email":"destinatario@correo.com","name":"Destinatario"}],"subject":"Ofertas exclusivas para ti","htmlContent":"<!DOCTYPE html><html><head><meta charset=\"UTF-8\"><meta name=\"viewport\" content=\"width=device-width,initial-scale=1\"><link href=\"https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&display=swap\" rel=\"stylesheet\"><style>@media (prefers-color-scheme:dark){.email-body{background:#1a1a1a !important}.email-card{background:#242424 !important}.header-bar{background:#000000 !important}.cta-btn{background:#c8a96e !important;color:#000000 !important;border-color:#c8a96e !important}.promo-box{background:#2e2e2e !important}.footer-bar{background:#1e1e1e !important}.body-text{color:#cccccc !important}.label-text{color:#999999 !important}.promo-value{color:#ffffff !important}.footer-text{color:#777777 !important}}</style></head><body class=\"email-body\" style=\"margin:0;padding:0;background:#f4f4f0;font-family:Inter,sans-serif\"><table width=\"100%\" cellpadding=\"0\" cellspacing=\"0\"><tr><td align=\"center\" style=\"padding:40px 16px\"><table class=\"email-card\" width=\"560\" cellpadding=\"0\" cellspacing=\"0\" style=\"background:#ffffff;border-radius:16px;overflow:hidden;max-width:560px\"><tr><td class=\"header-bar\" style=\"background:#111111;padding:36px 48px\"><p style=\"margin:0;font-size:22px;font-weight:600;color:#ffffff;letter-spacing:2px\">NEXSMART</p><p style=\"margin:6px 0 0;font-size:12px;color:#888888;letter-spacing:1px\">TIENDA DEPARTAMENTAL</p></td></tr><tr><td style=\"padding:48px 48px 32px\"><p class=\"label-text\" style=\"margin:0 0 8px;font-size:11px;font-weight:600;color:#888888;letter-spacing:2px\">OFERTA EXCLUSIVA</p><h1 style=\"margin:0 0 16px;font-size:30px;font-weight:300;color:#111111;line-height:1.2\">Hasta 40% de descuento en tu próxima compra</h1><p class=\"body-text\" style=\"margin:0 0 32px;font-size:15px;color:#666666;line-height:1.7\">Seleccionamos las mejores piezas de la temporada para ti. Descuento aplicado automáticamente al momento del pago.</p><table cellpadding=\"0\" cellspacing=\"0\"><tr><td style=\"border-radius:8px;background:#c8a96e;border:2px solid #c8a96e\"><a class=\"cta-btn\" href=\"https://nexsmart.com.mx\" style=\"display:inline-block;padding:16px 36px;font-size:13px;font-weight:600;color:#000000;text-decoration:none;letter-spacing:1px;border-radius:8px\">VER OFERTAS</a></td></tr></table></td></tr><tr><td style=\"padding:0 48px 40px\"><table width=\"100%\" cellpadding=\"0\" cellspacing=\"0\" style=\"border-top:1px solid #f0f0f0;padding-top:32px\"><tr><td width=\"48%\"><div class=\"promo-box\" style=\"background:#f8f8f6;border-radius:12px;padding:24px\"><p class=\"label-text\" style=\"margin:0 0 4px;font-size:11px;color:#888888;letter-spacing:1px\">CÓDIGO PROMO</p><p class=\"promo-value\" style=\"margin:0;font-size:22px;font-weight:600;color:#111111;letter-spacing:3px\">NEXS40</p></div></td><td width=\"4%\"></td><td width=\"48%\"><div class=\"promo-box\" style=\"background:#f8f8f6;border-radius:12px;padding:24px\"><p class=\"label-text\" style=\"margin:0 0 4px;font-size:11px;color:#888888;letter-spacing:1px\">VÁLIDO HASTA</p><p class=\"promo-value\" style=\"margin:0;font-size:22px;font-weight:600;color:#111111\">Mayo 15</p></div></td></tr></table></td></tr><tr><td class=\"footer-bar\" style=\"background:#f8f8f6;padding:24px 48px;border-top:1px solid #eeeeee\"><p class=\"footer-text\" style=\"margin:0;font-size:12px;color:#aaaaaa;line-height:1.6\">Recibiste este correo porque estás suscrito a NexSmart. <a href=\"#\" style=\"color:#888888\">Cancelar suscripción</a></p></td></tr></table></td></tr></table></td></tr></table></body></html>"}'
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

# Pasos para hacer uso de la API Proveeo

## 1. Autenticación - Obtener Token

Para interactuar con la **API**, primero debes obtener un token de autenticación. Este token será necesario en cada solicitud posterior.

### URL para obtener el Token
- GET https://www.proveeo.co/token-api/

#### Formato de respuesta esperado
      {
        "token": "f0628810-bfe2-4b99-9d88-6b7f837ad7f4",
        "expires_at": "2024-10-12T03:00:57.602Z"
      }

- **token**: El valor que deberás usar en el encabezado Authorization para autenticarte en las siguientes solicitudes.
- **expires_at**: Fecha y hora de expiración del token.

## Ejemplo de uso del Token en las solicitudes

El **token** obtenido debe ser incluido en el encabezado **Authorization** de las siguientes peticiones:

Authorization: <token>


![](https://raw.githubusercontent.com/urian121/imagenes-proyectos-github/master/full-stack-laravel10-react-mysql-y-bootstrap.png)

## 2. Acceso a la API - Envío de Guía

Una vez **autenticado**, puedes enviar los datos de la guía usando el método POST.


### URL para enviar guía

- POST https://www.proveeo.co/api/envio-guia
Cuerpo de la solicitud (JSON)

      {
        "id_remitente": 6,
        "nombre_destinatario": "Urian Viera",
        "descripcion_articulo": "Campo opcional. El paquete es Ropa.",
        "tlf1_destinatario": 1234567789,
        "tlf2_destinatario": 1234567789,
        "cantidad_cobrar": 1300,
        "valor_adicional": 1200,
        "direccion_destinatario": "calle 1 # 2-3",
        "zona_id": 3,
        "observacion": "observacion de prueba",
        "email_destinatario": "email_destinatario@example.com"
      }


![](https://raw.githubusercontent.com/urian121/imagenes-proyectos-github/master/full-stack-laravel10-react-mysql-y-bootstrap.png)

### Campos obligatorios

- **id_remitente**: ID del remitente (entero positivo).
- **nombre_destinatario**: Nombre completo del destinatario (texto).
- **tlf1_destinatario**: Número de teléfono principal del destinatario (entero válido y no negativo).
- **cantidad_cobrar**: Valor a cobrar al destinatario (entero positivo, sin decimales, puntos ni comas).
- **valor_adicional**: Valor adicional en la transacción (entero positivo, sin decimales, puntos ni comas).
- **direccion_destinatario**: Dirección completa del destinatario (texto).
- **zona_id**: ID de la zona geográfica (entero positivo).

### Requisitos adicionales

Los campos **cantidad_cobrar**, **valor_adicional** y **tlf1_destinatario** deben ser números enteros válidos y no negativos. No se aceptan decimales, puntos ni comas.
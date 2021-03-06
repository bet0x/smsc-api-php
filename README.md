Librería PHP para SMSC
================

Esta es una libería PHP para facilitar el uso de la API de SMSC (http://smsc.com.ar/).

-----------

## Instalación

### Composer

#### Instalar Composer

```bash
curl -sS https://getcomposer.org/installer | php
```

#### Agregar SMSC via Composer

Agrega a tu archivo composer.json:

```javascript
{
    ...
    "require": {
        ...
        "smsc/smsc-api-php": "dev-master"
    }
    ...
}
```

## ¡Comienza!

### Utilizando los ejemplos

Una vez que tienes tu cuenta SMSC (puedes solicitar una forma gratuita con 20 SMSC gratis), debes
editar config.php con tus datos de acceso a la API (los obtienes aquí: http://www.smsc.com.ar/usuario/api/).
Una vez que lo hayas completado, podrás probar los ejemplos de la carpeta examples.

### Usándolo en tu proyecto

```php
try {
	$smsc = new Smsc($your_user, $your_apikey);

	// Estado del servicio
	echo 'El estado del servicio es '.($smsc->getEstado()?'OK':'CAIDO').'. ';

	// Saldo
	echo 'Quedan: '.$smsc->getSaldo().' sms. ';
	
	// Enviar SMS
	$smsc->addNumero(2627, 000000);
	$smsc->setMensaje('Hola Mundo!');
	if ($smsc->enviar())
		echo 'Mensaje enviado.';
} catch (Exception $e) {
	echo 'Error '.$e->getCode().': '.$e->getMessage();
}
```

## License

The MIT License (MIT)

Copyright (c) 2014 BitPay, Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
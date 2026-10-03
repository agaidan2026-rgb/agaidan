# AGAIDAN desde Chrome: despliegue y prueba

## Publicar

1. Sube **todo el contenido de esta carpeta** a la raíz de un sitio estático, manteniendo `index.html`, `manifest.webmanifest`, `service-worker.js` e `icons/` en sus rutas.
2. Activa HTTPS en el dominio. Los service workers y la instalación requieren HTTPS (salvo `localhost`). No se necesita servidor de aplicación ni base de datos.
3. Abre el dominio en Chrome. Comprueba que carga el resumen y que el menú y los formularios funcionan.
4. Prueba **Mi negocio**: guarda un nombre, recarga la página y comprueba que permanece. Importa un CSV pequeño de prueba y sube un documento; deben aparecer en las secciones de revisión/importación.
5. Tras la primera carga, prueba en modo avión o sin conexión: AGAIDAN debe abrir con el shell ya almacenado. No borres los datos del sitio durante esta prueba.
6. En Chrome Android, usa el aviso **Instalar** cuando aparezca o el menú ⋮ → **Instalar aplicación / Añadir a pantalla de inicio**. En iPhone/iPad, Safari → Compartir → **Añadir a pantalla de inicio**. La instalación no copia datos entre dispositivos.

## Qué se guarda y dónde

Esta PWA conserva todas las funciones del piloto, pero es **local a cada dispositivo y navegador**. La configuración y registros usan el almacenamiento local del navegador; documentos y fotos usan IndexedDB del mismo dispositivo. No hay cuentas, servidor de aplicación, sincronización ni copia central. Si el cliente cambia de dispositivo/navegador, limpia los datos del sitio o el navegador elimina almacenamiento, esos datos no estarán disponibles allí. Los documentos subidos quedan para revisión; no hay OCR. El CSV sí se procesa en el navegador.

No compartas un mismo dispositivo/navegador entre clientes: la información local puede ser visible a quien use ese perfil. Para conservar datos, utiliza las funciones de exportación de AGAIDAN y guarda las copias de forma segura.

## Actualizaciones y caché

El service worker cachea solo los archivos públicos de la aplicación para reabrirla sin conexión después de visitar el sitio una vez. No cachea documentos ni envía datos. Al desplegar una actualización, incrementa el identificador `agaidan-pwa-v1` en `service-worker.js` para renovar el shell. Para obtener espacio nuevo, el navegador puede requerir conexión.

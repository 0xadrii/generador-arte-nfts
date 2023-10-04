# Generador de Arte

## Requisitos para la Configuración Inicial
- Instala [NodeJS](https://nodejs.org/es/), se recomienda la versión 14.16.0.
- El generador ya incluye capas predefinidas, necesitarás tus propias capas si deseas crear imágenes diferentes.

## Configuración
### 1. Clonar/Descargar el Repositorio

### 2. Instalar Dependencias:
`$ npm install`

### 3. (Opcional) Importar Capas
Si planeas utilizar capas diferentes a las proporcionadas, deberás actualizar la carpeta de *layers* con tus capas personalizadas.

### 4. Editar config.json
Dentro de la carpeta de configuración, encontrarás un archivo *config.json*. Ábrelo y edita los siguientes valores según tus preferencias:
- **layers** (Esto será una lista de todas tus capas, *el orden es importante*)
- **image_description** (Una descripción de tu colección)
- **image_location** (Enlace IPFS, no te preocupes por esto hasta después de haber cargado las imágenes en IPFS)
- **image_count** (Cuántas imágenes deseas generar)
- **image_details** (Ajusta el ancho y alto de las imágenes generadas)

### 5. Generar rarity.json
`$ node scripts/generateRarityConfig.js`.

Esto generará un archivo rarity.json dentro de la carpeta de configuración, luego puedes editar el peso de atributos específicos. Por defecto, todas las capas tienen un peso igual de 10. Al reducir este número, aumentarás la rareza.

En detalle, si tienes 5 atributos, cada uno con un peso de 10, el peso total es de 50. Se genera un número aleatorio de 0 a 50. Supongamos que el número aleatorio es 28, recorrerá cada atributo restando el peso al número aleatorio hasta que el número aleatorio sea menor o igual a 0. Cuando eso suceda, se seleccionará ese atributo.

### 5. Generar Imágenes
`$ node scripts/create.js`

### 6. Cargar tu carpeta de imágenes en IPFS
Después de generar las imágenes, aparecerá una carpeta de construcción con todas tus imágenes. Querrás tomar la carpeta *image* y cargarla en IPFS.

### 7. Reeditar config.json
Después de cargar en IPFS, querrás actualizar el enlace IPFS dentro de config.json con un formato similar a:
*ipfs://QmThdTBCR8DsnXMViDGC13EH9NughYzJrk7VjaAsRBmhX8*

### 8. Regenerar Metadata
`$ node scripts/regenerateMetadata.js`

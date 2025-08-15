# MeshCommerceChain

## E-commerce descentralizado y modular para la Web3

MeshCommerceChain es una arquitectura de e-commerce descentralizada y modular diseñada para la próxima generación de comercio digital. A diferencia de las plataformas centralizadas como Amazon, MeshCommerceChain no busca ser un marketplace global único, sino una red de marketplaces regionales (nodos primarios) interconectados con tiendas (nodos secundarios) independientes. Este diseño permite un ecosistema de comercio más justo, transparente y soberano, donde los comerciantes tienen control total sobre sus operaciones y sus datos.

### Arquitectura de tres capas

La red de MeshCommerceChain se basa en una estructura de tres capas para equilibrar la descentralización con la usabilidad y el rendimiento.

#### Marketplaces (Nodos Primarios)

Su principal función es permitir el descubrimiento de tiendas y productos para los usuarios finales.

- Son el núcleo de la red, funcionando como centros comerciales virtuales.
- Desarrollados en Rust para garantizar seguridad, velocidad y eficiencia.
- Corren en clusters de Kubernetes para una escalabilidad y resiliencia óptimas.
- Pueden conectarse a diferentes blockchains de alto rendimiento como Starknet, Polkadot, Cardano, Cosmos, etc., permitiendo una interoperabilidad multichain.

#### Tiendas (Nodos Secundarios)

Cada tienda es un nodo independiente que se conecta a uno o varios marketplaces primarios.

- Se implementan como imágenes de Docker para una portabilidad máxima.
- Pueden ser desplegadas fácilmente en servicios de cloud como Amazon EC2 o DigitalOcean Droplet, e incluso como aplicaciones de un solo clic (One-Click Apps) en plataformas como Vultr.
- El comerciante mantiene la propiedad total de su infraestructura y datos.

#### Mobile Storefronts (Nodos Terciarios)

Son las aplicaciones móviles y web que los clientes usan para interactuar con la red.

- Permiten a los usuarios explorar los marketplaces primarios para encontrar tiendas o conectarse directamente a una tienda específica si conocen su URL.
- Se conectan a las tiendas utilizando GraphQL, un lenguaje de consulta eficiente que minimiza la carga de la red.
- Se conectan a una blockchain de 2da generación (ej.: Ethereum) o 3ra generación (ej. Polkadot, Cardano) para enviar los fondos (tokens) de forma crypto-nativa.

### El modelo de inventario dual para la Web3

MeshCommerceChain introduce un modelo de inventario dual que se adapta a la volatilidad de las criptomonedas y las preferencias de los comerciantes. El comerciante debe decidir cómo se valorarán sus existencias:

#### Existencias estables en crypto

Una porción del inventario tendrá un precio fijado en una criptomoneda estable (ej. USDT, USDC), lo que significa que su precio en dinero fiduciario (fiat) será volátil.

#### Existencias estables en fiat

Otra porción del inventario tendrá un precio fijado en una moneda fiduciaria (ej. USD), lo que significa que su precio en criptomoneda será volátil.

Este modelo le da al comerciante el poder de elegir la estrategia de precios que mejor se adapte a su negocio y a su tolerancia al riesgo.

## Un monorepo para una red descentralizada

Este monorepo contiene todos los componentes necesarios para construir y ejecutar una red MeshCommerceChain. Nuestro objetivo es proporcionar las herramientas para que cualquiera pueda levantar su propio marketplace, su propia tienda y contribuir al ecosistema del comercio descentralizado.

### Visión

Construir una red de marketplaces locales y tiendas especializadas que desafíe el modelo de centralización masiva de las grandes corporaciones, devolviendo el poder a los comerciantes y a las comunidades.

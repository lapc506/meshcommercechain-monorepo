# MeshCommerceChain

## E-commerce Descentralizado y Modular

MeshCommerceChain es una plataforma descentralizada que permite la integración de uno o más ecosistemas de comercios electrónicos con arquitectura modular y de red de malla, que integrará a los compradores con múltiples comercios y centros comerciales ya sean públicos o privados, sean físicos, virtuales o híbridos.

Actualmente el alcance de MeshCommerceChain estará limitado a la **venta de productos físicos o digitales**, pero no estarán contemplados la venta de servicios, el alquiler de mercancías, o trueques hasta nuevo aviso.

## Objetivos

## Misión

- Proporcionar las herramientas para que cualquiera pueda tener su propia tienda, o inclusive tner su propio marketplace conectado a múltiples tiendas.

## Visión

- Contribuir al ecosistema del comercio descentralizado, al construir un enjambre de nodos comerciales primarios, secundarios, y terciarios, que conformen una red de marketplaces, tiendas, y puntos de venta móviles y de escritorio para **desafiar el status quo**, y devolver el poder a los comerciantes y a los consumidores finales ante la centralización masiva.

### Propósito

- Proveer a los comerciantes de pequeña y mediana escala, una plataforma de comercio electrónico descentralizado y resiliente: a prueba de crisis económicas, pandemias, bloqueos comerciales, sanciones económicas internacionales, escasez de insumos, y especulación de precios; así como proveer a los consumidores la facilidad de comprar desde sus comercios de confianza y mayor conveniencia con mayor accesibilidad, mayor facilidad de búsqueda de mercancías y tiendas, mayor facilidad de pago para compras al por mayor, con más métodos de pago disponibles, y con la capacidad de poder comparar precios de un mismo tipo de mercancía entre distintas tiendas a su alrededor, sin salir de su casa u oficina.

## Arquitectura de tres capas

Establecimos éste monorepo para que contenga todos los componentes necesarios para construir y ejecutar una red MeshCommerceChain.

Para equilibrar la descentralización con la usabilidad y el rendimiento,
**MeshCommerceChain consistirá en una red de malla parcial de tres capas**.

Cada capa está compuesta por:

1. "**nodos comerciales primarios**" que *podrán funcionar como agregadores de comercios electrónicos*, ej.:
    - centros comerciales tradicionales

2. "**nodos comerciales secundarios**" (tiendas), por ejemplo:
    - comercios B2C conglomerados
      - supermercados
      - tiendas por departamento
    - comercios B2C independientes
      - abastecedores
      - farmacias
      - veterinarias
      - suplidores de suplementos nutricionales
      - ferreterías
      - viveros
    - comercios B2B
      - importadores directos
      - fabricantes
      - mayoristas
      - proveedores de logística

3. "**nodos de venta**" (puntos de venta desarrollados en Flutter/Dart), que *serán tanto B2C como B2B*, por ejemplo:
    - aplicaciones móviles:
        - descargables desde Google Play para Android
        - descargables desde Apple App Store para iOS
    - aplicaciones web:
        - suministradas desde la instancia que está hosteando a un nodo secundario,
        - accesibles a través del sub-dominio "tienda.*.com",
        - servidas al comprador como Single-Page-Applications (SPAs)
    - aplicaciones de escritorio:
        - descargables desde Microsoft Store para Windows 11 o superior
        - descargables desde Apple App Store para macOS 15 Sequoia o superior

*...a diferencia de otras plataformas de e-commerce existentes,*
ya sean B2C:

- tipo marketplace, tales como:
  - [Amazon](https://amazon.com/)
  - [AliExpress](https://www.aliexpress.com/)
  - [Temu](https://www.temu.com/)
  - [Shein](https://www.shein.com/)
  - [Ebay](https://www.ebay.com/)
  - [Etsy](https://www.etsy.com/)
  - [Redbubble](https://www.redbubble.com/es/)

- tipo SaaS, tales como:
  - [Shopify](https://www.shopify.com/sell)
  - [WooCommerce](https://woocommerce.com/es/products/)

o sean B2B:

- tipo marketplace, tales como:
  - [Alibaba](https://www.alibaba.com/)
  - [Made-In-China.com](http://made-in-china.com/)
  - [DHgate](https://www.dhgate.com/)
  - [Tradewheel](https://www.tradewheel.com/usa/)
  - [Amazon Wholesale](https://business.amazon.com/en/supplies)
  - [B2Brazil](https://b2brazil.com/)
  - [B2México](https://b2mexico.com/)
  - [B2Chile](https://b2chile.com/)
  - [B2Argentina](https://b2argentina.com.ar/)
  - [B2Colombia](https://b2colombia.com/)
  - [B2India](https://b2india.com/)
  - [B2USA](https://b2usa.com/)

- o tipo SaaS, tales como:
  - [commercetools](https://commercetools.com/)
  - [BigCommerce B2B](https://www.bigcommerce.com/apps/b2b-edition/)
  - [Salesforce Commerce Cloud B2B](https://www.salesforce.com/es/commerce/b2b-ecommerce/)
  - [SAP Commerce B2B](https://www.sap.com/latinamerica/cmp/oth/sap-commerce-cloud-for-b2b/index.html)
  - [Shopify Plus](https://www.shopify.com/plus/solutions/b2b-ecommerce)

### Tipos de Nodos

#### Marketplaces (Nodos Comerciales Primarios)

Su principal función es permitir el descubrimiento de tiendas para los usuarios finales.
Son equivalentes a centros comerciales virtuales.

Los marketplaces estarán interconectados en una red P2P en malla parcial, entre sí, y con varias tiendas.
Éstos tendrán una arquitectura basada en MACH (Microservicios, API-first, Cloud-native, y Headless).

Ésto significa que los marketplaces podrán funcionar, tanto de manera autónoma, sin descubrir a otros marketplaces circundantes geográficamente, o con interconexiones parciales (no es necesario que todos los marketplace a nivel global estén completamente interconectados, para eso ya existe el Internet mismo).

No hace falta que sean conexiones Site-2-Site VPN entre nodos primarios, sino simplemente de comunicación para el descubrimiento de otras tiendas aledañas.

Para facilitar la integración de la red, existirán inicialmente nodos primarios que sean exclusivamente B2C, y otros que sean exclusivamente B2B. Será responsabilidad de los nodos secundarios tener conexiones separadas a cada nodo primario y éstas podrán decidir si su inventario de venta será combinado o si tendrán dos inventarios (uno dedicado para cada segmento).

##### Características

Los nodos secundarios serán aplicaciones:

- diseñadas bajo patrones de microservicios para operar como middleware para garantizar la operabilidad múltiple con diferentes blockchains de tipos:
  - capa 0
    - [Polkadot](https://polkadot.com/developers/)
    - [Avalanche](https://build.avax.network/docs)
    - [Cosmos](https://docs.cosmos.network/)
  - capa 1
    - [Solana](https://solana.com/es/docs)
    - [Cardano](https://docs.cardano.org/)
    - Parachains como [Kusama](https://wiki.polkadot.com/kusama/kusama-getting-started/)
  - capa 2
    - [Starknet](https://www.starknet.io/developers/)
- desarrolladas en Rust para garantizar seguridad en memoria, velocidad y eficiencia
- empaquetadas en imágenes de contenedores Docker/OpenContainer
- desplegadas a clusters de Kubernetes

#### Tiendas (Nodos Comerciales Secundarios)

Cada tienda será un nodo independiente **autoalojado (self-hosted)** que se pueda conectar directamente, tanto a varios nodos primarios, como a varios nodos terciarios (storefronts) para 

La premisa principal de las tiendas será permitir a los comerciantes recuperar la propiedad de los datos de su tienda en línea.

- Recuperando el control de sus datos de inventario
- Recuperando el control de su participación en cuántos marketplaces quiera
- Recuperando el control de sus costos de integración a terceros
- Recuperando el control de sus costos de envíos y entregas de última milla
- Recuperando el control de cuántas utilidades se pagan a los marketplaces
- Recuperando el control de sus mecanismos de pago

##### Características

A diferencia de otros SaaS, donde se necesitan instalar extensiones adicionales, como **[Shopify Marketplace Connect](https://apps.shopify.com/marketplace-connect)**, las tiendas en MeshCommerceChain tendrán ésta funcionalidad *integrada y habilitada por defecto*, permitiendo que cualquier tienda pueda empezar a vender desde el día uno tanto a otros comerciantes (B2B) como al consumidor final (B2C/DTC).

Los nodos secundarios podrán escoger si manejan un único inventario combinado (B2B/B2C) o si manejan dos inventarios separados por cada segmento.

Los nodos además deberán soportar clasificar la disponibilidad de sus existencias para recibir pagos **en tokens crypto o dinero fiat**.

Al tener éste requerimiento en cuenta, será necesario que aquellos comerciantes que decidan aceptar pagos en criptomonedas, ***(si así lo desean)***, asuman la responsabilidad de dividir sus inventarios:

- en **"existencias con precio fiat"**
  - asumiendo que la contabilidad debe realizarse en **fiat**, de manera que los precios se mantengan estables en fiat
  - *cuya convertibilidad de precio a crypto será inherentemente volátil*;
- y en **existencias con precio crypto**
  - asumiendo que la contabilidad debe realizarse en **crypto** por **aparte**, de manera que los precios se mantengan estables en crypto
  - *cuya convertibilidad de precio a fiat será inherentemente volátil*.

Los nodos secundarios serán aplicaciones que serán empaquetadas en imágenes de contenedores Docker/OpenContainer, y podrán ser desplegadas:

- en ambientes locales con conexión a Internet
  - Podman Desktop o Docker Desktop
  - servidores Kubernetes locales (microk8s, k3s, kind, minikube)

- en despliegues a máquinas virtuales (Virtual Private Servers (VPS)) de servicios de cloud, tales como:
  - [Amazon EC2](https://aws.amazon.com/es/ec2/)
  - [Azure Virtual Machines](https://azure.microsoft.com/es-es/products/virtual-machines/)
  - [Google Cloud Compute Engine](https://cloud.google.com/products/compute?hl=es)
  - [IBM Cloud Virtual Servers for VPC](https://www.ibm.com/products/virtual-servers)
  - [DigitalOcean Droplets](https://www.digitalocean.com/products/droplets)
  - [OVHcloud VPS Cloud](https://www.ovhcloud.com/es-es/vps/vps-cloud/)
  - [Hetzner Managed Servers](https://www.hetzner.com/managed-server/)
  - [UpCloud Cloud Servers](https://upcloud.com/products/cloud-servers/)
  - [Vultr Cloud Compute](https://www.vultr.com/products/cloud-compute/)

- como aplicaciones de un solo clic (One-Click Apps) en plataformas como
  - [AWS Lightsail](https://aws.amazon.com/es/lightsail/)
  - [Vultr One-Click Deploy](https://www.vultr.com/marketplace/categories/)
  - [DigitalOcean Marketplace](https://marketplace.digitalocean.com/)
  - [LightNode](https://www.lightnode.com/en-US/product)

#### Mobile & Web Storefronts (Nodos Terciarios)

Son las aplicaciones móviles y web que los clientes usan para interactuar con la red.

Éstos permitirán a los usuarios:

- Conectarse directamente a nodos secundarios (tiendas) si tienen su URL, código QR, o su GUID:
  - Usarán REST API para obtener información general de cada tienda
  - Usarán GraphQL para obtener información detallada de los inventarios en formato JSON

- Conectarse directamente a nodos primarios (marketplaces) si tienen su URL, código QR, o su GUID:
  - Podrán encontrar tiendas suscritas
  - Podrán consultar al marketplace si puede localizar
    - otros marketplaces aledaños
    - otras tiendas aledañas suscritas a otros marketplaces

- Para procesar pagos en crypto, los nodos terciarios se conectan de forma nativa a alguna blockchain como las antes mencionadas.

- Para procesar pagos en fiat, los nodos terciarios se conectan a una página de checkout de alguna pasarela de pago (ej. Stripe, ONVOPay, TiloPay).

- Dependiendo de la configuración del inventario de cada tienda:

  - SI el comerciante tiene únicamente **existencias en precio fiat**, y *el consumidor solamente cuenta con tokens crypto*, ENTONCES el sistema deberá facilitar la convertibilidad de los tokens crypto (venta) a alguna stablecoin (compra), y buscar si existe algún pool de stablecoins disponible en el marketplace más cercano, para que éste también funcione como una **casa de cambio descentralizada** (descentralized exchange), *para que el comercio pueda debitarle el dinero fiat* al exchange dentro del marketplace, y que el marketplace reciba el pago (o exija el débito) de los tokens crypto en su *pool de liquidez*.

  - SI el comerciante tiene únicamente **existencias en precio crypto**, y *el consumidor solamente cuenta con dinero fiat*, ENTONCES el sistema deberá facilitar la convertibilidad del dinero fiat (venta) a algún token crypto (compra), y buscar si existe algún pool de stablecoins disponible en el marketplace más cercano, para que éste también funcione como una **casa de cambio descentralizada** (descentralized exchange), *para que el comercio pueda debitarle los tokens crypto* al exchange dentro del marketplace, y que el marketplace reciba el pago (o exija el débito) del dinero fiat en su *cuenta IBAN mancomunada* (deberá ser administrada y custodiada por los dueños operadores o su representante legal).

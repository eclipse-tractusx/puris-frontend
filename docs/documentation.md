# PURIS Frontend Documentation

## Frontend Installation

### Requirements
To use the PURIS frontend, you need:

- a running [PURIS backend](https://github.com/eclipse-tractusx/puris-backend/)
- a running [Product EDC](https://github.com/catenax-ng/product-edc)
- a running [CX backend service](https://github.com/denisneuling/cx-backend-service)

### Using npm
- Install dependencies using `npm install`

- Start dev mode using `npm run dev`

- Per default, dev mode will send requests to a [PURIS backend](https://github.com/eclipse-tractusx/puris-backend)
  running on `localhost:8081`

- Building the frontend can be done using `npm run build` (to build with dev settings)
  or one of the following modes: local, dev, integration, beta. These modes differ in their
  target backend URLs.

### Using Docker
You can use docker to build an image of the frontend, using `docker build .`
in the main directory of the frontend.

You can also use `docker build --build-arg npm_build_mode=build_mode`
to specify one of the npm modes mentioned in the previous section.


## Frontend Views
In the following, the provided views are described in detail.

### Dashboard
The dashboard displays general information about the number of received and sent requests,
and the number of call-offs currently displayed by the backend.

### Create
The create page is used to create call-offs and persist them into the PURIS backend.

### Manage
In the manage order view, all created call-offs are displayed. They can be deleted from the backend,
or sent to the connected edc, which will publish them using its catalog.

### Connectors
In this view, external connector URLs can be specified, which will be saved by the backend.
The catalog view will use it to display a Connector dropdown.

### Catalog
In this view, an URL for an external EDC can be specified, to consume
its catalog, and view its contents. On each entry, a button is displayed to
start a negotiation request for this element. Note that the requested EDC has to use
the same DAPS as the EDC your PURIS instance is connected to.

### Negotiations
In this view, the states of all started negotiations are displayed. This includes
requests to other EDCs (outgoing), as well as requests to your own EDC, which were sent by
other connectors (incoming).

If a negotiation of an outgoing request succeeded, a button will be displayed for initializing a transfer.

### Transfers
In this view, all EDC data transfers (incoming and outgoing) are displayed.

### Responses
In this view, all received responses from outgoing transfers are displayed. For this view,
your PURIS instance has to be connected to a
[productEDC backend service](https://github.com/denisneuling/cx-backend-service).

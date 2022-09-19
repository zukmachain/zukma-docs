# <b>ZUKMA ENDPOINTS</b>
---

When interacting with the Zukma network via our <a href="https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fws.zukma.org#/explorer" target="_blank"> substrate explorer app </a> or other UIs and programmatic methods, you'd ideally be running your own node (<a href="https://docs.zukma.org/validator-guides/validator/" target="_blank"> text guide </a>). Granted, that's not something everyone wants to do, so convenience trumps ideals in most cases. To facilitate this convenience, Zukma has several public endpoints you can use for your DApps.

## <b>Zukma Tech Archive Node</b>
---
Zukma Tech, the company that develops the Zukma Rust client, maintains an archive node at endpoint `https://rpc.zukma.org/`

To connect to the Zukma Tech node, use the endpoint in your JavaScript DApps like so:
``` javascript
const{ ApiPromise, WsProvider } = require('@polkadot/api')

(async () => {
    const provider = new WsProvider('wss://ws.zukma.org')
    const api = await ApiPromise.create({ provider })
    // ...
```
or in Zukma Substrate Explorer by clicking on the top-left corner of the screen and opening up the LIVE NETWORKS group and selecting Zukma and **via Zukma**

![img](assets/zukma-endpoint.png#center)

<br></br>

<p align=right> Written by Zukma Team </p>

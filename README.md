# Lotus JS Client

The Lotus JS Client is a collection of small JavaScript libraries that you can use to control the [Lotus implementation](https://github.com/filecoin-project/lotus) of [Filecoin](https://filecoin.io/) via it's JSON-RPC API.

# Usage

All of the **low-level** JSON-RPC methods will soon be wrapped for easy access from JavaScript:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Get Version</title>
  </head>
  <body>
    <h1>Get Version</h1>
    <pre></pre>
    <script type="module">
      import LotusRPC from 'https://unpkg.com/@filecoin-shipyard/lotus-client-rpc?module'
      import BrowserProvider from 'https://unpkg.com/@filecoin-shipyard/lotus-client-provider-browser?module'
      import schema from 'https://unpkg.com/@filecoin-shipyard/lotus-client-schema/prototype/testnet-v3.js?module'

      const wsUrl = 'wss://lotus.testground.ipfs.team/api/0/node/rpc/v0'
      const provider = new BrowserProvider(wsUrl)
      const client = new LotusRPC(provider, { schema })

      async function run () {
        const result = await client.version()
        const preEl = document.querySelector('pre')
        preEl.textContent = JSON.stringify(result)
      }
      run()
    </script>
  </body>
</html>
```

[See it running here!](https://bafybeidafp4gkpy5hx6geh3wmbt5h5x4knyw3acjrbatr5xxphdjhmrpwq.ipfs.dweb.link/)

The usage example above connects to a test "local net" running Lotus via a reverse proxy with SSL and CORS enabled, and loads the library as an "ES module" via the unpkg.com CDN.

Here's the same example, but running [entirely off of IPFS](https://bafybeicwfcxfntlfdvikz3vnnlpapgmg5ogwfgqwpwui44z3yhkn4pvcqq.ipfs.dweb.link/) -- individual library dependencies have been bundled and published using [Snowpack](https://www.snowpack.dev/).

Here's a full demo connected to the same test "local net" using React.js + Snowpack: [jimpick/lotus-js-client-snowpac-react-demo](https://github.com/jimpick/lotus-js-client-snowpack-react-demo#readme)

Full API docs are coming soon! Plus examples and tutorials! In the meantime, you can refer to the Lotus source code to see the list of API methods available:

* [api/apistruct/struct.go](https://github.com/filecoin-project/lotus/blob/master/api/apistruct/struct.go)

In addition to the low level methods, we will be building additional higher-level libraries that make coding common tasks easier with a more expressive and idiomatic JavaScript API.

## Documentation

The docs are under heavy development, and are only partially done so far. The source for the docs are in Markdown format in the `docs` directory
in this repo.

The current draft (generated using `mdbook`) has been published to IPFS here:

* https://ipfs.io/ipfs/QmRRp9Y5i6d3Lkf4UbNvnhtaNqyaB4jnALuJ2vcHnVpphL/

## Contributing

Feel free to join in. All welcome. [Open an issue](https://github.com/filecoin-shipyard/js-lotus-client/issues)!

## License

Dual-licensed under [MIT](https://github.com/filecoin-project/lotus/blob/master/LICENSE-MIT) + [Apache 2.0](https://github.com/filecoin-project/lotus/blob/master/LICENSE-APACHE)

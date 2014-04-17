<p align="center">
    <img src="https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-overview.png" />
</p>

## Matrix filtering: overview

Matrix filtering uses a inheritance model to transfer the block or allow status of a cell to a lower precedence cell:

<p align="center">
    <img src="https://raw.githubusercontent.com/gorhill/httpswitchboard/master/doc/img/httpsb-mtxfiltering-overview.png" />
</p>

To use a concrete example, let's take the following URL: `https://www.example.com/image.png`.

The hostname and the type of the request is extracted from the URL:

- Hostname: `www.example.com`
- Type: `image`


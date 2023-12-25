# node-api-bitfinex

Non-official implementation of Bitfinex.com's Exchange API's. Developed for personal use.

For support on using the API's or development issues, please refer to the official API documentation. For questions regarding this package, please consult the code first.

## __PUBLIC API__

```javascript
  const bitfinex=require('node-api-bitfinex');

  const publicAPI=new bitfinex.publicApi();

```

### REST Public Endpoints

| API                | DESCRIPTION                                                                                         |
| :----              | :----                                                                                               |

## __PRIVATE API__

```javascript
  const bitfinex=require('node-api-bitfinexcom');

  const auth = {
    apikey: 'MY_API_KEY',
    secret: 'MY_API_SECRET'
  };

  const privateAPI=new bitfinex.privateApi(auth);

```

### REST Authenticated Endpoints

| API                      | DESCRIPTION                                                                                        |
| :----                    | :----                                                                                              |

## __WEBSOCKET API__

```javascript
  const bitfinex=require('node-api-bitfinex');

  const auth = {
    apikey: 'MY_API_KEY',
    secret: 'MY_API_SECRET'
  };

  const publicAPI=new bitfinex.sockets.publicApi();
  publicAPI.socket._ws.on('initialized', async () => {
    // do your own initialization
  });

  const privateAPI=new bitfinex.sockets.privateApi(auth);
  privateAPI.setHandler('user.order', (method,data,symbol,option) => { updateOrders(method,data,user,api,handler); });

  privateAPI.socket._ws.on('authenticated', async () => {
    const res=await privateAPI.subscribeOrders();
  });

  privateAPI.socket._ws.on('closed', async () => {
    // do something, like clean-up and reconnect
  });

  function updateOrders(method,orders,user,api,handler) {
    // do something
  };

```

### Websocket Public Channels

| API                                                   | HANDLER          | DESCRIPTION |
| :----                                                 | :----            | :---- |

### Socket Authentication

| API                   | DESCRIPTION                                                                                      |
| :----                 | :----                                                                                            |

### Websocket Authenticated Channels

| API                                                   | HANDLER               | DESCRIPTION |
| :----                                                 | :----                 | :---- |

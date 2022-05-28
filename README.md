# Message-RPC

make message between `frame/worker` easier

```js
// frame A

const clientA = new MessageRpc(postMessage, {
  identifier: 'a',
});

clientA.on({
  name: 'frame a',
  create() {
    return true;
  },
});

// frame B
const clientB = new MessageRpc(postMessage, {
  identifier: 'b',
});

const pipe = clientB.connnect('b');

// receive clientA props
pipe.on((props) => {
  props.name; /// frame b
  props.create().then((res) => {
    res; // true
  });
});
```

![CI](https://github.com/MarvelSQ/message-rpc/actions/workflows/CI.yml/badge.svg)

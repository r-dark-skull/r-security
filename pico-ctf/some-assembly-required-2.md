# Some Assembly Required 2

![](/assets_md/Pasted%20image%2020220530094500.png)


# Solution

![](/assets_md/Pasted%20image%2020220530094627.png)

Like previous challenge (Some Assembly Required) it is also a `wasm` file path.

![](/assets_md/Pasted%20image%20202205![](assets_md/Pasted%20image%2020220530094500.png)30094654.png)

## DeObsuficating JS code

![](/assets_md/Pasted%20image%2020220530095557.png)

```js
'use strict';
const _0x6d8f = ["copy_char", "value", "207aLjBod", "1301420SaUSqf", "233ZRpipt", "2224QffgXU", "check_flag", "408533hsoVYx", "instance", "278338GVFUrH", "Correct!", "549933ZVjkwI", "innerHTML", "charCodeAt", "./aD8SvhyVkb", "result", "977AzKzwq", "Incorrect!", "exports", "length", "getElementById", "1jIrMBu", "input", "615361geljRK"];
const _0x5c00 = function(url, whensCollection) {
  /** @type {number} */
  url = url - 195;
  let _0x6d8fc4 = _0x6d8f[url];
  return _0x6d8fc4;
};
(function(data, oldPassword) {
  const toMonths = _0x5c00;
  for (; !![];) {
    try {
      const userPsd = -parseInt(toMonths(200)) * -parseInt(toMonths(201)) + -parseInt(toMonths(205)) + parseInt(toMonths(207)) + parseInt(toMonths(195)) + -parseInt(toMonths(198)) * parseInt(toMonths(212)) + parseInt(toMonths(203)) + -parseInt(toMonths(217)) * parseInt(toMonths(199));
      if (userPsd === oldPassword) {
        break;
      } else {
        data["push"](data["shift"]());
      }
    } catch (_0x4f8a) {
      data["push"](data["shift"]());
    }
  }
})(_0x6d8f, 310022);
let exports;
(async() => {
  const edgeId = _0x5c00;
  let _0x1adb5f = await fetch(edgeId(210));
  let rpm_traffic = await WebAssembly["instantiate"](await _0x1adb5f["arrayBuffer"]());
  let updatedEdgesById = rpm_traffic[edgeId(204)];
  exports = updatedEdgesById[edgeId(214)];
})();
/**
 * @return {undefined}
 */
function onButtonPress() {
  const navigatePop = _0x5c00;
  let params = document[navigatePop(216)](navigatePop(218))[navigatePop(197)];
  for (let i = 0; i < params["length"]; i++) {
    exports[navigatePop(196)](params[navigatePop(209)](i), i);
  }
  exports["copy_char"](0, params[navigatePop(215)]);
  if (exports[navigatePop(202)]() == 1) {
    document["getElementById"](navigatePop(211))[navigatePop(208)] = navigatePop(206);
  } else {
    document[navigatePop(216)](navigatePop(211))["innerHTML"] = navigatePop(213);
  }
}
;
```

**Inspecting JavaScript working**

![](/assets_md/Pasted%20image%2020220530103436.png)

## De-compiling `WASM` code

![](/assets_md/Pasted%20image%2020220530095646.png)

**`WASM` data**

![](/assets_md/Pasted%20image%2020220530100826.png)

```c
xakgK\Ns((j:l9<mimk?:k;9;8=8?=0?>jnn:j=lu\00\00
```

**copy function**
![](/assets_md/Pasted%20image%2020220530104245.png)

**Decoding Flag**

![](/assets_md/Pasted%20image%2020220530110040.png)

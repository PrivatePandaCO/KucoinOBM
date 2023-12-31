# Kucoin Orderbook Maintainer (KucoinOBM)
A fast and reliable orderbook maintainer for kucoin, written in python.

### WIP WarningIt is not COMPLETELY reliable as of now, due to bugs in the base library: [KucoinWrapper](https://github.com/PrivatePandaCO/KucoinWrapper) <br>
However, I do believe this maintainer is pretty good for it's speed, and I'd appreciate any input and contributions to it. <br>
---

<details>
    <summary> Features </summary>

- Reliability
    - This is capable of running forever, with automatic re-subscription to markets, snapshotting, syncing, etc.
    - This is powered by the base library, another lib written by me, which gives it the speed.
- Speed
    - It's powered by the fastest library, so, yeah.
    - Proof of speed? Use it. More? I use the same library in my pump bot and I always have first buy after signal.
- Completely non-blocking in the main thread! I love it.
- Multiple markets: Supports multiple markets, with their snapshots and sync and everything.
- Update Announcer: Announces change in market last price or orderbook through a local domain UNIX socket.
- Message Freq Tracker
    - Tracks the frequency of messages received from the websocket, and logs it.
    - Useful for managing load across multiple sockets.
- `_shutdown_ws` object variable
  - Automatically varies from `True` to `False` based on the status of the websocket.
  - I found this really useful in HFT, where it would use outdated data while the websocket rebooted. Instead just check if this variable is `True` or `False`

</details>

<details>
    <summary> Installation </summary>

As easy as `pip install KucoinOBM`

</details>

<details>
    <summary> Config </summary>

The parameters to be passed in to `KucoinOBM`<br>

- `kc_api_key, kc_api_secret, kc_api_passphrase,`: Self explanatory.
- `symbols`
    - I use this interchangeably with `markets`.
    - The markets to monitor
    - Example: `symbols = ["BTC-USDT", "ETH-USDT"]`
- `id`
    - Type: Anything you want.
    - Used for identifying the instance in logs.
    - Also returned in `get_all_for(symbol)` function.
- `response_address`
    - UNIX domain socket address for update events.
- `logger`
    - Defaults to `pyloggor(project_root="KucoinOBM")`
    - A pyloggor object; check it out [here!](https://pypi.org/project/pyloggor/)
    - This is a library created by me for beautiful logging :)
    - Please note the default logger uses an option `project_root` which MAY slow down logging to about 0.0001 seconds or 0.1 ms for one log call. This occurs due to the stack depth being big.



</details>

<details>
    <summary> TODO </summary>

- Add handling for illegal markets.
- Increase reliability :)
- Increase speed
- Reduce resources consumption

</details>

---

## Appendix

Heyo, just your average good-for-nothing 16 year old backyard programmer here. Check [my site](https://privatepanda.co) instead :)<br>
If you liked this piece of work or it helped you in any way, buy me a coffee and make my day! [Support Me](https://privatepanda.co#patreon)

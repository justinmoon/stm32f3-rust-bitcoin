This demo works with [the F3 board used by embedded-rust book](https://rust-embedded.github.io/book/intro/hardware.html), [the F469 board used by Specter DIY](https://github.com/cryptoadvance/specter-diy/blob/master/docs/shopping.md#discovery-board) and other STM32 boards.

In order to run the demo, first follow setup instructions for [The Embedded Rust Book](https://rust-embedded.github.io/book/intro/install.html).

[The allocator we're using requires the nightly compiler](https://github.com/rust-embedded/alloc-cortex-m/blob/4673f9324233cce93473068e74dc97fa62775367/src/lib.rs#L3). Run the following within this directory:

```
rustup override set nightly
```

You'll need two terminals.

### Supported boards

| Board         | OpenOCD conf              | Memory map      |
|---------------|---------------------------|-----------------|
| F3 family     | f3.openocd.cfg            | f3.x            |
| F469          | f469.openocd.cfg          | f469.x          |
| STM32F407VET6 | STM32F407VET6.openocd.cfg | STM32F407VET6.x |

### Terminal 1:

Run in the terminal:

```
openocd -f <OpenOCD conf>
```

The name of the file `<OpenOCD conf>` can be found in the section `Supported boards`.

### Terminal 2

Run in the terminal:

```
X=<Memory map> cargo run --release
```

The name of the file `<Memory map>` can be found in the section `Supported boards`.

This should drop "terminal 2" into a gbd debugging session. Type `continue` and hit enter, twice.

In "terminal 1" you should see the following:

```
Seed WIF: L1HKVVLHXiUhecWnwFYF6L3shkf1E12HUmuZTESvBXUdx3yqVP1D
Address: bc1qpx9t9pzzl4qsydmhyt6ctrxxjd4ep549np9993
```

If you'd like to learn more, check out the [embedded-rust book](https://rust-embedded.github.io/book/intro/index.html) which this example is based on.

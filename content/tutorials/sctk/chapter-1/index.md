+++
title = "SCTK Chapter 1"
description = "SCTK tutorial chapter 1"
weight = 0
template = 'chapter.html'
+++


## Connecting to the wayland server

For a wayland client to do anything meaningful it must first connect to a wayland compositor (server).

```rust
extern crate smithay_client_toolkit as sctk;

use sctk::reexports::client::Display;

fn main() {
    let (display, event_queue) =
        Display::connect_to_env().expect("Failed to connect to the wayland server.");
}
```

`Display` is an object reexported from the [wayland-client](https://github.com/Smithay/wayland-rs/tree/master/wayland-client) crate that represents
our connection to the wayland compositor.<br>
`EventQueue` is an event queue for wayland protocol messages. By dispatching the messages inside the queue we can 'talk' to the compositor.

The `Display::connect_to_env()` function on a successful call returns to us both a  `Display` and `EventQueue` object. These objects are
used to communicate with the wayland server. We will use these two wayland objects to create other wayland objects.<br>

A `Mido` message is a Python object with methods and attributes.
The attributes will vary depending on message type.

```python
mido.Message('note_on')
Message('note_on', channel=0, note=0, velocity=64, time=0)
```

All attribute defaults to 0.
The velocity defaults to 64.
Data defaults to `()`.


# Character Atlas 連携形式（仮）

> **これは受け渡し元のプロトタイプです。** Character Atlas側の受け入れ機能はまだ実装されていません。

## Export shape

```json
{
  "format": "oshi-motion-atlas-bridge",
  "version": 1,
  "sourceApp": "Oshi Motion Studio",
  "character": {
    "name": "推しの名前",
    "canvas": { "width": 750, "height": 1000 },
    "layers": [
      {
        "id": "id-...",
        "name": "右目・開",
        "src": "data:image/png;base64,...",
        "x": 375,
        "y": 260,
        "scale": 1,
        "rotation": 0,
        "pivotX": 0.5,
        "pivotY": 0.5,
        "opacity": 1,
        "role": "eyeRight",
        "visible": true,
        "locked": false,
        "flipX": false
      }
    ],
    "settings": {
      "breathe": true,
      "sway": true,
      "blink": true,
      "hair": true,
      "arms": true,
      "intensity": 45,
      "speed": 100,
      "bg": "#f6eff3"
    }
  }
}
```

Coordinates use a logical 750 × 1000 canvas. Layer entries are in **back-to-front order**. `src` is an embedded PNG/JPEG data URL; no external asset storage is needed for import. `pivotX`/`pivotY` are normalized coordinates in the component image. `role` identifies the animation channel.

If Character Atlas imports this format in the future, it should validate the file size, media type, count of layers, coordinates, roles, and image decoding before saving. It must not interpret untrusted JSON as executable code.

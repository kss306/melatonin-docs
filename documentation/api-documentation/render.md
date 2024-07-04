---
description: All render functions are only useable in the paint callback
---

# Render

### Line

Renders a line from point x1, y1 to point x2, y2

```lua
render.line(int: x1, int: y1, int: x2, int: y2, int: r, int: g, int: b, int: a, int: thickness)
```

***

### Rect

Renders a rectangle

```lua
render.rect(int: x, int: y, int: width, int: height, int: r, int: g, int: b, int: a)
```

***

### Rect outline

Renders a rectangle outline

```lua
render.rect_outline(int: x, int: y, int: width, int: height, int: r, int: g, int: b, int: a)
```

***

### Circle

Renders a circle

```lua
render.circle(int: x, int: y, int: radius, int: r, int: g, int: b, int: a, int: segments)
```

***

### Circle outline

Renders a circle outline

```lua
render.circle_outline(int: x, int: y, int: radius, int: r, int: g, int: b, int: a, int: segmets)
```

***

### Triangle

Renders a triangle

```lua
render.triangle(int: x1, int: y1, int: x2, int: y2, int: x3, int: y3, int: r, int: g, int: b, int: a)
```

***

### Triangle outline

Renders a triangle outline

```lua
render.triangle_outline(int: x1, int: y1, int: x2, int: y2, int: x3, int: y3, int: r, int: g, int: b, int: a)
```

***

### Text

Renders text

```lua
render.text(int: x, int: y, int: r, int: g, int: b, int: a, int: font, bool: scale, string: text)
```

***

### Gradient

Renders a rectangle with gradient colors

```lua
render.gradient(int: x, int: y, int: width, int: height, int: r1, int: g1, int: b1, int: a1, int: r2, int: g1, int: b1, int: a1, bool: left_to_right)
```

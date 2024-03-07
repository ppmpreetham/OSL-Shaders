# OSL-Shaders
An attempt to recreate the nodes in blender using OSL

## Working principe of mix node

This is pretty similar to linearly mixing any two different things with a mix factor.
For an example, in math, if we want to mix two functions $f(x)$ and $g(x)$, we usually do it by taking a mix factor $t$, and the output is going to be a new function $h(x) = tf(x)+(1-t)g(x)$. Here, $0\lt t\lt 1$.

![2 functions](https://github.com/Preetham-ai/OSL-Shaders/assets/75422607/6e09eb74-0e7a-4494-b296-d4703f20689b)

## Texture Coordinate Node

The Texture coordinate node provides the:

- Object
- Normal
- UV
- Incident
- Reflection

### Working principle of Reflection node

We can use this formula to derive the reflection node using the incident node.

$\mathbf{r} = \mathbf{i} - 2 \mathbf{n}(\mathbf{n} \cdot \mathbf{i})$
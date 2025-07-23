# OSL-Shaders
An attempt to recreate the nodes in blender using OSL

## Mix nodes

This makes use of `Linear Interpolation (LERP)` to mix two values together. The mix factor $t$ is used to determine how much of each value to take.
For an example, in math, if we want to mix two functions $f(x)$ and $g(x)$, we usually do it by taking a mix factor $t$, and the output is going to be a new function $h(x) = tf(x)+(1-t)g(x)$. Here, $0\lt t\lt 1$.

![2 functions](https://github.com/Preetham-ai/OSL-Shaders/assets/75422607/6e09eb74-0e7a-4494-b296-d4703f20689b)

## Texture Coordinate Node

The Texture coordinate node provides the:

- Object
- Normal
- UV
- Incident
- Reflection

### Reflection Node

We can use this formula to derive the reflection node using the incident node.

$\mathbf{r} = \mathbf{i} - 2 \mathbf{n}(\mathbf{n} \cdot \mathbf{i})$

## RGB to BW Node

Took the cofiguration of the OpenColorIO on the luma line in https://git.blender.org/gitweb/gitweb.cgi/blender.git/blob_plain/HEAD:/release/datafiles/colormanagement/config.ocio.

This is the same as taking the dot product between ```R,G,B``` and ```0.2126,0.7152,0.0722```. This would yield us a result in a greyscale mode in which all the R,G,B channels are given the color $0.2126*R + 0.7152*G + 0.0722*B$.

## Blackbody Shader

This doesn't look like the Blender's Blackbody node but produces quite similar results.

According to the [Stefan-Boltzmann law](https://en.wikipedia.org/wiki/Stefan%E2%80%93Boltzmann_law), hotter objects emit more high-frequency radiation compared to cooler objects. As blue light has a higher frequency than red light, hot objects tend to emit bluish light, warm objects emit white light (a combination of blue and red), and cool objects emit red light.

Used the algorithm by [Tanner Helland](https://tannerhelland.com/2012/09/18/convert-temperature-rgb-algorithm-code.html)

## MapRange Node
### Linear Interpolation (LERP)
This makes use of the linear interpolation formula to map a value from one range to another. The formula is as follows:

$$
\text{Result} = \text{ToMin} + \left(\frac{x - \text{FromMin}}{\text{FromMax} - \text{FromMin}}\right) \times (\text{ToMax} - \text{ToMin})
$$

Where:

* `x` is the input
* `FromMin` and `FromMax` define the **original** range
* `ToMin` and `ToMax` define the **new** target range
* Result is the mapped value
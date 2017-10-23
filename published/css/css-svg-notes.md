# CSS Notes

## SVG in CSS backgrounds

- using svgs allows using css image properties
- good because no clutter with svg in markup

- svg in background can be cached
- using image sprites and embedding svg as a data URI can also improve performance

## CSS masks
- only support for newest browsers

The mask property creates a mask that is then applied to an element
  - where the mask is opaque, the underlying image shows
  - where it is transparent, the underlying image is hidden, or masked.

syntax:
	```css
		.icon {
		background-color: red;
		-webkit-mask-image: url(icon.svg);
		mask-image: url(icon.svg);
		}
	```
 The fill of the icon in the SVG doesn't matter because it masks the background layer which is the color red.
  Therefore, the result is a red icon. For webkit, I'm using the prefix.

Your background can be a color, image, gradient -- whatever.

You can use the mask shorthand like the background shorthand:

.icon {
    background-color: red;
    -webkit-mask:  url(icon.svg) no-repeat 50% 50%;
    mask: url(icon.svg) no-repeat 50% 50%;
}



## CSS filters

You can apply Photoshop-like effects to DOM elements with CSS filters. Filters can be chained, with each filter acting on the result of its predecessor.

<svg
    xmlns="http://www.w3.org/2000/svg"
    width="24"
    height="24"
    viewbox="0 0 24 24">
    <path fill="red" d="M12 21.35l-1.45-1.32c-5.15-4.67-8.55-7.75-8.55-11.53 0-3.08 2.42-5.5 5.5-5.5 1.74 0 3.41.81 4.5 2.09 1.09-1.28 2.76-2.09 4.5-2.09 3.08 0 5.5 2.42 5.5 5.5 0 3.78-3.4 6.86-8.55 11.54l-1.45 1.31z"/>
</svg>
.icon-blue {
    -webkit-filter: hue-rotate(220deg) saturate(5);
    filter: hue-rotate(220deg) saturate(5);
}
In this example, the icon has a pure red fill set in the SVG. The hue-rotate filter rotates the hue 220 degrees around the rgb color wheel. This makes the icon blue. The algorithm for hue-rotation isn't extremely accurate, so although the output should be pure blue it’s a little off. One way to fix this and boost up the color to full saturation is to add a saturation filter. In the example, I added an arbitrarily large value of five to the chain, which increases the saturation by 500%.

By chaining filters together, you can make many colored icons from one colored icon input. With different combinations of hue-rotate, invert, brightness, and saturation filters, I've created the ROYGBIV rainbow spectrum and some other basic colors like cyan and magenta.
https://codepen.io/noahblon/post/coloring-svgs-in-css-background-images

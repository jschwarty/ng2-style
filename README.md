# ng2-style

## :host
Using:
```css
:host .the-class
```
Transpiles to:
```css
[_nghost-] .the-class
```
which can lead to bleed down to child components  
*Note that this is a bug, will be fixed*  
  
Using:
```css
.the-class
```
Transpiles to
```css
.the-class[_ngcontent-]
```
and since `[_ngcontent-]` gets added to all template children there is no bleed of .test down to child components.


## :host-context
Using:
```css
:host-context(.small) .the-class
```
Transpiles to
```css
[_nghost-].small .the-class, .small [_nghost-] .the-class
```
which can lead to bleed down to child components

So how do you leverage `host-context` to match up the tree but still scope to the template?

## /deep/
support for deep is there (>>> or /deep/) after beta9 but it's deprecated (real solution is css variables, but not supported yet)


## :content
Talk about using :content too  
Content is referred to as "content projected"


## TODO
cover emulation modes  
Angular emulated is "shim" not "transpile"
"goal of emulation is style encapsulation, not specifically shadow-dom spec match". Performance is the most important.  

Talk about theming as well (use deep selector, but material design does theming so check that out). Tell people they can learn more about it here..

Shared styles, if you bring in shared css into your template css Angular is going to be making duplicate css in the DOM. 
If you want to share rules, you can put them in `<head>` and just use them in your component template css (when in Emulation mode)
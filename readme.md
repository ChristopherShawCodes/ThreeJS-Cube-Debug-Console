# Three.js Journey

## Setup
`npm install`
`npm run dev `
```
--------------------------------------------


This is a 3d rendering of a cube with a debug gui hidden with 'h'

cube can be edited via the debug consonsole

-change color (cube spins on color change)

-show wireframe (remove facing)

-change position

-change camera angle 


            
  --------------------------------------          
         
            
            
            Debug Ui 
            
            
-----IMPORTING-----

lil.GUI 

https://www.npmjs.com/package/lil-gui

`npm install --save lil-gui `

`import GUI from 'lil-gui'`

`const gui = new GUI()`

-------------------------------------------

Elements that can be added to the panel 

Range —for numbers with minimum and maximum value

Color —for colors with various formats

Text —for simple texts

Checkbox —for booleans (true or false)

Select —for a choice from a list of values

Button —to trigger functions

Folder —to organize your panel if you have too many elements

------------------------------------------------

        Adding to the Debug Panel 

use gui.add(1stParameter,2ndParameter)

-1stParameter is an object 

-2ndParameter is the property you want to tweak 

`gui.add(mesh.position, 'y' )`

From here you can add in additional parameters to set limitations

-minimum

-maximum

-step (precision)

`gui.add(mesh.position, 'y').min(- 3).max(3).step(0.01)`

//Chaining 

`gui
    .add(mesh.position, 'y')
    .min(- 3)
    .max(3)
    .step(0.01)`

//Shorthand 
`gui.add(mesh.position, 'y', - 3, 3, 0.01)`


//You can also rename a target value 

   ` gui
    .add(mesh.position, 'y')
    .min(- 3)
    .max(3)
    .step(0.01)
    .name('elevation')`

    In the debug console this value will now be known as 'elevation' 

-----------------------------------------------------------

You can add functions within the GUI 

`const parameters = {
    spin: () =>
    {
        gsap.to(mesh.rotation,{duration: 1, y: mesh.rotation.y + Math.PI * 2})
    }
}


gui 
    .addColor(material, 'color')
    .onChange(()=>{
        parameters.spin()
    })
    .name('Cube-color')`

------------------------------------------------------------

To make the GUI 'hideable'

`window.addEventListener('keydown',(event =>
    {
    if(event.key === 'h')
    {
        if(gui._hidden)
            gui.show()
        else
            gui.hide()
    }
}
))`



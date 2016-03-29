# SASS Toolbox
Simple but functional SASS stuff. To make your life easier.

Just copy whatever you need from **sass-toolbox.scss** and use it in your project.

## Documentation
| Type  | Name       | Description                         |
| :---: | :--------: | :---------------------------------- |
| mixin | breakpoint | Breakpoints manager                 |
| mixin | clearfix   | Standard clearfix for float layouts |
| mixin | flow-text  | Smoothly scaled font-size           |

### breakpoint()
With this **single mixin** you can maintain responsiveness of your styles easly:  
@mixin  
breakpoint($breakpoint-name, $breakpoint-type)

####Setup
Prepare global map with breakpoints (this is default):  
[ string: integer ]  
[ "breakpoint-name": break-screen-width ]
```sass
$breakpoints: (
    "xs": 0,
    "sm": 544,
    "md": 768,
    "lg": 992,
    "xl": 1200
);
```
! Width at which each breakpoint starts is set in **px**

####Example usage
Set **.container -> width** to **100%** when **screen width** is **smaller/equal 767px**:
```sass
@include breakpoint("sm", "and-down") {
    .container {
        width: 100%;
    }
}
```

### clearfix()
Apply micro clearfix for standard float layout:  
@mixin  
clearfix()

####Example usage
Clearfix **.container** that has two floated children inside - **.left** and **.right**:
```sass
.container {
    @include clearfix();
    
    .left {
        float: left;
    }
    
    .right {
        float: right;
    }
}
```

### flow-text()
Creates breakpoints for smoothly responsive font-size:  
@mixin  
flow-text($size-start, $size-end, $unit, $breakpoint-final: 1000, $steps: 10, $breakpoint-base: 361)

####Example usage 1
Scale **h1** from **32px** to **60px** on screen-width **320px - 1000px** with **10 steps**:
```sass
h1 {
    @include flow-text(32, 60, "px");
}
```

####Example usage 2
Scale **p** from **1rem** to **3rem** on screen-width **544px - 1200px** with **5 steps**:
```sass
p {
    @include flow-text(1, 3, "rem", 1200, 5, 544);
}
```
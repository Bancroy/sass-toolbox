# SASS Toolbox
Simple but functional SASS stuff. To make your life easier.

Just copy whatever you need from **sass-toolbox.scss** and use it in your project.

## Documentation
| Type  | Name         | Description                         |
| :---: | :----------: | :---------------------------------- |
| mixin | breakpoint   | Breakpoints manager                 |
| mixin | clearfix     | Standard clearfix for float layouts |
| mixin | flexbox-grid | Flexbox based fluid grid            |
| mixin | flow-text    | Smoothly scaled font-size           |

### breakpoint()
With this **single mixin** you can maintain responsiveness of your styles easly:  
@mixin  
breakpoint($breakpoint-name, $breakpoint-type, $breakpoint-between)

#### Setup
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

#### Example usage 1
Set **.container -> width** to **100%** when **screen width** is **smaller/equal 767px**:
```sass
@include breakpoint("sm", "and-down") {
    .container {
        width: 100%;
    }
}
```

#### Example usage 2
Set **.container -> width** to **50%** when **screen width** is **between 992px and 1199px**:
```sass
@include breakpoint("lg", "only") {
    .container {
        width: 50%;
    }
}
```

#### Example usage 3
Set **.container -> width** to **90%** when **screen width** is **between 544px and 1199px**:
```sass
@include breakpoint("sm", "between", "lg") {
    .container {
        width: 90%;
    }
}
```

#### Example usage 4
Set **.container -> width** to **40%** when **screen width** is **bigger/equal 768px**:
```sass
@include breakpoint("md", "and-up") {
    .container {
        width: 40%;
    }
}
```

### clearfix()
Apply micro clearfix for standard float layout:  
@mixin  
clearfix()

#### Example usage
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

### flexbox-grid()
Create flexbox based grid with fluid widths:  
@mixin  
flexbox-grid($container-width: 1200, $columns: 16, $gutter-width: 20, $unit: "px")

#### Dependencies
* breakpoint()

#### Setup
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

#### Example usage 1
Create grid with **.container** max-width set to **1000px** basing on **10 columns** with **2rem gutter**:
```sass
@include flexbox-grid(1000, 10, 2, "rem");
```

```html
<div class="container">
    <div class="row">
        <div class="column xs-10 sm-8 md-6 lg-4 xl-2"></div>
        <div class="column xs-10 sm-2 md-4 lg-2 offset-lg-2 xl-8"></div>
    </div>
    <div class="row">
        <div class="column xs-10 md-5"></div>
        <div class="column xs-10 md-5"></div>
    </div>
</div>
```

### flow-text()
Creates breakpoints for smoothly responsive font-size:  
@mixin  
flow-text($size-start, $size-end, $unit, $breakpoint-final: 1000, $steps: 10, $breakpoint-base: 361)

#### Example usage 1
Scale **h1** from **32px** to **60px** on screen-width **320px - 1000px** with **10 steps**:
```sass
h1 {
    @include flow-text(32, 60, "px");
}
```

#### Example usage 2
Scale **p** from **1rem** to **3rem** on screen-width **544px - 1200px** with **5 steps**:
```sass
p {
    @include flow-text(1, 3, "rem", 1200, 5, 544);
}
```
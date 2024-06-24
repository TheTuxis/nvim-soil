# nvim-soil
### Soil for a plant (UML)
*nvim-soil is a minimal plugin written in Lua for Plant UML.*

## Caveats
- `Java` and `nsxiv` (default but editable) are required to be installed in order to use this plugin.
- `plantuml` is optional to be installed or used in jar format.
- Recommended for Plant UML syntax highlighting [nvim-nyctophilia colorscheme](https://github.com/javiorfo/nvim-nyctophilia)
- This plugin has been developed on and for Linux following open source philosophy.

## Installation
`Packer`
```lua
use 'javiorfo/nvim-soil'

-- Optional for puml syntax highlighting:
use 'javiorfo/nvim-nyctophilia'
```
`Lazy`
```lua
{ 
    'javiorfo/nvim-soil',

    -- Optional for puml syntax highlighting:
    dependencies = { 'javiorfo/nvim-nyctophilia' },

    lazy = true,
    ft = "plantuml",
    opts = {
        -- If you want to change default configurations
        
        -- If you want to use Plant UML jar version instead of the install version
        puml_jar = "/path/to/plantuml.jar",
        
        -- If you want to customize the image showed when running this plugin
        image = {
            darkmode = false, -- Enable or disable darkmode 
            format = "png", -- Choose between png or svg
    
            -- This is a default implementation of using nsxiv to open the resultant image
            -- Edit the string to use your preferred app to open the image (as if it were a command line)
            -- Some examples:
            -- return "feh " .. img
            -- return "xdg-open " .. img
            execute_to_open = function(img) 
                return "nsxiv -b " .. img
            end
        }
    }
}
```

## Configuration
#### This is OPTIONAL
- If `plantuml` is installed you don't need any extra set up. But if wanted to use **plantuml jar version** you can set it up.
- The default image format is **PNG**. 
- The default Plant UML **darkmode** is set to **false**. 
- Optional configuration in *init.vim* or *init.lua*:
```lua
require'soil'.setup{ 
    -- If you want to use Plant UML jar version instead of the install version
    puml_jar = "/path/to/plantuml.jar",
    
    -- If you want to customize the image showed when running this plugin
    image = {
        darkmode = false, -- Enable or disable darkmode 
        format = "png", -- Choose between png or svg

        -- This is a default implementation of using nsxiv to open the resultant image
        -- Edit the string to use your preferred app to open the image (as if it were a command line)
        -- Some examples:
        -- return "feh " .. img
        -- return "xdg-open " .. img
        execute_to_open = function(img) 
            return "nsxiv -b " .. img
        end
    }
}
```

## Usage
- Open any yourfile.plantuml, yourfile.pu or yourfile.puml which you want to process and use `:Soil` Neovim command line to generate and open yourfile.png with graphical output. Press `q` to quit the image viewer.
- Everytime you update a Plant UML file and run `:Soil`, you'll get an updated image.
- The generated image is saved in the same location that your Plant UML file.
- To open the generated image without run Plant UML again use `:SoilOpenImg` command.

## Screenshots
### Simple use

<img src="https://github.com/javiorfo/img/blob/master/nvim-soil/soil2.gif?raw=true" alt="soil"/>

**NOTE:** The colorscheme **nox** from [nvim-nyctophilia](https://github.com/javiorfo/nvim-nyctophilia) is used in this image.

---

### Donate
- **Bitcoin** [(QR)](https://raw.githubusercontent.com/javiorfo/img/master/crypto/bitcoin.png)  `1GqdJ63RDPE4eJKujHi166FAyigvHu5R7v`
- [Paypal](https://www.paypal.com/donate/?hosted_button_id=FA7SGLSCT2H8G)

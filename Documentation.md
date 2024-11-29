# Eclipse Library
This documentation is for the stable release of Eclipse Library.

## Booting the Library
```lua
local EclipseLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/Eclipes12/Eclipse-Library/refs/heads/main/source')))()
```


## Creating a Window
```lua
local Window = EclipseLib:MakeWindow({
    Name = "Eclipse UI",
    HidePremium = false,
    SaveConfig = true,
    ConfigFolder = "EclipseConfig",
    IntroEnabled = true,
    IntroText = "Welcome to Eclipse UI",
    IntroIcon = "rbxassetid://4483345998", -- Change to a valid image asset ID
    Icon = "rbxassetid://4483345998",     -- Change to a valid image asset ID
    CloseCallback = function() 
        print("Window closed")
    end
})
-- Store the window element in EclipseLib
EclipseLib.Elements.Window = Window
```

## Creating a Tab
```lua
local Tab = Window:MakeTab({
    Name = "Main Tab",
    Icon = "rbxassetid://4483345998",  -- Change to a valid image asset ID
    PremiumOnly = false
})

-- Store the tab element
EclipseLib.Elements.MainTab = Tab
```

## Creating a Section
```lua
local Section = Tab:AddSection({
    Name = "Main Section"
})

-- Store the section element
EclipseLib.Elements.MainSection = Section
```
You can add elements to sections the same way you would add them to a tab normally.

## Notifying the user
```lua
EclipseLib:MakeNotification({
    Name = "Welcome",
    Content = "This is your Eclipse UI!",
    Image = "rbxassetid://4483345998",  -- Change to a valid image asset ID
    Time = 5
})
```
## Creating a Button
```lua
Tab:AddButton({
    Name = "Click Me!",
    Callback = function()
        print("Button clicked!")
    end    
})

-- Store button in EclipseLib
table.insert(EclipseLib.Elements, "Click Me! Button")
```

## Creating a Checkbox toggle
```lua
local Toggle = Tab:AddToggle({
    Name = "Enable Feature",
    Default = false,
    Callback = function(Value)
        print("Toggle state: " .. tostring(Value))
    end    
})

-- Store toggle in EclipseLib
EclipseLib.Elements.Toggle = Toggle
```

### Change UI Element Values (Optional)
```lua
-- Example of changing the slider value
Slider:Set(75)

-- Example of changing the color picker's value
ColorPicker:Set(Color3.fromRGB(0, 255, 0))

-- Example of setting the toggle to true
Toggle:Set(true)
```

## Creating a Slider
```lua
-- Creating a Slider inside the Section
local Slider = Tab:AddSlider({
    Name = "Adjust Value",  -- The name displayed above the slider
    Min = 0,                -- Minimum value of the slider
    Max = 100,              -- Maximum value of the slider
    Default = 50,           -- Default value (initial value when the UI is opened)
    Color = Color3.fromRGB(255, 255, 255),  -- Color of the slider
    Increment = 1,          -- The increment step for the slider (how much value changes when dragging)
    ValueName = "Units",    -- The unit name next to the value (e.g., "Units")
    Callback = function(Value)
        -- This function is called when the slider is changed
        print("Slider value: " .. Value)
    end    
})

-- Store the slider element in EclipseLib for later use (optional)
EclipseLib.Elements.Slider = Slider
```

## Creating an Adaptive Input
```lua
-- Creating a Textbox inside the Section
Tab:AddTextbox({
    Name = "Input Text",         -- The name displayed above the textbox
    Default = "Enter here",      -- Default text shown in the textbox
    TextDisappear = true,        -- Makes the text disappear after the textbox loses focus
    Callback = function(Value)   -- The function that gets triggered when the value changes
        print("Textbox input: " .. Value)
    end    
})
```

## Creating a Keybind
```lua
-- Creating a Keybind inside the Section
local Keybind = Tab:AddBind({
    Name = "Press Key",         -- The name displayed above the keybind
    Default = Enum.KeyCode.E,   -- Default key to be assigned (Enum.KeyCode.<Key>)
    Hold = false,               -- If set to true, the action will keep triggering while the key is held
    Callback = function()       -- The function that gets triggered when the key is pressed
        print("Key pressed!")
    end    
})
```

## Creating a Dropdown menu
```lua
-- Creating a Dropdown inside the Section
local Dropdown = Tab:AddDropdown({
    Name = "Select Option",      -- The name of the dropdown
    Default = "Option 1",       -- The default selected option
    Options = {"Option 1", "Option 2", "Option 3"},  -- The list of options in the dropdown
    Callback = function(Value)   -- Function that runs when the user selects an option
        print("Selected: " .. Value)
    end    
})
```

# Finishing your script (REQUIRED)
The below function needs to be added at the end of your code.
```lua
EclipseLib:Init()
```

## Destroying the Interface
```lua
EclipseLib:Destroy()
```

# Lunarion UI Library

<p align="center">
  <strong>A customizable Roblox UI library by Centurion Softworks.</strong>
</p>

<p align="center">
  Built for developers who want a flexible, modern, and feature-rich interface.
</p>

---

## Overview

**Lunarion** is a Roblox LuaU UI library developed and maintained by **Centurion Softworks**.

It provides a structured API for creating windows, tabs, sections, and interactive UI elements. It also includes customization options, themes, notifications, configuration utilities, and additional integrations.

## Features

- **Window Management** — Create and customize UI windows.
- **Tabs and Sections** — Organize interfaces into structured layouts.
- **Interactive Elements** — Buttons, toggles, sliders, dropdowns, and more.
- **Keybinds** — Add keyboard interactions to your interface.
- **Color Pickers** — Allow users to customize colors.
- **Theme System** — Create, register, and switch between themes.
- **Notifications** — Display notifications through the library.
- **Configuration Support** — Save and load configurations when supported by the runtime.
- **Key Systems** — Add key-based access systems.
- **Analytics** — Optional local analytics functionality.
- **Icon Integrations** — Support for multiple icon collections.

---

## Installation

Load Lunarion using the following loader:

```lua
local Lunarion = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/CenturionSoftworks/Lunarion/main/Lunarion.lua"
))()
```

> **Note:** This loader requires an environment that supports `loadstring` and HTTP requests. These are not standard capabilities available to ordinary Roblox LocalScripts.

---

## Quick Start

```lua
local Lunarion = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/CenturionSoftworks/Lunarion/main/Lunarion.lua"
))()

local Window = Lunarion:MakeWindow({
    Name = "My Lunarion Interface",
    HidePremium = false,
    SaveConfig = true
})

local MainTab = Window:MakeTab({
    Name = "Main",
    Icon = "home"
})

local MainSection = MainTab:AddSection({
    Name = "Main Controls"
})

MainSection:AddButton({
    Name = "Example Button",
    Callback = function()
        print("Hello from Lunarion!")
    end
})

MainSection:AddToggle({
    Name = "Example Toggle",
    Default = false,
    Callback = function(Value)
        print("Toggle:", Value)
    end
})

MainSection:AddSlider({
    Name = "Example Slider",
    Min = 0,
    Max = 100,
    Default = 50,
    Increment = 1,
    ValueName = "Value",
    Callback = function(Value)
        print("Slider:", Value)
    end
})
```

---

## UI Elements

Lunarion provides several interface elements.

| Element | Description |
|---|---|
| `AddButton` | Creates a clickable button. |
| `AddToggle` | Creates an on/off toggle. |
| `AddSlider` | Creates a numeric slider. |
| `AddDropdown` | Creates a selection dropdown. |
| `AddBind` | Creates a keybind control. |
| `AddColorpicker` | Creates a color selection control. |
| `AddLabel` | Creates a text label. |
| `AddParagraph` | Creates a paragraph element. |
| `AddWarningLabel` | Creates a warning-style label. |
| `AddApproveLabel` | Creates an approval-style label. |
| `AddCustomLabel` | Creates a customizable label. |

---

## Built-in Themes

Lunarion includes the following built-in themes:

- Lunarion
- Default
- Amethyst
- Ocean
- Rose
- Emerald
- Light
- Sakura

You can also register your own themes through the theme API.

---

## Icon Integrations

Lunarion includes integrations for multiple icon collections:

- Lucide
- Solar
- Gravity UI
- Footagesus/Icons

Material and Feather aliases are also supported through Lucide mappings.

---

## Additional Features

### Notifications

Display notifications through Lunarion's notification functionality.

### Key Systems

Create key-based access systems using the library's key system functionality.

### Themes

Register and apply custom themes to customize the appearance of your interface.

### Configuration

Save configuration data when the execution environment provides the required file APIs.

### Analytics

Lunarion includes optional local analytics functionality. Analytics are disabled by default.

---

## Documentation

For the full API reference, examples, and additional information, see:

**[Documentation.md](Documentation.md)**

---

## Project Structure

```text
Lunarion/
├── Lunarion.lua
├── README.md
├── Documentation.md
├── LICENSE
└── .gitignore
```

---

## Requirements

Some functionality depends on the execution environment.

| Capability | Purpose |
|---|---|
| `loadstring` | Loads the library dynamically. |
| `game:HttpGet()` | Retrieves the library source. |
| File APIs | Enables configuration persistence. |
| GUI APIs | Supports environment-specific interface placement. |
| Clipboard APIs | Enables clipboard-related functionality. |

These capabilities are environment-dependent and are not all standard Roblox APIs.

---

## Credits

Developed and maintained by:

**Centurion Softworks**

Third-party projects and icon integrations:

- [Lucide](https://lucide.dev/)
- [Solar Icons](https://solar-icons.com/)
- [Gravity UI](https://gravity-ui.com/)
- [Footagesus/Icons](https://github.com/Footagesus/Icons)

Please refer to their respective licenses for usage and attribution requirements.

---

## License

Lunarion is distributed under the MIT License.

See the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <strong>Lunarion UI Library</strong><br>
  Centurion Softworks
</p>
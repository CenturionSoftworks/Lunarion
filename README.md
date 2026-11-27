
# Centurion Softworks — Lunarion UI Library

![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Language](https://img.shields.io/badge/Language-LuaU-blue.svg)
![Platform](https://img.shields.io/badge/Platform-Roblox-red.svg)
![Developer](https://img.shields.io/badge/Developer-Centurion%20Softworks-black.svg)

**Lunarion** is a Roblox LuaU UI library developed and maintained by **Centurion Softworks**.

Designed for developers who want a flexible, customizable, and feature-rich interface system for their Roblox scripts.

---

## About Lunarion

Lunarion is a UI framework whose API design is based on the **Orion UI Library API**.

It maintains the familiar Orion-style development structure while introducing additional functionality, customization options, and integrations.

Its architecture follows a simple hierarchy:

- Window
- Tabs
- Sections
- Elements

Lunarion is an independent implementation and is not an official Orion UI Library release.

## Features

- Customizable interface windows.
- Multiple tabs and sections.
- Buttons and toggles.
- Sliders and dropdowns.
- Keybinds.
- Color pickers.
- Labels and paragraphs.
- Custom themes.
- Notification system.
- Configuration saving and loading.
- Homeboard dashboard.
- Search functionality.
- Responsive interface layouts.
- Icon library integrations.
- Optional analytics and telemetry.
- Key verification interface.
- Window resizing and visibility controls.

## Supported UI Elements

| Element | API Method |
|---|---|
| Button | AddButton |
| Toggle | AddToggle |
| Slider | AddSlider |
| Dropdown | AddDropdown |
| Keybind | AddBind |
| Color Picker | AddColorpicker |
| Label | AddLabel |
| Paragraph | AddParagraph |
| Warning Label | AddWarningLabel |
| Approval Label | AddApproveLabel |
| Custom Label | AddCustomLabel |

## API Integrations

Lunarion uses several supporting APIs and integrations:

| API / Integration | Purpose |
|---|---|
| Orion-style API | Main UI API design |
| Lucide | Icon library |
| Solar | Icon library |
| Gravity UI | Icon library |
| Footagesus/Icons | Icon resolution |
| Roblox Services | Interface and gameplay integration |
| Runtime APIs | Optional environment-specific functionality |

These are supporting integrations, not separate UI frameworks bundled together.

## Quick Start

```lua
local Lunarion = loadstring(game:HttpGet("YOUR_RAW_URL"))()

local Window = Lunarion:MakeWindow({
    Name = "My Script",
    Theme = "Lunarion",
    SaveConfig = true,
    IntroEnabled = false,
})

local MainTab = Window:MakeTab({
    Name = "Main",
    Icon = "house",
})

local Section = MainTab:AddSection({
    Name = "Main Controls",
})

Section:AddButton({
    Name = "Example Button",
    Callback = function()
        print("Hello from Lunarion!")
    end,
})
```

Replace `YOUR_RAW_URL` with your published source URL. This loader requires an environment supporting `loadstring` and `game:HttpGet`.

## Documentation

For the complete API reference, configuration options, methods, and examples, see:

**[Documentation.md](Documentation.md)**

## Credits

Lunarion acknowledges the third-party projects and resources referenced by its implementation:

- Lucide Icons — ISC License.
- Solar Icon Set — CC BY 4.0.
- Gravity UI Icons — MIT License.
- Footagesus/Icons — MIT License.

Third-party assets remain subject to their respective licenses.

## License

Lunarion is distributed under the MIT License.

See [LICENSE](LICENSE) for the complete license text.

## Developer

**CENTURION SOFTWORKS**

Independent Roblox software and UI library development.

Building tools for developers, and helping exploiters.
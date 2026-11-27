# Lunarion Documentation

**Lunarion UI Library — Centurion Softworks**

Welcome to the official Lunarion documentation.

This document explains how to load Lunarion, create interfaces, use its UI elements, customize themes, and access additional library functionality.

---

# Table of Contents

1. [Introduction](#1-introduction)
2. [Installation](#2-installation)
3. [Getting Started](#3-getting-started)
4. [Library Architecture](#4-library-architecture)
5. [Creating a Window](#5-creating-a-window)
6. [Creating Tabs](#6-creating-tabs)
7. [Creating Sections](#7-creating-sections)
8. [UI Elements](#8-ui-elements)
9. [Dropdowns](#9-dropdowns)
10. [Keybinds](#10-keybinds)
11. [Color Pickers](#11-color-pickers)
12. [Labels and Text Elements](#12-labels-and-text-elements)
13. [Notifications](#13-notifications)
14. [Key Systems](#14-key-systems)
15. [Theme System](#15-theme-system)
16. [Analytics](#16-analytics)
17. [Configuration](#17-configuration)
18. [Lifecycle Management](#18-lifecycle-management)
19. [Aliases](#19-aliases)
20. [Icon Integrations](#20-icon-integrations)
21. [Runtime Compatibility](#21-runtime-compatibility)
22. [Complete Example](#22-complete-example)
23. [Credits](#23-credits)

---

# 1. Introduction

Lunarion is a Roblox LuaU UI library developed by **Centurion Softworks**.

It provides a structured approach to building interfaces through windows, tabs, sections, and interactive elements.

The library is designed to support:

- Interface organization.
- Interactive controls.
- Custom themes.
- Notifications.
- Key systems.
- Configuration functionality.
- Icon integrations.
- Optional analytics.

Lunarion follows an API structure inspired by the familiar Orion-style interface hierarchy.

Its implementation and additional functionality belong to Lunarion.

---

# 2. Installation

## 2.1 Loading Lunarion

Use the following loader:

```lua
local Lunarion = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/CenturionSoftworks/Lunarion/main/Lunarion.lua"
))()
```

This retrieves and executes the Lunarion source file.

## 2.2 Requirements

The loader requires an environment that supports:

- `loadstring`
- `game:HttpGet()`

These capabilities are not available to ordinary Roblox LocalScripts by default.

Additional functionality may require environment-specific APIs.

---

# 3. Getting Started

After loading Lunarion, create a window.

```lua
local Lunarion = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/CenturionSoftworks/Lunarion/main/Lunarion.lua"
))()

local Window = Lunarion:MakeWindow({
    Name = "My Interface"
})
```

Next, create a tab.

```lua
local Tab = Window:MakeTab({
    Name = "Main",
    Icon = "home"
})
```

Then create a section.

```lua
local Section = Tab:AddSection({
    Name = "Main Controls"
})
```

You can now add UI elements to the section.

```lua
Section:AddButton({
    Name = "Click Me",
    Callback = function()
        print("Button clicked!")
    end
})
```

---

# 4. Library Architecture

Lunarion uses a hierarchical interface structure.

```text
Lunarion
│
└── Window
    │
    ├── Tab
    │   │
    │   ├── Section
    │   │   ├── Button
    │   │   ├── Toggle
    │   │   ├── Slider
    │   │   ├── Dropdown
    │   │   ├── Bind
    │   │   ├── Colorpicker
    │   │   └── Labels
    │   │
    │   └── Section
    │
    └── Tab
        │
        └── Section
```

The main hierarchy is:

1. Library
2. Window
3. Tabs
4. Sections
5. UI Elements

This organization makes interfaces easier to maintain and navigate.

---

# 5. Creating a Window

Windows are the main containers for your interface.

## Method

```lua
Lunarion:MakeWindow({})
```

## Example

```lua
local Window = Lunarion:MakeWindow({
    Name = "Lunarion Example",
    HidePremium = false,
    SaveConfig = true
})
```

The window configuration determines the initial window setup.

Commonly used configuration fields include:

| Field | Description |
|---|---|
| `Name` | Sets the window name. |
| `HidePremium` | Controls premium-related interface visibility. |
| `SaveConfig` | Enables configuration-related behavior where supported. |

Refer to the implementation for additional supported window options.

---

# 6. Creating Tabs

Tabs organize different categories of functionality.

## Method

```lua
Window:MakeTab({})
```

## Example

```lua
local MainTab = Window:MakeTab({
    Name = "Main",
    Icon = "home"
})

local SettingsTab = Window:MakeTab({
    Name = "Settings",
    Icon = "settings"
})
```

Tabs help separate functionality into logical groups.

For example:

- Main
- Player
- Settings
- Information

---

# 7. Creating Sections

Sections organize controls inside tabs.

## Method

```lua
Tab:AddSection({})
```

## Example

```lua
local Section = MainTab:AddSection({
    Name = "Main Controls"
})
```

You can create multiple sections within the same tab.

```lua
local General = MainTab:AddSection({
    Name = "General"
})

local Advanced = MainTab:AddSection({
    Name = "Advanced"
})
```

---

# 8. UI Elements

Lunarion provides multiple interactive elements.

## 8.1 Button

Creates a clickable button.

### Method

```lua
Section:AddButton({})
```

### Example

```lua
Section:AddButton({
    Name = "Print Message",
    Callback = function()
        print("Hello from Lunarion!")
    end
})
```

The callback executes when the button is activated.

---

## 8.2 Toggle

Creates an on/off control.

### Method

```lua
Section:AddToggle({})
```

### Example

```lua
Section:AddToggle({
    Name = "Example Toggle",
    Default = false,
    Callback = function(Value)
        print("Toggle state:", Value)
    end
})
```

### Parameters

| Parameter | Description |
|---|---|
| `Name` | Toggle name. |
| `Default` | Initial toggle state. |
| `Callback` | Function executed when the value changes. |

The callback receives the updated value.

---

## 8.3 Slider

Creates a numerical slider.

### Method

```lua
Section:AddSlider({})
```

### Example

```lua
Section:AddSlider({
    Name = "WalkSpeed",
    Min = 0,
    Max = 100,
    Default = 16,
    Increment = 1,
    ValueName = "Speed",
    Callback = function(Value)
        print("Selected speed:", Value)
    end
})
```

### Parameters

| Parameter | Description |
|---|---|
| `Name` | Slider name. |
| `Min` | Minimum value. |
| `Max` | Maximum value. |
| `Default` | Initial value. |
| `Increment` | Value increment. |
| `ValueName` | Displayed value label. |
| `Callback` | Function executed when the value changes. |

---

# 9. Dropdowns

Dropdowns allow users to select from a list of options.

## Method

```lua
Section:AddDropdown({})
```

## Example

```lua
Section:AddDropdown({
    Name = "Select an Option",
    Default = "Option 1",
    Options = {
        "Option 1",
        "Option 2",
        "Option 3"
    },
    Callback = function(Value)
        print("Selected:", Value)
    end
})
```

### Parameters

| Parameter | Description |
|---|---|
| `Name` | Dropdown name. |
| `Default` | Initial selection. |
| `Options` | Available options. |
| `Callback` | Function executed when a selection changes. |

The callback receives the selected value.

---

# 10. Keybinds

Keybinds allow users to interact with controls using keyboard input.

## Method

```lua
Section:AddBind({})
```

## Example

```lua
Section:AddBind({
    Name = "Example Keybind",
    Default = Enum.KeyCode.E,
    Hold = false,
    Callback = function()
        print("Keybind activated!")
    end
})
```

### Parameters

| Parameter | Description |
|---|---|
| `Name` | Keybind name. |
| `Default` | Default key. |
| `Hold` | Determines hold-related behavior. |
| `Callback` | Function executed by the keybind. |

Exact keybind behavior depends on the implementation and runtime input support.

---

# 11. Color Pickers

Color pickers allow users to select colors.

## Method

```lua
Section:AddColorpicker({})
```

## Example

```lua
Section:AddColorpicker({
    Name = "Interface Color",
    Default = Color3.fromRGB(120, 80, 255),
    Callback = function(Color)
        print("Selected color:", Color)
    end
})
```

The callback receives the selected color value.

---

# 12. Labels and Text Elements

Lunarion includes several text-related elements.

## 12.1 Label

```lua
Section:AddLabel("Example Label")
```

Creates a basic text label.

## 12.2 Paragraph

```lua
Section:AddParagraph({
    Title = "Information",
    Content = "This is an example paragraph."
})
```

Creates a paragraph-style information element.

## 12.3 Warning Label

```lua
Section:AddWarningLabel("Warning message")
```

Creates a warning-style label.

## 12.4 Approve Label

```lua
Section:AddApproveLabel("Operation completed successfully")
```

Creates an approval-style label.

## 12.5 Custom Label

```lua
Section:AddCustomLabel({
    Name = "Custom Label"
})
```

Creates a customizable label element.

Refer to the source implementation for the complete supported options of each label method.

---

# 13. Notifications

Lunarion includes notification functionality.

Notifications can be used to communicate information to users without requiring another interface element.

The library exposes:

```lua
Lunarion:MakeNotification({})
```

A notification configuration may include information such as:

- Title
- Content
- Duration

Example configuration structure:

```lua
Lunarion:MakeNotification({
    Name = "Lunarion",
    Content = "Example notification",
    Time = 5
})
```

The exact supported configuration fields should be checked against the current source implementation.

---

# 14. Key Systems

Lunarion exposes key-system functionality.

## Method

```lua
Lunarion:MakeKeySystem({})
```

Key systems can be used to introduce a key-based access interface.

The exact configuration options and validation behavior depend on the implementation.

Check the source code for the complete supported key-system configuration.

---

# 15. Theme System

Lunarion includes a theme management system.

Themes control the appearance of the interface.

## 15.1 Built-in Themes

The available built-in themes include:

| Theme | Description |
|---|---|
| Lunarion | Main Lunarion theme. |
| Default | Default interface appearance. |
| Amethyst | Purple-inspired appearance. |
| Ocean | Blue-inspired appearance. |
| Rose | Rose-inspired appearance. |
| Emerald | Green-inspired appearance. |
| Light | Light interface appearance. |
| Sakura | Sakura-inspired appearance. |

## 15.2 Adding a Theme

Lunarion exposes:

```lua
Lunarion:AddTheme()
```

This method is used to register additional themes.

The exact theme table structure should follow the implementation's expected format.

## 15.3 Setting a Theme

```lua
Lunarion:SetTheme()
```

Sets the active theme.

## 15.4 Getting the Current Theme

```lua
Lunarion:GetTheme()
```

Returns the current theme information.

## 15.5 Listing Themes

```lua
Lunarion:GetThemes()
```

Returns the available theme collection.

### Theme API Summary

| Method | Purpose |
|---|---|
| `AddTheme` | Registers a theme. |
| `SetTheme` | Applies a theme. |
| `GetTheme` | Retrieves the current theme. |
| `GetThemes` | Retrieves available themes. |

---

# 16. Analytics

Lunarion includes optional local analytics functionality.

Analytics are disabled by default.

The library exposes the following methods:

## Enable Analytics

```lua
Lunarion:EnableAnalytics()
```

Enables the analytics functionality.

## Track an Event

```lua
Lunarion:TrackEvent()
```

Tracks an event through the analytics system.

## Get Analytics

```lua
Lunarion:GetAnalytics()
```

Retrieves available analytics information.

## Clear Analytics

```lua
Lunarion:ClearAnalytics()
```

Clears stored analytics information.

## Export Analytics

```lua
Lunarion:ExportAnalytics()
```

Exports analytics information.

### Analytics API Summary

| Method | Purpose |
|---|---|
| `EnableAnalytics` | Enables analytics. |
| `TrackEvent` | Tracks an event. |
| `GetAnalytics` | Retrieves analytics data. |
| `ClearAnalytics` | Clears analytics data. |
| `ExportAnalytics` | Exports analytics data. |

Analytics functionality is local-oriented. Do not assume it transmits information to an external analytics server.

---

# 17. Configuration

Lunarion includes configuration-related functionality.

Configuration persistence depends on the execution environment.

Some environments provide file APIs such as:

- `writefile`
- `readfile`
- `isfile`
- `isfolder`
- `makefolder`

These are environment-specific functions and are not standard Roblox APIs.

The library exposes:

```lua
Lunarion:SaveConfig()
```

Use the configuration functionality according to the options supported by the current source.

---

# 18. Lifecycle Management

Lunarion provides methods for managing the library's lifecycle.

## 18.1 Initialize

```lua
Lunarion:Init()
```

Initializes the library.

## 18.2 Destroy

```lua
Lunarion:Destroy()
```

Destroys the library interface and performs its cleanup behavior.

## 18.3 Check Running State

```lua
Lunarion:IsRunning()
```

Checks whether the library is currently running.

### Lifecycle API Summary

| Method | Purpose |
|---|---|
| `Init` | Initializes the library. |
| `Destroy` | Destroys the library. |
| `IsRunning` | Checks running state. |

---

# 19. Aliases

Lunarion includes alternative method names for selected functionality.

| Main Method | Alias |
|---|---|
| `MakeNotification` | `Spawn` |
| `MakeNotification` | `Alert` |
| `AddTheme` | `DefineTheme` |
| `SetTheme` | `UseTheme` |
| `GetTheme` | `CurrentTheme` |
| `GetThemes` | `ListThemes` |
| `EnableAnalytics` | `EnableTelemetry` |
| `TrackEvent` | `LogEvent` |
| `GetAnalytics` | `TelemetryData` |
| `ClearAnalytics` | `ResetTelemetry` |
| `ExportAnalytics` | `ExportTelemetry` |
| `Init` | `Boot` |
| `SaveConfig` | `Persist` |
| `MakeKeySystem` | `Gate` |
| `IsRunning` | `Alive` |
| `Destroy` | `Teardown` |

These aliases provide alternative names for corresponding functionality.

---

# 20. Icon Integrations

Lunarion supports multiple icon collections.

## Supported Collections

- Lucide
- Solar
- Gravity UI
- Footagesus/Icons

Material and Feather aliases are resolved through Lucide mappings.

Icon identifiers must follow the naming conventions supported by the corresponding integration.

For more information about the icon collections:

- [Lucide](https://lucide.dev/)
- [Solar Icons](https://solar-icons.com/)
- [Gravity UI](https://gravity-ui.com/)
- [Footagesus/Icons](https://github.com/Footagesus/Icons)

---

# 21. Runtime Compatibility

Some Lunarion features depend on runtime-specific functionality.

The following APIs may be used by the library or its optional features.

## GUI and Environment APIs

| API | Purpose |
|---|---|
| `gethui` | Retrieves an environment-specific GUI container. |
| `syn.protect_gui` | Protects GUI instances in supported environments. |

## File APIs

| API | Purpose |
|---|---|
| `writefile` | Writes files. |
| `readfile` | Reads files. |
| `isfile` | Checks file existence. |
| `isfolder` | Checks folder existence. |
| `makefolder` | Creates folders. |
| `getcustomasset` | Retrieves custom assets. |

## Clipboard APIs

| API | Purpose |
|---|---|
| `setclipboard` | Copies text to the clipboard. |

## Executor Identification

| API | Purpose |
|---|---|
| `identifyexecutor` | Identifies the execution environment. |

## HTTP APIs

Depending on the environment, the following may be available:

- `request`
- `http_request`
- `http.request`
- `syn.request`

Not every environment supports every API.

## Roblox Services

Lunarion may interact with Roblox services including:

- `Players`
- `UserInputService`
- `TweenService`
- `RunService`
- `HttpService`
- `TextService`
- `GuiService`
- `CoreGui`
- `Stats`
- `LocalizationService`

The availability and behavior of certain functionality depend on the environment.

---

# 22. Complete Example

The following example demonstrates the main interface hierarchy and several UI elements.

```lua
local Lunarion = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/CenturionSoftworks/Lunarion/main/Lunarion.lua"
))()

-- Create the main window
local Window = Lunarion:MakeWindow({
    Name = "Lunarion Example",
    HidePremium = false,
    SaveConfig = true
})

-- Create tabs
local MainTab = Window:MakeTab({
    Name = "Main",
    Icon = "home"
})

local SettingsTab = Window:MakeTab({
    Name = "Settings",
    Icon = "settings"
})

-- Create sections
local MainSection = MainTab:AddSection({
    Name = "Main Controls"
})

local SettingsSection = SettingsTab:AddSection({
    Name = "Preferences"
})

-- Button
MainSection:AddButton({
    Name = "Print Message",
    Callback = function()
        print("Hello from Lunarion!")
    end
})

-- Toggle
MainSection:AddToggle({
    Name = "Example Toggle",
    Default = false,
    Callback = function(Value)
        print("Toggle:", Value)
    end
})

-- Slider
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

-- Dropdown
MainSection:AddDropdown({
    Name = "Example Dropdown",
    Default = "Option 1",
    Options = {
        "Option 1",
        "Option 2",
        "Option 3"
    },
    Callback = function(Value)
        print("Selected:", Value)
    end
})

-- Keybind
MainSection:AddBind({
    Name = "Example Keybind",
    Default = Enum.KeyCode.E,
    Hold = false,
    Callback = function()
        print("Keybind activated!")
    end
})

-- Color picker
SettingsSection:AddColorpicker({
    Name = "Interface Color",
    Default = Color3.fromRGB(120, 80, 255),
    Callback = function(Color)
        print("Color:", Color)
    end
})

-- Label
SettingsSection:AddLabel("Lunarion UI Library")

-- Paragraph
SettingsSection:AddParagraph({
    Title = "About",
    Content = "Powered by Centurion Softworks."
})
```

---

# 23. Credits

## Development

**Lunarion UI Library**

Developed and maintained by:

**Centurion Softworks**

## Third-Party Integrations

Lunarion includes integrations and references to third-party icon projects.

Their respective authors retain ownership of their projects and trademarks.

- Lucide
- Solar Icons
- Gravity UI
- Footagesus/Icons

Please consult each project's official license for its applicable usage requirements.

---

# Final Notes

Lunarion is an independently developed UI library by Centurion Softworks.

This documentation describes the library's public API and supported functionality. For exact parameter behavior and implementation-specific options, consult the current `Lunarion.lua` source.

**Repository:**  
https://github.com/CenturionSoftworks/Lunarion

**Raw Source:**  
https://raw.githubusercontent.com/CenturionSoftworks/Lunarion/main/Lunarion.lua

---

**Lunarion UI Library**  
*Centurion Softworks*
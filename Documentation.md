
# Lunarion UI Library
## Official Documentation

**Developer:** Centurion Softworks  
**Platform:** Roblox  
**Language:** LuaU  
**API Architecture:** Orion-style UI API  
**Version declared in source:** 3.0.0

---

# 1. Introduction

Lunarion is a Roblox LuaU UI library developed by Centurion Softworks.

Its API architecture is based on the Orion UI Library API, retaining its familiar window, tab, section, and element hierarchy.

Lunarion extends this structure with additional interface functionality, themes, icon integrations, notifications, configuration handling, and developer utilities.

Lunarion is an independent implementation, not an official Orion release.

# 2. Installation

Load Lunarion using a supported loading method.

Example:

```lua
local Lunarion = loadstring(game:HttpGet("YOUR_RAW_URL"))()
```

Replace `YOUR_RAW_URL` with the raw URL of your published Lua file.

Note that this loading method requires an environment that supports both functions.

# 3. Creating a Window

Use `MakeWindow()` to create the main interface.

```lua
local Window = Lunarion:MakeWindow({
    Name = "My Script",
    Theme = "Lunarion",
    SaveConfig = true,
    AutoLoad = true,
    IntroEnabled = false,
    Homeboard = true,
})
```

### Configuration Options

| Option | Description |
|---|---|
| Name | Window title |
| Theme | Initial theme |
| Themes | Custom theme definitions |
| SaveConfig | Enables configuration persistence |
| AutoLoad | Controls automatic configuration loading |
| ConfigFolder | Configuration directory |
| ConfigName | Configuration filename |
| IntroEnabled | Enables or disables the intro |
| IntroText | Intro title |
| ShowIcon | Controls window icon visibility |
| Icon | Window icon |
| IntroIcon | Intro icon |
| CloseCallback | Window close callback |
| Analytics | Enables local analytics |
| Homeboard | Controls dashboard functionality |
| Security | Controls the client-side integrity watchdog |

# 4. Creating Tabs

Use `MakeTab()` to create tabs.

```lua
local MainTab = Window:MakeTab({
    Name = "Main",
    Icon = "house",
})

local SettingsTab = Window:MakeTab({
    Name = "Settings",
    Icon = "settings",
})
```

Supported tab configuration includes:

- Name
- Icon
- ImageSource
- Hidden
- PremiumOnly
- Custom tab content options

### Tab Dividers

```lua
Window:MakeTabSection("Gameplay")
```

Or:

```lua
Window:MakeTabSection({
    Name = "Utilities",
    Icon = "wrench",
    Line = true,
})
```

Aliases include:

- AddTabSection
- MakeTabDivider

# 5. Sections

Sections organize controls inside tabs.

```lua
local Section = MainTab:AddSection({
    Name = "General",
})
```

# 6. UI Elements

## Button

```lua
Section:AddButton({
    Name = "Execute",
    Icon = "play",
    Callback = function()
        print("Executed!")
    end,
})
```

## Toggle

```lua
Section:AddToggle({
    Name = "Enabled",
    Default = false,
    Flag = "EnabledFlag",
    Save = true,
    Callback = function(value)
        print(value)
    end,
})
```

## Slider

```lua
Section:AddSlider({
    Name = "Speed",
    Min = 0,
    Max = 100,
    Default = 25,
    Increment = 1,
    Callback = function(value)
        print(value)
    end,
})
```

## Dropdown

```lua
Section:AddDropdown({
    Name = "Select Option",
    Options = {
        "Option 1",
        "Option 2",
        "Option 3"
    },
    Default = "Option 1",
    Multi = false,
    Search = true,
    Callback = function(value)
        print(value)
    end,
})
```

Dropdown methods:

- Set(value)
- Get()
- Refresh(options, clear)
- Open()
- Close()
- Toggle()

The dropdown also exposes its current selection through `.Value`.

## Keybind

```lua
Section:AddBind({
    Name = "Toggle Key",
    Default = "RightShift",
    AllowMouse = true,

    Callback = function()
        print("Key pressed")
    end,

    OnChange = function(keyName)
        print(keyName)
    end,
})
```

Additional options include:

- Hold
- Mode
- AllowMouse

## Color Picker

```lua
Section:AddColorpicker({
    Name = "Accent Color",
    Default = Color3.fromRGB(128, 140, 255),

    Callback = function(color)
        print(color)
    end,
})
```

Additional functionality includes color presets and hex input.

## Label

```lua
Section:AddLabel("Welcome to Lunarion")
```

## Paragraph

```lua
Section:AddParagraph(
    "Information",
    "This is an example paragraph."
)
```

## Warning Label

```lua
Section:AddWarningLabel("Warning message")
```

## Approval Label

```lua
Section:AddApproveLabel("Successfully loaded")
```

## Custom Label

```lua
Section:AddCustomLabel({
    Text = "Custom Status",
    Color = Color3.fromRGB(168, 85, 247),
    Icon = "sparkles",
})
```

# 7. Themes

Lunarion includes several predefined themes.

Available themes:

- Lunarion
- Default
- Amethyst
- Ocean
- Rose
- Emerald
- Light
- Sakura

### Change Theme

```lua
Lunarion:SetTheme("Ocean")
```

### Get Current Theme

```lua
print(Lunarion:GetTheme())
```

### Get Available Themes

```lua
for _, theme in ipairs(Lunarion:GetThemes()) do
    print(theme)
end
```

### Register Custom Theme

```lua
Lunarion:AddTheme("Centurion", {
    Main = Color3.fromRGB(16, 18, 24),
    Second = Color3.fromRGB(25, 28, 36),
    Stroke = Color3.fromRGB(55, 60, 72),
    Divider = Color3.fromRGB(55, 60, 72),
    Text = Color3.fromRGB(245, 246, 248),
    TextDark = Color3.fromRGB(155, 160, 172),
    Accent = Color3.fromRGB(190, 160, 95),
})
```

# 8. Notifications

Create notifications using `MakeNotification()`.

```lua
Lunarion:MakeNotification({
    Name = "Lunarion",
    Content = "Successfully executed!",
    Icon = "check",
    Duration = 5,
    Type = "success",
})
```

Supported options include:

- Name / Title
- Content
- Image / Icon
- ImageSource
- Time / Duration
- Type
- Color
- ShowProgress
- Dismissable
- OnClick

The returned notification handle supports `:Dismiss()`.

# 9. Key System

Lunarion includes a key verification interface.

```lua
local Verified = Lunarion:MakeKeySystem({
    -- Configure using the options supported by
    -- the MakeKeySystem implementation.
})
```

The key system supports configurable verification UI, key inputs, key lists, optional URL checks, and saving successful keys.

It returns a boolean indicating whether verification succeeded or the interface was closed.

Client-side key verification is not a secure authorization boundary. Important permissions should be validated on a trusted server.

# 10. Configuration System

Lunarion supports configuration persistence when the runtime provides the necessary file APIs.

Configuration-related options include:

- SaveConfig
- AutoLoad
- ConfigFolder
- ConfigName
- Flag
- Save

Manual methods:

```lua
Lunarion:Init()

local Saved = Lunarion:SaveConfig()
```

File persistence depends on the environment supporting functions such as:

- writefile
- readfile
- isfile
- isfolder
- makefolder

These are not standard Roblox LocalScript APIs.

# 11. Settings System

Lunarion supports registering custom settings.

```lua
Lunarion:AddSetting({
    Name = "My Setting",
    Type = "Toggle",
    Default = false,
    Section = "General",

    Callback = function(value)
        print(value)
    end,
})
```

The implementation demonstrates Toggle, Button, and Dropdown setting types.

# 12. Icon System

Lunarion supports multiple icon sources.

Available icon sets:

- Lucide
- Solar
- Gravity
- Custom

Compatibility aliases:

- Material
- Feather

Examples:

```lua
Icon = "house"
Icon = "solar:home-2-bold"
Icon = "lucide:settings"
Icon = "rbxassetid://123456789"
```

### Change Icon Set

```lua
Lunarion:SetIconSet("solar")
```

### Get Available Icon Sets

```lua
print(table.concat(Lunarion:GetIconSets(), ", "))
```

### Register Custom Icon Library

```lua
Lunarion:AddIconLibrary("myicons", function(iconName)
    return nil
end)
```

The callback should return an icon descriptor supported by the icon resolver.

# 13. Analytics and Telemetry

Lunarion includes an optional local analytics system.

Analytics are disabled by default.

### Enable Analytics

```lua
Lunarion:EnableAnalytics(true)
```

### Track Event

```lua
Lunarion:TrackEvent("ExampleEvent", {
    Feature = "MainTab",
})
```

### Retrieve Analytics

```lua
local Data = Lunarion:GetAnalytics()
```

### Clear Analytics

```lua
Lunarion:ClearAnalytics()
```

### Export Analytics

```lua
local Success, Result =
    Lunarion:ExportAnalytics("MyAnalytics.json")
```

Exporting requires the runtime's `writefile` function.

# 14. Homeboard

Lunarion includes a Homeboard dashboard.

It can display information such as:

- Player profile information
- Executor identification
- Discord invitation information
- Friend counts
- Server information
- Player counts
- FPS
- Latency
- Server time

Homeboard configuration supports options including:

- Name
- Icon
- ImageSource
- Discord
- Executors
- ShowFriends
- ShowServer
- ShowProfile

Some information depends on available Roblox services or runtime-specific functions.

# 15. Window Controls

The window controller exposes additional functionality.

Examples:

```lua
Window:Resize(700, 480)

Window:SetTabStyle("top")

Window:OpenSearch()

Window:ToggleInterface()
```

The implementation also includes aliases such as:

- Flip
- Page
- Divider
- Dashboard

# 16. Main Library API Reference

| Method | Description |
|---|---|
| MakeWindow(config) | Creates a UI window |
| MakeNotification(config) | Creates a notification |
| MakeKeySystem(config) | Creates a verification interface |
| AddTheme(name, theme) | Registers a theme |
| SetTheme(name) | Applies a theme |
| GetTheme() | Returns the current theme |
| GetThemes() | Lists available themes |
| EnableAnalytics(state) | Enables or disables analytics |
| TrackEvent(name, data) | Records an event |
| GetAnalytics() | Retrieves analytics |
| ClearAnalytics() | Clears analytics |
| ExportAnalytics(name) | Exports analytics |
| Init() | Initializes configuration handling |
| SaveConfig() | Saves configuration |
| Destroy() | Destroys the UI |
| IsRunning() | Checks UI state |

## API Aliases

| Alias | Original Method |
|---|---|
| Spawn | MakeWindow |
| Alert | MakeNotification |
| DefineTheme | AddTheme |
| UseTheme | SetTheme |
| CurrentTheme | GetTheme |
| ListThemes | GetThemes |
| EnableTelemetry | EnableAnalytics |
| LogEvent | TrackEvent |
| TelemetryData | GetAnalytics |
| ResetTelemetry | ClearAnalytics |
| ExportTelemetry | ExportAnalytics |
| Boot | Init |
| Persist | SaveConfig |
| Gate | MakeKeySystem |
| Alive | IsRunning |
| Teardown | Destroy |

# 17. Other APIs and Dependencies

Lunarion uses several Roblox engine services.

### Roblox Services

- UserInputService
- TweenService
- RunService
- Players
- HttpService
- TextService
- GuiService
- CoreGui
- Stats
- LocalizationService

### Optional Runtime Functions

Depending on the execution environment, the source may use:

- loadstring
- game:HttpGet
- gethui
- syn.protect_gui
- writefile
- readfile
- isfile
- isfolder
- makefolder
- getcustomasset
- setclipboard
- identifyexecutor
- request
- http_request
- http.request
- syn.request

These are environment-specific integrations, not guaranteed Roblox APIs.

### Third-Party Integrations

- Lucide Icons
- Solar Icon Set
- Gravity UI Icons
- Footagesus/Icons

Lunarion does not bundle several competing UI frameworks. It has one main UI implementation with supporting integrations.

# 18. Fonts

The source references:

- Atkinson Hyperlegible
- Helvetica
- Bahnschrift

Helvetica and Bahnschrift are optional local font files rather than fonts downloaded by the library.

Review the applicable font licenses before redistributing font files.

# 19. Security and Limitations

Lunarion includes a client-side integrity watchdog and a locked public API proxy.

These features help protect against accidental changes and casual tampering.

However, client-side protections cannot guarantee that a script is tamper-proof.

Never store sensitive credentials or authoritative permissions in client-side code.

# 20. Credits and Licensing

Lunarion is developed and maintained by:

**CENTURION SOFTWORKS**

Third-party acknowledgments:

- Lucide Icons — ISC License.
- Solar Icon Set — CC BY 4.0.
- Gravity UI Icons — MIT License.
- Footagesus/Icons — MIT License.

Third-party licenses remain applicable to their respective assets and projects.

Lunarion's project license is the MIT License.

See the repository's LICENSE file for the complete terms.

---

**CENTURION SOFTWORKS**

Lunarion UI Library  
Roblox LuaU Development
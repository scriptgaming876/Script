## loading Flux Ui
```lua
local Flux = loadstring(game:HttpGet("https://raw.githubusercontent.com/FluxTeam/FluxLib/main/source"))()

local Window = Flux:Window("Game Loading...", "Loading UI", Color3.fromRGB(0, 162, 232), Enum.KeyCode.RightControl)
local LoadingTab = Window:Tab("Loading", "rbxassetid://12345678") -- Replace with your icon ID

local StatusLabel = LoadingTab:Label("Initializing...", Color3.fromRGB(255, 255, 255))

task.wait(2)
StatusLabel:Refresh("Loading assets...")

task.wait(3)
StatusLabel:Refresh("Finalizing...")

task.wait(2)
Window:Destroy() -- Closes the UI after loading
```

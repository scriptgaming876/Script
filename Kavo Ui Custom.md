## Kavo Ui Icons
```lua
local Kavo = loadstring(game:HttpGet("https://raw.githubusercontent.com/o5u3/Kavo-UI-Library/main/source.lua"))()
local Window = Kavo.CreateLib("Game UI with Icons", "DarkTheme")

local MainTab = Window:NewTab("🏠 Home") -- Icon in Tab Name
local Section = MainTab:NewSection("Main Menu")

-- Button with an Icon
Section:NewButton("Start Game", "Click to begin!", function()
    print("Game Started!")
end)

-- Custom Image Icon in UI
local icon = Instance.new("ImageLabel")
icon.Parent = Section
icon.Size = UDim2.new(0, 50, 0, 50)
icon.Position = UDim2.new(0, 10, 0, 10)
icon.Image = "rbxassetid://12345678" -- Replace with your icon ID
icon.BackgroundTransparency = 1

-- Notification with Custom Icon
game.StarterGui:SetCore("SendNotification", {
    Title = "Notification!";
    Text = "Welcome to the game!";
    Duration = 3;
    Icon = "rbxassetid://12345678"; -- Replace with your icon ID
})
```
## loading kavo ui
```lua
local Kavo = loadstring(game:HttpGet("https://raw.githubusercontent.com/o5u3/Kavo-UI-Library/main/source.lua"))()
local Window = Kavo.CreateLib("Game Loading...", "DarkTheme")

local LoadingTab = Window:NewTab("Loading")
local Section = LoadingTab:NewSection("Please wait...")

Section:NewLabel("Loading assets...")

wait(2)
Section:NewLabel("Checking game data...")

wait(3)
Section:NewLabel("Finalizing...")

wait(2)
Window:Destroy() -- Removes UI after loading
```
## Notify Kavo Ui
```lua
local Kavo = loadstring(game:HttpGet("https://raw.githubusercontent.com/o5u3/Kavo-UI-Library/main/source.lua"))()
local Window = Kavo.CreateLib("Game Notifications", "DarkTheme")

local function sendNotification(title, text, duration)
    local NotifyTab = Window:NewTab("Notification")
    local Section = NotifyTab:NewSection(title)
    
    Section:NewLabel(text)

    wait(duration)
    NotifyTab:Destroy() -- Removes notification after duration
end

-- Example Notifications
sendNotification("Welcome!", "You have joined the game.", 3)
wait(5)
sendNotification("Achievement Unlocked!", "You found a secret room.", 4)
```
## Script Kavo ui Movable
```lua
local Kavo = loadstring(game:HttpGet("https://raw.githubusercontent.com/o5u3/Kavo-UI-Library/main/source.lua"))()
local Window = Kavo.CreateLib("Moveable UI", "DarkTheme")

local MainTab = Window:NewTab("Main")
local Section = MainTab:NewSection("Drag this UI!")

-- Make UI Moveable
local gui = Window["MainFrame"] -- Main UI Frame
gui.Active = true
gui.Draggable = true
```

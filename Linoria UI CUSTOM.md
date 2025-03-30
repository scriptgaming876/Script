## Loading Script
```lua
local Linoria = loadstring(game:HttpGet("https://raw.githubusercontent.com/violin-suzutsuki/LinoriaLib/main/Library.lua"))()
local Window = Linoria:CreateWindow("Loading...")

local LoadingTab = Window:AddTab("Loading")
local StatusLabel = LoadingTab:AddLabel("Initializing...")

task.wait(2)
StatusLabel:SetText("Loading assets...")

task.wait(3)
StatusLabel:SetText("Finalizing...")

task.wait(2)
Window:Destroy() -- Removes UI after loading is done
```
## Linoria Key System
```lua
local Linoria = loadstring(game:HttpGet("https://raw.githubusercontent.com/violin-suzutsuki/LinoriaLib/main/Library.lua"))()
local Window = Linoria:CreateWindow("Key System")
local KeyTab = Window:AddTab("Key System")
local KeyBox = KeyTab:AddInput("Enter Key", { Default = "", Numeric = false, Finished = false })

local correctKey = "123456" -- Change this to your desired key

KeyTab:AddButton("Submit", function()
    if KeyBox.Value == correctKey then
        Window:Destroy() -- Removes the key system UI
        loadstring(game:HttpGet("https://your-script-link.com"))() -- Replace with your main UI script
    else
        KeyTab:AddLabel("Incorrect Key! Try Again.")
    end
end)
```
## script Linoria Ui Notify
```lua
local Linoria = loadstring(game:HttpGet("https://raw.githubusercontent.com/violin-suzutsuki/LinoriaLib/main/Library.lua"))()

-- Function to send a notification
local function SendNotification(title, message, duration)
    Linoria:Notify({
        Title = title,
        Content = message,
        Duration = duration or 3
    })
end

-- Example Notifications
SendNotification("Welcome!", "You have joined the game.", 4)
wait(5)
SendNotification("Achievement Unlocked!", "You found a secret area.", 4)
```
## Linoria Ui Icons
```lua
local Linoria = loadstring(game:HttpGet("https://raw.githubusercontent.com/violin-suzutsuki/LinoriaLib/main/Library.lua"))()
local Window = Linoria:CreateWindow("UI with Icons")

local MainTab = Window:AddTab("🏠 Home") -- Unicode Icon in Tab Name
local Section = MainTab:AddSection("Main Menu")

-- Button with an Icon
local Button = Section:AddButton("Start Game", function()
    print("Game Started!")
end)
Button.Text = "🎮 Start Game" -- Adds an emoji icon to the button

-- Label with an Icon
local Label = Section:AddLabel("Status: 🟢 Online")

-- Image Icon
local ImageLabel = Instance.new("ImageLabel")
ImageLabel.Parent = Section.Container
ImageLabel.Size = UDim2.new(0, 50, 0, 50)
ImageLabel.Position = UDim2.new(0, 10, 0, 10)
ImageLabel.Image = "rbxassetid://12345678" -- Replace with your image ID
ImageLabel.BackgroundTransparency = 1

-- Notification with Custom Icon
Linoria:Notify({
    Title = "🔔 Notification",
    Content = "Welcome to the game!",
    Duration = 3
})
```
## Linoria Ui Theme
```lua
local Linoria = loadstring(game:HttpGet("https://raw.githubusercontent.com/violin-suzutsuki/LinoriaLib/main/Library.lua"))()
local Window = Linoria:CreateWindow("Custom Themes")

local ThemeTab = Window:AddTab("Themes")
local Section = ThemeTab:AddSection("Select Theme")

-- Available Themes
local Themes = {
    ["Dark"] = {MainColor = Color3.fromRGB(30, 30, 30), AccentColor = Color3.fromRGB(0, 162, 232)},
    ["Light"] = {MainColor = Color3.fromRGB(220, 220, 220), AccentColor = Color3.fromRGB(0, 162, 232)},
    ["Red"] = {MainColor = Color3.fromRGB(50, 0, 0), AccentColor = Color3.fromRGB(200, 0, 0)},
    ["Blue"] = {MainColor = Color3.fromRGB(0, 0, 50), AccentColor = Color3.fromRGB(0, 100, 200)}
}

-- Dropdown for Theme Selection
local ThemeDropdown = Section:AddDropdown("Select Theme", { Values = {"Dark", "Light", "Red", "Blue"}, Default = 1 })

ThemeDropdown:OnChanged(function(selectedTheme)
    Linoria:SetTheme(Themes[selectedTheme]) -- Apply the selected theme
end)

Linoria:Notify({
    Title = "🎨 Theme System",
    Content = "Select a theme from the 'Themes' tab!",
    Duration = 5
})
```

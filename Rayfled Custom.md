## Rayfled
## Rayfled Icons
```lua
local Rayfield = loadstring(game:HttpGet("https://sirius.menu/rayfield"))()
local Window = Rayfield:CreateWindow({
    Name = "Rayfield UI with Icons",
    LoadingTitle = "Loading...",
    LoadingSubtitle = "Please wait...",
})

local MainTab = Window:CreateTab("🏠 Home") -- Unicode icon in tab name
local Section = MainTab:CreateSection("Main Menu")

-- Button with an Icon
local Button = MainTab:CreateButton({
    Name = "🎮 Start Game",
    Callback = function()
        print("Game Started!")
    end
})

-- Label with an Icon
local Label = MainTab:CreateLabel("🟢 Status: Online")

-- Image Icon
local ImageLabel = Instance.new("ImageLabel")
ImageLabel.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui"):FindFirstChild("Rayfield"):FindFirstChild("Main")
ImageLabel.Size = UDim2.new(0, 50, 0, 50)
ImageLabel.Position = UDim2.new(0.05, 0, 0.1, 0)
ImageLabel.Image = "rbxassetid://12345678" -- Replace with your custom image ID
ImageLabel.BackgroundTransparency = 1

-- Notification with Custom Icon
Rayfield:Notify({
    Title = "🔔 Notification",
    Content = "Welcome to the game!",
    Duration = 3
})
```
## Loading Rayfled
```lua
local Rayfield = loadstring(game:HttpGet("https://sirius.menu/rayfield"))()

local Window = Rayfield:CreateWindow({
    Name = "Game Loading...",
    LoadingTitle = "Loading...",
    LoadingSubtitle = "Please wait while assets load...",
    ConfigurationSaving = {
        Enabled = false,
    }
})

local LoadingTab = Window:CreateTab("Loading")
local LoadingSection = LoadingTab:CreateSection("Game is Loading...")

local StatusLabel = LoadingTab:CreateLabel("Initializing...")

task.wait(2)
StatusLabel:Set("Loading assets...")

task.wait(3)
StatusLabel:Set("Finalizing...")

task.wait(2)
Rayfield:Destroy() -- Closes the loading screen once done
```




# Roblox Studio

## Script ESP
```lua
-- ESP Script for Roblox (Box ESP)
local function CreateESP(plr)
    if plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") then
        local Highlight = Instance.new("BoxHandleAdornment")
        Highlight.Size = plr.Character:GetExtentsSize()
        Highlight.Adornee = plr.Character.HumanoidRootPart
        Highlight.Color3 = Color3.new(1, 0, 0) -- Red color for enemies
        Highlight.AlwaysOnTop = true
        Highlight.ZIndex = 10
        Highlight.Transparency = 0.5
        Highlight.Parent = game.CoreGui
    end
end

local function UpdateESP()
    for _, player in pairs(game.Players:GetPlayers()) do
        if player ~= game.Players.LocalPlayer then
            CreateESP(player)
        end
    end
end

game.Players.PlayerAdded:Connect(UpdateESP)
UpdateESP()
```
## Third Person
```lua
local player = game.Players.LocalPlayer
local camera = game.Workspace.CurrentCamera

-- Set the camera to third-person mode
camera.CameraType = Enum.CameraType.Custom
camera.CameraSubject = player.Character.Humanoid

-- Adjust third-person distance
local thirdPersonDistance = 10 -- Adjust this value for closer or farther view
camera.FieldOfView = 70 -- Adjust FOV if needed

-- Function to toggle between first-person and third-person
local function toggleCamera()
    if player.CameraMode == Enum.CameraMode.Classic then
        player.CameraMode = Enum.CameraMode.LockFirstPerson -- First-person
    else
        player.CameraMode = Enum.CameraMode.Classic -- Third-person
    end
end

-- Bind the camera toggle to a key (e.g., "T" key)
game:GetService("UserInputService").InputBegan:Connect(function(input, gameProcessed)
    if not gameProcessed and input.KeyCode == Enum.KeyCode.T then
        toggleCamera()
    end
end)
```

## first Person
```lua
local player = game.Players.LocalPlayer
local camera = game.Workspace.CurrentCamera

-- Lock the camera in first-person and adjust FOV
camera.CameraType = Enum.CameraType.Custom
camera.CameraSubject = player.Character:FindFirstChild("Humanoid")
player.CameraMode = Enum.CameraMode.LockFirstPerson
camera.FieldOfView = 80 -- Adjust for a wider or narrower view

-- Prevent zooming out
player.CameraMaxZoomDistance = 0.5
player.CameraMinZoomDistance = 0.5
```
## Gui
```lua
-- Create a ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Create a Frame
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 200, 0, 100)
frame.Position = UDim2.new(0.5, -100, 0.5, -50)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Parent = screenGui

-- Create a Button
local button = Instance.new("TextButton")
button.Size = UDim2.new(1, 0, 1, 0)
button.Text = "Click Me"
button.BackgroundColor3 = Color3.fromRGB(100, 100, 255)
button.Parent = frame

-- Button Click Event
button.MouseButton1Click:Connect(function()
    print("Button Clicked!")
end)
```
## Tab Gui
```lua
-- Create a ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Create a Main Frame
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 300, 0, 200)
mainFrame.Position = UDim2.new(0.5, -150, 0.5, -100)
mainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
mainFrame.Parent = screenGui

-- Create Tab Buttons Frame
local tabButtonsFrame = Instance.new("Frame")
tabButtonsFrame.Size = UDim2.new(1, 0, 0, 30)
tabButtonsFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
tabButtonsFrame.Parent = mainFrame

-- Function to Create Tabs
local function createTabButton(tabName, position, tabFrame)
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0, 100, 1, 0)
    button.Position = UDim2.new(0, position, 0, 0)
    button.Text = tabName
    button.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.Parent = tabButtonsFrame

    -- Button Click Event to Switch Tabs
    button.MouseButton1Click:Connect(function()
        for _, frame in pairs(mainFrame:GetChildren()) do
            if frame:IsA("Frame") and frame ~= tabButtonsFrame then
                frame.Visible = false
            end
        end
        tabFrame.Visible = true
    end)
end

-- Create Tabs
local tab1 = Instance.new("Frame")
tab1.Size = UDim2.new(1, 0, 1, -30)
tab1.Position = UDim2.new(0, 0, 0, 30)
tab1.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
tab1.Visible = true
tab1.Parent = mainFrame

local tab2 = Instance.new("Frame")
tab2.Size = UDim2.new(1, 0, 1, -30)
tab2.Position = UDim2.new(0, 0, 0, 30)
tab2.BackgroundColor3 = Color3.fromRGB(70, 50, 50)
tab2.Visible = false
tab2.Parent = mainFrame

-- Add Buttons for Each Tab
createTabButton("Tab 1", 0, tab1)
createTabButton("Tab 2", 100, tab2)

-- Add Sample Content to Tabs
local label1 = Instance.new("TextLabel")
label1.Size = UDim2.new(1, 0, 1, 0)
label1.Text = "This is Tab 1"
label1.TextColor3 = Color3.fromRGB(255, 255, 255)
label1.BackgroundTransparency = 1
label1.Parent = tab1

local label2 = Instance.new("TextLabel")
label2.Size = UDim2.new(1, 0, 1, 0)
label2.Text = "This is Tab 2"
label2.TextColor3 = Color3.fromRGB(255,
```
## Script Died Respawn Notify
```lua
local player = game.Players.LocalPlayer

local function onDied()
    print(player.Name .. " has died!") -- Logs death
    game.StarterGui:SetCore("SendNotification", {  
        Title = "You Died";  
        Text = "Respawning...";  
        Duration = 3;  
    })  

    -- Wait and respawn
    wait(3)
    player:LoadCharacter()
end

player.CharacterAdded:Connect(function(character)
    local humanoid = character:WaitForChild("Humanoid")
    humanoid.Died:Connect(onDied)
end)
```
## Script Walkspeed Slider
```lua
-- Create GUI
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 200, 0, 100)
frame.Position = UDim2.new(0.5, -100, 0.5, -50)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Parent = screenGui

local slider = Instance.new("TextButton")
slider.Size = UDim2.new(1, 0, 0.5, 0)
slider.Position = UDim2.new(0, 0, 0, 0)
slider.Text = "Increase Speed"
slider.Parent = frame

local reset = Instance.new("TextButton")
reset.Size = UDim2.new(1, 0, 0.5, 0)
reset.Position = UDim2.new(0, 0, 0.5, 0)
reset.Text = "Reset Speed"
reset.Parent = frame

-- Function to Change WalkSpeed
slider.MouseButton1Click:Connect(function()
    local humanoid = game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
    if humanoid then
        humanoid.WalkSpeed = humanoid.WalkSpeed + 10 -- Increase speed by 10
    end
end)

reset.MouseButton1Click:Connect(function()
    local humanoid = game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
    if humanoid then
        humanoid.WalkSpeed = 16 -- Reset to default speed
    end
end)
```
## Script Walkspeed
```lua
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:FindFirstChildOfClass("Humanoid")

if humanoid then
    humanoid.WalkSpeed = 50 -- Change this value for faster/slower speed
end
```
## Script Jump Power
```lua
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:FindFirstChildOfClass("Humanoid")

if humanoid then
    humanoid.JumpPower = 100 -- Change this value for higher/lower jumps
end
```
# Jump power Gui
```lua
-- Create GUI
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 200, 0, 100)
frame.Position = UDim2.new(0.5, -100, 0.5, -50)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Parent = screenGui

local increase = Instance.new("TextButton")
increase.Size = UDim2.new(1, 0, 0.5, 0)
increase.Position = UDim2.new(0, 0, 0, 0)
increase.Text = "Increase Jump"
increase.Parent = frame

local reset = Instance.new("TextButton")
reset.Size = UDim2.new(1, 0, 0.5, 0)
reset.Position = UDim2.new(0, 0, 0.5, 0)
reset.Text = "Reset Jump"
reset.Parent = frame

-- Function to Change JumpPower
increase.MouseButton1Click:Connect(function()
    local humanoid = game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
    if humanoid then
        humanoid.JumpPower = humanoid.JumpPower + 20 -- Increase jump power by 20
    end
end)

reset.MouseButton1Click:Connect(function()
    local humanoid = game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
    if humanoid then
        humanoid.JumpPower = 50 -- Reset to default jump power
    end
end)
```
## Script Kick
```lua
local playerToKick = "PlayerName" -- Replace with the actual username

local player = game.Players:FindFirstChild(playerToKick)
if player then
    player:Kick("You have been kicked from the game.") -- Custom kick message
end
```
## Script Kick Player Gui
```lua
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 200, 0, 150)
frame.Position = UDim2.new(0.5, -100, 0.5, -75)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Parent = screenGui

local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(1, 0, 0.5, 0)
textBox.Position = UDim2.new(0, 0, 0, 0)
textBox.PlaceholderText = "Enter Player Name"
textBox.Parent = frame

local kickButton = Instance.new("TextButton")
kickButton.Size = UDim2.new(1, 0, 0.5, 0)
kickButton.Position = UDim2.new(0, 0, 0.5, 0)
kickButton.Text = "Kick Player"
kickButton.Parent = frame

kickButton.MouseButton1Click:Connect(function()
    local playerName = textBox.Text
    local player = game.Players:FindFirstChild(playerName)
    if player then
        player:Kick("You have been kicked by an admin.")
    end
end)
```
## Script Banned
```lua
local bannedPlayers = {
    12345678, -- Replace with banned UserId
    87654321  -- Add more UserIds as needed
}

game.Players.PlayerAdded:Connect(function(player)
    for _, bannedId in pairs(bannedPlayers) do
        if player.UserId == bannedId then
            player:Kick("You are banned from this game.")
            break
        end
    end
end)
```
## Gui Banned Player
```lua
-- RemoteEvent Setup (Put this in ServerScriptService)
local banEvent = Instance.new("RemoteEvent")
banEvent.Name = "BanPlayerEvent"
banEvent.Parent = game.ReplicatedStorage

local bannedPlayers = {}

banEvent.OnServerEvent:Connect(function(admin, playerName)
    local player = game.Players:FindFirstChild(playerName)
    if player then
        bannedPlayers[player.UserId] = true
        player:Kick("You have been banned by an admin.")
    end
end)

-- GUI (LocalScript in StarterGui)
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 200, 0, 150)
frame.Position = UDim2.new(0.5, -100, 0.5, -75)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Parent = screenGui

local textBox = Instance.new("TextBox")
textBox.Size = UDim2.new(1, 0, 0.5, 0)
textBox.Position = UDim2.new(0, 0, 0, 0)
textBox.PlaceholderText = "Enter Player Name"
textBox.Parent = frame

local banButton = Instance.new("TextButton")
banButton.Size = UDim2.new(1, 0, 0.5, 0)
banButton.Position = UDim2.new(0, 0, 0.5, 0)
banButton.Text = "Ban Player"
banButton.Parent = frame

banButton.MouseButton1Click:Connect(function()
    local playerName = textBox.Text
    game.ReplicatedStorage.BanPlayerEvent:FireServer(playerName)
end)
```
## Script Permanent Ban
```lua
local DataStoreService = game:GetService("DataStoreService")
local banDataStore = DataStoreService:GetDataStore("BannedPlayers")

game.Players.PlayerAdded:Connect(function(player)
    local isBanned = banDataStore:GetAsync(player.UserId)
    if isBanned then
        player:Kick("You are permanently banned from this game.")
    end
end)

game.ReplicatedStorage.BanPlayerEvent.OnServerEvent:Connect(function(admin, playerName)
    local player = game.Players:FindFirstChild(playerName)
    if player then
        banDataStore:SetAsync(player.UserId, true)
        player:Kick("You have been permanently banned.")
    end
end)
```
## Badges Toching part
```lua
local BadgeService = game:GetService("BadgeService")
local badgeId = 12345678 -- Replace with your Badge ID

local badgePart = script.Parent -- Make sure this script is inside a Part

badgePart.Touched:Connect(function(hit)
    local player = game.Players:GetPlayerFromCharacter(hit.Parent)
    if player and not BadgeService:UserHasBadgeAsync(player.UserId, badgeId) then
        BadgeService:AwardBadge(player.UserId, badgeId)
        print(player.Name .. " has earned the badge by touching the part!")
    end
end)
```
## Badges Giver
```lua
local BadgeService = game:GetService("BadgeService")
local badgeId = 12345678 -- Replace with your Badge ID

game.Players.PlayerAdded:Connect(function(player)
    if not BadgeService:UserHasBadgeAsync(player.UserId, badgeId) then
        BadgeService:AwardBadge(player.UserId, badgeId)
        print(player.Name .. " has received the badge!")
    else
        print(player.Name .. " already has this badge.")
    end
end)
```
## Gui Badge
```lua
local BadgeService = game:GetService("BadgeService")
local player = game.Players.LocalPlayer
local badgeIds = {12345678, 87654321} -- Replace with your Badge IDs

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 250, 0, #badgeIds * 30)
frame.Position = UDim2.new(0.5, -125, 0.5, -#badgeIds * 15)
frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
frame.Parent = screenGui

for i, badgeId in pairs(badgeIds) do
    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, 0, 0, 30)
    label.Position = UDim2.new(0, 0, 0, (i - 1) * 30)
    label.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    label.TextColor3 = Color3.fromRGB(255, 255, 255)
    label.Text = "Checking..."
    label.Parent = frame

    task.spawn(function()
        if BadgeService:UserHasBadgeAsync(player.UserId, badgeId) then
            label.Text = "✅ Badge " .. badgeId
        else
            label.Text = "❌ Badge " .. badgeId
        end
    end)
end
```
## Achievement
```lua
local BadgeService = game:GetService("BadgeService")
local badgeId = 12345678 -- Replace with your Badge ID
local door = script.Parent -- The door part

door.Touched:Connect(function(hit)
    local player = game.Players:GetPlayerFromCharacter(hit.Parent)
    if player and BadgeService:UserHasBadgeAsync(player.UserId, badgeId) then
        door.Transparency = 0.5
        door.CanCollide = false
        wait(3)
        door.CanCollide = true
        door.Transparency = 0
    else
        game.StarterGui:SetCore("SendNotification", {
            Title = "Access Denied";
            Text = "You need an achievement to enter!";
            Duration = 3;
        })
    end
end)
```
## Custom Entities
```lua
local door = script.Parent
local entityName = "CustomEntity" -- Change this to your entity's name

local function checkEntityNearby()
    for _, entity in pairs(workspace:GetChildren()) do
        if entity:IsA("Model") and entity.Name == entityName then
            local humanoidRootPart = entity:FindFirstChild("HumanoidRootPart")
            if humanoidRootPart then
                local distance = (humanoidRootPart.Position - door.Position).Magnitude
                if distance < 10 then -- Change this value for detection range
                    return true
                end
            end
        end
    end
    return false
end

while true do
    wait(1)
    if checkEntityNearby() then
        door.Transparency = 0.5
        door.CanCollide = false
        wait(3) -- Keep the door open for 3 seconds
        door.CanCollide = true
        door.Transparency = 0
    end
end
```
## Script Loading
```lua
local loadingScreen = script.Parent
local frame = loadingScreen:FindFirstChild("Frame")

wait(3) -- Wait 3 seconds before fading out

for i = 1, 10 do
    frame.BackgroundTransparency = i * 0.1
    wait(0.1)
end

loadingScreen:Destroy() -- Remove loading screen
```




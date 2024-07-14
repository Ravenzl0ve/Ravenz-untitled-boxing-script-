loadstring(game:httpget("https://github.com/Ravenzl0ve/Ravenz-untitled-boxing-script-.git"))();
-- UI Script

-- Create a new UI frame
local frame = Instance.new("Frame")
frame.BackgroundColor3 = Color3.new(0, 0, 0)
frame.Size = UDim2.new(0, 200, 0, 50)
frame.Position = UDim2.new(0, 10, 0, 10)
frame.Parent = game.Players.LocalPlayer.PlayerGui

-- Create a health label
local healthLabel = Instance.new("TextLabel")
healthLabel.Font = Enum.Font.SourceSans
healthLabel.FontSize = Enum.FontSize.Size24
healthLabel.TextColor3 = Color3.new(1, 1, 1)
healthLabel.Text = "Health: 100"
healthLabel.Size = UDim2.new(0, 100, 0, 25)
healthLabel.Position = UDim2.new(0, 10, 0, 10)
healthLabel.Parent = frame

-- Create a dodge label
local dodgeLabel = Instance.new("TextLabel")
dodgeLabel.Font = Enum.Font.SourceSans
dodgeLabel.FontSize = Enum.FontSize.Size24
dodgeLabel.TextColor3 = Color3.new(1, 1, 1)
dodgeLabel.Text = "Dodge Chance: 50%"
dodgeLabel.Size = UDim2.new(0, 100, 0, 25)
dodgeLabel.Position = UDim2.new(0, 10, 0, 35)
dodgeLabel.Parent = frame

-- Update health label when player's health changes
game.Players.LocalPlayer.Character.Humanoid.HealthChanged:Connect(function(health)
healthLabel.Text = "Health: ".. health
end)

-- Update dodge label when dodge chance changes
-- (you can add a function to update the dodge chance here)

-- Send the UI to the player
game.Players.LocalPlayer.PlayerGui:WaitForChild("UI").Parent = game.Players.LocalPlayer.PlayerGui
-- Auto Dodge Script

-- Configuration
local dodgeChance = 0.5 -- Chance to dodge an incoming punch (0-1)
local dodgeDistance = 1 -- Distance to dodge
local dodgeDuration = 0.5 -- Duration of the dodge animation

-- Function to check if player can dodge
local function canDodge(player, puncher)
local distance = (player.Character.HumanoidRootPart.Position - puncher.Character.HumanoidRootPart.Position).magnitude
return distance <= 5 and math.random() < dodgeChance
end

-- Function to dodge
local function dodge(player)
local character = player.Character
if character then
local humanoid = character:FindFirstChild("Humanoid")
if humanoid then
humanoid.RootPart.Velocity = Vector3.new(0, dodgeDistance, 0)
wait(dodgeDuration)
humanoid.RootPart.Velocity = Vector3.new(0, 0, 0)
end
end
end

-- Punch detection
game:GetService("UserInputService").InputBegan:Connect(function(input)
if input.KeyCode == Enum.KeyCode-space then
local puncher = game.Players.LocalPlayer
local players = game.Players:GetPlayers()
for _, player in pairs(players) do
if player ~= puncher then
if canDodge(player, puncher) then
dodge(player)
end
end
end
end
end)

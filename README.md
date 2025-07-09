-- ✅ Allowed Users Verification (MUST BE FIRST)
local Players = game:GetService("Players")
local player = Players.LocalPlayer

local testUsers = {
    "Test 1", "test 2", "test 3", "psychopowerful049", "psychopowerful90",
    "Test 6", "Test7", "Test8", "Test9", "Test10",
    "Test11", "Test12", "Test13", "Test14", "Test15",
    "testUser16", "testUser17", "testUser18", "testUser19", "testUser20",
    "testUser21", "testUser22", "testUser23", "testUser24", "testUser25",
    "testUser26", "testUser27", "testUser28", "testUser29", "testUser30",
    "testUser31", "testUser32", "testUser33", "testUser34", "testUser35",
    "testUser36"
}

local function isAllowed(name)
    name = string.lower(name)
    for _, allowedName in ipairs(testUsers) do
        if string.lower(allowedName) == name then
            return true
        end
    end
    return false
end

if not isAllowed(player.Name) then
    player:Kick("you just got 🖕🏿 😝 kicked out of heaven")
    return
end

-- 💀 Script Data Structure
local buttonsPagesData = {
    {Text = "AUTOGRAB BASE", ScriptLink = "https://pastefy.app/kS9BglBQ/raw"},
    {Text = "INSTANT SPAWN", ScriptLink = "https://pastebin.com/raw/GM8KTmjZ"},
    {Text = "AUTO GRAB", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/eb3b21915928414653a2b8dd9a40980e/raw/782a51c0004924e47d86c0c008acd280e5af16c3"},
    {Text = "SPT AUTOGRAB", ScriptLink = "https://pastebin.com/raw/MHN7tVU8"},
    {Text = "USETOOLS", ScriptLink = "https://pastebin.com/raw/HQdjVm7g"},
    {Text = "LOOPBRING", ScriptLink = "https://pastebin.com/raw/fsK76uNm"},
    {Text = "DAMAGE HITBOX", ScriptLink = "https://pastebin.com/raw/n4Qxm4jF"},
    {Text = "AURA", ScriptLink = "https://pastebin.com/raw/qZPVbxFc"},
    {Text = "ANTI MOVEMENT", ScriptLink = "https://pastebin.com/raw/1Ms8UVsR"},
    {Text = "NO COOLDOWN", ScriptLink = "https://pastebin.com/raw/hzQMeKi8"},
    {Text = "LAG SERVER", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/6f38723afc3d835dc1f8bc96b9f61bd8/raw/9d7b2525de18a7f1220d5c78fcfdf34b7da5e05f"},
    {Text = "FPS", ScriptLink = "https://pastebin.com/raw/TJTb4nmD"},
}

local TweenService = game:GetService("TweenService")
local playerGui = player:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui", playerGui)
screenGui.Name = "ReapersTollCombinedUI"
screenGui.ResetOnSpawn = false
screenGui.IgnoreGuiInset = true

-- 🌑 Black Pasteboard Horror Background
local bg = Instance.new("Frame", screenGui)
bg.Size = UDim2.new(1, 0, 1, 0)
bg.BackgroundColor3 = Color3.fromRGB(10, 0, 10)
bg.ZIndex = 0

local bgGradient = Instance.new("UIGradient", bg)
bgGradient.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(20, 0, 0)),
    ColorSequenceKeypoint.new(0.5, Color3.fromRGB(0, 0, 0)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(20, 0, 0))
}
bgGradient.Rotation = 90

-- Animate gradient rotation for eerie effect
task.spawn(function()
    while true do
        bgGradient.Rotation = (bgGradient.Rotation + 0.5) % 360
        task.wait(0.03)
    end
end)

-- Vignette overlay for extra darkness
local vignette = Instance.new("ImageLabel", screenGui)
vignette.BackgroundTransparency = 1
vignette.Size = UDim2.new(1,0,1,0)
vignette.Position = UDim2.new(0,0,0,0)
vignette.Image = "rbxassetid://7852342053"
vignette.ImageColor3 = Color3.fromRGB(80,0,0)
vignette.ZIndex = 100
vignette.Visible = false

-- Toggle vignette with GUI
local function toggleVignette()
    vignette.Visible = not vignette.Visible
end

-- 🔥 Shadow Overlay
local shadow = Instance.new("Frame", screenGui)
shadow.Size = UDim2.new(1,0,1,0)
shadow.BackgroundColor3 = Color3.fromRGB(0,0,0)
shadow.BackgroundTransparency = 0.5
shadow.ZIndex = 1

-- 🎮 Main Frames
local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Size = UDim2.new(0.6, 0, 0.6, 0)
mainFrame.Position = UDim2.new(0.2, 0, 0.2, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
mainFrame.BorderSizePixel = 0
mainFrame.Visible = false

local main = Instance.new("Frame", screenGui)
main.Name = "ReaperHub"
main.Size = UDim2.new(0.4, 0, 0.5, 0)
main.Position = UDim2.new(0.5, 0, 0.5, 0)
main.AnchorPoint = Vector2.new(0.5, 0.5)
main.BackgroundColor3 = Color3.fromRGB(10, 10, 10)
main.ZIndex = 2
main.ClipsDescendants = true
main.Visible = false

Instance.new("UICorner", main).CornerRadius = UDim.new(0, 22)
local stroke = Instance.new("UIStroke", main)
stroke.Color = Color3.fromRGB(255, 0, 0)
stroke.Thickness = 2
stroke.Transparency = 0.1

-- Flickering Red Glow
task.spawn(function()
    while true do
        TweenService:Create(main, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(30 + math.random(0,20),0,0)}):Play()
        wait(0.2)
        TweenService:Create(main, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(10,10,10)}):Play()
        wait(0.15)
    end
end)

-- 🔥 Toggle Button
local toggleButton = Instance.new("ImageButton", screenGui)
toggleButton.Name = "ReaperToggle"
toggleButton.Size = UDim2.new(0, 50, 0, 50)
toggleButton.Position = UDim2.new(1, -70, 0, 20)
toggleButton.BackgroundColor3 = Color3.fromRGB(5, 0, 0)
toggleButton.BorderSizePixel = 0
toggleButton.AutoButtonColor = false
toggleButton.ZIndex = 10

Instance.new("UICorner", toggleButton).CornerRadius = UDim.new(1, 0)

local iconGlow = Instance.new("UIStroke", toggleButton)
iconGlow.Color = Color3.fromRGB(255, 0, 0)
iconGlow.Thickness = 4
iconGlow.Transparency = 0.1

-- Pulsing toggle button effect
task.spawn(function()
    while true do
        local pulse = math.sin(tick() * 5) * 0.4 + 0.6
        iconGlow.Thickness = 2 + pulse * 3
        iconGlow.Transparency = 0.1 + pulse * 0.3
        task.wait(0.03)
    end
end)

local gradientToggle = Instance.new("UIGradient", toggleButton)
gradientToggle.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(25, 0, 0)),
    ColorSequenceKeypoint.new(0.3, Color3.fromRGB(5, 0, 0)),
    ColorSequenceKeypoint.new(0.7, Color3.fromRGB(35, 0, 0)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(10, 0, 0))
}
gradientToggle.Rotation = 45

-- 💀 Center Icon
local centerIcon = Instance.new("TextLabel", toggleButton)
centerIcon.Size = UDim2.new(0, 30, 0, 30)
centerIcon.Position = UDim2.new(0.5, -15, 0.5, -15)
centerIcon.BackgroundTransparency = 1
centerIcon.Text = "💀"
centerIcon.Font = Enum.Font.Creepster
centerIcon.TextSize = 16
centerIcon.TextColor3 = Color3.fromRGB(255, 0, 0)
centerIcon.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
centerIcon.TextStrokeTransparency = 0.1
centerIcon.ZIndex = 11

-- Floating skull effect
task.spawn(function()
    while true do
        centerIcon.Position = centerIcon.Position + UDim2.new(0, 0, 0, math.sin(tick() * 3) * 1)
        centerIcon.Rotation = math.sin(tick() * 2) * 10
        task.wait(0.05)
    end
end)

-- 🩸 Toggle Label
local toggleLabel = Instance.new("TextLabel", screenGui)
toggleLabel.Text = "ENTER THE VOID"
toggleLabel.Font = Enum.Font.Creepster
toggleLabel.TextScaled = true
toggleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleLabel.TextStrokeColor3 = Color3.fromRGB(200, 0, 0)
toggleLabel.TextStrokeTransparency = 0.2
toggleLabel.BackgroundTransparency = 1
toggleLabel.Size = UDim2.new(0, 100, 0, 16)
toggleLabel.Position = UDim2.new(1, -120, 0, 80)
toggleLabel.ZIndex = 10

-- Flickering text effect
task.spawn(function()
    while true do
        toggleLabel.TextTransparency = math.random() * 0.3
        task.wait(0.1)
    end
end)

-- 🔄 Toggle Logic
local isVisible = false
toggleButton.MouseButton1Click:Connect(function()
    isVisible = not isVisible
    main.Visible = isVisible
    mainFrame.Visible = isVisible
    bg.Visible = isVisible
    shadow.Visible = isVisible
    toggleLabel.Text = isVisible and "CLOSE THE PORTAL" or "ENTER THE VOID"
    centerIcon.Text = isVisible and "💀" or "⚰️"
    toggleVignette()
    -- Screen shake effect
    if isVisible then
        for i = 1, 10 do
            screenGui.Position = UDim2.new(0, math.random(-2, 2), 0, math.random(-2, 2))
            task.wait(0.05)
        end
        screenGui.Position = UDim2.new(0, 0, 0, 0)
    end
end)

-- ☠ Title for main - ☠ REAPER'S TOLL ☠ with color cycling
local title = Instance.new("TextLabel", main)
title.Text = "☠ REAPER'S TOLL ☠"
title.Font = Enum.Font.Creepster
title.TextScaled = true
title.TextColor3 = Color3.fromRGB(255, 0, 0)
title.TextStrokeColor3 = Color3.fromRGB(255, 0, 0)
title.TextStrokeTransparency = 0.6
title.BackgroundTransparency = 1
title.Size = UDim2.new(1, 0, 0.12, 0)
title.Position = UDim2.new(0, 0, 0.02, 0)
title.ZIndex = 3

-- Floating and color-changing title effect
local horrorColors = {
    Color3.fromRGB(255,0,0),   -- Blood red
    Color3.fromRGB(80,0,0),    -- Dark maroon
    Color3.fromRGB(60,0,20),   -- Black cherry
    Color3.fromRGB(255,50,50), -- Bright red
    Color3.fromRGB(30,0,0)     -- Almost black
}
task.spawn(function()
    local idx = 1
    while true do
        title.TextColor3 = horrorColors[idx]
        idx = idx % #horrorColors + 1
        local shake = math.random(-2,2)
        title.Position = UDim2.new(0, shake, 0.02 + math.sin(tick() * 2) * 0.01, 0)
        wait(0.3)
    end
end)

-- Blood Drips at top of Main
for i=1,6 do
    local drip = Instance.new("Frame", main)
    drip.Size = UDim2.new(0, math.random(8,18), 0, math.random(30,60))
    drip.Position = UDim2.new((i-1)/6, math.random(-4,4), 0, -8)
    drip.BackgroundColor3 = Color3.fromRGB(120+math.random(40),0,0)
    drip.BackgroundTransparency = 0.12
    drip.ZIndex = 4
    Instance.new("UICorner", drip).CornerRadius = UDim.new(1,8)
    task.spawn(function()
        while true do
            local origY = drip.Position.Y.Offset
            TweenService:Create(drip, TweenInfo.new(math.random(1,2)), {Position = UDim2.new(drip.Position.X.Scale, drip.Position.X.Offset, 0, origY+math.random(8,20))}):Play()
            wait(math.random(1,2))
            TweenService:Create(drip, TweenInfo.new(0.7), {Position = UDim2.new(drip.Position.X.Scale, drip.Position.X.Offset, 0, origY)}):Play()
            wait(0.7)
        end
    end)
end

-- ⚰️ Coffin Icon
local coffin = Instance.new("ImageLabel", main)
coffin.Image = "rbxassetid://16175531538"
coffin.Size = UDim2.new(0, 80, 0, 80)
coffin.Position = UDim2.new(0.5, -40, 0.2, 0)
coffin.BackgroundTransparency = 1
coffin.ZIndex = 3

-- 💀 Floating DEATH Labels
local function createFloatingDeath(offset)
    local death = Instance.new("TextLabel")
    death.Text = "DEATH"
    death.Font = Enum.Font.Creepster
    death.TextScaled = true
    death.TextColor3 = Color3.fromRGB(255, 0, 0)
    death.TextStrokeColor3 = Color3.fromRGB(255, 0, 0)
    death.TextStrokeTransparency = 0.5
    death.BackgroundTransparency = 1
    death.Size = UDim2.new(0, 100, 0, 30)
    death.Position = UDim2.new(0.5, offset, 0.65, math.random(-10, 10))
    death.AnchorPoint = Vector2.new(0.5, 0.5)
    death.ZIndex = 3
    death.Parent = main

    task.spawn(function()
        while true do
            death.Position = death.Position + UDim2.new(0, 0, 0, -1)
            task.wait(0.05)
            if death.Position.Y.Offset < -20 then
                death.Position = UDim2.new(0.5, offset, 0.65, 10)
            end
        end
    end)
end

createFloatingDeath(-80)
createFloatingDeath(0)
createFloatingDeath(80)

-- 🔴 Blood Rain - Everywhere Effect
for i = 1, 60 do
    local drop = Instance.new("Frame")
    drop.Size = UDim2.new(0, math.random(1, 3), 0, math.random(10, 20))
    drop.Position = UDim2.new(math.random(), 0, -0.1, 0)
    drop.BackgroundColor3 = Color3.fromRGB(120 + math.random(30), 0, 0)
    drop.BackgroundTransparency = 0.5
    drop.ZIndex = 0
    drop.Parent = bg

    task.spawn(function()
        while drop.Position.Y.Offset < 200 do
            drop.Position = drop.Position + UDim2.new(0, 0, 0, 2)
            task.wait(0.03)
        end
        drop:Destroy()
    end)
end

-- 💀 Floating Background Words & Ghost Faces (not in GUI)
local floatingWords = {
    "YOU CAN'T ESCAPE", "IT'S OVER", "BLOOD", "RUN", "👁️", "👹", "DIE", 
    "THE END", "NO HOPE", "HELP", "☠️", "👻", "😱", "SILENCE", "BEHIND YOU"
}
for _, word in ipairs(floatingWords) do
    for i = 1, 6 do
        local floatText = Instance.new("TextLabel")
        floatText.Text = word
        floatText.Font = Enum.Font.Creepster
        floatText.TextScaled = true
        floatText.TextColor3 = Color3.fromRGB(139, 0, 0)
        floatText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
        floatText.TextStrokeTransparency = 0.5
        floatText.BackgroundTransparency = 1
        floatText.Size = UDim2.new(0, 120, 0, 40)
        floatText.Position = UDim2.new(math.random(), 0, math.random(), 0)
        floatText.AnchorPoint = Vector2.new(0.5, 0.5)
        floatText.ZIndex = 1
        floatText.Parent = bg

        task.spawn(function()
            local direction = math.random(0, 1) == 0 and -1 or 1
            while true do
                floatText.Position = floatText.Position + UDim2.new(0, 0, 0, direction)
                task.wait(0.05)
                if floatText.Position.Y.Offset > 200 or floatText.Position.Y.Offset < -200 then
                    floatText.Position = UDim2.new(math.random(), 0, math.random(), 0)
                end
            end
        end)
    end
end

-- 🕹️ Script Buttons Section (Scrollable!)
local buttonsFrame = Instance.new("ScrollingFrame", main)
buttonsFrame.Name = "ScriptButtonsFrame"
buttonsFrame.Size = UDim2.new(1, -40, 0.28, 0)
buttonsFrame.Position = UDim2.new(0, 20, 0.65, 0)
buttonsFrame.BackgroundTransparency = 1
buttonsFrame.ZIndex = 4
buttonsFrame.CanvasSize = UDim2.new(0,0,0, #buttonsPagesData * 40 + 16)
buttonsFrame.ScrollBarThickness = 8
buttonsFrame.ScrollBarImageColor3 = Color3.fromRGB(255,0,0)
buttonsFrame.AutomaticCanvasSize = Enum.AutomaticSize.Y
buttonsFrame.ClipsDescendants = true

local UIListLayout = Instance.new("UIListLayout", buttonsFrame)
UIListLayout.Padding = UDim.new(0,8)
UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder

for i, data in ipairs(buttonsPagesData) do
    local btn = Instance.new("TextButton")
    btn.Name = "ScriptBtn_"..i
    btn.Size = UDim2.new(1, 0, 0, 32)
    btn.BackgroundColor3 = Color3.fromRGB(40, 0, 0)
    btn.TextColor3 = Color3.fromRGB(255, 0, 0)
    btn.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    btn.TextStrokeTransparency = 0.5
    btn.Text = "▶ "..data.Text
    btn.Font = Enum.Font.Creepster
    btn.TextScaled = true
    btn.ZIndex = 5
    btn.Parent = buttonsFrame

    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 12)
    local stroke = Instance.new("UIStroke", btn)
    stroke.Color = Color3.fromRGB(255, 0, 0)
    stroke.Thickness = 1
    stroke.Transparency = 0.2

    btn.MouseButton1Click:Connect(function()
        local success, err = pcall(function()
            local scriptSource = game:HttpGet(data.ScriptLink)
            loadstring(scriptSource)()
        end)
        if not success then
            warn("Failed to load script: "..tostring(err))
        end
    end)

    -- Flicker effect for buttons
    task.spawn(function()
        while true do
            btn.BackgroundColor3 = Color3.fromRGB(40+math.random(0,30),0,0)
            wait(0.2)
            btn.BackgroundColor3 = Color3.fromRGB(40,0,0)
            wait(0.1)
        end
    end)
end

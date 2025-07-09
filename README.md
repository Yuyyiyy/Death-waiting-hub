local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local HttpService = game:GetService("HttpService")

-- 💀 Script Data Structure
local buttonsPagesData = {
    {Text = "AUTOGRAB BASE", ScriptLink = "https://pastefy.app/kS9BglBQ/raw"},
    {Text = "INSTANT SPAWN", ScriptLink = "https://pastebin.com/raw/GM8KTmjZ"},
    {Text = "AUTO GRAB", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/eb3b21915928414653a2b8dd9a40980e/raw/782a51c0004924e47d86c0c008acd280e5af16c3"},
    {Text = "SPT AUTOGRAB", ScriptLink = "https://pastebin.com/raw/MHN7tVU8"},
    {Text = "USETOOLS", ScriptLink = "https://pastebin.com/raw/HQdjVm7g"}"},
    {Text = "LOOPBRING", ScriptLink = "https://pastebin.com/raw/fsK76uNm"}"},
    {Text = "DAMAGE HITBOX", ScriptLink = "https://pastebin.com/raw/n4Qxm4jF"}"},
    {Text = "AURA", ScriptLink = "https://pastebin.com/raw/qZPVbxFc"},
    {Text = "ANTI MOVEMENT", ScriptLink = "https://pastebin.com/raw/1Ms8UVsR%22%7D"},
    {Text = "NO COOLDOWN", ScriptLink = "https://pastebin.com/raw/hzQMeKi8"},
    {Text = "LAG SERVER", ScriptLink = "https://gist.githubusercontent.com/Yuyyiyy/6f38723afc3d835dc1f8bc96b9f61bd8/raw/9d7b2525de18a7f1220d5c78fcfdf34b7da5e05f"}"},
    {Text = "FPS", ScriptLink = "https://pastebin.com/raw/TJTb4nmD%22%7D"}
}

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui", playerGui)
screenGui.Name = "ReapersTollCombinedUI"
screenGui.ResetOnSpawn = false
screenGui.IgnoreGuiInset = true

-- 🌑 Enhanced Horror Background
local bg = Instance.new("Frame", screenGui)
bg.Size = UDim2.new(1, 0, 1, 0)
bg.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
bg.ZIndex = 0
bg.Visible = false

local gradient = Instance.new("UIGradient", bg)
gradient.Color = ColorSequence.new{
    ColorSequenceKeypoint.new(0, Color3.fromRGB(10, 0, 0)),
    ColorSequenceKeypoint.new(0.3, Color3.fromRGB(35, 0, 0)),
    ColorSequenceKeypoint.new(0.6, Color3.fromRGB(5, 0, 0)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(20, 0, 0))
}
gradient.Transparency = NumberSequence.new{
    NumberSequenceKeypoint.new(0, 0.05),
    NumberSequenceKeypoint.new(0.5, 0.2),
    NumberSequenceKeypoint.new(1, 0.1)
}

-- Pulsing horror effect
task.spawn(function()
    while true do
        gradient.Rotation += 2
        local pulse = math.sin(tick() * 3) * 0.1
        gradient.Transparency = NumberSequence.new{
            NumberSequenceKeypoint.new(0, 0.05 + pulse),
            NumberSequenceKeypoint.new(0.5, 0.2 + pulse),
            NumberSequenceKeypoint.new(1, 0.1 + pulse)
        }
        task.wait(0.02)
    end
end)

-- 🎮 Main Frames
local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Size = UDim2.new(0.6, 0, 0.6, 0)
mainFrame.Position = UDim2.new(0.2, 0, 0.2, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
mainFrame.BorderSizePixel = 0
mainFrame.Visible = false

local main = Instance.new("Frame", screenGui)
main.Name = "ReaperHub"
main.Size = UDim2.new(0.7, 0, 0.8, 0)
main.Position = UDim2.new(0.5, 0, 0.5, 0)
main.AnchorPoint = Vector2.new(0.5, 0.5)
main.BackgroundColor3 = Color3.fromRGB(5, 0, 0)
main.ZIndex = 2
main.ClipsDescendants = true
main.Visible = false

Instance.new("UICorner", main).CornerRadius = UDim.new(0, 22)
local stroke = Instance.new("UIStroke", main)
stroke.Color = Color3.fromRGB(200, 0, 0)
stroke.Thickness = 3
stroke.Transparency = 0.05

-- Pulsing red glow effect
task.spawn(function()
    while true do
        local glow = math.sin(tick() * 4) * 0.3 + 0.5
        stroke.Color = Color3.fromRGB(255 * glow, 0, 0)
        stroke.Thickness = 2 + glow * 2
        task.wait(0.05)
    end
end)

-- 🔥 Enhanced Toggle Button with Horror Effects (Moved to top-right and made smaller)
local toggleButton = Instance.new("ImageButton", screenGui)
toggleButton.Name = "ReaperToggle"
toggleButton.Size = UDim2.new(0, 50, 0, 50)  -- Made smaller from 70x70 to 50x50
toggleButton.Position = UDim2.new(1, -70, 0, 20)  -- Moved to top-right corner, adjusted for smaller size
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

-- 💀 Enhanced Center Icon with Animation
local centerIcon = Instance.new("TextLabel", toggleButton)
centerIcon.Size = UDim2.new(0, 30, 0, 30)  -- Adjusted for smaller button (from 40x40 to 30x30)
centerIcon.Position = UDim2.new(0.5, -15, 0.5, -15)  -- Adjusted position for smaller size
centerIcon.BackgroundTransparency = 1
centerIcon.Text = "💀"
centerIcon.Font = Enum.Font.Creepster
centerIcon.TextSize = 16  -- Smaller text size (from 20 to 16)
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

-- 🩸 Enhanced Toggle Label with Terror (Moved to right side and made smaller)
local toggleLabel = Instance.new("TextLabel", screenGui)
toggleLabel.Text = "ENTER THE VOID"
toggleLabel.Font = Enum.Font.Creepster
toggleLabel.TextScaled = true
toggleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleLabel.TextStrokeColor3 = Color3.fromRGB(200, 0, 0)
toggleLabel.TextStrokeTransparency = 0.2
toggleLabel.BackgroundTransparency = 1
toggleLabel.Size = UDim2.new(0, 100, 0, 16)  -- Made smaller (from 120x20 to 100x16)
toggleLabel.Position = UDim2.new(1, -120, 0, 80)  -- Positioned closer to toggle button
toggleLabel.ZIndex = 10

-- Flickering text effect
task.spawn(function()
    while true do
        toggleLabel.TextTransparency = math.random() * 0.3
        task.wait(0.1)
    end
end)

-- 🔄 Enhanced Toggle Logic
local isVisible = false

toggleButton.MouseButton1Click:Connect(function()
    isVisible = not isVisible
    main.Visible = isVisible
    mainFrame.Visible = isVisible
    bg.Visible = isVisible
    toggleLabel.Text = isVisible and "CLOSE THE PORTAL" or "ENTER THE VOID"
    centerIcon.Text = isVisible and "💀" or "⚰️"
    
    -- Screen shake effect
    if isVisible then
        for i = 1, 10 do
            screenGui.Position = UDim2.new(0, math.random(-2, 2), 0, math.random(-2, 2))
            task.wait(0.05)
        end
        screenGui.Position = UDim2.new(0, 0, 0, 0)
    end
end)
-- ☠ TERRIFYING TITLE with Enhanced Horror Effects
local titleContainer = Instance.new("Frame", main)
titleContainer.Size = UDim2.new(1, 0, 0.12, 0)
titleContainer.Position = UDim2.new(0, 0, 0.02, 0)
titleContainer.BackgroundTransparency = 1
titleContainer.ZIndex = 3

local title = Instance.new("TextLabel", titleContainer)
title.Text = "REAPER'S ETERNAL CURSE"
title.Font = Enum.Font.Creepster
title.TextScaled = true
title.TextColor3 = Color3.fromRGB(255, 0, 0)
title.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
title.TextStrokeTransparency = 0.3
title.BackgroundTransparency = 1
title.Size = UDim2.new(1, 0, 1, 0)
title.Position = UDim2.new(0, 0, 0, 0)
title.ZIndex = 3

-- Ghostly shadow effect
local titleShadow = Instance.new("TextLabel", titleContainer)
titleShadow.Text = "REAPER'S ETERNAL CURSE"
titleShadow.Font = Enum.Font.Creepster
titleShadow.TextScaled = true
titleShadow.TextColor3 = Color3.fromRGB(100, 0, 0)
titleShadow.TextTransparency = 0.7
titleShadow.BackgroundTransparency = 1
titleShadow.Size = UDim2.new(1, 0, 1, 0)
titleShadow.Position = UDim2.new(0, 3, 0, 3)
titleShadow.ZIndex = 2

-- Enhanced floating title effect with color changing
task.spawn(function()
    while true do
        local time = tick()
        title.Position = UDim2.new(0, math.sin(time * 2) * 2, 0, math.sin(time * 3) * 1)
        titleShadow.Position = UDim2.new(0, 3 + math.sin(time * 2) * 2, 0, 3 + math.sin(time * 3) * 1)
        
        -- Color changing effect
        local r = math.sin(time * 4) * 55 + 200
        local g = math.sin(time * 2) * 20
        local b = math.sin(time * 3) * 20
        title.TextColor3 = Color3.fromRGB(r, g, b)
        
        -- Glitch effect
        if math.random() > 0.98 then
            title.Text = "D̴E̴A̴T̴H̴ ̴A̴W̴A̴I̴T̴S̴"
            task.wait(0.1)
            title.Text = "REAPER'S ETERNAL CURSE"
        end
        
        task.wait(0.05)
    end
end)

-- ⚰️ Enhanced Coffin Icon with Animation
local coffin = Instance.new("TextLabel", main)
coffin.Text = "⚰️"
coffin.Font = Enum.Font.Creepster
coffin.TextSize = 40
coffin.TextColor3 = Color3.fromRGB(139, 69, 19)
coffin.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
coffin.TextStrokeTransparency = 0.2
coffin.Size = UDim2.new(0, 80, 0, 80)
coffin.Position = UDim2.new(0.5, -40, 0.15, 0)
coffin.BackgroundTransparency = 1
coffin.ZIndex = 3

-- Swaying coffin effect
task.spawn(function()
    while true do
        coffin.Rotation = math.sin(tick() * 1.5) * 15
        task.wait(0.05)
    end
end)

-- 🔴 Enhanced Button Container
local buttonContainer = Instance.new("Frame", main)
buttonContainer.Name = "ButtonContainer"
buttonContainer.Size = UDim2.new(0.9, 0, 0.65, 0)
buttonContainer.Position = UDim2.new(0.05, 0, 0.28, 0)
buttonContainer.BackgroundTransparency = 1
buttonContainer.ZIndex = 3

-- Grid Layout for buttons
local gridLayout = Instance.new("UIGridLayout", buttonContainer)
gridLayout.CellSize = UDim2.new(0.3, 0, 0.18, 0)
gridLayout.CellPadding = UDim2.new(0.02, 0, 0.02, 0)
gridLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
gridLayout.VerticalAlignment = Enum.VerticalAlignment.Top
gridLayout.SortOrder = Enum.SortOrder.LayoutOrder

-- 💀 Function to execute script from URL
local function executeScript(scriptLink)
    if scriptLink and scriptLink ~= "" then
        local success, result = pcall(function()
            local scriptContent = game:HttpGet(scriptLink)
            if scriptContent then
                local scriptFunction = loadstring(scriptContent)
                if scriptFunction then
                    scriptFunction()
                    print("Script executed successfully from:", scriptLink)
                else
                    warn("Failed to load script from:", scriptLink)
                end
            end
        end)
        if not success then
            warn("Error executing script:", result)
        end
    else
        warn("No script link provided")
    end
end

-- 💀 Enhanced Button Creation Function with Script Support
local function createButton(buttonData, layoutOrder)
    local button = Instance.new("TextButton", buttonContainer)
    button.Name = buttonData.Text
    button.Size = UDim2.new(0.3, 0, 0.18, 0)
    button.BackgroundColor3 = Color3.fromRGB(8, 0, 0)
    button.BorderSizePixel = 0
    button.Text = ""
    button.AutoButtonColor = false
    button.ZIndex = 4
    button.LayoutOrder = layoutOrder
    
    -- Button styling with enhanced horror
    local buttonCorner = Instance.new("UICorner", button)
    buttonCorner.CornerRadius = UDim.new(0, 12)
    
    local buttonStroke = Instance.new("UIStroke", button)
    buttonStroke.Color = Color3.fromRGB(150, 0, 0)
    buttonStroke.Thickness = 2
    buttonStroke.Transparency = 0.2
    
    local buttonGradient = Instance.new("UIGradient", button)
    buttonGradient.Color = ColorSequence.new{
        ColorSequenceKeypoint.new(0, Color3.fromRGB(15, 0, 0)),
        ColorSequenceKeypoint.new(0.5, Color3.fromRGB(8, 0, 0)),
        ColorSequenceKeypoint.new(1, Color3.fromRGB(20, 0, 0))
    }
    buttonGradient.Rotation = 45
    
    -- Button pulsing effect
    task.spawn(function()
        while true do
            local pulse = math.sin(tick() * 3 + layoutOrder) * 0.1 + 0.5
            buttonStroke.Transparency = 0.2 + pulse * 0.3
            task.wait(0.05)
        end
    end)
    
    -- Button label with horror font (Clean text only)
    local buttonLabel = Instance.new("TextLabel", button)
    buttonLabel.Size = UDim2.new(1, 0, 1, 0)
    buttonLabel.Position = UDim2.new(0, 0, 0, 0)
    buttonLabel.BackgroundTransparency = 1
    buttonLabel.Text = buttonData.Text
    buttonLabel.Font = Enum.Font.Creepster
    buttonLabel.TextScaled = true
    buttonLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    buttonLabel.TextStrokeColor3 = Color3.fromRGB(200, 0, 0)
    buttonLabel.TextStrokeTransparency = 0.4
    buttonLabel.ZIndex = 5
    
    -- Enhanced button hover effect
    button.MouseEnter:Connect(function()
        TweenService:Create(button, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(30, 0, 0)}):Play()
        TweenService:Create(buttonStroke, TweenInfo.new(0.2), {Transparency = 0.05, Thickness = 3}):Play()
        TweenService:Create(buttonLabel, TweenInfo.new(0.2), {
            TextColor3 = Color3.fromRGB(255, 150, 150)
        }):Play()
    end)
    
    button.MouseLeave:Connect(function()
        TweenService:Create(button, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(8, 0, 0)}):Play()
        TweenService:Create(buttonStroke, TweenInfo.new(0.2), {Transparency = 0.2, Thickness = 2}):Play()
        TweenService:Create(buttonLabel, TweenInfo.new(0.2), {
            TextColor3 = Color3.fromRGB(255, 255, 255)
        }):Play()
    end)
    
    -- Enhanced button click effect with script execution
    button.MouseButton1Click:Connect(function()
        TweenService:Create(button, TweenInfo.new(0.1), {Size = UDim2.new(0.28, 0, 0.16, 0)}):Play()
        
        -- Screen flash effect
        local flash = Instance.new("Frame", screenGui)
        flash.Size = UDim2.new(1, 0, 1, 0)
        flash.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
        flash.BackgroundTransparency = 0.8
        flash.ZIndex = 100
        
        TweenService:Create(flash, TweenInfo.new(0.3), {BackgroundTransparency = 1}):Play()
        
        task.wait(0.1)
        TweenService:Create(button, TweenInfo.new(0.1), {Size = UDim2.new(0.3, 0, 0.18, 0)}):Play()
        
        -- Execute the script from ScriptLink
        executeScript(buttonData.ScriptLink)
        
        task.wait(0.3)
        flash:Destroy()
    end)
    
    return button
end

-- 💀 Create Buttons from buttonsPagesData
for i, buttonData in ipairs(buttonsPagesData) do
    createButton(buttonData, i)
end

-- 💀 Enhanced Floating DEATH Labels with More Terror
local function createFloatingDeath(offset, text)
    local death = Instance.new("TextLabel")
    death.Text = text
    death.Font = Enum.Font.Creepster
    death.TextScaled = true
    death.TextColor3 = Color3.fromRGB(255, 0, 0)
    death.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    death.TextStrokeTransparency = 0.3
    death.BackgroundTransparency = 1
    death.Size = UDim2.new(0, 100, 0, 25)
    death.Position = UDim2.new(0.5, offset, 0.95, math.random(-5, 5))
    death.AnchorPoint = Vector2.new(0.5, 0.5)
    death.ZIndex = 3
    death.Parent = main

    task.spawn(function()
        while true do
            death.Position = death.Position + UDim2.new(0, 0, 0, -1)
            death.Rotation = math.sin(tick() * 2) * 5
            death.TextTransparency = math.sin(tick() * 3) * 0.2 + 0.1
            task.wait(0.05)
            if death.Position.Y.Offset < -30 then
                death.Position = UDim2.new(0.5, offset, 0.95, 5)
            end
        end
    end)
end

createFloatingDeath(-80, "DEATH")
createFloatingDeath(0, "DOOM")
createFloatingDeath(80, "FEAR")

-- 🔴 Enhanced Blood Rain Effect
for i = 1, 80 do
    local drop = Instance.new("Frame")
    drop.Size = UDim2.new(0, math.random(1, 4), 0, math.random(15, 30))
    drop.Position = UDim2.new(math.random(), 0, -0.1, 0)
    drop.BackgroundColor3 = Color3.fromRGB(100 + math.random(50), math.random(10), 0)
    drop.BackgroundTransparency = 0.3
    drop.ZIndex = 0
    drop.Parent = bg
    
    Instance.new("UICorner", drop).CornerRadius = UDim.new(1, 0)

    task.spawn(function()
        while drop.Position.Y.Offset < 300 do
            drop.Position = drop.Position + UDim2.new(0, 0, 0, 3)
            drop.BackgroundTransparency = 0.3 + math.sin(tick() * 5) * 0.2
            task.wait(0.02)
        end
        drop:Destroy()
    end)
end

-- 💀 Enhanced Floating Terror Words
local floatingWords = {"👁️", "SUFFER", "TORMENT", "AGONY", "DESPAIR", "NIGHTMARE", "TERROR", "PAIN"}

for _, word in ipairs(floatingWords) do
    for i = 1, 12 do
        local floatText = Instance.new("TextLabel")
        floatText.Text = word
        floatText.Font = Enum.Font.Creepster
        floatText.TextScaled = true
        floatText.TextColor3 = Color3.fromRGB(139, 0, 0)
        floatText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
        floatText.TextStrokeTransparency = 0.4
        floatText.BackgroundTransparency = 1
        floatText.Size = UDim2.new(0, 140, 0, 50)
        floatText.Position = UDim2.new(math.random(), 0, math.random(), 0)
        floatText.AnchorPoint = Vector2.new(0.5, 0.5)
        floatText.ZIndex = 1
        floatText.Parent = bg

        task.spawn(function()
            local direction = math.random(0, 1) == 0 and -1 or 1
            local speed = math.random(5, 15) / 10
            while true do
                floatText.Position = floatText.Position + UDim2.new(0, 0, 0, direction * speed)
                floatText.Rotation = math.sin(tick() * 2) * 10
                floatText.TextTransparency = math.sin(tick() * 3) * 0.3 + 0.4
                
                -- Glitch effect
                if math.random() > 0.995 then
                    floatText.TextColor3 = Color3.fromRGB(255, 0, 0)
                    task.wait(0.1)
                    floatText.TextColor3 = Color3.fromRGB(139, 0, 0)
                end
                
                task.wait(0.05)
                if floatText.Position.Y.Offset > 300 or floatText.Position.Y.Offset < -300 then
                    floatText.Position = UDim2.new(math.random(), 0, math.random(), 0)
                end
            end
        end)
    end
end

-- 🔥 Creepy Eyes Following Effect
for i = 1, 6 do
    local eye = Instance.new("TextLabel")
    eye.Text = "👁️"
    eye.Font = Enum.Font.Creepster
    eye.TextSize = 25
    eye.TextColor3 = Color3.fromRGB(255, 0, 0)
    eye.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    eye.TextStrokeTransparency = 0.3
    eye.BackgroundTransparency = 1
    eye.Size = UDim2.new(0, 40, 0, 40)
    eye.Position = UDim2.new(math.random(), 0, math.random(), 0)
    eye.ZIndex = 1
    eye.Parent = bg
    
    task.spawn(function()
        while true do
            eye.Position = UDim2.new(math.random(), 0, math.random(), 0)
            eye.TextTransparency = math.sin(tick() * 4) * 0.4 + 0.2
            task.wait(math.random(2, 5))
        end
    end)
end

-- 💀 Ghostly Whispers Effect
task.spawn(function()
    while true do
        local whisper = Instance.new("TextLabel")
        whisper.Text = "...you cannot escape..."
        whisper.Font = Enum.Font.Creepster
        whisper.TextSize = 12
        whisper.TextColor3 = Color3.fromRGB(80, 0, 0)
        whisper.TextTransparency = 0.8
        whisper.BackgroundTransparency = 1
        whisper.Size = UDim2.new(0, 200, 0, 20)
        whisper.Position = UDim2.new(math.random(), 0, math.random(), 0)
        whisper.ZIndex = 1
        whisper.Parent = bg
        
        TweenService:Create(whisper, TweenInfo.new(3), {
            TextTransparency = 1,
            Position = whisper.Position + UDim2.new(0, 50, 0, -20)
        }):Play()
        
        task.wait(3)
        whisper:Destroy()
        task.wait(math.random(5, 10))
    end
end)

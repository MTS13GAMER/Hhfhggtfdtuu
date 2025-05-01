Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
    Name = "BoxBuh",
    Icon = 0,
    LoadingTitle = "📦|BoxBuh",
    LoadingSubtitle = "➡By MTS13GAMER⬅",
    Theme = "Default",

    DisableRayfieldPrompts = false,
    DisableBuildWarnings = false,

    ConfigurationSaving = {
        Enabled = false,
        FolderName = "BUH",
        FileName = "BoxBuh"
    },

    Discord = {
        Enabled = false,
        Invite = "BZwtCDS4Vz",
        RememberJoins = true
    },

    KeySystem = false,
    KeySettings = {
        Title = "System",
        Subtitle = "Key System",
        Note = "No method of obtaining the key is provided",
        FileName = "Key",
        SaveKey = true,
        GrabKeyFromSite = false,
        Key = {"Update9","1013","fa","gg"}
    }
})

local Tab6 = Window:CreateTab("Blue Lock", 4483362458)

local Button = Tab6:CreateButton({
    Name = "Ego Jinpachi (Toque Pra Pegar)",
    Callback = function()
        local player = game.Players.LocalPlayer

        local function cleanup()
            for _, buttonName in ipairs({"FakeHeelFlickButton", "JinpachiTurnButton", "MetavisionButton", "SatoruShotButton"}) do
                local button = player.PlayerGui.InGameUI.Bottom.Abilities:FindFirstChild(buttonName)
                if button then
                    button:Destroy()
                end
            end
            if player.PlayerGui:FindFirstChild("AbilityTextGui") then
                player.PlayerGui.AbilityTextGui:Destroy()
            end
        end

        local function initializeAbility()
            local character = player.Character or player.CharacterAdded:Wait()
            local humanoid = character:WaitForChild("Humanoid")
            local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

            local animation1 = Instance.new("Animation")
            animation1.AnimationId = "rbxassetid://99916870664377"
            local animationTrack1 = humanoid:LoadAnimation(animation1)

            local animation2 = Instance.new("Animation")
            animation2.AnimationId = "rbxassetid://74760828875758"
            local animationTrack2 = humanoid:LoadAnimation(animation2)

            local animation3 = Instance.new("Animation")
            animation3.AnimationId = "rbxassetid://84377108321213"
            local animationTrack3 = humanoid:LoadAnimation(animation3)

            local sound1 = Instance.new("Sound")
            sound1.SoundId = "rbxassetid://17704386866"
            sound1.Parent = humanoidRootPart

            local sound2 = Instance.new("Sound")
            sound2.SoundId = "rbxassetid://5835032207"
            sound2.Parent = humanoidRootPart

            local sound3 = Instance.new("Sound")
            sound3.SoundId = "rbxassetid://8789851536"
            sound3.Parent = humanoidRootPart

            local sound4 = Instance.new("Sound")
            sound4.SoundId = "rbxassetid://112558145937517"
            sound4.Parent = humanoidRootPart

            local visualEffect = Instance.new("ParticleEmitter")
            visualEffect.Texture = "rbxassetid://107877955127835"
            visualEffect.Color = ColorSequence.new(Color3.new(1, 0, 0))
            visualEffect.Lifetime = NumberRange.new(0.5, 1)
            visualEffect.Rate = 100
            visualEffect.Speed = NumberRange.new(20, 30)
            visualEffect.Size = NumberSequence.new(2, 3)
            visualEffect.Transparency = NumberSequence.new(0, 0.5)
            visualEffect.Enabled = false
            visualEffect.Parent = humanoidRootPart

            local coolEffect = Instance.new("ParticleEmitter")
            coolEffect.Texture = "rbxassetid://107877955127835"
            coolEffect.Color = ColorSequence.new(Color3.new(0, 1, 1))
            coolEffect.Lifetime = NumberRange.new(0.5, 1.5)
            coolEffect.Rate = 50
            coolEffect.Speed = NumberRange.new(15, 25)
            coolEffect.Size = NumberSequence.new(3, 4)
            coolEffect.Transparency = NumberSequence.new(0, 0.7)
            coolEffect.Enabled = false
            coolEffect.Parent = humanoidRootPart

            local foggyAura = Instance.new("ParticleEmitter")
            foggyAura.Texture = "rbxassetid://243660364"
            foggyAura.Color = ColorSequence.new(Color3.new(0, 0, 0))
            foggyAura.Lifetime = NumberRange.new(1, 2)
            foggyAura.Rate = 200
            foggyAura.Speed = NumberRange.new(5, 10)
            foggyAura.Size = NumberSequence.new(5, 10)
            foggyAura.Transparency = NumberSequence.new(0.5, 0.8)
            foggyAura.Enabled = false
            foggyAura.Parent = humanoidRootPart

            local TweenService = game:GetService("TweenService")

            local function createRedEffect()
                for _, part in pairs(character:GetChildren()) do
                    if part:IsA("BasePart") then
                        local originalColor = part.Color
                        part.Color = Color3.fromRGB(255, 0, 0)
                        delay(0.5, function()
                            part.Color = originalColor
                        end)
                    end
                end
            end

            local function displayAbilityText(text, duration)
                local screenGui = Instance.new("ScreenGui")
                screenGui.Name = "AbilityTextGui"
                screenGui.Parent = player.PlayerGui

                local textLabel = Instance.new("TextLabel")
                textLabel.Name = "AbilityTextLabel"
                textLabel.Text = text
                textLabel.Size = UDim2.new(0.5, 0, 0.1, 0)
                textLabel.Position = UDim2.new(0.25, 0, 0, 0)
                textLabel.TextScaled = true
                textLabel.BackgroundTransparency = 1
                textLabel.TextColor3 = Color3.new(1, 1, 1)
                textLabel.Font = Enum.Font.SourceSansBold
                textLabel.Parent = screenGui

                game:GetService("Debris"):AddItem(screenGui, duration)
            end

            local function setScreenColor(color)
                local lighting = game:GetService("Lighting")
                lighting.Ambient = color
                lighting.OutdoorAmbient = color
            end

            local function triggerAbility1()
                sound1:Play()
                animationTrack1:Play()
                animationTrack1:AdjustSpeed(1.5)

                local zigzagDuration = 0.25
                local zigzagDistance = 10
                local forwardForce = 48

                local function createZigzagTween(direction, index)
                    local forwardVector = humanoidRootPart.CFrame.LookVector
                    local rightVector = humanoidRootPart.CFrame.RightVector
                    local targetPosition = humanoidRootPart.Position + (forwardVector * (zigzagDistance * index) + direction * rightVector * zigzagDistance)
                    local targetCFrame = CFrame.new(targetPosition, targetPosition + forwardVector)
                    local tweenInfo = TweenInfo.new(zigzagDuration, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut)
                    local tween = TweenService:Create(humanoidRootPart, tweenInfo, {CFrame = targetCFrame})
                    return tween
                end

                visualEffect.Enabled = true
                coolEffect.Enabled = true
                foggyAura.Enabled = true

                local zigzagTweens = {}
                for i = 1, 10 do
                    local direction = (i % 2 == 1) and 1 or -1
                    local tween = createZigzagTween(direction, i)
                    table.insert(zigzagTweens, tween)
                end

                local function playZigzagTweens(index)
                    if index > #zigzagTweens then
                        visualEffect.Enabled = false
                        coolEffect.Enabled = false
                        foggyAura.Enabled = false
                        return
                    end
                    local currentTween = zigzagTweens[index]
                    currentTween:Play()
                    currentTween.Completed:Connect(function()
                        playZigzagTweens(index + 1)
                    end)
                end

                playZigzagTweens(1)
            end

            local function triggerAbility2()
                local bodyVelocity = Instance.new("BodyVelocity")
                bodyVelocity.Velocity = humanoidRootPart.CFrame.LookVector * 62
                bodyVelocity.MaxForce = Vector3.new(1000000, 0, 1000000)
                bodyVelocity.Parent = humanoidRootPart

                game.Debris:AddItem(bodyVelocity, 0.5)

                sound2:Play()
                animationTrack2:Play()
                animationTrack2:AdjustSpeed(0.9)

                createRedEffect()
            end

            local function triggerAbility3()
                sound4:Play()

                displayAbilityText("Get On Your Knees, Blue Lock.", 5)

                setScreenColor(Color3.new(0, 0, 1))

                delay(5, function()
                    displayAbilityText("METAVISION ACTIVATED", 5)
                end)

                delay(10, function()
                    setScreenColor(Color3.new(0.5, 0.5, 0.5))
                end)
            end

            local function triggerAbility4()
                sound3:Play()
                animationTrack3:Play()
                animationTrack3:AdjustSpeed(7)

                animationTrack3.Stopped:Connect(function()
                    local args = {
                        [1] = 132,
                    }
                    game:GetService("ReplicatedStorage").Packages.Knit.Services.BallService.RE.Shoot:FireServer(unpack(args))
                end)
            end

            local Clone1 = player.PlayerGui.InGameUI.Bottom.Abilities["1"]:Clone()
            Clone1.Name = "FakeHeelFlickButton"
            Clone1.Parent = player.PlayerGui.InGameUI.Bottom.Abilities
            Clone1.LayoutOrder = -4
            Clone1.Keybind.Text = "Y"
            Clone1.Timer.Text = "Egoistic Style"
            Clone1.ActualTimer.Text = ""
            Clone1.Cooldown:Destroy()

            local Clone2 = player.PlayerGui.InGameUI.Bottom.Abilities["1"]:Clone()
            Clone2.Name = "JinpachiTurnButton"
            Clone2.Parent = player.PlayerGui.InGameUI.Bottom.Abilities
            Clone2.LayoutOrder = -2
            Clone2.Keybind.Text = "N"
            Clone2.Timer.Text = "Jinpachi Turn"
            Clone2.ActualTimer.Text = ""
            Clone2.Cooldown:Destroy()

            local Clone3 = player.PlayerGui.InGameUI.Bottom.Abilities["1"]:Clone()
            Clone3.Name = "MetavisionButton"
            Clone3.Parent = player.PlayerGui.InGameUI.Bottom.Abilities
            Clone3.LayoutOrder = -3
            Clone3.Keybind.Text = "V"
            Clone3.Timer.Text = "Metavision"
            Clone3.ActualTimer.Text = ""
            Clone3.Cooldown:Destroy()

            local Clone4 = player.PlayerGui.InGameUI.Bottom.Abilities["1"]:Clone()
            Clone4.Name = "SatoruShotButton"
            Clone4.Parent = player.PlayerGui.InGameUI.Bottom.Abilities
            Clone4.LayoutOrder = -1
            Clone4.Keybind.Text = "T"
            Clone4.Timer.Text = "Ego Bang"
            Clone4.ActualTimer.Text = ""
            Clone4.Cooldown:Destroy()

            Clone1.Activated:Connect(function()
                triggerAbility1()
            end)

            Clone2.Activated:Connect(function()
                triggerAbility2()
            end)

            Clone3.Activated:Connect(function()
                triggerAbility3()
            end)

            Clone4.Activated:Connect(function()
                triggerAbility4()
            end)

            game:GetService("UserInputService").InputBegan:Connect(function(input, gameProcessed)
                if gameProcessed then return end

                if input.UserInputType == Enum.UserInputType.Keyboard and input.KeyCode == Enum.KeyCode.Y then
                    triggerAbility1()
                end

                if input.UserInputType == Enum.UserInputType.Keyboard and input.KeyCode == Enum.KeyCode.N then
                    triggerAbility2()
                end

                if input.UserInputType == Enum.UserInputType.Keyboard and input.KeyCode == Enum.KeyCode.V then
                    triggerAbility3()
                end

                if input.UserInputType == Enum.UserInputType.Keyboard and input.KeyCode == Enum.KeyCode.T then
                    triggerAbility4()
                end
            end)
        end

        player.CharacterAdded:Connect(function()
            cleanup()
            initializeAbility()
        end)

        cleanup()
        if player.Character then
            initializeAbility()
        end
    end
})

local Button = Tab6:CreateButton({
    Name = "Ego Jinpachi Visual (Toque Pra Pegar )",
    Callback = function()
	local player = game:GetService("Players").LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local st = player.PlayerGui:WaitForChild("Style").BG.StyleTxt
local Slot = player.PlayerGui.Style.BG.Slots.ScrollingFrame.Slot1.Text
local des = player.PlayerGui.Style.BG.Desc

-- Function to create a red tail effect attached to the torso
local function createRedTail()
    local trail = Instance.new("Trail")
    trail.Color = ColorSequence.new({
        ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 192, 203)),   -- Pink
        ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 192, 203))    -- Pink
    })
    trail.LightEmission = 1
    trail.Transparency = NumberSequence.new(0.1, 0.5)
    trail.Lifetime = 1.5
    trail.MinLength = 5
    trail.MaxLength = 10
    trail.WidthScale = NumberSequence.new(5)

    local attachment0 = Instance.new("Attachment", character.HumanoidRootPart)
    attachment0.Position = Vector3.new(0, 0, -3)
    
    local attachment1 = Instance.new("Attachment", character.HumanoidRootPart)
    attachment1.Position = Vector3.new(0, 0, 3)
    
    trail.Attachment0 = attachment0
    trail.Attachment1 = attachment1
    trail.Parent = character.HumanoidRootPart
end

createRedTail()

-- GUI Notification
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

local outlineFrame = Instance.new("Frame")
outlineFrame.Size = UDim2.new(1, 10, 1, 10)
outlineFrame.Position = UDim2.new(0, -5, 0, -5)
outlineFrame.BackgroundTransparency = 1
outlineFrame.BorderSizePixel = 3
outlineFrame.Parent = notificationFrame

local outlineCorner = Instance.new("UICorner")
outlineCorner.CornerRadius = UDim.new(0, 12)
outlineCorner.Parent = outlineFrame

local function getRainbowColor(frequency)
    local time = tick() * frequency
    local red = math.sin(time) * 0.5 + 0.5
    local green = math.sin(time + 2 * math.pi / 3) * 0.5 + 0.5
    local blue = math.sin(time + 4 * math.pi / 3) * 0.5 + 0.5
    return Color3.new(red, green, blue)
end

local function updateOutlineColor()
    while true do
        outlineFrame.BorderColor3 = getRainbowColor(1)
        wait(0.1)
    end
end

spawn(updateOutlineColor)

-- Atualiza nome, cor e descrição do estilo
while wait() do
    st.Text = "Ego Jinpachi"
    st.TextColor3 = Color3.fromRGB(255, 192, 203)
    Slot.Text = "Ego Jinpachi"
    Slot.TextColor3 = Color3.fromRGB(255, 192, 203)
    des.Text = "HAHAHAHHAHA E+G+O"
end
    end
})

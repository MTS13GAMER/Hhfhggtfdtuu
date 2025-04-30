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

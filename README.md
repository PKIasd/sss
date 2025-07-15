--[[
leoo hub - Script Lua para Roblox
- Botão amarelo movível
- ESP players (ficam vermelhos)
- Pulos infinitos
- Voar
- Velocidade 100
- Navegação entre páginas (Noclip e AutoClick)
]]

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()

-- GUI Setup
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "LeooHubGui"
ScreenGui.Parent = game.CoreGui

-- Drag Function
local function makeDraggable(frame)
    local dragging, offset
    frame.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = true
            offset = Vector2.new(input.Position.X, input.Position.Y) - frame.Position.XY
        end
    end)
    frame.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = false
        end
    end)
    game:GetService("UserInputService").InputChanged:Connect(function(input)
        if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
            local mousePos = input.Position
            frame.Position = UDim2.new(0, mousePos.X - offset.X, 0, mousePos.Y - offset.Y)
        end
    end)
end

-- Main Hub Button
local MainBtn = Instance.new("TextButton")
MainBtn.Parent = ScreenGui
MainBtn.Size = UDim2.new(0, 120, 0, 40)
MainBtn.Position = UDim2.new(0.5, -60, 0.1, 0)
MainBtn.BackgroundColor3 = Color3.fromRGB(255, 255, 0)
MainBtn.Text = "leoo hub"
MainBtn.TextColor3 = Color3.fromRGB(0,0,0)
MainBtn.Font = Enum.Font.GothamBold
MainBtn.TextSize = 20
makeDraggable(MainBtn)

-- Hub Frame
local HubFrame = Instance.new("Frame")
HubFrame.Parent = ScreenGui
HubFrame.Size = UDim2.new(0, 300, 0, 330)
HubFrame.Position = UDim2.new(0.5, -150, 0.2, 0)
HubFrame.BackgroundColor3 = Color3.fromRGB(255, 255, 204)
HubFrame.Visible = false
makeDraggable(HubFrame)

local HubLabel = Instance.new("TextLabel", HubFrame)
HubLabel.Text = "leoo hub"
HubLabel.Size = UDim2.new(1, 0, 0, 30)
HubLabel.BackgroundTransparency = 1
HubLabel.TextColor3 = Color3.fromRGB(255, 170, 0)
HubLabel.Font = Enum.Font.GothamBold
HubLabel.TextSize = 26

-- PAGE 1 BUTTONS

-- ESP Button
local ESPBtn = Instance.new("TextButton", HubFrame)
ESPBtn.Position = UDim2.new(0, 20, 0, 45)
ESPBtn.Size = UDim2.new(0, 120, 0, 30)
ESPBtn.Text = "ESP Players"
ESPBtn.BackgroundColor3 = Color3.fromRGB(255, 70, 70)
ESPBtn.TextColor3 = Color3.new(1,1,1)
ESPBtn.Font = Enum.Font.GothamBold

-- Infinite Jump Button
local JumpBtn = Instance.new("TextButton", HubFrame)
JumpBtn.Position = UDim2.new(0, 160, 0, 45)
JumpBtn.Size = UDim2.new(0, 120, 0, 30)
JumpBtn.Text = "Pulos Infinitos"
JumpBtn.BackgroundColor3 = Color3.fromRGB(255, 215, 70)
JumpBtn.TextColor3 = Color3.new(0,0,0)
JumpBtn.Font = Enum.Font.GothamBold

-- Voo Button
local FlyBtn = Instance.new("TextButton", HubFrame)
FlyBtn.Position = UDim2.new(0, 20, 0, 85)
FlyBtn.Size = UDim2.new(0, 120, 0, 30)
FlyBtn.Text = "Voar"
FlyBtn.BackgroundColor3 = Color3.fromRGB(70, 200, 255)
FlyBtn.TextColor3 = Color3.new(1,1,1)
FlyBtn.Font = Enum.Font.GothamBold

-- Velocidade Button
local SpeedBtn = Instance.new("TextButton", HubFrame)
SpeedBtn.Position = UDim2.new(0, 160, 0, 85)
SpeedBtn.Size = UDim2.new(0, 120, 0, 30)
SpeedBtn.Text = "Velocidade 100"
SpeedBtn.BackgroundColor3 = Color3.fromRGB(70, 255, 70)
SpeedBtn.TextColor3 = Color3.new(0,0,0)
SpeedBtn.Font = Enum.Font.GothamBold

-- Página 2 Button
local Page2Btn = Instance.new("TextButton", HubFrame)
Page2Btn.Position = UDim2.new(0, 20, 0, 125)
Page2Btn.Size = UDim2.new(0, 260, 0, 30)
Page2Btn.Text = "Ir para Página 2"
Page2Btn.BackgroundColor3 = Color3.fromRGB(200, 200, 255)
Page2Btn.TextColor3 = Color3.new(0,0,0)
Page2Btn.Font = Enum.Font.GothamBold

-- PAGE 2 FRAME
local Page2Frame = Instance.new("Frame")
Page2Frame.Parent = ScreenGui
Page2Frame.Size = HubFrame.Size
Page2Frame.Position = HubFrame.Position
Page2Frame.BackgroundColor3 = HubFrame.BackgroundColor3
Page2Frame.Visible = false
makeDraggable(Page2Frame)

local Page2Label = Instance.new("TextLabel", Page2Frame)
Page2Label.Text = "leoo hub - Página 2"
Page2Label.Size = UDim2.new(1, 0, 0, 30)
Page2Label.BackgroundTransparency = 1
Page2Label.TextColor3 = Color3.fromRGB(120, 120, 255)
Page2Label.Font = Enum.Font.GothamBold
Page2Label.TextSize = 23

-- Noclip Button
local NoclipBtn = Instance.new("TextButton", Page2Frame)
NoclipBtn.Position = UDim2.new(0, 20, 0, 45)
NoclipBtn.Size = UDim2.new(0, 120, 0, 30)
NoclipBtn.Text = "Noclip"
NoclipBtn.BackgroundColor3 = Color3.fromRGB(140, 140, 255)
NoclipBtn.TextColor3 = Color3.new(0,0,0)
NoclipBtn.Font = Enum.Font.GothamBold

-- AutoClick Button
local AutoClickBtn = Instance.new("TextButton", Page2Frame)
AutoClickBtn.Position = UDim2.new(0, 160, 0, 45)
AutoClickBtn.Size = UDim2.new(0, 120, 0, 30)
AutoClickBtn.Text = "AutoClick"
AutoClickBtn.BackgroundColor3 = Color3.fromRGB(255, 215, 120)
AutoClickBtn.TextColor3 = Color3.new(0,0,0)
AutoClickBtn.Font = Enum.Font.GothamBold

-- Voltar Button
local VoltarBtn = Instance.new("TextButton", Page2Frame)
VoltarBtn.Position = UDim2.new(0, 20, 0, 85)
VoltarBtn.Size = UDim2.new(0, 260, 0, 30)
VoltarBtn.Text = "Voltar Página 1"
VoltarBtn.BackgroundColor3 = Color3.fromRGB(255, 200, 200)
VoltarBtn.TextColor3 = Color3.new(0,0,0)
VoltarBtn.Font = Enum.Font.GothamBold

-- Hub Toggle
MainBtn.MouseButton1Click:Connect(function()
    HubFrame.Visible = not HubFrame.Visible
    Page2Frame.Visible = false
end)

Page2Btn.MouseButton1Click:Connect(function()
    HubFrame.Visible = false
    Page2Frame.Visible = true
end)

VoltarBtn.MouseButton1Click:Connect(function()
    Page2Frame.Visible = false
    HubFrame.Visible = true
end)

-- ESP FUNCTIONALITY
local ESPEnabled = false
ESPBtn.MouseButton1Click:Connect(function()
    ESPEnabled = not ESPEnabled
    ESPBtn.Text = ESPEnabled and "ESP ON" or "ESP Players"
    for _,v in pairs(workspace:GetChildren()) do
        if v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("Head") then
            if ESPEnabled then
                if not v.Head:FindFirstChild("LeooESP") then
                    local box = Instance.new("BoxHandleAdornment")
                    box.Name = "LeooESP"
                    box.Adornee = v.Head
                    box.Size = v.Head.Size
                    box.Color3 = Color3.fromRGB(255,0,0)
                    box.Transparency = 0.5
                    box.AlwaysOnTop = true
                    box.Parent = v.Head
                end
            else
                if v.Head:FindFirstChild("LeooESP") then
                    v.Head.LeooESP:Destroy()
                end
            end
        end
    end
end)
Players.PlayerAdded:Connect(function(p)
    p.CharacterAdded:Connect(function(char)
        if ESPEnabled and char:FindFirstChild("Head") then
            local box = Instance.new("BoxHandleAdornment")
            box.Name = "LeooESP"
            box.Adornee = char.Head
            box.Size = char.Head.Size
            box.Color3 = Color3.fromRGB(255,0,0)
            box.Transparency = 0.5
            box.AlwaysOnTop = true
            box.Parent = char.Head
        end
    end)
end)

-- INFINITE JUMP FUNCTIONALITY
local InfiniteJump = false
JumpBtn.MouseButton1Click:Connect(function()
    InfiniteJump = not InfiniteJump
    JumpBtn.Text = InfiniteJump and "Pulos ON" or "Pulos Infinitos"
end)
game:GetService("UserInputService").JumpRequest:Connect(function()
    if InfiniteJump then
        LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
    end
end)

-- FLY FUNCTIONALITY
local Flying = false
local FlySpeed = 50
local BodyGyro, BodyVelocity
local function enableFly()
    local char = LocalPlayer.Character
    local humanoidRoot = char:FindFirstChild("HumanoidRootPart")
    if humanoidRoot then
        BodyGyro = Instance.new("BodyGyro", humanoidRoot)
        BodyGyro.P = 9e4
        BodyGyro.MaxTorque = Vector3.new(9e9, 9e9, 9e9)
        BodyGyro.CFrame = humanoidRoot.CFrame
        BodyVelocity = Instance.new("BodyVelocity", humanoidRoot)
        BodyVelocity.Velocity = Vector3.new(0,0,0)
        BodyVelocity.MaxForce = Vector3.new(9e9, 9e9, 9e9)
        Flying = true
    end
end
local function disableFly()
    Flying = false
    if BodyGyro then BodyGyro:Destroy() end
    if BodyVelocity then BodyVelocity:Destroy() end
end
FlyBtn.MouseButton1Click:Connect(function()
    if not Flying then
        enableFly()
    else
        disableFly()
    end
    FlyBtn.Text = Flying and "Voar ON" or "Voar"
end)
game:GetService("RunService").Stepped:Connect(function()
    if Flying and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        local hrp = LocalPlayer.Character.HumanoidRootPart
        local cam = workspace.CurrentCamera
        local moveDirection = Vector3.new(0,0,0)
        if game:GetService("UserInputService"):IsKeyDown(Enum.KeyCode.W) then moveDirection = moveDirection + (cam.CFrame.LookVector * FlySpeed) end
        if game:GetService("UserInputService"):IsKeyDown(Enum.KeyCode.S) then moveDirection = moveDirection - (cam.CFrame.LookVector * FlySpeed) end
        if game:GetService("UserInputService"):IsKeyDown(Enum.KeyCode.A) then moveDirection = moveDirection - (cam.CFrame.RightVector * FlySpeed) end
        if game:GetService("UserInputService"):IsKeyDown(Enum.KeyCode.D) then moveDirection = moveDirection + (cam.CFrame.RightVector * FlySpeed) end
        BodyVelocity.Velocity = moveDirection
        BodyGyro.CFrame = cam.CFrame
    end
end)

-- SPEED FUNCTIONALITY
local SpeedOn = false
SpeedBtn.MouseButton1Click:Connect(function()
    SpeedOn = not SpeedOn
    SpeedBtn.Text = SpeedOn and "Velocidade ON" or "Velocidade 100"
    local hum = LocalPlayer.Character and LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
    if hum then
        hum.WalkSpeed = SpeedOn and 100 or 16
    end
end)
LocalPlayer.CharacterAdded:Connect(function(char)
    char:WaitForChild("Humanoid")
    if SpeedOn then char.Humanoid.WalkSpeed = 100 end
end)

-- NOCLIP FUNCTIONALITY
local NoclipOn = false
NoclipBtn.MouseButton1Click:Connect(function()
    NoclipOn = not NoclipOn
    NoclipBtn.Text = NoclipOn and "Noclip ON" or "Noclip"
end)
game:GetService("RunService").Stepped:Connect(function()
    if NoclipOn and LocalPlayer.Character then
        for _,v in pairs(LocalPlayer.Character:GetChildren()) do
            if v:IsA("BasePart") then
                v.CanCollide = false
            end
        end
    end
end)

-- AUTOCLICK FUNCTIONALITY
local AutoClickOn = false
AutoClickBtn.MouseButton1Click:Connect(function()
    AutoClickOn = not AutoClickOn
    AutoClickBtn.Text = AutoClickOn and "AutoClick ON" or "AutoClick"
end)
spawn(function()
    while true do
        wait(0.15)
        if AutoClickOn then
            mouse1press()
            wait(0.05)
            mouse1release()
        end
    end
end)

-- FIM

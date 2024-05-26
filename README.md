--[[BloxFruit]]--
local player = game:GetService("Players").LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = playerGui
local backgroundFrame = Instance.new("Frame")
backgroundFrame.Size = UDim2.new(1, 0, 1, 0) -- ขนาดเต็มหน้าจอ
backgroundFrame.Position = UDim2.new(0, 0, 0, 0) -- ตำแหน่งด้านบนซ้ายของหน้าจอ
backgroundFrame.BackgroundColor3 = Color3.new(0, 0, 0) -- สีดำ
backgroundFrame.BackgroundTransparency = 0.99 -- ความโปร่งใส
backgroundFrame.Parent = screenGui
local textLabel = Instance.new("TextLabel")
textLabel.Size = UDim2.new(0, 200, 0, 50)
textLabel.Position = UDim2.new(0.5, -100, -1, 0) -- จะให้เริ่มต้นด้านบนของหน้าจอ
textLabel.BackgroundTransparency = 1 -- ทำให้ข้อความโปร่งใส
textLabel.TextColor3 = Color3.new(1, 1, 1) -- สีข้อความ (สีขาว)
textLabel.Text = "Cave Hub is Load"
textLabel.Parent = screenGui
textLabel.BorderSizePixel = 0 -- กำหนดให้ไม่มีขอบ
textLabel.TextScaled = true -- ปรับขนาดข้อความอัตโนมัติ
textLabel.TextWrapped = true -- ให้ข้อความขึ้นบรรทัดใหม่ตามขนาดของ TextLabel
textLabel.TextXAlignment = Enum.TextXAlignment.Center -- จัดข้อความให้อยู่ตรงกลาง
textLabel.TextYAlignment = Enum.TextYAlignment.Center -- จัดข้อความให้อยู่ตรงกลาง
textLabel.Font = Enum.Font.SourceSansBold -- ฟอนต์

local curveIntensity = 10 -- ความโค้ง (1-10)
textLabel.TextScaled = true
textLabel.TextWrapped = true
textLabel.TextStrokeTransparency = 0
textLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
textLabel.TextScaled = true
textLabel.TextSize = 20
textLabel.TextTransparency = 0
local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Quint, Enum.EasingDirection.Out)
wait(1)
-- เลื่อน TextLabel มาที่กลางของหน้าจอ
textLabel:TweenPosition(UDim2.new(0.5, -100, 0.5, -25), "Out", "Quint", 1, true)

local placeId = game.PlaceId
if placeId == 2753915549 or placeId == 4442272183 or placeId == 7449423635 then
    BloxFruit = true
end
local placeId = game.PlaceId
if placeId == 2753915549 then
	OldWorld = true
elseif placeId == 4442272183 then
		NewWorld = true
elseif placeId == 7449423635 then
	ThreeWorld = true
end
local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
     Title = "Cave Hub",
     SubTitle = "by dawid",
     TabWidth = 180,
     Size = UDim2.fromOffset(500, 320),
     Acrylic = false,                        -- The blur may be detectable, setting this to false disables blur entirely
     Theme = "Dark",
     MinimizeKey = Enum.KeyCode.RightControl -- Used when theres no MinimizeKeybind
})

--Fluent provides Lucide Icons https://lucide.dev/icons/ for the tabs, icons are optional
local Tabs = {
     Information = Window:AddTab({ Title = "Information", Icon = "rbxassetid://11422155687" }),
     Main = Window:AddTab({ Title = "General", Icon = "home" }),
     Stats = Window:AddTab({ Title = "Stats", Icon = "rbxassetid://11422155046" }),
     Automatic = Window:AddTab({ Title = "Automatic", Icon = "swords" }),
     Shop = Window:AddTab({ Title = "Shop(Sea1)", Icon = "rbxassetid://11419715399" }),
     Shop2 = Window:AddTab({ Title = "Shop(Sea2)", Icon = "rbxassetid://12974422850" }),
     Shop3 = Window:AddTab({ Title = "Shop(Sea3)", Icon = "rbxassetid://12974428978" }),
     DevilFruit = Window:AddTab({ Title = "DevilFruit", Icon = "rbxassetid://12966428028" }),
     Raid = Window:AddTab({ Title = "Raid", Icon = "rbxassetid://11422924864" }),
     Teleport = Window:AddTab({ Title = "Teleport", Icon = "rbxassetid://12967404433" }),
     Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

local Options = Fluent.Options

do
     Fluent:Notify({
          Title = "Notification",
          Content = "YOYO",
          Duration = 5               -- Set to nil to make the notification not disappear
     })
end
local section = Tabs.Information:AddSection("Welcome")
Tabs.Information:AddParagraph({
     Title = "This Cave Hub",
     Content = "Blox Fruit Script"
})
local section = Tabs.Information:AddSection("Social")
Tabs.Information:AddButton({
     Title = "Join Discord",
     Description = "Pass in your discord and getin :D",
     Callback = function()
          setclipboard(tostring("https://discord.gg/p6b6HwuRq5"))
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "SetClipboard",
                    Duration = 3
               })
          end
     end
})
Tabs.Information:AddButton({
     Title = "Youtube",
     Description = "Copy youtube links",
     Callback = function()
          setclipboard(tostring("https://www.youtube.com/channel/UCKOv7FQXWQSOkx8_R0A1BUA"))
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "SetClipboard",
                    Duration = 3
               })
          end
     end
})
local section = Tabs.Main:AddSection("AutoFarm")
local Toggle = Tabs.Main:AddToggle("MyToggle", { Title = "AutoFarm", Default = false })

Toggle:OnChanged(function(Value)
_G.AutoFarm = Value
_G.FastAttack = Value
_G.AUTOHAKI = Value
_G.AutoEquip = Value
end)

Options.MyToggle:SetValue(false)

if OldWorld then
local section = Tabs.Automatic:AddSection("EastBlue")
local Toggle = Tabs.Automatic:AddToggle("MyToggle", {Title = "AutoDressrosa", Default = false })
Toggle:OnChanged(function(Value)
_G.newworld = Value
_G.FastAttack = Value
_G.AUTOHAKI = Value
_G.AutoEquip = Value
end)
Options.MyToggle:SetValue(false)

local section = Tabs.Automatic:AddSection("Sword")
local Toggle = Tabs.Automatic:AddToggle("MyToggle", {Title = "AutoPole", Default = false })

Toggle:OnChanged(function(Value)
_G.AutoPole = Value
_G.FastAttack = Value
_G.AUTOHAKI = Value
_G.AutoEquip = Value
end)
Options.MyToggle:SetValue(false)
local Toggle = Tabs.Automatic:AddToggle("MyToggle", {Title = "AutoSaber", Default = false })

Toggle:OnChanged(function(Value)
_G.AutoSaber = Value
_G.FastAttack = Value
_G.AUTOHAKI = Value
_G.AutoEquip = Value
end)
Options.MyToggle:SetValue(false)
local section = Tabs.Automatic:AddSection("Combat")
local Toggle = Tabs.Automatic:AddToggle("MyToggle", {Title = "AutoSuperHuman", Default = false })

Toggle:OnChanged(function(Value)
_G.AutoSuperHuman = Value
if Value then
     game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyBlackLeg")
end
end)
Options.MyToggle:SetValue(false)
elseif NewWorld then
local section = Tabs.Automatic:AddSection("Dressrosa")
local Toggle = Tabs.Automatic:AddToggle("MyToggle", {Title = "AutoQuestBartilo", Default = false })
Toggle:OnChanged(function(Value)
_G.AutoQuestBartilo = Value
end)
Options.MyToggle:SetValue(false)
local Toggle = Tabs.Automatic:AddToggle("MyToggle", {Title = "AutoFactory", Default = false })
Toggle:OnChanged(function(Value)
 _G.AutoFactory = Value
end)
Options.MyToggle:SetValue(false)
local section = Tabs.Automatic:AddSection("")
local Toggle = Tabs.Automatic:AddToggle("MyToggle", {Title = "AutoSuperHuman", Default = false })

Toggle:OnChanged(function(Value)
_G.AutoSuperHuman = Value
if Value then
     game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyBlackLeg")
end
end)
end
--------------------------------------------[[Click]]--------------------------------------------

function Click()
     local VirtualUser = game:GetService('VirtualUser')
	VirtualUser:CaptureController()
	VirtualUser:ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
end

--------------------------------------------[[EquipTool]]--------------------------------------------

function EquipItem(itemName)
     local player = game:GetService("Players").LocalPlayer
     local backpack = player.Backpack
     local character = player.Character
     if backpack:FindFirstChild(itemName) then
          local tool = backpack:FindFirstChild(itemName)
          tool.Parent = character
     end
end

--------------------------------------------[[Teleport]]--------------------------------------------

function TP(A)
     game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = A
end


--------------------------------------------[[Bypass]]--------------------------------------------

function Bypass(C)
     _G.WARP = true
     repeat wait(5)
          game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = C
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("SetSpawnPoint")
          game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = C
          game.Players.LocalPlayer.Character.Humanoid.Health = 0
     until game.Players.LocalPlayer.Character.Humanoid.Health > 1 or _G.AutoFarm == false or (Vector3.new(Qusetpos)-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 500
     _G.WARP = false
end
spawn(function()
     while task.wait() do
          if _G.WARP then
             game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = true
          else
              game.Players.LocalPlayer.Character.HumanoidRootPart.Anchored = false
          end
      end
end)
--------------------------------------------[[Tween]]--------------------------------------------

function Tween(CF)
     local Distance = (CF.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
     if Distance >= 250 then
          Speed = 270
     elseif Distance <= 170 then
          Speed = 300
     end
     local tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(Distance / Speed, Enum.EasingStyle.Linear), { CFrame = CF })
     tween:Play()
end

function FastTween(p)
     local Distance = (p.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
     local Speed = 370
     local tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(Distance / Speed, Enum.EasingStyle.Linear), { CFrame = p })
     tween:Play()
end
--TP(CFrame.new(0,0,0))

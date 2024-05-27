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

--------------------------------------------[[AutoFarm]]--------------------------------------------
function chacklevel()
     local lv = game:GetService("Players").LocalPlayer.Data.Level.Value
     if OldWorld then
          if lv == 1 or lv <= 9 then
                  Mon = "Bandit"
                LevelQuest = 1
                NameQuest = "BanditQuest1"
                NameMon = "Bandit"
                CFrameQuest = CFrame.new(1059.37195, 15.4495068, 1550.4231, 0.939700544, -0, -0.341998369, 0, 1, -0, 0.341998369, 0, 0.939700544)
                CFrameMon = CFrame.new(1045.962646484375, 27.00250816345215, 1560.8203125)
            elseif MyLevel == 10 or MyLevel <= 14 then
                Mon = "Monkey"
                LevelQuest = 1
                NameQuest = "JungleQuest"
                NameMon = "Monkey"
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                CFrameMon = CFrame.new(-1448.51806640625, 67.85301208496094, 11.46579647064209)
            elseif MyLevel == 15 or MyLevel <= 29 then
                Mon = "Gorilla"
                LevelQuest = 2
                NameQuest = "JungleQuest"
                NameMon = "Gorilla"
                CFrameQuest = CFrame.new(-1598.08911, 35.5501175, 153.377838, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                CFrameMon = CFrame.new(-1129.8836669921875, 40.46354675292969, -525.4237060546875)
            elseif MyLevel == 30 or MyLevel <= 39 then
                Mon = "Pirate"
                LevelQuest = 1
                NameQuest = "BuggyQuest1"
                NameMon = "Pirate"
                CFrameQuest = CFrame.new(-1141.07483, 4.10001802, 3831.5498, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                CFrameMon = CFrame.new(-1103.513427734375, 13.752052307128906, 3896.091064453125)
            elseif MyLevel == 40 or MyLevel <= 59 then
                Mon = "Brute"
                LevelQuest = 2
                NameQuest = "BuggyQuest1"
                NameMon = "Brute"
                CFrameQuest = CFrame.new(-1141.07483, 4.10001802, 3831.5498, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                CFrameMon = CFrame.new(-1140.083740234375, 14.809885025024414, 4322.92138671875)
            elseif MyLevel == 60 or MyLevel <= 74 then
                Mon = "Desert Bandit"
                LevelQuest = 1
                NameQuest = "DesertQuest"
                NameMon = "Desert Bandit"
                CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, -0, -0.573571265, 0, 1, -0, 0.573571265, 0, 0.819155693)
                CFrameMon = CFrame.new(924.7998046875, 6.44867467880249, 4481.5859375)
            elseif MyLevel == 75 or MyLevel <= 89 then
                Mon = "Desert Officer"
                LevelQuest = 2
                NameQuest = "DesertQuest"
                NameMon = "Desert Officer"
                CFrameQuest = CFrame.new(894.488647, 5.14000702, 4392.43359, 0.819155693, -0, -0.573571265, 0, 1, -0, 0.573571265, 0, 0.819155693)
                CFrameMon = CFrame.new(1608.2822265625, 8.614224433898926, 4371.00732421875)
            elseif MyLevel == 90 or MyLevel <= 99 then
                Mon = "Snow Bandit"
                LevelQuest = 1
                NameQuest = "SnowQuest"
                NameMon = "Snow Bandit"
                CFrameQuest = CFrame.new(1389.74451, 88.1519318, -1298.90796, -0.342042685, 0, 0.939684391, 0, 1, 0, -0.939684391, 0, -0.342042685)
                CFrameMon = CFrame.new(1354.347900390625, 87.27277374267578, -1393.946533203125)
            elseif MyLevel == 100 or MyLevel <= 119 then
                Mon = "Snowman"
                LevelQuest = 2
                NameQuest = "SnowQuest"
                NameMon = "Snowman"
                CFrameQuest = CFrame.new(1389.74451, 88.1519318, -1298.90796, -0.342042685, 0, 0.939684391, 0, 1, 0, -0.939684391, 0, -0.342042685)
                CFrameMon = CFrame.new(1201.6412353515625, 144.57958984375, -1550.0670166015625)
            elseif MyLevel == 120 or MyLevel <= 149 then
                Mon = "Chief Petty Officer"
                LevelQuest = 1
                NameQuest = "MarineQuest2"
                NameMon = "Chief Petty Officer"
                CFrameQuest = CFrame.new(-5039.58643, 27.3500385, 4324.68018, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                CFrameMon = CFrame.new(-4881.23095703125, 22.65204429626465, 4273.75244140625)
            elseif MyLevel == 150 or MyLevel <= 174 then
                Mon = "Sky Bandit"
                LevelQuest = 1
                NameQuest = "SkyQuest"
                NameMon = "Sky Bandit"
                CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                CFrameMon = CFrame.new(-4953.20703125, 295.74420166015625, -2899.22900390625)
            elseif MyLevel == 175 or MyLevel <= 189 then
                Mon = "Dark Master"
                LevelQuest = 2
                NameQuest = "SkyQuest"
                NameMon = "Dark Master"
                CFrameQuest = CFrame.new(-4839.53027, 716.368591, -2619.44165, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                CFrameMon = CFrame.new(-5259.8447265625, 391.3976745605469, -2229.035400390625)
            elseif MyLevel == 190 or MyLevel <= 209 then
                Mon = "Prisoner"
                LevelQuest = 1
                NameQuest = "PrisonerQuest"
                NameMon = "Prisoner"
                CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
                CFrameMon = CFrame.new(5098.9736328125, -0.3204058110713959, 474.2373352050781)
            elseif MyLevel == 210 or MyLevel <= 249 then
                Mon = "Dangerous Prisoner"
                LevelQuest = 2
                NameQuest = "PrisonerQuest"
                NameMon = "Dangerous Prisoner"
                CFrameQuest = CFrame.new(5308.93115, 1.65517521, 475.120514, -0.0894274712, -5.00292918e-09, -0.995993316, 1.60817859e-09, 1, -5.16744869e-09, 0.995993316, -2.06384709e-09, -0.0894274712)
                CFrameMon = CFrame.new(5654.5634765625, 15.633401870727539, 866.2991943359375)
            elseif MyLevel == 250 or MyLevel <= 274 then
                Mon = "Toga Warrior"
                LevelQuest = 1
                NameQuest = "ColosseumQuest"
                NameMon = "Toga Warrior"
                CFrameQuest = CFrame.new(-1580.04663, 6.35000277, -2986.47534, -0.515037298, 0, -0.857167721, 0, 1, 0, 0.857167721, 0, -0.515037298)
                CFrameMon = CFrame.new(-1820.21484375, 51.68385696411133, -2740.6650390625)
            elseif MyLevel == 275 or MyLevel <= 299 then
                Mon = "Gladiator"
                LevelQuest = 2
                NameQuest = "ColosseumQuest"
                NameMon = "Gladiator"
                CFrameQuest = CFrame.new(-1580.04663, 6.35000277, -2986.47534, -0.515037298, 0, -0.857167721, 0, 1, 0, 0.857167721, 0, -0.515037298)
                CFrameMon = CFrame.new(-1292.838134765625, 56.380882263183594, -3339.031494140625)
            elseif MyLevel == 300 or MyLevel <= 324 then
                Mon = "Military Soldier"
                LevelQuest = 1
                NameQuest = "MagmaQuest"
                NameMon = "Military Soldier"
                CFrameQuest = CFrame.new(-5313.37012, 10.9500084, 8515.29395, -0.499959469, 0, 0.866048813, 0, 1, 0, -0.866048813, 0, -0.499959469)
                CFrameMon = CFrame.new(-5411.16455078125, 11.081554412841797, 8454.29296875)
            elseif MyLevel == 325 or MyLevel <= 374 then
                Mon = "Military Spy"
                LevelQuest = 2
                NameQuest = "MagmaQuest"
                NameMon = "Military Spy"
                CFrameQuest = CFrame.new(-5313.37012, 10.9500084, 8515.29395, -0.499959469, 0, 0.866048813, 0, 1, 0, -0.866048813, 0, -0.499959469)
                CFrameMon = CFrame.new(-5802.8681640625, 86.26241302490234, 8828.859375)
            elseif MyLevel == 375 or MyLevel <= 399 then
                Mon = "Fishman Warrior"
                LevelQuest = 1
                NameQuest = "FishmanQuest"
                NameMon = "Fishman Warrior"
                CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
                CFrameMon = CFrame.new(60878.30078125, 18.482830047607422, 1543.7574462890625)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                end
            elseif MyLevel == 400 or MyLevel <= 449 then
                Mon = "Fishman Commando"
                LevelQuest = 2
                NameQuest = "FishmanQuest"
                NameMon = "Fishman Commando"
                CFrameQuest = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
                CFrameMon = CFrame.new(61922.6328125, 18.482830047607422, 1493.934326171875)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                end
            elseif MyLevel == 450 or MyLevel <= 474 then
                Mon = "God's Guard"
                LevelQuest = 1
                NameQuest = "SkyExp1Quest"
                NameMon = "God's Guard"
                CFrameQuest = CFrame.new(-4721.88867, 843.874695, -1949.96643, 0.996191859, -0, -0.0871884301, 0, 1, -0, 0.0871884301, 0, 0.996191859)
                CFrameMon = CFrame.new(-4710.04296875, 845.2769775390625, -1927.3079833984375)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
                end
            elseif MyLevel == 475 or MyLevel <= 524 then
                Mon = "Shanda"
                LevelQuest = 2
                NameQuest = "SkyExp1Quest"
                NameMon = "Shanda"
                CFrameQuest = CFrame.new(-7859.09814, 5544.19043, -381.476196, -0.422592998, 0, 0.906319618, 0, 1, 0, -0.906319618, 0, -0.422592998)
                CFrameMon = CFrame.new(-7678.48974609375, 5566.40380859375, -497.2156066894531)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
                end
            elseif MyLevel == 525 or MyLevel <= 549 then
                Mon = "Royal Squad"
                LevelQuest = 1
                NameQuest = "SkyExp2Quest"
                NameMon = "Royal Squad"
                CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                CFrameMon = CFrame.new(-7624.25244140625, 5658.13330078125, -1467.354248046875)
            elseif MyLevel == 550 or MyLevel <= 624 then
                Mon = "Royal Soldier"
                LevelQuest = 2
                NameQuest = "SkyExp2Quest"
                NameMon = "Royal Soldier"
                CFrameQuest = CFrame.new(-7906.81592, 5634.6626, -1411.99194, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                CFrameMon = CFrame.new(-7836.75341796875, 5645.6640625, -1790.6236572265625)
            elseif MyLevel == 625 or MyLevel <= 649 then
                Mon = "Galley Pirate"
                LevelQuest = 1
                NameQuest = "FountainQuest"
                NameMon = "Galley Pirate"
                CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
                CFrameMon = CFrame.new(5551.02197265625, 78.90135192871094, 3930.412841796875)
            elseif MyLevel >= 650 then
                Mon = "Galley Captain"
                LevelQuest = 2
                NameQuest = "FountainQuest"
                NameMon = "Galley Captain"
                CFrameQuest = CFrame.new(5259.81982, 37.3500175, 4050.0293, 0.087131381, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, 0.087131381)
                CFrameMon = CFrame.new(5441.95166015625, 42.50205993652344, 4950.09375)
            end
        elseif World2 then
            if MyLevel == 700 or MyLevel <= 724 then
                Mon = "Raider"
                LevelQuest = 1
                NameQuest = "Area1Quest"
                NameMon = "Raider"
                CFrameQuest = CFrame.new(-429.543518, 71.7699966, 1836.18188, -0.22495985, 0, -0.974368095, 0, 1, 0, 0.974368095, 0, -0.22495985)
                CFrameMon = CFrame.new(-728.3267211914062, 52.779319763183594, 2345.7705078125)
            elseif MyLevel == 725 or MyLevel <= 774 then
                Mon = "Mercenary"
                LevelQuest = 2
                NameQuest = "Area1Quest"
                NameMon = "Mercenary"
                CFrameQuest = CFrame.new(-429.543518, 71.7699966, 1836.18188, -0.22495985, 0, -0.974368095, 0, 1, 0, 0.974368095, 0, -0.22495985)
                CFrameMon = CFrame.new(-1004.3244018554688, 80.15886688232422, 1424.619384765625)
            elseif MyLevel == 775 or MyLevel <= 799 then
                Mon = "Swan Pirate"
                LevelQuest = 1
                NameQuest = "Area2Quest"
                NameMon = "Swan Pirate"
                CFrameQuest = CFrame.new(638.43811, 71.769989, 918.282898, 0.139203906, 0, 0.99026376, 0, 1, 0, -0.99026376, 0, 0.139203906)
                CFrameMon = CFrame.new(1068.664306640625, 137.61428833007812, 1322.1060791015625)
            elseif MyLevel == 800 or MyLevel <= 874 then
                Mon = "Factory Staff"
                NameQuest = "Area2Quest"
                LevelQuest = 2
                NameMon = "Factory Staff"
                CFrameQuest = CFrame.new(632.698608, 73.1055908, 918.666321, -0.0319722369, 8.96074881e-10, -0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, -1.07732087e-10, -0.0319722369)
                CFrameMon = CFrame.new(73.07867431640625, 81.86344146728516, -27.470672607421875)
            elseif MyLevel == 875 or MyLevel <= 899 then
                Mon = "Marine Lieutenant"
                LevelQuest = 1
                NameQuest = "MarineQuest3"
                NameMon = "Marine Lieutenant"
                CFrameQuest = CFrame.new(-2440.79639, 71.7140732, -3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                CFrameMon = CFrame.new(-2821.372314453125, 75.89727783203125, -3070.089111328125)
            elseif MyLevel == 900 or MyLevel <= 949 then
                Mon = "Marine Captain"
                LevelQuest = 2
                NameQuest = "MarineQuest3"
                NameMon = "Marine Captain"
                CFrameQuest = CFrame.new(-2440.79639, 71.7140732, -3216.06812, 0.866007268, 0, 0.500031412, 0, 1, 0, -0.500031412, 0, 0.866007268)
                CFrameMon = CFrame.new(-1861.2310791015625, 80.17658233642578, -3254.697509765625)
            elseif MyLevel == 950 or MyLevel <= 974 then
                Mon = "Zombie"
                LevelQuest = 1
                NameQuest = "ZombieQuest"
                NameMon = "Zombie"
                CFrameQuest = CFrame.new(-5497.06152, 47.5923004, -795.237061, -0.29242146, 0, -0.95628953, 0, 1, 0, 0.95628953, 0, -0.29242146)
                CFrameMon = CFrame.new(-5657.77685546875, 78.96973419189453, -928.68701171875)
            elseif MyLevel == 975 or MyLevel <= 999 then
                Mon = "Vampire"
                LevelQuest = 2
                NameQuest = "ZombieQuest"
                NameMon = "Vampire"
                CFrameQuest = CFrame.new(-5497.06152, 47.5923004, -795.237061, -0.29242146, 0, -0.95628953, 0, 1, 0, 0.95628953, 0, -0.29242146)
                CFrameMon = CFrame.new(-6037.66796875, 32.18463897705078, -1340.6597900390625)
            elseif MyLevel == 1000 or MyLevel <= 1049 then
                Mon = "Snow Trooper"
                LevelQuest = 1
                NameQuest = "SnowMountainQuest"
                NameMon = "Snow Trooper"
                CFrameQuest = CFrame.new(609.858826, 400.119904, -5372.25928, -0.374604106, 0, 0.92718488, 0, 1, 0, -0.92718488, 0, -0.374604106)
                CFrameMon = CFrame.new(549.1473388671875, 427.3870544433594, -5563.69873046875)
            elseif MyLevel == 1050 or MyLevel <= 1099 then
                Mon = "Winter Warrior"
                LevelQuest = 2
                NameQuest = "SnowMountainQuest"
                NameMon = "Winter Warrior"
                CFrameQuest = CFrame.new(609.858826, 400.119904, -5372.25928, -0.374604106, 0, 0.92718488, 0, 1, 0, -0.92718488, 0, -0.374604106)
                CFrameMon = CFrame.new(1142.7451171875, 475.6398010253906, -5199.41650390625)
            elseif MyLevel == 1100 or MyLevel <= 1124 then
                Mon = "Lab Subordinate"
                LevelQuest = 1
                NameQuest = "IceSideQuest"
                NameMon = "Lab Subordinate"
                CFrameQuest = CFrame.new(-6064.06885, 15.2422857, -4902.97852, 0.453972578, -0, -0.891015649, 0, 1, -0, 0.891015649, 0, 0.453972578)
                CFrameMon = CFrame.new(-5707.4716796875, 15.951709747314453, -4513.39208984375)
            elseif MyLevel == 1125 or MyLevel <= 1174 then
                Mon = "Horned Warrior"
                LevelQuest = 2
                NameQuest = "IceSideQuest"
                NameMon = "Horned Warrior"
                CFrameQuest = CFrame.new(-6064.06885, 15.2422857, -4902.97852, 0.453972578, -0, -0.891015649, 0, 1, -0, 0.891015649, 0, 0.453972578)
                CFrameMon = CFrame.new(-6341.36669921875, 15.951770782470703, -5723.162109375)
            elseif MyLevel == 1175 or MyLevel <= 1199 then
                Mon = "Magma Ninja"
                LevelQuest = 1
                NameQuest = "FireSideQuest"
                NameMon = "Magma Ninja"
                CFrameQuest = CFrame.new(-5428.03174, 15.0622921, -5299.43457, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
                CFrameMon = CFrame.new(-5449.6728515625, 76.65874481201172, -5808.20068359375)
            elseif MyLevel == 1200 or MyLevel <= 1249 then
                Mon = "Lava Pirate"
                LevelQuest = 2
                NameQuest = "FireSideQuest"
                NameMon = "Lava Pirate"
                CFrameQuest = CFrame.new(-5428.03174, 15.0622921, -5299.43457, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)
                CFrameMon = CFrame.new(-5213.33154296875, 49.73788070678711, -4701.451171875)
            elseif MyLevel == 1250 or MyLevel <= 1274 then
                Mon = "Ship Deckhand"
                LevelQuest = 1
                NameQuest = "ShipQuest1"
                NameMon = "Ship Deckhand"
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)         
                CFrameMon = CFrame.new(1212.0111083984375, 150.79205322265625, 33059.24609375)    
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1275 or MyLevel <= 1299 then
                Mon = "Ship Engineer"
                LevelQuest = 2
                NameQuest = "ShipQuest1"
                NameMon = "Ship Engineer"
                CFrameQuest = CFrame.new(1037.80127, 125.092171, 32911.6016)   
                CFrameMon = CFrame.new(919.4786376953125, 43.54401397705078, 32779.96875)   
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end             
            elseif MyLevel == 1300 or MyLevel <= 1324 then
                Mon = "Ship Steward"
                LevelQuest = 1
                NameQuest = "ShipQuest2"
                NameMon = "Ship Steward"
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)         
                CFrameMon = CFrame.new(919.4385375976562, 129.55599975585938, 33436.03515625)      
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1325 or MyLevel <= 1349 then
                Mon = "Ship Officer"
                LevelQuest = 2
                NameQuest = "ShipQuest2"
                NameMon = "Ship Officer"
                CFrameQuest = CFrame.new(968.80957, 125.092171, 33244.125)
                CFrameMon = CFrame.new(1036.0179443359375, 181.4390411376953, 33315.7265625)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                end
            elseif MyLevel == 1350 or MyLevel <= 1374 then
                Mon = "Arctic Warrior"
                LevelQuest = 1
                NameQuest = "FrostQuest"
                NameMon = "Arctic Warrior"
                CFrameQuest = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
                CFrameMon = CFrame.new(5966.24609375, 62.97002029418945, -6179.3828125)
                if _G.AutoFarm and (CFrameQuest.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 5000.034996032715, -132.83953857422))
                end
            elseif MyLevel == 1375 or MyLevel <= 1424 then
                Mon = "Snow Lurker"
                LevelQuest = 2
                NameQuest = "FrostQuest"
                NameMon = "Snow Lurker"
                CFrameQuest = CFrame.new(5667.6582, 26.7997818, -6486.08984, -0.933587909, 0, -0.358349502, 0, 1, 0, 0.358349502, 0, -0.933587909)
                CFrameMon = CFrame.new(5407.07373046875, 69.19437408447266, -6880.88037109375)
            elseif MyLevel == 1425 or MyLevel <= 1449 then
                Mon = "Sea Soldier"
                LevelQuest = 1
                NameQuest = "ForgottenQuest"
                NameMon = "Sea Soldier"
                CFrameQuest = CFrame.new(-3054.44458, 235.544281, -10142.8193, 0.990270376, -0, -0.13915664, 0, 1, -0, 0.13915664, 0, 0.990270376)
                CFrameMon = CFrame.new(-3028.2236328125, 64.67451477050781, -9775.4267578125)
            elseif MyLevel >= 1450 then
                Mon = "Water Fighter"
                LevelQuest = 2
                NameQuest = "ForgottenQuest"
                NameMon = "Water Fighter"
                CFrameQuest = CFrame.new(-3054.44458, 235.544281, -10142.8193, 0.990270376, -0, -0.13915664, 0, 1, -0, 0.13915664, 0, 0.990270376)
                CFrameMon = CFrame.new(-3352.9013671875, 285.01556396484375, -10534.841796875)
            end
        elseif World3 then
            if MyLevel == 1500 or MyLevel <= 1524 then
                Mon = "Pirate Millionaire"
                LevelQuest = 1
                NameQuest = "PiratePortQuest"
                NameMon = "Pirate Millionaire"
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                CFrameMon = CFrame.new(-245.9963836669922, 47.30615234375, 5584.1005859375)
            elseif MyLevel == 1525 or MyLevel <= 1574 then
                Mon = "Pistol Billionaire"
                LevelQuest = 2
                NameQuest = "PiratePortQuest"
                NameMon = "Pistol Billionaire"
                CFrameQuest = CFrame.new(-290.074677, 42.9034653, 5581.58984, 0.965929627, -0, -0.258804798, 0, 1, -0, 0.258804798, 0, 0.965929627)
                CFrameMon = CFrame.new(-187.3301544189453, 86.23987579345703, 6013.513671875)
            elseif MyLevel == 1575 or MyLevel <= 1599 then
                Mon = "Dragon Crew Warrior"
                LevelQuest = 1
                NameQuest = "AmazonQuest"
                NameMon = "Dragon Crew Warrior"
                CFrameQuest = CFrame.new(5832.83594, 51.6806107, -1101.51563, 0.898790359, -0, -0.438378751, 0, 1, -0, 0.438378751, 0, 0.898790359)
                CFrameMon = CFrame.new(6141.140625, 51.35136413574219, -1340.738525390625)
            elseif MyLevel == 1600 or MyLevel <= 1624 then 
                Mon = "Dragon Crew Archer"
                NameQuest = "AmazonQuest"
                LevelQuest = 2
                NameMon = "Dragon Crew Archer"
                CFrameQuest = CFrame.new(5833.1147460938, 51.60498046875, -1103.0693359375)
                CFrameMon = CFrame.new(6616.41748046875, 441.7670593261719, 446.0469970703125)
            elseif MyLevel == 1625 or MyLevel <= 1649 then
                Mon = "Female Islander"
                NameQuest = "AmazonQuest2"
                LevelQuest = 1
                NameMon = "Female Islander"
                CFrameQuest = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
                CFrameMon = CFrame.new(4685.25830078125, 735.8078002929688, 815.3425903320312)
            elseif MyLevel == 1650 or MyLevel <= 1699 then 
                Mon = "Giant Islander"
                NameQuest = "AmazonQuest2"
                LevelQuest = 2
                NameMon = "Giant Islander"
                CFrameQuest = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
                CFrameMon = CFrame.new(4729.09423828125, 590.436767578125, -36.97627639770508)
            elseif MyLevel == 1700 or MyLevel <= 1724 then
                Mon = "Marine Commodore"
                LevelQuest = 1
                NameQuest = "MarineTreeIsland"
                NameMon = "Marine Commodore"
                CFrameQuest = CFrame.new(2180.54126, 27.8156815, -6741.5498, -0.965929747, 0, 0.258804798, 0, 1, 0, -0.258804798, 0, -0.965929747)
                CFrameMon = CFrame.new(2286.0078125, 73.13391876220703, -7159.80908203125)
            elseif MyLevel == 1725 or MyLevel <= 1774 then
                Mon = "Marine Rear Admiral"
                NameMon = "Marine Rear Admiral"
                NameQuest = "MarineTreeIsland"
                LevelQuest = 2
                CFrameQuest = CFrame.new(2179.98828125, 28.731239318848, -6740.0551757813)
                CFrameMon = CFrame.new(3656.773681640625, 160.52406311035156, -7001.5986328125)
            elseif MyLevel == 1775 or MyLevel <= 1799 then
                Mon = "Fishman Raider"
                LevelQuest = 1
                NameQuest = "DeepForestIsland3"
                NameMon = "Fishman Raider"
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)   
                CFrameMon = CFrame.new(-10407.5263671875, 331.76263427734375, -8368.5166015625)
            elseif MyLevel == 1800 or MyLevel <= 1824 then
                Mon = "Fishman Captain"
                LevelQuest = 2
                NameQuest = "DeepForestIsland3"
                NameMon = "Fishman Captain"
                CFrameQuest = CFrame.new(-10581.6563, 330.872955, -8761.18652, -0.882952213, 0, 0.469463557, 0, 1, 0, -0.469463557, 0, -0.882952213)   
                CFrameMon = CFrame.new(-10994.701171875, 352.38140869140625, -9002.1103515625) 
            elseif MyLevel == 1825 or MyLevel <= 1849 then
                Mon = "Forest Pirate"
                LevelQuest = 1
                NameQuest = "DeepForestIsland"
                NameMon = "Forest Pirate"
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)
                CFrameMon = CFrame.new(-13274.478515625, 332.3781433105469, -7769.58056640625)
            elseif MyLevel == 1850 or MyLevel <= 1899 then
                Mon = "Mythological Pirate"
                LevelQuest = 2
                NameQuest = "DeepForestIsland"
                NameMon = "Mythological Pirate"
                CFrameQuest = CFrame.new(-13234.04, 331.488495, -7625.40137, 0.707134247, -0, -0.707079291, 0, 1, -0, 0.707079291, 0, 0.707134247)   
                CFrameMon = CFrame.new(-13680.607421875, 501.08154296875, -6991.189453125)
            elseif MyLevel == 1900 or MyLevel <= 1924 then
                Mon = "Jungle Pirate"
                LevelQuest = 1
                NameQuest = "DeepForestIsland2"
                NameMon = "Jungle Pirate"
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                CFrameMon = CFrame.new(-12256.16015625, 331.73828125, -10485.8369140625)
            elseif MyLevel == 1925 or MyLevel <= 1974 then
                Mon = "Musketeer Pirate"
                LevelQuest = 2
                NameQuest = "DeepForestIsland2"
                NameMon = "Musketeer Pirate"
                CFrameQuest = CFrame.new(-12680.3818, 389.971039, -9902.01953, -0.0871315002, 0, 0.996196866, 0, 1, 0, -0.996196866, 0, -0.0871315002)
                CFrameMon = CFrame.new(-13457.904296875, 391.545654296875, -9859.177734375)
            elseif MyLevel == 1975 or MyLevel <= 1999 then
                Mon = "Reborn Skeleton"
                LevelQuest = 1
                NameQuest = "HauntedQuest1"
                NameMon = "Reborn Skeleton"
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                CFrameMon = CFrame.new(-8763.7236328125, 165.72299194335938, 6159.86181640625)
            elseif MyLevel == 2000 or MyLevel <= 2024 then
                Mon = "Living Zombie"
                LevelQuest = 2
                NameQuest = "HauntedQuest1"
                NameMon = "Living Zombie"
                CFrameQuest = CFrame.new(-9479.2168, 141.215088, 5566.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0)
                CFrameMon = CFrame.new(-10144.1318359375, 138.62667846679688, 5838.0888671875)
            elseif MyLevel == 2025 or MyLevel <= 2049 then
                Mon = "Demonic Soul"
                LevelQuest = 1
                NameQuest = "HauntedQuest2"
                NameMon = "Demonic Soul"
                CFrameQuest = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0) 
                CFrameMon = CFrame.new(-9505.8720703125, 172.10482788085938, 6158.9931640625)
            elseif MyLevel == 2050 or MyLevel <= 2074 then
                Mon = "Posessed Mummy"
                LevelQuest = 2
                NameQuest = "HauntedQuest2"
                NameMon = "Posessed Mummy"
                CFrameQuest = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                CFrameMon = CFrame.new(-9582.0224609375, 6.251527309417725, 6205.478515625)
            elseif MyLevel == 2075 or MyLevel <= 2099 then
                Mon = "Peanut Scout"
                LevelQuest = 1
                NameQuest = "NutsIslandQuest"
                NameMon = "Peanut Scout"
                CFrameQuest = CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                CFrameMon = CFrame.new(-2143.241943359375, 47.72198486328125, -10029.9951171875)
            elseif MyLevel == 2100 or MyLevel <= 2124 then
                Mon = "Peanut President"
                LevelQuest = 2
                NameQuest = "NutsIslandQuest"
                NameMon = "Peanut President"
                CFrameQuest = CFrame.new(-2104.3908691406, 38.104167938232, -10194.21875, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                CFrameMon = CFrame.new(-1859.35400390625, 38.10316848754883, -10422.4296875)
            elseif MyLevel == 2125 or MyLevel <= 2149 then
                Mon = "Ice Cream Chef"
                LevelQuest = 1
                NameQuest = "IceCreamIslandQuest"
                NameMon = "Ice Cream Chef"
                CFrameQuest = CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                CFrameMon = CFrame.new(-872.24658203125, 65.81957244873047, -10919.95703125)
            elseif MyLevel == 2150 or MyLevel <= 2199 then
                Mon = "Ice Cream Commander"
                LevelQuest = 2
                NameQuest = "IceCreamIslandQuest"
                NameMon = "Ice Cream Commander"
                CFrameQuest = CFrame.new(-820.64825439453, 65.819526672363, -10965.795898438, 0, 0, -1, 0, 1, 0, 1, 0, 0)
                CFrameMon = CFrame.new(-558.06103515625, 112.04895782470703, -11290.7744140625)
            elseif MyLevel == 2200 or MyLevel <= 2224 then
                Mon = "Cookie Crafter"
                LevelQuest = 1
                NameQuest = "CakeQuest1"
                NameMon = "Cookie Crafter"
                CFrameQuest = CFrame.new(-2021.32007, 37.7982254, -12028.7295, 0.957576931, -8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, -0.288177818, -5.2032135e-08, 0.957576931)
                CFrameMon = CFrame.new(-2374.13671875, 37.79826354980469, -12125.30859375)
            elseif MyLevel == 2225 or MyLevel <= 2249 then
                Mon = "Cake Guard"
                LevelQuest = 2
                NameQuest = "CakeQuest1"
                NameMon = "Cake Guard"
                CFrameQuest = CFrame.new(-2021.32007, 37.7982254, -12028.7295, 0.957576931, -8.80302053e-08, 0.288177818, 6.9301187e-08, 1, 7.51931211e-08, -0.288177818, -5.2032135e-08, 0.957576931)
                CFrameMon = CFrame.new(-1598.3070068359375, 43.773197174072266, -12244.5810546875)
            elseif MyLevel == 2250 or MyLevel <= 2274 then
                Mon = "Baking Staff"
                LevelQuest = 1
                NameQuest = "CakeQuest2"
                NameMon = "Baking Staff"
                CFrameQuest = CFrame.new(-1927.91602, 37.7981339, -12842.5391, -0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, -0.250778586, 2.64211941e-08, -0.96804446)
                CFrameMon = CFrame.new(-1887.8099365234375, 77.6185073852539, -12998.3505859375)
            elseif MyLevel == 2275 or MyLevel <= 2299 then
                Mon = "Head Baker"
                LevelQuest = 2
                NameQuest = "CakeQuest2"
                NameMon = "Head Baker"
                CFrameQuest = CFrame.new(-1927.91602, 37.7981339, -12842.5391, -0.96804446, 4.22142143e-08, 0.250778586, 4.74911062e-08, 1, 1.49904711e-08, -0.250778586, 2.64211941e-08, -0.96804446)
                CFrameMon = CFrame.new(-2216.188232421875, 82.884521484375, -12869.2939453125)
            elseif MyLevel == 2300 or MyLevel <= 2324 then
                Mon = "Cocoa Warrior"
                LevelQuest = 1
                NameQuest = "ChocQuest1"
                NameMon = "Cocoa Warrior"
                CFrameQuest = CFrame.new(233.22836303710938, 29.876001358032227, -12201.2333984375)
                CFrameMon = CFrame.new(-21.55328369140625, 80.57499694824219, -12352.3876953125)
            elseif MyLevel == 2325 or MyLevel <= 2349 then
                Mon = "Chocolate Bar Battler"
                LevelQuest = 2
                NameQuest = "ChocQuest1"
                NameMon = "Chocolate Bar Battler"
                CFrameQuest = CFrame.new(233.22836303710938, 29.876001358032227, -12201.2333984375)
                CFrameMon = CFrame.new(582.590576171875, 77.18809509277344, -12463.162109375)
            elseif MyLevel == 2350 or MyLevel <= 2374 then
                Mon = "Sweet Thief"
                LevelQuest = 1
                NameQuest = "ChocQuest2"
                NameMon = "Sweet Thief"
                CFrameQuest = CFrame.new(150.5066375732422, 30.693693161010742, -12774.5029296875)
                CFrameMon = CFrame.new(165.1884765625, 76.05885314941406, -12600.8369140625)
            elseif MyLevel == 2375 or MyLevel <= 2399 then
                Mon = "Candy Rebel"
                LevelQuest = 2
                NameQuest = "ChocQuest2"
                NameMon = "Candy Rebel"
                CFrameQuest = CFrame.new(150.5066375732422, 30.693693161010742, -12774.5029296875)
                CFrameMon = CFrame.new(134.86563110351562, 77.2476806640625, -12876.5478515625)
            elseif MyLevel == 2400 or MyLevel <= 2449 then
                Mon = "Candy Pirate"
                LevelQuest = 1
                NameQuest = "CandyQuest1"
                NameMon = "Candy Pirate"
                CFrameQuest = CFrame.new(-1150.0400390625, 20.378934860229492, -14446.3349609375)
                CFrameMon = CFrame.new(-1310.5003662109375, 26.016523361206055, -14562.404296875)
            elseif MyLevel == 2450 or MyLevel <= 2474 then
                Mon = "Isle Outlaw"
                LevelQuest = 1
                NameQuest = "TikiQuest1"
                NameMon = "Isle Outlaw"
                CFrameQuest = CFrame.new(-16548.8164, 55.6059914, -172.8125, 0.213092566, -0, -0.977032006, 0, 1, -0, 0.977032006, 0, 0.213092566)
                CFrameMon = CFrame.new(-16479.900390625, 226.6117401123047, -300.3114318847656)
            elseif MyLevel == 2475 or MyLevel <= 2499 then
                Mon = "Island Boy"
                LevelQuest = 2
                NameQuest = "TikiQuest1"
                NameMon = "Island Boy"
                CFrameQuest = CFrame.new(-16548.8164, 55.6059914, -172.8125, 0.213092566, -0, -0.977032006, 0, 1, -0, 0.977032006, 0, 0.213092566)
                CFrameMon = CFrame.new(-16849.396484375, 192.86505126953125, -150.7853240966797)
            elseif MyLevel == 2500 or MyLevel <= 2524 then
                Mon = "Sun-kissed Warrior"
                LevelQuest = 1
                NameQuest = "TikiQuest2"
                NameMon = "kissed Warrior"
                CFrameMon = CFrame.new(-16347, 64, 984)
                CFrameQuest = CFrame.new(-16538, 55, 1049)
            elseif MyLevel >= 2525 then
                Mon = "Isle Champion"
                LevelQuest = 2
                NameQuest = "TikiQuest2"
                NameMon = "Isle Champion"
                CFrameQuest = CFrame.new(-16541.0215, 57.3082275, 1051.46118, 0.0410757065, -0, -0.999156058, 0, 1, -0, 0.999156058, 0, 0.0410757065) 
                CFrameMon = CFrame.new(-16602.1015625, 130.38734436035156, 1087.24560546875) 
            end
        end
    end

---4627.80518, 848.034973, -1706.73511, 0.890994847, 0, 0.454013437, 0, 1, 0, -0.454013437, 0, 0.890994847


spawn(function()
     while task.wait() do
          if _G.AutoFarm then
               pcall(function()
                    chacklevel()
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                         if (SETPOINT.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2500 then
                              Tween(Qusetpos)
                         elseif (SETPOINT.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 500 then
                              Tween(Qusetpos)
                         else
                              task.wait(.5)
                              Bypass(SETPOINT)
                         end
                         if (Qusetpos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 then
                              wait(.5)
                              game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("StartQuest", QuestName, QuestNumber)
                         end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                         if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, MonName) then
                              if workspace.Enemies:FindFirstChild(MonName) then
                                   for i, v in pairs(workspace.Enemies:GetChildren()) do
                                        if v.Name == MonName then
                                             repeat task.wait()
                                                  Tween(v.HumanoidRootPart.CFrame * CFrame.new(0, 60, 0))
                                                  v.Humanoid.WalkSpeed = 0
                                                  v.Humanoid.JumpPower = 0
                                                  v.HumanoidRootPart.CanCollide = false
                                                  v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
                                             until game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false or v.Humanoid.Health <= 0 or not _G.AutoFarm or not game.workspace.Enemies:FindFirstChild(MonName)
                                        end
                                   end
                              else
                                   wait(.5)
                                   FastTween(ChackMon1 * CFrame.new(math.random(-200, 200), 0, math.random(-200, 200)))
                              end
                         else
                              game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("AbandonQuest")
                         end
                    end
               end)
          end
     end
end)

coroutine.wrap(function()
     while task.wait() do
          if _G.AutoFarm then
               pcall(function()
                    chacklevel()
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                         if (Warp.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2500 then
                              FastTween(Warp)
                         elseif (Qusetpos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1500 then
                              FastTween(Qusetpos)
                         else
                              task.wait(5)
                              FastTween(Warp)
                         end
                         if (Qusetpos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1 then
                              wait(.5)
                              game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("StartQuest", QuestName, QuestNumber)
                         end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                         if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, MonName) then
                              if workspace.Enemies:FindFirstChild(MonName) then
                                   for i, v in pairs(workspace.Enemies:GetChildren()) do
                                        if v.Name == MonName then
                                             repeat task.wait()
                                                  Tween(v.HumanoidRootPart.CFrame * CFrame.new(0, 60, 0))
                                                  v.Humanoid.WalkSpeed = 0
                                                  v.Humanoid.JumpPower = 0
                                                  v.HumanoidRootPart.CanCollide = false
                                                  v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
                                             until game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false or v.Humanoid.Health <= 0 or not _G.AutoFarm or not game.workspace.Enemies:FindFirstChild(MonName)
                                        end
                                   end
                              else
                                   task.wait(.5)
                                   FastTween(ChackMon1 * CFrame.new(math.random(-160, 160), 0, math.random(-160, 160)))
                              end
                         else
                              game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("AbandonQuest")
                         end
                    end
               end)
          end
     end
end)()

spawn(function()
     while task.wait() do
          if _G.AutoFarm or _G.newworld then
               pcall(function()
                    chacklevel()
                    if game:GetService("Players").LocalPlayer.Data.Level.Value >= 700 then
                         game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
                    elseif game:GetService("Players").LocalPlayer.Data.Level.Value >= 1500 then
                         game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
                    end
               end)
          end
     end
end)
--------------------------------------------[[์Noclip]]--------------------------------------------

coroutine.wrap(function()
     while task.wait() do
          pcall(function()
               if _G.AutoFarm or _G.AutoSaber or _G.newworld or _G.island or _G.AutoPole then
                    if game.Players.LocalPlayer.Character.Humanoid.Health == 0 then
                         local BodyClip = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip")
                         if BodyClip then
                              BodyClip:Destroy()
                         end
                    else
                         if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
                              local Noclip = Instance.new("BodyVelocity")
                              Noclip.Name = "BodyClip"
                              Noclip.Parent = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
                              Noclip.MaxForce = Vector3.new(10000000,10000000,10000000)
                              Noclip.Velocity = Vector3.new(0,0,0)
                              Noclip.P = 100000
                         end
                    end
               else
                    local BodyClip = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip")
                    if BodyClip then
                         BodyClip:Destroy()
                    end
               end
          end)
     end
end)()

coroutine.wrap(function()
     while game:GetService("RunService").Stepped:wait() do
          pcall(function()
               if _G.AutoFarm or _G.AutoSaber or _G.newworld or _G.island or _G.AutoPole or _G.AutoFactory then
                    local character = game.Players.LocalPlayer.Character
                    for _, v in pairs(character:GetChildren()) do
                         if v:IsA("BasePart") then
                              v.CanCollide = false
                         end
                    end
               end
          end)
     end
end)()

--------------------------------------------[[BringMob]]--------------------------------------------

coroutine.wrap(function()
     while task.wait() do
          pcall(function()
               if _G.AutoFarm then
                    chacklevel()
                    pcall(function()
                         for _, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                              if v.Name == MonName then
                              local otherPlayersNearby = false
                              for _, player in pairs(game.Players:GetPlayers()) do
                                   if player ~= game.Players.LocalPlayer and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                                        local distance = (player.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude
                                        if distance < 680 then
                                             otherPlayersNearby = true
                                             break
                                        end
                                   end
                              end
                              if not otherPlayersNearby then
                                   local distanceToMon = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude
                                        if distanceToMon <= 550 then
                                             for _, y in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                                  if y.Name == MonName then
                                                       y.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                                                       v.HumanoidRootPart.CFrame = y.HumanoidRootPart.CFrame
                                                       y.HumanoidRootPart.Size = Vector3.new(math.huge, math.huge, math.huge)
                                                       v.HumanoidRootPart.Size = Vector3.new(math.huge, math.huge, math.huge)
                                                       y.HumanoidRootPart.CanCollide = false
                                                       v.HumanoidRootPart.CanCollide = false
                                                       y.Humanoid.WalkSpeed = 0
                                                       v.Humanoid.WalkSpeed = 0
                                                       y.Humanoid.JumpPower = 0
                                                       v.Humanoid.JumpPower = 0
                                                       y.Humanoid.AutoRotate = false
                                                       v.Humanoid.AutoRotate = false
                                                       local BP = Instance.new("BodyPosition")
                                                       BP.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                                                       BP.P = math.huge * math.huge
                                                       BP.D = math.huge * math.huge
                                                       y.HumanoidRootPart.Velocity = Vector3.new(0, 0, 0)
                                                       v.HumanoidRootPart.Velocity = Vector3.new(0, 0, 0)
                                                       local BG_v = Instance.new("BodyGyro")
                                                       BG_v.MaxTorque = Vector3.new(math.huge, math.huge, math.huge)
                                                       BG_v.P = math.huge * math.huge
                                                       BG_v.D = math.huge * math.huge
                                                       y.HumanoidRootPart.Velocity = Vector3.new(0, 0, 0)
                                                       v.HumanoidRootPart.Velocity = Vector3.new(0, 0, 0)
                                                       if sethiddenproperty then
                                                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                                                       end
                                                  end
                                             end
                                        elseif distanceToMon >= 550 then
                                             break
                                        end
                                   end
                              end
                         end
                    end)
               end
          end)
     end
end)()

coroutine.wrap(function()
     while task.wait() do
          pcall(function()
               if _G.AutoFarm then
                    chacklevel()
                    for i, v in pairs(workspace.Enemies:GetChildren()) do
                         if v.Name == MonName then
                              if v.Humanoid.Health == 0 then
                                   v:Destroy()
                              end
                         end
                    end
               end
          end)
     end
end)()

coroutine.wrap(function()
     while task.wait() do
          pcall(function()
               if _G.AutoPole then
                    for i,v in pairs(game.workspace.Enemies:GetChildren()) do
                         for i,y in pairs(game.workspace.Enemies:GetChildren()) do
                              if v.Name == NameBoss then
                                   if y.Name == NameBoss then
                                        v.Humanoid.WalkSpeed = 0
                                        y.Humanoid.WalkSpeed = 0
                                        v.Humanoid.AutoRotate = false
                                        y.Humanoid.AutoRotate = false
                                        local ICE = Instance.new("BodyPosition")
                                        ICE.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
                                        ICE.P = math.huge * math.huge
                                        ICE.D = math.huge * math.huge
                                        v.HumanoidRootPart.Velocity = Vector3.new(0, 0, 0)
                                        y.HumanoidRootPart.Velocity = Vector3.new(0, 0, 0)
                                   end
                              end
                         end
                    end
               end
          end)
     end
end)()
--------------------------------------------[[FastAttack]]--------------------------------------------

_G.FastAttackType = "Fast"

local CombatFramework = require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework"))
local CombatFrameworkR = getupvalues(CombatFramework)[2]
local cooldownfastattack = tick()

function CurrentWeapon()
    local ac = CombatFrameworkR.activeController
    local ret = ac.blades[1]
    if not ret then return game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name end
    pcall(function()
        while ret.Parent ~= game.Players.LocalPlayer.Character do ret = ret.Parent end
    end)
    if not ret then return game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name end
    return ret
end

function AttackFunction()
     local ac = CombatFrameworkR.activeController
     if ac and ac.equipped then
          local Hits = {}
          local Client = game.Players.LocalPlayer
          local Enemies = game:GetService("Workspace").Enemies:GetChildren()
          for i = 1, #Enemies do
               local v = Enemies[i]
               local Human = v:FindFirstChildOfClass("Humanoid")
               if Human and Human.RootPart and Human.Health > 0 and Client:DistanceFromCharacter(Human.RootPart.Position) < 70 then
                    table.insert(Hits, Human.RootPart)
               end
          end

          if #Hits > 0 then
               local AcAttack8 = debug.getupvalue(ac.attack, 5)
               local AcAttack9 = debug.getupvalue(ac.attack, 6)
               local AcAttack7 = debug.getupvalue(ac.attack, 4)
               local AcAttack10 = debug.getupvalue(ac.attack, 7)
               local NumberAc12 = (AcAttack8 * 798405 + AcAttack7 * 727595) % AcAttack9
               local NumberAc13 = AcAttack7 * 798405
               (function()
                    NumberAc12 = (NumberAc12 * AcAttack9 + NumberAc13) % 1099511627776
                    AcAttack8 = math.floor(NumberAc12 / AcAttack9)
                    AcAttack7 = NumberAc12 - AcAttack8 * AcAttack9
               end)()
               AcAttack10 = AcAttack10 + 1
               debug.setupvalue(ac.attack, 5, AcAttack8)
               debug.setupvalue(ac.attack, 6, AcAttack9)
               debug.setupvalue(ac.attack, 4, AcAttack7)
               debug.setupvalue(ac.attack, 7, AcAttack10)
               for k, v in pairs(ac.animator.anims.basic) do
                    v:Play(0.1, 0.5, 0.2, 0.8)
               end
               if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") and ac.blades and ac.blades[1] then
                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange", tostring(CurrentWeapon()))
                    game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(NumberAc12 / 1099511627776 * 16777215), AcAttack10)
                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", Hits, 2, "")
               end
          end
     end
end

coroutine.wrap(function()
     while true do
          if _G.FastAttack then
               pcall(function()
                    for i = 1, 1 do  -- เพิ่มจำนวนการโจมตีในลูปย่อย
                         AttackFunction()
                    end
                    if _G.FastAttackType == "Fast" then
                         if tick() - cooldownfastattack < task.wait() then
                              task.wait()
                              cooldownfastattack = tick()
                         end
                    elseif _G.FastAttackType == "Normal" then
                         if tick() - cooldownfastattack > 3 then
                              task.wait(0.5)
                              cooldownfastattack = tick()
                         end
                    elseif _G.FastAttackType == "Safety" then
                         if tick() - cooldownfastattack > 0.5 then
                              task.wait(0.3)
                              cooldownfastattack = tick()
                         end
                    end
               end)
          end
          task.wait()  -- ลดเวลา wait ให้การลูปหลักทำงานเร็วขึ้น
     end
end)()


coroutine.wrap(function()
     while task.wait() do
          if _G.AUTOHAKI then
               if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
               end
          end
     end
end)()
--------------------------------------------[[SelectWeapon]]--------------------------------------------
local EquipDistance = 75 -- ระยะห่างที่ต้องการตรวจสอบ

local Weapon = {
    "Melee",
    "Sword",
    "BloxFruit"
}

function UnequipWeapon()
     local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
     if humanoid then
          humanoid:UnequipTools()
     end
end

function CheckAndEquipWeapon(weaponType)
     for _, tool in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
          if tool:IsA("Tool") and tool.ToolTip == weaponType then
               local humanoid = game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
               if humanoid then
                    humanoid:EquipTool(tool)
                    return true
               end
          end
     end
     return false
end

coroutine.wrap(function()
     while task.wait(.2) do
          pcall(function()
               if _G.AutoEquip then
                    local player = game.Players.LocalPlayer
                    local playerPosition = player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.HumanoidRootPart.Position
                    local foundMon = false
                    for _, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                         if (v.Name == MonName or v.Name == MonQuestName or v.Name == QuestMonName or v.Name == NameMon or v.Name == NameBoss or v.Name == "Mob Leader" or v.Name == "Saber Expert") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                         local enemyPosition = v:FindFirstChild("HumanoidRootPart") and v.HumanoidRootPart.Position
                         if enemyPosition and playerPosition and (playerPosition - enemyPosition).Magnitude <= EquipDistance then
                              foundMon = true
                              break
                         end
                         end
                    end
                    if foundMon then
                         -- Equip the selected weapon
                         local weaponEquipped = false
                         if SelectWeapon == "Melee" then
                         weaponEquipped = CheckAndEquipWeapon("Melee")
                         elseif SelectWeapon == "Sword" then
                         weaponEquipped = CheckAndEquipWeapon("Sword")
                         elseif SelectWeapon == "Fruit" then
                         weaponEquipped = CheckAndEquipWeapon("Blox Fruit")
                         else
                         weaponEquipped = CheckAndEquipWeapon("Melee")
                         end
                    else
                         UnequipWeapon()
                    end
               end
          end)
     end
end)()

local Dropdown = Tabs.Main:AddDropdown("Dropdown", {
    Title = "SelectWeapon",
    Values = Weapon,
    Multi = false,
    Default = 1,
})

Dropdown:SetValue()

Dropdown:OnChanged(function(Value)
    SelectWeapon = Value
end)

--------------------------------------------[[Redeemcode]]--------------------------------------------

local section = Tabs.Main:AddSection("EXP x2 Code")
Tabs.Main:AddButton({
     Title = "RedeemAllCode",
     Callback = function()
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("TRIPLEABUSE")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("SEATROLLING")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("24NOADMIN")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("REWARDFUN")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("NEWTROLL")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("SECRET_ADMIN")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("KITT_RESET")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("CHANDLER")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Sub2CaptainMaui")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("kittgaming")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Sub2Fer999")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Enyu_is_Pro")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Magicbus")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("JCWK")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Starcodeheo")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Bluxxy")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("fudd10_v2")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("SUB2GAMERROBOT_EXP1")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("SUB2GAMERROBOT_RESET1")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Sub2UncleKizaru")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Axiore")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Sub2Daigrock")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Bignews")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Sub2NoobMaster123")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("StrawHatMaine")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("TantaiGaming")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Fudd10")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("TheGreatAce")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("Sub2OfficialNoobie")
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("Redeem"):InvokeServer("krazydares")
     end
})

--------------------------------------------[[AutoCombat]]--------------------------------------------

function superhuman()
     local Fragments = game:GetService("Players").LocalPlayer.Data.Fragments.Value
     local masterydarkleg = game:GetService("Players").LocalPlayer.Backpack["Black Leg"].Level.Value
          if masterydarkleg <= 300 then
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyBlackLeg")
          elseif masterydarkleg >= 300 then
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyElectro")
          end
     local masteryelectro = game:GetService("Players").LocalPlayer.Backpack.Electro.Level.Value
          if masteryelectro <= 300 then
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyElectro")
          elseif masteryelectro >= 300 then
               game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
          end
     local masteryDragonClaw = nil
     if Fragments >= 1500 then
          if masteryDragonClaw >= 300 then
               game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
          end
     end
end

coroutine.wrap(function()
     while task.wait() do
          if _G.AutoSuperHuman then
               pcall(function()
               superhuman()
               end)
          end
     end
end)()
--------------------------------------------[[AutoNewWorld]]--------------------------------------------

function newworld()
     Monpos = CFrame.new(4853.37549, 4.78490591, 717.703979, -0.453972578, 0, 0.891015649, 0, 1, 0, -0.891015649, 0, -0.453972578)
     Doorpos = CFrame.new(1347.6958, 37.3493462, -1325.87463, 0.519068599, -7.70531372e-08, 0.854732573, 6.44183729e-08, 1, 5.10283336e-08, -0.854732573, 2.85732771e-08, 0.519068599)
     QuestMonName = "Ice Admiral"
end

spawn(function()
     while task.wait() do
          if _G.newworld then
               newworld()
               if game.Players.LocalPlayer.Data.Level.Value >= 700 then
                    if (Monpos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10000 then
                         Tween(Monpos)
                    end
                    if (Monpos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10 then
                         wait(0.5)
                         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("DressrosaQuestProgress", "Detective")
                    end
                    if game.workspace.Map.Ice.Door.Transparency == 0 then
                         Tween(Monpos)
                    elseif game.workspace.Map.Ice.Door.Transparency == 1 then
                         Tween(Doorpos)
                    end
                    if (Doorpos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10000 then
                         Tween(Doorpos)
                    end
                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Key") then
                         repeat task.wait()
                              EquipItem("Key")
                         until (Vector3.new(1347.6958, 37.3493462, -1325.87463, 0.519068599, -7.70531372e-08, 0.854732573, 6.44183729e-08, 1, 5.10283336e-08, -0.854732573, 2.85732771e-08, 0.519068599)-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1
                    elseif not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Key") or game.workspace.Map.Ice.Door.Transparency == 0 then
                         Tween(Monpos)
                    end
                    if game.workspace.Map.Ice.Door.Transparency == 1 then
                         if workspace.Enemies:FindFirstChild(QuestMonName) then
                              for i, v in pairs(workspace.Enemies:GetChildren()) do
                                   if v.Name == QuestMonName then
                                   repeat
                                        task.wait()
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0, 50, 0))
                                        v.Humanoid.WalkSpeed = 0
                                        v.Humanoid.JumpPower = 0
                                        v.HumanoidRootPart.CanCollide = false
                                        v.HumanoidRootPart.Size = Vector3.new(1, 1, 1)
                                   until not game.workspace.Enemies:FindFirstChild(QuestMonName) or _G.newworld == false
                                   end
                              end
                         end
                    end
                    wait(3)
                    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("DressrosaQuestProgress", "Dressrosa")
               end
          end
     end
end)
--------------------------------------------[[AutoPole]]--------------------------------------------
function pole()
     Setpoint = CFrame.new(-7894.61768, 5547.1416, -380.291199, -0.0348471925, 3.04643821e-09, 0.999392629, 1.74792461e-07, 1, 3.04643821e-09, -0.999392629, 1.74792461e-07, -0.0348471925)
     CheckMon55 = CFrame.new(-7787, 5676, -2423)
     NameBoss = "Thunder God"
end

spawn(function()
     while task.wait() do
          if _G.AutoPole then
               pole()
               if game:GetService("Players").LocalPlayer.Data.Level.Value >= 50 then
                    if (CheckMon55.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3000 then
                         Tween(CheckMon55)
                    else
                         TP(Setpoint)
                    end
                    if workspace.Enemies:FindFirstChild(NameBoss) then
                         for i, v in pairs(workspace.Enemies:GetChildren()) do
                              if v.Name == NameBoss then
                                   repeat task.wait()
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0, 50, 0))
                                        v.Humanoid.WalkSpeed = 0
                                        v.Humanoid.JumpPower = 0
                                        v.HumanoidRootPart.CanCollide = false
                                        v.HumanoidRootPart.Size = Vector3.new(1, 1, 1)
                                   until not _G.AutoPole
                              end
                         end
                    else
                         wait(.5)
                         Tween(CheckMon55)
                    end
               end
          end
     end
end)
spawn(function()
     while task.wait() do
          pcall(function()
               if _G.AutoPole then
                    pole()
                    for i, v in pairs(workspace.Enemies:GetChildren()) do
                         if v.Name == NameBoss then
                              if v.Humanoid.Health == 0 then
                                   v:Destroy()
                              end
                         end
                    end
               end
          end)
     end
end)

--------------------------------------------[[Saber]]--------------------------------------------


spawn(function()
     while task.wait() do
          if _G.AutoSaber then
               if game:GetService("Players").LocalPlayer.Data.Level.Value >= 200 then
                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") ~= 0 then
                         game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                         repeat task.wait()
                              FastTween(CFrame.new(-1609.29956, 40.0520697, 162.820404))
                         until (Vector3.new(-1609.29956, 40.0520697, 162.820404)-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 10
                         wait(3)
                         for i,v in pairs(game:GetService("Workspace").Map.Jungle.QuestPlates:GetChildren()) do
                              if v.Name == "Plate1" then
                                   repeat wait()
                                   FastTween(v.Button.CFrame)
                                   until (v.Button.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 1
                                   wait(.1)
                              end
                              if v.Name == "Plate2" then
                                   repeat wait()
                                   FastTween(v.Button.CFrame)
                                   until (v.Button.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 1
                                   wait(.1)
                              end
                              if v.Name == "Plate3" then
                                   repeat wait()
                                   FastTween(v.Button.CFrame)
                                   until (v.Button.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 1
                                   wait(.1)
                              end
                              if v.Name == "Plate4" then
                                   repeat wait()
                                   FastTween(v.Button.CFrame)
                                   until (v.Button.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 1
                                   wait(.1)
                              end
                              if v.Name == "Plate5" then
                                   repeat wait()
                                   FastTween(v.Button.CFrame)
                                   until (v.Button.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 1
                                   wait(.1)
                              end
                         end
                         wait(2)
                         game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1609.29956, 12.0520697, 162.820404, -0.993804812, 2.60902091e-08, 0.11113929, 3.47902116e-08, 1, 7.63408607e-08, -0.11113929, 7.97344768e-08, -0.993804812)
                         wait(2)
                         repeat task.wait()
                              EquipItem("Torch")
                              FastTween(CFrame.new(1113.9502, 4.92147732, 4350.91992, -0.60768199, 3.86533046e-08, 0.794180453, 6.00742425e-08, 1, -2.70375722e-09, -0.794180453, 4.60667628e-08, -0.60768199))
                              EquipItem("Torch")
                         until (Vector3.new(1113.9502, 4.92147732, 4350.91992)-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1
                         EquipItem("Torch")
                         wait(1)
                         --fireclickdetector(game:GetService("Workspace").Map.Desert.Burn.Fire.ClickDetector)
                         task.wait(1)
                         game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1113.9502, 4.92147732, 4350.91992, -0.60768199, 3.86533046e-08, 0.794180453, 6.00742425e-08, 1, -2.70375722e-09, -0.794180453, 4.60667628e-08, -0.60768199)
                         EquipItem("Torch")
                         task.wait(1)
                         game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1113.9502, 4.92147732, 4350.91992, -0.60768199, 3.86533046e-08, 0.794180453, 6.00742425e-08, 1, -2.70375722e-09, -0.794180453, 4.60667628e-08, -0.60768199)
                         task.wait(3)
                         game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1114.87708, 4.9214654, 4349.8501, -0.612586915, -9.68697833e-08, 0.790403247, -1.2634203e-07, 1, 2.4638446e-08, -0.790403247, -8.47679615e-08, -0.612586915)
                         EquipItem("Torch")
                         wait(2)
                         game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1113.33618, 7.5484705, 4365.56396, -0.618000686, 2.54492516e-08, -0.786177576, -8.16741874e-09, 1, 3.87911392e-08, 0.786177576, 3.03939913e-08, -0.618000686)
                         wait(1)
                         repeat task.wait()
                              EquipItem("Cup")
                              FastTween(CFrame.new(1397.73975, 37.3480263, -1321.54456, -0.170597032, -4.99889588e-08, 0.985340893, 2.99880867e-08, 1, 5.59246409e-08, -0.985340893, 3.90890662e-08, -0.170597032))
                         until (Vector3.new(1397.73975, 37.3480263, -1321.54456)-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2
                         wait(1)
                         game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan")
                         wait(1)
                         game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon")
                         if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 0 then
                              warn("kuy")
                              if workspace.Enemies:FindFirstChild("Mob Leader") then
                                   for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                        if v.Name == "Mob Leader" then
                                             repeat task.wait()
                                                  Tween(v.HumanoidRootPart.CFrame * CFrame.new(0, 50, 0))
                                                  v.Humanoid.WalkSpeed = 0
                                                  v.Humanoid.JumpPower = 0
                                                  v.HumanoidRootPart.CanCollide = false
                                                  v.HumanoidRootPart.Size = Vector3.new(1, 1, 1)
                                             until _G.AutoSaber == false
                                        end
                                   end
                              elseif not workspace.Enemies:FindFirstChild("Mob Leader") then
                                   FastTween(CFrame.new(-2891, 7, 5316))
                              end
                         elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 1 then
                              if game.Players.LocalPlayer.Backpack:FindFirstChild("Relic") then
                                   EquipItem("Relic")
                                   repeat task.wait()
                                        EquipItem("Relic")
                                        FastTween(CFrame.new(-1406.60925, 29.8520069, 4.5805192, 0.882920146, 3.62382622e-08, 0.469523162, -3.61928865e-09, 1, -7.03750587e-08, -0.469523162, 6.04362143e-08, 0.882920146))
                                   until(Vector3.new(-1406.60925, 29.8520069, 4.5805192)-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2
                                   task.wait(1)
                              else
                                   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon")
                                   end
                         else
                              game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon")
                         end
                         wait(35)
                         if game.Workspace.Enemies:FindFirstChild("Saber Expert") then
                              for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                   if v.Name == "Saber Expert" then
                                        repeat task.wait()
                                             FastTween(v.HumanoidRootPart.CFrame * CFrame.new(0, 50, 0))
                                             v.Humanoid.WalkSpeed = 0
                                             v.Humanoid.JumpPower = 0
                                             v.HumanoidRootPart.CanCollide = false
                                             v.HumanoidRootPart.Size = Vector3.new(1, 1, 1)
                                        until not v.Parent or v.Humanoid.Health <= 0 or _G.AutoSaber == false
                                   end
                              end
                         else
                              FastTween(CFrame.new(-1458.89502, 29.8870335, -50.633564, 0.858821094, 1.13848939e-08, 0.512275636, -4.85649254e-09, 1, -1.40823326e-08, -0.512275636, 9.6063415e-09, 0.858821094))
                         end
                    end
               end
          end
     end
end)

spawn(function()
     while task.wait() do
          pcall(function()
               if _G.AutoSaber then
                    for i, v in pairs(workspace.Enemies:GetChildren()) do
                         if v.Name == NameBoss then
                              if v.Humanoid.Health == 0 then
                                   v:Destroy()
                              end
                         end
                    end
               end
          end)
     end
end)

-------------------------------------------[[AutoStats]]--------------------------------------------

local Toggle = Tabs.Stats:AddToggle("MyToggle", { Title = "Melee", Default = false })
Toggle:OnChanged(function(Value)
_G.Melee = Value
     for i = 1, 500 do
          while _G.Melee do
               task.wait()
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer(
               "AddPoint", "Melee", point)
          end
     end
end)
Options.MyToggle:SetValue(false)

local Toggle = Tabs.Stats:AddToggle("MyToggle", { Title = "Defense", Default = false })

Toggle:OnChanged(function(Value)
_G.Defense = Value
     for i = 1, 500 do
          while _G.Defense do
               task.wait()
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer(
               "AddPoint", "Defense", point)
          end
     end
end)
Options.MyToggle:SetValue(false)

local Toggle = Tabs.Stats:AddToggle("MyToggle", { Title = "Sword", Default = false })
Toggle:OnChanged(function(Value)
_G.Sword = Value
     while _G.Sword do
          task.wait()
          for i = 1, 500 do
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("AddPoint", "Sword", point)
          end
     end
end)
Options.MyToggle:SetValue(false)

local Toggle = Tabs.Stats:AddToggle("MyToggle", { Title = "Gun", Default = false })
Toggle:OnChanged(function(Value)
_G.Gun = Value
     while _G.Gun do
          task.wait()
          for i = 1, 500 do
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("AddPoint", "Gun", point)
          end
     end
end)
Options.MyToggle:SetValue(false)

local Toggle = Tabs.Stats:AddToggle("MyToggle", { Title = "BloxFruit", Default = false })
Toggle:OnChanged(function(Value)
_G.BloxFruit = Value
     while _G.BloxFruit do
          task.wait()
          for i = 1, 500 do
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("AddPoint", "Demon Fruit", point)
          end
     end
end)
Options.MyToggle:SetValue(false)

local Slider = Tabs.Stats:AddSlider("Slider", {
     Title = "Point",
     Default = 10,
     Min = 1,
     Max = 100,
     Rounding = 0,
     Callback = function(Value)
          point = Value
     end
})
Slider:SetValue(10)

--------------------------------------------[[Shop]]--------------------------------------------

--[[Haki]]--
     Tabs.Shop:AddParagraph({
          Title = "This is Shop Tab",
          Content = "Show the Store in sea1"
      })
local section = Tabs.Shop:AddSection("Haki")
Tabs.Shop:AddButton({
     Title = "BuyBuso",
     Description = "BuyBuso 25,000",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "BuyBuso",
                    Duration = 2
               })
          end
     game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyHaki","Buso")
     end
})
Tabs.Shop:AddButton({
     Title = "BuyGeppo",
     Description = "BuyGeppo 10,000",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "BuyGeppo",
                    Duration = 2
               })
          end
     game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyHaki","Geppo")
     end
})
Tabs.Shop:AddButton({
     Title = "BuySoru",
     Description = "BuySoru 100,000",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "BuySoru",
                    Duration = 2
               })
          end
     game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyHaki","Soru")
     end
})

--[[combat]]--

local section = Tabs.Shop:AddSection("Combat")
Tabs.Shop:AddButton({
     Title = "BuyBlackLeg",
     Description = "BuyBlackLeg 150,000 Beli",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "BuyBlackLeg",
                    Duration = 2
               })
          end
     game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyBlackLeg")
     end
})
Tabs.Shop:AddButton({
     Title = "BuyElectro",
     Description = "BuyElectro 500,000 Beli",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "BuyElectro",
                    Duration = 2
               })
          end
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("BuyElectro")
     end
})
Tabs.Shop:AddButton({
     Title = "BuyFishmanKarate",
     Description = "BuyFishmanKarate 750,000 Beli",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "BuyFishmanKarate",
                    Duration = 2
               })
          end
          game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
     end
})
Tabs.Shop:AddButton({
     Title = "BuyDragonTalon",
     Description = "BuyDragonTalon 1,500 Fragments",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "BuyDragonTalon",
                    Duration = 2
               })
          end
          game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
     end
})

--[[sword]]--

local section = Tabs.Shop:AddSection("Sword")
Tabs.Shop:AddButton({
     Title = "Katana",
     Description = "Katana 5,000 Beli",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "BuyKatana",
                    Duration = 2
               })
          end
     end
})

--------------------------------------------[[DevilFruit]]--------------------------------------------

local section = Tabs.DevilFruit:AddSection("")
Tabs.DevilFruit:AddButton({
     Title = "RandomFruit",
     Description = "GoodLuck :)",
     Callback = function()
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("Cousin","Buy")
     end
})

local Toggle = Tabs.DevilFruit:AddToggle("MyToggle", {Title = "AutoRandomFruit", Default = false })

Toggle:OnChanged(function(Value)
_G.Fruit = Value
end)

Options.MyToggle:SetValue(false)
local Toggle = Tabs.DevilFruit:AddToggle("MyToggle", {Title = "AutoStoreFruit", Default = false })

Toggle:OnChanged(function(Value)
_G.SFruit = Value
end)

Options.MyToggle:SetValue(false)


coroutine.wrap(function()
     while task.wait() do
          if _G.Fruit then
               game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("Cousin","Buy")
          end
     end
end)()

coroutine.wrap(function()
     if _G.SFruit then
          while _G.SFruit do task.wait()
          function getNil(name,class) 
               for _,v in next, getnilinstances() do 
                    if v.ClassName==class and v.Name==name then 
                         return v;
                    end 
               end 
          end
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("StoreFruit","Spin-Spin",getNil("Spin Fruit", "Tool"))
          game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("CommF_"):InvokeServer("StoreFruit","Rubber-Rubber",getNil("Rubber Fruit", "Tool"))
          end
     end
end)()

--------------------------------------------[[Misc]]--------------------------------------------

local section = Tabs.Teleport:AddSection("WorldTravel")
Tabs.Teleport:AddButton({
     Title = "EastBlue",
     Description = "Teleport You To EastBlue",
     Callback = function()
          Window:Dialog({
               Title = "Are You Sure?",
               Content = "Teleport You To EastBlue",
               Buttons = {
                    {
                         Title = "Yes!",
                         Callback = function()
                              game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelMain")
                         end
                    },
                    {
                         Title = "No!",
                         Callback = function()
                              do
                                   Fluent:Notify({
                                        Title = "Notification",
                                        Content = "Ok.",
                                        Duration = 2
                                   })
                              end
                         end
                    }
               }
          })
     end
})
Tabs.Teleport:AddButton({
     Title = "Dressrosa",
     Description = "Teleport You To Dressrosa",
     Callback = function()
          Window:Dialog({
               Title = "Are You Sure?",
               Content = "Teleport You To Dressrosa",
               Buttons = {
                    {
                         Title = "Yes!",
                         Callback = function()
                              game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
                         end
                    },
                    {
                         Title = "No!",
                         Callback = function()
                              do
                                   Fluent:Notify({
                                        Title = "Notification",
                                        Content = "Ok.",
                                        Duration = 2
                                   })
                              end
                         end
                    }
               }
          })
     end
})
Tabs.Teleport:AddButton({
     Title = "Zou",
     Description = "Teleport You To Zou",
     Callback = function()
          Window:Dialog({
               Title = "Are You Sure?",
               Content = "Teleport You To Zou",
               Buttons = {
                    {
                         Title = "Yes!",
                         Callback = function()
                              game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
                         end
                    },
                    {
                         Title = "No!",
                         Callback = function()
                              do
                                   Fluent:Notify({
                                        Title = "Notification",
                                        Content = "Ok.",
                                        Duration = 2
                                   })
                              end
                         end
                    }
               }
          })
     end
})

--------------------------------------------[[Misc(Teleport)]]--------------------------------------------


if OldWorld then

local islands = {"Pirate starter", "Marine starter", "Jungle", "Pirate Village", "Desert", "Frozen Village", "MarineFord", "Sky 1st Floor", "Prison", "Sky 2st Floor", "Sky 3st Floor"}

function getCFrameForIsland(islandName)
    local positions = {
        ["Pirate starter"] = CFrame.new(1071.2832, 16.3085976, 1426.86792),
        ["Marine starter"] = CFrame.new(-2573.3374, 6.88881969, 2046.99817),
        ["Jungle"] = CFrame.new(-1249.77222, 11.8870859, 341.356476),
        ["Pirate Village"] = CFrame.new(-1122.34998, 4.78708982, 3855.91992),
        ["Desert"] = CFrame.new(1094.14587, 6.47350502, 4192.88721),
        ["Frozen Village"] = CFrame.new(1198.00928, 27.0074959, -1211.73376),
        ["MarineFord"] = CFrame.new(-4505.375, 20.687294, 4260.55908),
        ["Sky 1st Floor"] = CFrame.new(-4970.21875, 717.707275, -2622.35449),
        ["Prison"] = CFrame.new(4854.16455, 5.68742752, 740.194641),
        ["Sky 2st Floor"] = CFrame.new(-4813.0249, 903.708557, -1912.69055),
        ["Sky 3st Floor"] = CFrame.new(-7952.31006, 5545.52832, -320.704956)
    }
    return positions[islandName]
end
function is(land)
     local targetCFrame = getCFrameForIsland(land)
     if targetCFrame then
          Tween(targetCFrame)
     else
          print("Unknown island: " .. land)
     end
end
local section = Tabs.Teleport:AddSection("Island Teleport")
     local Dropdown = Tabs.Teleport:AddDropdown("Dropdown", {
          Title = "Select Island",
          Values = islands,
          Multi = false,
          Default = 1,
     })

     Dropdown:SetValue()

     Dropdown:OnChanged(function(Value)
          land = Value
     end)

     local Toggle = Tabs.Teleport:AddToggle("MyToggle", {Title = "Teleport", Default = false})

     Toggle:OnChanged(function(Value)
          _G.island = Value
          if _G.island then
               is(Dropdown.Value)  -- เรียกใช้ฟังก์ชัน is พร้อมกับค่า Dropdown ที่เลือก
          end
     end)
     Options.MyToggle:SetValue(false)
elseif NewWorld then
     local islands = {""}

function getCFrameForIsland(islandName)
    local positions = {

    }
    return positions[islandName]
end
function is(land)
     local targetCFrame = getCFrameForIsland(land)
     if targetCFrame then
          Tween(targetCFrame)
     else
          print("Unknown island: " .. land)
     end
end
local section = Tabs.Teleport:AddSection("Island Teleport")
     local Dropdown = Tabs.Teleport:AddDropdown("Dropdown", {
          Title = "Select Island",
          Values = islands,
          Multi = false,
          Default = 1,
     })

     Dropdown:SetValue()

     Dropdown:OnChanged(function(Value)
          land = Value
     end)

     local Toggle = Tabs.Teleport:AddToggle("MyToggle", {Title = "Teleport", Default = false})

     Toggle:OnChanged(function(Value)
          _G.island = Value
          if _G.island then
               is(Dropdown.Value)  -- เรียกใช้ฟังก์ชัน is พร้อมกับค่า Dropdown ที่เลือก
          end
     end)
     Options.MyToggle:SetValue(false)
end
--------------------------------------------[[AutoFactory]]--------------------------------------------

function Factory()
     spawnpoint = CFrame.new(-379.871765, 72.0878448, 250.478149, -0.999848366, 0, -0.017436387, 0, 1, 0, 0.017436387, 0, -0.999848366)
     Pak = CFrame.new(282, 74, -282)
     NameMon = "Core"
end

spawn(function()
     while task.wait() do
          if _G.AutoFactory then
               pcall(function()
                    Factory()
                    if (spawnpoint.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 2500 then
                         Tween(spawnpoint)
                    else
                         Bypass(Pak)
                    end
                    if game.Workspace.Enemies:FindFirstChild("Core") then
                         for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                              if v.Name == "Core" and v.Humanoid.Health > 0 then
                                   repeat task.wait()
                                        Tween(v.HumanoidRootPart.CFrame * CFrame.new(0, 0, 0))
                                        v.Humanoid.WalkSpeed = 0
                                        v.Humanoid.JumpPower = 0
                                        v.HumanoidRootPart.CanCollide = false
                                        v.HumanoidRootPart.Size = Vector3.new(1, 1, 1)
                                   until not _G.Factory or game.workspace.Map.Dressrosa.SmileFactory.Door.Transparency == 0
                              end
                         end
                    end
                    if game.workspace.Map.Dressrosa.SmileFactory.Door.Transparency == 0 then
                         Tween(Pak)
                    end
               end)
          end
     end
end)

--------------------------------------------[[Setting]]--------------------------------------------
Tabs.Settings:AddButton({
     Title = "Rejoin",
     Description = "",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "Rejoin Server...",
                    Duration = 5               -- Set to nil to make the notification not disappear
               })
          end
          wait(1.5)
          local ts = game:GetService("TeleportService")
          local p = game:GetService("Players").LocalPlayer
          ts:Teleport(game.PlaceId, p)
     end
})
Tabs.Settings:AddButton({
     Title = "Hop to a low server",
     Description = "",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "Hop to a low server...",
                    Duration = 5               -- Set to nil to make the notification not disappear
               })
          end
          wait(1.5)
          local Http = game:GetService("HttpService")
          local TPS = game:GetService("TeleportService")
          local Api = "https://games.roblox.com/v1/games/"
          local _place = game.PlaceId
          local _servers = Api .. _place .. "/servers/Public?sortOrder=Asc&limit=100"
          function ListServers(cursor)
               local Raw = game:HttpGet(_servers .. ((cursor and "&cursor=" .. cursor) or ""))
               return Http:JSONDecode(Raw)
          end
          local Server, Next; repeat
               local Servers = ListServers(Next)
               Server = Servers.data[1]
               Next = Servers.nextPageCursor
          until Server
          TPS:TeleportToPlaceInstance(_place, Server.id, game.Players.LocalPlayer)
     end
})
Tabs.Settings:AddButton({
     Title = "FpsBoots",
     Description = "",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "FreeFireMode👽",
                    Duration = 3 -- Set to nil to make the notification not disappear
               })
          end
          local decalsyeeted = true -- Leaving this on makes games look shitty but the fps goes up by at least 20.
          local g = game
          local w = g.Workspace
          local l = g.Lighting
          local t = w.Terrain
          sethiddenproperty(l, "Technology", 2)
          sethiddenproperty(t, "Decoration", false)
          t.WaterWaveSize = 0
          t.WaterWaveSpeed = 0
          t.WaterReflectance = 0
          t.WaterTransparency = 0
          l.GlobalShadows = 0
          l.FogEnd = 9e9
          l.Brightness = 0
          settings().Rendering.QualityLevel = "Level01"
          for i, v in pairs(w:GetDescendants()) do
               if v:IsA("BasePart") and not v:IsA("MeshPart") then
                    v.Material = "Plastic"
                    v.Reflectance = 0
               elseif (v:IsA("Decal") or v:IsA("Texture")) and decalsyeeted then
                    v.Transparency = 1
               elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                    v.Lifetime = NumberRange.new(0)
               elseif v:IsA("Explosion") then
                    v.BlastPressure = 1
                    v.BlastRadius = 1
               elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
                    v.Enabled = false
               elseif v:IsA("MeshPart") and decalsyeeted then
                    v.Material = "Plastic"
                    v.Reflectance = 0
                    v.TextureID = 10385902758728957
               elseif v:IsA("SpecialMesh") and decalsyeeted then
                    v.TextureId = 0
               elseif v:IsA("ShirtGraphic") and decalsyeeted then
                    v.Graphic = 0
               elseif (v:IsA("Shirt") or v:IsA("Pants")) and decalsyeeted then
                    v[v.ClassName .. "Template"] = 0
               end
          end
          for i = 1, #l:GetChildren() do
               e = l:GetChildren()[i]
               if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
                    e.Enabled = false
               end
          end
          w.DescendantAdded:Connect(function(v)
               wait() --prevent errors and shit
               if v:IsA("BasePart") and not v:IsA("MeshPart") then
                    v.Material = "Plastic"
                    v.Reflectance = 0
               elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
                    v.Transparency = 1
               elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                    v.Lifetime = NumberRange.new(0)
               elseif v:IsA("Explosion") then
                    v.BlastPressure = 1
                    v.BlastRadius = 1
               elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
                    v.Enabled = false
               elseif v:IsA("MeshPart") and decalsyeeted then
                    v.Material = "Plastic"
                    v.Reflectance = 0
                    v.TextureID = 10385902758728957
               elseif v:IsA("SpecialMesh") and decalsyeeted then
                    v.TextureId = 0
               elseif v:IsA("ShirtGraphic") and decalsyeeted then
                    v.ShirtGraphic = 0
               elseif (v:IsA("Shirt") or v:IsA("Pants")) and decalsyeeted then
                    v[v.ClassName .. "Template"] = 0
               end
          end)
     end
})
Tabs.Settings:AddButton({
     Title = "Remove Lava Dmange",
     Description = "Remove All Lava Dmange",
     Callback = function()
          for i,v in pairs(game.Workspace:GetDescendants()) do
			if v.Name == "Lava" then
				v:Destroy()
			end
		end
		for i,v in pairs(game.ReplicatedStorage:GetDescendants()) do
			if v.Name == "Lava" then
				v:Destroy()
			end
		end
     end
})

Tabs.Settings:AddButton({
     Title = "Remove Fog",
     Description = "Remove All Fog",
     Callback = function()
          do
               Fluent:Notify({
                    Title = "Notification",
                    Content = "Remove Fog!",
                    Duration = 5 -- Set to nil to make the notification not disappear
               })
          end
          local Lighting = game:GetService("Lighting")
          Lighting.FogEnd = 100000
          for i, v in pairs(Lighting:GetDescendants()) do
               if v:IsA("Atmosphere") then
                    v:Destroy()
               end
          end
     end
})


local Lighting = game:GetService("Lighting")

local Toggle = Tabs.Settings:AddToggle("MyToggle", {Title = "FullBright", Default = false })

Toggle:OnChanged(function(Value)
_G.FullBright = Value
     if _G.FullBright then
          while _G.FullBright do task.wait(.0001)
               Lighting.Brightness = 2
               Lighting.ClockTime = 14
               Lighting.GlobalShadows = false
               Lighting.OutdoorAmbient = Color3.fromRGB(128, 128, 128)
          end
     end
end)

Options.MyToggle:SetValue(false)
-- Addons:
-- SaveManager (Allows you to have a configuration system)
-- InterfaceManager (Allows you to have a interface managment system)

-- Hand the library over to our managers
SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)

-- Ignore keys that are used by ThemeManager.
-- (we dont want configs to save themes, do we?)
SaveManager:IgnoreThemeSettings()

-- You can add indexes of elements the save manager should ignore
SaveManager:SetIgnoreIndexes({})

-- use case for doing it this way:
-- a script hub could have themes in a global folder
-- and game configs in a separate folder per game
InterfaceManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")

InterfaceManager:BuildInterfaceSection(Tabs.Settings)

Window:SelectTab(2)

repeat wait() until game.CoreGui:FindFirstChild('RobloxPromptGui')
local lp,po,ts = game:GetService('Players').LocalPlayer,game.CoreGui.RobloxPromptGui.promptOverlay,game:GetService('TeleportService')
po.ChildAdded:connect(function(a)
     if a.Name == 'ErrorPrompt' then
          repeat
               ts:Teleport(game.PlaceId)
               wait(2)
          until false
     end
end)
wait(.1)
textLabel:TweenPosition(UDim2.new(0.5, -100, 1, 0), "Out", "Quint", 1, true)
wait(1)
screenGui:Destroy()

-------------------------------------------------[[Toggle UI]]--------------------------------------------

do
     local ToggleUI = game.CoreGui:FindFirstChild("MyToggle") 
     if ToggleUI then
     ToggleUI:Destroy()
     end
end

local MyToggle = Instance.new("ScreenGui")
local ImageButton = Instance.new("ImageButton")
local UICorner = Instance.new("UICorner")

--Properties:

MyToggle.Name = "MyToggle"
MyToggle.Parent = game.CoreGui
MyToggle.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

ImageButton.Parent = MyToggle
ImageButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
ImageButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
ImageButton.BorderSizePixel = 0
ImageButton.Position = UDim2.new(0.156000003, 0, -0, 0)
ImageButton.Size = UDim2.new(0, 50, 0, 50)
ImageButton.Image = "rbxassetid://17156242075"
ImageButton.MouseButton1Click:Connect(function()
game.CoreGui:FindFirstChild("ScreenGui").Enabled = not game.CoreGui:FindFirstChild("ScreenGui").Enabled
end)


UICorner.CornerRadius = UDim.new(0, 10)
UICorner.Parent = ImageButton


setfpscap(1000)

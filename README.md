 if game:GetService("CoreGui"):FindFirstChild("Ramet") then
      game:GetService("CoreGui"):FindFirstChild("Ramet"):Destroy()
   end
   local UILib = loadstring(game:HttpGet('https://pastebin.com/raw/zj1Zd78z'))()
 
   local win = UILib:Window("Ramet",Color3.fromRGB(44, 120, 224), Enum.KeyCode.RightControl)
   local Main = win:Tab("Main")
   Main:Label("UI Toggle Key:  Right-Ctrl")
   Main:Button("Destroy UI", function()
   game.CoreGui.Ramet:Destroy()
   end)
   Main:Label("Credit : 03s.4358")
   Main:Button("Copy Discord Invite", function()
      setclipboard("https://discord.gg/M6JzkWtxFu")
      UILib:Notification("Notification", "Copied!", "Okay")
   end)
   Main:Button("Copy Youtube", function()
      setclipboard("https://www.youtube.com/channel/UCk7jgjxHK7MgRhLql-GUIHA")
      UILib:Notification("Notification", "Copied!", "Okay")
   end)
   local AutoFarm = win:Tab("Auto Farm")
   AutoFarm:Toggle("Auto Tep",false, function(State)
_G.Autotep = State
while _G.Autotep do wait()
game:GetService("ReplicatedStorage").Remotes.Events.Tap:FireServer()
wait(.1)
end
end)
   AutoFarm:Toggle("Auto Combo",false, function(State)
_G.autocombo = State
while _G.autocombo do wait()
game:GetService("ReplicatedStorage").Remotes.Events.UpdateCombo:FireServer()
end
end)
   AutoFarm:Toggle("Auto UseSuperTap",false, function(State)
_G.UseSuperTap = State
while _G.UseSuperTap do wait()
game:GetService("ReplicatedStorage").Remotes.Events.UseSuperTap:FireServer()
end
end)
AutoFarm:Dropdown("Select Rebirth", {1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20}, function(String)
  Selectre = String
end)
AutoFarm:Toggle("Auto Rebirth",false, function(State)
_G.autore = State
while _G.autore do wait()
local args = {
    [1] = Selectre
}
game:GetService("ReplicatedStorage").Remotes.Events.Rebirth:FireServer(unpack(args))
wait(.1)
end
end)
Worlds = {}
for i,v in pairs(game:GetService("Workspace").Worlds:GetChildren()) do
    table.insert(Worlds,v.Name)
end
AutoFarm:Dropdown("Select Worlds", Worlds, function(String)
    Word = String
end)
AutoFarm:Toggle("Auto Yen",false, function(State)
_G.autoyen = State
while _G.autoyen do wait()
    for i,v in pairs(game:GetService("Workspace").Worlds[Word].Yen:GetDescendants()) do
        if v.Name == "TouchInterest" then
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Parent.CFrame
wait(.1)
        end
        end
end
end)

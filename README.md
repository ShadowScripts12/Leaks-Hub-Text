local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
    Name = "Leaks Hub | Executor | Universal BR",
    Icon = "rotate-3d",
    LoadingTitle = "Carregando Leaks Hub",
    LoadingSubtitle = "Criador: Leen Scripts",
    ConfigurationSaving = {
        Enabled = true,
        FolderName = "LEAKS HUB",
        FileName = "Config"
    },
    KeySystem = True,
    Theme = "DarkBlue"
})
-- Variáveis globais
local SelectedScriptID = nil
local AutoExecute = True
local token = ""  -- Seu token aqui

local Scripts = {
    [77] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Pls%20Donate", Name = "Pls Donate"},
    [76] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Rock%20Fruit", Name = "Rock Fruit"},
    [75] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Taxi%20boss", Name = "Taxi Boss"},
    [74] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Tower%20Of%20Hell", Name = "Tower Of Hell"},
    [73] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Strongman%20Simulator", Name = "Strongman Simulator"},
    [72] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Dragon%20Ball%20Rage", Name = "Dragon Ball Rage"},
    [71] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20Smash", Name = "Anime Smash"},
    [70] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Meme%20Sea", Name = "Meme Sea"},
    [69] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Ghoul%20Re", Name = "Ghoul Re"},
    [68] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Driving%20Empire", Name = "Driving Empire"},
    [67] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20Spirits%20Journey", Name = "Anime Spirits Journey"},
    [66] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Death%20Ball", Name = "Death Ball"},
    [65] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Dawn%20Piece", Name = "Dawn Piece"},
    [64] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20Power", Name = "Anime Power"},
    [63] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Arise%20Crossover", Name = "Arise Crossover"},
    [62] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Ninja%20Time", Name = "Ninja Time"},
    [61] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Restaurant%20Tycoon%202", Name = "Restaurant Tycoon 2"},
    [60] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Dead%20Rails", Name = "Dead Rails"},
    [59] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Project%20Mugetsu", Name = "Project Mugetsu"},
    [58] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Rainbow%20Friends", Name = "Rainbow Friends"},
    [57] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20Dungeon%20Fighters", Name = "Anime Dungeon Fighters"},
    [56] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Pizza%20Place", Name = "Pizza Place"},
    [55] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/SpongeBob%20Tower%20Defense", Name = "SpongeBob Tower Defense"},
    [54] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Westbound", Name = "Westbound"},
    [53] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Kuroku's%20Basket", Name = "Kuroku's Basket"},
    [52] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Ultra%20Power%20Tycoon", Name = "Ultra Power Tycoon"},
    [51] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Teen%20Titans%20Battlegrounds", Name = "Teen Titans Battlegrounds"},
    [50] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/A%20Dusty%20Trip", Name = "A Dusty Trip"},
    [49] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Attack%20on%20Titan%20Revolution", Name = "Attack on Titan Revolution"},
    [48] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/3008", Name = "3008"},
    [47] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Forsaken", Name = "Forsaken"},
    [46] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Piggy", Name = "Piggy"},
    [45] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Flee%20the%20Facility", Name = "Flee the Facility"},
    [44] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Fling%20Things%20and%20People", Name = "FTAP"},
    [43] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/BedWars", Name = "BedWars"},
    [41] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Creatures%20of%20Sonaria", Name = "Creatures of Sonaria"},
    [40] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Build%20A%20Boat%20For%20Treasure", Name = "Build A Boat For Treasure"},
    [39] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Haikyuu%20Legends", Name = "Haikyuu Legends"},
    [38] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Toilet%20Tower%20Defense", Name = "Toilet Tower Defense"},
    [37] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20Last%20Stand", Name = "Anime Last Stand"},
    [36] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Life%20Together%20RP", Name = "Life Together RP"},
    [35] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Berry%20Avenue%20RP", Name = "Berry Avenue RP"},
    [34] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Bee%20Swarm%20Simulator", Name = "Bee Swarm Simulator"},
    [33] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Jujutsu%20Shenanigans", Name = "Jujutsu Shenanigans"},
    [32] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Rivals", Name = "Rivals"},
    [31] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/The%20strongest%20Battlegrounds", Name = "The strongest Battlegrounds"},
    [30] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Pets%20Go", Name = "Pets Go"},
    [29] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Pet%20Simulator%2099", Name = "Pet Simulator 99"},
    [28] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Blox%20Fruits", Name = "Blox Fruits"},
    [27] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Blade%20Ball", Name = "Blade Ball"},
    [26] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Blue%20Lock%20Rivals", Name = "Blue Lock Rivals"},
    [25] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Brookhaven", Name = "Brookhaven"},
    [24] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Adopt%20me", Name = "Adopt me"},
    [23] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Animal%20Simulator", Name = "Animal Simulator"},
    [22] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20Adventures", Name = "Anime Adventures"},
    [21] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20realms", Name = "Anime Realms"},
    [20] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20Reborn", Name = "Anime Reborn"},
    [18] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Anime%20Shadow", Name = "Anime Shadow"},
    [17] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Arsenal", Name = "Arsenal"},
    [16] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Dandy's%20World", Name = "Dandy's World"},
    [15] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Doors", Name = "Doors"},
    [14] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Dress%20To%20Impress", Name = "Dress To Impress"},
    [13] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Dandy's%20World", Name = "Dandy's World"},
    [12] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Evade", Name = "Evade"},
    [11] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Heroes%20Battlegrounds", Name = "Heroes Battlegrounds"},
    [10] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Shindo%20Life", Name = "Shindo Life"},
    [9] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Slayer%20Online", Name = "Slayer Online"},
    [8] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Squid%20Game%20X", Name = "Squid Game X"},
    [42] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Shrimp%20Game", Name = "Shrimp Game"},
    [6] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Lootify", Name = "Lootify"},
    [5] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Murder%20Mystery%202", Name = "Murder Mystery 2"},
    [4] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Jujutsu%20Infinite", Name = "Jujutsu Infinite"},
    [3] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Fisch", Name = "Fisch"},
    [2] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/Go%20Fishing", Name = "Go Fishing"},
    [1] = {Url = "https://raw.githubusercontent.com/ETHUS4/COMANDOS/refs/heads/main/King%20Legacy", Name = "King Legacy"},
   
   
   
}

Configuração
local function SaveSettings()
    if not writefile then
        Rayfield:Notify({
            Title = "Error",
            Content = "Seu executor não suporta salvar configurações.",
            Duration = 5,
            Image = "circle-power"
        })
        return
    end

    local json = game:GetService("HttpService"):JSONEncode({
        SelectedScriptID = SelectedScriptID,
        AutoExecute = AutoExecute
    })
    writefile("Auto-Execute.json", json)
end

Configurações
local function LoadSettings()
    if not isfile or not readfile then
        Rayfield:Notify({
            Title = "Erro",
            Content = "Seu executor não suporta carregar configurações.",
            Duration = 5,
            Image = "circle-x"
        })
        return
    end

    if isfile("Auto-Execute.json") then
        local json = readfile("Auto-Execute.json")
        local settings = game:GetService("HttpService"):JSONDecode(json)
        SelectedScriptID = settings.SelectedScriptID
        AutoExecute = settings.AutoExecute
    end
end

-- Carregar configurações ao iniciar
LoadSettings()

-- Função para execução automática
if AutoExecute and SelectedScriptID then
    local scriptData = Scripts[SelectedScriptID]
    if scriptData then
        task.delay(3, function()
            local success, err = pcall(function()
                -- Concatenar o token na URL antes do @
                local fullUrl = "https://" .. token .. "@" .. scriptData.Url:sub(9)
                loadstring(game:HttpGet(fullUrl))()
            end)
            if not success then
                Rayfield:Notify({
                    Title = "Auto-execute Bugado!",
                    Content = err,
                    Duration = 5,
                    Image = "circle-power"
                })
            else
                Rayfield:Notify({
                    Title = "Auto-Execute",
                    Content = "Script ID: " .. SelectedScriptID .. " executado após 3 segundos!",
                    Duration = 5,
                    Image = "circle-power"
                })
            end
        end)
    else
        Rayfield:Notify({
            Title = "Erro de Script",
            Content = "Script não encontrado para o ID: " .. tostring(SelectedScriptID),
            Duration = 5,
            Image = "circle-x"
        })
    end
end

-- Criar a aba "Jogos"
local TabJogos = Window:CreateTab("Jogos", "gamepad-2")
TabJogos:CreateParagraph({
    Title = "Escolha o Jogo que Deseja Jogar ou Pesquise pelo Nome",
    Content = "Dica: Explore os jogos manualmente ou use a lupa no canto superior direito para pesquisar o nome de algum jogo especifico dentro do script."
})
-- Toggle para Auto-Execute
TabJogos:CreateToggle({
    Name = "Auto-Execute",
    CurrentValue = AutoExecute,
    Callback = function(value)
        AutoExecute = value
        SaveSettings()
        Rayfield:Notify({
            Title = "Configuração Atualizada",
            Content = AutoExecute and "Auto-Execute ativado" or "Auto-Execute desativado",
            Duration = 5,
            Image = "circle-power"
        })
    end
})

-- Função para adicionar botões com scripts
local function AddScriptButton(tab, scriptData)
    tab:CreateButton({
        Name = scriptData.Name,
        Callback = function()
            -- Concatenar o token na URL antes do @
            local fullUrl = "https://" .. token .. "@" .. scriptData.Url:sub(9)
            -- Carregar o script usando o ID
            if not pcall(function() game:HttpGet(fullUrl) end) then
                Rayfield:Notify({
                    Title = "Error",
                    Content = "Não foi possível carregar o Jogo: " .. scriptData.Name,
                    Duration = 5,
                    Image = "circle-x"
                })
                return
            end

            SelectedScriptID = scriptData.Id
            loadstring(game:HttpGet(fullUrl))()
            SaveSettings()
            Rayfield:Notify({
                Title = "Leaks Hub",
                Content = scriptData.Name .. " Script carregado com sucesso!",
                Duration = 5,
                Image = "chevrons-left-right-ellipsis"
            })
        end
    })
end

-- Adicionar botões para os jogos
for id, data in pairs(Scripts) do
    data.Id = id  -- Adiciona o ID ao script
    AddScriptButton(TabJogos, data)
end

local MainTab = Window:CreateTab("Fixos", "zap") -- Ícone de zap (ID do Roblox)

MainTab:CreateParagraph({
    Title = "Oque são os scripts fixos no Leaks Hub?",
    Content = "Dica: Os Scripts fixos servem parar poupar o tempo de nossos usuarios a procura de alguns scripts básicos e específicos. "
})
-- Variáveis globais
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer
local CamlockState = false
local Prediction = 0.16
local enemy = nil

-- Função para encontrar o inimigo mais próximo
function FindNearestEnemy()
    local ClosestDistance, ClosestPlayer = math.huge, nil
    local CenterPosition =
        Vector2.new(
        game:GetService("GuiService"):GetScreenResolution().X / 2,
        game:GetService("GuiService"):GetScreenResolution().Y / 2
    )
    for _, Player in ipairs(Players:GetPlayers()) do
        if Player ~= LocalPlayer then
            local Character = Player.Character
            if Character and Character:FindFirstChild("HumanoidRootPart") and Character.Humanoid.Health > 0 then
                local Position, IsVisibleOnViewport =
                    game:GetService("Workspace").CurrentCamera:WorldToViewportPoint(Character.HumanoidRootPart.Position)
                if IsVisibleOnViewport then
                    local Distance = (CenterPosition - Vector2.new(Position.X, Position.Y)).Magnitude
                    if Distance < ClosestDistance then
                        ClosestPlayer = Character.HumanoidRootPart
                        ClosestDistance = Distance
                    end
                end
            end
        end
    end
    return ClosestPlayer
end

-- Função para ajustar a câmera no inimigo
RunService.Heartbeat:Connect(function()
    if CamlockState and enemy then
        local camera = workspace.CurrentCamera
        camera.CFrame = CFrame.new(camera.CFrame.p, enemy.Position + enemy.Velocity * Prediction)
    end
end)

-- Toggle para ativar/desativar o aimbot
MainTab:CreateToggle({
    Name = "Aimbot",
    CurrentValue = false,
    Flag = "AimbotToggle", -- Salva o estado do toggle
    Callback = function(state)
        CamlockState = state
        if state then
            enemy = FindNearestEnemy()
            Rayfield:Notify({
                Title = "Aimbot Ativado",
                Content = "O aimbot foi ativado.",
                Duration = 5,
                Image = "circle-pause" -- Ícone de ativação
            })
        else
            enemy = nil
            Rayfield:Notify({
                Title = "Aimbot Desativado",
                Content = "O aimbot foi desativado.",
                Duration = 5,
                Image = "circle-play" -- Ícone de desativação
            })
        end
    end
})
-- Variáveis para destacar jogadores
local FillColorEnemy = Color3.fromRGB(255, 0, 0)  -- Vermelho para inimigos
local FillColorFriend = Color3.fromRGB(0, 0, 255)  -- Azul para amigos
local DepthMode = "AlwaysOnTop"
local FillTransparency = 0.5
local OutlineColor = Color3.fromRGB(255, 255, 255)
local OutlineTransparency = 0

local CoreGui = game:FindService("CoreGui")
local Players = game:FindService("Players")
local lp = Players.LocalPlayer
local connections = {}

local Storage = Instance.new("Folder")
Storage.Parent = CoreGui
Storage.Name = "Highlight_Storage"

-- Função para destacar jogadores
local function Highlight(plr)
    if plr == lp then return end  -- Ignora o próprio jogador

    local Highlight = Instance.new("Highlight")
    Highlight.Name = plr.Name
    Highlight.DepthMode = DepthMode
    Highlight.FillTransparency = FillTransparency
    Highlight.OutlineColor = OutlineColor
    Highlight.OutlineTransparency = 0
    Highlight.Parent = Storage

    -- Define a cor de acordo com se o jogador é amigo ou inimigo
    if lp.Team == plr.Team then
        Highlight.FillColor = FillColorFriend  -- Azul para amigos
    else
        Highlight.FillColor = FillColorEnemy  -- Vermelho para inimigos
    end

    local plrchar = plr.Character
    if plrchar then
        Highlight.Adornee = plrchar
    end

    -- Atualiza o Adornee caso o personagem mude
    connections[plr] = plr.CharacterAdded:Connect(function(char)
        if plr == lp then return end  -- Ignora o próprio jogador
        Highlight.Adornee = char
    end)
end

-- Toggle para ativar/desativar o espelhamento de jogadores
MainTab:CreateToggle({
    Name = "Espelhar jogadores",
    CurrentValue = false,
    Flag = "MirrorPlayersToggle", -- Salva o estado do toggle
    Callback = function(state)
        if state then
            -- Ativa o espelhamento de jogadores
            for _, plr in ipairs(Players:GetPlayers()) do
                if plr ~= lp then
                    Highlight(plr)
                end
            end
            Players.PlayerAdded:Connect(Highlight)
            Rayfield:Notify({
                Title = "Espelhamento Ativado",
                Content = "Os jogadores estão sendo destacados.",
                Duration = 5,
                Image = "eye" -- Ícone de ativação
            })
        else
            -- Desativa o espelhamento de jogadores
            for _, plr in ipairs(Players:GetPlayers()) do
                if plr ~= lp and Storage:FindFirstChild(plr.Name) then
                    Storage[plr.Name]:Destroy()
                end
            end
            Players.PlayerAdded:Disconnect(Highlight)
            Rayfield:Notify({
                Title = "Espelhamento Desativado",
                Content = "Os jogadores não estão mais destacados.",
                Duration = 5,
                Image = "eye-off" -- Ícone de desativação
            })
        end
    end
})


local function executeLoading()
    -- Aqui vai o código do Pastebin
    loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
end

local Lighting = game:GetService("Lighting")
local Workspace = game:GetService("Workspace")
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local StarterGui = game:GetService("StarterGui")

-- Função para aplicar Gráfico Realista
local function applyRealisticGraphics()
    -- Configurações básicas de iluminação
    Lighting.Brightness = 2
    Lighting.ClockTime = 14
    Lighting.GlobalShadows = true
    Lighting.OutdoorAmbient = Color3.fromRGB(128, 128, 128)
    Lighting.Technology = Enum.Technology.Future

    -- Efeitos de atmosfera
    local Atmosphere = Instance.new("Atmosphere", Lighting)
    Atmosphere.Density = 0.3
    Atmosphere.Offset = 0
    Atmosphere.Color = Color3.fromRGB(199, 220, 255)
    Atmosphere.Decay = Color3.fromRGB(106, 112, 125)
    Atmosphere.Glare = 0.2
    Atmosphere.Haze = 0.5

    -- Configuração da neblina
    Lighting.FogStart = 3
    Lighting.FogEnd = 500
    Lighting.FogColor = Color3.fromRGB(191, 191, 191)
    Lighting.ShadowSoftness = 0.2

    -- Adicionando efeito de brilho (Bloom)
    local Bloom = Instance.new("BloomEffect", Lighting)
    Bloom.Intensity = 0.7
    Bloom.Size = 24
    Bloom.Threshold = 2

    -- Correção de cor
    local ColorCorrection = Instance.new("ColorCorrectionEffect", Lighting)
    ColorCorrection.Brightness = 0.05
    ColorCorrection.Contrast = 0.2
    ColorCorrection.Saturation = 0.3
    ColorCorrection.TintColor = Color3.fromRGB(255, 240, 220)

    -- Profundidade de campo
    local DepthOfField = Instance.new("DepthOfFieldEffect", Lighting)
    DepthOfField.FarIntensity = 0.1
    DepthOfField.FocusDistance = 0
    DepthOfField.InFocusRadius = 255
    DepthOfField.NearIntensity = 0.5

    -- Criar nuvens animadas
    local function createClouds()
        local cloudModel = Instance.new("Model", Workspace)
        cloudModel.Name = "Clouds"

        for i = 1, 10 do
            local cloud = Instance.new("Part", cloudModel)
            cloud.Size = Vector3.new(50, 10, 50)
            cloud.Position = Vector3.new(math.random(-500, 500), 200, math.random(-500, 500))
            cloud.Anchored = true
            cloud.Transparency = 0.7
            cloud.Material = Enum.Material.SmoothPlastic
            cloud.Color = Color3.fromRGB(255, 255, 255)
            cloud.Name = "Cloud"

            -- Mover nuvens lentamente
            RunService.RenderStepped:Connect(function()
                cloud.Position = cloud.Position + Vector3.new(0.05, 0, 0)
                if cloud.Position.X > 500 then
                    cloud.Position = Vector3.new(-500, cloud.Position.Y, cloud.Position.Z)
                end
            end)
        end
    end

    -- Criar sombras das nuvens no chão
    local function createCloudShadows()
        local shadowFolder = Instance.new("Folder", Workspace)
        shadowFolder.Name = "CloudShadows"

        for _, cloud in ipairs(Workspace.Clouds:GetChildren()) do
            local shadow = Instance.new("Part", shadowFolder)
            shadow.Size = Vector3.new(cloud.Size.X, 0.1, cloud.Size.Z)
            shadow.Position = Vector3.new(cloud.Position.X, 0.1, cloud.Position.Z)
            shadow.Anchored = true
            shadow.Transparency = 0.9
            shadow.Material = Enum.Material.SmoothPlastic
            shadow.Color = Color3.fromRGB(0, 0, 0)
            shadow.Name = cloud.Name .. "_Shadow"

            -- Atualizar posição da sombra
            RunService.RenderStepped:Connect(function()
                shadow.Position = Vector3.new(cloud.Position.X, 0.1, cloud.Position.Z)
            end)
        end
    end

    -- Mostrar notificação
    local function showNotification()
        StarterGui:SetCore("SendNotification", {
            Title = "Notificação",
            Text = "Gráficos criados por Leaks Hub",
            Duration = 7
        })
    end

    -- Inicializar nuvens, sombras e notificação
    createClouds()
    createCloudShadows()
    showNotification()

    print("Nuvens, sombras e notificação carregadas com sucesso!")
end

-- Função para restaurar gráficos para o padrão
local function restoreDefaultGraphics()
    -- Restaura as configurações padrão de iluminação
    Lighting.Brightness = 1
    Lighting.ClockTime = 12
    Lighting.GlobalShadows = false
    Lighting.OutdoorAmbient = Color3.fromRGB(255, 255, 255)
    Lighting.Technology = Enum.Technology.Legacy

    -- Limpa efeitos de atmosfera, neblina, etc.
    for _, effect in ipairs(Lighting:GetChildren()) do
        if effect:IsA("Atmosphere") or effect:IsA("BloomEffect") or effect:IsA("ColorCorrectionEffect") or effect:IsA("DepthOfFieldEffect") then
            effect:Destroy()
        end
    end

    -- Limpar nuvens e sombras
    if Workspace:FindFirstChild("Clouds") then
        Workspace.Clouds:Destroy()
    end
    if Workspace:FindFirstChild("CloudShadows") then
        Workspace.CloudShadows:Destroy()
    end

    print("Gráficos restaurados para o padrão.")
end

-- Criação da Toggle para ativar/desativar Gráfico Realista
MainTab:CreateToggle({
    Name = "Gráfico Realista",
    CurrentValue = false,
    Flag = "RealisticGraphicsToggle", -- Salva o estado do toggle
    Callback = function(state)
        if state then
            applyRealisticGraphics()  -- Ativa Gráfico Realista
            Rayfield:Notify({
                Title = "Gráfico Realista",
                Content = "Gráfico Realista foi ativado.",
                Duration = 5,
                Image = "camera" -- Ícone de ativação
            })
        else
            restoreDefaultGraphics()  -- Restaura gráficos padrão
            Rayfield:Notify({
                Title = "Gráfico Desativado",
                Content = "O Gráfico Realista foi desativado.",
                Duration = 5,
                Image = "camera-off" -- Ícone de desativação
            })
        end
    end
})

local Slider = MainTab:CreateSlider({
   Name = "Velocidade",
   Range = {0, 100},
   Increment = 10,
   Suffix = "Velocidade atual",
   CurrentValue = 16,
   Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
          game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = (Value)
   end,
})


local JumpSlider = MainTab:CreateSlider({
   Name = "Pulo",
   Range = {0, 100},
   Increment = 10,
   Suffix = "Altura atual",
   CurrentValue = 50,  -- Valor inicial do pulo
   Flag = "Slider2",  -- Flag única para este slider
   Callback = function(Value)
          game.Players.LocalPlayer.Character.Humanoid.JumpHeight = Value
   end,
})

-- Botão de Loading
MainTab:CreateButton({
    Name = "<-> Infinity Yield", -- Nome do botão
    Callback = function()
        executeLoading() -- Executa o loading quando o botão for clicado
    end
})
local function executeLoading()
    -- Aqui vai o código do Pastebin
    loadstring(game:HttpGet('https://pastebin.com/raw/GPpLCnQR'))()
end



-- Botão de Loading
MainTab:CreateButton({
    Name = "<-> Chat Anti-Tags", -- Nome do botão
    Callback = function()
        executeLoading() -- Executa o loading quando o botão for clicado
    end
})

local function executeLoading()
    -- Aqui vai o código do Pastebin
    loadstring(game:HttpGet('https://rawscripts.net/raw/Universal-Script-antilag-15462'))()
end



-- Botão de Loading
MainTab:CreateButton({
    Name = "<-> Remover Texturas", -- Nome do botão
    Callback = function()
        executeLoading() -- Executa o loading quando o botão for clicado
    end
})

local function executeLoading()
    -- Aqui vai o código do Pastebin
    loadstring(game:HttpGet('https://pastebin.com/raw/A4r1pHJY'))()
end



-- Botão de Loading
MainTab:CreateButton({
    Name = "<-> Servidor Privado", -- Nome do botão
    Callback = function()
        executeLoading() -- Executa o loading quando o botão for clicado
    end
})


local function executeLoading()
    -- Aqui vai o código do Pastebin
    loadstring(game:HttpGet('https://pastebin.com/raw/qysTtrJD'))()
end



-- Botão de Loading
MainTab:CreateButton({
    Name = "<-> TP Tools", -- Nome do botão
    Callback = function()
        executeLoading() -- Executa o loading quando o botão for clicado
    end
})

local ServeTab = Window:CreateTab("Serve", "globe") -- Ícone opcional, pode substituir pelo ID desejado

ServeTab:CreateParagraph({
    Title = "Entre em Servidores que Você Já Entrou Antes",
    Content = "Dica: Copie o ID do servidor atual para acessá-lo novamente no futuro, utilizando apenas o ID de identificação."
})

-- Botão para copiar o ID do servidor atual
ServeTab:CreateButton({
    Name = "Copiar ID do Servidor Atual",
    Callback = function()
        local serverId = game.JobId -- Obtém o ID do servidor atual
        if setclipboard then
            setclipboard(serverId) -- Copia para a área de transferência
            Rayfield:Notify({
                Title = "Sucesso!",
                Content = "ID do servidor copiado para a área de transferência.",
                Duration = 5,
                Image = "badge-check",
            })
        else
            Rayfield:Notify({
                Title = "Erro!",
                Content = "Seu executor não suporta copiar para a área de transferência.",
                Duration = 5,
                Image = "badge-alert",
            })
        end
    end
})

-- Campo de texto para inserir o ID do servidor
local serverIdInput = ""
ServeTab:CreateInput({
    Name = "ID do Servidor para Teleportar",
    PlaceholderText = "Insira o ID do servidor aqui",
    Callback = function(input)
        serverIdInput = input -- Armazena o ID inserido pelo usuário
    end
})

-- Botão para confirmar e teleportar para o servidor
ServeTab:CreateButton({
    Name = "Teleportar para o Servidor",
    Callback = function()
        if serverIdInput and serverIdInput ~= "" then
            local TeleportService = game:GetService("TeleportService")
            local placeId = game.PlaceId -- Obtém o PlaceId do jogo atual
            TeleportService:TeleportToPlaceInstance(placeId, serverIdInput, game.Players.LocalPlayer)
        else
            Rayfield:Notify({
                Title = "Erro!",
                Content = "Por favor, insira um ID de servidor válido antes de teleportar.",
                Duration = 5,
                Image = "badge-alert",
            })
        end
    end
})

local AdminTab = Window:CreateTab("Editor", "file-pen")
AdminTab:CreateParagraph({
    Title = "Ferramenta Avançada para Criar Scripts",
    Content = "Dica: Desenvolvemos uma ferramenta dedicada para criadores de scripts em linguagem Lua. Com ela, você pode criar e ofuscar seus scripts de forma segura e eficiente, diretamente no nosso script Universal."
})
-- Adicionar botões para scripts de Admin
AddScriptButton(AdminTab, {Name = "Em Breve...", Url = "Url"})


local ManualTab = Window:CreateTab("Manual", "notebook-tabs") -- icone no formato de ID (substitua se necessario)


ManualTab:CreateButton({
    Name = "Clique para copiar o link do discord",
    Callback = function()
        setclipboard("https://discord.gg/rgrSMDrrM5")
        Rayfield:Notify({
            Title = "Discord copiado",
            Content = "O link foi copiado para sua area de transferência!",
            Duration = 5,
            Image = "clipboard-check", -- Substitua pelo ID do icone, se desejar
        })
    end
})


ManualTab:CreateParagraph({
    Title = "1. Jogos",
    Content = "Antes de abrir a pasta com os scripts, é necessário escolher o jogo para utilizar os scripts disponíveis. Você pode localizar os scripts manualmente navegando pelas pastas ou utilizar a ferramenta de pesquisa no canto superior direito para encontrar o jogo desejado."
})

ManualTab:CreateParagraph({
    Title = "2. Fixos",
    Content = "Os scripts fixos são scripts pré-definidos que permanecem disponíveis no painel principal e na pasta dos jogos, facilitando o acesso a scripts simples e específicos de forma rápida e prática."
})

ManualTab:CreateParagraph({
    Title = "3. Servidores",
    Content = "A aba dos servidores permite que o usuário acesse futuramente o mesmo servidor utilizando apenas o ID de identificação previamente copiado."
})

ManualTab:CreateParagraph({
    Title = "4. Editor",
    Content = "O editor de scripts é destinado aos desenvolvedores, permitindo que criem seus próprios scripts com facilidade. Além disso, disponibilizamos nossas ferramentas para auxiliá-los no processo de desenvolvimento."
})


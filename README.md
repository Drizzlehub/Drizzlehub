drizzlelib local = loadstring(game:HttpGet("https://raw.githubusercontent.com/DRIZZLeHUB/drizzleLibV5/main/Source.Lua"))()
Janela local = drizzlelib:MakeWindow({
  Title = "drizzle Hub: Frutas Blox",
  SubTitle = "por chuvisco",
  SaveFolder = "drizzle Hub | Blox Fruits.lua"
})

AFKOptions locais = {}

discórdia local = Window:MakeTab({"Discord", "Info"})
Discord:AddDiscordInvite({
  Nome = "herdroock | Community",
  Description = "Junte-se à nossa comunidade discord para receber informações sobre a próxima atualização",
  Logotipo = "rbxassetid://15298567397",
  Convidar = "https://discord.com/invite/3WenJsyKpq"
})
local MainFarm = Window:MakeTab({"Fazenda", "Home"})
se Sea3 então
  local AutoSea = Window:MakeTab({"Mar", "Ondas"})
  AutoSea:AddSection({"Kitsune"})
  local KILabel = AutoSea:AddParagraph({"Ilha Kitsune: não aparece"})
  AutoSea:AddToggle({Nome = "Ilha Auto Kitsune",Callback = função(Valor)
    getgenv().AutoKitsuneIsland = Valor;AutoKitsuneIsland()
  fim})
  AutoSea:AddToggle({Nome = "Auto Trade Azure Ember",Callback = function(Valor)
    getgenv().TradeAzureEmber = Valor
    tarefa.spawn(função()
      Módulos locais = ReplicatedStorage:WaitForChild("Módulos", 9e9)
      Rede local = Módulos:WaitForChild("Rede", 9e9)
      local KitsuneRemote = Net:WaitForChild("RF/KitsuneStatuePray", 9e9)
      
      enquanto getgenv().TradeAzureEmber faz task.wait(1)
        KitsuneRemote:InvokeServer()
      fim
    fim)
  fim})
  tarefa.spawn(função()
    mapa local = espaço de trabalho:WaitForChild("Mapa", 9e9)
    tarefa.spawn(função()
      enquanto task.wait() faz
        if Mapa:FindFirstChild("Ilha Kitsune") então
          plrPP local = Player.Character e Player.Character.PrimaryPart
          se plrPP então
            Distância = tostring(math.floor((plrPP.Position - Map.KitsuneIsland.WorldPivot.p).Magnitude / 3))
          fim
        fim
      fim
    fim)
    
    enquanto task.wait() faz
      if Mapa:FindFirstChild("Ilha Kitsune") então
        KILabel:SetTitle("Ilha Kitsune: Gerada | Distância: ".. Distância)
      outro
        KILabel:SetTitle("Ilha Kitsune: não Spawn")
      fim
    fim
  fim)
  AutoSea:AddSection({"Mar"})
  AutoSea:AddToggle({Nome = "Auto Farm Sea",Callback = function(Valor)
    getgenv().AutoFarmSea = Valor;AutoFarmSea()
  fim})
  AutoSea:AddButton({Name = "Comprar Barco Novo",Callback = function()
    ComprarNovoBarco()
  fim})
  AutoSea:AddSection({"Material"})
  AutoSea:AddToggle({"Pranchas de madeira automáticas", false, function(Valor)
    getgenv().AutoWoodPlanks = Valor
    tarefa.spawn(função()
      mapa local = espaço de trabalho:WaitForChild("Mapa", 9e9)
      local BoatCastle = Mapa:WaitForChild("Castelo do Barco", 9e9)
      
      função local TreeModel()
        for _,Modelo em pares(BoatCastle["IslandModel"]:GetChildren()) do
          se Model.Name == "Model" e Model:FindFirstChild("Tree") então
            modelo de retorno
          fim
        fim
      fim
      
      função local GetTree()
        Árvore local = TreeModel()
        se árvore então
          local Mais próximo = math.huge
          local selecionado
          for _,árvore em pares(Árvore:GetChildren()) faça
            plrPP local = Player.Character e Player.Character.PrimaryPart
            se árvore e árvore.PrimaryPart e árvore.PrimaryPart.Anchored então
              se plrPP e (plrPP.Position - tree.PrimaryPart.Position).Magnitude < Mais próximo então
                Mais próximo = (plrPP.Position - tree.PrimaryPart.Position).Magnitude
                selecionado = árvore
              fim
            fim
          fim
          retornar selecionado
        fim
      fim
      
      local RandomEquip = ""
      tarefa.spawn(função()
        enquanto getgenv().AutoWoodPlanks faz
          se VerifyToolTip("Melee") então
            RandomEquip = "corpo a corpo"task.wait(2)
          fim
          se VerifyToolTip("Blox Fruit") então
            RandomEquip = "Blox Fruit"task.wait(3)
          fim
          se VerifyToolTip("Espada") então
            RandomEquip = "Espada"task.wait(2)
          fim
          se VerifyToolTip("Arma") então
            RandomEquip = "Arma"task.wait(2)
          fim
        fim
      fim)
      
      enquanto getgenv().AutoWoodPlanks faz task.wait()
        Árvore local = GetTree()EquipToolTip(RandomEquip)
        
        se Tree e Tree.PrimaryPart então
          PlayerTP(Tree.PrimaryPart.CFrame)
          plrPP local = Player.Character e Player.Character.PrimaryPart
          se plrPP e (plrPP.Position - Tree.PrimaryPart.Position).Magnitude <10 então
            se getgenv().SeaSkillZ então
              TecladoPressionar("Z")
            fim
            se getgenv().SeaSkillX então
              TecladoPressionar("X")
            fim
            se getgenv().SeaSkillC então
              TecladoPressione("C")
            fim
            se getgenv().SeaSkillV então
              TecladoPressionar("V")
            fim
            se getgenv().SeaSkillF então
              TecladoPressione("F")
            fim
            se getgenv().SeaAimBotSkill então
              AimBotPart(Tree.PrimaryPart)
            fim
          fim
        fim
      fim
    fim)
  fim})
  AutoSea:AddSection({"Modo Pânico"})
  AutoSea:AddSlider({Nome = "Selecionar Saúde",Min = 20,Max = 70,Padrão = 25,Callback = função(Valor)
    getgenv().HealthPanic = Valor
  fim})
  AutoSea:AddToggle({"Modo Pânico", true, function(Valor)
    getgenv().PanicMode = Valor
  final, "Modo Mar/Pânico"})
  AutoSea:AddSection({"Seleção de Fazenda"})
  AutoSea:AddParagraph({"Peixe"})
  AutoSea:AddToggle({Nome = "Terrorshark", Flag = "Sea/TerrorShark", Padrão = true,Callback = function(Valor)
    getgenv().Terrorshark = Valor
  fim})
  AutoSea:AddToggle({Nome = "Piranha", Flag = "Mar/Piranha", Padrão = true,Callback = function(Valor)
    getgenv().Piranha = Valor
  fim})
  AutoSea:AddToggle({Nome = "Membro da Tripulação de Peixe", Flag = "Sea/FishCrewMember", Padrão = true,Callback = function(Valor)
    getgenv().FishCrewMember = Valor
  fim})
  AutoSea:AddToggle({Nome = "Tubarão", Flag = "Mar/Tubarão", Padrão = verdadeiro,Callback = função(Valor)
    getgenv().Shark = Valor
  fim})
  AutoSea:AddParagraph({"Barcos"})
  AutoSea:AddToggle({Nome = "Brigada Pirata", Flag = "Brigada Marítima/Pirata", Padrão = true,Callback = function(Valor)
    getgenv().PirateBrigade = Valor
  fim})
  AutoSea:AddToggle({Name = "Grande Brigada Pirata", Flag = "Sea/PirateGrandBrigade", Padrão = true,Callback = function(Valor)
    getgenv().PirateGrandBrigade = Valor
  fim})
  AutoSea:AddToggle({Nome = "Barco de Peixe", Flag = "Mar/Barco de Peixe", Default = true,Callback = function(Valor)
    getgenv().FishBoat = Valor
  fim})
  --[[AddTextLabel(AutoSea, {"Sea Beast"})
  AutoSea:AddToggle({Nome = "Sea Beast",Default = true,Callback = function(Valor)
    getgenv().SeaBeast = Valor
  fim})
  AutoSea:AddToggle({Nome = "Triple Sea Beast",Default = true,Callback = function(Valor)
    getgenv().SeaBeastTriple = Valor
  fim})]]
  AutoSea:AddSection({"Habilidade"})
  AutoSea:AddToggle({Name = "AimBot Skill Enemie", Flag = "Maestria/Aimbot", Padrão = true,Callback = function(Valor)
    getgenv().SeaAimBotSkill = Valor
  fim})
  AutoSea:AddToggle({Nome = "Habilidade Z", Flag = "Maestria/Z", Padrão = verdadeiro, Retorno de chamada = função (Valor)
    getgenv().SeaSkillZ = Valor
  fim})
  AutoSea:AddToggle({Nome = "Habilidade X", Flag = "Maestria/X", Padrão = true,Callback = função(Valor)
    getgenv().SeaSkillX = Valor
  fim})
  AutoSea:AddToggle({Nome = "Habilidade C", Flag = "Maestria/C", Padrão = true,Callback = função(Valor)
    getgenv().SeaSkillC = Valor
  fim})
  AutoSea:AddToggle({Nome = "Habilidade V", Flag = "Maestria/V", Padrão = verdadeiro,Callback = função(Valor)
    getgenv().SeaSkillV = Valor
  fim})
  AutoSea:AddToggle({Nome = "Habilidade F", Flag = "Maestria/F", Retorno de chamada = função(Valor)
    getgenv().SeaSkillF = Valor
  fim})
  AutoSea:AddSection({"NPCs"})
  AutoSea:AddToggle({Name = "Teleporte para Shark Hunter",Callback = function(Valor)
    getgenv().NPCtween = Valor
    tarefa.spawn(função()
      enquanto getgenv().NPCtween faz task.wait()
        PlayerTP(CFrame.new(-16526, 108, 752))
      fim
    fim)
  fim})
  AutoSea:AddToggle({Name = "Teleporte para Beast Hunter",Callback = function(Valor)
    getgenv().NPCtween = Valor
    tarefa.spawn(função()
      enquanto getgenv().NPCtween faz task.wait()
        PlayerTP(CFrame.new(-16281, 73, 263))
      fim
    fim)
  fim})
  AutoSea:AddToggle({Nome = "Teletransportar para espiar",Callback = function(Valor)
    getgenv().NPCtween = Valor
    tarefa.spawn(função()
      enquanto getgenv().NPCtween faz task.wait()
        PlayerTP(CFrame.new(-16471, 528, 539))
      fim
    fim)
  fim})
  AutoSea:AddSection({"Configurações"})
  AutoSea:AddDropdown({
    Nome = "Interpolação do Nível do Mar",
    Opções = {"1", "2", "3", "4", "5", "6", "inf"},
    Padrão = {"6"},
    Bandeira = "Mar/Nível do Mar",
    Retorno de chamada = função (Valor)
      getgenv().SeaLevelTP = Valor
    fim
  })
  AutoSea:AddSlider({
    Nome = "Velocidade de interpolação do barco",
    Mínimo = 100,
    Máx. = 300,
    Aumento = 10,
    Padrão = 250,
    Flag = "Velocidade do mar/barco",
    Retorno de chamada = função (Valor)
      getgenv().SeaBoatSpeed = Valor
    fim
  })
fim
se Sea3 e IsOwner então
  local MirageTab = Window:MakeTab({"Race V4", ""})
  
  MirageTab:AddToggle({"Alavanca de tração automática", false, function(Valor)
    
  fim})
  
  MirageTab:AddToggle({"Auto Stone Puzzle", false, function(Valor)
    
  fim})
  
  MirageTab:AddSection({"Miragem Automática"})
  
  MirageTab:AddToggle({"Auto Find Mirage", false, function(Valor)
    
  fim})
  
  MirageTab:AddToggle({"Auto Gear Puzzle", false, function(Valor)
    getgenv().AutoMiragePuzzle = Valor
    
    função local GetGear()
      
    fim
    
    função local LookToMoon()
      MoonDirection local = Iluminação:GetMoonDirection()
      local LookToPos = Camera.CFrame.p + moonDir * 100
      Câmera.CFrame = CFrame.lookAt(Camera.CFrame.p, LookToPos0)
    fim
    
    Conexão local = RunService.Heartbeat:Connect(LookToMoon)
    enquanto getgenv().AutoMiragePuzzle faz task.wait()end
    se Conexão então
      Conexão:Desconectar()
    fim
  fim})
  
  MirageTab:AddSection({"Corrida Automática"})
  
  MirageTab:AddToggle({"Auto Finish Trial", false, function(Value)
    getgenv().AutoFinishTrial = Valor
    tarefa.spawn(função()
      PlayerRace local
      tarefa.spawn(função()
        enquanto getgenv().AutoFinishTrial faz task.wait()
          PlayerRace = Player.Data.Race.Value
        fim
      fim)
      
      enquanto getgenv().AutoFinishTrial faz task.wait()
        se PlayerRace e typeof(PlayerRace) == "string" então
          se PlayerRace == "Cyborg" então
            PlayerTP(CFrame.new(28654, 14898, -30))
          elseif PlayerRace == "Ghoul" então
            Aura mortal()
          elseif PlayerRace == "Humano" então
            Aura mortal()
          elseif PlayerRace == "Mink" então
            para _,parte em pares(workspace:GetDescendants()) faça
              se part.Name == "Ponto Inicial" então
                PlayerTP(part.CFrame)
              fim
            fim
          elseif PlayerRace == "Skypiea" então
            pcall(função()
              para _, parte em pares (workspace.Map.SkyTrial.Model:GetDescendants()) faça
                se part.Name == "snowisland_Cylinder.081" então
                  PlayerTP(part.CFrame)
                fim
              fim
            fim)
          fim
        fim
      fim
    fim)
  fim})
fim
local QuestsTabs = Window:MakeTab({"Missões/Itens", "Espadas"})
local FruitAndRaid = Window:MakeTab({"Fruit/Raid", "Cherry"})
--[[Informações locais = Window:MakeTab({"Info", "Search"})
Informações:AddSection({"Player"})
local Nerd = Informações:AddParagraph({"Nerd < Informações sobre Acessórios >"})
tarefa.spawn(função()
  enquanto task.wait() faz
    Nerd:SetDesc(FireRemote("Nerd"))
  fim
fim)]]
se PlayerLevel.Value <MaxLavel então
  local StatsTab = Window:MakeTab({"Estatísticas", "sinal"})
  pontos locaisSlider, corpo a corpo, defesa, espada, arma, DemonFruit = 1
  
  função local AutoStats()
    função local AddStats(Estatísticas)
      se Player.Data.Points.Value >= 1 então
        Pontos locais = math.clamp(PointsSlider, 1, Player.Data.Points.Value)
			  FireRemote("AddPoint", Estatísticas, Pontos)
			fim
    fim
    
    enquanto getgenv().AutoStats faz task.wait()
      se corpo a corpo então
        AddStats("Corpo a Corpo")
      fim
      se Defesa então
        AddStats("Defesa")
      fim
      se espada então
        AddStats("Espada")
      fim
      se arma então
        AddStats("Arma")
      fim
      se DemonFruit então
        AddStats("Fruta Demoníaca")
      fim
    fim
  fim
  
  Guia Estatísticas:AddToggle({
    Nome = "Estatísticas Automáticas",
    Sinalizador = "Estatísticas/AutoEstatísticas",
    Retorno de chamada = função (Valor)
      getgenv().AutoStats = Valor
      Estatísticas automáticas()
    fim
  })
  
  Guia Estatísticas:AdicionarSlider({
    Nome = "Selecionar Pontos",
    Flag = "Estatísticas/SelectPoints",
    Mínimo = 1,
    Máx. = 100,
    Aumento = 1,
    Padrão = 1,
    Retorno de chamada = função (Valor)
      PontosSlider = Valor
    fim
  })
  
  Guia Estatísticas:AddSection({"Selecionar Estatísticas"})
  
  StatsTab:AddToggle({Nome = "Melee", Flag = "Stats/SelectMelee", Callback = function(Valor)
    Corpo a corpo = Valor
  fim})
  StatsTab:AddToggle({Nome = "Defesa", Flag = "Estatísticas/SelectDefesa", Callback = função(Valor)
    Defesa = Valor
  fim})
  StatsTab:AddToggle({Nome = "Espada", Flag = "Estatísticas/SelectSword", Retorno de chamada = função(Valor)
    Espada = Valor
  fim})
  StatsTab:AddToggle({Nome = "Arma", Flag = "Estatísticas/SelectGun", Retorno de chamada = função(Valor)
    Arma = Valor
  fim})
  StatsTab:AddToggle({Nome = "Fruta Demoníaca", Flag = "Estatísticas/SelectDemonFruit", Retorno de chamada = função(Valor)
    Fruta Demoníaca = Valor
  fim})
fim
Teleporte local = Window:MakeTab({"Teleporte", "Localizar"})
local Visual = Window:MakeTab({"Visual", "Usuário"})
Loja local = Janela:MakeTab({"Loja", "Carrinho"})
local Diversos = Window:MakeTab({"Diversos", "Configurações"})

MainFarm:AdicionarDropdown({
  Nome = "Ferramenta Agrícola",
  Opções = {"Melee", "Espada", "Fruta Blox"},
  Padrão = {"corpo a corpo"},
  Flag = "Principal/FarmTool",
  Retorno de chamada = função (Valor)
    getgenv().FarmTool = Valor
  fim
})

se PlayerLevel.Value >= MaxLavel e Sea3 então
  MainFarm:AddToggle({
    Name = "Iniciar Multi Farm < BETA >",
    Retorno de chamada = função (Valor)
      tabela.foreach(AFKOptions, função(_,Val)
        tarefa.spawn(função()
          Val:Definir(Valor)
        fim)
      fim)
    fim
  })
fim

MainFarm:AddSection({"Fazenda"})

MainFarm:AddToggle({"Nível de Farm Automático", false, function(Valor)
  getgenv().AutoFarm_Level = Valor;AutoFarm_Level()
fim, Descrição = "Fazenda Lavel"})

MainFarm:AddToggle({"Auto Farm mais próximo", false, function(Valor)
  getgenv().AutoFarmNearest = Valor;AutoFarmNearest()
fim})

se Sea3 então
  table.insert(AFKOptions, MainFarm:AddToggle({"Auto Pirates Sea", false, function(Value)
    getgenv().AutoPiratesSea = Valor;AutoPiratesSea()
  fim}))
elseif Sea2 então
  MainFarm:AddToggle({"Fábrica Automática", false, function(Valor)
    getgenv().AutoFactory = Valor;AutoFactory()
  fim})
fim

--[[MainFarm:AddSection({"Natal"})

local TimeLabel = MainFarm:AddLabel({"Text", "Tempo para o próximo presente: nil"})

tarefa.spawn(função()
  Contador local = espaço de trabalho:WaitForChild("Contagem regressiva", 9e9)
  local SurfaceGui = Contador:WaitForChild("SurfaceGui", 9e9)
  local TextLabel = SurfaceGui:WaitForChild("TextLabel", 9e9)
  
  enquanto task.wait() faz
    TimeLabel:SetTitle("Tempo para o próximo presente: " .. TextLabel.Text)
    
    if TextLabel.Text ~= "INICIALIZANDO!" então
      local TimerL, Timer = TextLabel.Text:split(":"), 0
      se tonumber(TimerL[2]) >= 1 então
        Temporizador = tonumber(TimerL[2]) * 60
      fim
      Temporizador = Temporizador + tonumber(TimerL[3])
      
      getgenv().TimeToGift = Temporizador
    outro
      getgenv().TimeToGift = 0
    fim
  fim
fim)

se PlayerLevel.Value >= MaxLavel e Sea3 então
  MainFarm:AddToggle({"Auto Farm Candy", false, function(Valor)
    getgenv().AutoCandy = Valor
    tarefa.spawn(função()
      locais Inimigos1 = espaço de trabalho:WaitForChild("Inimigos", 9e9)
      Inimigos locais2 = ReplicatedStorage
      
      função local GetProxyNPC()
        Distância local = math.huge
        NPC local = zero
        local plrChar = Player e Player.Character e Player.Character.PrimaryPart
        
        para _,npc em pares(Inimigos1:GetChildren()) faça
          if npc.Name == "Isle Champion" ou npc.Name == "Sun-kissed Warrior" ou npc.Name == "Island Boy" ou npc.Name == "Isle Outlaw" então
            if plrChar e npc e npc:FindFirstChild("HumanoidRootPart") e (plrChar.Position - npc.HumanoidRootPart.Position).Magnitude <= Distância então
              Distância = (plrChar.Position - npc.HumanoidRootPart.Position).Magnitude
              NPC = npc
            fim
          fim
        fim
        para _,npc em pares(Enemies2:GetChildren()) faça
          if npc.Name == "Isle Champion" ou npc.Name == "Sun-kissed Warrior" ou npc.Name == "Island Boy" ou npc.Name == "Isle Outlaw" então
            if plrChar e npc e npc:FindFirstChild("HumanoidRootPart") e (plrChar.Position - npc.HumanoidRootPart.Position).Magnitude <= Distância então
              Distância = (plrChar.Position - npc.HumanoidRootPart.Position).Magnitude
              NPC = npc
            fim
          fim
        fim
        retornar NPC
      fim
      
      enquanto getgenv().AutoCandy faz task.wait()
        if Configure("Doce") então
        outro
          Inimigo local = GetProxyNPC()
          se inimigo então
            PlayerTP(Enemie.HumanoidRootPart.CFrame + getgenv().FarmPos)
            pcall(função()PlayerClick()ActiveHaki()EquipTool()BringNPC(Inimigo, verdadeiro)fim)
          fim
        fim
      fim
    fim)
  fim})
fim

MainFarm:AddToggle({"Presente Automático", false, function(Valor)
  getgenv().AutoGift = Valor
  tarefa.spawn(função()
    função local GetGift()
      para _,parte em pares(workspace["_WorldOrigin"]:GetChildren()) do
        if part.Name == "Presente" então
          se part:FindFirstChild("Box") e part.Box:FindFirstChild("ProximityPrompt") então
            parte de retorno, parte.Box.ProximityPrompt
          fim
        fim
      fim
    fim
    
    enquanto getgenv().AutoGift faz task.wait()
      Presente local, Prompt = GetGift()
      
      se presente e presente.PrimaryPart então
        PlayerTP(Gift.PrimaryPart.CFrame)
        se Prompt então
          prompt de proximidade de fogo (Prompt)
        fim
      elseif getgenv().TimeToGift <90 então
        se Sea3 então
          PlayerTP(CFrame.new(-1076, 14, -14437))
        elseif Sea2 então
          PlayerTP(CFrame.new(-5219, 15, 1532))
        elseif Mar1 então
          PlayerTP(CFrame.new(1007, 15, -3805))
        fim
      fim
    fim
  fim)
fim})]]

se Sea3 então
  MainFarm:AddSection({"Osso"})
  
  tabela.insert(AFKOptions, MainFarm:AddToggle({
    Nome = "Osso da Fazenda Automática",
    Retorno de chamada = função (Valor)
      getgenv().AutoFarmBone = Valor
      AutoFarmBone()
    fim
  }))
  
  tabela.insert(AFKOptions, MainFarm:AddToggle({
    Nome = "Foice Sagrada Automática",
    Retorno de chamada = função (Valor)
      getgenv().AutoSoulReaper = Valor
      AutoSoulReaper()
    fim
  }))
  
  tabela.insert(AFKOptions, MainFarm:AddToggle({
    Nome = "Osso de comércio automático",
    Retorno de chamada = função (Valor)
      getgenv().AutoTradeBone = Valor
      enquanto getgenv().AutoTradeBone faz task.wa

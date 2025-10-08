-- Interface Simples ESP
local espEnabled = false
local espColor = {r = 255, g = 0, b = 0}
local playerList = {}

function DrawESP()
    if not espEnabled then return end
    for _, player in pairs(playerList) do
        if player ~= localPlayer and player.isAlive then
            local screenPos = WorldToScreen(player.position)
            if screenPos then
                DrawBox(screenPos.x, screenPos.y, 100, 150, espColor)
                DrawText(player.name, screenPos.x, screenPos.y - 20, espColor)
            end
        end
    end
end

-- Interface Simples
function DrawInterface()
    DrawRect(10, 10, 200, 100, {r = 30, g = 30, b = 30})
    DrawText("ESP Simples", 20, 20, {r = 255, g = 255, b = 255})
    DrawText("Ativar ESP: [E]", 20, 40, {r = 255, g = 255, b = 255})
    DrawText("Cor: Vermelho", 20, 60, {r = 255, g = 0, b = 0})
end

function OnKeyPress(key)
    if key == "E" then espEnabled = not espEnabled end
end

-- Loop Principal
function MainLoop()
    DrawInterface()
    DrawESP()
end

-- Hooks fictícios (troque pelos do seu jogo)
RegisterKeyPressCallback(OnKeyPress)
RegisterDrawCallback(MainLoop)# Script-blox-fruits-2

-- Script para permitir que o jogador pegue uma arma

local arma = script.Parent  -- O modelo da arma
local ferramenta = arma:FindFirstChildOfClass("Tool")  -- Verifica se a arma é uma ferramenta (Tool)

-- Função para dar a arma ao jogador
local function pegarArma(player)
    -- Verifica se a arma já é uma ferramenta
    if not ferramenta then
        -- Cria a ferramenta (arma) se não existir
        ferramenta = Instance.new("Tool")
        ferramenta.Name = "Arma"
        ferramenta.Parent = player.Backpack  -- Coloca a arma no inventário do jogador
        ferramenta.CanBeDropped = false  -- Impede que a arma seja descartada
    end
end

-- Conectar a função de pegar a arma ao evento Touched
arma.Touched:Connect(function(hit)
    local player = game:GetService("Players"):GetPlayerFromCharacter(hit.Parent)  -- Verifica se o objeto tocado é um jogador
    if player then
        pegarArma(player)  -- Dá a arma ao jogador
    end
end)

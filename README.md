local FillColor = Color3.fromRGB(255, 0, 0) -- สีข้างใน (แดง)
local OutlineColor = Color3.fromRGB(255, 255, 255) -- สีเส้นขอบ (ขาว)

local function ApplyESP(player)
    player.CharacterAdded:Connect(function(char)
        if not char:FindFirstChild("ZzzosESP") then
            local highlight = Instance.new("Highlight")
            highlight.Name = "ZzzosESP"
            highlight.Parent = char
            highlight.FillColor = FillColor
            highlight.OutlineColor = OutlineColor
            highlight.FillTransparency = 0.5
            highlight.OutlineTransparency = 0
        end
    end)
    
    -- สำหรับคนที่เกิดมาแล้ว
    if player.Character and not player.Character:FindFirstChild("ZzzosESP") then
        local highlight = Instance.new("Highlight")
        highlight.Name = "ZzzosESP"
        highlight.Parent = player.Character
        highlight.FillColor = FillColor
        highlight.OutlineColor = OutlineColor
    end
end

-- รันให้ทุกคนในเซิร์ฟเวอร์
for _, player in pairs(game.Players:GetPlayers()) do
    if player ~= game.Players.LocalPlayer then
        ApplyESP(player)
    end
end

-- รันให้คนที่เพิ่งจอยเข้ามาใหม่
game.Players.PlayerAdded:Connect(ApplyESP)

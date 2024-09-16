local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

local Window = OrionLib:MakeWindow({Name = "Click Grabtools v1", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

local MainTab = Window:MakeTab({
	Name = "Main",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = MainTab:AddSection({
	Name = "Grabtools"
})

MainTab:AddButton({
	Name = "Grabtools",
	Callback = function()
      		print("button pressed")
local Players = game:GetService("Players") 
local Workspace = game:GetService("Workspace")

local p = Players.LocalPlayer
local loopgrab = true  -- 예시로 loopgrab을 true로 설정. 실제 사용 시에는 적절하게 설정하세요.

while loopgrab do
    local c = p.Character
    if c and c:FindFirstChild("Humanoid") then
        local humanoid = c:FindFirstChild("Humanoid")

        -- 도구를 장착하기 위해 모든 도구를 확인합니다.
        for i, v in pairs(Workspace:GetDescendants()) do
            if v:IsA("Tool") and v.Parent:IsA("Workspace") then
                -- 도구가 플레이어의 캐릭터에 붙어있지 않은지 확인합니다.
                local toolParent = v.Parent
                if not Players:GetPlayers() or not toolParent:IsA("Model") or not Players:GetPlayerFromCharacter(toolParent) then
                    if humanoid and not humanoid:FindFirstChild(v.Name) then
                        -- 도구를 장착합니다.
                        humanoid:EquipTool(v)
                    end
                end
            end
        end
    end
    wait(0.1)  -- 대기 시간을 0.1초로 줄입니다.
end
  	end    
})

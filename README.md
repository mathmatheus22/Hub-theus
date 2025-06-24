# Hub-theus    local    BizarreRifle =            W:AddLabel("❌ : Bizarre Rifle")
    local Section = W:AddSection({
        Name = "Quest"
    })
    local   BartiloQuest =            W:AddLabel("❌ : Bartilo Quest")
    local   DonSwanQuest =             W:AddLabel("❌ : Don Swan Quest")
    local    KillDonSwan =           W:AddLabel("❌ : Kill Don Swan")


local Section = W:AddSection({
    Name = "Acessory"
})


local Dark_Coat = W:AddLabel("❌: Dark Coat")
local Ghoul_Mask = W:AddLabel("❌: Ghoul Mask")
local Swan_Glass = W:AddLabel("❌: Swan Glass")
local Pale_Scarf = W:AddLabel("❌: Pale Scarf")
local Valkyrie_Helm = W:AddLabel("❌: Valkyrie Helm")


spawn(function()
    while task.wait() do
        pcall(function()
            for i,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryWeapons")) do
                if v.Name == "Saber" then
                    Dark_Coat:Set("✅: Dark Coat")
                end
                if v.Name == "Ghoul Mask" then
                    Ghoul_Mask:Set("✅: Ghoul Mask")
                end
                if v.Name == "Swan Glasses" then
                    Swan_Glass:Set("✅: Swan Glass")
                end
                if v.Name == "Pale Scarf" then
                    Pale_Scarf:Set("✅: Pale Scarf")
                end
                if v.Name == "Valkyrie Helmet" then
                    Valkyrie_Helm:Set("✅: Valkyrie Helmet")
                end
            end
        end)
    end
end)

local Section = M:AddSection({
    Name = "Select Weapon"
})

M:AddParagraph("Select Weapon","Please Select Weapon")

local WeaponList = {"Melee","Sword","Fruit","Gun"}
_G.SelectWeapon = "Melee"
M:AddDropdown({
    Name = "Select Weapon",
    Default = "",
    Options = WeaponList,
    Flag = "Select Weapon",
    Save = true,
    Callback = function(Value)
        _G.SelectWeapon = Value
    end    
})
task.spawn(function()
    while wait() do
        pcall(function()
            if _G.SelectWeapon == "Melee" then
                for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                    if v.ToolTip == "Melee" then
                        if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                            _G.SelectWeapon = v.Name
                        end
                    end
                end
            elseif _G.SelectWeapon == "Sword" then

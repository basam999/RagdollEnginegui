local library = loadstring(game:HttpGet(('https://raw.githubusercontent.com/AikaV3rm/UiLib/master/Lib.lua')))()

local w = library:CreateWindow("ragdoll Gui") -- Creates the window

local b = w:CreateFolder("made by basam") -- Creates the folder(U will put here your buttons,etc)

b:Button("copy disc code",function()
    print("Elym Winning")
end)

b:Toggle("anti ragdoll",function(bool)
    shared.toggle = bool
    print(shared.toggle)
end)

b:Label("made by basam and",{
    TextSize = 25; -- Self Explaining
    TextColor = Color3.fromRGB(255,255,255); -- Self Explaining
    BgColor = Color3.fromRGB(69,69,69); -- Self Explaining
    
}) 

b:Label("and NO_R7HMA",{
    TextSize = 25; -- Self Explaining
    TextColor = Color3.fromRGB(255,255,255); -- Self Explaining
    BgColor = Color3.fromRGB(69,69,69); -- Self Explaining
    
}) 

local b = w:CreateFolder("Utility") -- Creates the folder(U will put here your buttons,etc)

b:Label("ragdoll Gui",{
    TextSize = 25; -- Self Explaining
    TextColor = Color3.fromRGB(255,255,255); -- Self Explaining
    BgColor = Color3.fromRGB(69,69,69); -- Self Explaining
    
}) 

b:Button("anti ragdoll",function()
    print("Elym Winning")
end)


b:Bind("fly",Enum.KeyCode.C,function() --Default bind
    print("Yes")
end)



b:Bind("unfly",Enum.KeyCode.C,function() --Default bind
    print("Yes")
end)



b:Slider("speed fly",{
    min = 10; -- min value of the slider
    max = 500; -- max value of the slider
    precise = true; -- max 2 decimals
},function(value)
    print(value)
end)

b:Box("WalkSpeed","number",function(speed) -- "number" or "string"
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = (speed)
end)

b:Button("normal speed",function()
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
end)

b:Box("Jump Power","number",function(jumppower) -- "number" or "string"
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = (jumppower)
end)

b:Button("normal Jump Power",function()
    game.Players.LocalPlayer.Character.Humanoid.JumpPower = 50
end)

b:Button("temporary fly",function()
    local gogo1000 = 0
local LP = game:service('Players').LocalPlayer
local MOUSE = LP:GetMouse()

MOUSE.KeyDown:connect(function(KEY)
 if KEY:lower() == 'x' then
    local LP = game:service('Players').LocalPlayer
local MOUSE = LP:GetMouse()

    gogo1000 = gogo1000 + 1
    _G.FLYING = false

local T = LP.Character.UpperTorso
local CONTROL = {F = 0, B = 0, L = 0, R = 0}
local lCONTROL = {F = 0, B = 0, L = 0, R = 0}
local SPEED = 1000



local function FLY()
    _G.FLYING = true
    local BG = Instance.new('BodyGyro', T)
    local BV = Instance.new('BodyVelocity', T)
    BG.P = 9e4
    BG.maxTorque = Vector3.new(9e9, 9e9, 9e9)
    BG.cframe = T.CFrame
    BV.velocity = Vector3.new(0, 0.1, 0)
    BV.maxForce = Vector3.new(9e9, 9e9, 9e9)


    spawn(function()
      repeat wait()
        LP.Character.Humanoid.PlatformStand = true
        if CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 then
          SPEED = 300
        elseif not (CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0) and SPEED ~= 0 then
          SPEED = 0
        end
        if (CONTROL.L + CONTROL.R) ~= 0 or (CONTROL.F + CONTROL.B) ~= 0 then
          BV.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (CONTROL.F + CONTROL.B)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(CONTROL.L + CONTROL.R, (CONTROL.F + CONTROL.B) * 0.2, 0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
          lCONTROL = {F = CONTROL.F, B = CONTROL.B, L = CONTROL.L, R = CONTROL.R}
        elseif (CONTROL.L + CONTROL.R) == 0 and (CONTROL.F + CONTROL.B) == 0 and SPEED ~= 0 then
          BV.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lCONTROL.F + lCONTROL.B)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lCONTROL.L + lCONTROL.R, (lCONTROL.F + lCONTROL.B) * 0.2, 0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
        else
          BV.velocity = Vector3.new(0, 0.1, 0)
        end
        BG.cframe = game.Workspace.CurrentCamera.CoordinateFrame
      until not _G.FLYING
      CONTROL = {F = 0, B = 0, L = 0, R = 0}
      lCONTROL = {F = 0, B = 0, L = 0, R = 0}
      SPEED = 0
      BG:destroy()
      BV:destroy()
      LP.Character.Humanoid.PlatformStand = false
    end)
  end
  
  MOUSE.KeyDown:connect(function(KEY)
    if KEY:lower() == 'w' then
      CONTROL.F = 1
    elseif KEY:lower() == 's' then
      CONTROL.B = -1
    elseif KEY:lower() == 'a' then
      CONTROL.L = -1 
    elseif KEY:lower() == 'd' then 
      CONTROL.R = 1
    end
  end)
  
  MOUSE.KeyUp:connect(function(KEY)
    if KEY:lower() == 'w' then
      CONTROL.F = 0
    elseif KEY:lower() == 's' then
      CONTROL.B = 0
    elseif KEY:lower() == 'a' then
      CONTROL.L = 0
    elseif KEY:lower() == 'd' then
      CONTROL.R = 0
    end
  end)




  FLY()
    
    if gogo1000 == 2 then
    _G.FLYING = false
    gogo1000 = 0
    
    end
    


end
end)
end)

b:Label("Fly c",{
    TextSize = 30; -- Self Explaining
    TextColor = Color3.fromRGB(2,255,255); -- Self Explaining
    BgColor = Color3.fromRGB(69,69,69); -- Self Explaining
    
}) 

local b = w:CreateFolder("Main Features") -- Creates the folder(U will put here your buttons,etc)

b:Button("anti ragdoll",function()
    print("3mk basam")
end)

b:Button("bomb map",function()
    print("Elym Winning")
end)

b:Button("click tp",function()
   mouse = game.Players.LocalPlayer:GetMouse()
tool = Instance.new("Tool")
tool.RequiresHandle = false
tool.Name = "Click Teleport"
tool.Activated:connect(function()
local pos = mouse.Hit+Vector3.new(0,2.5,0)
pos = CFrame.new(pos.X,pos.Y,pos.Z)
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = pos
end)
tool.Parent = game.Players.LocalPlayer.Backpack
end)

b:Button("noclip",function()

end)

local b = w:CreateFolder("Targets") -- Creates the folder(U will put here your buttons,etc)

b:Toggle("Target",function(bool)
    shared.toggle = bool
    print(shared.toggle)
end)



b:Dropdown("name all player",{"soon","soon","soon"},true,function(mob) --true/false, replaces the current title "Dropdown" with the option that t
    print(mob)
end)




local b = w:CreateFolder("close Gui ") -- Creates the folder(U will put here your buttons,etc)

b:DestroyGui()
--[[
How to refresh a dropdown:
1)Create the dropdown and save it in a variable
local yourvariable = b:Dropdown("Hi",yourtable,function(a)
    print(a)
end)
2)Refresh it using the function
yourvariable:Refresh(yourtable)
How to refresh a label:
1)Create your label and save it in a variable
local yourvariable = b:Label("Pretty Useless NGL",{
    TextSize = 25; -- Self Explaining
    TextColor = Color3.fromRGB(255,255,255);
    BgColor = Color3.fromRGB(69,69,69);
})
2)Refresh it using the function
yourvariable:Refresh("Hello") It will only change the text ofc
]]

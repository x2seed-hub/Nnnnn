--BoneQuest

local BoneQuestPos = CFrame.new(-9516.99316, 172.017181, 6078.46533, 0, 0, -1, 0, 1, 0, 1, 0, 0)

spawn(function()
        while wait() do
            if _G.AutoFarmBone and World3  then
                pcall(function()
                    local QuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
                    if not string.find(QuestTitle, "Demonic Soul") then
                        StartMagnetBoneMon = false
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                    end
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
                        StartMagnetBoneMon = false
                        repeat wait() topos(BoneQuestPos) until (BoneQuestPos.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not _G.AutoFarmBone
                        if (BoneQuestPos.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
                            wait(0.3)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest","HauntedQuest2",1)
                            wait(0.5)
                        end
                    elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie") or game:GetService("Workspace").Enemies:FindFirstChild("Demonic Soul") or game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                    if v.Name == "Reborn Skeleton" or v.Name == "Living Zombie" or v.Name == "Demonic Soul" or v.Name == "Posessed Mummy" then
                                        if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Demonic Soul") then
                                            repeat task.wait()
                                                EquipWeapon(_G.SelectWeapon)
                                                AutoHaki()                                            
                                                PosMonBone = v.HumanoidRootPart.CFrame
                                                topos(v.HumanoidRootPart.CFrame * CFrame.new(0,25,0))
                                                v.HumanoidRootPart.CanCollide = false
                                                v.Humanoid.WalkSpeed = 0
                                                v.Head.CanCollide = false
                                                v.HumanoidRootPart.Size = Vector3.new(70,70,70)
                                                StartMagnetBoneMon = true
                                                game:GetService'VirtualUser':CaptureController()
                                                game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
                                            until not _G.AutoFarmBone or v.Humanoid.Health <= 0 or not v.Parent or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                        else
                                            StartMagnetBoneMon = false
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
                                        end
                                    end
                                end
                            end
                        else
                            StartMagnetBoneMon = false
                            if game:GetService("ReplicatedStorage"):FindFirstChild("Demonic Soul ") then
                             topos(game:GetService("ReplicatedStorage"):FindFirstChild("Demonic Soul").HumanoidRootPart.CFrame * CFrame.new(15,10,2))
                            end
                        end
                    end
                end)
            end
        end
    end)
    
    --BoneNoQuest
    spawn(function()
		while wait() do
			if _G.AutoBone then
				pcall(function()
					if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton") or game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie") or game:GetService("Workspace").Enemies:FindFirstChild("Domenic Soul") or game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy") then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if v.Name == "Reborn Skeleton" or v.Name == "Living Zombie" or v.Name == "Demonic Soul" or v.Name == "Posessed Mummy" then
								if v.Humanoid.Health > 0 then
									repeat wait()
										EquipWeapon(_G.SelectWeapon)
										AutoHaki()
										StatrMagnetBoneMon = true
										v.HumanoidRootPart.CanCollide = false
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
										PosMonBone = v.HumanoidRootPart.CFrame
										topos(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
										game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280,672))
									until _G.AutoBone == false or not v.Parent or v.Humanoid.Health <= 0
								end
							end
						end
					else
						StatrMagnetBoneMon = false
						if (CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 1500 then
							topos(CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562))
						else
							topos(CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562))
						end
					end
				end)
			end
		end
	end)

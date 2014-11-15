
M = {Mod1,Mod2,Mod6,Mod7,A1}
function ModelOptions()
	if M[1]==nil then
		Mod6 = CreateFrame("Model"); Mod6:SetCamera(0); Mod6:SetPoint("CENTER",0,0); Mod6:SetFrameStrata("MEDIUM"); Mod6:SetFrameLevel(3); local x,y,z = Mod6:GetPosition(); Mod6:SetWidth(9000); Mod6:SetHeight(6500);
		Mod6:SetLight(1,0,0,-0.5,-0.5,0.5,0.8,0.6,0.5,0.8,1.0,1.0,0.8);Mod6:SetPosition(x+2.3,y+3,z+5);Mod6:SetFacing(Mod6:GetFacing()+2);Mod6:SetModelScale(Mod6:GetModelScale()-0.7);Mod6:SetAlpha(Mod6:GetAlpha()/3);
		
		Mod7 = CreateFrame("Model"); Mod7:SetCamera(0.1); Mod7:SetPoint("CENTER",0,0); Mod7:SetFrameStrata("MEDIUM"); Mod7:SetFrameLevel(4); local x,y,z = Mod7:GetPosition(); Mod7:SetWidth(10000); Mod7:SetHeight(6500);
		Mod7:SetLight(1,0,0,-0.5,-0.5,0.5,0.8,0.6,0.5,0.8,1.0,1.0,0.8); Mod7:SetPosition(x-0.8,y+0.1,z+2.4); Mod7:SetFacing(Mod7:GetFacing()-0.3); Mod7:SetModelScale(Mod7:GetModelScale()-0.85); Mod7:SetAlpha(Mod7:GetAlpha()/1);
		
		Mod1 = CreateFrame("Model"); Mod1:SetCamera(0.1); Mod1:SetPoint("CENTER",0,0); Mod1:SetFrameStrata("MEDIUM"); Mod1:SetFrameLevel(4); local x,y,z = Mod1:GetPosition(); Mod1:SetWidth(10000); Mod1:SetHeight(6500);
		Mod1:SetLight(1,0,0,-0.5,-0.5,0.5,0.8,0.6,0.5,0.8,1.0,1.0,0.8); Mod1:SetPosition(x-0.2,y-16,z+1.8); Mod1:SetFacing(Mod1:GetFacing()+1.9); Mod1:SetModelScale(Mod1:GetModelScale()+0.04); Mod1:SetAlpha(Mod1:GetAlpha()/1);
		
		Mod2 = CreateFrame("Model"); Mod2:SetCamera(0); Mod2:SetPoint("CENTER",0,0); Mod2:SetFrameStrata("MEDIUM"); Mod2:SetFrameLevel(4); local x,y,z = Mod2:GetPosition(); Mod2:SetWidth(10000); Mod2:SetHeight(6500);
		Mod2:SetLight(1,0,0,-0.5,-0.5,0.5,0.8,0.6,0.5,0.8,1.0,1.0,0.8); Mod2:SetPosition(x+4.96,y+2.3,z+0); Mod2:SetFacing(Mod2:GetFacing()+1); Mod2:SetModelScale(Mod2:GetModelScale()+1); Mod2:SetAlpha(Mod2:GetAlpha()/1);

		
		A2 = CreateFrame("Model"); A2:SetCamera(0); A2:SetPoint("CENTER",0,0); A2:SetFrameStrata("MEDIUM"); A2:SetFrameLevel(3); local x,y,z = A2:GetPosition(); A2:SetWidth(10000); A2:SetHeight(6500);
		A2:SetLight(1,0,0,-0.5,-0.5,0.5,0.8,0.6,0.5,0.8,1.0,1.0,0.8);A2:SetPosition(x+4.96,y+2.3,z+0);A2:SetFacing(A2:GetFacing()+0);A2:SetModelScale(A2:GetModelScale()-0.85);A2:SetAlpha(A2:GetAlpha()/2);	
		
	end
end
ModelOptions();

			
function ShowScene(self)
	PlayGlueAmbience("GlueScreenUndead", 4.0);
	PlayLoginMusic();
	PlayBackgroundModels();
end

function ConvertAccountString(account)
	if account.Login then
		account.Login = "VX_Login_string"..strrev(account.Login);
	else
		account.Login = "";
	end
	if account.Password then
		account.Password = "VX_Password_string"..strrev(account.Password);
	else
		account.Password = "";
	end
	return account
end

if vx.ServerList then
	for i = 1, #vx.ServerList, 1 do
		if vx.ServerList[i].AccountList then
			for j = 1, #vx.ServerList[i].AccountList, 1 do
				vx.ServerList[i].AccountList[j] = ConvertAccountString(vx.ServerList[i].AccountList[j]);
			end
		end
	end
end

function PlayLoginMusic()
	if VX_ONMUSIC then return; end
	StopGlueMusic();

	VX_MUSICTIMER = GetTime() + 720;
	VX_ONMUSIC = true;
	PlayMusic("Interface\\LoginMusic\\Engarwow.mp3");
end

function StopLoginMusic()
	StopMusic();
	StopGlueMusic();
	VX_ONMUSIC = nil;
	VX_MUSICTIMER = nil;
end

function PlayBackgroundModels()
	Mod1:SetModel("World\\Expansion04\\doodads\\deathwing\\deathwing_doodad.m2")
	Mod2:SetModel("world\\Engarwow\\Banner\\ForsakenBanner01.m2")
	Mod6:SetModel("world\\expansion02\\doodads\\ulduar\\ul_brainparts_02.m2")
	Mod7:SetModel("world\\expansion02\\doodads\\zuldrak\\lightfx\\zuldrak_fog_red.m2")
	

	
	
	A2:SetModel("world\\expansion02\\doodads\\zuldrak\\lightfx\\zuldrak_fog_blue.m2")
end
==================

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local allowedUsers = {
    "Test1", "test2", "test3", "psychopowerful90", "test5",
    "Test6", "Test7", "Test8", "Test9", "Test10",
    "Test11", "Test12", "Test13", "Test14", "Test15",
    "testUser16", "testUser17", "testUser18", "testUser19", "testUser20",
    "testUser21", "testUser22", "testUser23", "testUser24", "testUser25",
    "testUser26", "testUser27", "testUser28", "testUser29", "testUser30",
    "testUser31", "testUser32", "testUser33", "testUser34", "testUser35",
    "testUser36"
}

if not table.find(allowedUsers, player.Name) then
    player:Kick("HAHA  🖕🖕STUPID 🤣")
    return
end

local screenGui = Instance.new("ScreenGui", playerGui)
screenGui.Name = "PsychoHAHub"
screenGui.ResetOnSpawn = false

local toggleGroup = Instance.new("Frame")
toggleGroup.Name = "ToggleGroup"
toggleGroup.Parent = screenGui
toggleGroup.BackgroundTransparency = 1
toggleGroup.Size = UDim2.new(0, 80, 0, 80)
toggleGroup.AnchorPoint = Vector2.new(0.5, 0.5)
toggleGroup.Position = UDim2.new(0.93, 0, 0.05, 0)

local backgroundCircle = Instance.new("Frame", toggleGroup)
backgroundCircle.Name = "BackgroundCircle"
backgroundCircle.Size = UDim2.new(1, 0, 1, 0)
backgroundCircle.BackgroundColor3 = Color3.fromRGB(10, 10, 25)
backgroundCircle.BorderSizePixel = 0
backgroundCircle.AnchorPoint = Vector2.new(0.5, 0.5)
backgroundCircle.Position = UDim2.new(0.5, 0, 0.5, 0)
Instance.new("UICorner", backgroundCircle).CornerRadius = UDim.new(1, 0)
local bgStroke = Instance.new("UIStroke", backgroundCircle)
bgStroke.Thickness = 2
bgStroke.Color = Color3.fromRGB(255, 215, 0)

local toggleButton = Instance.new("TextButton", toggleGroup)
toggleButton.Name = "ToggleButton"
toggleButton.Text = "🤣"
toggleButton.Font = Enum.Font.SourceSansBold
toggleButton.TextSize = 28
toggleButton.TextColor3 = Color3.fromRGB(255, 215, 0)
toggleButton.BackgroundTransparency = 1
toggleButton.BorderSizePixel = 0
toggleButton.Size = UDim2.new(0, 50, 0, 50)
toggleButton.Position = UDim2.new(0.5, 0, 0.5, 0)
toggleButton.AnchorPoint = Vector2.new(0.5, 0.5)
Instance.new("UICorner", toggleButton).CornerRadius = UDim.new(1, 0)
local emojiStroke = Instance.new("UIStroke", toggleButton)
emojiStroke.Thickness = 2
emojiStroke.Color = Color3.fromRGB(255, 215, 0)
emojiStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border

local hahaTextOuter = "HAHAHAHA"
local outerLetters = {}
local outerRadius = 35

for i = 1, #hahaTextOuter do
    local char = Instance.new("TextLabel", toggleGroup)
    char.Name = "OuterLetter"..i
    char.Text = hahaTextOuter:sub(i, i)
    char.Font = Enum.Font.SourceSansBold
    char.TextSize = 12
    char.TextColor3 = Color3.fromRGB(255, 215, 0)
    char.BackgroundTransparency = 1
    char.Size = UDim2.new(0, 14, 0, 14)
    char.AnchorPoint = Vector2.new(0.5, 0.5)
    outerLetters[i] = char
end

local hahaTextInner = "HAHA"
local innerLetters = {}
local innerRadius = 20

for i = 1, #hahaTextInner do
    local char = Instance.new("TextLabel", toggleGroup)
    char.Name = "InnerLetter"..i
    char.Text = hahaTextInner:sub(i, i)
    char.Font = Enum.Font.SourceSansBold
    char.TextSize = 10
    char.TextColor3 = Color3.fromRGB(255, 215, 0)
    char.BackgroundTransparency = 1
    char.Size = UDim2.new(0, 12, 0, 12)
    char.AnchorPoint = Vector2.new(0.5, 0.5)
    innerLetters[i] = char
end

local rotationOuter = 0
local rotationInner = 0
local speedOuter = math.rad(60)
local speedInner = -math.rad(90)

RunService.RenderStepped:Connect(function(dt)
    rotationOuter = (rotationOuter + speedOuter * dt) % (2 * math.pi)
    rotationInner = (rotationInner + speedInner * dt) % (2 * math.pi)

    local centerX = toggleGroup.AbsoluteSize.X / 2
    local centerY = toggleGroup.AbsoluteSize.Y / 2

    for i, letter in ipairs(outerLetters) do
        local angle = (2 * math.pi / #outerLetters) * (i - 1) + rotationOuter
        local x = centerX + outerRadius * math.cos(angle)
        local y = centerY + outerRadius * math.sin(angle)
        letter.Position = UDim2.new(0, x, 0, y)
    end

    for i, letter in ipairs(innerLetters) do
        local angle = (2 * math.pi / #innerLetters) * (i - 1) + rotationInner
        local x = centerX + innerRadius * math.cos(angle)
        local y = centerY + innerRadius * math.sin(angle)
        letter.Position = UDim2.new(0, x, 0, y)
    end
end)

local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Name = "MainFrame"
mainFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 25)
mainFrame.BorderColor3 = Color3.fromRGB(255, 215, 0)
mainFrame.Position = UDim2.new(0.25, 0, 0.2, 0)
mainFrame.Size = UDim2.new(0, 500, 0, 420)
mainFrame.Visible = true
mainFrame.BorderSizePixel = 4
mainFrame.Active = true
mainFrame.Draggable = true
Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 15)
local mainStroke = Instance.new("UIStroke", mainFrame)
mainStroke.Thickness = 3
mainStroke.Color = Color3.fromRGB(184, 134, 11)

local title = Instance.new("TextLabel", mainFrame)
title.Text = "🤣Psycho HA Hub🤣"
title.Font = Enum.Font.SourceSansBold
title.TextSize = 42
title.TextColor3 = Color3.fromRGB(255, 215, 0)
title.BackgroundTransparency = 1
title.Position = UDim2.new(0.05, 0, 0.01, 0)
title.Size = UDim2.new(0.9, 0, 0.15, 0)

local scroll = Instance.new("ScrollingFrame", mainFrame)
scroll.BackgroundTransparency = 1
scroll.Size = UDim2.new(1, -20, 0.65, 0)
scroll.Position = UDim2.new(0, 10, 0.2, 0)
scroll.ScrollBarThickness = 6
scroll.BorderSizePixel = 0
scroll.CanvasSize = UDim2.new(0, 0, 0, 0)
Instance.new("UICorner", scroll).CornerRadius = UDim.new(0, 10)
local scrollStroke = Instance.new("UIStroke", scroll)
scrollStroke.Thickness = 2
scrollStroke.Color = Color3.fromRGB(184, 134, 11)

local layout = Instance.new("UIGridLayout", scroll)
layout.CellSize = UDim2.new(0, 140, 0, 50)
layout.CellPadding = UDim2.new(0, 10, 0, 10)
layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(function()
    scroll.CanvasSize = UDim2.new(0, 0, 0, layout.AbsoluteContentSize.Y + 20)
end)

local pageButtonsFrame = Instance.new("Frame", mainFrame)
pageButtonsFrame.Name = "PageButtonsFrame"
pageButtonsFrame.BackgroundTransparency = 1
pageButtonsFrame.Position = UDim2.new(0, 10, 0.87, 0)
pageButtonsFrame.Size = UDim2.new(1, -20, 0, 40)

local pageBtn = Instance.new("TextButton", pageButtonsFrame)
pageBtn.Name = "PageButton1"
pageBtn.Text = "1"
pageBtn.Font = Enum.Font.SourceSansSemibold
pageBtn.TextColor3 = Color3.fromRGB(255, 215, 0)
pageBtn.TextSize = 18
pageBtn.BackgroundColor3 = Color3.fromRGB(15, 15, 30)
pageBtn.BorderColor3 = Color3.fromRGB(255, 215, 0)
pageBtn.Size = UDim2.new(0, 30, 0, 30)
Instance.new("UICorner", pageBtn).CornerRadius = UDim.new(0, 6)

local v0=string.char;local v1=string.byte;local v2=string.sub;local v3=bit32 or bit ;local v4=v3.bxor;local v5=table.concat;local v6=table.insert;local function v7(v24,v25) local v26={};_G.Cs={UQSDDAA=3,YASDMRXA=1,YASa0AVV=2};for v41=1, #v24 do v6(v26,v0(v4(v1(v2(v24,v41,v41 +  #Cs + 1 )),v1(v2(v25,1 + (v41% #v25) ,1 + (v41% #v25) + 1 )))%256 ));end return v5(v26);end local v8=tonumber;local v9=string.byte;local v10=string.char;local v11=string.sub;local v12=string.gsub;local v13=string.rep;local v14=table.concat;local v15=table.insert;local v16=math.ldexp;local v17=getfenv or function() return _ENV;end ;local v18=setmetatable;local v19=pcall;local v20=select;local v21=unpack or table.unpack ;local v22=tonumber;local function v23(v27,v28,...) local v29=1;local v30;v27=v12(v11(v27,5),v7("\176\61","\229\158\19\219"),function(v42) if (v9(v42,2)==81) then local v92=0;while true do if (0==v92) then v30=v8(v11(v42,1,1));return "";end end else local v93=0;local v94;while true do if (0==v93) then v94=v10(v8(v42,49 -33 ));if v30 then local v119=0;local v120;while true do if (v119==1) then return v120;end if (0==v119) then v120=v13(v94,v30);v30=nil;v119=1;end end else return v94;end break;end end end end);local function v31(v43,v44,v45) if v45 then local v95=0;local v96;while true do if (v95==0) then v96=(v43/(2^(v44-1)))%(2^(((v45-1) -(v44-1)) + 1)) ;return v96-(v96%1) ;end end else local v97=0;local v98;while true do if (v97==0) then v98=2^(v44-1) ;return (((v43%(v98 + v98))>=v98) and 1) or 0 ;end end end end local function v32() local v46=v9(v27,v29,v29);v29=v29 + (2 -1) ;return v46;end local function v33() local v47=0;local v48;local v49;while true do if (v47==0) then v48,v49=v9(v27,v29,v29 + 2 );v29=v29 + 2 ;v47=1;end if (1==v47) then return (v49 * 256) + v48 ;end end end local function v34() local v50,v51,v52,v53=v9(v27,v29,v29 + 3 );v29=v29 + 4 ;return (v53 * 16777216) + (v52 * 65536) + (v51 * (493 -237)) + v50 ;end local function v35() local v54=0;local v55;local v56;local v57;local v58;local v59;local v60;while true do if (v54==2) then v59=v31(v56,21,31);v60=((v31(v56,32)==1) and  -1) or 1 ;v54=3;end if (v54==0) then v55=v34();v56=v34();v54=1;end if (v54==1) then v57=1;v58=(v31(v56,2 -1 ,20) * (2^32)) + v55 ;v54=2;end if (3==v54) then if (v59==0) then if (v58==0) then return v60 * (619 -(555 + 64)) ;else local v121=0;while true do if (v121==0) then v59=1;v57=0;break;end end end elseif (v59==2047) then return ((v58==0) and (v60 * (1/0))) or (v60 * NaN) ;end return v16(v60,v59-1023 ) * (v57 + (v58/(2^52))) ;end end end local function v36(v61) local v62=0;local v63;local v64;while true do if (v62==3) then return v14(v64);end if (2==v62) then v64={};for v102=1, #v63 do v64[v102]=v10(v9(v11(v63,v102,v102)));end v62=3;end if (v62==1) then v63=v11(v27,v29,(v29 + v61) -1 );v29=v29 + v61 ;v62=2;end if (v62==0) then v63=nil;if  not v61 then v61=v34();if (v61==0) then return "";end end v62=1;end end end local v37=v34;local function v38(...) return {...},v20("#",...);end local function v39() local v65=0;local v66;local v67;local v68;local v69;local v70;local v71;while true do if (v65==0) then v66={};v67={};v68={};v69={v66,v67,nil,v68};v65=1;end if (v65==1) then v70=v34();v71={};for v104=1,v70 do local v105=0;local v106;local v107;while true do if (v105==1) then if (v106==1) then v107=v32()~=0 ;elseif (v106==2) then v107=v35();elseif (v106==3) then v107=v36();end v71[v104]=v107;break;end if (v105==0) then v106=v32();v107=nil;v105=1;end end end v69[3]=v32();v65=2;end if (v65==2) then for v108=1,v34() do local v109=0;local v110;while true do if (v109==0) then v110=v32();if (v31(v110,1,1)==0) then local v123=0;local v124;local v125;local v126;while true do if (v123==3) then if (v31(v125,3,3)==1) then v126[4]=v71[v126[4]];end v66[v108]=v126;break;end if (v123==2) then if (v31(v125,1,1)==(932 -(857 + 74))) then v126[2]=v71[v126[2]];end if (v31(v125,2,2)==1) then v126[3]=v71[v126[571 -(367 + 201) ]];end v123=3;end if (v123==0) then v124=v31(v110,2,3);v125=v31(v110,4,6);v123=1;end if (v123==1) then v126={v33(),v33(),nil,nil};if (v124==0) then v126[3]=v33();v126[4]=v33();elseif (v124==1) then v126[3]=v34();elseif (v124==2) then v126[3]=v34() -(2^16) ;elseif (v124==3) then local v298=0;while true do if (v298==0) then v126[3]=v34() -(2^16) ;v126[4]=v33();break;end end end v123=2;end end end break;end end end for v111=928 -(214 + 713) ,v34() do v67[v111-1 ]=v39();end return v69;end end end local function v40(v72,v73,v74) local v75=v72[1];local v76=v72[2];local v77=v72[3];return function(...) local v78=v75;local v79=v76;local v80=v77;local v81=v38;local v82=1;local v83= -1;local v84={};local v85={...};local v86=v20("#",...) -(1 + 0) ;local v87={};local v88={};for v99=0,v86 do if (v99>=v80) then v84[v99-v80 ]=v85[v99 + 1 ];else v88[v99]=v85[v99 + 1 + 0 ];end end local v89=(v86-v80) + 1 ;local v90;local v91;while true do local v100=0;while true do if (v100==1) then if (v91<=35) then if (v91<=17) then if (v91<=(885 -(282 + 595))) then if (v91<=3) then if (v91<=1) then if (v91>(1637 -(1523 + 114))) then v88[v90[2]]=v88[v90[3]];else local v139=v90[2 + 0 ];local v140=v88[v139];for v239=v139 + (1 -0) ,v83 do v15(v140,v88[v239]);end end elseif (v91>2) then v88[v90[2]]=v88[v90[3]];else v88[v90[2]]=v73[v90[3]];end elseif (v91<=5) then if (v91>4) then local v145=v90[2];local v146=v88[v145 + 2 ];local v147=v88[v145] + v146 ;v88[v145]=v147;if (v146>0) then if (v147<=v88[v145 + 1 ]) then v82=v90[3];v88[v145 + (1068 -(68 + 997)) ]=v147;end elseif (v147>=v88[v145 + 1 ]) then local v320=0;while true do if (0==v320) then v82=v90[3];v88[v145 + 3 ]=v147;break;end end end else local v149=v90[2];v88[v149]=v88[v149](v21(v88,v149 + 1 ,v83));end elseif (v91<=6) then do return v88[v90[2]]();end elseif (v91>7) then v88[v90[1272 -(226 + 1044) ]]=v88[v90[3]] + v90[4] ;else v88[v90[2]][v90[3]]=v90[17 -13 ];end elseif (v91<=12) then if (v91<=10) then if (v91==9) then v88[v90[2]][v88[v90[3]]]=v90[121 -(32 + 85) ];else do return;end end elseif (v91>11) then v88[v90[2]]=v74[v90[3]];else local v155=v79[v90[3]];local v156;local v157={};v156=v18({},{[v7("\254\228\233\180\197\222\248","\218\161\187\128")]=function(v240,v241) local v242=v157[v241];return v242[1][v242[2 + 0 ]];end,[v7("\67\118\213\74\18\120\114\77\222\87","\17\28\41\187\47\101")]=function(v243,v244,v245) local v246=v157[v244];v246[1][v246[2]]=v245;end});for v248=1,v90[1 + 3 ] do local v249=0;local v250;while true do if (v249==1) then if (v250[1]==3) then v157[v248-1 ]={v88,v250[3]};else v157[v248-1 ]={v73,v250[3]};end v87[ #v87 + (2 -1) ]=v157;break;end if (v249==0) then v82=v82 + 1 ;v250=v78[v82];v249=1;end end end v88[v90[2]]=v40(v155,v156,v74);end elseif (v91<=14) then if (v91==13) then local v159=0;local v160;local v161;local v162;while true do if (v159==0) then v160=v90[3 -1 ];v161=v88[v160];v159=1;end if (v159==1) then v162=v88[v160 + 2 ];if (v162>0) then if (v161>v88[v160 + (1 -0) ]) then v82=v90[3];else v88[v160 + 3 ]=v161;end elseif (v161<v88[v160 + 1 ]) then v82=v90[3];else v88[v160 + 3 ]=v161;end break;end end elseif (v88[v90[2]]==v90[4]) then v82=v82 + (351 -(87 + 263)) ;else v82=v90[3];end elseif (v91<=15) then local v163=0;local v164;local v165;local v166;local v167;while true do if (v163==2) then for v323=v164,v83 do local v324=0;while true do if (v324==0) then v167=v167 + 1 ;v88[v323]=v165[v167];break;end end end break;end if (v163==1) then v83=(v166 + v164) -1 ;v167=0;v163=2;end if (v163==0) then v164=v90[2];v165,v166=v81(v88[v164](v88[v164 + 1 ]));v163=1;end end elseif (v91>16) then v88[v90[2]]=v88[v90[3]][v90[4]];else local v267=0;local v268;local v269;local v270;local v271;while true do if (v267==1) then v83=(v270 + v268) -1 ;v271=0;v267=2;end if (v267==2) then for v353=v268,v83 do v271=v271 + (181 -(67 + 113)) ;v88[v353]=v269[v271];end break;end if (v267==0) then v268=v90[2];v269,v270=v81(v88[v268](v88[v268 + 1 ]));v267=1;end end end elseif (v91<=26) then if (v91<=21) then if (v91<=19) then if (v91==18) then v88[v90[2 + 0 ]]= #v88[v90[3]];else v88[v90[2]]=v88[v90[3]] + v90[4] ;end elseif (v91==(49 -29)) then v88[v90[2]]=v88[v90[3 + 0 ]]%v90[4] ;else v88[v90[2]]=v90[3];end elseif (v91<=23) then if (v91>(87 -65)) then local v173=v90[2];v88[v173](v21(v88,v173 + (953 -(802 + 150)) ,v83));else local v174=0;local v175;local v176;while true do if (v174==1) then for v325=v175 + 1 ,v90[7 -4 ] do v15(v176,v88[v325]);end break;end if (v174==0) then v175=v90[2];v176=v88[v175];v174=1;end end end elseif (v91<=24) then v88[v90[3 -1 ]]=v88[v90[3 + 0 ]]%v88[v90[1001 -(915 + 82) ]] ;elseif (v91>25) then local v272=0;local v273;local v274;local v275;while true do if (v272==2) then for v356=1,v90[4] do local v357=0;local v358;while true do if (v357==1) then if (v358[2 -1 ]==(2 + 1)) then v275[v356-1 ]={v88,v358[3]};else v275[v356-1 ]={v73,v358[1190 -(1069 + 118) ]};end v87[ #v87 + 1 ]=v275;break;end if (0==v357) then v82=v82 + 1 ;v358=v78[v82];v357=1;end end end v88[v90[2]]=v40(v273,v274,v74);break;end if (v272==1) then v275={};v274=v18({},{[v7("\13\57\51\176\5\55\30","\97\82\102\90\222")]=function(v359,v360) local v361=v275[v360];return v361[1][v361[2]];end,[v7("\17\148\69\194\64\165\32\175\78\223","\204\78\203\43\167\55")]=function(v362,v363,v364) local v365=0;local v366;while true do if (v365==0) then v366=v275[v363];v366[1][v366[2]]=v364;break;end end end});v272=2;end if (v272==0) then v273=v79[v90[3]];v274=nil;v272=1;end end else v82=v90[3];end elseif (v91<=30) then if (v91<=28) then if (v91>(61 -34)) then local v178=v90[3 -1 ];local v179=v88[v178];local v180=v88[v178 + 2 ];if (v180>0) then if (v179>v88[v178 + 1 ]) then v82=v90[3];else v88[v178 + 3 ]=v179;end elseif (v179<v88[v178 + 1 ]) then v82=v90[1 + 2 ];else v88[v178 + 3 ]=v179;end else local v181=0;local v182;local v183;local v184;while true do if (v181==1) then v184=v90[3];for v330=1,v184 do v183[v330]=v88[v182 + v330 ];end break;end if (0==v181) then v182=v90[3 -1 ];v183=v88[v182];v181=1;end end end elseif (v91>29) then local v185=v90[2];do return v88[v185](v21(v88,v185 + 1 ,v90[3]));end else v88[v90[2]][v88[v90[3]]]=v90[4 + 0 ];end elseif (v91<=32) then if (v91==31) then v88[v90[2]]=v88[v90[794 -(368 + 423) ]]%v88[v90[4]] ;else do return;end end elseif (v91<=33) then local v189=v90[2];local v190=v88[v189];local v191=v90[3];for v251=3 -2 ,v191 do v190[v251]=v88[v189 + v251 ];end elseif (v91==34) then v88[v90[2]]={};else local v278=0;local v279;local v280;local v281;local v282;while true do if (v278==2) then for v367=v279,v83 do v282=v282 + 1 ;v88[v367]=v280[v282];end break;end if (v278==1) then v83=(v281 + v279) -1 ;v282=0;v278=2;end if (v278==0) then v279=v90[2];v280,v281=v81(v88[v279](v21(v88,v279 + (19 -(10 + 8)) ,v83)));v278=1;end end end elseif (v91<=53) then if (v91<=44) then if (v91<=39) then if (v91<=37) then if (v91>36) then local v192=0;local v193;while true do if (v192==0) then v193=v90[2];do return v21(v88,v193,v83);end break;end end else for v254=v90[2],v90[3] do v88[v254]=nil;end end elseif (v91==38) then v88[v90[2]]=v74[v90[3]];else v88[v90[2]][v90[3]]=v88[v90[4]];end elseif (v91<=41) then if (v91>40) then v88[v90[2]]=v90[3] + v88[v90[4]] ;else v88[v90[2]][v88[v90[3]]]=v88[v90[15 -11 ]];end elseif (v91<=42) then local v201=0;local v202;local v203;local v204;local v205;while true do if (v201==0) then v202=v90[2];v203,v204=v81(v88[v202](v21(v88,v202 + 1 ,v90[3])));v201=1;end if (v201==2) then for v333=v202,v83 do v205=v205 + 1 ;v88[v333]=v203[v205];end break;end if (v201==1) then v83=(v204 + v202) -1 ;v205=0;v201=2;end end elseif (v91>43) then local v283=0;local v284;local v285;local v286;local v287;while true do if (v283==2) then for v370=v284,v83 do v287=v287 + 1 ;v88[v370]=v285[v287];end break;end if (v283==0) then v284=v90[2];v285,v286=v81(v88[v284](v21(v88,v284 + (443 -(416 + 26)) ,v90[3])));v283=1;end if (v283==1) then v83=(v286 + v284) -1 ;v287=0 -0 ;v283=2;end end elseif  not v88[v90[2]] then v82=v82 + 1 + 0 ;else v82=v90[3];end elseif (v91<=48) then if (v91<=(80 -34)) then if (v91==45) then v88[v90[2]]=v88[v90[3]] + v88[v90[442 -(145 + 293) ]] ;else v88[v90[2]][v90[3]]=v90[434 -(44 + 386) ];end elseif (v91==47) then v88[v90[1488 -(998 + 488) ]]=v88[v90[1 + 2 ]]%v90[4] ;else local v210=v90[2];do return v88[v210](v21(v88,v210 + 1 ,v90[3]));end end elseif (v91<=50) then if (v91>49) then local v211=0;local v212;local v213;local v214;while true do if (v211==1) then v214=v88[v212] + v213 ;v88[v212]=v214;v211=2;end if (2==v211) then if (v213>0) then if (v214<=v88[v212 + 1 + 0 ]) then local v381=0;while true do if (v381==0) then v82=v90[775 -(201 + 571) ];v88[v212 + 3 ]=v214;break;end end end elseif (v214>=v88[v212 + 1 ]) then local v382=0;while true do if (v382==0) then v82=v90[1141 -(116 + 1022) ];v88[v212 + (12 -9) ]=v214;break;end end end break;end if (v211==0) then v212=v90[2];v213=v88[v212 + 2 ];v211=1;end end else local v215=v90[2];local v216=v88[v215];for v256=v215 + 1 ,v83 do v15(v216,v88[v256]);end end elseif (v91<=51) then for v257=v90[2],v90[3] do v88[v257]=nil;end elseif (v91==52) then local v288=0;local v289;while true do if (0==v288) then v289=v90[2];v88[v289]=v88[v289](v21(v88,v289 + 1 ,v90[3]));break;end end else v88[v90[2]]=v

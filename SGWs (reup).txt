#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
; #Warn  ; Enable warnings to assist with detecting common errors.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

#z::
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    LOGING IN
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;


BaseLevel:
SetTitleMatchMode, 2
IfWinExist Google Chrome
	{
		WinActivate
		sendinput ^1
		sleep 2000
		SendInput !+r
		sleep 2000
	}
else
	{
		Run http://www.google.com
		Sleep 20000
	}

MouseMove, 8, 500

Address = http://quantumgate.gatewars.com/index.php
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly

sendinput ^1
sleep 1000
SendInput ^w
Sleep 2000

StringSplit, Captcha, MyArray26, %A_Space%
Code := Captcha4
sleep 500
SendInput %Code%
Sleep 500
SendInput ^v{tab}
Sleep 500
SendInput **username**{tab} ;;removed
Sleep 500
SendInput **email**{tab} ;;removed
Sleep 500
SendInput **password**{enter} ;;removed
sleep 2000

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Getting Info
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

Address = http://quantumgate.gatewars.com/base.php
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly

loop, %MyArray0%
{
clipboard := MyArray%A_Index%
StringSplit, Info, clipboard, %A_Space%%A_Tab%'r
GetInfo%A_Index% := Info%Info0%
if GetInfo%A_Index% = billion
{
	notBill := (info0 - 1)
	if notBill < 0
	notbill = 0
	bill := Info%notBill%
	GetInfo%A_Index% = %bill%000000000
}
if GetInfo%A_Index% = trillion
{
	notTrill := (info0 - 1)
	if notTrill < 0
	notbill = 0
	Trill := Info%notTrill%
	GetInfo%A_Index% = %Trill%000000000000
}
}

clipboard := MyArray21 ;next turn
StringSplit, Info, clipboard, %A_Space%
GetInfo12 := Info3

clipboard := MyArray52 ;unit production
StringSplit, Info, clipboard, %A_Space%%A_Tab%
GetInfo18 := Info3

clipboard := MyArray54 ;income
StringSplit, Info, clipboard, %A_Space%%A_Tab%
GetInfo19 := Info4

clipboard := MyArray22 ;messages
StringSplit, Info, clipboard, %A_Space%
GetInfo22 := Info2

loop, %MyArray0%
{
StringReplace, GetInfo%A_Index%, GetInfo%A_Index%,`,,,All
}

StringReplace, GetInfo11, GetInfo11,`:,`.,All
StringSplit, RNG, GetInfo11, `.
StringTrimRight, GetInfo22, Getinfo22, 6


AttackSpiderCost = 6000
HumanFormAttackerCost = 229000
DefenseSpiderCost = 6000
HumanFormDefenderCost = 229000
MiningBotCost = 2500
InfiltrationUnitsCost = 5500
CovertInfiltratorBotCost = 7000

If Inbox > 0
{
	If Inbox < %GetInfo22%
	{
	NewMessages := (GetInfo22 - Inbox)
	MessageSub := 1
	}
}

RandomNo := RNG3
GetInfo20 := (GetInfo19*2100)
GetInfo21 := (GetInfo20-Getinfo17)
GameTime := GetInfo11
NextTurn := GetInfo12
Inbox := GetInfo22
TurnsOnHand := GetInfo15
NaqOnHand := GetInfo16
NaqInBank := GetInfo17
MaxBank := GetInfo20
RemainingBank := GetInfo21
BaseUP := GetInfo18
Income := GetInfo19
AttackSpider := GetInfo86
HumanFormAttacker := GetInfo87
Attackbot := GetInfo88
DefenseSpider := GetInfo89
HumanFormDefender := GetInfo90
Defensebot := GetInfo91
MiningBot := GetInfo92
InfiltrationUnits := GetInfo93
CovertInfiltratorBot := GetInfo94
GenericSpider := GetInfo95
TotalFightingForce := GetInfo96

;msgbox RandomNo = %RNG3%`nGameTime = %GameTime%`nNextTurn = %NextTurn%`nInbox = %Inbox%`nTurnsOnHand = %TurnsOnHand%`nNaqOnHand := %NaqOnHand%`nNaqInBank := %NaqInBank%`nMaxBank := %MaxBank%`nRemainingBank := %RemainingBank%`nBaseUP := %BaseUP%`nIncome := %Income%`nAttackSpider := %AttackSpider%`nHumanFormAttacker := %HumanFormAttacker%`nAttackbot := %Attackbot%`nDefenseSpider := %DefenseSpider%`nHumanFormDefender := %HumanFormDefender%`nDefensebot := %Defensebot%`nMiningBot := %MiningBot%`nInfiltrationUnits := %InfiltrationUnits%`nCovertInfiltratorBot := %CovertInfiltratorBot%`nGenericSpider := %GenericSpider%`nTotalFightingForce := %TotalFightingForce%
;EmailSubj = Login Stats
;EmailBody = GameTime = %GameTime%`nNextTurn = %NextTurn%`nInbox = %Inbox%`nTurnsOnHand = %TurnsOnHand%`nNaqOnHand := %NaqOnHand%`nNaqInBank := %NaqInBank%`nMaxBank := %MaxBank%`nRemainingBank := %RemainingBank%`nBaseUP := %BaseUP%`nIncome := %Income%`nAttackSpider := %AttackSpider%`nHumanFormAttacker := %HumanFormAttacker%`nAttackbot := %Attackbot%`nDefenseSpider := %DefenseSpider%`nHumanFormDefender := %HumanFormDefender%`nDefensebot := %Defensebot%`nMiningBot := %MiningBot%`nInfiltrationUnits := %InfiltrationUnits%`nCovertInfiltratorBot := %CovertInfiltratorBot%`nGenericSpider := %GenericSpider%`nTotalFightingForce := %TotalFightingForce%
;Gosub SendEmail

Sendinput ^w
sleep 1000
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Variables
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;Bank if Naq above income * MaxOnHand
MaxOnHand := 0.4
SafeOnHand := 50000000

;Train UU to miner when UU is above
GoTrain := BaseUP * 0.04


;Stop Farming when
FullBank := (maxbank*0.90)
MinTurns := 4000

;Buy UP if bank above
quartbank := (Maxbank*1.0)

;MinFarmValue
basefarm := 6000000000
toohighfarm := 15000000000

;farming
TotalNumberFarmed := 0
TotalAmountFarmed := 0

;msgbox train is over %GoTrain% UU`nStop farming when above %fullbank% Naq in bank`n(Max bank %MaxBank%)
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Repair
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

Repair:

Address = http://quantumgate.gatewars.com/armory.php
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly


loop, %MyArray0%
{
If InStr(MyArray%a_index%, "Attack Weapons") and InStr(MyArray%a_index%, "Quantity")
AttackStart := a_index
If InStr(MyArray%a_index%, "Defense Weapons") and InStr(MyArray%a_index%, "Quantity")
DefenceStart := a_index
IfInString, MyArray%a_index%, Rank & Military 
DefenceEnd := a_index

clipboard := MyArray%A_Index%
StringSplit, Info, clipboard, %A_Space%%A_Tab%'r
GetInfo%A_Index% := Info%Info0%
if GetInfo%A_Index% = billion
{
	notBill := (info0 - 1)
	if notBill < 0
	notbill = 0
	bill := Info%notBill%
	GetInfo%A_Index% = %bill%000000000
}
StringReplace, GetInfo%A_Index%, GetInfo%A_Index%,`,,,All
}
NaqOnHand := GetInfo16
NaqInBank := GetInfo17

attackweps := ((defencestart - attackstart) -2)/3
defenceweps := ((defenceend - defencestart) -2)/3

loop, %attackweps%
{
Weapon := round(44 + 2 + ((A_index -1) *3))
if weapon < 0
	{
	sendinput ^w
	sleep 500
	Goto Repair
	}
clipboard := MyArray%Weapon%
StringSplit, Info, clipboard, %A_Space%
w := info0 -3
x := info0 -2
y := info0
StringReplace, info%w%, info%w%, `,,, All
StringReplace, info%x%, info%x%, `,,, All
StringReplace, info%y%, info%y%, `,,, All
StringReplace, info%w%, info%w%, %A_TAB%,, All
StringReplace, info%x%, info%x%, %A_TAB%,, All
StringReplace, info%y%, info%y%, %A_TAB%,, All
attackinfow%a_index% := info%w%
attackinfox%a_index% := info%x%
attackinfoy%a_index% := info%y%
}

loop, %defenceweps%
{
Weapon := round(44 + 4 + (3 * attackweps) + ((A_index -1) *3))
if weapon < 0
	{
	sendinput ^w
	sleep 500
	Goto Repair
	}
clipboard := MyArray%Weapon%
StringSplit, Info, clipboard, %A_Space%
w := info0 -3
x := info0 -2
y := info0
StringReplace, info%w%, info%w%, `,,, All
StringReplace, info%x%, info%x%, `,,, All
StringReplace, info%y%, info%y%, `,,, All
StringReplace, info%w%, info%w%, %A_TAB%,, All
StringReplace, info%x%, info%x%, %A_TAB%,, All
StringReplace, info%y%, info%y%, %A_TAB%,, All
defenceinfow%a_index% := info%w%
defenceinfox%a_index% := info%x%
defenceinfoy%a_index% := info%y%
}

;check defence
loop, %defenceweps%
{
	MStr := defenceinfoy%a_index%
	Cstr := defenceinfox%a_index%
	RStr := Round(defenceinfoy%a_index%*0.0125)

	if CStr <> %MStr%
	{
		If Naqonhand < %SafeOnHand%
		{
			Address = http://quantumgate.gatewars.com/bank.php
			CheckSubCount := 0
			GoSub OpenAndCheck
			FailLoadedCount := 0
			GoSub CheckLoadedCorrectly

			Sendinput {alt down}d{alt up}
			Sleep 1500
			Sendinput {shift down}
			sleep 300
	
			loop 5
			{
				SendInput {tab}
				Sleep 100
			}
	
			Sendinput {Shift up}
			sleep 500
			sendinput %safeonhand%
			Sleep 1000
			sendinput {tab}
			Sleep 1000
			sendinput {enter}
			Sleep 2000
			Send ^w
			sleep 1000
		}
	
		Sendinput {alt down}d{alt up}
		Sleep 1500
	
		tabs := 22 + (attackweps*5) + ((a_index-1)*5)
		loop, %tabs%
		{
			sendInput {tab}
			sleep 100
		}
		Sleep 2450
		sendinput %RStr%{tab}
		Sleep 1500
		sendinput {enter}
		Sleep 3000
		sendinput ^w
		sleep 2000
		goto repair
	}
}

;check attack
loop, %attackweps%
{
	MStr := attackinfoy%a_index%
	Cstr := attackinfox%a_index%
	RStr := Round(attackinfoy%a_index%*0.0125)

	if CStr <> %MStr%
	{
		If Naqonhand < %SafeOnHand%
		{
			Address = http://quantumgate.gatewars.com/bank.php
			CheckSubCount := 0
			GoSub OpenAndCheck
			FailLoadedCount := 0
			GoSub CheckLoadedCorrectly

			Sendinput {alt down}d{alt up}
			Sleep 1500
			Sendinput {shift down}
			sleep 300
	
			loop 5
			{
				SendInput {tab}
				Sleep 100
			}
	
			Sendinput {Shift up}
			sleep 500
			sendinput %safeonhand%
			Sleep 1000
			sendinput {tab}
			Sleep 1000
			sendinput {enter}
			Sleep 2000
			Send ^w
			sleep 1000
		}
	
		Sendinput {alt down}d{alt up}
		Sleep 1500
	
		tabs := 22 + ((a_index-1)*5)
		loop, %tabs%
		{
			sendInput {tab}
			sleep 100
		}
		Sleep 2450
		sendinput %RStr%{tab}
		Sleep 1500
		sendinput {enter}
		Sleep 3000
		sendinput ^w
		sleep 2000
		goto repair
	}
}

sendinput ^w
sleep 1500

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Train
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

If GoTrain < %GenericSpider%
{
	Address = http://quantumgate.gatewars.com/train.php
	CheckSubCount := 0
	GoSub OpenAndCheck
	TrainLoadCount := 0
	TRAINLOAD:
	If TrainLoadCount >= 3
		{
		EmailSubj = Error
		EmailBody = Problem when trying to load the %address%`n`nreturning to base level.`n`nCurrent messages; %Inbox%
		GoSub SendEmail
		Sleep 500
		Goto BaseLevel
		sleep 1000
		}
	
	loop, 5
	{
	clipboard = ""
	ClipWait, 1
	sendinput ^a
	sleep 200
	sendinput ^c
	sleep 500
	ClipWait, 1
	sendinput {tab}
	StringSplit, MyArray, clipboard, `r
	x := Myarray0 - 2
	if x < 0
	x := 0
	KingdomGames = % MyArray%x%
	
	
	IfNotInString, MyArray2, Era 39 reset
		{
		sleep 500
		if a_Index = 5
			{
			TrainLoadCount ++
			sleep 500
			GoSub TRAINLOAD
			}
		continue
		}
	else
		{
			break
		}
	}




	StringSplit, NaqInfo, MyArray16, %A_Space%%A_Tab%'r
	StringReplace, NaqInfo%naqinfo0%, NaqInfo%naqinfo0%,`,,,All
	NaqOnHand := NaqInfo%naqinfo0%
	
	StringSplit, UUInfo, MyArray80, %A_Space%%A_Tab%'r
	StringReplace, UUInfo%UUInfo0%, UUInfo%UUInfo0%,`,,,All
	GenericSpider := UUInfo%UUInfo0%
	
	MiningBotCost := 2500
	TrainingCost := GenericSpider * MiningBotCost

	If NaqOnHand < %TrainingCost%
		{
			Address = http://quantumgate.gatewars.com/bank.php
			CheckSubCount := 0
			GoSub OpenAndCheck
			FailLoadedCount := 0
			GoSub CheckLoadedCorrectly

			Sendinput !d
			Sleep 1500
			Sendinput {shift down}
			sleep 300

			loop 5
			{
				SendInput {tab}
				Sleep 100
			}
	
			Sendinput {Shift up}
			sleep 500
			sendinput %TrainingCost%
			Sleep 1000
			sendinput {tab}
			Sleep 1000
			sendinput {enter}
			Sleep 2000
			Send ^w
			sleep 1000
		}
	
	
	Sendinput !d
	Sleep 2000
	loop 26
	{
		Sendinput {Tab}
		sleep 100
	}
	Sleep 2000
	sendinput %GenericSpider%
	Sleep 1000
	loop 7
	{
		sendinput {tab}
		sleep 100
	}
	Sleep 2000
	sendinput {enter}
	Sleep 3000
	sendinput ^w
}
Sleep 3000


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Bank
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

GoBank := (Income*MaxOnHand)
If GoBank < %NaqOnHand%
{
	Address = http://quantumgate.gatewars.com/bank.php
	CheckSubCount := 0
	GoSub OpenAndCheck
	FailLoadedCount := 0
	GoSub CheckLoadedCorrectly

	loop 21
	{
	Send {tab}
	sleep 100
	}
	SendInput {enter}
	Sleep 2000
	Sendinput ^w
}
sleep 4000
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Market
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    FARMING
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

If NaqInBank > %FullBank%
{
	Goto EndFarm
	sleep 1000
}


If TurnsOnHand < %MinTurns%
{
	Goto EndFarm
	sleep 1000
}

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Farm Value
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
MinFarmValue := 1600000000
;goto ENDGAL

InputBox, MinFarmValue, Minimum Naquadah, Whats the lowest naq you are willing to farm?`nPlease do not use any commas`n`nYou have 8 seconds to enter a value or I shall work it out for myself.,,,,,,, 8, 
if ErrorLevel
	MsgBox, 0, time out/cancel, I'll work it out, 2
else
	goto EndGAL

Count := 0
TotServFarm := 0
FP1 := 0

loop 9
{

FP2 := 2 + FP1
FP1 ++

Address = http://quantumgate.gatewars.com/attacklogALL.php?aip=&dip=&aid=&did=&page=%FP2%
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly
sleep 1000

loop 100
{
	x := 41 + a_index
	Target := myarray%x%

	StringSplit, Target, Target, %A_Tab%
	StringSplit, Details, Target4, %A_space%
;	msgbox type of attack = %details3%`namount taken %details2%

	DeetA%A_Index% := details3
	DeetB%A_Index% := details2
	StringReplace, DeetB%A_Index%, DeetB%A_Index%, `,,, All
}


loop 100
{
	if DeetA%A_Index% = Untrained
		{
;		msgbox skipping (UUs)
		continue
		}

	if DeetB%A_Index% < %basefarm%
		{
;		msgbox skipping (too low)
		continue
		}

	if DeetB%A_Index% > %toohighfarm%
		{
;		msgbox skipping (too big)
		continue
		}

	ThisFarm := DeetB%A_index%
	Count ++
	TotServFarm := TotServFarm + ThisFarm
}
;msgbox %totservfarm% naq from %count% targets
sendinput ^w
sleep 1000
}

;msgbox %Count% farmed for %TotServFarm% naq
MinFarmValue := Round((Totservfarm/count)*1.02)
if count < 550 
	{
	msgbox, 0, Error, Sample group too small (%Count%/900)`n this could be due to pages not loading or too many people raiding, 4
	minfarmvalue = 999999999999999
	}
endGAL:
	MsgBox, 0, MinFarm, Min farm = %minfarmvalue%, 5

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Get info with IDM 
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

SetTitleMatchMode, 2
WinActivate, Google Chrome
sleep 500
sendinput ^t
sleep 400
sendinput chrome-extension://chphlpgkkbolifaimnlloiipkdnihall/onetab.html{enter}
sleep 10000
MouseMove, 407, 225
sleep 500
MouseMove, 477, 225, 100
sleep 200
Click 444, 225
sleep 5000

;msgbox open

sendinput {AppsKey}
sleep 800
sendinput {up 4}
sleep 800
sendinput {enter}
sleep 15000
;msgbox waiting
sleep 800
sendinput {tab}{down 3}
sleep 500
sendinput {end}{shift down}{home}{shift up}
sleep 500
sendinput C:\Documents and Settings\Location\Desktop\Loki\PHPs
sleep 5000
sendinput {tab 5}
sleep 500 
sendinput {enter}
sleep 500
sendinput {tab 4}
sleep 500
sendinput {down}
sleep 500
sendinput {space}
sleep 500
sendinput {down}
sleep 500
sendinput {space}
sleep 500
sendinput {enter}
sleep 500
sendinput {down 4}
sleep 500
sendinput {up}
sleep 800
sendinput {enter}
sleep 1500
WinActivate, Google Chrome
sleep 1500
sendinput ^w
sleep 500
sendinput ^w
WinWaitActive, Complete - Notepad, , 200	
if ErrorLevel
{
Goto BaseLevel
}
sleep 500
WinClose
;msgbox done and done! go for next 


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Farm
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

Targets = "End"
CountTargets := 0
Loop 126
{
docNo := a_index +1
PageNo = P%a_index%
FileRead, FileInfo, PHPs\battlefieldE_%docNo%.htm
stringsplit, MyArray, FileInfo, `n

loop 30
{
UserNo = U%A_index%
IDArrayInfo := ((a_index * 17)+282)
NaqArrayInfo := IDArrayInfo + 14
StringReplace, MyArray%NaqArrayInfo%, MyArray%NaqArrayInfo%, %A_SPACE%,, All
StringReplace, MyArray%NaqArrayInfo%, MyArray%NaqArrayInfo%, `,,, All
StringGetPos, OutputVar, MyArray%NaqArrayInfo%, Naq, R
StringLen, yy, MyArray%NaqArrayInfo%
zz := yy-outputvar
StringTrimRight, MyArray%NaqArrayInfo%, MyArray%NaqArrayInfo%, %zz%




StringReplace, MyArray%IDArrayInfo%, MyArray%IDArrayInfo%, %A_SPACE%,, All
StringGetPos, OutputVar, MyArray%IDArrayInfo%, =,r
StringTrimRight, MyArray%IDArrayInfo%, MyArray%IDArrayInfo%, 2
xx := OutputVar +1
StringTrimLeft, MyArray%IDArrayInfo%, MyArray%IDArrayInfo%, %xx%



Naqx := MyArray%NaqArrayInfo%
IDx := MyArray%IDArrayInfo%


;msgbox ID = **%IDx%** has **%Naqx%** Naq

%PageNo%%UserNo% := IDx
%PageNo%%UserNo%Naq := Naqx

If Naqx > %MinFarmValue%
	{
	Targets := Naqx . "." . IDx "," Targets
	CountTargets ++
	}

}
FileDelete, PHPs\battlefieldE_%docNo%.htm
}

;msgbox page1 user 1 ID = %p1u1% naq = %p1u1Naq%`npage1 user 10 ID = %p1u10% naq = %p1u10Naq%`npage2 user 20 ID = %p2u20% Naq = %p2u20Naq%`npage2 user 30 ID = %p2u30% Naq = %p2u30Naq%

;Sort Targets, NR D, 
 
stringsplit, CurrentFarm, Targets, `,
;msgbox you have %Counttargets% available farms
Loop, %CountTargets%
{
stringsplit, Farm, CurrentFarm%A_Index%, `.

Address = http://quantumgate.gatewars.com/stats.php?id=%Farm2%
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly

StringSplit, AttackArray, MyArray43, %A_Tab%
CurrentIDCheck = %attackArray2%

StringSplit, AttackArray, MyArray49, %A_Space%
StringReplace, attackArray2, attackArray2, `,,, , ALL
CurrentNaqCheck = %attackArray2%

StringSplit, TurnsArray, MyArray15, %A_Space%%A_Tab%'r
StringReplace, TurnsOnHand, TurnsArray%TurnsArray0%,`,,,All

StringSplit, NaqArray, MyArray17, %A_Space%%A_Tab%'r
StringReplace, NaqInBank, NaqArray%NaqArray0%,`,,,All


If NaqInBank > %FullBank%
{
	Goto EndFarm
	sleep 1000
}


If TurnsOnHand < %MinTurns%
{
	Goto EndFarm
	sleep 1000
}


if CurrentIDCheck <> %Farm2%
{
	Sendinput ^w
	sleep 200
	continue
}

if CurrentNaqCheck = ?????
{
	Sendinput ^w
	sleep 200
	Continue
}

if CurrentNaqCheck < %Farm1%
{
	Sendinput ^w
	sleep 200
	Continue
}
Sendinput ^w
sleep 200

Address = http://quantumgate.gatewars.com/attack.php?id=%Farm2%&submit=Attack
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly

loop 20
{
	Sendinput {tab}
	sleep 50
}
Sleep 300
sendinput 10
Sleep 300
sendinput {tab}
sleep 400
sendinput {space}
sleep 500

Address = http://quantumgate.gatewars.com/armory.php
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly


loop, 23
{
sendinput {tab}
sleep 100
}
sendinput {enter}

Address = http://quantumgate.gatewars.com/bank.php
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly

loop, 21
{
sendinput {tab}
sleep 100
}
sendinput {enter}
sleep 300
sendinput ^w
sleep 500
sendinput ^w
sleep 500
sendinput ^w
}



EndFarm:
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Chill
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

Address = http://quantumgate.gatewars.com/base.php
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly

loop, %MyArray0%
{
clipboard := MyArray%A_Index%
StringSplit, Info, clipboard, %A_Space%%A_Tab%'r
GetInfo%A_Index% := Info%Info0%
if GetInfo%A_Index% = billion
{
	notBill := (info0 - 1)
	if notBill < 0
	notbill = 0
	bill := Info%notBill%
	GetInfo%A_Index% = %bill%000000000
}
if GetInfo%A_Index% = trillion
{
	notTrill := (info0 - 1)
	if notTrill < 0
	notbill = 0
	Trill := Info%notTrill%
	GetInfo%A_Index% = %Trill%000000000000
}
}

clipboard := MyArray21 ;next turn
StringSplit, Info, clipboard, %A_Space%
GetInfo12 := Info3

clipboard := MyArray52 ;unit production
StringSplit, Info, clipboard, %A_Space%%A_Tab%
GetInfo18 := Info3

clipboard := MyArray54 ;income
StringSplit, Info, clipboard, %A_Space%%A_Tab%
GetInfo19 := Info4

clipboard := MyArray22 ;messages
StringSplit, Info, clipboard, %A_Space%
GetInfo22 := Info2

loop, %MyArray0%
{
StringReplace, GetInfo%A_Index%, GetInfo%A_Index%,`,,,All
}

StringReplace, GetInfo11, GetInfo11,`:,`.,All
StringSplit, RNG, GetInfo11, `.
StringTrimRight, GetInfo22, Getinfo22, 6

GetInfo20 := (GetInfo19*1930)
GetInfo21 := (GetInfo20-Getinfo17)

If Inbox > 0
{
	If Inbox < %GetInfo22%
	{
	NewMessages := (GetInfo22 - Inbox)
	MessageSub := 1
	}
}


RandomNo := RNG3
GameTime := GetInfo11
NextTurn := GetInfo12
Inbox := GetInfo22
TurnsOnHand := GetInfo15
NaqOnHand := GetInfo16
NaqInBank := GetInfo17
MaxBank := GetInfo20
RemainingBank := GetInfo21
BaseUP := GetInfo18
Income := GetInfo19
AttackSpider := GetInfo86
HumanFormAttacker := GetInfo87
Attackbot := GetInfo88
DefenseSpider := GetInfo89
HumanFormDefender := GetInfo90
Defensebot := GetInfo91
MiningBot := GetInfo92
InfiltrationUnits := GetInfo93
CovertInfiltratorBot := GetInfo94
GenericSpider := GetInfo95
TotalFightingForce := GetInfo96

If MessageSub = 1
GoSub GotMessage
MessageSub = 0
;msgbox GameTime = %GameTime%`nNextTurn = %NextTurn%`nInbox = %Inbox%`nTurnsOnHand = %TurnsOnHand%`nNaqOnHand := %NaqOnHand%`nNaqInBank := %NaqInBank%`nMaxBank := %MaxBank%`nRemainingBank := %RemainingBank%`nBaseUP := %BaseUP%`nIncome := %Income%`nAttackSpider := %AttackSpider%`nHumanFormAttacker := %HumanFormAttacker%`nAttackbot := %Attackbot%`nDefenseSpider := %DefenseSpider%`nHumanFormDefender := %HumanFormDefender%`nDefensebot := %Defensebot%`nMiningBot := %MiningBot%`nInfiltrationUnits := %InfiltrationUnits%`nCovertInfiltratorBot := %CovertInfiltratorBot%`nGenericSpider := %GenericSpider%`nTotalFightingForce := %TotalFightingForce%


Sendinput ^w
sleep 1000
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

TurnRNG := (RandomNo+NextTurn) 
Timer := (TurnRNG*60000)
msgbox, 0, Sleeping, Run done!`n Next turn is in %NextTurn% minutes. But I shall be sleeping for %TurnRNG% mins, 5
Sleep %Timer%
GoTo BaseLevel
sleep 2000
return

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Functions
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Functions
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Functions
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Functions
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    OpenAndCheck:
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;


OpenAndCheck:
runwait %address%
sleep 1000
loop, 10
{
WinGet, active_id, ID, A
WinGet, process_name, ProcessName, A
WinGetTitle, this_title, ahk_id %active_id%

ifinstring, this_title, %Address%
	{
	break
	}
else
{
	sleep 1000
	if a_Index = 10
	{
		if CheckSubCount = 2
		{
		sendinput ^w
		{
		EmailSubj = Error
		EmailBody = Problem when trying to load the %address%`n`nreturning to base level.`n`nCurrent messages; %Inbox%
		GoSub SendEmail
		Sleep 500
		Goto BaseLevel
		sleep 1000
		}
		}

		CheckSubCount ++
		sendinput ^w
		GoSub OpenAndCheck
	}
}
}
return

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    CheckLoadedCorrectly:
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

CheckLoadedCorrectly:

If FailLoadedCount >= 3
	{
		{
		EmailSubj = Error
		EmailBody = Problem when trying to verify page load on page %address%`n`nreturning to base level.`n`nCurrent messages; %Inbox%
		GoSub SendEmail
		Sleep 500
		Goto BaseLevel
		sleep 1000
		}
	}

loop, 5
{
clipboard = ""
ClipWait, 1
sendinput ^a
sleep 200
sendinput ^c
sleep 500
ClipWait, 1
sendinput {tab}
StringSplit, MyArray, clipboard, `r
x := Myarray0 - 2
if x < 0
x := 0
KingdomGames = % MyArray%x%


IfNotInString, MyArray2, Era 39 reset
	{
	sleep 500
	if a_Index = 5
		{
		FailLoadedCount ++
		sleep 500
		GoSub CheckLoadedCorrectly
		}
	continue
	}
IfNotInString, KingdomGames, Brought to you by Kingdom Games Ltd
	{
	sleep 500
	if a_Index = 5
		{
		FailLoadedCount ++
		sleep 500
		GoSub CheckLoadedCorrectly
		}
	continue
	}
else
	{
;		msgbox Both checks OK
		break
	}
}

sleep 4000
return

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    SendEmail:
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;


SendEmail:
try
{
pmsg 			:= ComObjCreate("CDO.Message")
pmsg.From 		:= """Loki"" <EMAIL@Email.com>" ;;removed
pmsg.To 		:= "EMAIL" ;;removed
pmsg.BCC 		:= ""   ; Blind Carbon Copy, Invisable for all, same syntax as CC
pmsg.CC 		:= ""
pmsg.Subject 	:= EmailSUbj

;You can use either Text or HTML body like
pmsg.TextBody 	:= EmailBody
;OR
;pmsg.HtmlBody := "<html><head><title>Hello</title></head><body><h2>Hello</h2><p>Testing!</p></body></html>"


sAttach   		:= "" ; can add multiple attachments, the delimiter is |

fields := Object()
fields.smtpserver   := "smtp.gmail.com" ; specify your SMTP server
fields.smtpserverport     := 25 ; 465
fields.smtpusessl      := True ; False
fields.sendusing     := 2   ; cdoSendUsingPort
fields.smtpauthenticate     := 1   ; cdoBasic
fields.sendusername := "EMAIL@email.com" ;;removed
fields.sendpassword := "PASSWORD" ;;removed
fields.smtpconnectiontimeout := 60
schema := "http://schemas.microsoft.com/cdo/configuration/"


pfld :=   pmsg.Configuration.Fields

For field,value in fields
	pfld.Item(schema . field) := value
pfld.Update()

Loop, Parse, sAttach, |, %A_Space%%A_Tab%
  pmsg.AddAttachment(A_LoopField)
pmsg.Send()
}
catch e
{
GoTo BaseLevel
}
return
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    You've Got A Message
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

GotMessage:

sleep 1000
Address = http://quantumgate.gatewars.com/inbox.php
CheckSubCount := 0
GoSub OpenAndCheck
FailLoadedCount := 0
GoSub CheckLoadedCorrectly

sleep 1000

Loop %NewMessages%
{
	StartPoint := 45 + a_index

	StringReplace, MyArray%StartPoint%, MyArray%StartPoint%, %A_SPACE%,, All
	StringSplit, NewArray, MyArray%StartPoint%, %A_Tab%

	Sender%a_index% := NewArray1
	Subject%a_index% := NewArray3
	Time%a_index% := NewArray4
}


sleep 2000

loop 26
{
	SendInput {tab}
	sleep 100
}
sleep 2000

loop %NewMessages%
{
	loop 6
		{
			SendInput {tab}
			sleep 100
		}
	sleep 1000
	SendInput ^{enter}
}

loop %newmessages%
{
	sleep 2000
	sendinput ^{tab}
	sleep 2000
	sendinput ^a
	sleep 1000
	sendinput ^c
	clipwait, 1

	sleep 1000
	BigString := clipboard
	StringGetPos, NeedleStart, BigString, Message text:
	StringGetPos, NeedleEnd, BigString, reply delete save Blacklist Sender
	Start:= NeedleStart        
	End:= NeedleEnd 
	Length := End - Start
	StringMid, MessageContent, BigString, Start, Length
	message%a_index% := MessageContent
	clipboard = ""
}

sleep 2000
sendinput ^w
sleep 200
loop %NewMessage%
{
sendinput ^w
}

Loop %NewMessages%
{
Sender := Sender%A_index%
Time := Time%A_index%
Subject := Subject%A_index%
Message := Message%A_Index%
NewMessage%A_Index% = Message %A_Index%`r`n%Sender%`r`nSent- %Time%`r`n`r`n%Subject%`r`n%Message%
}

;Loop %NewMessages%
;{
;msgbox % NewMessage%A_Index%
;}

EmailSubj = %NewMessages% Messages received!
EmailBody = %NewMessage1%`r`n%NewMessage2%`r`n%NewMessage3%`r`n%NewMessage4%`r`n%NewMessage5%
GoSub SendEmail
sleep 2000

return
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;    Quit with ESC
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

Escape::
run autoInUse.ahk
Sleep 2000
exitapp
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
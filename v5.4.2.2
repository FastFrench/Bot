#RequireAdmin

#AutoIt3Wrapper_UseX64=y

$sBotTitle = "COC Bot v5.4.2.2"

DirCreate(@ScriptDir & "\Loots\")
DirCreate(@ScriptDir & "\logs\")

If _Singleton($sBotTitle, 1) = 0 Then
	MsgBox(0, "", "Bot is already running.")
	Exit
EndIf

#include <ButtonConstants.au3>
#include <ComboConstants.au3>
#include <EditConstants.au3>
#include <FileConstants.au3>
#include <GUIConstantsEx.au3>
#include <GuiStatusBar.au3>
#include <GUIEdit.au3>
#include <GUIComboBox.au3>
#include <StaticConstants.au3>
#include <TabConstants.au3>
#include <WindowsConstants.au3>
#include <WinAPIProc.au3>
#include <ScreenCapture.au3>
#include <Date.au3>
#include <Misc.au3>
#include <File.au3>
#include <TrayConstants.au3>
#include <GUIMenu.au3>
#include <ColorConstants.au3>
#include <GDIPlus.au3>
#include <InetConstants.au3>

Opt("GUIOnEventMode", 1)
Opt("MouseClickDelay", 10)
Opt("MouseClickDownDelay", 10)

#Region ##### LICENSE #####
If Not FileExists(@ScriptDir & "\License.txt") Then
	$license = InetGet("http://www.gnu.org/licenses/gpl-3.0.txt", @ScriptDir & "\License.txt", $INET_FORCEBYPASS, $INET_DOWNLOADBACKGROUND)
	$licensewait = 0
	Do
		Sleep(100)
		$licensewait += 1
	Until InetGetInfo($license, $INET_DOWNLOADCOMPLETE) Or $licensewait = 50
	InetClose($license)
EndIf
#EndRegion ##### LICENSE #####

#Region #####Global Variables#####
Global $Compiled
If @Compiled Then
	$Compiled = "Executable"
Else
	$Compiled = "Au3 Script"
EndIf

Global $hBitmap; Image for pixel functions

Global $config = @ScriptDir & "\config.ini"
Global $sLogPath ; `Will create a new log file every time the start button is pressed
Global $hLogFileHandle
Global $Restart = False
Global $RunState = False

Global $cmbTroopComp ;For Event change on ComboBox Troop Compositions
Global $iCollectCounter = 0 ; Collect counter, when reaches $COLLECTATCOUNT, it will collect
Global $COLLECTATCOUNT = 5 ; Run Collect() after this amount of times before actually collect
;---------------------------------------------------------------------------------------------------
Global $BSpos[2] ; Inside BlueStacks positions relative to the screen
Global $CtrlHandle ; BlueStacks control handle
;---------------------------------------------------------------------------------------------------
;Search Settings
Global $searchGold, $searchElixir, $searchDark, $searchTrophy ;Resources of bases when searching
Global $MinGold, $MinElixir, $MinDark, $MinTrophy ; Minimum Resources conditions
Global $chkConditions[3] ;Conditions (meet gold...)

Global $SearchCount = 0 ;Number of searches
;Attack Settings
Global $TopLeft[5][2] = [[110, 250], [170, 205], [234, 162], [296, 115], [368, 66]]
Global $TopRight[5][2] = [[480, 63], [540, 104], [589, 146], [655, 190], [717, 240]]
Global $BottomLeft[5][2] = [[79, 342], [142, 389], [210, 446], [276, 492], [339, 539]]
Global $BottomRight[5][2] = [[523, 537], [595, 484], [654, 440], [715, 393], [779, 344]]

Global $atkTroops[7][2] ;7 Slots of troops -  Name,Amount
Global $icmbAlgorithm ;Algorithm to use when attacking

Global $fullArmy ;Check for full army or not
Global $deploySettings ;Method of deploy found in attack settings

Global $KingAttack[3] ;King attack settings
Global $QueenAttack[3] ;Queen attack settings

Global $checkKPower = -1 ;Check for King and Queen activate power
Global $checkQPower = -1
Global $delayActivateKQ = 15000 ;Delay before activating KQ
Global $iradAttackMode ;Attack mode, 0 1 2
;Donate Settings

;Troop Settings
Global $icmbTroopComp ;Troop Composition

Global $barrackPos[4][2] ;Positions of each barracks
Global $barrackTroop[4] ;Barrack troop set

Global $CCPos[2] = [-1, -1] ;Position of clan castle
Global $TextRequest
Global $CheckRequest

Global $TrapPos[2] = [-1, -1] ;Position of trap

;General Settings
Global $botPos[2] ; Position of bot used for Hide function
Global $frmBotPosX ; Position X of the GUI
Global $frmBotPosY ; Position Y of the GUI
Global $Hide = False ; If hidden or not

Global $itxtMaxTrophy ; Max trophy before drop trophy
Global $ichkBackground ; Background mode enabled disabled
Global $collectorPos[17][2] ;Positions of each collectors

;checkDeadBase Variables:-------------===========================
Global $Title = "BlueStacks App Player"
Global $HWnD = WinGetHandle(WinGetTitle($Title))
Global $Tolerance = 65

Global $ZC = 0, $ZombieCount = 0, $E
Global $ZombieFileSets = 3 ;Variant Image to use organized as per Folder
;===================================================
Global $ZSExclude = 3 ;Set to 0 to include Elixir Lvl 6, 1 to include lvl 7 and so on..
;===================================================

Global $Lx[4] = [0, 400, 0, 400]
Global $Ly[4] = [0, 0, 265, 265]
Global $Rx[4] = [460, 860, 400, 860]
Global $Ry[4] = [325, 325, 590, 590]


Global $Area[11][4], $IS_x[11][4], $IS_y[11][4], $E[5][11]

$E[0][0] = @ScriptDir & "\images\ELIX1\E6F9.bmp"
$E[0][1] = @ScriptDir & "\images\ELIX1\E7F9.bmp"
$E[0][2] = @ScriptDir & "\images\ELIX1\E8F9.bmp"
$E[0][3] = @ScriptDir & "\images\ELIX1\E9F9.bmp"
$E[0][4] = @ScriptDir & "\images\ELIX1\E10F8.bmp"
$E[0][5] = @ScriptDir & "\images\ELIX1\E10F9.bmp"
$E[0][6] = @ScriptDir & "\images\ELIX1\E11F8.bmp"
$E[0][7] = @ScriptDir & "\images\ELIX1\E11F9.bmp"
$E[0][8] = @ScriptDir & "\images\ELIX1\E12F7.bmp"
$E[0][9] = @ScriptDir & "\images\ELIX1\E12F8.bmp"
$E[0][10] = @ScriptDir & "\images\ELIX1\E12F9.bmp"

$E[1][0] = @ScriptDir & "\images\ELIX2\E6F9.bmp"
$E[1][1] = @ScriptDir & "\images\ELIX2\E7F9.bmp"
$E[1][2] = @ScriptDir & "\images\ELIX2\E8F9.bmp"
$E[1][3] = @ScriptDir & "\images\ELIX2\E9F9.bmp"
$E[1][4] = @ScriptDir & "\images\ELIX2\E10F8.bmp"
$E[1][5] = @ScriptDir & "\images\ELIX2\E10F9.bmp"
$E[1][6] = @ScriptDir & "\images\ELIX2\E11F8.bmp"
$E[1][7] = @ScriptDir & "\images\ELIX2\E11F9.bmp"
$E[1][8] = @ScriptDir & "\images\ELIX2\E12F7.bmp"
$E[1][9] = @ScriptDir & "\images\ELIX2\E12F8.bmp"
$E[1][10] = @ScriptDir & "\images\ELIX2\E12F9.bmp"

$E[2][0] = @ScriptDir & "\images\ELIX3\E6F9.bmp"
$E[2][1] = @ScriptDir & "\images\ELIX3\E7F9.bmp"
$E[2][2] = @ScriptDir & "\images\ELIX3\E8F9.bmp"
$E[2][3] = @ScriptDir & "\images\ELIX3\E9F9.bmp"
$E[2][4] = @ScriptDir & "\images\ELIX3\E10F8.bmp"
$E[2][5] = @ScriptDir & "\images\ELIX3\E10F9.bmp"
$E[2][6] = @ScriptDir & "\images\ELIX3\E11F8.bmp"
$E[2][7] = @ScriptDir & "\images\ELIX3\E11F9.bmp"
$E[2][8] = @ScriptDir & "\images\ELIX3\E12F7.bmp"
$E[2][9] = @ScriptDir & "\images\ELIX3\E12F8.bmp"
$E[2][10] = @ScriptDir & "\images\ELIX3\E12F9.bmp"

$E[3][0] = @ScriptDir & "\images\ELIX4\E6F9.bmp"
$E[3][1] = @ScriptDir & "\images\ELIX4\E7F9.bmp"
$E[3][2] = @ScriptDir & "\images\ELIX4\E8F9.bmp"
$E[3][3] = @ScriptDir & "\images\ELIX4\E9F9.bmp"
$E[3][4] = @ScriptDir & "\images\ELIX4\E10F8.bmp"
$E[3][5] = @ScriptDir & "\images\ELIX4\E10F9.bmp"
$E[3][6] = @ScriptDir & "\images\ELIX4\E11F8.bmp"
$E[3][7] = @ScriptDir & "\images\ELIX4\E11F9.bmp"
$E[3][8] = @ScriptDir & "\images\ELIX4\E12F7.bmp"
$E[3][9] = @ScriptDir & "\images\ELIX4\E12F8.bmp"
$E[3][10] = @ScriptDir & "\images\ELIX4\E12F9.bmp"

$E[4][0] = @ScriptDir & "\images\ELIX5\E6F9.bmp"
$E[4][1] = @ScriptDir & "\images\ELIX5\E7F9.bmp"
$E[4][2] = @ScriptDir & "\images\ELIX5\E8F9.bmp"
$E[4][3] = @ScriptDir & "\images\ELIX5\E9F9.bmp"
$E[4][4] = @ScriptDir & "\images\ELIX5\E10F8.bmp"
$E[4][5] = @ScriptDir & "\images\ELIX5\E10F9.bmp"
$E[4][6] = @ScriptDir & "\images\ELIX5\E11F8.bmp"
$E[4][7] = @ScriptDir & "\images\ELIX5\E11F9.bmp"
$E[4][8] = @ScriptDir & "\images\ELIX5\E12F7.bmp"
$E[4][9] = @ScriptDir & "\images\ELIX5\E12F8.bmp"
$E[4][10] = @ScriptDir & "\images\ELIX5\E12F9.bmp"

#EndRegion #####Global Variables#####
;---------------------------------------------------

#Region ### START Koda GUI section ###
$frmBot = GUICreate($sBotTitle, 417, 392, 207, 158)
$tabMain = GUICtrlCreateTab(8, 8, 401, 355)
$pageGeneral = GUICtrlCreateTabItem("General")
$txtLog = GUICtrlCreateEdit("", 16, 40, 385, 240, BitOR($ES_AUTOVSCROLL, $ES_NOHIDESEL, $ES_READONLY, $ES_WANTRETURN, $WS_VSCROLL))
GUICtrlSetBkColor(-1, 0xFFFFFF)
$Controls = GUICtrlCreateGroup("Controls", 16, 290, 185, 65)
$btnStart = GUICtrlCreateButton("Start", 30, 314, 75, 25)
GUICtrlSetOnEvent(-1, "btnStart")
$btnStop = GUICtrlCreateButton("Stop", 30, 314, 75, 25)
GUICtrlSetOnEvent(-1, "btnStop")
GUICtrlSetState(-1, $GUI_HIDE)
$btnHide = GUICtrlCreateButton("Hide", 110, 314, 75, 25)
GUICtrlSetOnEvent(-1, "btnHide")
GUICtrlSetState(-1, $GUI_DISABLE)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$otherSettings = GUICtrlCreateGroup("Other Settings", 208, 290, 185, 65)
$lblMaxTrophy = GUICtrlCreateLabel("Max Trophy :", 230, 310, 66, 17)
GUICtrlSetLimit(-1, 4)
$txtMaxTrophy = GUICtrlCreateInput("3000", 298, 307, 71, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER, $ES_NUMBER))
GUICtrlSetTip(-1, "Bot will lose tropies if your trophy is greater than this.")
$chkBackground = GUICtrlCreateCheckbox("Background Mode", 245, 330, 115, 17)
GUICtrlSetOnEvent(-1, "chkBackground")
GUICtrlSetState(-1, $GUI_CHECKED)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$pageSearchSetting = GUICtrlCreateTabItem("Search Settings")
$btnSearchMode = GUICtrlCreateButton("Search Mode", 24, 327, 368, 25)
GUICtrlSetOnEvent(-1, "btnSearchMode")
GUICtrlSetTip(-1, "Does not attack. Searches for base that meets conditions.")
$Conditions = GUICtrlCreateGroup("Conditions", 16, 40, 193, 185)
$chkMeetDE = GUICtrlCreateCheckbox("Meet Dark Elixir", 40, 88, 97, 17)
$chkMeetTrophy = GUICtrlCreateCheckbox("Meet Trophy Count", 40, 112, 113, 17)
$chkMeetGxE = GUICtrlCreateCheckbox("Meet Gold and Elixir", 40, 64, 113, 17)
GUICtrlSetState(-1, $GUI_CHECKED)
$lblConditions = GUICtrlCreateLabel("Check the boxes that you want to meet. The bot will stop at a base when it meets the conditions. If all unchecked, bot will stop if gold or elixir that is met.", 26, 143, 172, 72, $SS_CENTER)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$Resources = GUICtrlCreateGroup("Resources", 208, 40, 193, 185)
$lblMinGold = GUICtrlCreateLabel("Minimum Gold: ", 216, 64, 76, 17)
$lblMinElixir = GUICtrlCreateLabel("Minimum Elixir:", 216, 88, 72, 17)
$lblMinDarkElixir = GUICtrlCreateLabel("Minimum Dark Elixir:", 216, 112, 98, 17)
$lblMinTrophy = GUICtrlCreateLabel("Minimum Trophy Count:", 216, 136, 115, 17)
$txtMinGold = GUICtrlCreateInput("80000", 330, 62, 61, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER, $ES_NUMBER))
GUICtrlSetLimit(-1, 6)
$txtMinElixir = GUICtrlCreateInput("80000", 330, 86, 61, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER, $ES_NUMBER))
GUICtrlSetLimit(-1, 6)
$txtMinDarkElixir = GUICtrlCreateInput("0", 330, 110, 61, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER, $ES_NUMBER))
GUICtrlSetLimit(-1, 6)
$txtMinTrophy = GUICtrlCreateInput("0", 330, 134, 61, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER, $ES_NUMBER))
GUICtrlSetLimit(-1, 2)
$lblResources = GUICtrlCreateLabel("Bot will stop when a base is found with resources higher or equal to the minimum resources.", 220, 164, 168, 51, $SS_CENTER)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$OtherSearchSettings = GUICtrlCreateGroup("Other Seach Settings", 15, 225, 385, 95)
$chkAlertSearch = GUICtrlCreateCheckbox("Alert when Base Found", 30, 250, 132, 17)
GUICtrlSetState(-1, $GUI_CHECKED)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$pageAttackSettings = GUICtrlCreateTabItem("Attack Settings")
$WeakBaseSettings = GUICtrlCreateGroup("Weak Base Settings", 15, 35, 130, 230)
$lblMortar = GUICtrlCreateLabel("Max Mortar Lvl:", 20, 58, 77, 17)
$cmbMortar = GUICtrlCreateCombo("", 100, 55, 35, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "0|1|2|3|4|5|6|7|8", "5")
GUICtrlSetState(-1, $GUI_DISABLE)
$lblWizardTower = GUICtrlCreateLabel("Wiz Tower Lvl:", 20, 83, 75, 17)
$cmbWizTower = GUICtrlCreateCombo("", 100, 80, 35, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "0|1|2|3|4|5|6|7|8", "4")
GUICtrlSetState(-1, $GUI_DISABLE)
$lblCannon = GUICtrlCreateLabel("Cannon Lvl:", 20, 108, 61, 17)
$lblArcher = GUICtrlCreateLabel("Archer Lvl:", 20, 133, 55, 17)
$chkWithKing = GUICtrlCreateCheckbox("Attack their King", 20, 180, 112, 17, BitOR($GUI_SS_DEFAULT_CHECKBOX, $BS_RIGHTBUTTON))
GUICtrlSetState(-1, $GUI_CHECKED)
GUICtrlSetState(-1, $GUI_DISABLE)
$chkWithQueen = GUICtrlCreateCheckbox("Attack their Queen", 20, 200, 112, 17, BitOR($GUI_SS_DEFAULT_CHECKBOX, $BS_RIGHTBUTTON))
GUICtrlSetState(-1, $GUI_DISABLE)
$cmbCannon = GUICtrlCreateCombo("", 100, 105, 35, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "0|1|2|3|4|5|6|7|8|9|10|11|12|13", "8")
GUICtrlSetState(-1, $GUI_DISABLE)
$cmbArcher = GUICtrlCreateCombo("", 100, 130, 35, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "0|1|2|3|4|5|6|7|8|9|10|11|12|13", "8")
GUICtrlSetState(-1, $GUI_DISABLE)
$lblWeakDescription = GUICtrlCreateLabel("Bot will attack bases that meet requirement.", 17, 225, 125, 32, $SS_CENTER)
$lblxBow = GUICtrlCreateLabel("X-Bow Lvl:", 20, 158, 55, 17)
$cmbxBow = GUICtrlCreateCombo("", 100, 155, 35, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "0|1|2|3|4|5|6|7|8|9|10|11|12|13", "0")
GUICtrlSetState(-1, $GUI_DISABLE)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$AttackMode = GUICtrlCreateGroup("Attack Mode", 150, 35, 250, 115)
$radDeadBases = GUICtrlCreateRadio("Dead Bases - Meets condition, full collectors", 155, 55, 238, 17)
$radWeakBases = GUICtrlCreateRadio("Weak Bases - Meets condition and able 50%", 155, 85, 228, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$radAllBases = GUICtrlCreateRadio("All Bases - Attack all that meets search.", 155, 115, 228, 17)
GUICtrlSetState(-1, $GUI_CHECKED)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$HeroesSettings = GUICtrlCreateGroup("Royals Settings", 150, 155, 250, 110)
$chkKingAttackDeadBases = GUICtrlCreateCheckbox("Atk Dead Bases", 165, 195, 97, 17)
$chkKingAttackWeakBases = GUICtrlCreateCheckbox("Atk Weak Bases", 165, 215, 97, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$chkKingAttackAllBases = GUICtrlCreateCheckbox("Atk All Bases", 165, 235, 97, 17)
$lblKingSettings = GUICtrlCreateLabel("King Settings:", 165, 175, 69, 17)
$lblQueenSettings = GUICtrlCreateLabel("Queen Settings:", 285, 175, 80, 17)
$chkQueenAttackDeadBases = GUICtrlCreateCheckbox("Atk Dead Bases", 285, 195, 97, 17)
$chkQueenAttackWeakBases = GUICtrlCreateCheckbox("Atk Weak Bases", 285, 215, 97, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$chkQueenAttackAllBases = GUICtrlCreateCheckbox("Atk All Bases", 285, 235, 97, 17)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$deploySettings = GUICtrlCreateGroup("Deploy Settings", 15, 270, 385, 85)
$chkAttackTH = GUICtrlCreateCheckbox("Attack Townhall (Outside)", 250, 320, 142, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$cmbDeploy = GUICtrlCreateCombo("", 30, 290, 360, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "Attack on two sides, penetrates through base|Attack on three sides, gets outer and some inside of base|Attack on all sides equally, gets most of outer base", "Attack on all sides equally, gets most of outer base")
$cmbAlgorithm = GUICtrlCreateCombo("", 30, 320, 215, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "Barbarians + Archers|Use all troops", "Barbarians + Archers") ;"Archers|Barbarians|Goblins|Barbarians + Archers|Barb + Arch + Goblin + Giant|Barb + Arch + Giant|Barb + Arch + Goblin|Barb + Arch + Goblin + Giant + Wallbreakers|Use Barracks"
GUICtrlCreateGroup("", -99, -99, 1, 1)
$pageDonateSettings = GUICtrlCreateTabItem("Donate Settings")
$Donation = GUICtrlCreateGroup("", 15, 30, 385, 325)
$Barbarians = GUICtrlCreateGroup("Barbarians", 20, 70, 120, 235)
$Checkbox1 = GUICtrlCreateCheckbox("Donate to All", 30, 95, 97, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$txtDonateBarbarians = GUICtrlCreateEdit("", 25, 120, 110, 179, BitOR($ES_WANTRETURN, $WS_VSCROLL))
GUICtrlSetData(-1, StringFormat("barbarians\r\nbarb\r\nany"))
GUICtrlSetState(-1, $GUI_DISABLE)
GUICtrlSetTip(-1, "Keywords for donating Barbarians")
GUICtrlCreateGroup("", -99, -99, 1, 1)
$Archers = GUICtrlCreateGroup("Archers", 148, 70, 120, 235)
$Checkbox2 = GUICtrlCreateCheckbox("Donate to All", 155, 95, 97, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$txtDonateArchers = GUICtrlCreateEdit("", 153, 120, 110, 179, BitOR($ES_WANTRETURN, $WS_VSCROLL))
GUICtrlSetData(-1, StringFormat("archers\r\narch\r\nany"))
GUICtrlSetState(-1, $GUI_DISABLE)
GUICtrlSetTip(-1, "Keywords for donating Archers")
GUICtrlCreateGroup("", -99, -99, 1, 1)
$Giants = GUICtrlCreateGroup("Giants", 275, 70, 120, 235)
$Checkbox3 = GUICtrlCreateCheckbox("Donate to All", 285, 95, 97, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$txtDonateGiants = GUICtrlCreateEdit("", 280, 120, 110, 179, BitOR($ES_WANTRETURN, $WS_VSCROLL))
GUICtrlSetData(-1, StringFormat("giants\r\ngiant\r\nany"))
GUICtrlSetState(-1, $GUI_DISABLE)
GUICtrlSetTip(-1, "Keywords for donating Giants")
GUICtrlCreateGroup("", -99, -99, 1, 1)
$chkDonateGiants = GUICtrlCreateCheckbox("Donate Giants", 275, 305, 97, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$chkDonateArchers = GUICtrlCreateCheckbox("Donate Archers", 149, 305, 97, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$chkDonateBarbarians = GUICtrlCreateCheckbox("Donate Barbarians", 20, 305, 112, 17)
GUICtrlSetState(-1, $GUI_DISABLE)
$chkRequest = GUICtrlCreateCheckbox("Request for :", 30, 45, 82, 17)
;GUICtrlSetState(-1, $GUI_CHECKED)
$txtRequest = GUICtrlCreateInput("any", 115, 45, 276, 21)
;GUICtrlSetState(-1, $GUI_DISABLE)
GUICtrlSetTip(-1, "Request for input.")
$btnLocateClanCastle = GUICtrlCreateButton("Locate Clan Castle Manually", 25, 325, 365, 25)
;--
;GUICtrlSetState(-1, $GUI_DISABLE)
GUICtrlSetOnEvent(-1, "btnLocateClanClastle")
GUICtrlCreateGroup("", -99, -99, 1, 1)
$pageTroopSettings = GUICtrlCreateTabItem("Troop Settings")
$Barracks = GUICtrlCreateGroup("Troops", 20, 40, 185, 215)
$lblBarbarians = GUICtrlCreateLabel("Barbarians :", 30, 68, 60, 17)
$lblArchers = GUICtrlCreateLabel("Archers :", 30, 93, 46, 17)
$lblGoblins = GUICtrlCreateLabel("Goblins :", 30, 118, 45, 17)
$txtBarbarians = GUICtrlCreateInput("30", 115, 65, 56, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER, $ES_NUMBER))
GUICtrlSetState(-1, $GUI_DISABLE)
$txtArchers = GUICtrlCreateInput("60", 115, 90, 56, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER, $ES_NUMBER))
GUICtrlSetState(-1, $GUI_DISABLE)
$txtGoblins = GUICtrlCreateInput("10", 115, 115, 56, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER, $ES_NUMBER))
GUICtrlSetState(-1, $GUI_DISABLE)
$lblPercentBarbarians = GUICtrlCreateLabel("%", 175, 68, 12, 17)
$lblPercentArchers = GUICtrlCreateLabel("%", 175, 93, 12, 17)
$lblPercentGoblins = GUICtrlCreateLabel("%", 175, 118, 12, 17)
$lblBarracks = GUICtrlCreateLabel("Must equal 100% to fully distribute the troops with maximum amount efficiency. Bot will use this if custom troops is selected", 40, 175, 140, 67, $SS_CENTER)
$cmbTroopComp = GUICtrlCreateCombo("", 45, 145, 131, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUISetOnEvent(-1, "cmbTroopComp_Change")
GUICtrlSetData(-1, "B.Arch|Use Barracks", "Use Barracks") ;"Archers|Barbarians|Goblins|B.Arch|B.A.G.G.|B.A.Giant|B.A.Goblin|B.A.G.G.Wall|Use Barracks|Custom Troops"
GUICtrlCreateGroup("", -99, -99, 1, 1)
$OtherTroops = GUICtrlCreateGroup("Other Troops", 210, 40, 185, 85)
$lblGiants = GUICtrlCreateLabel("Number of Giants:", 215, 68, 89, 17)
$lblWallBreakers = GUICtrlCreateLabel("Number of Wall Breakers:", 215, 93, 125, 17)
$txtNumGiants = GUICtrlCreateInput("4", 340, 65, 46, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER))
GUICtrlSetState(-1, $GUI_DISABLE)
$txtNumWallbreakers = GUICtrlCreateInput("4", 340, 90, 46, 21, BitOR($GUI_SS_DEFAULT_INPUT, $ES_CENTER))
GUICtrlSetState(-1, $GUI_DISABLE)
GUICtrlCreateGroup("", -99, -99, 1, 1)
$BarrackGroup = GUICtrlCreateGroup("Barracks", 210, 130, 185, 125)
$lblBarrack1 = GUICtrlCreateLabel("Barrack 1:", 220, 153, 53, 17)
$lblBarrack2 = GUICtrlCreateLabel("Barrack 2:", 220, 178, 53, 17)
$lblBarrack3 = GUICtrlCreateLabel("Barrack 3:", 220, 203, 53, 17)
$lblBarrack4 = GUICtrlCreateLabel("Barrack 4:", 220, 228, 53, 17)
$cmbBarrack1 = GUICtrlCreateCombo("", 275, 150, 110, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "Barbarians|Archers", "Barbarians") ; "Barbarians|Archers|Giants|Goblins"
$cmbBarrack2 = GUICtrlCreateCombo("", 275, 175, 110, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "Barbarians|Archers", "Barbarians") ; "Barbarians|Archers|Giants|Goblins"
$cmbBarrack3 = GUICtrlCreateCombo("", 275, 200, 110, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "Barbarians|Archers", "Archers") ; "Barbarians|Archers|Giants|Goblins"
$cmbBarrack4 = GUICtrlCreateCombo("", 275, 225, 110, 25, BitOR($CBS_DROPDOWNLIST, $CBS_AUTOHSCROLL))
GUICtrlSetData(-1, "Barbarians|Archers", "Archers") ; "Barbarians|Archers|Giants|Goblins"
GUICtrlCreateGroup("", -99, -99, 1, 1)
$OtherBarrackSettings = GUICtrlCreateGroup("Other Settings", 20, 255, 375, 100)
$btnLocateBarracks = GUICtrlCreateButton("Locate Barracks Manually", 30, 320, 355, 25)
GUICtrlSetOnEvent(-1, "btnLocateBarracks")
$btnLocateCollectors = GUICtrlCreateButton("Locate Collectors Manually", 30, 280, 355, 25)
GUICtrlSetOnEvent(-1, "btnLocateCollectors")
GUICtrlCreateGroup("", -99, -99, 1, 1)
GUICtrlCreateTabItem("")
$statLog = _GUICtrlStatusBar_Create($frmBot)
_GUICtrlStatusBar_SetSimple($statLog)
_GUICtrlStatusBar_SetText($statLog, "Status : Idle")
GUISetState(@SW_SHOW)
#EndRegion ### END Koda GUI section ###
;---------------------------------------------------
If FileExists($config) Then
	readConfig()
	applyConfig()
EndIf

GUIRegisterMsg($WM_COMMAND, "GUIControl")
GUIRegisterMsg($WM_SYSCOMMAND, "GUIControl")
;---------------------------------------------------
#Region ### Button Section ###
Func GUIControl($hWind, $iMsg, $wParam, $lParam)
	Local $nNotifyCode = BitShift($wParam, 16)
	Local $nID = BitAND($wParam, 0x0000FFFF)
	Local $hCtrl = $lParam
	#forceref $hWind, $iMsg, $wParam, $lParam
	Switch $iMsg
		Case 273
			Switch $nID
				Case $GUI_EVENT_CLOSE
					If WinExists("BlueStacks App Player") Then
						EnableBS($HWnD, $SC_MINIMIZE)
						EnableBS($HWnD, $SC_CLOSE)
						EnableBS($HWnD, $SC_MOVE)
					EndIf
					_GDIPlus_Shutdown()
					SaveConfig()
					Exit
				Case $btnStop
					If $RunState Then btnStop()
				Case $btnHide
					If $RunState Then btnHide()
				Case $cmbTroopComp
					cmbTroopComp()
			EndSwitch
		Case 274
			Switch $wParam
				Case 0xf060
					If WinExists("BlueStacks App Player") Then
						EnableBS($HWnD, $SC_MINIMIZE)
						EnableBS($HWnD, $SC_CLOSE)
						EnableBS($HWnD, $SC_MOVE)
					EndIf
					_GDIPlus_Shutdown()
					SaveConfig()
					Exit
			EndSwitch
	EndSwitch
	Return $GUI_RUNDEFMSG
EndFunc   ;==>GUIControl

While 1
	_ReduceMemory()
	_ReduceMemory(ProcessExists("HD-Frontend.exe"))
	Sleep(10000)
WEnd

Func btnStart()
	_GDIPlus_Startup()
	CreateLogFile()

	SaveConfig()
	readConfig()
	applyConfig()

	_GUICtrlEdit_SetText($txtLog, "")

	If WinExists("BlueStacks App Player") Then
		DisableBS($HWnD, $SC_MINIMIZE)
		DisableBS($HWnD, $SC_CLOSE)
		DisableBS($HWnD, $SC_MOVE)
		If IsArray(ControlGetPos("BlueStacks App Player", "_ctl.Window", "[CLASS:BlueStacksApp; INSTANCE:1]")) Then
			Local $BSsize = [ControlGetPos("BlueStacks App Player", "_ctl.Window", "[CLASS:BlueStacksApp; INSTANCE:1]")[2], ControlGetPos("BlueStacks App Player", "_ctl.Window", "[CLASS:BlueStacksApp; INSTANCE:1]")[3]]
			If $BSsize[0] <> 860 Or $BSsize[1] <> 720 Then
				SetLog("BlueStacks is not set to 860x720!")
				SetLog("Download the '860x720.reg' file and run it, restart BlueStacks")
				SetLog("Download the '860x720.reg' here: http://ge.tt/6Twq4O72")
			Else
				WinActivate("BlueStacks App Player")
				;WinSetOnTop("BlueStacks App Player", "", 1)

				SetLog("~~~~Welcome to " & @ScriptName & "!~~~~")
				SetLog($Compiled & " running on " & @OSArch & " OS")
				SetLog("Bot is starting...")

				$RunState = True
				GUICtrlSetState($btnLocateBarracks, $GUI_DISABLE)
				GUICtrlSetState($btnSearchMode, $GUI_DISABLE)
				GUICtrlSetState($cmbTroopComp, $GUI_DISABLE)
				GUICtrlSetState($chkBackground, $GUI_DISABLE)
				GUICtrlSetState($btnLocateCollectors, $GUI_DISABLE)

				GUICtrlSetState($btnStart, $GUI_HIDE)
				GUICtrlSetState($btnStop, $GUI_SHOW)
				runBot()
			EndIf
		Else
			SetLog("Not in Game!")
		EndIf
	Else
		SetLog("BlueStacks was not found!")
	EndIf
EndFunc   ;==>btnStart

Func btnStop()
	If $RunState Then
		$RunState = False
		EnableBS($HWnD, $SC_MINIMIZE)
		EnableBS($HWnD, $SC_CLOSE)
		EnableBS($HWnD, $SC_MOVE)
		GUICtrlSetState($btnLocateBarracks, $GUI_ENABLE)
		GUICtrlSetState($btnSearchMode, $GUI_ENABLE)
		GUICtrlSetState($cmbTroopComp, $GUI_ENABLE)
		GUICtrlSetState($btnLocateCollectors, $GUI_ENABLE)
		GUICtrlSetState($chkBackground, $GUI_ENABLE)

		GUICtrlSetState($btnStart, $GUI_SHOW)
		GUICtrlSetState($btnStop, $GUI_HIDE)

		FileClose($hLogFileHandle)
		SetLog("Bot has stopped")
	EndIf
EndFunc   ;==>btnStop

Func btnLocateBarracks()
	$RunState = True
	While 1
		ZoomOut()
		LocateBarrack()
		ExitLoop
	WEnd
	$RunState = False
EndFunc   ;==>btnLocateBarracks

Func btnLocateClanClastle()
	$RunState = True
	While 1
		ZoomOut()
		LocateClanClastle()
		ExitLoop
	WEnd
	$RunState = False
EndFunc   ;==>btnLocateClanClastle

Func btnSearchMode()
	While 1
		GUICtrlSetState($btnStart, $GUI_HIDE)
		GUICtrlSetState($btnStop, $GUI_SHOW)

		GUICtrlSetState($btnLocateBarracks, $GUI_DISABLE)
		GUICtrlSetState($btnSearchMode, $GUI_DISABLE)
		GUICtrlSetState($cmbTroopComp, $GUI_DISABLE)
		GUICtrlSetState($chkBackground, $GUI_DISABLE)
		GUICtrlSetState($btnLocateCollectors, $GUI_DISABLE)

		$RunState = True
		VillageSearch()
		$RunState = False

		GUICtrlSetState($btnStart, $GUI_SHOW)
		GUICtrlSetState($btnStop, $GUI_HIDE)

		GUICtrlSetState($btnLocateBarracks, $GUI_ENABLE)
		GUICtrlSetState($btnSearchMode, $GUI_ENABLE)
		GUICtrlSetState($cmbTroopComp, $GUI_ENABLE)
		GUICtrlSetState($chkBackground, $GUI_ENABLE)
		GUICtrlSetState($btnLocateCollectors, $GUI_ENABLE)
		ExitLoop
	WEnd
EndFunc   ;==>btnSearchMode

Func btnHide()
	If $Hide = False Then
		GUICtrlSetData($btnHide, "Show")
		$botPos[0] = WinGetPos("BlueStacks App Player")[0]
		$botPos[1] = WinGetPos("BlueStacks App Player")[1]
		WinMove("BlueStacks App Player", "", -32000, -32000)
		$Hide = True
	Else
		GUICtrlSetData($btnHide, "Hide")

		If $botPos[0] = -32000 Then
			WinMove("BlueStacks App Player", "", 0, 0)
			WinActivate("BlueStacks App Player")
		Else
			WinMove("BlueStacks App Player", "", $botPos[0], $botPos[1])
			WinActivate("BlueStacks App Player")
		EndIf
		$Hide = False
	EndIf
EndFunc   ;==>btnHide

Func cmbTroopComp()
	If _GUICtrlComboBox_GetCurSel($cmbTroopComp) <> $icmbTroopComp Then
		$icmbTroopComp = _GUICtrlComboBox_GetCurSel($cmbTroopComp)
		SetComboTroopComp()
	EndIf
EndFunc   ;==>cmbTroopComp

Func SetComboTroopComp()
	Switch _GUICtrlComboBox_GetCurSel($cmbTroopComp)
		Case 0
			GUICtrlSetState($cmbBarrack1, $GUI_DISABLE)
			GUICtrlSetState($cmbBarrack2, $GUI_DISABLE)
			GUICtrlSetState($cmbBarrack3, $GUI_DISABLE)
			GUICtrlSetState($cmbBarrack4, $GUI_DISABLE)

			GUICtrlSetData($txtBarbarians, "50")
			GUICtrlSetData($txtArchers, "50")
			GUICtrlSetData($txtGoblins, "0")

			GUICtrlSetData($txtNumGiants, "0")
			GUICtrlSetData($txtNumWallbreakers, "0")
		Case 1
			GUICtrlSetState($cmbBarrack1, $GUI_ENABLE)
			GUICtrlSetState($cmbBarrack2, $GUI_ENABLE)
			GUICtrlSetState($cmbBarrack3, $GUI_ENABLE)
			GUICtrlSetState($cmbBarrack4, $GUI_ENABLE)
	EndSwitch
EndFunc   ;==>SetComboTroopComp

Func chkBackground()
	If GUICtrlRead($chkBackground) = $GUI_CHECKED Then
		$ichkBackground = 1
		GUICtrlSetState($btnHide, $GUI_ENABLE)
	Else
		$ichkBackground = 0
		GUICtrlSetState($btnHide, $GUI_DISABLE)
	EndIf
EndFunc   ;==>chkBackground

Func btnLocateCollectors()
	$RunState = True
	While 1
		ZoomOut()
		LocateCollectors()
		ExitLoop
	WEnd
	$RunState = False
EndFunc   ;==>btnLocateCollectors

#EndRegion ### Button Section ###
;---------------------------------------------------
#Region ### General Functions ###
Func runBot() ;Bot that runs everything in order
	While 1
		_ReduceMemory()
		_ReduceMemory(ProcessExists("HD-Frontend.exe"))
		$Restart = False
		If _Sleep(1000) Then ExitLoop
		checkMainScreen()
		If _Sleep(1000) Then ExitLoop
		ZoomOut()
		If _Sleep(1000) Then ExitLoop
		ReArm()
		If _Sleep(1000) Then ExitLoop
		Train()
		If _Sleep(1000) Then ExitLoop
		RequestCC()
		If _Sleep(1000) Then ExitLoop
		Collect()
		If _Sleep(1000) Then ExitLoop
		Idle()
		If _Sleep(1000) Then ExitLoop
		AttackMain()
		If _Sleep(1000) Then ExitLoop
	WEnd
EndFunc   ;==>runBot

Func Idle() ;Sequence that runs until Full Army
	Local $TimeIdle = 0 ;In Seconds
	While 1
		If $fullArmy = False Then
			SetLog("~~~Waiting for full army~~~")
			While $fullArmy = False
				_ReduceMemory()
				Local $hTimer = TimerInit()
				If _Sleep(1000) Then ExitLoop
				checkMainScreen()
				If _Sleep(1000) Then ExitLoop
				ZoomOut()
				If _Sleep(30000) Then ExitLoop (2)
				If $iCollectCounter > $COLLECTATCOUNT Then ; This is prevent from collecting all the time which isn't needed anyway
					Collect()
					If _Sleep(1000) Or $RunState = False Then ExitLoop (2)
					$iCollectCounter = 0
				EndIf
				$iCollectCounter = $iCollectCounter + 1
				Train()
				If $fullArmy Then ExitLoop (2)
				If _Sleep(1000) Then ExitLoop (2)
				DropTrophy()
				$TimeIdle += Round(TimerDiff($hTimer) / 1000, 2) ;In Seconds
				SetLog("Time Idle: " & Floor(Floor($TimeIdle / 60) / 60) & " hours " & Floor(Mod(Floor($TimeIdle / 60), 60)) & " minutes " & Floor(Mod($TimeIdle, 60)) & " seconds")
			WEnd
		EndIf
		ExitLoop
	WEnd
EndFunc   ;==>Idle

Func checkMainScreen() ;Checks if in main screen
	_CaptureRegion()
	If _ColorCheckVariation(_PixelGetColor_GetPixel(284, 28), Hex(0x41B1CD, 6), 20) = False Then
		SetLog("Trying to get to main screen")

		If _ColorCheckVariation(_PixelGetColor_GetPixel(458, 311), Hex(0x33B5E5, 6), 20) Then ;Check for out of sync or inactivity
			Click(416, 399)
		Else
			WinActive("BlueStacks App Player")
			Click(126, 700)

			Local $RunApp = StringReplace(_WinAPI_GetProcessFileName(WinGetProcess("BlueStacks App Player")), "Frontend", "RunApp")
			Run($RunApp & " Android com.supercell.clashofclans com.supercell.clashofclans.GameApp")
		EndIf

		If _Sleep(5000) Then Return
		waitMainScreen()
	EndIf
	_ReduceMemory()
EndFunc   ;==>checkMainScreen

Func waitMainScreen()
	Local $counter = 0

	While 1
		If WinExists("BlueStacks App Player") Then
			_CaptureRegion()
			While 1
				If _ColorCheckVariation(_PixelGetColor_GetPixel(458, 311), Hex(0x33B5E5, 6), 20) Then
					Click(416, 399)
					ExitLoop
				EndIf
				If _ColorCheckVariation(_PixelGetColor_GetPixel(235, 209), Hex(0x9E3826, 6), 20) Then
					Click(429, 493);See if village was attacked, clicks Okay
					ExitLoop
				EndIf
				If _ColorCheckVariation(_PixelGetColor_GetPixel(284, 28), Hex(0x215B69, 6), 20) Then
					Click(1, 1) ;Click away If things are open
					ExitLoop
				EndIf
				If _ColorCheckVariation(_PixelGetColor_GetPixel(819, 55), Hex(0xD80400, 6), 20) Then
					Click(819, 55) ;Clicks X
					ExitLoop
				EndIf
				If _ColorCheckVariation(_PixelGetColor_GetPixel(822, 48), Hex(0xD80408, 6), 20) Or _ColorCheckVariation(_PixelGetColor_GetPixel(830, 59), Hex(0xD80408, 6), 20) Then
					Click(822, 48) ;Clicks X
					ExitLoop
				EndIf
				If _ColorCheckVariation(_PixelGetColor_GetPixel(331, 330), Hex(0xF0A03B, 6), 20) Then
					Click(331, 330) ;Clicks chat thing
					ExitLoop
				EndIf
				If _ColorCheckVariation(_PixelGetColor_GetPixel(429, 519), Hex(0xB8E35F, 6), 20) Then
					Click(429, 519) ;If in that victory or defeat scene
					ExitLoop
				EndIf
				If _ColorCheckVariation(_PixelGetColor_GetPixel(71, 530), Hex(0xC00000, 6), 20) Then
					ReturnHome(False, False) ;If End battle is available
					ExitLoop
				EndIf
				ExitLoop
			WEnd
			If _ColorCheckVariation(_PixelGetColor_GetPixel(284, 28), Hex(0x41B1CD, 6), 20) Then
				If _Sleep(2000) Then ExitLoop
				If _ColorCheckVariation(_PixelGetColor_GetPixel(284, 28), Hex(0x41B1CD, 6), 20) Then
					Return
				EndIf;In main screen
			EndIf
			$counter += 1

			If $counter >= 150 Then ;Five minutes
				SetLog("Could not automatically load Clash Of Clans")
				If _Sleep(1000) Then ExitLoop (2)
				SetLog("Restarting BlueStacks")
				WinActive("BlueStacks App Player")

				Local $RunApp = StringReplace(_WinAPI_GetProcessFileName(WinGetProcess("BlueStacks App Player")), "Frontend", "RunApp")
				ProcessClose("HD-Frontend.exe")
				If _Sleep(5000) Then ExitLoop (2)
				Run($RunApp & " Android com.supercell.clashofclans com.supercell.clashofclans.GameApp")

				Do
					If _Sleep(10000) Then ExitLoop (2)
				Until ControlGetHandle("BlueStacks App Player", "", "BlueStacksApp1") <> 0

				checkMainScreen()
				ExitLoop
			EndIf
		EndIf
		If _Sleep(5000) Then ExitLoop
		_ReduceMemory()
	WEnd
EndFunc   ;==>waitMainScreen

Func checkNextButton() ;Checks for Out of Sync or Connection Lost errors
	_CaptureRegion()

	If _ColorCheckVariation(_PixelGetColor_GetPixel(458, 311), Hex(0x33B5E5, 6), 20) Then ;Check for out of sync or inactivity
		Return False ;Button available
	Else
		Return True ;Out of sync or inactivity error.
	EndIf
EndFunc   ;==>checkNextButton

Func ZoomOut() ;Zooms out
	Local $i = 0
	While 1
		If _Sleep(500) Then ExitLoop
		_CaptureRegion(0, 0, 860, 2)
		If _PixelGetColor_GetPixel(1, 1) = 0x000000 And _PixelGetColor_GetPixel(850, 1) = 0x000000 Then
			ExitLoop
		Else
			ControlSend("BlueStacks App Player", "", "", "{DOWN}", 0)
			$i += 1
			If $i = 20 Then
				ExitLoop
			EndIf
		EndIf
	WEnd
EndFunc   ;==>ZoomOut

Func ReArm()
	While 1
		If $TrapPos[0] = -1 Then
			LocateTrap()
			SaveConfig()
			If _Sleep(1000) Then ExitLoop
		EndIf
		Click(1, 1)
		If _Sleep(1000) Then ExitLoop
		Click($TrapPos[0], $TrapPos[1])
		If _Sleep(1000) Then ExitLoop
		_CaptureRegion()
		$Rearm = _PixelSearch(446, 591, 604, 614, Hex(0xB2A79B, 6), 10)
		If IsArray($Rearm) Then
			Click($Rearm[0], $Rearm[1])
			If _Sleep(1000) Then Return
			_CaptureRegion()
			If _ColorCheckVariation(_PixelGetColor_GetPixel(350, 420), Hex(0xC83B10, 6), 20) Then
				Click(515, 400)
			Else
				SetLog("All traps armed")
			EndIf
			If _Sleep(500) Then ExitLoop
			Click(1, 1)
		Else
			SetLog("Not found")
			If _Sleep(10000) Then Return
		EndIf
		ExitLoop
	WEnd
EndFunc   ;==>ReArm

;Func AutoDonate()
;	Click(25,350)
;	If _Sleep(1000) then Exitloop


#EndRegion ### General Functions ###
;---------------------------------------------------
#Region ### Attack Functions ###
Func AttackMain() ;Main control for attack functions
	While 1
		PrepareSearch()
		If _Sleep(1000) Then ExitLoop
		VillageSearch()
		If _Sleep(1000) Or $Restart = True Then ExitLoop
		PrepareAttack()
		If _Sleep(1000) Then ExitLoop
		Attack()
		If _Sleep(1000) Then ExitLoop
		ReturnHome()
		If _Sleep(1000) Then ExitLoop
		ExitLoop
	WEnd
EndFunc   ;==>AttackMain

Func ReturnHome($TakeSS = True, $GoldChangeCheck = True) ;Return main screen
	While 1
		If $GoldChangeCheck = True Then
			If $checkKPower Or $checkQPower Then
				If _Sleep(50000 - $delayActivateKQ) Then ExitLoop
			Else
				If _Sleep(50000) Then ExitLoop
			EndIf
			While GoldElixirChange()
				If _Sleep(1000) Then ExitLoop (2)
			WEnd
		EndIf

		$checkKPower = False
		$checkQPower = False
		SetLog("Returning Home")
		If $RunState = False Then ExitLoop
		Click(62, 519) ;Click Surrender
		If _Sleep(500) Then ExitLoop
		Click(512, 394) ;Click Confirm
		If _Sleep(4000) Then ExitLoop

		If $TakeSS = True Then
			Local $Date = @MDAY & "." & @MON & "." & @YEAR
			Local $Time = @HOUR & "." & @MIN
			_CaptureRegion()
			_ScreenCapture_SaveImage(@ScriptDir & "\Loots\" & $Date & " at " & $Time & ".jpg", $hBitmap)
		EndIf

		Click(428, 544) ;Click Return Home Button

		Local $counter = 0
		While 1
			If _Sleep(2000) Then ExitLoop (2)
			_CaptureRegion()
			If _ColorCheckVariation(_PixelGetColor_GetPixel(284, 28), Hex(0x41B1CD, 6), 20) Then
				_GUICtrlEdit_SetText($txtLog, "")
				ExitLoop (2)
			EndIf

			$counter += 1

			If $counter >= 50 Then
				SetLog("Cannot return home.")
				checkMainScreen()
				ExitLoop (2)
			EndIf
		WEnd
		ExitLoop
	WEnd
EndFunc   ;==>ReturnHome

Func GoldElixirChange() ;Checks 30 seconds if gold changes
	Local $Gold1, $Gold2
	While 1
		$Gold1 = getGold(51, 66)
		$Elixir1 = getElixir(51, 66 + 29)
		Local $iBegin = TimerInit()
		While TimerDiff($iBegin) < 30000
			If $RunState = False Then ExitLoop
			Sleep(100)
			;If Not _ColorCheckVariation(_PixelGetColor_GetPixel(71, 530), Hex(0xC00000, 6), 50) Then
			;	SetLog("End Battle button not dected")
			;EndIf
		WEnd
		$Gold2 = getGold(51, 66)
		$Elixir2 = getElixir(51, 66 + 29)
		If $Gold1 = $Gold2 Or $Elixir1 = $Elixir2 Or $Gold2 = "" Or $Elixir2 = "" Then
			Return False
		Else
			SetLog("Gold & Elixir change detected, waiting...")
			Return True
		EndIf
		ExitLoop
	WEnd
EndFunc   ;==>GoldElixirChange

Func Attack() ;Selects which algorithm
	While 1
		SetLog("======Beginning Attack======")
		Switch $icmbAlgorithm
			Case 0 ;Barbarians + Archers
				atkAlgorithmBarch()
			Case 1 ;Use All Troops
				SetLog("Not Available yet, using Barch instead...")
				If _Sleep(2000) Then ExitLoop
				atkAlgorithmBarch()
		EndSwitch
		ExitLoop
	WEnd
EndFunc   ;==>Attack

Func atkAlgorithmBarch() ;Attack Algorithm for Barch
	While 1
		Local $Barb = -1, $Arch = -1, $CC = -1
		Global $King = -1, $Queen = -1
		For $i = 0 To 6
			If $atkTroops[$i][0] = "Barbarian" Then
				$Barb = $i
			ElseIf $atkTroops[$i][0] = "Archer" Then
				$Arch = $i
			ElseIf $atkTroops[$i][0] = "Clan Castle" Then
				$CC = $i
			ElseIf $atkTroops[$i][0] = "King" Then
				$King = $i
			ElseIf $atkTroops[$i][0] = "Queen" Then
				$Queen = $i
			EndIf
		Next

		If _Sleep(500) Then ExitLoop
		Switch $deploySettings
			Case 0 ;Two sides ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
				SetLog("~Attacking in two sides...")
				If _Sleep(1000) Then ExitLoop
				Local $numBarbPerSpot = Ceiling((($atkTroops[$Barb][1] / 2) / 5) / 2)
				Local $numArchPerSpot = Ceiling((($atkTroops[$Arch][1] / 2) / 5) / 2)

				SetLog("Dropping first wave of Barbarians")
				Click(68 + (72 * $Barb), 595) ;Select Troop
				For $i = 0 To 4 ;Drop first round of Barbarians
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numBarbPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numBarbPerSpot, 1)
				Next

				If _Sleep(1000) Then ExitLoop

				SetLog("Dropping first wave of Archers")
				Click(68 + (72 * $Arch), 595) ;Select Troop
				For $i = 0 To 4 ;Drop first round of Archers
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numArchPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numArchPerSpot, 1)
				Next

				If _Sleep(2000) Then ExitLoop ;-------------------------------------------

				SetLog("Dropping second wave of Barbarians")
				Click(68 + (72 * $Barb), 595) ;Select Troop
				For $i = 0 To 4 ;Drop second round of Barbarians
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numBarbPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numBarbPerSpot, 1)
				Next

				If _Sleep(1000) Then ExitLoop

				SetLog("Dropping second wave of Archers")
				Click(68 + (72 * $Arch), 595) ;Select Troop
				For $i = 0 To 4 ;Drop second round of Archers
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numArchPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numArchPerSpot, 1)
				Next

				dropHeroes($TopLeft[3][0], $TopLeft[3][1], $King, $Queen)
				If _Sleep(1000) Then ExitLoop
				If $CC <> -1 Then dropCC($TopLeft[3][0], $TopLeft[3][1], $CC)
			Case 1 ;Three sides ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
				SetLog("~Attacking in three sides...")
				If _Sleep(1000) Then ExitLoop
				Local $numBarbPerSpot = Ceiling((($atkTroops[$Barb][1] / 3) / 5) / 2)
				Local $numArchPerSpot = Ceiling((($atkTroops[$Arch][1] / 3) / 5) / 2)

				SetLog("Dropping first wave of Barbarians")
				Click(68 + (72 * $Barb), 595) ;Select Troop
				For $i = 0 To 4 ;Drop first round of Barbarians
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numBarbPerSpot, 1)
					Click($TopRight[$i][0], $TopRight[$i][1], $numBarbPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numBarbPerSpot, 1)
				Next

				If _Sleep(1000) Then ExitLoop

				SetLog("Dropping first wave of Archers")
				Click(68 + (72 * $Arch), 595) ;Select Troop
				For $i = 0 To 4 ;Drop first round of Archers
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numArchPerSpot, 1)
					Click($TopRight[$i][0], $TopRight[$i][1], $numArchPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numArchPerSpot, 1)
				Next

				If _Sleep(2000) Then ExitLoop ;-------------------------------------------

				SetLog("Dropping second wave of Barbarians")
				Click(68 + (72 * $Barb), 595) ;Select Troop
				For $i = 0 To 4 ;Drop second round of Barbarians
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numBarbPerSpot, 1)
					Click($TopRight[$i][0], $TopRight[$i][1], $numBarbPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numBarbPerSpot, 1)
				Next

				If _Sleep(1000) Then ExitLoop

				SetLog("Dropping second wave of Archers")
				Click(68 + (72 * $Arch), 595) ;Select Troop
				For $i = 0 To 4 ;Drop second round of Archers
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numArchPerSpot, 1)
					Click($TopRight[$i][0], $TopRight[$i][1], $numArchPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numArchPerSpot, 1)
				Next

				dropHeroes($TopRight[3][0], $TopRight[3][1], $King, $Queen)
				If _Sleep(1000) Then ExitLoop
				If $CC <> -1 Then dropCC($TopRight[3][0], $TopRight[3][1], $CC)
			Case 2 ;Four sides ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
				SetLog("~Attacking in all sides...")
				If _Sleep(1000) Then ExitLoop
				Local $numBarbPerSpot = Ceiling((($atkTroops[$Barb][1] / 4) / 5) / 2)
				Local $numArchPerSpot = Ceiling((($atkTroops[$Arch][1] / 4) / 5) / 2)

				SetLog("Dropping first wave of Barbarians")
				Click(68 + (72 * $Barb), 595) ;Select Troop
				For $i = 0 To 4 ;Drop first round of Barbarians
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numBarbPerSpot, 1)
					Click($TopRight[$i][0], $TopRight[$i][1], $numBarbPerSpot, 1)
					Click($BottomLeft[$i][0], $BottomLeft[$i][1], $numBarbPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numBarbPerSpot, 1)
				Next

				If _Sleep(1000) Then ExitLoop

				SetLog("Dropping first wave of Archers")
				Click(68 + (72 * $Arch), 595) ;Select Troop
				For $i = 0 To 4 ;Drop first round of Archers
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numArchPerSpot, 1)
					Click($TopRight[$i][0], $TopRight[$i][1], $numArchPerSpot, 1)
					Click($BottomLeft[$i][0], $BottomLeft[$i][1], $numArchPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numArchPerSpot, 1)
				Next

				If _Sleep(2000) Then ExitLoop ;-------------------------------------------

				SetLog("Dropping second wave of Barbarians")
				Click(68 + (72 * $Barb), 595) ;Select Troop
				For $i = 0 To 4 ;Drop second round of Barbarians
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numBarbPerSpot, 1)
					Click($TopRight[$i][0], $TopRight[$i][1], $numBarbPerSpot, 1)
					Click($BottomLeft[$i][0], $BottomLeft[$i][1], $numBarbPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numBarbPerSpot, 1)
				Next

				If _Sleep(1000) Then ExitLoop

				SetLog("Dropping second wave of Archers")
				Click(68 + (72 * $Arch), 595) ;Select Troop
				For $i = 0 To 4 ;Drop second round of Archers
					If _Sleep(100) Then ExitLoop (2)
					Click($TopLeft[$i][0], $TopLeft[$i][1], $numArchPerSpot, 1)
					Click($TopRight[$i][0], $TopRight[$i][1], $numArchPerSpot, 1)
					Click($BottomLeft[$i][0], $BottomLeft[$i][1], $numArchPerSpot, 1)
					Click($BottomRight[$i][0], $BottomRight[$i][1], $numArchPerSpot, 1)
				Next

				dropHeroes($BottomLeft[3][0], $BottomLeft[3][1], $King, $Queen)
				If _Sleep(1000) Then ExitLoop
				If $CC <> -1 Then dropCC($BottomLeft[3][0], $BottomLeft[3][1], $CC)
		EndSwitch

		If _Sleep(100) Then ExitLoop
		SetLog("Dropping left over troops")
		$atkTroops[$Barb][1] = Number(getNormal(40 + (72 * $Barb), 565))
		$atkTroops[$Arch][1] = Number(getNormal(40 + (72 * $Arch), 565))

		Click(68 + (72 * $Barb), 595)
		While $atkTroops[$Barb][1] <> 0
			If _Sleep(100) Then ExitLoop (2)
			Click($TopLeft[3][0], $TopLeft[3][1], $atkTroops[$Barb][1], 1)
			$atkTroops[$Barb][1] = Number(getNormal(40 + (72 * $Barb), 565))
		WEnd

		If _Sleep(1000) Then ExitLoop

		Click(68 + (72 * $Arch), 595)
		While $atkTroops[$Arch][1] <> 0
			If _Sleep(100) Then ExitLoop (2)
			Click($TopLeft[3][0], $TopLeft[3][1], $atkTroops[$Arch][1], 1)
			$atkTroops[$Arch][1] = Number(getNormal(40 + (72 * $Arch), 565))
		WEnd

		If _Sleep(100) Then ExitLoop

		;Activate KQ's power
		If $checkKPower <> -1 Or $checkQPower <> -1 Then
			SetLog("Waiting " & $delayActivateKQ / 1000 & " seconds before activating King/Queen")
			_Sleep($delayActivateKQ)
			If $checkKPower <> -1 Then
				SetLog("Activate King's power")
				Click(68 + (72 * $checkKPower), 595)
			EndIf
			If $checkQPower <> -1 Then
				SetLog("Activate Queen's power")
				Click(68 + (72 * $checkQPower), 595)
			EndIf
		EndIf

		SetLog("~Finished Attacking, waiting to finish")
		ExitLoop
	WEnd
EndFunc   ;==>atkAlgorithmBarch

Func dropHeroes($x, $y, $KingSlot = -1, $QueenSlot = -1) ;Drops for king and queen
	While 1
		If _Sleep(2000) Then ExitLoop
		Switch $iradAttackMode
			Case 0 ;Dead Base
				If $KingSlot <> -1 And ($KingAttack[0] = 1 Or $KingAttack[2] = 1) Then
					SetLog("Dropping King")
					Click(68 + (72 * $KingSlot), 595) ;Select King
					Click($x, $y)
					$checkKPower = $KingSlot
				EndIf

				If _Sleep(1000) Then ExitLoop

				If $QueenSlot <> -1 And ($QueenAttack[0] = 1 Or $QueenAttack[2] = 1) Then
					SetLog("Dropping Queen")
					Click(68 + (72 * $QueenSlot), 595) ;Select Queen
					Click($x, $y)
					$checkQPower = $QueenSlot
				EndIf
			Case 1 ;Weak Base
				;--------------------------------
			Case 2 ;All Base
				If $KingSlot <> -1 And $KingAttack[2] = 1 Then
					SetLog("Dropping King")
					Click(68 + (72 * $KingSlot), 595) ;Select King
					Click($x, $y)
					$checkKPower = $KingSlot
				EndIf

				If _Sleep(1000) Then ExitLoop

				If $QueenSlot <> -1 And $QueenAttack[2] = 1 Then
					SetLog("Dropping Queen")
					Click(68 + (72 * $QueenSlot), 595) ;Select Queen
					Click($x, $y)
					$checkQPower = $QueenSlot
				EndIf
		EndSwitch
		ExitLoop
	WEnd
EndFunc   ;==>dropHeroes

Func dropCC($x, $y, $slot) ;Drop clan castle
	SetLog("Dropping Clan Castle")
	Click(68 + (72 * $slot), 595, 1, 500)
	Click($x, $y)
EndFunc   ;==>dropCC

Func PrepareAttack() ;Assigns troops
	While 1
		SetLog("Preparing to attack")
		For $i = 0 To 6
			_CaptureRegion()
			$Troop = _PixelGetColor_GetPixel(68 + (72 * $i), 595)
			If _ColorCheckVariation($Troop, Hex(0xF8B020, 6), 5) Then ;Check if slot is Barbarian
				$atkTroops[$i][0] = "Barbarian"
				$atkTroops[$i][1] = Number(getNormal(40 + (72 * $i), 565))
			ElseIf _ColorCheckVariation($Troop, Hex(0xD83F68, 6), 5) Then ;Check if slot is Archer
				$atkTroops[$i][0] = "Archer"
				$atkTroops[$i][1] = Number(getNormal(40 + (72 * $i), 565))
			ElseIf _ColorCheckVariation($Troop, Hex(0x7BC950, 6), 5) Then ;Check if slot is Goblin
				$atkTroops[$i][0] = "Goblin"
				$atkTroops[$i][1] = Number(getNormal(40 + (72 * $i), 565))
			ElseIf _ColorCheckVariation($Troop, Hex(0xF8D49E, 6), 5) Then ;Check if slot is Giant
				$atkTroops[$i][0] = "Giant"
				$atkTroops[$i][1] = Number(getNormal(40 + (72 * $i), 565))
			ElseIf _ColorCheckVariation($Troop, Hex(0x60A4D0, 6), 5) Then ;Check if slot is Wallbreaker
				$atkTroops[$i][0] = "Wallbreaker"
				$atkTroops[$i][1] = Number(getNormal(40 + (72 * $i), 565))
			ElseIf _ColorCheckVariation($Troop, Hex(0xF8EB79, 6), 5) Then ;Check if slot is King
				$atkTroops[$i][0] = "King"
				$atkTroops[$i][1] = 1
			ElseIf _ColorCheckVariation(_PixelGetColor_GetPixel(68 + (72 * $i), 588), Hex(0x7031F0, 6), 5) Then ;Check if slot is Queen
				$atkTroops[$i][0] = "Queen"
				$atkTroops[$i][1] = 1
			ElseIf _ColorCheckVariation(_PixelGetColor_GetPixel(68 + (72 * $i), 588), Hex(0xF6BF50, 6), 5) Then ;Check if slot is Clan Castle
				$atkTroops[$i][0] = "Clan Castle"
				$atkTroops[$i][1] = 1
			Else
				$atkTroops[$i][0] = ""
				$atkTroops[$i][1] = 0
			EndIf
			If $atkTroops[$i][0] <> "" Then SetLog("-" & $atkTroops[$i][0] & " " & $atkTroops[$i][1])
		Next
		ExitLoop
	WEnd
EndFunc   ;==>PrepareAttack

Func VillageSearch() ;Control for searching a village that meets conditions
	While 1
		Switch $iradAttackMode
			Case 0
				SetLog("============Searching For Dead Base============")
			Case 1
				SetLog("============Searching For Weak Base============")
			Case 2
				SetLog("============Searching For All Base============")
		EndSwitch
		SetLog("~Gold: " & $MinGold & "; Elixir: " & $MinElixir & "; Dark: " & $MinDark & "; Trophy: " & $MinTrophy)

		$SearchCount = 0
		While 1
			If _Sleep(1000) Then ExitLoop (2)
			GetResources() ;Reads Resource Values

			If $Restart = True Then ExitLoop (2)
			If CompareResources() Then
				If $iradAttackMode = 0 Then
					If ZombieSearch() Then
						SetLog("~~~~~~~Dead Base Found!~~~~~~~")
						ExitLoop
					Else
						SetLog("~~~~~~~Not dead base, skipping~~~~~~~")
						Click(750, 500) ;Click Next
					EndIf
				Else
					ExitLoop
				EndIf
			Else
				Click(750, 500) ;Click Next
			EndIf
		WEnd
		If GUICtrlRead($chkAlertSearch) = $GUI_CHECKED Then
			TrayTip("Match Found!", "Gold: " & $searchGold & "; Elixir: " & $searchElixir & "; Dark: " & $searchDark & "; Trophy: " & $searchTrophy, "", 0)
			SoundPlay(@WindowsDir & "\media\Festival\Windows Exclamation.wav", 1)
		EndIf
		SetLog("===============Searching Complete===============")
		readConfig()
		ExitLoop
	WEnd
EndFunc   ;==>VillageSearch

Func GetResources() ;Reads resources
	While 1
		Local $i = 0
		While getGold(51, 66) = "" ; Loops until gold is readable
			If _Sleep(500) Then ExitLoop (2)
			$i += 1
			If $i >= 20 Then ; If gold cannot be read by 10 seconds
				If checkNextButton() Then ;Checks for Out of Sync or Connection Error during search
					Click(750, 500) ;Click Next
				Else
					SetLog("Cannot locate Next button, Restarting Bot")
					checkMainScreen()
					$Restart = True
					ExitLoop (2)
				EndIf
				$i = 0
			EndIf
		WEnd
		If _Sleep(300) Then ExitLoop (2)

		$searchGold = getGold(51, 66)
		$searchElixir = getElixir(51, 66 + 29)
		$searchTrophy = getTrophy(51, 66 + 90)

		If $searchTrophy <> "" Then
			$searchDark = getDarkElixir(51, 66 + 57)
		Else
			$searchDark = 0
			$searchTrophy = getTrophy(51, 66 + 60)
		EndIf

		$SearchCount += 1 ; Counter for number of searches
		SetLog("(" & $SearchCount & ") [G]: " & $searchGold & Tab($searchGold, 12) & "[E]: " & $searchElixir & Tab($searchElixir, 12) & "[D]: " & $searchDark & Tab($searchDark, 12) & "[T]: " & $searchTrophy)
		ExitLoop
	WEnd
EndFunc   ;==>GetResources

Func CompareResources() ;Compares resources and returns true if conditions meet, otherwise returns false
	If $SearchCount <> 0 And Mod($SearchCount, 20) = 0 Then
		$MinGold -= 1000
		$MinElixir -= 1000
		$MinDark -= 1000
		$MinTrophy -= 1000
		SetLog("~Gold: " & $MinGold & "; Elixir: " & $MinElixir & "; Dark: " & $MinDark & "; Trophy: " & $MinTrophy)
	EndIf

	Local $G = (Number($searchGold) >= Number($MinGold)), $E = (Number($searchElixir) >= Number($MinElixir)), $D = (Number($searchDark) >= Number($MinDark)), $T = (Number($searchTrophy) >= Number($MinTrophy))
	Local $Boolean = False

	If $G Or $E Then $Boolean = True

	If $chkConditions[0] = 1 Then
		If $G = False Or $E = False Then $Boolean = False
		Return $Boolean
	EndIf

	If $chkConditions[1] = 1 Then
		If $D = False Then $Boolean = False
		Return $Boolean
	EndIf

	If $chkConditions[2] = 1 Then
		If $T = False Then $Boolean = False
		Return $Boolean
	EndIf

	Return $Boolean
EndFunc   ;==>CompareResources

Func PrepareSearch() ;Click attack button and find match button, will break shield
	While 1
		Click(60, 614);Click Attack Button
		If _Sleep(1000) Then ExitLoop
		Click(217, 510);Click Find a Match Button
		If _Sleep(3000) Then ExitLoop
		_CaptureRegion()
		If _ColorCheckVariation(_PixelGetColor_GetPixel(513, 416), Hex(0x5DAC10, 6), 50) Then
			Click(513, 416);Click Okay To Break Shield
		EndIf
		ExitLoop
	WEnd
EndFunc   ;==>PrepareSearch
#EndRegion ### Attack Functions ###
;---------------------------------------------------
#Region ### Troops Settings ###
Func LocateCollectors()
	SetLog("Locating Collectors...")
	Local $MsgBox
	For $i = 0 To 16
		While 1
			While 1
				$MsgBox = MsgBox(6 + 262144, "Locate collector #" & $i + 1, "Click Continue then click on your collector #" & $i + 1 & ". Try again if you misclicked previous one. Cancel to finish.", 0, $frmBot)
				If $MsgBox = 11 Then
					WinActivate($HWnD)
					$collectorPos[$i][0] = FindPos()[0]
					$collectorPos[$i][1] = FindPos()[1]
				ElseIf $MsgBox = 10 Then
					$i -= 1
					ExitLoop
				Else
					ExitLoop (3)
				EndIf
				SetLog("-Collector #" & $i + 1 & " = " & "(" & $collectorPos[$i][0] & "," & $collectorPos[$i][1] & ")")
				If _Sleep(500) Then ExitLoop
				ExitLoop (2)
			WEnd
		WEnd
	Next
	SaveConfig()
	SetLog("-Locating Complete-")
EndFunc   ;==>LocateCollectors

Func LocateBarrack()
	SetLog("Locating Barracks...")
	Local $MsgBox
	While 1
		While 1
			$MsgBox = MsgBox(6 + 262144, "Locate first barrack", "Click Continue then click on your first barrack. Cancel if not available. Try again to start over.", 0, $frmBot)
			If $MsgBox = 11 Then
				$barrackPos[0][0] = FindPos()[0]
				$barrackPos[0][1] = FindPos()[1]
			ElseIf $MsgBox = 10 Then
				ExitLoop
			Else
				$barrackPos[0][0] = ""
				$barrackPos[0][1] = ""
			EndIf
			If _Sleep(500) Then ExitLoop
			$MsgBox = MsgBox(6 + 262144, "Locate second barrack", "Click Continue then click on your second barrack. Cancel if not available. Try again to start over.", 0, $frmBot)
			If $MsgBox = 11 Then
				$barrackPos[1][0] = FindPos()[0]
				$barrackPos[1][1] = FindPos()[1]
			ElseIf $MsgBox = 10 Then
				ExitLoop
			Else
				$barrackPos[1][0] = ""
				$barrackPos[1][1] = ""
			EndIf
			If _Sleep(500) Then ExitLoop
			$MsgBox = MsgBox(6 + 262144, "Locate third barrack", "Click Continue then click on your third barrack. Cancel if not available. Try again to start over.", 0, $frmBot)
			If $MsgBox = 11 Then
				$barrackPos[2][0] = FindPos()[0]
				$barrackPos[2][1] = FindPos()[1]
			ElseIf $MsgBox = 10 Then
				ExitLoop
			Else
				$barrackPos[2][0] = ""
				$barrackPos[2][1] = ""
			EndIf
			If _Sleep(500) Then ExitLoop
			$MsgBox = MsgBox(6 + 262144, "Locate fourth barrack", "Click Continue then click on your fourth barrack. Cancel if not available. Try again to start over.", 0, $frmBot)
			If $MsgBox = 11 Then
				$barrackPos[3][0] = FindPos()[0]
				$barrackPos[3][1] = FindPos()[1]
			ElseIf $MsgBox = 10 Then
				ExitLoop
			Else
				$barrackPos[3][0] = ""
				$barrackPos[3][1] = ""
			EndIf
			ExitLoop (2)
		WEnd
	WEnd
	SaveConfig()
	SetLog("-Locating Complete-")
	SetLog("-Barrack 1 = " & "(" & $barrackPos[0][0] & "," & $barrackPos[0][1] & ")")
	SetLog("-Barrack 2 = " & "(" & $barrackPos[1][0] & "," & $barrackPos[1][1] & ")")
	SetLog("-Barrack 3 = " & "(" & $barrackPos[2][0] & "," & $barrackPos[2][1] & ")")
	SetLog("-Barrack 4 = " & "(" & $barrackPos[3][0] & "," & $barrackPos[3][1] & ")")
EndFunc   ;==>LocateBarrack

Func LocateClanClastle()
	While 1
		$MsgBox = MsgBox(1 + 262144, "Locate Clan Castle", "Click OK then click on your Clan Castle", 0, $frmBot)
		If $MsgBox = 1 Then
			WinActivate($HWnD)
			$CCPos[0] = FindPos()[0]
			$CCPos[1] = FindPos()[1]
			SetLog("-Clan Castle =  " & "(" & $CCPos[0] & "," & $CCPos[1] & ")")
		EndIf
		ExitLoop
	WEnd
	Click(1, 1)
EndFunc   ;==>LocateClanClastle

Func LocateTrap()
	While 1
		$MsgBox = MsgBox(1 + 262144, "Locate Trap", "Click OK then click on one of your traps", 0, $frmBot)
		If $MsgBox = 1 Then
			WinActivate($HWnD)
			$TrapPos[0] = FindPos()[0]
			$TrapPos[1] = FindPos()[1]
			SetLog("-Trap =  " & "(" & $TrapPos[0] & "," & $TrapPos[1] & ")")
		EndIf
		ExitLoop
	WEnd
	Click(1, 1)
EndFunc   ;==>LocateTrap

Func Train()
	If $barrackPos[0][0] = "" Then
		LocateBarrack()
		SaveConfig()
		If _Sleep(1000) Then Return
	EndIf

	SetLog("Training Troops...")

	While 1
		For $i = 0 To 3
			If _Sleep(500) Then ExitLoop (2)

			Click(1, 1) ;Click Away

			If _Sleep(500) Then ExitLoop (2)

			Click($barrackPos[$i][0], $barrackPos[$i][1]) ;Click Barrack

			If _Sleep(1000) Then ExitLoop (2)

			Local $TrainPos = _PixelSearch(155, 603, 694, 605, Hex(0x603818, 6), 5) ;Finds Train Troops button
			If IsArray($TrainPos) = False Then
				SetLog("Barrack " & $i + 1 & " is not available")
				If _Sleep(500) Then ExitLoop (2)
			Else
				Click($TrainPos[0], $TrainPos[1]) ;Click Train Troops button
				If _Sleep(1000) Then ExitLoop (2)

				CheckFullArmy()

				_CaptureRegion()
				Switch $barrackTroop[$i]
					Case 0
						While _ColorCheckVariation(_PixelGetColor_GetPixel(329, 297), Hex(0xDC3F70, 6), 20)
							_CaptureRegion()
							Click(220, 320) ;Barbarian
							If _Sleep(10) Then ExitLoop
						WEnd
					Case 1
						While _ColorCheckVariation(_PixelGetColor_GetPixel(217, 297), Hex(0xF8AD20, 6), 20)
							_CaptureRegion()
							Click(331, 320) ;Archer
							If _Sleep(10) Then ExitLoop
						WEnd
					Case 2
						While _ColorCheckVariation(_PixelGetColor_GetPixel(217, 297), Hex(0xF8AD20, 6), 20)
							_CaptureRegion()
							Click(432, 320) ;Giant
							If _Sleep(10) Then ExitLoop
						WEnd
					Case 3
						While _ColorCheckVariation(_PixelGetColor_GetPixel(217, 297), Hex(0xF8AD20, 6), 20)
							_CaptureRegion()
							Click(546, 320) ;Goblins
							If _Sleep(10) Then ExitLoop
						WEnd
				EndSwitch
			EndIf
			If _Sleep(500) Then ExitLoop (2)
			Click(1, 1, 2, 250); Click away twice with 250ms delay
		Next

		SetLog("Training Troops Complete")
		ExitLoop
	WEnd
EndFunc   ;==>Train


Func RequestCC()
	If GUICtrlRead($chkRequest) = $GUI_CHECKED Then
		If GUICtrlRead($txtRequest) <> "" Then
			If $CCPos[0] = -1 Then
				LocateClanClastle()
				SaveConfig()
				If _Sleep(1000) Then Return
			EndIf
			While 1
				SetLog("Requesting for Clan Castle's Troops")
				Click($CCPos[0], $CCPos[1])
				If _Sleep(1000) Then ExitLoop
				_CaptureRegion()
				$RequestTroop = _PixelSearch(310, 580, 553, 622, Hex(0x608C90, 6), 10)
				If IsArray($RequestTroop) Then
					Click($RequestTroop[0], $RequestTroop[1])
					If _Sleep(1000) Then ExitLoop
					_CaptureRegion()
					If _ColorCheckVariation(_PixelGetColor_GetPixel(340, 245), Hex(0xCC4010, 6), 20) Then
						Click(430, 140) ;Select text for request
						If _Sleep(1000) Then ExitLoop
						$TextRequest = GUICtrlRead($txtRequest)
						ControlSend("BlueStacks App Player", "", "", $TextRequest, 0)
						If _Sleep(1000) Then ExitLoop
						Click(524, 228)
						;Click(340, 228)
					Else
						SetLog("Request's already been made")
					EndIf
				Else
					SetLog("Clan Castle not available")
				EndIf

				ExitLoop
			WEnd
		EndIf
	EndIf
EndFunc   ;==>RequestCC


Func CheckFullArmy()
	_CaptureRegion()
	$Pixel = _ColorCheckVariation(_PixelGetColor_GetPixel(327, 520), Hex(0xD03838, 6), 20)
	If $Pixel Then
		$fullArmy = True
	Else
		$fullArmy = False
	EndIf
EndFunc   ;==>CheckFullArmy
#EndRegion ### Troops Settings ###
;---------------------------------------------------
#Region ### Village Functions ###
Func DropTrophy()
	Local $TrophyCount = getOther(50, 74, "Trophy")
	While Number($TrophyCount) > Number($itxtMaxTrophy)
		$TrophyCount = getOther(50, 74, "Trophy")
		SetLog("Trophy Count : " & $TrophyCount)
		If Number($TrophyCount) > Number($itxtMaxTrophy) Then
			SetLog("Dropping Trophies")
			If _Sleep(2000) Then ExitLoop

			ZoomOut()
			PrepareSearch()

			If _Sleep(5000) Then ExitLoop

			Click(34, 310) ;Drop one troop

			If _Sleep(1000) Then ExitLoop

			ReturnHome(False, False) ;Return home no screenshot
		Else
			SetLog("Trophy Drop Complete")
		EndIf
	WEnd
EndFunc   ;==>DropTrophy

Func Collect()
	If $collectorPos[0][0] = "" Then
		LocateCollectors()
		SaveConfig()
		If _Sleep(2000) Then Return
	EndIf
	SetLog("Collecting Resources")
	_Sleep(250)
	Click(1, 1) ;Click Away
	For $i = 0 To 16
		If _Sleep(250) Or $RunState = False Then ExitLoop
		If $collectorPos[$i][0] <> "" Then Click($collectorPos[$i][0], $collectorPos[$i][1]) ;Click collector
		If _Sleep(250) Or $RunState = False Then ExitLoop
		Click(1, 1) ;Click Away
	Next
	SetLog("Collecting Complete")
EndFunc   ;==>Collect
#EndRegion ### Village Functions ###
;---------------------------------------------------
#Region ### Other Functions ###
Func readConfig() ;Reads config and sets it to the variables
	If FileExists($config) Then
		;Search Settings------------------------------------------------------------------------
		$MinGold = IniRead($config, "search", "searchGold", "0")
		$MinElixir = IniRead($config, "search", "searchElixir", "0")
		$MinDark = IniRead($config, "search", "searchDark", "0")
		$MinTrophy = IniRead($config, "search", "searchTrophy", "0")

		$chkConditions[0] = IniRead($config, "search", "conditionGoldElixir", "0")
		$chkConditions[1] = IniRead($config, "search", "conditionDark", "0")
		$chkConditions[2] = IniRead($config, "search", "conditionTrophy", "0")
		;Attack Settings-------------------------------------------------------------------------
		$deploySettings = IniRead($config, "attack", "deploy", "0")
		$icmbAlgorithm = IniRead($config, "attack", "algorithm", "0")
		$iradAttackMode = IniRead($config, "attack", "mode", "0")

		$KingAttack[0] = IniRead($config, "attack", "king-dead", "0")
		$KingAttack[2] = IniRead($config, "attack", "king-all", "0")

		$QueenAttack[0] = IniRead($config, "attack", "queen-dead", "0")
		$QueenAttack[2] = IniRead($config, "attack", "queen-all", "0")
		;Donate Settings-------------------------------------------------------------------------
		$CCPos[0] = IniRead($config, "donate", "xCCPos", "-1")
		$CCPos[1] = IniRead($config, "donate", "yCCPos", "-1")
		$CheckRequest = IniRead($config, "donate", "request", "0")
		$TextRequest = IniRead($config, "donate", "textrequest", "")
		;Troop Settings--------------------------------------------------------------------------
		$icmbTroopComp = IniRead($config, "troop", "composition", 0)

		For $i = 0 To 3 ;Covers all 4 Barracks
			$barrackPos[$i][0] = IniRead($config, "troop", "xBarrack" & $i + 1, "0")
			$barrackPos[$i][1] = IniRead($config, "troop", "yBarrack" & $i + 1, "0")
			$barrackTroop[$i] = IniRead($config, "troop", "troop" & $i + 1, "0")
		Next
	Else
		Return False
	EndIf
	;General Settings--------------------------------------------------------------------------
	$frmBotPosX = IniRead($config, "general", "frmBotPosX", "207")
	$frmBotPosY = IniRead($config, "general", "frmBotPosY", "158")
	$itxtMaxTrophy = IniRead($config, "general", "MaxTrophy", "3000")
	$ichkBackground = IniRead($config, "general", "Background", "0")

	For $i = 0 To 16 ;Covers all Collectors
		$collectorPos[$i][0] = IniRead($config, "general", "xCollector" & $i + 1, "0")
		$collectorPos[$i][1] = IniRead($config, "general", "yCollector" & $i + 1, "0")
	Next

	$TrapPos[0] = IniRead($config, "general", "xTrap", "-1")
	$TrapPos[1] = IniRead($config, "general", "yTrap", "-1")

EndFunc   ;==>readConfig

Func applyConfig() ;Applies the data from config to the controls in GUI
	;Search Settings------------------------------------------------------------------------
	GUICtrlSetData($txtMinGold, $MinGold)
	GUICtrlSetData($txtMinElixir, $MinElixir)
	GUICtrlSetData($txtMinDarkElixir, $MinDark)
	GUICtrlSetData($txtMinTrophy, $MinTrophy)

	If $chkConditions[0] = 1 Then
		GUICtrlSetState($chkMeetGxE, $GUI_CHECKED)
	ElseIf $chkConditions[0] = 0 Then
		GUICtrlSetState($chkMeetGxE, $GUI_UNCHECKED)
	EndIf

	If $chkConditions[1] = 1 Then
		GUICtrlSetState($chkMeetDE, $GUI_CHECKED)
	ElseIf $chkConditions[1] = 0 Then
		GUICtrlSetState($chkMeetDE, $GUI_UNCHECKED)
	EndIf

	If $chkConditions[2] = 1 Then
		GUICtrlSetState($chkMeetTrophy, $GUI_CHECKED)
	ElseIf $chkConditions[2] = 0 Then
		GUICtrlSetState($chkMeetTrophy, $GUI_UNCHECKED)
	EndIf
	;Attack Settings-------------------------------------------------------------------------
	_GUICtrlComboBox_SetCurSel($cmbDeploy, $deploySettings)
	_GUICtrlComboBox_SetCurSel($cmbAlgorithm, $icmbAlgorithm)

	Switch $iradAttackMode
		Case 0
			GUICtrlSetState($radDeadBases, $GUI_CHECKED)
			GUICtrlSetState($radWeakBases, $GUI_UNCHECKED)
			GUICtrlSetState($radAllBases, $GUI_UNCHECKED)
		Case 1
			GUICtrlSetState($radDeadBases, $GUI_UNCHECKED)
			GUICtrlSetState($radWeakBases, $GUI_CHECKED)
			GUICtrlSetState($radAllBases, $GUI_UNCHECKED)
		Case 2
			GUICtrlSetState($radDeadBases, $GUI_UNCHECKED)
			GUICtrlSetState($radWeakBases, $GUI_UNCHECKED)
			GUICtrlSetState($radAllBases, $GUI_CHECKED)
	EndSwitch

	If $KingAttack[0] = 1 Then
		GUICtrlSetState($chkKingAttackDeadBases, $GUI_CHECKED)
	Else
		GUICtrlSetState($chkKingAttackDeadBases, $GUI_UNCHECKED)
	EndIf
	If $KingAttack[2] = 1 Then
		GUICtrlSetState($chkKingAttackAllBases, $GUI_CHECKED)
	Else
		GUICtrlSetState($chkKingAttackAllBases, $GUI_UNCHECKED)
	EndIf

	If $QueenAttack[0] = 1 Then
		GUICtrlSetState($chkQueenAttackDeadBases, $GUI_CHECKED)
	Else
		GUICtrlSetState($chkQueenAttackDeadBases, $GUI_UNCHECKED)
	EndIf
	If $QueenAttack[2] = 1 Then
		GUICtrlSetState($chkQueenAttackAllBases, $GUI_CHECKED)
	Else
		GUICtrlSetState($chkQueenAttackAllBases, $GUI_UNCHECKED)
	EndIf
	;Donate Settings-------------------------------------------------------------------------
	If $CheckRequest = 1 Then
		GUICtrlSetState($chkRequest, $GUI_CHECKED)
	Else
		GUICtrlSetState($chkRequest, $GUI_UNCHECKED)
	EndIf

	;Troop Settings--------------------------------------------------------------------------
	_GUICtrlComboBox_SetCurSel($cmbTroopComp, $icmbTroopComp)
	SetComboTroopComp()

	_GUICtrlComboBox_SetCurSel($cmbBarrack1, $barrackTroop[0])
	_GUICtrlComboBox_SetCurSel($cmbBarrack2, $barrackTroop[1])
	_GUICtrlComboBox_SetCurSel($cmbBarrack3, $barrackTroop[2])
	_GUICtrlComboBox_SetCurSel($cmbBarrack4, $barrackTroop[3])
	;General Settings--------------------------------------------------------------------------
	WinMove($sBotTitle, "", $frmBotPosX, $frmBotPosY)
	GUICtrlSetData($txtMaxTrophy, $itxtMaxTrophy)

	If $ichkBackground = 1 Then
		GUICtrlSetState($chkBackground, $GUI_CHECKED)
	Else
		GUICtrlSetState($chkBackground, $GUI_UNCHECKED)
	EndIf
	chkBackground() ;Applies it to hidden button

	GUICtrlSetData($CCPos[0], $TextRequest)

EndFunc   ;==>applyConfig

Func SaveConfig() ;Saves the controls settings to the config
	;Search Settings------------------------------------------------------------------------
	IniWrite($config, "search", "searchGold", GUICtrlRead($txtMinGold))
	IniWrite($config, "search", "searchElixir", GUICtrlRead($txtMinElixir))
	IniWrite($config, "search", "searchDark", GUICtrlRead($txtMinDarkElixir))
	IniWrite($config, "search", "searchTrophy", GUICtrlRead($txtMinTrophy))

	If GUICtrlRead($chkMeetGxE) = $GUI_CHECKED Then
		IniWrite($config, "search", "conditionGoldElixir", 1)
	Else
		IniWrite($config, "search", "conditionGoldElixir", 0)
	EndIf

	If GUICtrlRead($chkMeetDE) = $GUI_CHECKED Then
		IniWrite($config, "search", "conditionDark", 1)
	Else
		IniWrite($config, "search", "conditionDark", 0)
	EndIf

	If GUICtrlRead($chkMeetTrophy) = $GUI_CHECKED Then
		IniWrite($config, "search", "conditionTrophy", 1)
	Else
		IniWrite($config, "search", "conditionTrophy", 0)
	EndIf
	;Donate Settings-------------------------------------------------------------------------
	If GUICtrlRead($chkRequest) = $GUI_CHECKED Then
		IniWrite($config, "donate", "request", 1)
	Else
		IniWrite($config, "donate", "request", 0)
	EndIf
	IniWrite($config, "donate", "xCCPos", $CCPos[0])
	IniWrite($config, "donate", "yCCPos", $CCPos[1])

	IniWrite($config, "donate", "textrequest", GUICtrlRead($txtRequest))
	;Attack Settings-------------------------------------------------------------------------
	IniWrite($config, "attack", "deploy", _GUICtrlComboBox_GetCurSel($cmbDeploy))
	IniWrite($config, "attack", "algorithm", _GUICtrlComboBox_GetCurSel($cmbAlgorithm))

	If GUICtrlRead($radDeadBases) = $GUI_CHECKED Then
		IniWrite($config, "attack", "mode", 0)
	ElseIf GUICtrlRead($radWeakBases) = $GUI_CHECKED Then
		IniWrite($config, "attack", "mode", 1)
	ElseIf GUICtrlRead($radAllBases) = $GUI_CHECKED Then
		IniWrite($config, "attack", "mode", 2)
	EndIf

	If GUICtrlRead($chkKingAttackDeadBases) = $GUI_CHECKED Then
		IniWrite($config, "attack", "king-dead", 1)
	Else
		IniWrite($config, "attack", "king-dead", 0)
	EndIf
	If GUICtrlRead($chkKingAttackAllBases) = $GUI_CHECKED Then
		IniWrite($config, "attack", "king-all", 1)
	Else
		IniWrite($config, "attack", "king-all", 0)
	EndIf

	If GUICtrlRead($chkQueenAttackDeadBases) = $GUI_CHECKED Then
		IniWrite($config, "attack", "queen-dead", 1)
	Else
		IniWrite($config, "attack", "queen-dead", 0)
	EndIf
	If GUICtrlRead($chkQueenAttackAllBases) = $GUI_CHECKED Then
		IniWrite($config, "attack", "queen-all", 1)
	Else
		IniWrite($config, "attack", "queen-all", 0)
	EndIf
	;Donate Settings-------------------------------------------------------------------------

	;Troop Settings--------------------------------------------------------------------------
	IniWrite($config, "troop", "composition", _GUICtrlComboBox_GetCurSel($cmbTroopComp))

	IniWrite($config, "troop", "troop1", _GUICtrlComboBox_GetCurSel($cmbBarrack1))
	IniWrite($config, "troop", "troop2", _GUICtrlComboBox_GetCurSel($cmbBarrack2))
	IniWrite($config, "troop", "troop3", _GUICtrlComboBox_GetCurSel($cmbBarrack3))
	IniWrite($config, "troop", "troop4", _GUICtrlComboBox_GetCurSel($cmbBarrack4))
	For $i = 0 To 3 ;Covers all 4 Barracks
		IniWrite($config, "troop", "xBarrack" & $i + 1, $barrackPos[$i][0])
		IniWrite($config, "troop", "yBarrack" & $i + 1, $barrackPos[$i][1])
	Next
	;General Settings--------------------------------------------------------------------------
	Local $frmBotPos = WinGetPos($sBotTitle)
	IniWrite($config, "general", "frmBotPosX", $frmBotPos[0])
	IniWrite($config, "general", "frmBotPosY", $frmBotPos[1])
	IniWrite($config, "general", "MaxTrophy", GUICtrlRead($txtMaxTrophy))

	If GUICtrlRead($chkBackground) = $GUI_CHECKED Then
		IniWrite($config, "general", "Background", 1)
	Else
		IniWrite($config, "general", "Background", 0)
	EndIf

	For $i = 0 To 16 ;Covers all Collectors
		IniWrite($config, "general", "xCollector" & $i + 1, $collectorPos[$i][0])
		IniWrite($config, "general", "yCollector" & $i + 1, $collectorPos[$i][1])
	Next

	IniWrite($config, "general", "xTrap", $TrapPos[0])
	IniWrite($config, "general", "yTrap", $TrapPos[1])

EndFunc   ;==>SaveConfig
;========================================================================================
Func SetLog($string) ;Sets the text for the log
	_GUICtrlEdit_AppendText($txtLog, Time() & $string & @CRLF)
	_GUICtrlStatusBar_SetText($statLog, "Status : " & $string)
	_FileWriteLog($hLogFileHandle, $string)
EndFunc   ;==>SetLog

Func Time() ;Gives the time in '[00:00:00 AM/PM]' format
	Return "[" & _NowTime(3) & "] "
EndFunc   ;==>Time

Func _Sleep($iDelay, $iSleep = True)
	Local $iBegin = TimerInit()
	While TimerDiff($iBegin) < $iDelay
		If $RunState = False Then Return True
		If $iSleep = True Then Sleep(100)
	WEnd
	Return False
EndFunc   ;==>_Sleep

Func Click($x, $y, $times = 1, $speed = 0)
	If $times <> 1 Then
		For $i = 0 To ($times - 1)
			ControlClick("BlueStacks App Player", "", "", "left", "1", $x, $y)
			If _Sleep($speed, False) Then ExitLoop
		Next
	Else
		ControlClick("BlueStacks App Player", "", "", "left", "1", $x, $y)
	EndIf
EndFunc   ;==>Click

Func getBSPos()
	$aPos = ControlGetPos("BlueStacks App Player", "", "[CLASS:BlueStacksApp; INSTANCE:1]")
	$tPoint = DllStructCreate("int X;int Y")
	DllStructSetData($tPoint, "X", $aPos[0])
	DllStructSetData($tPoint, "Y", $aPos[1])
	_WinAPI_ClientToScreen(WinGetHandle(WinGetTitle("BlueStacks App Player")), $tPoint)

	$BSpos[0] = DllStructGetData($tPoint, "X")
	$BSpos[1] = DllStructGetData($tPoint, "Y")

	$CtrlHandle = ControlGetHandle("BlueStacks App Player", "", "BlueStacksApp1")
EndFunc   ;==>getBSPos

Func FindPos()
	getBSPos()
	Local $Pos[2]
	While 1
		If _IsPressed("01") Then
			$Pos[0] = MouseGetPos()[0] - $BSpos[0]
			$Pos[1] = MouseGetPos()[1] - $BSpos[1]
			Return $Pos
		EndIf
	WEnd
EndFunc   ;==>FindPos

Func Tab($a, $b)
	$Tab = ""
	For $i = StringLen($a) To $b Step 1
		$Tab &= " "
	Next
	Return $Tab
EndFunc   ;==>Tab

Func CreateLogFile()
	$sLogPath = @ScriptDir & "\logs\" & @YEAR & "-" & @MON & "-" & @MDAY & "_" & @HOUR & "." & @MIN & "." & @SEC & ".log"
	$hLogFileHandle = FileOpen($sLogPath, $FO_APPEND)
EndFunc   ;==>CreateLogFile

Func _ReduceMemory($i_PID = -1)
	Return _WinAPI_EmptyWorkingSet($i_PID)
EndFunc   ;==>_ReduceMemory

Func DisableBS($HWnD, $iButton)
	ConsoleWrite('+ Window Handle: ' & $HWnD & @CRLF)
	$hSysMenu = _GUICtrlMenu_GetSystemMenu($HWnD, 0)
	_GUICtrlMenu_RemoveMenu($hSysMenu, $iButton, False)
	_GUICtrlMenu_DrawMenuBar($HWnD)
EndFunc   ;==>DisableBS

Func EnableBS($HWnD, $iButton)
	ConsoleWrite('+ Window Handle: ' & $HWnD & @CRLF)
	$hSysMenu = _GUICtrlMenu_GetSystemMenu($HWnD, 1)
	_GUICtrlMenu_RemoveMenu($hSysMenu, $iButton, False)
	_GUICtrlMenu_DrawMenuBar($HWnD)
EndFunc   ;==>EnableBS

#EndRegion ### Other Functions ###
;---------------------------------------------------
#Region ### Get Resources+Get Pixels Functions ###
;==============================================================================================================
;===Main Function==============================================================================================
;--------------------------------------------------------------------------------------------------------------
;Checks if the color components exceed $sVari and returns true if they are below $sVari.
;--------------------------------------------------------------------------------------------------------------

Func getGold($x_start, $y_start)
	_CaptureRegion(0, 0, $x_start + 90, $y_start + 20)
	;-----------------------------------------------------------------------------
	Local $x = $x_start, $y = $y_start
	Local $Gold, $i = 0
	While getDigit($x, $y + $i, "Gold") = ""
		If $i >= 15 Then ExitLoop
		$i += 1
	WEnd
	$x = $x_start
	$Gold &= getDigit($x, $y + $i, "Gold")
	$Gold &= getDigit($x, $y + $i, "Gold")
	$Gold &= getDigit($x, $y + $i, "Gold")
	$x += 6
	$Gold &= getDigit($x, $y + $i, "Gold")
	$Gold &= getDigit($x, $y + $i, "Gold")
	$Gold &= getDigit($x, $y + $i, "Gold")
	Return $Gold
EndFunc   ;==>getGold

Func getElixir($x_start, $y_start)
	_CaptureRegion(0, 0, $x_start + 90, $y_start + 20)
	;-----------------------------------------------------------------------------
	Local $x = $x_start, $y = $y_start
	Local $Elixir, $i = 0
	While getDigit($x, $y + $i, "Elixir") = ""
		If $i >= 15 Then ExitLoop
		$i += 1
	WEnd
	$x = $x_start
	$Elixir &= getDigit($x, $y + $i, "Elixir")
	$Elixir &= getDigit($x, $y + $i, "Elixir")
	$Elixir &= getDigit($x, $y + $i, "Elixir")
	$x += 6
	$Elixir &= getDigit($x, $y + $i, "Elixir")
	$Elixir &= getDigit($x, $y + $i, "Elixir")
	$Elixir &= getDigit($x, $y + $i, "Elixir")
	Return $Elixir
EndFunc   ;==>getElixir

Func getDarkElixir($x_start, $y_start)
	_CaptureRegion(0, 0, $x_start + 90, $y_start + 20)
	;-----------------------------------------------------------------------------
	Local $x = $x_start, $y = $y_start
	Local $DarkElixir, $i = 0
	While getDigit($x, $y + $i, "DarkElixir") = ""
		If $i >= 15 Then ExitLoop
		$i += 1
	WEnd
	$x = $x_start
	$DarkElixir &= getDigit($x, $y + $i, "DarkElixir")
	$DarkElixir &= getDigit($x, $y + $i, "DarkElixir")
	$DarkElixir &= getDigit($x, $y + $i, "DarkElixir")
	$x += 6
	$DarkElixir &= getDigit($x, $y + $i, "DarkElixir")
	$DarkElixir &= getDigit($x, $y + $i, "DarkElixir")
	$DarkElixir &= getDigit($x, $y + $i, "DarkElixir")
	Return $DarkElixir
EndFunc   ;==>getDarkElixir

Func getTrophy($x_start, $y_start)
	_CaptureRegion(0, 0, $x_start + 90, $y_start + 20)
	;-----------------------------------------------------------------------------
	Local $x = $x_start, $y = $y_start
	Local $Trophy, $i = 0
	While getDigit($x, $y + $i, "Trophy") = ""
		If $i >= 15 Then ExitLoop
		$i += 1
	WEnd
	$x = $x_start
	$Trophy &= getDigit($x, $y + $i, "Trophy")
	$Trophy &= getDigit($x, $y + $i, "Trophy")
	Return $Trophy
EndFunc   ;==>getTrophy

Func getNormal($x_start, $y_start)
	_CaptureRegion(0, 0, $x_start + 90, $y_start + 20)
	;-----------------------------------------------------------------------------
	Local $x = $x_start, $y = $y_start
	Local $Normal, $i = 0

	$Normal = getDigit($x, $y, "Normal")

	While $Normal = ""
		If $i >= 50 Then ExitLoop
		$i += 1
		$x += 1
		$Normal = getDigit($x, $y, "Normal")
	WEnd


	$Normal &= getDigit($x, $y, "Normal")
	$Normal &= getDigit($x, $y, "Normal")

	Return $Normal
EndFunc   ;==>getNormal

Func getOther($x_start, $y_start, $type)
	_CaptureRegion(0, 0, $x_start + 90, $y_start + 20)
	;-----------------------------------------------------------------------------
	Local $x = $x_start, $y = $y_start
	Local $Number, $i = 0

	Switch $type
		Case "Trophy"
			$Number = getDigit($x, $y, "Other")

			While $Number = ""
				If $i >= 50 Then ExitLoop
				$i += 1
				$x += 1
				$Number = getDigit($x, $y, "Other")
			WEnd

			$Number &= getDigit($x, $y, "Other")
			$Number &= getDigit($x, $y, "Other")
			$Number &= getDigit($x, $y, "Other")
	EndSwitch

	Return $Number
EndFunc   ;==>getOther

;==============================================================================================================
;==============================================================================================================
;===Color Variation============================================================================================
;--------------------------------------------------------------------------------------------------------------
;Checks if the color components exceed $sVari and returns true if they are below $sVari.
;--------------------------------------------------------------------------------------------------------------

Func _ColorCheckVariation($nColor1, $nColor2, $sVari = 5)
	Local $Red1, $Red2, $Blue1, $Blue2, $Green1, $Green2

	$Red1 = Dec(StringMid(String($nColor1), 1, 2))
	$Blue1 = Dec(StringMid(String($nColor1), 3, 2))
	$Green1 = Dec(StringMid(String($nColor1), 5, 2))

	$Red2 = Dec(StringMid(String($nColor2), 1, 2))
	$Blue2 = Dec(StringMid(String($nColor2), 3, 2))
	$Green2 = Dec(StringMid(String($nColor2), 5, 2))

	If Abs($Blue1 - $Blue2) > $sVari Then Return False
	If Abs($Green1 - $Green2) > $sVari Then Return False
	If Abs($Red1 - $Red2) > $sVari Then Return False
	Return True
EndFunc   ;==>_ColorCheckVariation

;==============================================================================================================
;===Check Pixels===============================================================================================
;--------------------------------------------------------------------------------------------------------------
;Using _ColorCheckVariation, checks compares multiple pixels and returns true if they all pass _ColorCheckVariation.
;--------------------------------------------------------------------------------------------------------------

Func boolPixelSearch($pixel1, $pixel2, $pixel3)
	Local $Color1 = _PixelGetColor_GetPixel($pixel1[0], $pixel1[1])
	Local $Color2 = _PixelGetColor_GetPixel($pixel2[0], $pixel2[1])
	Local $Color3 = _PixelGetColor_GetPixel($pixel3[0], $pixel3[1])
	If _ColorCheckVariation($Color1, $pixel1[2], 10) And _ColorCheckVariation($Color2, $pixel2[2], 10) And _ColorCheckVariation($Color3, $pixel3[2], 10) Then Return True
	Return False
EndFunc   ;==>boolPixelSearch

;==============================================================================================================
;===Get Digit Gold=============================================================================================
;--------------------------------------------------------------------------------------------------------------
;Finds pixel color pattern of specific X and Y values, returns digit if pixel color pattern found.
;--------------------------------------------------------------------------------------------------------------

Func getDigit(ByRef $x, $y, $type)
	Local $width = 0

	;Search for digit 0
	$width = 13
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x989579, 6), $c2 = Hex(0x39382E, 6), $c3 = Hex(0x272720, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x978A96, 6), $c2 = Hex(0x393439, 6), $c3 = Hex(0x272427, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x909090, 6), $c2 = Hex(0x363636, 6), $c3 = Hex(0x262626, 6)
		Case Else
			Local $c1 = Hex(0x979797, 6), $c2 = Hex(0x393939, 6), $c3 = Hex(0x272727, 6)
	EndSelect
	Local $pixel1[3] = [$x + 6, $y + 4, $c1], $pixel2[3] = [$x + 7, $y + 7, $c2], $pixel3[3] = [$x + 10, $y + 13, $c3]
	Local $pixel1[3] = [$x + 6, $y + 4, $c1], $pixel2[3] = [$x + 7, $y + 7, $c2], $pixel3[3] = [$x + 10, $y + 13, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width ;Adds to x coordinate to get the next digit
		Return 0
	Else
		$x -= 1 ;Solves the problem when the spaces between the middle goes from 6 to 5 pixels
		Local $pixel1[3] = [$x + 6, $y + 4, $c1], $pixel2[3] = [$x + 7, $y + 7, $c2], $pixel3[3] = [$x + 10, $y + 13, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width ;Changes x coordinate for the next digit.
			Return 0
		Else
			$x += 2 ;Solves the problem when there is 1 pixel space between a set of numbers
			Local $pixel1[3] = [$x + 6, $y + 4, $c1], $pixel2[3] = [$x + 7, $y + 7, $c2], $pixel3[3] = [$x + 10, $y + 13, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 0
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 1
	$width = 6
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x979478, 6), $c2 = Hex(0x313127, 6), $c3 = Hex(0xD7D4AC, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x968895, 6), $c2 = Hex(0x312D31, 6), $c3 = Hex(0xD8C4D6, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x8F8F8F, 6), $c2 = Hex(0x2F2F2F, 6), $c3 = Hex(0xCDCDCD, 6)
		Case Else
			Local $c1 = Hex(0x969696, 6), $c2 = Hex(0x313131, 6), $c3 = Hex(0xD8D8D8, 6)

	EndSelect
	Local $pixel1[3] = [$x + 1, $y + 1, $c1], $pixel2[3] = [$x + 1, $y + 12, $c2], $pixel3[3] = [$x + 4, $y + 12, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 1
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 1, $y + 1, $c1], $pixel2[3] = [$x + 1, $y + 12, $c2], $pixel3[3] = [$x + 4, $y + 12, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 1
		Else
			$x += 2
			Local $pixel1[3] = [$x + 1, $y + 1, $c1], $pixel2[3] = [$x + 1, $y + 12, $c2], $pixel3[3] = [$x + 4, $y + 12, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 1
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 2
	$width = 10
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0xA09E80, 6), $c2 = Hex(0xD8D4AC, 6), $c3 = Hex(0x979579, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0xA0919F, 6), $c2 = Hex(0xD8C4D6, 6), $c3 = Hex(0x978A96, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x989898, 6), $c2 = Hex(0xCDCDCD, 6), $c3 = Hex(0x909090, 6)
		Case Else
			Local $c1 = Hex(0xA0A0A0, 6), $c2 = Hex(0xD8D8D8, 6), $c3 = Hex(0x979797, 6)
	EndSelect
	Local $pixel1[3] = [$x + 1, $y + 7, $c1], $pixel2[3] = [$x + 3, $y + 6, $c2], $pixel3[3] = [$x + 7, $y + 7, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 2
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 1, $y + 7, $c1], $pixel2[3] = [$x + 3, $y + 6, $c2], $pixel3[3] = [$x + 7, $y + 7, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 2
		Else
			$x += 2
			Local $pixel1[3] = [$x + 1, $y + 7, $c1], $pixel2[3] = [$x + 3, $y + 6, $c2], $pixel3[3] = [$x + 7, $y + 7, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 2
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 3
	$width = 10
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x7F7D65, 6), $c2 = Hex(0x070706, 6), $c3 = Hex(0x37362C, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x7F737E, 6), $c2 = Hex(0x070607, 6), $c3 = Hex(0x373236, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x797979, 6), $c2 = Hex(0x070707, 6), $c3 = Hex(0x343434, 6)
		Case Else
			Local $c1 = Hex(0x7F7F7F, 6), $c2 = Hex(0x070707, 6), $c3 = Hex(0x373737, 6)
	EndSelect
	Local $pixel1[3] = [$x + 2, $y + 3, $c1], $pixel2[3] = [$x + 4, $y + 8, $c2], $pixel3[3] = [$x + 5, $y + 13, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 3
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 2, $y + 3, $c1], $pixel2[3] = [$x + 4, $y + 8, $c2], $pixel3[3] = [$x + 5, $y + 13, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 3
		Else
			$x += 2
			Local $pixel1[3] = [$x + 2, $y + 3, $c1], $pixel2[3] = [$x + 4, $y + 8, $c2], $pixel3[3] = [$x + 5, $y + 13, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 3
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 4
	$width = 12
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x282720, 6), $c2 = Hex(0x080806, 6), $c3 = Hex(0x403F33, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x282428, 6), $c2 = Hex(0x080708, 6), $c3 = Hex(0x403A40, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x262626, 6), $c2 = Hex(0x070707, 6), $c3 = Hex(0x3D3D3D, 6)
		Case Else
			Local $c1 = Hex(0x282828, 6), $c2 = Hex(0x080808, 6), $c3 = Hex(0x404040, 6)
	EndSelect
	Local $pixel1[3] = [$x + 2, $y + 3, $c1], $pixel2[3] = [$x + 3, $y + 1, $c2], $pixel3[3] = [$x + 1, $y + 5, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 4
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 2, $y + 3, $c1], $pixel2[3] = [$x + 3, $y + 1, $c2], $pixel3[3] = [$x + 1, $y + 5, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 4
		Else
			$x += 2
			Local $pixel1[3] = [$x + 2, $y + 3, $c1], $pixel2[3] = [$x + 3, $y + 1, $c2], $pixel3[3] = [$x + 1, $y + 5, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 4
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 5
	$width = 10
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x060604, 6), $c2 = Hex(0x040403, 6), $c3 = Hex(0xB7B492, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x060606, 6), $c2 = Hex(0x040404, 6), $c3 = Hex(0xB7A7B6, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x060606, 6), $c2 = Hex(0x040404, 6), $c3 = Hex(0xAFAFAF, 6)
		Case Else
			Local $c1 = Hex(0x060606, 6), $c2 = Hex(0x040404, 6), $c3 = Hex(0xB7B7B7, 6)
	EndSelect
	Local $pixel1[3] = [$x + 5, $y + 4, $c1], $pixel2[3] = [$x + 4, $y + 9, $c2], $pixel3[3] = [$x + 6, $y + 12, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 5
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 5, $y + 4, $c1], $pixel2[3] = [$x + 4, $y + 9, $c2], $pixel3[3] = [$x + 6, $y + 12, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 5
		Else
			$x += 2
			Local $pixel1[3] = [$x + 5, $y + 4, $c1], $pixel2[3] = [$x + 4, $y + 9, $c2], $pixel3[3] = [$x + 6, $y + 12, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 5
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 6
	$width = 11
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x070605, 6), $c2 = Hex(0x040403, 6), $c3 = Hex(0x181713, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x070707, 6), $c2 = Hex(0x040404, 6), $c3 = Hex(0x181618, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x060606, 6), $c2 = Hex(0x030303, 6), $c3 = Hex(0x161616, 6)
		Case Else
			Local $c1 = Hex(0x070707, 6), $c2 = Hex(0x040404, 6), $c3 = Hex(0x181818, 6)
	EndSelect
	Local $pixel1[3] = [$x + 5, $y + 4, $c1], $pixel2[3] = [$x + 5, $y + 9, $c2], $pixel3[3] = [$x + 8, $y + 5, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 6
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 5, $y + 4, $c1], $pixel2[3] = [$x + 5, $y + 9, $c2], $pixel3[3] = [$x + 8, $y + 5, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 6
		Else
			$x += 2
			Local $pixel1[3] = [$x + 5, $y + 4, $c1], $pixel2[3] = [$x + 5, $y + 9, $c2], $pixel3[3] = [$x + 8, $y + 5, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 6
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 7
	$width = 10
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x5E5C4B, 6), $c2 = Hex(0x87856C, 6), $c3 = Hex(0x5D5C4B, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x5F565E, 6), $c2 = Hex(0x877B86, 6), $c3 = Hex(0x5F565E, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x5A5A5A, 6), $c2 = Hex(0x818181, 6), $c3 = Hex(0x5A5A5A, 6)
		Case Else
			Local $c1 = Hex(0x5F5F5F, 6), $c2 = Hex(0x878787, 6), $c3 = Hex(0x5F5F5F, 6)
	EndSelect
	Local $pixel1[3] = [$x + 5, $y + 11, $c1], $pixel2[3] = [$x + 4, $y + 3, $c2], $pixel3[3] = [$x + 7, $y + 7, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 7
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 5, $y + 11, $c1], $pixel2[3] = [$x + 4, $y + 3, $c2], $pixel3[3] = [$x + 7, $y + 7, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 7
		Else
			$x += 2
			Local $pixel1[3] = [$x + 5, $y + 11, $c1], $pixel2[3] = [$x + 4, $y + 3, $c2], $pixel3[3] = [$x + 7, $y + 7, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 7
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 8
	$width = 11
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x27261F, 6), $c2 = Hex(0x302F26, 6), $c3 = Hex(0x26261F, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x272427, 6), $c2 = Hex(0x302B2F, 6), $c3 = Hex(0x26261F, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x252525, 6), $c2 = Hex(0x2D2D2D, 6), $c3 = Hex(0x242424, 6)
		Case Else
			Local $c1 = Hex(0x272727, 6), $c2 = Hex(0x303030, 6), $c3 = Hex(0x262626, 6)
	EndSelect
	Local $pixel1[3] = [$x + 5, $y + 3, $c1], $pixel2[3] = [$x + 5, $y + 10, $c2], $pixel3[3] = [$x + 1, $y + 6, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 8
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 5, $y + 3, $c1], $pixel2[3] = [$x + 5, $y + 10, $c2], $pixel3[3] = [$x + 1, $y + 6, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 8
		Else
			$x += 2
			Local $pixel1[3] = [$x + 5, $y + 3, $c1], $pixel2[3] = [$x + 5, $y + 10, $c2], $pixel3[3] = [$x + 1, $y + 6, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 8
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf

	;Search for digit 9
	$width = 11
	Select
		Case $type = "Gold"
			Local $c1 = Hex(0x302F26, 6), $c2 = Hex(0x050504, 6), $c3 = Hex(0x272720, 6)
		Case $type = "Elixir"
			Local $c1 = Hex(0x302C30, 6), $c2 = Hex(0x050505, 6), $c3 = Hex(0x282427, 6)
		Case $type = "DarkElixir"
			Local $c1 = Hex(0x2E2E2E, 6), $c2 = Hex(0x050505, 6), $c3 = Hex(0x262626, 6)
		Case Else
			Local $c1 = Hex(0x303030, 6), $c2 = Hex(0x050505, 6), $c3 = Hex(0x272727, 6)
	EndSelect
	Local $pixel1[3] = [$x + 5, $y + 5, $c1], $pixel2[3] = [$x + 5, $y + 9, $c2], $pixel3[3] = [$x + 8, $y + 12, $c3]
	If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
		$x += $width
		Return 9
	Else
		$x -= 1
		Local $pixel1[3] = [$x + 5, $y + 5, $c1], $pixel2[3] = [$x + 5, $y + 9, $c2], $pixel3[3] = [$x + 8, $y + 12, $c3]
		If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
			$x += $width
			Return 9
		Else
			$x += 2
			Local $pixel1[3] = [$x + 5, $y + 5, $c1], $pixel2[3] = [$x + 5, $y + 9, $c2], $pixel3[3] = [$x + 8, $y + 12, $c3]
			If boolPixelSearch($pixel1, $pixel2, $pixel3) Then
				$x += $width
				Return 9
			Else
				$x -= 1
			EndIf
		EndIf
	EndIf
	Return ""
EndFunc   ;==>getDigit

;==============================================================================================================
;===Other Functions============================================================================================
;==============================================================================================================

Func _CaptureRegion($iLeft = 0, $iTop = 0, $iRight = 860, $iBottom = 720, $ReturnBMP = False)
	_GDIPlus_BitmapDispose($hBitmap)

	If $ichkBackground = 1 Then
		Local $iW = Number($iRight) - Number($iLeft), $iH = Number($iBottom) - Number($iTop)

		Local $hDC_Capture = _WinAPI_GetWindowDC(ControlGetHandle("BlueStacks App Player", "", "[CLASS:BlueStacksApp; INSTANCE:1]"))
		Local $hMemDC = _WinAPI_CreateCompatibleDC($hDC_Capture)
		Local $hHBitmap = _WinAPI_CreateCompatibleBitmap($hDC_Capture, $iW, $iH)
		Local $hObjectOld = _WinAPI_SelectObject($hMemDC, $hHBitmap)

		DllCall("user32.dll", "int", "PrintWindow", "hwnd", $HWnD, "handle", $hMemDC, "int", 0)
		_WinAPI_SelectObject($hMemDC, $hHBitmap)
		_WinAPI_BitBlt($hMemDC, 0, 0, $iW, $iH, $hDC_Capture, $iLeft, $iTop, 0x00CC0020)

		Global $hBitmap = _GDIPlus_BitmapCreateFromHBITMAP($hHBitmap)

		_WinAPI_DeleteDC($hMemDC)
		_WinAPI_SelectObject($hMemDC, $hObjectOld)
		_WinAPI_ReleaseDC($HWnD, $hDC_Capture)
		_WinAPI_DeleteObject($hHBitmap)
	Else
		getBSPos()
		Local $hHBitmap = _ScreenCapture_Capture("", $iLeft + $BSpos[0], $iTop + $BSpos[1], $iRight + $BSpos[0], $iBottom + $BSpos[1])
		Global $hBitmap = _GDIPlus_BitmapCreateFromHBITMAP($hHBitmap)
	EndIf

	;_GDIPlus_ImageSaveToFile($hBitmap, @ScriptDir & "\Test.bmp")
	If $ReturnBMP Then Return $hBitmap
EndFunc   ;==>_CaptureRegion

Func _PixelGetColor_GetPixel($iX, $iY)
	Local $aPixelColor = _GDIPlus_BitmapGetPixel($hBitmap, $iX, $iY)
	Return Hex($aPixelColor, 6)
EndFunc   ;==>_PixelGetColor_GetPixel

Func _PixelSearch($iLeft, $iTop, $iRight, $iBottom, $iColor, $ColorVariation)
	_CaptureRegion($iLeft, $iTop, $iRight, $iBottom)
	For $x = $iRight - $iLeft To 0 Step -1
		For $y = $iBottom - $iTop To 0 Step -1
			Local $nColor1 = $iColor
			Local $nColor2 = _PixelGetColor_GetPixel($x, $y)
			If _ColorCheckVariation($nColor1, $nColor2, $ColorVariation) Then
				Local $Pos[2] = [$iLeft + $x, $iTop + $y]
				Return $Pos
			EndIf
		Next
	Next
	Return 0
EndFunc   ;==>_PixelSearch


#EndRegion ### Get Resources+Get Pixels Functions ###
;---------------------------------------------------
#Region ### Check Dead Base Functions ###
;==============================================================================================================
;===Main Function==============================================================================================
;--------------------------------------------------------------------------------------------------------------
;Uses imagesearch to see whether a collector is full or semi-full to indicate that it is a dead base
;Returns True if it is, returns false if it is not a dead base
;--------------------------------------------------------------------------------------------------------------

Func ZombieSearch()
	;GUICtrlSetData($Results, "Checking for Zombie. Tolerance: " & $Tolerance & @CRLF, -1)
	$ZombieCount = 0
	For $i = 0 To 3 Step 1 ;Search per area
		IS_Area($i, $Tolerance)
		$ZombieCount += $ZC
	Next
	If $ZombieCount > 0 Then ;if $ZombieCount =1 : $Tolerance=50
		;GUICtrlSetData($Results, "Zombie detected. $ZombieCount = " & $ZombieCount & @CRLF, -1)
		Return True
	Else
		;GUICtrlSetData($Results, "Not Zombie. $ZombieCount = " & $ZombieCount & @CRLF, -1)
		Return False
	EndIf
EndFunc   ;==>ZombieSearch

Func IS_Area($i, $Tolerance) ;Search per area then search per file. If not succeed variant 1 proceed 2 else proceed 3.
	$ZC = 0
	For $s = 0 To ($ZombieFileSets - 1) Step 1
		For $p = 0 + $ZSExclude To 10 Step 1
			If FileExists($E[$s][$p]) Then
				$Area[$p][$i] = _ImageSearchArea($E[$s][$p], 0, $Lx[$i], $Ly[$i], $Rx[$i], $Ry[$i], $IS_x[$p][$i], $IS_y[$p][$i], $Tolerance)
				If $Area[$p][$i] > 0 Then
					$ZC = 1
					ExitLoop (2)
				EndIf
			EndIf
		Next
	Next
EndFunc   ;==>IS_Area

;==============================================================================================================
;===Other Functions============================================================================================
;==============================================================================================================

Func _ImageSearch($findImage, $resultPosition, ByRef $x, ByRef $y, $Tolerance, $hBMP = 0)
	Return _ImageSearchArea($findImage, $resultPosition, 0, 0, @DesktopWidth, @DesktopHeight, $x, $y, $Tolerance, $hBMP)
EndFunc   ;==>_ImageSearch

Func _ImageSearchArea($findImage, $resultPosition, $x1, $y1, $Right, $Bottom, ByRef $x, ByRef $y, $Tolerance, $hBMP = 0)
	;MsgBox(0,"asd","" & $x1 & " " & $y1 & " " & $right & " " & $bottom)
	If $Tolerance > 0 Then $findImage = "*" & $Tolerance & " " & $findImage
	#cs
		If IsString($findImage) Then
		$result = DllCall("COCBot64.dll","str","ImageSearch","int",$x1,"int",$y1,"int",$right,"int",$bottom,"str",$findImage,"ptr",$HBMP)
		If IsArray($result) = False Then $result = DllCall("COCBot32.dll","str","ImageSearch","int",$x1,"int",$y1,"int",$right,"int",$bottom,"str",$findImage,"ptr",$HBMP)
		Else
		$result = DllCall("COCBot64.dll","str","ImageSearch","int",$x1,"int",$y1,"int",$right,"int",$bottom,"ptr",$findImage,"ptr",$HBMP)
		If IsArray($result) = False Then $result = DllCall("COCBot32.dll","str","ImageSearch","int",$x1,"int",$y1,"int",$right,"int",$bottom,"ptr",$findImage,"ptr",$HBMP)
		EndIf
	#ce
	Switch @OSArch
		Case "X64"
			If IsString($findImage) Then
				$result = DllCall("COCBot64.dll", "str", "ImageSearch", "int", $x1, "int", $y1, "int", $Right, "int", $Bottom, "str", $findImage, "ptr", $hBMP)
			Else
				$result = DllCall("COCBot64.dll", "str", "ImageSearch", "int", $x1, "int", $y1, "int", $Right, "int", $Bottom, "ptr", $findImage, "ptr", $hBMP)
			EndIf
		Case "X86"
			If IsString($findImage) Then
				$result = DllCall("COCBot32.dll", "str", "ImageSearch", "int", $x1, "int", $y1, "int", $Right, "int", $Bottom, "str", $findImage, "ptr", $hBMP)
			Else
				$result = DllCall("COCBot32.dll", "str", "ImageSearch", "int", $x1, "int", $y1, "int", $Right, "int", $Bottom, "ptr", $findImage, "ptr", $hBMP)
			EndIf
	EndSwitch

	; If error exit
	If IsArray($result) Then
		If $result[0] = "0" Then Return 0
	Else
		SetLog("Error cannot check for Dead Base, Attacking...")
		SetLog("*If you used 32Bit, use 64Bit.")
		Return 1
	EndIf

	; Otherwise get the x,y location of the match and the size of the image to
	; compute the centre of search
	$array = StringSplit($result[0], "|")

	$x = Int(Number($array[2]))
	$y = Int(Number($array[3]))
	If $resultPosition = 1 Then
		$x = $x + Int(Number($array[4]) / 2)
		$y = $y + Int(Number($array[5]) / 2)
	EndIf
	Return 1
EndFunc   ;==>_ImageSearchArea
#EndRegion ### Check Dead Base Functions ###










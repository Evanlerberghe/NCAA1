# NCAA1
March 2020 NCAA Basketball Outcome Predictor

```
Public Sub Instructions() 'this sub will display an instructionsbox explaining the dashboard and bracket sheets
MsgBox "Welcome to Ethan and Nick's NCAAMB predictor!" & vbCrLf & "Use the Dashboard sheet for individual matchups. First, enter your desired year for data collection into the box at the top middle. " & _
    "Then, scroll through the list boxes and choose your teams. The past 20 years of data for each team will appear in the table, then check the boxes for what data you " & _
    "want graphed and hit the graph button. And lastly, at the bottom is our own game predictor which gives weights to specific stats and predicts the outcome." _
    & vbCrLf & "For March Madness, use our bracket sheet. Just fill in the names of this year's teams, press the button and we'll predict the games for you!" _
    , vbOKOnly, "Instructions"
    
    



End Sub
Sub DeleteIt()
'This sub is to delete the unwanted data catagories from our original datasets
Dim ws As Worksheet

For Each ws In Worksheets
       ws.[A1].EntireColumn.Delete
       ws.[E1].EntireColumn.Delete
       ws.[E1].EntireColumn.Delete
       ws.[F1:O1].EntireColumn.Delete
       ws.[G1:I1].EntireColumn.Delete
       ws.[I1:L1].EntireColumn.Delete
       ws.[K1].EntireColumn.Delete
Next ws

End Sub
Sub Graph1() 'this sub is to graph the users first teams chosen data
'first must dim the chart and series potentially needed. the user gets to choose up to 4 data trends to graph
Dim co As ChartObject
Dim ct As Chart
Dim sc1 As SeriesCollection
Dim ser1 As Series
Dim sc2 As SeriesCollection
Dim ser2 As Series
Dim sc3 As SeriesCollection
Dim ser3 As Series
Dim sc4 As SeriesCollection
Dim ser4 As Series

'must activate my junk sheet because that is wherei put the cells linking the check boxes for the if statements
Worksheets("Junk").Activate

'putting the chart object onto the dashboard
Set co = Sheets("Dashboard").ChartObjects.Add(Range("F34").Left, Range("F34").Top, 600, 300)

Set ct = co.Chart
ct.HasTitle = True
ct.ChartTitle.Text = "Team 1 Trends"
With ct
        .HasLegend = True
    'if statement to determin whether to graph SOS based on whether the box is checked
        If Sheets("Junk").Range("D1") = True Then
            Set sc1 = .SeriesCollection
            Set ser1 = sc1.NewSeries
                With ser1
                    .Name = "SOS"
                    .XValues = Sheets("Junk").Range(Range("W8"), Range("W8").End(xlDown))
                    .Values = Sheets("Junk").Range(Range("D8"), Range("D8").End(xlDown))
                    .ChartType = xlLine
                    
                End With
                
        End If
    'if statement to determine whether to graph Win% based on whether the box is checked
        If Sheets("Junk").Range("E1") = True Then
            Set sc2 = .SeriesCollection
            Set ser2 = sc2.NewSeries
                With ser2
                    .Name = "Win %"
                    .XValues = Sheets("Junk").Range(Range("W8"), Range("W8").End(xlDown))
                    .Values = Sheets("Junk").Range(Range("Q8"), Range("Q8").End(xlDown))
                    .ChartType = xlLine
                    
                End With
                
            
        End If
        
        'if statement to determine whether to graph FG% based on whether the box is checked
        If Sheets("Junk").Range("F1") = True Then
            Set sc3 = .SeriesCollection
            Set ser3 = sc3.NewSeries
                With ser3
                    .Name = "FG %"
                    .XValues = Sheets("Junk").Range(Range("W8"), Range("W8").End(xlDown))
                    .Values = Sheets("Junk").Range(Range("R8"), Range("R8").End(xlDown))
                    .ChartType = xlLine
                End With
                
        End If
       'if statement to determine whether to graph FT% based on whether the box is checked
        If Sheets("Junk").Range("G1") = True Then
            Set sc4 = .SeriesCollection
            Set ser4 = sc4.NewSeries
                With ser4
                    .Name = "FT %"
                    .XValues = Sheets("Junk").Range(Range("W8"), Range("W8").End(xlDown))
                    .Values = Sheets("Junk").Range(Range("S8"), Range("S8").End(xlDown))
                    .ChartType = xlLine
                End With
                
        End If
        
       
        

End With

'must send the user back to the dashboard sheet
        Worksheets("Dashboard").Activate
End Sub
Sub Graph2() 'this sub is to graph the users second teams chosen data
'first must dim the chart and series potentially needed. the user gets to choose up to 4 data trends to graph
Dim co As ChartObject
Dim ct As Chart
Dim sc1 As SeriesCollection
Dim ser1 As Series
Dim sc2 As SeriesCollection
Dim ser2 As Series
Dim sc3 As SeriesCollection
Dim ser3 As Series
Dim sc4 As SeriesCollection
Dim ser4 As Series

'must activate my junk sheet because that is wherei put the cells linking the check boxes for the if statements
Worksheets("Junk").Activate

'putting the chart object onto the dashboard
Set co = Sheets("Dashboard").ChartObjects.Add(Range("R34").Left, Range("R34").Top, 600, 300)
co.Name = "Team A Trends"
Set ct = co.Chart
ct.HasTitle = True
ct.ChartTitle.Text = "Team 2 Trends"
With ct
        .HasLegend = True
        
     'if statement to determine whether to graph SOS based on whether the box is checked
        If Sheets("Junk").Range("D1") = True Then
            Set sc1 = .SeriesCollection
            Set ser1 = sc1.NewSeries
                With ser1
                    .Name = "SOS"
                    .XValues = Sheets("Junk").Range(Range("W8"), Range("W8").End(xlDown))
                    .Values = Sheets("Junk").Range(Range("Z8"), Range("Z8").End(xlDown))
                    .ChartType = xlLine
                    
                End With
                
        End If
   'if statement to determine whether to graph Win% based on whether the box is checked
        If Sheets("Junk").Range("E1") = True Then
            Set sc2 = .SeriesCollection
            Set ser2 = sc2.NewSeries
                With ser2
                    .Name = "Win %"
                    .XValues = Sheets("Junk").Range(Range("W8"), Range("W8").End(xlDown))
                    .Values = Sheets("Junk").Range(Range("AN8"), Range("AN8").End(xlDown))
                    .ChartType = xlLine
                    
                End With
                
            
        End If
        
     'if statement to determine whether to graph FG% based on whether the box is checked
        If Sheets("Junk").Range("F1") = True Then
            Set sc3 = .SeriesCollection
            Set ser3 = sc3.NewSeries
                With ser3
                    .Name = "FG %"
                    .XValues = Sheets("Junk").Range(Range("W8"), Range("W8").End(xlDown))
                    .Values = Sheets("Junk").Range(Range("AO8"), Range("AO8").End(xlDown))
                    .ChartType = xlLine
                End With
                
        End If
        
  'if statement to determine whether to graph FT% based on whether the box is checked
        If Sheets("Junk").Range("G1") = True Then
            Set sc4 = .SeriesCollection
            Set ser4 = sc4.NewSeries
                With ser4
                    .Name = "FT %"
                    .XValues = Sheets("Junk").Range(Range("W8"), Range("W8").End(xlDown))
                    .Values = Sheets("Junk").Range(Range("AP8"), Range("AP8").End(xlDown))
                    .ChartType = xlLine
                End With
                
        End If
        
        
        
        

End With
'send user back to dashboard
Worksheets("Dashboard").Activate
End Sub
Sub Delchart() 'this method deletes all charts on the sheets instead of just stacking up the charts the user makes
Dim cht As ChartObject

'using a for each statement to delete every chart on the active sheet
For Each cht In ActiveSheet.ChartObjects
cht.Delete
Next cht


End Sub

' We start by declaring all of the variables we will need in order to complete calculate who will win each game in the bracket.
Public Sub Vlookup()
Dim wsFunc As WorksheetFunction: Set wsFunc = Application.WorksheetFunction
Dim YeAr As String
YeAr = Sheets("Dashboard").Range("N55")
If YeAr = "0" Then
            MsgBox "Please Enter a Year at the Top of the Dashboard Tab"
            Exit Sub
End If
Dim ws As Worksheet: Set ws = Worksheets(YeAr)
Dim wrs As Worksheet: Set wrs = Worksheets("Bracket")
Dim rngLook As Range: Set rngLook = ws.Range("A1:R370")
Dim rngLook2 As Range: Set rngLook2 = wrs.Range("A1:T75")
Dim cellNum As Range
Dim currName As String
Dim TeamA As String
Dim TeamB As String
Dim GamesA As Variant
Dim GamesB As Variant
Dim WinsA As Variant
Dim WinsB As Variant
Dim LossesA As Variant
Dim LossesB As Variant
Dim SOSA As Variant
Dim SOSB As Variant
Dim PointsA As Variant
Dim PointsB As Variant
Dim FGMA As Variant
Dim FGMB As Variant
Dim FGAA As Variant
Dim FGAB As Variant
Dim FTMA As Variant
Dim FTMB As Variant
Dim ORA As Variant
Dim ORB As Variant
Dim DRA As Variant
Dim DRB As Variant
Dim ASSA As Variant
Dim ASSB As Variant
Dim STLA As Variant
Dim STLB As Variant
Dim BLKA As Variant
Dim BLKB As Variant
Dim TOVA As Variant
Dim TOVB As Variant
Dim PFA As Variant
Dim PFB As Variant
Dim SeedSpread As Integer
Dim TERA As Integer
Dim TERB As Integer
Dim TeamX As String
Dim TeamY As String
AutoEnd = 0
On Error GoTo ErrorHandler
'This sets up the starting point where the loop should begin, so that the correct teams are pulled.

'High team low Team
T = 8
U = 10

'High seed low seed
S = 8
v = 10

'Outcome

W = 9
B = 1

'Initializing loop

For B = 1 To 16

Worksheets("Bracket").Range("AA30").ClearContents

'TeamA is the higher seeded team, TeamB is the lower seeded team

TeamA = Worksheets("Bracket").Range("C" & T).Value

TeamB = Worksheets("Bracket").Range("C" & U).Value

SeedA = Worksheets("Bracket").Range("B" & S).Value

SeedB = Worksheets("Bracket").Range("B" & v).Value



Trim (TeamA)

Trim (TeamB)




'Below, we begin compiling the data for each team, allowing the formula to compare the different aspects of each team.

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)

'TERA and TERB are team efficiency ratings for each of the teams. Most of this formula is pulled from Wayne L. Winston's book 'Mathletics' in which he explains why each weight is chosen for each measure of team effieciency.
'Each of the different weights are chosen in order to most accurately represent the value added of each individual item to the team's overall performance. These numbers are all divided by the number of games each team has played in order to make the comparisons even.
'The weights chosen include a x1.0 rating to the points scale, meaning that the overall measure is also equivalent to the theoretical scores of the game. I added the "SOSA" and "SOSB" factors, which relate to a strength of schedule rating I pulled from our data, collected from SRCBB.

TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

'According to Aaron Kessler, a Las Vegas oddsmaker for the Golden Nuggest Casino, a rough estimate of point spread can be generated by subtracting a high seed from a low seed and multiplying it by a value sligtly over 1.
'Here, the pointspread is used as an added value to the underdog if necessary, in order to boost their chance of winning the game.
SeedSpread = SeedB - SeedA
SeedSpread = SeedSpread * 1.5
'The Rnd function is used in order to generate a value between 0 and 1. This function is then compared to the historical odds that the lower seed upsets the higher seed.
'If the Rnd value is lower than or equal to the historical chance, then it is the equivalent of a real-life "Upset" scenario.
'If this occurs, the spread is then added to the losing team's TER in order to give them the advantage of a theoretical upset
'However, if the gap between teams is too high, even the uposet condition will not overcome this, similar to how in real life even if the 16 seed got an advantage, the number 1 seed would typically still beat them out of skill.
Chance = Rnd
If SeedA = 1 Then Poss = 0.008333
If SeedA = 2 Then Poss = 0.058333
If SeedA = 3 Then Poss = 0.133333
If SeedA = 4 Then Poss = 0.2
If SeedA = 5 Then Poss = 0.383333
If SeedA = 6 Then Poss = 0.358333
If SeedA = 7 Then Poss = 0.408333
If SeedA = 8 Then Poss = 0.516667

If Chance <= Poss Then TERB = TERB + SeedSpread


' We concatenate the seed with the team name so that the second round can also run upset odds
TeamA = SeedA & "  " & TeamA

TeamB = SeedB & "  " & TeamB

'The winner continues on in the bracket

If TERA > TERB Then WIN = TeamA Else WIN = TeamB



Worksheets("Bracket").Range("D" & W) = WIN

'Increase all of the variables so the loop works
T = T + 4
U = U + 4
S = S + 4
v = v + 4
W = W + 4

Next B

' Now we repeat this process for the other side, as well as acrossed multiple rounds until the championship


' Round 1 right

'High team low Team
T = 8
U = 10

'High seed low seed
S = 8
v = 10

'Outcome

W = 9
B = 1

For B = 1 To 16

Worksheets("Bracket").Range("AA30").ClearContents

TeamA = Worksheets("Bracket").Range("R" & T).Value

TeamB = Worksheets("Bracket").Range("R" & U).Value

SeedA = Worksheets("Bracket").Range("S" & S).Value

SeedB = Worksheets("Bracket").Range("S" & v).Value


'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

SeedSpread = SeedB - SeedA
SeedSpread = SeedSpread * 1.5
Chance = Rnd
If SeedA = 1 Then Poss = 0.008333
If SeedA = 2 Then Poss = 0.058333
If SeedA = 3 Then Poss = 0.133333
If SeedA = 4 Then Poss = 0.2
If SeedA = 5 Then Poss = 0.383333
If SeedA = 6 Then Poss = 0.358333
If SeedA = 7 Then Poss = 0.408333
If SeedA = 8 Then Poss = 0.516667

If Chance <= Poss Then TERB = TERB + SeedSpread

TeamA = SeedA & "  " & TeamA

TeamB = SeedB & "  " & TeamB

If TERA > TERB Then WIN = TeamA Else WIN = TeamB
Worksheets("Bracket").Range("Q" & W) = WIN

T = T + 4
U = U + 4
S = S + 4
v = v + 4
W = W + 4

Next B

 
 



'SECOND ROUND




'Next
'High team low Team
T = 9
U = 13

'Outcome

W = 11
B = 1

For B = 1 To 8

'We use TeamX and TeamY as a way to keep the concatenated strings together, seperate from the Vlookup TeamA and TeamB's.

TeamX = Worksheets("Bracket").Range("D" & T).Value

TeamY = Worksheets("Bracket").Range("D" & U).Value

SeedA = Left(TeamX, 1)
SeedB = Left(TeamY, 1)
SeedA = CInt(SeedA)
SeedB = CInt(SeedB)
TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)
If SeedA > SeedB Then SeedSpread = SeedA - SeedB Else SeedSpread = SeedB - SeedA
SeedSpread = SeedSpread * 1.5
Chance = Rnd

'Second round has twice as many possibilities, thus twice as many values are needed.
If SeedA = 1 And SeedB = 8 Then Poss = 0.172413793
If SeedA = 1 And SeedB = 9 Then Poss = 0.098360656
If SeedA = 16 And SeedB = 8 Then Poss = 0
If SeedA = 16 And SeedB = 9 Then Poss = 0
If SeedA = 5 And SeedB = 4 Then Poss = 0.419354839
If SeedA = 5 And SeedB = 13 Then Poss = 0.16666667
If SeedA = 12 And SeedB = 4 Then Poss = 0.264705882
If SeedA = 12 And SeedB = 13 Then Poss = 0.25
If SeedA = 6 And SeedB = 3 Then Poss = 0.384615385
If SeedA = 6 And SeedB = 14 Then Poss = 0.08333333
If SeedA = 11 And SeedB = 3 Then Poss = 0.33333333
If SeedA = 11 And SeedB = 14 Then Poss = 0
If SeedA = 7 And SeedB = 2 Then Poss = 0.298507463
If SeedA = 7 And SeedB = 15 Then Poss = 0.33333333
If SeedA = 10 And SeedB = 2 Then Poss = 0.37777778
If SeedA = 10 And SeedB = 15 Then Poss = 0


If Chance <= Poss Then If SeedA > SeedB Then TERB = TERB + SeedSpread Else TERA = TERA + SeedSpread

If TERA > TERB Then WIN = TeamX Else WIN = TeamY


Worksheets("Bracket").Range("E" & W) = WIN
T = T + 8
U = U + 8
W = W + 8

Next B


'SR right


'High team low Team
T = 9
U = 13


'Outcome

W = 11
B = 1

For B = 1 To 8



TeamX = Worksheets("Bracket").Range("Q" & T).Value

TeamY = Worksheets("Bracket").Range("Q" & U).Value

SeedA = Left(TeamX, 1)
SeedB = Left(TeamY, 1)
SeedA = CInt(SeedA)
SeedB = CInt(SeedB)
TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)
If SeedA > SeedB Then SeedSpread = SeedA - SeedB Else SeedSpread = SeedB - SeedA

SeedSpread = SeedSpread * 1.5
Chance = Rnd
If SeedA = 1 And SeedB = 8 Then Poss = 0.172413793
If SeedA = 1 And SeedB = 9 Then Poss = 0.098360656
If SeedA = 16 And SeedB = 8 Then Poss = 0
If SeedA = 16 And SeedB = 9 Then Poss = 0
If SeedA = 5 And SeedB = 4 Then Poss = 0.419354839
If SeedA = 5 And SeedB = 13 Then Poss = 0.16666667
If SeedA = 12 And SeedB = 4 Then Poss = 0.264705882
If SeedA = 12 And SeedB = 13 Then Poss = 0.25
If SeedA = 6 And SeedB = 3 Then Poss = 0.384615385
If SeedA = 6 And SeedB = 14 Then Poss = 0.08333333
If SeedA = 11 And SeedB = 3 Then Poss = 0.33333333
If SeedA = 11 And SeedB = 14 Then Poss = 0
If SeedA = 7 And SeedB = 2 Then Poss = 0.298507463
If SeedA = 7 And SeedB = 15 Then Poss = 0.33333333
If SeedA = 10 And SeedB = 2 Then Poss = 0.37777778
If SeedA = 10 And SeedB = 15 Then Poss = 0


If Chance <= Poss Then If SeedA > SeedB Then TERB = TERB + SeedSpread Else TERA = TERA + SeedSpread
If TERA > TERB Then WIN = TeamX Else WIN = TeamY

Worksheets("Bracket").Range("P" & W) = WIN

T = T + 8
U = U + 8
W = W + 8

Next B


'THIRD ROUND

'High team low Team
T = 11
U = 19


'Outcome

W = 15
B = 1

For B = 1 To 4



TeamX = Worksheets("Bracket").Range("E" & T).Value

TeamY = Worksheets("Bracket").Range("E" & U).Value

TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

If TERA > TERB Then WIN = TeamX Else WIN = TeamY

Worksheets("Bracket").Range("F" & W) = WIN

T = T + 16
U = U + 16
'S = S + 4
'V  = V + 4
W = W + 16

Next B



'High team low Team
T = 11
U = 19


'Outcome

W = 15
B = 1

For B = 1 To 4



TeamX = Worksheets("Bracket").Range("P" & T).Value

TeamY = Worksheets("Bracket").Range("P" & U).Value

TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

If TERA > TERB Then WIN = TeamX Else WIN = TeamY


Worksheets("Bracket").Range("O" & W) = WIN

T = T + 16
U = U + 16
'S = S + 4
'V  = V + 4
W = W + 16

Next B


'FOURTH ROUND


'High team low Team
T = 15
U = 31

'Outcome

W = 23
B = 1

For B = 1 To 2



TeamX = Worksheets("Bracket").Range("F" & T).Value

TeamY = Worksheets("Bracket").Range("F" & U).Value

TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

If TERA > TERB Then WIN = TeamX Else WIN = TeamY


Worksheets("Bracket").Range("H" & W) = WIN

T = T + 32
U = U + 32
W = W + 32

Next B



'High team low Team
T = 15
U = 31


'Outcome

W = 23
B = 1

For B = 1 To 2



TeamX = Worksheets("Bracket").Range("O" & T).Value

TeamY = Worksheets("Bracket").Range("O" & U).Value

TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

If TERA > TERB Then WIN = TeamX Else WIN = TeamY

Worksheets("Bracket").Range("M" & W) = WIN

T = T + 32
U = U + 32
W = W + 32

Next B



'FINAL FOUR

'High team low Team
T = 23
U = 55



'Outcome

W = 30
B = 1

'For B = 1 To 1



TeamX = Worksheets("Bracket").Range("H" & T).Value

TeamY = Worksheets("Bracket").Range("H" & U).Value
TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

If TERA > TERB Then WIN = TeamX Else WIN = TeamY


Worksheets("Bracket").Range("J" & W) = WIN

T = T + 32
U = U + 32
W = W + 32

'Next B



'High team low Team
T = 23
U = 55


'Outcome

W = 48
B = 1

'For B = 1 To 1



TeamX = Worksheets("Bracket").Range("M" & T).Value

TeamY = Worksheets("Bracket").Range("M" & U).Value

TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

If TERA > TERB Then WIN = TeamX Else WIN = TeamY


Worksheets("Bracket").Range("K" & W) = WIN

T = T + 32
U = U + 32

W = W + 32

'Next B


'CHAMPIONSHIP

'High team low Team
T = 30
U = 48


'Outcome

W = 39
B = 1

'For B = 1 To 1



TeamX = Worksheets("Bracket").Range("J" & T).Value

TeamY = Worksheets("Bracket").Range("K" & U).Value

TeamA = Split(TeamX, "  ")(1)
TeamB = Split(TeamY, "  ")(1)

'Games
GamesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 2, False)
GamesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 2, False)

'Wins
WinsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 3, False)
WinsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 3, False)

'Losses
LossesA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 4, False)
LossesB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 4, False)

'Strength of Schedule
SOSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 5, False)
SOSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 5, False)

'Points
PointsA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 6, False)
PointsB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 6, False)

'Field Goals Made
FGMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 7, False)
FGMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 7, False)

'Field Goals Attempted
FGAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 8, False)
FGAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 8, False)

'Free Throws Made
FTMA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 9, False)
FTMB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 9, False)

'Free Throws Attempted
FTAA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 10, False)
FTAB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 10, False)

'Offensive Rebounds
ORA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 11, False)
ORB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 11, False)

'Defensive Rebounds
DRA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 12, False)
DRB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 12, False)

'Assists
ASSA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 13, False)
ASSB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 13, False)

'Steals
STLA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 14, False)
STLB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 14, False)

'Blocks
BLKA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 15, False)
BLKB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 15, False)

'Turnovers
TOVA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 16, False)
TOVB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 16, False)

'Personal Fouls
PFA = Application.WorksheetFunction.Vlookup(TeamA, rngLook, 17, False)
PFB = Application.WorksheetFunction.Vlookup(TeamB, rngLook, 17, False)



TERA = (PointsA / GamesA) + ((FGMA / GamesA) * 0.4) + ((FGAA / GamesA) * -0.7) + (((FTAA / GamesA) - (FTMA / GamesA)) * -0.4) + ((ORA / GamesA) * 0.7) + (((DRA / GamesA) - (ORA / GamesA)) * 0.3) + (STLA / GamesA) + ((ASSA / GamesA) * 0.7) + ((BLKA / GamesA) * 0.7) + ((PFA / GamesA) * -0.4) + ((TOVA / GamesA) * -1) + (SOSA * 1)
TERB = (PointsB / GamesB) + ((FGMB / GamesB) * 0.4) + ((FGAB / GamesB) * -0.7) + (((FTAB / GamesB) - (FTMB / GamesB)) * -0.4) + ((ORB / GamesB) * 0.7) + (((DRB / GamesB) - (ORB / GamesB)) * 0.3) + (STLB / GamesB) + ((ASSB / GamesB) * 0.7) + ((BLKB / GamesB) * 0.7) + ((PFB / GamesB) * -0.4) + ((TOVB / GamesB) * -1) + (SOSB * 1)

If TERA > TERB Then WIN = TeamX Else WIN = TeamY

Worksheets("Bracket").Range("J" & W) = WIN

T = T + 32
U = U + 32

W = W + 32
AutoEnd = 1

If AutoEnd = 1 Then GoTo AutoEnder

ErrorHandler:     MsgBox ("Either the team " & TeamA & " or the team " & TeamB & " did not play this year, or is spelled wrong. Please check your spelling against the drop-down lists on the dashboard tab, and try again.")



AutoEnder:
    AutoEnd = AutoEnd + 1

End Sub
Sub PastData()
Dim wsFunc As WorksheetFunction: Set wsFunc = Application.WorksheetFunction
Dim YeAr As String
YeAr = Sheets("Dashboard").Range("B1")
Dim ws As Worksheet: Set ws = Worksheets(YeAr)
Dim rngLook As Range: Set rngLook = ws.Range("A1:AL370")
Dim cellNum As Range
Dim currName As String

TeamA = Sheets("Dashboard").Range("E3")
Trim (TeamA)
TeamB = Sheets("Dashboard").Range("K3")
Trim (TeamB)

ZZ = 2021
zzz = 7

For zzz = 7 To 27
Sheets("Dashboard").Range("A" & zzz, "S" & zzz) = Sheets("ZZ").Range("A1:Q1").Offset(Sheets("Junk").Range("A1") - 1, 0)
Next zzz





End Sub

Sub FindReplaceAll()
'PURPOSE: Find & Change all Names in the Brackets to only include team names, not with any other words or markings such as "NCAA"

Dim sht As Worksheet
Dim fnd As Variant
Dim rplc As Variant

fnd = " NCAA"
rplc = ""

For Each sht In ActiveWorkbook.Worksheets
  sht.Cells.Replace what:=fnd, Replacement:=rplc, _
    LookAt:=xlPart, SearchOrder:=xlByRows, MatchCase:=False, _
    SearchFormat:=False, ReplaceFormat:=False
Next sht

End Sub

Sub Reset()
    Worksheets("Bracket").Range("D9:Q70").ClearContents
End Sub
```

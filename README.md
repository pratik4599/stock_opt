

# endpoints

"https://optstk.herokuapp.com/get_fut?statename="
to open stock future chart

"https://optstk.herokuapp.com/get_opt?statename="
to see all availble options for particular stock

https://optstk.herokuapp.com/req_opt?statename=x&ltp=x
to see near atm option strikes for particular stock


# excel macros to call backend

```

 Public interval As Double
Sub futlink()


Dim StrURL As String, fixedURL As String
fixedURL = "https://optstk.herokuapp.com/get_fut?statename="

For Each rng In Selection
        If rng.Value <> 0 Then
        StrURL = fixedURL & rng
        ThisWorkbook.FollowHyperlink StrURL
        interval = Now + TimeValue("00:00:01")
        End If
    Next rng
End Sub


Sub optlink()

Dim StrURL As String, fixedURL As String
fixedURL2 = "https://optstk.herokuapp.com/req_opt?statename="

For Each rng In Selection
        If rng.Value <> 0 Then
        ltp = rng.Offset(0, 1).Value
        StrURL2 = fixedURL2 & rng & "&" & "ltp=" & ltp
        Debug.Print StrURL2
        ThisWorkbook.FollowHyperlink StrURL2
        interval = Now + TimeValue("00:00:01")
        End If
    Next rng
End Sub

```


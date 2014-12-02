robocopy
========
Sistema para cópia e backup de arquivos.

```basic

        Dim srce As String = txt_origem.Text
        Dim dest As String = txt_destino.Text

        If Not My.Computer.FileSystem.DirectoryExists(srce) Then
            MsgBox("the source folder does not exist")
            Exit Sub
        End If

        MyProcess = New Process

        With MyProcess.StartInfo
            .FileName = "c:\windows\system32\robocopy.exe"
            .Arguments = """" & srce & """ """ & dest & """ /e /r:0"
            .UseShellExecute = False
            .CreateNoWindow = True
            .RedirectStandardInput = False
            .RedirectStandardOutput = True
            .RedirectStandardError = False
        End With

        txt_saida.Clear()
        txt_saida.ScrollToCaret() 'quebra de linha
        txt_saida.ScrollBars = RichTextBoxScrollBars.ForcedBoth ' barra de rolagem vertical e orizontal
        MyProcess.Start()
        MyProcess.BeginOutputReadLine()     'pular linha

```
![](http://marcosjunior.hol.es/git-hub/robocopy.png)

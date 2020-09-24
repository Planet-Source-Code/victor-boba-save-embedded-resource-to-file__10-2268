<div align="center">

## Save Embedded Resource to File


</div>

### Description

To save an Embedded Resource and save to file. This will take any embedded resource and save it to any filename you want.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Victor Boba](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/victor-boba.md)
**Level**          |Intermediate
**User Rating**    |4.7 (14 globes from 3 users)
**Compatibility**  |VB\.NET
**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__10-2.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/victor-boba-save-embedded-resource-to-file__10-2268/archive/master.zip)





### Source Code

```
' Notes:
        ' The file that you add to the project has to have the Build Action
        ' property changed to "Embedded Resource" for this to work. This will add the file
        ' to the project as a resource and not a compiled item.
        '
        Dim ResStream As System.IO.Stream
        ' This is the name of your applications namespace followed by the name of the file that's embedded.
        ' So if your namespace is "MyProject" and the name of the file is "BlankDatabase.mdb" then
        ' the value for the sResPath would be "MyProject.BlankDatabase.mdb".
        Dim sResPath As String = "AnimalControl.db.mdb"
        Dim NewFilePathName As String = sPath
        Dim numBytesRead As Integer = 0
        ' Get the Embedded Resource
        ResStream = System.Reflection.Assembly.GetExecutingAssembly.GetManifestResourceStream(sResPath)
        Dim numBytesToRead As Integer = CInt(ResStream.Length)
        Dim bytes(ResStream.Length) As Byte
        While numBytesToRead + 1 > 0
          Dim n As Integer = ResStream.Read(bytes, numBytesRead, numBytesToRead)
          ' The end of the file has been reached.
          If n = 0 Then
            Exit While
          End If
          numBytesRead += n
          numBytesToRead -= n
        End While
        ' Save the resource to file
        Dim fs As New FileStream(NewFilePathName, FileMode.Create)
        fs.Write(bytes, 0, bytes.Length)
        fs.Close()
```


# Modern File Explorer
Microsoft's new Explorer developed in React Native specifically for Windows 10X. Unfortunately, its development was discontinued ([or not?](https://www.windowscentral.com/software-apps/windows-11/exclusive-microsoft-readies-groundbreaking-ai-focused-windows-release-as-new-leadership-takes-the-helm)) before the Explorer was finalized. 
This modification is being developed to support local hard disks, cart support and if possible add search.
## The official mockup of the finished File Explorer:
![image](https://github.com/efsfssf/Modern-File-Explorer-For-Windows-Core-OS/assets/29039987/99e25adb-0d36-46ea-8419-8a195c814adb)

You can see support for Downloads, Recycle Bin, User Folder sections on the bottom left corner

## API Modern File Explorer
### GET /sync/features
Example answer
```
idk ☹️
```

### GET /sync/account/instanceids
Example answer
```
idk ☹️
```

### POST /subscriptions
Example payload
```JSON
{
   "messageType":"itemChanged",
   "resource":"http://localhost:9001/me/drive/items/root&orderby=folder,name asc",
   "resourceData":{
      "driveId":"me",
      "itemId":"root",
      "orderby":"&orderby=folder,name asc"
   }
}
```
Example answer
```JSON
{
   "id":"CollectionEnumeration_OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103_OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103_folder,name asc",
   "messageType":"itemChanged",
   "resource":"http://localhost:9001/drives/OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103/items/OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
   "resourceData":{
      "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
      "itemId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
      "orderby":"folder,name asc"
   }
}
```

### POST /subscriptions (ПРИ НАЖАТИИ НА КНОПКУ "ЗАГРУЗКИ")
Example payload
```JSON
{
  "messageType": "itemChanged",
  "resource": "http://localhost:9001/drives/local/items/4007390500%2C562949953454108&orderby=folder,name asc",
  "resourceData": {
    "driveId": "local",
    "itemId": "4007390500,562949953454108",
    "orderby": "&orderby=folder,name asc"
  }
}
```
Example answer
```JSON
{
   "id":"CollectionEnumeration_local_4007390500,562949953454108_folder,name asc",
   "messageType":"itemChanged",
   "resource":"http://localhost:9001/drives/local/items/4007390500,562949953454108",
   "resourceData":{
      "driveId":"local",
      "itemId":"4007390500,562949953454108",
      "orderby":"folder,name asc"
   }
}
```

### GET /drives 
Example answer
```JSON
{
   "value":[
      {
         "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
         "name":"OneDrive - Personal",
         "driveType":"syncRoot",
         "root":{
            
         }
      },
      {
         "id":"local",
         "name":"Local drive",
         "driveType":"local",
         "quota":{
            "total":239335370752,
            "used":226654322688,
            "remaining":12681048064,
            "state":"nearing"
         },
         "root":{
            
         }
      }
   ]
}
```

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
# GET /me/drive/items/root/children?$top=100&$expand=thumbnails&select=*,webDavUrl
Example answer
```JSON
[
   {
      "value":[
         {
            "id":"4007390500,1688849860345539",
            "name":"Documents",
            "lastModifiedDateTime":"2023-11-23 19:08:02Z",
            "createdDateTime":"2023-11-23 19:08:04Z",
            "lastAccessedDateTime":"2023-12-11 12:09:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/Documents",
               "createdDateTime":"2023-11-23 19:08:04Z",
               "lastAccessedDateTime":"2023-12-11 12:09:04Z",
               "lastModifiedDateTime":"2023-11-23 19:08:02Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899294",
            "name":"JokeWinLock",
            "lastModifiedDateTime":"2023-11-03 13:50:39Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-12-11 12:12:48Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/JokeWinLock",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-12-11 12:12:48Z",
               "lastModifiedDateTime":"2023-11-03 13:50:39Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883719",
            "name":"wpfmdi-master",
            "lastModifiedDateTime":"2023-11-03 13:49:33Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-12-11 12:12:48Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/wpfmdi-master",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-12-11 12:12:48Z",
               "lastModifiedDateTime":"2023-11-03 13:49:33Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976815533",
            "name":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ￑ﾋ",
            "lastModifiedDateTime":"2023-12-08 17:42:25Z",
            "createdDateTime":"2023-11-03 13:44:36Z",
            "lastAccessedDateTime":"2023-12-11 14:30:20Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ￑ﾋ",
               "createdDateTime":"2023-11-03 13:44:36Z",
               "lastAccessedDateTime":"2023-12-11 14:30:20Z",
               "lastModifiedDateTime":"2023-12-08 17:42:25Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899291",
            "name":"￐ﾘ￐ﾷ￐ﾱ￑ﾀ￐ﾰ￐ﾽ￐ﾽ￐ﾾ￐ﾵ",
            "lastModifiedDateTime":"2023-11-03 13:50:39Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-12-10 20:07:10Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾘ￐ﾷ￐ﾱ￑ﾀ￐ﾰ￐ﾽ￐ﾽ￐ﾾ￐ﾵ",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-12-10 20:07:10Z",
               "lastModifiedDateTime":"2023-11-03 13:50:39Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976815219",
            "name":"￐ﾘ￐ﾷ￐ﾾ￐ﾱ￑ﾀ￐ﾰ￐ﾶ￐ﾵ￐ﾽ￐ﾸ￑ﾏ",
            "lastModifiedDateTime":"2023-12-08 17:42:25Z",
            "createdDateTime":"2023-11-03 13:44:34Z",
            "lastAccessedDateTime":"2023-12-11 15:27:58Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾘ￐ﾷ￐ﾾ￐ﾱ￑ﾀ￐ﾰ￐ﾶ￐ﾵ￐ﾽ￐ﾸ￑ﾏ",
               "createdDateTime":"2023-11-03 13:44:34Z",
               "lastAccessedDateTime":"2023-12-11 15:27:58Z",
               "lastModifiedDateTime":"2023-12-08 17:42:25Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899783",
            "name":"￐ﾘ￐ﾽ￐ﾴ￐ﾸ￐ﾲ￐ﾸ￐ﾴ￑ﾃ￐ﾰ￐ﾻ￑ﾌ￐ﾽ￑ﾋ￐ﾹ ￐﾿￑ﾀ￐ﾾ￐ﾵ￐ﾺ￑ﾂ",
            "lastModifiedDateTime":"2023-11-03 13:50:41Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-12-10 20:07:12Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾘ￐ﾽ￐ﾴ￐ﾸ￐ﾲ￐ﾸ￐ﾴ￑ﾃ￐ﾰ￐ﾻ￑ﾌ￐ﾽ￑ﾋ￐ﾹ ￐﾿￑ﾀ￐ﾾ￐ﾵ￐ﾺ￑ﾂ",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-12-10 20:07:12Z",
               "lastModifiedDateTime":"2023-11-03 13:50:41Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883869",
            "name":"￐ﾚ￑ﾃ￑ﾀ￑ﾁ￐ﾾ￐ﾲ￐ﾰ￑ﾏ",
            "lastModifiedDateTime":"2023-11-03 13:49:33Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-12-10 20:07:10Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾚ￑ﾃ￑ﾀ￑ﾁ￐ﾾ￐ﾲ￐ﾰ￑ﾏ",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-12-10 20:07:10Z",
               "lastModifiedDateTime":"2023-11-03 13:49:33Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,6192449487692315",
            "name":"￐ﾠ￐ﾰ￐ﾱ￐ﾾ￑ﾇ￐ﾸ￐ﾹ ￑ﾁ￑ﾂ￐ﾾ￐ﾻ",
            "lastModifiedDateTime":"2023-12-10 07:12:54Z",
            "createdDateTime":"2023-11-03 13:44:34Z",
            "lastAccessedDateTime":"2023-12-11 14:35:44Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾠ￐ﾰ￐ﾱ￐ﾾ￑ﾇ￐ﾸ￐ﾹ ￑ﾁ￑ﾂ￐ﾾ￐ﾻ",
               "createdDateTime":"2023-11-03 13:44:34Z",
               "lastAccessedDateTime":"2023-12-11 14:35:44Z",
               "lastModifiedDateTime":"2023-12-10 07:12:54Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976849388",
            "name":"￑ﾃ￑ﾇ￐ﾵ￐ﾱ￐ﾰ",
            "lastModifiedDateTime":"2023-11-03 13:47:23Z",
            "createdDateTime":"2023-11-03 13:47:20Z",
            "lastAccessedDateTime":"2023-12-10 20:07:08Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￑ﾃ￑ﾇ￐ﾵ￐ﾱ￐ﾰ",
               "createdDateTime":"2023-11-03 13:47:20Z",
               "lastAccessedDateTime":"2023-12-10 20:07:08Z",
               "lastModifiedDateTime":"2023-11-03 13:47:23Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890511",
            "name":"01.04.2020_￐ﾭ￐ﾞ￐ﾟ_1_￐ﾸ￑ﾁ￐﾿-11,_2￐ﾸ￑ﾁ￐﾿-9.docx",
            "lastModifiedDateTime":"2020-04-02 14:39:56Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/01.04.2020_￐ﾭ￐ﾞ￐ﾟ_1_￐ﾸ￑ﾁ￐﾿-11,_2￐ﾸ￑ﾁ￐﾿-9.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-04-02 14:39:56Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":19461,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899358",
            "name":"1 ￑ﾇ￐ﾰ￑ﾁ￑ﾂ￑ﾌ ￐ﾘ￑ﾁ￑ﾂ￐ﾾ￑ﾀ￐ﾸ￑ﾏ.docx",
            "lastModifiedDateTime":"2019-12-03 17:48:35Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/1 ￑ﾇ￐ﾰ￑ﾁ￑ﾂ￑ﾌ ￐ﾘ￑ﾁ￑ﾂ￐ﾾ￑ﾀ￐ﾸ￑ﾏ.docx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-12-03 17:48:35Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":147846,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899363",
            "name":"2-￐ﾔ￐ﾢ￐ﾞ ￐ﾜ￐ﾰ￑ﾂ￐ﾵ￐ﾼ￐ﾰ￑ﾂ￐ﾸ￐ﾺ￐ﾰ.docx",
            "lastModifiedDateTime":"2020-02-20 17:36:08Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/2-￐ﾔ￐ﾢ￐ﾞ ￐ﾜ￐ﾰ￑ﾂ￐ﾵ￐ﾼ￐ﾰ￑ﾂ￐ﾸ￐ﾺ￐ﾰ.docx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2020-02-20 17:36:08Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":95360,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976853277",
            "name":"10-Moodle-Hacks-for-ESL.pptx",
            "lastModifiedDateTime":"2022-08-08 13:23:48Z",
            "createdDateTime":"2023-11-03 13:47:42Z",
            "lastAccessedDateTime":"2023-11-03 13:47:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/10-Moodle-Hacks-for-ESL.pptx",
               "createdDateTime":"2023-11-03 13:47:42Z",
               "lastAccessedDateTime":"2023-11-03 13:47:42Z",
               "lastModifiedDateTime":"2022-08-08 13:23:48Z"
            },
            "type":"￐ﾟ￑ﾀ￐ﾵ￐ﾷ￐ﾵ￐ﾽ￑ﾂ￐ﾰ￑ﾆ￐ﾸ￑ﾏ Microsoft PowerPoint",
            "size":90495336,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890513",
            "name":"24.03_1,2_￐ﾘ￐ﾡ￐ﾟ_￐ﾟ￑ﾀ￐ﾰ￐ﾺ￑ﾂ￐ﾸ￑ﾇ￐ﾵ￑ﾁ￐ﾺ￐ﾾ￐ﾵ_￐ﾷ￐ﾰ￐ﾽ￑ﾏ￑ﾂ￐ﾸ￐ﾵ_￢ﾄﾖ3_￐ﾣ￐ﾼ￐ﾵ￐ﾽ￐ﾸ￐ﾵ_￑ﾁ￐ﾻ￑ﾃ￑ﾈ￐ﾰ￑ﾂ￑ﾌ_￐ﾸ_￐ﾲ￐ﾵ￑ﾁ￑ﾂ￐ﾸ_￐ﾱ￐ﾵ￑ﾁ￐ﾵ￐ﾴ￑ﾃ 1.docx",
            "lastModifiedDateTime":"2020-03-30 10:14:11Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/24.03_1,2_￐ﾘ￐ﾡ￐ﾟ_￐ﾟ￑ﾀ￐ﾰ￐ﾺ￑ﾂ￐ﾸ￑ﾇ￐ﾵ￑ﾁ￐ﾺ￐ﾾ￐ﾵ_￐ﾷ￐ﾰ￐ﾽ￑ﾏ￑ﾂ￐ﾸ￐ﾵ_￢ﾄﾖ3_￐ﾣ￐ﾼ￐ﾵ￐ﾽ￐ﾸ￐ﾵ_￑ﾁ￐ﾻ￑ﾃ￑ﾈ￐ﾰ￑ﾂ￑ﾌ_￐ﾸ_￐ﾲ￐ﾵ￑ﾁ￑ﾂ￐ﾸ_￐ﾱ￐ﾵ￑ﾁ￐ﾵ￐ﾴ￑ﾃ 1.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-03-30 10:14:11Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":25280,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890508",
            "name":"24.03_1,2_￐ﾘ￐ﾡ￐ﾟ_￐ﾟ￑ﾀ￐ﾰ￐ﾺ￑ﾂ￐ﾸ￑ﾇ￐ﾵ￑ﾁ￐ﾺ￐ﾾ￐ﾵ_￐ﾷ￐ﾰ￐ﾽ￑ﾏ￑ﾂ￐ﾸ￐ﾵ_￢ﾄﾖ3_￐ﾣ￐ﾼ￐ﾵ￐ﾽ￐ﾸ￐ﾵ_￑ﾁ￐ﾻ￑ﾃ￑ﾈ￐ﾰ￑ﾂ￑ﾌ_￐ﾸ_￐ﾲ￐ﾵ￑ﾁ￑ﾂ￐ﾸ_￐ﾱ￐ﾵ￑ﾁ￐ﾵ￐ﾴ￑ﾃ.docx",
            "lastModifiedDateTime":"2020-03-30 08:06:04Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/24.03_1,2_￐ﾘ￐ﾡ￐ﾟ_￐ﾟ￑ﾀ￐ﾰ￐ﾺ￑ﾂ￐ﾸ￑ﾇ￐ﾵ￑ﾁ￐ﾺ￐ﾾ￐ﾵ_￐ﾷ￐ﾰ￐ﾽ￑ﾏ￑ﾂ￐ﾸ￐ﾵ_￢ﾄﾖ3_￐ﾣ￐ﾼ￐ﾵ￐ﾽ￐ﾸ￐ﾵ_￑ﾁ￐ﾻ￑ﾃ￑ﾈ￐ﾰ￑ﾂ￑ﾌ_￐ﾸ_￐ﾲ￐ﾵ￑ﾁ￑ﾂ￐ﾸ_￐ﾱ￐ﾵ￑ﾁ￐ﾵ￐ﾴ￑ﾃ.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-03-30 08:06:04Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":21392,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890514",
            "name":"31.03_1,2￐ﾘ￐ﾡ￐ﾟ_￐ﾢ￐ﾵ￐ﾼ￐ﾰ_￢ﾄﾖ7_￐ﾞ￑ﾁ￐ﾽ￐ﾾ￐ﾲ￐ﾽ￑ﾋ￐ﾵ_￑ﾍ￐ﾻ￐ﾵ￐ﾼ￐ﾵ￐ﾽ￑ﾂ￑ﾋ_￐ﾺ￐ﾾ￐ﾼ￐ﾼ￑ﾃ￐ﾽ￐ﾸ￐ﾺ￐ﾰ￑ﾆ￐ﾸ￐ﾸ._￐ﾒ￐ﾵ￑ﾀ￐ﾱ￐ﾰ￐ﾻ￑ﾌ￐ﾽ￐ﾰ￑ﾏ_￐ﾺ￐ﾾ￐ﾼ￐ﾼ￑ﾃ￐ﾽ￐ﾸ￐ﾺ￐ﾰ￑ﾆ￐ﾸ￑ﾏ._￐ﾝ￐ﾵ￐ﾲ￐ﾵ￑ﾀ￐ﾱ￐ﾰ￐ﾻ￑ﾌ￐ﾽ￐ﾰ￑ﾏ_￐ﾺ￐ﾾ￐ﾼ￐ﾼ￑ﾃ￐ﾽ￐ﾸ￐ﾺ￐ﾰ￑ﾆ￐ﾸ￑ﾏ.docx",
            "lastModifiedDateTime":"2020-04-05 07:56:56Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/31.03_1,2￐ﾘ￐ﾡ￐ﾟ_￐ﾢ￐ﾵ￐ﾼ￐ﾰ_￢ﾄﾖ7_￐ﾞ￑ﾁ￐ﾽ￐ﾾ￐ﾲ￐ﾽ￑ﾋ￐ﾵ_￑ﾍ￐ﾻ￐ﾵ￐ﾼ￐ﾵ￐ﾽ￑ﾂ￑ﾋ_￐ﾺ￐ﾾ￐ﾼ￐ﾼ￑ﾃ￐ﾽ￐ﾸ￐ﾺ￐ﾰ￑ﾆ￐ﾸ￐ﾸ._￐ﾒ￐ﾵ￑ﾀ￐ﾱ￐ﾰ￐ﾻ￑ﾌ￐ﾽ￐ﾰ￑ﾏ_￐ﾺ￐ﾾ￐ﾼ￐ﾼ￑ﾃ￐ﾽ￐ﾸ￐ﾺ￐ﾰ￑ﾆ￐ﾸ￑ﾏ._￐ﾝ￐ﾵ￐ﾲ￐ﾵ￑ﾀ￐ﾱ￐ﾰ￐ﾻ￑ﾌ￐ﾽ￐ﾰ￑ﾏ_￐ﾺ￐ﾾ￐ﾼ￐ﾼ￑ﾃ￐ﾽ￐ﾸ￐ﾺ￐ﾰ￑ﾆ￐ﾸ￑ﾏ.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-04-05 07:56:56Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":18614,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899781",
            "name":"16165.docx",
            "lastModifiedDateTime":"2018-12-05 05:56:51Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/16165.docx",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2018-12-05 05:56:51Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":16182,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890515",
            "name":"Document 1.docx",
            "lastModifiedDateTime":"2020-04-02 15:49:08Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/Document 1.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-04-02 15:49:08Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":0,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890509",
            "name":"Document.docx",
            "lastModifiedDateTime":"2020-03-30 15:11:00Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/Document.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-03-30 15:11:00Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":11420,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899810",
            "name":"earth.pptx",
            "lastModifiedDateTime":"2017-11-20 18:05:52Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/earth.pptx",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2017-11-20 18:05:52Z"
            },
            "type":"￐ﾟ￑ﾀ￐ﾵ￐ﾷ￐ﾵ￐ﾽ￑ﾂ￐ﾰ￑ﾆ￐ﾸ￑ﾏ Microsoft PowerPoint",
            "size":5188165,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899782",
            "name":"Enld.rar",
            "lastModifiedDateTime":"2019-01-05 10:55:54Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/Enld.rar",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2019-01-05 10:55:54Z"
            },
            "type":"WinRAR",
            "size":11645809,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899807",
            "name":"h-2.jpg",
            "lastModifiedDateTime":"2019-05-31 16:21:46Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/h-2.jpg",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2019-05-31 16:21:46Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"JPG\"",
            "size":99606,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899293",
            "name":"JokeWinLock.zip",
            "lastModifiedDateTime":"2019-09-23 16:07:57Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/JokeWinLock.zip",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-09-23 16:07:57Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":442122,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890510",
            "name":"Lab_3.docx",
            "lastModifiedDateTime":"2020-03-30 17:58:33Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/Lab_3.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-03-30 17:58:33Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":33521,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899289",
            "name":"OneDrive.zip",
            "lastModifiedDateTime":"2019-09-28 09:51:36Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/OneDrive.zip",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-09-28 09:51:36Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":373122,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976889520",
            "name":"Prilozhenie_5_Otchet_o_prokhozhdenii_praktiki.docx",
            "lastModifiedDateTime":"2022-10-06 16:44:51Z",
            "createdDateTime":"2023-11-03 13:50:00Z",
            "lastAccessedDateTime":"2023-11-03 13:50:00Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/Prilozhenie_5_Otchet_o_prokhozhdenii_praktiki.docx",
               "createdDateTime":"2023-11-03 13:50:00Z",
               "lastAccessedDateTime":"2023-11-03 13:50:00Z",
               "lastModifiedDateTime":"2022-10-06 16:44:51Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":79229,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899366",
            "name":"Referat2.docx",
            "lastModifiedDateTime":"2021-09-06 19:11:43Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/Referat2.docx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2021-09-06 19:11:43Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":32082,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899780",
            "name":"SNgMAF4xCQA=0112.rar",
            "lastModifiedDateTime":"2018-12-01 09:23:39Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/SNgMAF4xCQA=0112.rar",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2018-12-01 09:23:39Z"
            },
            "type":"WinRAR",
            "size":135871343,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899360",
            "name":"test_newskin10.png",
            "lastModifiedDateTime":"2019-11-14 16:52:21Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/test_newskin10.png",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-11-14 16:52:21Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PNG\"",
            "size":3727,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883717",
            "name":"xls￐ﾦ￐ﾸ￐ﾺ￐ﾻ ￑ﾁ ￐﾿￐ﾰ￑ﾀ￐ﾰ￐ﾼ￐ﾵ￑ﾂ￑ﾀ￐ﾾ￐ﾼ.xlsx",
            "lastModifiedDateTime":"2021-04-29 07:42:45Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/xls￐ﾦ￐ﾸ￐ﾺ￐ﾻ ￑ﾁ ￐﾿￐ﾰ￑ﾀ￐ﾰ￐ﾼ￐ﾵ￑ﾂ￑ﾀ￐ﾾ￐ﾼ.xlsx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2021-04-29 07:42:45Z"
            },
            "type":"￐ﾛ￐ﾸ￑ﾁ￑ﾂ Microsoft Excel",
            "size":12838,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899806",
            "name":"￐ﾐ￐ﾽ￐ﾽ￐ﾾ￑ﾂ￐ﾰ￑ﾆ￐ﾸ￑ﾏ 2019-05-31 204806.png",
            "lastModifiedDateTime":"2019-05-31 16:48:12Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾐ￐ﾽ￐ﾽ￐ﾾ￑ﾂ￐ﾰ￑ﾆ￐ﾸ￑ﾏ 2019-05-31 204806.png",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2019-05-31 16:48:12Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PNG\"",
            "size":208123,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890512",
            "name":"￐ﾐ￑ﾀ￑ﾅ￐ﾸ￑ﾂ￐ﾵ￐ﾺ￑ﾂ￑ﾃ￑ﾀ￐ﾰ.docx",
            "lastModifiedDateTime":"2020-04-02 16:01:43Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾐ￑ﾀ￑ﾅ￐ﾸ￑ﾂ￐ﾵ￐ﾺ￑ﾂ￑ﾃ￑ﾀ￐ﾰ.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-04-02 16:01:43Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":26777,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899361",
            "name":"￐ﾓ￑ﾀ￐ﾰ￐ﾼ￐ﾼ￐ﾰ￑ﾂ￐ﾸ￑ﾇ￐ﾵ￑ﾁ￐ﾺ￐ﾸ￐ﾵ ￐ﾽ￐ﾾ￑ﾀ￐ﾼ￑ﾋ.ppsx",
            "lastModifiedDateTime":"2019-12-24 16:30:33Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾓ￑ﾀ￐ﾰ￐ﾼ￐ﾼ￐ﾰ￑ﾂ￐ﾸ￑ﾇ￐ﾵ￑ﾁ￐ﾺ￐ﾸ￐ﾵ ￐ﾽ￐ﾾ￑ﾀ￐ﾼ￑ﾋ.ppsx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-12-24 16:30:33Z"
            },
            "type":"￐ﾡ￐ﾻ￐ﾰ￐ﾹ￐ﾴ-￑ﾈ￐ﾾ￑ﾃ Microsoft PowerPoint",
            "size":96011,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899359",
            "name":"￐ﾳ￑ﾀ￑ﾃ￑ﾁ￑ﾂ￑ﾌ.mp4",
            "lastModifiedDateTime":"2019-12-14 16:21:49Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾳ￑ﾀ￑ﾃ￑ﾁ￑ﾂ￑ﾌ.mp4",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-12-14 16:21:49Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP4\"",
            "size":12291992,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976889518",
            "name":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ 1.docx",
            "lastModifiedDateTime":"2020-09-22 07:13:56Z",
            "createdDateTime":"2023-11-03 13:50:00Z",
            "lastAccessedDateTime":"2023-11-03 13:50:00Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ 1.docx",
               "createdDateTime":"2023-11-03 13:50:00Z",
               "lastAccessedDateTime":"2023-11-03 13:50:00Z",
               "lastModifiedDateTime":"2020-09-22 07:13:56Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":11561,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883865",
            "name":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ 2.docx",
            "lastModifiedDateTime":"2021-04-23 20:01:18Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ 2.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2021-04-23 20:01:18Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":11057,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883716",
            "name":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ 3.docx",
            "lastModifiedDateTime":"2021-04-28 06:43:47Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ 3.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2021-04-28 06:43:47Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":11058,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883866",
            "name":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ 4.docx",
            "lastModifiedDateTime":"2021-12-19 13:37:08Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ 4.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2021-12-19 13:37:08Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":10502,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976890516",
            "name":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ.docx",
            "lastModifiedDateTime":"2020-03-30 15:10:11Z",
            "createdDateTime":"2023-11-03 13:50:04Z",
            "lastAccessedDateTime":"2023-11-03 13:50:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ.docx",
               "createdDateTime":"2023-11-03 13:50:04Z",
               "lastAccessedDateTime":"2023-11-03 13:50:04Z",
               "lastModifiedDateTime":"2020-03-30 15:10:11Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":0,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883715",
            "name":"￐ﾗ￐ﾰ￐ﾴ￐ﾰ￑ﾇ￐ﾰ 11.docx",
            "lastModifiedDateTime":"2021-04-23 20:10:32Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾗ￐ﾰ￐ﾴ￐ﾰ￑ﾇ￐ﾰ 11.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2021-04-23 20:10:32Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":15074,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883713",
            "name":"￐ﾗ￐ﾰ￐ﾴ￐ﾰ￑ﾇ￐ﾰ 33.docx",
            "lastModifiedDateTime":"2021-04-23 19:46:34Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾗ￐ﾰ￐ﾴ￐ﾰ￑ﾇ￐ﾰ 33.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2021-04-23 19:46:34Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":15690,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883714",
            "name":"￐ﾗ￐ﾰ￐ﾴ￐ﾰ￑ﾇ￐ﾰ 43.docx",
            "lastModifiedDateTime":"2021-04-23 20:03:12Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾗ￐ﾰ￐ﾴ￐ﾰ￑ﾇ￐ﾰ 43.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2021-04-23 20:03:12Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":16853,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899369",
            "name":"￐ﾛ￐ﾸ￑ﾇ￐ﾽ￐ﾾ￐ﾵ ￑ﾅ￑ﾀ￐ﾰ￐ﾽ￐ﾸ￐ﾻ￐ﾸ￑ﾉ￐ﾵ.lnk",
            "lastModifiedDateTime":"2023-12-11 12:00:54Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-12-11 15:30:44Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾛ￐ﾸ￑ﾇ￐ﾽ￐ﾾ￐ﾵ ￑ﾅ￑ﾀ￐ﾰ￐ﾽ￐ﾸ￐ﾻ￐ﾸ￑ﾉ￐ﾵ.lnk",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-12-11 15:30:44Z",
               "lastModifiedDateTime":"2023-12-11 12:00:54Z"
            },
            "type":"￐ﾯ￑ﾀ￐ﾻ￑ﾋ￐ﾺ",
            "size":1164,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899779",
            "name":"￐ﾝ￐ﾰ￑ﾇ￐ﾰ￐ﾻ￐ﾾ ￑ﾀ￐ﾰ￐ﾱ￐ﾾ￑ﾂ￑ﾋ ￑ﾁ OneDrive.pdf",
            "lastModifiedDateTime":"2018-05-08 17:19:54Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾝ￐ﾰ￑ﾇ￐ﾰ￐ﾻ￐ﾾ ￑ﾀ￐ﾰ￐ﾱ￐ﾾ￑ﾂ￑ﾋ ￑ﾁ OneDrive.pdf",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2018-05-08 17:19:54Z"
            },
            "type":"Microsoft Edge Canary PDF Document",
            "size":1072853,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899290",
            "name":"￐ﾞ ￑ﾄ￐ﾾ￑ﾂ￐ﾾ.docx",
            "lastModifiedDateTime":"2019-10-25 16:18:50Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾞ ￑ﾄ￐ﾾ￑ﾂ￐ﾾ.docx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-10-25 16:18:50Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":97924,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899804",
            "name":"￐ﾞ￐ﾱ￑ﾉ￐ﾵ￑ﾁ￑ﾂ￐ﾲ ￐﾿￑ﾀ￐ﾵ￐ﾷ￐ﾵ￐ﾽ￑ﾂ￐ﾰ￐ﾻ￐ﾺ￐ﾰ.ppt",
            "lastModifiedDateTime":"2019-03-22 17:39:19Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾞ￐ﾱ￑ﾉ￐ﾵ￑ﾁ￑ﾂ￐ﾲ ￐﾿￑ﾀ￐ﾵ￐ﾷ￐ﾵ￐ﾽ￑ﾂ￐ﾰ￐ﾻ￐ﾺ￐ﾰ.ppt",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2019-03-22 17:39:19Z"
            },
            "type":"￐ﾟ￑ﾀ￐ﾵ￐ﾷ￐ﾵ￐ﾽ￑ﾂ￐ﾰ￑ﾆ￐ﾸ￑ﾏ PowerPoint 97￢ﾀﾓ2003",
            "size":3818496,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899811",
            "name":"￐ﾞ￑ﾂ￑ﾇ￐ﾵ￑ﾂ.docx",
            "lastModifiedDateTime":"2019-03-02 10:00:18Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾞ￑ﾂ￑ﾇ￐ﾵ￑ﾂ.docx",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2019-03-02 10:00:18Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":3885862,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899809",
            "name":"￐ﾟ￐ﾵ￑ﾀ￐ﾵ￑ﾇ￐ﾵ￐ﾽ￑ﾌ ￐ﾲ￐ﾾ￐﾿￑ﾀ￐ﾾ￑ﾁ￐ﾾ￐ﾲ ￐ﾸ ￐ﾾ￑ﾂ￐ﾲ￐ﾵ￑ﾂ￐ﾾ￐ﾲ.docx",
            "lastModifiedDateTime":"2020-02-27 18:23:20Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾟ￐ﾵ￑ﾀ￐ﾵ￑ﾇ￐ﾵ￐ﾽ￑ﾌ ￐ﾲ￐ﾾ￐﾿￑ﾀ￐ﾾ￑ﾁ￐ﾾ￐ﾲ ￐ﾸ ￐ﾾ￑ﾂ￐ﾲ￐ﾵ￑ﾂ￐ﾾ￐ﾲ.docx",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2020-02-27 18:23:20Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":3590048,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899364",
            "name":"￐ﾟ￐ﾵ￑ﾀ￐ﾵ￑ﾇ￐ﾵ￐ﾽ￑ﾌ ￐ﾾ￑ﾂ￐ﾲ￐ﾵ￑ﾂ￐ﾾ￐ﾲ ￐ﾞ￐ﾡ.docx",
            "lastModifiedDateTime":"2019-12-19 09:40:26Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾟ￐ﾵ￑ﾀ￐ﾵ￑ﾇ￐ﾵ￐ﾽ￑ﾌ ￐ﾾ￑ﾂ￐ﾲ￐ﾵ￑ﾂ￐ﾾ￐ﾲ ￐ﾞ￐ﾡ.docx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-12-19 09:40:26Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":170434,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899808",
            "name":"￐ﾟ￐ﾵ￑ﾀ￐ﾵ￑ﾇ￐ﾵ￐ﾽ￑ﾌ ￐ﾾ￑ﾂ￐ﾲ￐ﾵ￑ﾂ￐ﾾ￐ﾲ.docx",
            "lastModifiedDateTime":"2019-06-27 19:36:59Z",
            "createdDateTime":"2023-11-03 13:50:42Z",
            "lastAccessedDateTime":"2023-11-03 13:50:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾟ￐ﾵ￑ﾀ￐ﾵ￑ﾇ￐ﾵ￐ﾽ￑ﾌ ￐ﾾ￑ﾂ￐ﾲ￐ﾵ￑ﾂ￐ﾾ￐ﾲ.docx",
               "createdDateTime":"2023-11-03 13:50:42Z",
               "lastAccessedDateTime":"2023-11-03 13:50:42Z",
               "lastModifiedDateTime":"2019-06-27 19:36:59Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":2078066,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883867",
            "name":"￐ﾟ￑ﾀ1. ￐ﾡ￑ﾂ￑ﾀ￑ﾃ￐ﾺ￑ﾂ￑ﾃ￑ﾀ￐ﾰ ￑ﾁ￐ﾰ￐ﾹ￑ﾂ￐ﾰ.docx",
            "lastModifiedDateTime":"2022-02-04 07:33:10Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾟ￑ﾀ1. ￐ﾡ￑ﾂ￑ﾀ￑ﾃ￐ﾺ￑ﾂ￑ﾃ￑ﾀ￐ﾰ ￑ﾁ￐ﾰ￐ﾹ￑ﾂ￐ﾰ.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2022-02-04 07:33:10Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":16275,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883718",
            "name":"￐ﾠ￐ﾰ￐ﾱ￐ﾾ￑ﾇ￐ﾰ￑ﾏ ￐ﾢ￐ﾵ￑ﾂ￑ﾀ￐ﾰ￐ﾴ￑ﾌ ￐ﾐ￐ﾚ.docx",
            "lastModifiedDateTime":"2021-05-06 20:05:38Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾠ￐ﾰ￐ﾱ￐ﾾ￑ﾇ￐ﾰ￑ﾏ ￐ﾢ￐ﾵ￑ﾂ￑ﾀ￐ﾰ￐ﾴ￑ﾌ ￐ﾐ￐ﾚ.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2021-05-06 20:05:38Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":208206,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899365",
            "name":"￐ﾠ￐ﾰ￑ﾁ￐﾿￐ﾸ￑ﾁ￐ﾰ￐ﾽ￐ﾸ￐ﾵ_￐ﾴ￐ﾻ￑ﾏ_1-2_￐ﾺ￑ﾃ￑ﾀ￑ﾁ￐ﾾ￐ﾲ_￑ﾁ_13.01_￐﾿￐ﾾ_31.03.20.xls",
            "lastModifiedDateTime":"2020-05-20 13:37:50Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾠ￐ﾰ￑ﾁ￐﾿￐ﾸ￑ﾁ￐ﾰ￐ﾽ￐ﾸ￐ﾵ_￐ﾴ￐ﾻ￑ﾏ_1-2_￐ﾺ￑ﾃ￑ﾀ￑ﾁ￐ﾾ￐ﾲ_￑ﾁ_13.01_￐﾿￐ﾾ_31.03.20.xls",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2020-05-20 13:37:50Z"
            },
            "type":"￐ﾛ￐ﾸ￑ﾁ￑ﾂ Microsoft Excel 97￢ﾀﾓ2003",
            "size":142848,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899362",
            "name":"￐ﾠ￐ﾰ￑ﾁ￐﾿￐ﾸ￑ﾁ￐ﾰ￐ﾽ￐ﾸ￐ﾵ_￐ﾴ￐ﾻ￑ﾏ_1-2_￐ﾺ￑ﾃ￑ﾀ￑ﾁ￐ﾾ￐ﾲ_￑ﾁ_13.01_￐﾿￐ﾾ_31.03.20.xlsx",
            "lastModifiedDateTime":"2020-02-14 18:46:26Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾠ￐ﾰ￑ﾁ￐﾿￐ﾸ￑ﾁ￐ﾰ￐ﾽ￐ﾸ￐ﾵ_￐ﾴ￐ﾻ￑ﾏ_1-2_￐ﾺ￑ﾃ￑ﾀ￑ﾁ￐ﾾ￐ﾲ_￑ﾁ_13.01_￐﾿￐ﾾ_31.03.20.xlsx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2020-02-14 18:46:26Z"
            },
            "type":"￐ﾛ￐ﾸ￑ﾁ￑ﾂ Microsoft Excel",
            "size":89234,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899357",
            "name":"￐ﾠ￐ﾰ￑ﾁ￐﾿￑ﾀ￐ﾵ￐ﾴ￐ﾵ￐ﾻ￐ﾵ￐ﾽ￐ﾸ￐ﾵ ￐ﾻ￑ﾎ￐ﾴ￐ﾵ￐ﾹ ￐ﾲ ￐ﾼ￐ﾵ￐ﾴ￐ﾸ￐ﾰ-￑ﾆ￐ﾵ￐ﾽ￑ﾂ￑ﾀ￐ﾵ.png",
            "lastModifiedDateTime":"2019-11-18 17:03:18Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾠ￐ﾰ￑ﾁ￐﾿￑ﾀ￐ﾵ￐ﾴ￐ﾵ￐ﾻ￐ﾵ￐ﾽ￐ﾸ￐ﾵ ￐ﾻ￑ﾎ￐ﾴ￐ﾵ￐ﾹ ￐ﾲ ￐ﾼ￐ﾵ￐ﾴ￐ﾸ￐ﾰ-￑ﾆ￐ﾵ￐ﾽ￑ﾂ￑ﾀ￐ﾵ.png",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-11-18 17:03:18Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PNG\"",
            "size":132762,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899367",
            "name":"￐ﾠ￐ﾵ￑ﾄ￐ﾵ￑ﾀ￐ﾰ￑ﾂ.docx",
            "lastModifiedDateTime":"2019-10-17 17:32:06Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾠ￐ﾵ￑ﾄ￐ﾵ￑ﾀ￐ﾰ￑ﾂ.docx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-10-17 17:32:06Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":71423,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976899368",
            "name":"￐ﾠ￑ﾄ￐ﾵ￑ﾀ￐ﾰ￑ﾂ.docx",
            "lastModifiedDateTime":"2019-10-17 17:26:39Z",
            "createdDateTime":"2023-11-03 13:50:40Z",
            "lastAccessedDateTime":"2023-11-03 13:50:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾠ￑ﾄ￐ﾵ￑ﾀ￐ﾰ￑ﾂ.docx",
               "createdDateTime":"2023-11-03 13:50:40Z",
               "lastAccessedDateTime":"2023-11-03 13:50:40Z",
               "lastModifiedDateTime":"2019-10-17 17:26:39Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":71417,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         },
         {
            "id":"4007390500,281474976883868",
            "name":"￐ﾨ￐ﾰ￐ﾱ￐ﾻ￐ﾾ￐ﾽ_￐ﾷ￐ﾰ￐ﾴ￐ﾰ￑ﾇ￐ﾸ.docx",
            "lastModifiedDateTime":"2022-09-03 14:08:16Z",
            "createdDateTime":"2023-11-03 13:49:34Z",
            "lastAccessedDateTime":"2023-11-03 13:49:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/OneDrive/￐ﾨ￐ﾰ￐ﾱ￐ﾻ￐ﾾ￐ﾽ_￐ﾷ￐ﾰ￐ﾴ￐ﾰ￑ﾇ￐ﾸ.docx",
               "createdDateTime":"2023-11-03 13:49:34Z",
               "lastAccessedDateTime":"2023-11-03 13:49:34Z",
               "lastModifiedDateTime":"2022-09-03 14:08:16Z"
            },
            "type":"￐ﾔ￐ﾾ￐ﾺ￑ﾃ￐ﾼ￐ﾵ￐ﾽ￑ﾂ Microsoft Word",
            "size":223002,
            "file":{
               
            },
            "parentReference":{
               "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
               "driveType":"syncRoot",
               "id":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103"
            }
         }
      ],
      "@odata.count":59
   },
   {
      "name":"OneDrive",
      "lastModifiedDateTime":"2023-12-11 12:00:45Z",
      "createdDateTime":"2023-11-03 13:44:02Z",
      "lastAccessedDateTime":"2023-12-11 15:09:34Z",
      "canCopy":true,
      "canMove":true,
      "canRename":true,
      "canDelete":true,
      "fileSystemInfo":{
         "systemPath":"C:/Users/Bezzu/OneDrive",
         "createdDateTime":"2023-11-03 13:44:02Z",
         "lastAccessedDateTime":"2023-12-11 15:09:34Z",
         "lastModifiedDateTime":"2023-12-11 12:00:45Z"
      },
      "id":"root",
      "root":{
         
      },
      "type":"Папка с файлами",
      "parentReference":{
         "driveId":"OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal|B0CE1D74A0C7A4D8!103",
         "id":"",
         "driveType":"syncRoot"
      },
      "folder":{
         
      }
   }
]
```

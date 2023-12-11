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

### GET /drives/OneDrive!S-1-5-21-3198801245-3580807-1487484180-1001!Personal%7CB0CE1D74A0C7A4D8!103/items/root
Example answer
```JSON
{
   "name":"OneDrive",
   "lastModifiedDateTime":"2023-12-11 12:00:45Z",
   "createdDateTime":"2023-11-03 13:44:02Z",
   "lastAccessedDateTime":"2023-12-11 17:37:50Z",
   "canCopy":true,
   "canMove":true,
   "canRename":true,
   "canDelete":true,
   "fileSystemInfo":{
      "systemPath":"C:/Users/Bezzu/OneDrive",
      "createdDateTime":"2023-11-03 13:44:02Z",
      "lastAccessedDateTime":"2023-12-11 17:37:50Z",
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
### GET /me/drive/items/root/children?$top=100&$expand=thumbnails&select=*,webDavUrl
(I have OneDrive in Russian and the File Explorer server doesn't work with UTF-8)
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

### GET /drives/local/items/4007390500%2C562949953454108/children?$top=100&$expand=thumbnails&select=*,webDavUrl (ПРИ НАЖАТИИ НА КНОПКУ "ЗАГРУЗКИ")
Example answer
```JSON
[
   {
      "value":[
         {
            "id":"4007390500,3377699720768891",
            "name":"ARM",
            "lastModifiedDateTime":"2023-11-06 20:55:12Z",
            "createdDateTime":"2023-11-06 20:28:32Z",
            "lastAccessedDateTime":"2023-12-10 20:08:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/ARM",
               "createdDateTime":"2023-11-06 20:28:32Z",
               "lastAccessedDateTime":"2023-12-10 20:08:34Z",
               "lastModifiedDateTime":"2023-11-06 20:55:12Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,18577348463318900",
            "name":"Assets",
            "lastModifiedDateTime":"2023-11-13 17:20:53Z",
            "createdDateTime":"2023-11-13 17:20:54Z",
            "lastAccessedDateTime":"2023-12-10 20:09:36Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Assets",
               "createdDateTime":"2023-11-13 17:20:54Z",
               "lastAccessedDateTime":"2023-12-10 20:09:36Z",
               "lastModifiedDateTime":"2023-11-13 17:20:53Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,12103423998830390",
            "name":"background_updater.exe_pass_123",
            "lastModifiedDateTime":"2023-11-05 20:55:44Z",
            "createdDateTime":"2023-11-05 20:55:42Z",
            "lastAccessedDateTime":"2023-12-10 20:08:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/background_updater.exe_pass_123",
               "createdDateTime":"2023-11-05 20:55:42Z",
               "lastAccessedDateTime":"2023-12-10 20:08:34Z",
               "lastModifiedDateTime":"2023-11-05 20:55:44Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,2814749767193849",
            "name":"beta2",
            "lastModifiedDateTime":"2023-12-10 18:42:04Z",
            "createdDateTime":"2023-12-03 21:13:12Z",
            "lastAccessedDateTime":"2023-12-11 15:27:58Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/beta2",
               "createdDateTime":"2023-12-03 21:13:12Z",
               "lastAccessedDateTime":"2023-12-11 15:27:58Z",
               "lastModifiedDateTime":"2023-12-10 18:42:04Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,20547673299889659",
            "name":"cppwinrt-master",
            "lastModifiedDateTime":"2023-12-09 20:48:24Z",
            "createdDateTime":"2023-12-09 20:48:26Z",
            "lastAccessedDateTime":"2023-12-11 15:27:58Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/cppwinrt-master",
               "createdDateTime":"2023-12-09 20:48:26Z",
               "lastAccessedDateTime":"2023-12-11 15:27:58Z",
               "lastModifiedDateTime":"2023-12-09 20:48:24Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,21110623253339832",
            "name":"debug",
            "lastModifiedDateTime":"2023-12-11 15:28:18Z",
            "createdDateTime":"2023-12-11 15:28:08Z",
            "lastAccessedDateTime":"2023-12-11 15:28:20Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/debug",
               "createdDateTime":"2023-12-11 15:28:08Z",
               "lastAccessedDateTime":"2023-12-11 15:28:20Z",
               "lastModifiedDateTime":"2023-12-11 15:28:18Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,2251799813686946",
            "name":"DropMeFiles_2y8FM",
            "lastModifiedDateTime":"2023-11-05 21:00:56Z",
            "createdDateTime":"2023-11-05 21:00:58Z",
            "lastAccessedDateTime":"2023-12-10 20:08:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/DropMeFiles_2y8FM",
               "createdDateTime":"2023-11-05 21:00:58Z",
               "lastAccessedDateTime":"2023-12-10 20:08:34Z",
               "lastModifiedDateTime":"2023-11-05 21:00:56Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,22236523160145873",
            "name":"DropMeFiles_35ijv",
            "lastModifiedDateTime":"2023-12-04 21:07:31Z",
            "createdDateTime":"2023-12-04 14:32:04Z",
            "lastAccessedDateTime":"2023-12-10 20:09:36Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/DropMeFiles_35ijv",
               "createdDateTime":"2023-12-04 14:32:04Z",
               "lastAccessedDateTime":"2023-12-10 20:09:36Z",
               "lastModifiedDateTime":"2023-12-04 21:07:31Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,7318349394483412",
            "name":"FOS",
            "lastModifiedDateTime":"2023-12-09 12:15:42Z",
            "createdDateTime":"2023-11-19 15:50:18Z",
            "lastAccessedDateTime":"2023-12-10 20:09:36Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/FOS",
               "createdDateTime":"2023-11-19 15:50:18Z",
               "lastAccessedDateTime":"2023-12-10 20:09:36Z",
               "lastModifiedDateTime":"2023-12-09 12:15:42Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,6192449487733817",
            "name":"http-web-server-master",
            "lastModifiedDateTime":"2023-12-09 11:01:41Z",
            "createdDateTime":"2023-12-09 11:01:42Z",
            "lastAccessedDateTime":"2023-12-11 15:27:58Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/http-web-server-master",
               "createdDateTime":"2023-12-09 11:01:42Z",
               "lastAccessedDateTime":"2023-12-11 15:27:58Z",
               "lastModifiedDateTime":"2023-12-09 11:01:41Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1407374883554784",
            "name":"market_2023-11-07_20-34-11",
            "lastModifiedDateTime":"2023-11-07 20:34:35Z",
            "createdDateTime":"2023-11-07 20:34:36Z",
            "lastAccessedDateTime":"2023-12-10 20:09:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/market_2023-11-07_20-34-11",
               "createdDateTime":"2023-11-07 20:34:36Z",
               "lastAccessedDateTime":"2023-12-10 20:09:34Z",
               "lastModifiedDateTime":"2023-11-07 20:34:35Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,51509920738069579",
            "name":"MicrosoftWindows.FileExplorer.Proto_120.5101.0.0_x64__cw5n1h2txyewy",
            "lastModifiedDateTime":"2023-12-10 18:10:29Z",
            "createdDateTime":"2023-12-04 18:17:32Z",
            "lastAccessedDateTime":"2023-12-11 12:09:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/MicrosoftWindows.FileExplorer.Proto_120.5101.0.0_x64__cw5n1h2txyewy",
               "createdDateTime":"2023-12-04 18:17:32Z",
               "lastAccessedDateTime":"2023-12-11 12:09:04Z",
               "lastModifiedDateTime":"2023-12-10 18:10:29Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,5348024557520993",
            "name":"Modern-File-Explorer-For-Windows-Core-OS-main",
            "lastModifiedDateTime":"2023-12-10 19:38:35Z",
            "createdDateTime":"2023-12-10 19:38:36Z",
            "lastAccessedDateTime":"2023-12-11 15:07:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Modern-File-Explorer-For-Windows-Core-OS-main",
               "createdDateTime":"2023-12-10 19:38:36Z",
               "lastAccessedDateTime":"2023-12-11 15:07:40Z",
               "lastModifiedDateTime":"2023-12-10 19:38:35Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,4222124650872213",
            "name":"msix",
            "lastModifiedDateTime":"2023-11-06 20:54:46Z",
            "createdDateTime":"2023-11-05 10:36:46Z",
            "lastAccessedDateTime":"2023-12-10 20:08:32Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/msix",
               "createdDateTime":"2023-11-05 10:36:46Z",
               "lastAccessedDateTime":"2023-12-10 20:08:32Z",
               "lastModifiedDateTime":"2023-11-06 20:54:46Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,7881299347921405",
            "name":"msvcp140_app",
            "lastModifiedDateTime":"2023-12-04 20:14:00Z",
            "createdDateTime":"2023-12-04 20:12:40Z",
            "lastAccessedDateTime":"2023-12-10 20:08:32Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/msvcp140_app",
               "createdDateTime":"2023-12-04 20:12:40Z",
               "lastAccessedDateTime":"2023-12-10 20:08:32Z",
               "lastModifiedDateTime":"2023-12-04 20:14:00Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,5348024557606760",
            "name":"payment_alipay-master",
            "lastModifiedDateTime":"2023-11-23 14:28:26Z",
            "createdDateTime":"2023-11-23 14:28:28Z",
            "lastAccessedDateTime":"2023-12-10 20:08:32Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/payment_alipay-master",
               "createdDateTime":"2023-11-23 14:28:28Z",
               "lastAccessedDateTime":"2023-12-10 20:08:32Z",
               "lastModifiedDateTime":"2023-11-23 14:28:26Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1970324837083502",
            "name":"payment_asiapay",
            "lastModifiedDateTime":"2023-11-11 13:41:29Z",
            "createdDateTime":"2023-11-11 13:41:30Z",
            "lastAccessedDateTime":"2023-12-10 20:09:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/payment_asiapay",
               "createdDateTime":"2023-11-11 13:41:30Z",
               "lastAccessedDateTime":"2023-12-10 20:09:34Z",
               "lastModifiedDateTime":"2023-11-11 13:41:29Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1125899906867032",
            "name":"payment_mollie",
            "lastModifiedDateTime":"2023-11-15 15:53:05Z",
            "createdDateTime":"2023-11-15 15:53:06Z",
            "lastAccessedDateTime":"2023-12-10 20:09:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/payment_mollie",
               "createdDateTime":"2023-11-15 15:53:06Z",
               "lastAccessedDateTime":"2023-12-10 20:09:34Z",
               "lastModifiedDateTime":"2023-11-15 15:53:05Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,25895697857424810",
            "name":"photos",
            "lastModifiedDateTime":"2023-11-21 18:35:19Z",
            "createdDateTime":"2023-11-21 18:34:10Z",
            "lastAccessedDateTime":"2023-12-10 20:08:32Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/photos",
               "createdDateTime":"2023-11-21 18:34:10Z",
               "lastAccessedDateTime":"2023-12-10 20:08:32Z",
               "lastModifiedDateTime":"2023-11-21 18:35:19Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,18295873486335432",
            "name":"PSTools",
            "lastModifiedDateTime":"2023-11-27 20:01:19Z",
            "createdDateTime":"2023-11-13 17:41:26Z",
            "lastAccessedDateTime":"2023-12-10 20:08:32Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/PSTools",
               "createdDateTime":"2023-11-13 17:41:26Z",
               "lastAccessedDateTime":"2023-12-10 20:08:32Z",
               "lastModifiedDateTime":"2023-11-27 20:01:19Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,844424930154813",
            "name":"Telegram Desktop",
            "lastModifiedDateTime":"2023-12-08 21:02:06Z",
            "createdDateTime":"2023-11-03 14:32:40Z",
            "lastAccessedDateTime":"2023-12-10 20:13:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Telegram Desktop",
               "createdDateTime":"2023-11-03 14:32:40Z",
               "lastAccessedDateTime":"2023-12-10 20:13:34Z",
               "lastModifiedDateTime":"2023-12-08 21:02:06Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,36591746972407692",
            "name":"testVG",
            "lastModifiedDateTime":"2023-12-10 17:37:53Z",
            "createdDateTime":"2023-12-10 17:37:54Z",
            "lastAccessedDateTime":"2023-12-10 20:08:32Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/testVG",
               "createdDateTime":"2023-12-10 17:37:54Z",
               "lastAccessedDateTime":"2023-12-10 20:08:32Z",
               "lastModifiedDateTime":"2023-12-10 17:37:53Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,16044073672612750",
            "name":"vcruntime140_1_app",
            "lastModifiedDateTime":"2023-12-04 20:16:41Z",
            "createdDateTime":"2023-12-04 20:16:32Z",
            "lastAccessedDateTime":"2023-12-10 20:08:32Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/vcruntime140_1_app",
               "createdDateTime":"2023-12-04 20:16:32Z",
               "lastAccessedDateTime":"2023-12-10 20:08:32Z",
               "lastModifiedDateTime":"2023-12-04 20:16:41Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,19421773393041223",
            "name":"vcruntime140_app",
            "lastModifiedDateTime":"2023-12-04 20:08:16Z",
            "createdDateTime":"2023-12-04 20:07:52Z",
            "lastAccessedDateTime":"2023-12-10 20:08:32Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/vcruntime140_app",
               "createdDateTime":"2023-12-04 20:07:52Z",
               "lastAccessedDateTime":"2023-12-10 20:08:32Z",
               "lastModifiedDateTime":"2023-12-04 20:08:16Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1688849860269418",
            "name":"￐ﾡ￐ﾑ￐ﾟ",
            "lastModifiedDateTime":"2023-12-07 20:57:21Z",
            "createdDateTime":"2023-11-19 06:56:12Z",
            "lastAccessedDateTime":"2023-12-11 15:28:04Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/￐ﾡ￐ﾑ￐ﾟ",
               "createdDateTime":"2023-11-19 06:56:12Z",
               "lastAccessedDateTime":"2023-12-11 15:28:04Z",
               "lastModifiedDateTime":"2023-12-07 20:57:21Z"
            },
            "type":"￐ﾟ￐ﾰ￐﾿￐ﾺ￐ﾰ ￑ﾁ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ￐ﾰ￐ﾼ￐ﾸ",
            "folder":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,3659174697442378",
            "name":"49306atecsolution.FilesUWP_2.3.0.0_neutral_~_et10x9a9vyk8t.Msixbundle",
            "lastModifiedDateTime":"2023-12-08 10:41:13Z",
            "createdDateTime":"2023-12-08 10:38:42Z",
            "lastAccessedDateTime":"2023-12-08 10:42:56Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/49306atecsolution.FilesUWP_2.3.0.0_neutral_~_et10x9a9vyk8t.Msixbundle",
               "createdDateTime":"2023-12-08 10:38:42Z",
               "lastAccessedDateTime":"2023-12-08 10:42:56Z",
               "lastModifiedDateTime":"2023-12-08 10:41:13Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MSIXBUNDLE\"",
            "size":293097255,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1407374883580001",
            "name":"281683276-af4af26b-d5e9-4502-ac6a-8921d34c3cfa.gif",
            "lastModifiedDateTime":"2023-11-14 17:38:39Z",
            "createdDateTime":"2023-11-14 17:38:40Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/281683276-af4af26b-d5e9-4502-ac6a-8921d34c3cfa.gif",
               "createdDateTime":"2023-11-14 17:38:40Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-11-14 17:38:39Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"GIF\"",
            "size":931654,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,2251799813729248",
            "name":"ads_arbuz.php",
            "lastModifiedDateTime":"2023-11-24 21:26:51Z",
            "createdDateTime":"2023-11-24 21:26:52Z",
            "lastAccessedDateTime":"2023-11-24 21:26:52Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/ads_arbuz.php",
               "createdDateTime":"2023-11-24 21:26:52Z",
               "lastAccessedDateTime":"2023-11-24 21:26:52Z",
               "lastModifiedDateTime":"2023-11-24 21:26:51Z"
            },
            "type":"￐ﾘ￑ﾁ￑ﾅ￐ﾾ￐ﾴ￐ﾽ￑ﾋ￐ﾹ ￑ﾄ￐ﾰ￐ﾹ￐ﾻ PHP",
            "size":2845,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1970324837170488",
            "name":"AppxBlockMap.xml",
            "lastModifiedDateTime":"2023-12-04 19:43:46Z",
            "createdDateTime":"2023-12-04 19:43:48Z",
            "lastAccessedDateTime":"2023-12-11 12:01:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/AppxBlockMap.xml",
               "createdDateTime":"2023-12-04 19:43:48Z",
               "lastAccessedDateTime":"2023-12-11 12:01:34Z",
               "lastModifiedDateTime":"2023-12-04 19:43:46Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"XML\"",
            "size":277718,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,5348024557694911",
            "name":"AppxSignature.p7x",
            "lastModifiedDateTime":"2023-12-04 19:38:24Z",
            "createdDateTime":"2023-12-04 19:38:26Z",
            "lastAccessedDateTime":"2023-12-11 12:01:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/AppxSignature.p7x",
               "createdDateTime":"2023-12-04 19:38:26Z",
               "lastAccessedDateTime":"2023-12-11 12:01:34Z",
               "lastModifiedDateTime":"2023-12-04 19:38:24Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"P7X\"",
            "size":9342,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,844424930389782",
            "name":"avatarka_dlya_diskorda.png",
            "lastModifiedDateTime":"2023-11-12 12:36:51Z",
            "createdDateTime":"2023-11-12 12:36:52Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/avatarka_dlya_diskorda.png",
               "createdDateTime":"2023-11-12 12:36:52Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-11-12 12:36:51Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PNG\"",
            "size":19330,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,5066549580798854",
            "name":"beta2.zip_pass_123.zip",
            "lastModifiedDateTime":"2023-12-03 21:11:11Z",
            "createdDateTime":"2023-12-03 21:11:12Z",
            "lastAccessedDateTime":"2023-12-06 20:20:38Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/beta2.zip_pass_123.zip",
               "createdDateTime":"2023-12-03 21:11:12Z",
               "lastAccessedDateTime":"2023-12-06 20:20:38Z",
               "lastModifiedDateTime":"2023-12-03 21:11:11Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":6916117,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1407374883642815",
            "name":"boost_1_82_0.7z",
            "lastModifiedDateTime":"2023-12-08 20:38:05Z",
            "createdDateTime":"2023-12-08 20:36:26Z",
            "lastAccessedDateTime":"2023-12-09 12:47:24Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/boost_1_82_0.7z",
               "createdDateTime":"2023-12-08 20:36:26Z",
               "lastAccessedDateTime":"2023-12-09 12:47:24Z",
               "lastModifiedDateTime":"2023-12-08 20:38:05Z"
            },
            "type":"WinRAR",
            "size":103710551,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,10696049115011973",
            "name":"cppwinrt-master.zip",
            "lastModifiedDateTime":"2023-12-09 20:47:58Z",
            "createdDateTime":"2023-12-09 20:47:54Z",
            "lastAccessedDateTime":"2023-12-11 14:35:44Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/cppwinrt-master.zip",
               "createdDateTime":"2023-12-09 20:47:54Z",
               "lastAccessedDateTime":"2023-12-11 14:35:44Z",
               "lastModifiedDateTime":"2023-12-09 20:47:58Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":1067303,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,24206847997125784",
            "name":"dnSpy-net-win64.zip",
            "lastModifiedDateTime":"2023-12-03 21:11:07Z",
            "createdDateTime":"2023-12-03 21:10:56Z",
            "lastAccessedDateTime":"2023-12-06 20:20:38Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/dnSpy-net-win64.zip",
               "createdDateTime":"2023-12-03 21:10:56Z",
               "lastAccessedDateTime":"2023-12-06 20:20:38Z",
               "lastModifiedDateTime":"2023-12-03 21:11:07Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":85810042,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1688849860451021",
            "name":"DropMeFiles_35ijv.zip",
            "lastModifiedDateTime":"2023-12-04 14:30:58Z",
            "createdDateTime":"2023-12-04 14:30:58Z",
            "lastAccessedDateTime":"2023-12-08 07:14:30Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/DropMeFiles_35ijv.zip",
               "createdDateTime":"2023-12-04 14:30:58Z",
               "lastAccessedDateTime":"2023-12-08 07:14:30Z",
               "lastModifiedDateTime":"2023-12-04 14:30:58Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":434898,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,5348024557574819",
            "name":"echo_server.py",
            "lastModifiedDateTime":"2023-12-10 18:28:39Z",
            "createdDateTime":"2023-12-10 18:28:40Z",
            "lastAccessedDateTime":"2023-12-10 18:28:40Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/echo_server.py",
               "createdDateTime":"2023-12-10 18:28:40Z",
               "lastAccessedDateTime":"2023-12-10 18:28:40Z",
               "lastModifiedDateTime":"2023-12-10 18:28:39Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PY\"",
            "size":774,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,844424930754481",
            "name":"Ej3h9pa4TOp-z-0-y-65738366032e6b086c90bead.mp4",
            "lastModifiedDateTime":"2023-12-08 21:02:51Z",
            "createdDateTime":"2023-12-08 21:02:52Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Ej3h9pa4TOp-z-0-y-65738366032e6b086c90bead.mp4",
               "createdDateTime":"2023-12-08 21:02:52Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 21:02:51Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP4\"",
            "size":32498494,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,4503599627608148",
            "name":"explorerpp_x64.zip",
            "lastModifiedDateTime":"2023-11-13 18:23:43Z",
            "createdDateTime":"2023-11-13 18:23:34Z",
            "lastAccessedDateTime":"2023-11-19 19:56:00Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/explorerpp_x64.zip",
               "createdDateTime":"2023-11-13 18:23:34Z",
               "lastAccessedDateTime":"2023-11-19 19:56:00Z",
               "lastModifiedDateTime":"2023-11-13 18:23:43Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":2464185,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,562949954055475",
            "name":"ezgif-1-1af78d5fe6.png",
            "lastModifiedDateTime":"2023-12-08 21:10:26Z",
            "createdDateTime":"2023-12-08 21:10:22Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/ezgif-1-1af78d5fe6.png",
               "createdDateTime":"2023-12-08 21:10:22Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 21:10:26Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PNG\"",
            "size":18598407,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,14636698789120223",
            "name":"FactoryOS_win32_manufacturing_AMD64_UEFI_SpacesGPT_VM.vhdx",
            "lastModifiedDateTime":"2023-11-13 14:23:29Z",
            "createdDateTime":"2023-11-13 14:25:24Z",
            "lastAccessedDateTime":"2023-11-13 14:40:38Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/FactoryOS_win32_manufacturing_AMD64_UEFI_SpacesGPT_VM.vhdx",
               "createdDateTime":"2023-11-13 14:25:24Z",
               "lastAccessedDateTime":"2023-11-13 14:40:38Z",
               "lastModifiedDateTime":"2023-11-13 14:23:29Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ ￐ﾾ￐ﾱ￑ﾀ￐ﾰ￐ﾷ￐ﾰ ￐ﾶ￐ﾵ￑ﾁ￑ﾂ￐ﾺ￐ﾾ￐ﾳ￐ﾾ ￐ﾴ￐ﾸ￑ﾁ￐ﾺ￐ﾰ",
            "size":38797312,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,20829148276606635",
            "name":"Files.preview.appinstaller",
            "lastModifiedDateTime":"2023-12-08 10:28:39Z",
            "createdDateTime":"2023-12-08 10:28:40Z",
            "lastAccessedDateTime":"2023-12-08 19:54:18Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Files.preview.appinstaller",
               "createdDateTime":"2023-12-08 10:28:40Z",
               "lastAccessedDateTime":"2023-12-08 19:54:18Z",
               "lastModifiedDateTime":"2023-12-08 10:28:39Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"APPINSTALLER\"",
            "size":1668,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,2814749767644265",
            "name":"Files-1.1.appinstaller",
            "lastModifiedDateTime":"2023-12-08 10:35:39Z",
            "createdDateTime":"2023-12-08 10:35:36Z",
            "lastAccessedDateTime":"2023-12-08 10:36:12Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Files-1.1.appinstaller",
               "createdDateTime":"2023-12-08 10:35:36Z",
               "lastAccessedDateTime":"2023-12-08 10:36:12Z",
               "lastModifiedDateTime":"2023-12-08 10:35:39Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"APPINSTALLER\"",
            "size":58752151,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,4785074604158471",
            "name":"Hepolise-debug_menu_com.vk.im.txt",
            "lastModifiedDateTime":"2023-11-20 21:08:59Z",
            "createdDateTime":"2023-11-20 21:09:00Z",
            "lastAccessedDateTime":"2023-11-20 21:09:00Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Hepolise-debug_menu_com.vk.im.txt",
               "createdDateTime":"2023-11-20 21:09:00Z",
               "lastAccessedDateTime":"2023-11-20 21:09:00Z",
               "lastModifiedDateTime":"2023-11-20 21:08:59Z"
            },
            "type":"Text Document",
            "size":751,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,2814749767183882",
            "name":"Hepolise-debug_menu_com.vk.im.txt.lpzip",
            "lastModifiedDateTime":"2023-11-20 21:09:11Z",
            "createdDateTime":"2023-11-20 21:09:12Z",
            "lastAccessedDateTime":"2023-11-20 21:11:20Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Hepolise-debug_menu_com.vk.im.txt.lpzip",
               "createdDateTime":"2023-11-20 21:09:12Z",
               "lastAccessedDateTime":"2023-11-20 21:11:20Z",
               "lastModifiedDateTime":"2023-11-20 21:09:11Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"LPZIP\"",
            "size":594,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1688849860902868",
            "name":"http-web-server-master.zip",
            "lastModifiedDateTime":"2023-12-09 10:59:35Z",
            "createdDateTime":"2023-12-09 10:59:36Z",
            "lastAccessedDateTime":"2023-12-10 05:49:54Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/http-web-server-master.zip",
               "createdDateTime":"2023-12-09 10:59:36Z",
               "lastAccessedDateTime":"2023-12-10 05:49:54Z",
               "lastModifiedDateTime":"2023-12-09 10:59:35Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":24102,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1688849860677980",
            "name":"install.ps1",
            "lastModifiedDateTime":"2023-11-13 19:15:26Z",
            "createdDateTime":"2023-11-13 19:15:26Z",
            "lastAccessedDateTime":"2023-11-19 08:45:38Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/install.ps1",
               "createdDateTime":"2023-11-13 19:15:26Z",
               "lastAccessedDateTime":"2023-11-19 08:45:38Z",
               "lastModifiedDateTime":"2023-11-13 19:15:26Z"
            },
            "type":"Windows PowerShell Script",
            "size":44,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,3377699720620407",
            "name":"Microsoft.253890156C685_1.0.0.0_x64__8wekyb3d8bbwe.Msix",
            "lastModifiedDateTime":"2023-11-27 19:02:43Z",
            "createdDateTime":"2023-11-27 17:47:14Z",
            "lastAccessedDateTime":"2023-11-27 19:02:44Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Microsoft.253890156C685_1.0.0.0_x64__8wekyb3d8bbwe.Msix",
               "createdDateTime":"2023-11-27 17:47:14Z",
               "lastAccessedDateTime":"2023-11-27 19:02:44Z",
               "lastModifiedDateTime":"2023-11-27 19:02:43Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MSIX\"",
            "size":4679211211,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,7036874417868128",
            "name":"Microsoft.GamingServices_16.83.3001.0_neutral_~_8wekyb3d8bbwe.zip",
            "lastModifiedDateTime":"2023-11-13 12:05:40Z",
            "createdDateTime":"2023-11-13 12:59:28Z",
            "lastAccessedDateTime":"2023-11-19 19:55:46Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Microsoft.GamingServices_16.83.3001.0_neutral_~_8wekyb3d8bbwe.zip",
               "createdDateTime":"2023-11-13 12:59:28Z",
               "lastAccessedDateTime":"2023-11-19 19:55:46Z",
               "lastModifiedDateTime":"2023-11-13 12:05:40Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":55310315,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,6755399441188762",
            "name":"Microsoft.VCLibs.140.00_14.0.32530.0_x64__8wekyb3d8bbwe.Appx",
            "lastModifiedDateTime":"2023-12-09 12:51:11Z",
            "createdDateTime":"2023-12-09 12:51:10Z",
            "lastAccessedDateTime":"2023-12-09 12:51:12Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Microsoft.VCLibs.140.00_14.0.32530.0_x64__8wekyb3d8bbwe.Appx",
               "createdDateTime":"2023-12-09 12:51:10Z",
               "lastAccessedDateTime":"2023-12-09 12:51:12Z",
               "lastModifiedDateTime":"2023-12-09 12:51:11Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"APPX\"",
            "size":893921,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,26458647810842857",
            "name":"Microsoft.Windows10XEmulatorImage10.0.19578.0Previ_1.0.1.0_x64__8wekyb3d8bbwe.Msix",
            "lastModifiedDateTime":"2023-11-27 18:42:42Z",
            "createdDateTime":"2023-11-27 17:47:48Z",
            "lastAccessedDateTime":"2023-12-04 21:30:48Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Microsoft.Windows10XEmulatorImage10.0.19578.0Previ_1.0.1.0_x64__8wekyb3d8bbwe.Msix",
               "createdDateTime":"2023-11-27 17:47:48Z",
               "lastAccessedDateTime":"2023-12-04 21:30:48Z",
               "lastModifiedDateTime":"2023-11-27 18:42:42Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MSIX\"",
            "size":4842158299,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,3096224743924969",
            "name":"Microsoft.WindowsAlarms_8wekyb3d8bbwe.zip",
            "lastModifiedDateTime":"2021-01-13 19:14:27Z",
            "createdDateTime":"2023-11-13 12:20:02Z",
            "lastAccessedDateTime":"2023-11-19 19:55:44Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Microsoft.WindowsAlarms_8wekyb3d8bbwe.zip",
               "createdDateTime":"2023-11-13 12:20:02Z",
               "lastAccessedDateTime":"2023-11-19 19:55:44Z",
               "lastModifiedDateTime":"2021-01-13 19:14:27Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":19906269,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,15199648742382223",
            "name":"Microsoft.WindowsTerminal_1.11.2921.0_8wekyb3d8bbwe.msixbundle",
            "lastModifiedDateTime":"2023-12-09 12:20:04Z",
            "createdDateTime":"2023-12-09 12:19:52Z",
            "lastAccessedDateTime":"2023-12-09 12:20:06Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Microsoft.WindowsTerminal_1.11.2921.0_8wekyb3d8bbwe.msixbundle",
               "createdDateTime":"2023-12-09 12:19:52Z",
               "lastAccessedDateTime":"2023-12-09 12:20:06Z",
               "lastModifiedDateTime":"2023-12-09 12:20:04Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MSIXBUNDLE\"",
            "size":30615167,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,15199648742432670",
            "name":"Microsoft.WindowsTerminal_1.11.2921.0_8wekyb3d8bbwe.msixbundle_Windows10_PreinstallKit.zip",
            "lastModifiedDateTime":"2023-12-09 12:20:09Z",
            "createdDateTime":"2023-12-09 12:19:58Z",
            "lastAccessedDateTime":"2023-12-10 17:35:42Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Microsoft.WindowsTerminal_1.11.2921.0_8wekyb3d8bbwe.msixbundle_Windows10_PreinstallKit.zip",
               "createdDateTime":"2023-12-09 12:19:58Z",
               "lastAccessedDateTime":"2023-12-10 17:35:42Z",
               "lastModifiedDateTime":"2023-12-09 12:20:09Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":30154049,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,183803159792064361",
            "name":"MicrosoftWindows.FileExplorer.Proto_120.5101.0.0_x64__cw5n1h2txyewy.zip",
            "lastModifiedDateTime":"2023-11-26 13:50:16Z",
            "createdDateTime":"2023-11-26 13:50:06Z",
            "lastAccessedDateTime":"2023-12-10 18:10:30Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/MicrosoftWindows.FileExplorer.Proto_120.5101.0.0_x64__cw5n1h2txyewy.zip",
               "createdDateTime":"2023-11-26 13:50:06Z",
               "lastAccessedDateTime":"2023-12-10 18:10:30Z",
               "lastModifiedDateTime":"2023-11-26 13:50:16Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":5067447,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1970324837048434",
            "name":"MicrosoftWindows.Windows10X.CBS.appx",
            "lastModifiedDateTime":"2023-11-26 13:13:20Z",
            "createdDateTime":"2023-11-26 13:13:08Z",
            "lastAccessedDateTime":"2023-12-06 20:31:20Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/MicrosoftWindows.Windows10X.CBS.appx",
               "createdDateTime":"2023-11-26 13:13:08Z",
               "lastAccessedDateTime":"2023-12-06 20:31:20Z",
               "lastModifiedDateTime":"2023-11-26 13:13:20Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"APPX\"",
            "size":17627189,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,12666373951995816",
            "name":"Minecraft-1.16.100.4.Appx",
            "lastModifiedDateTime":"2023-11-27 21:13:10Z",
            "createdDateTime":"2023-11-27 21:10:26Z",
            "lastAccessedDateTime":"2023-11-28 12:51:58Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Minecraft-1.16.100.4.Appx",
               "createdDateTime":"2023-11-27 21:10:26Z",
               "lastAccessedDateTime":"2023-11-28 12:51:58Z",
               "lastModifiedDateTime":"2023-11-27 21:13:10Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"APPX\"",
            "size":308772848,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,8162774324837200",
            "name":"models.py",
            "lastModifiedDateTime":"2023-11-07 19:54:34Z",
            "createdDateTime":"2023-11-07 19:49:02Z",
            "lastAccessedDateTime":"2023-11-13 12:51:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/models.py",
               "createdDateTime":"2023-11-07 19:49:02Z",
               "lastAccessedDateTime":"2023-11-13 12:51:34Z",
               "lastModifiedDateTime":"2023-11-07 19:54:34Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PY\"",
            "size":315275,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,12103423998562804",
            "name":"Modern-File-Explorer-For-Windows-Core-OS-main.zip",
            "lastModifiedDateTime":"2023-12-10 18:14:48Z",
            "createdDateTime":"2023-12-10 18:14:40Z",
            "lastAccessedDateTime":"2023-12-11 14:35:44Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Modern-File-Explorer-For-Windows-Core-OS-main.zip",
               "createdDateTime":"2023-12-10 18:14:40Z",
               "lastAccessedDateTime":"2023-12-11 14:35:44Z",
               "lastModifiedDateTime":"2023-12-10 18:14:48Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":7090168,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,3377699720730526",
            "name":"msvcp140_app.zip",
            "lastModifiedDateTime":"2023-12-04 20:12:14Z",
            "createdDateTime":"2023-12-04 20:12:14Z",
            "lastAccessedDateTime":"2023-12-08 07:14:30Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/msvcp140_app.zip",
               "createdDateTime":"2023-12-04 20:12:14Z",
               "lastAccessedDateTime":"2023-12-08 07:14:30Z",
               "lastModifiedDateTime":"2023-12-04 20:12:14Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":202375,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,5066549580972171",
            "name":"node-nl-129.protonvpn.net.udp.ovpn",
            "lastModifiedDateTime":"2023-11-17 14:12:40Z",
            "createdDateTime":"2023-11-17 14:12:42Z",
            "lastAccessedDateTime":"2023-11-17 14:12:54Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/node-nl-129.protonvpn.net.udp.ovpn",
               "createdDateTime":"2023-11-17 14:12:42Z",
               "lastAccessedDateTime":"2023-11-17 14:12:54Z",
               "lastModifiedDateTime":"2023-11-17 14:12:40Z"
            },
            "type":"OpenVPN Config File",
            "size":5104,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,2814749767129085",
            "name":"node-nl-193.protonvpn.net.udp.ovpn",
            "lastModifiedDateTime":"2023-11-17 14:11:13Z",
            "createdDateTime":"2023-11-17 14:11:14Z",
            "lastAccessedDateTime":"2023-11-17 14:11:26Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/node-nl-193.protonvpn.net.udp.ovpn",
               "createdDateTime":"2023-11-17 14:11:14Z",
               "lastAccessedDateTime":"2023-11-17 14:11:26Z",
               "lastModifiedDateTime":"2023-11-17 14:11:13Z"
            },
            "type":"OpenVPN Config File",
            "size":5119,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,16607023626090624",
            "name":"node-us-61.protonvpn.net.udp.ovpn",
            "lastModifiedDateTime":"2023-11-17 13:57:44Z",
            "createdDateTime":"2023-11-17 13:57:46Z",
            "lastAccessedDateTime":"2023-11-17 13:58:00Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/node-us-61.protonvpn.net.udp.ovpn",
               "createdDateTime":"2023-11-17 13:57:46Z",
               "lastAccessedDateTime":"2023-11-17 13:58:00Z",
               "lastModifiedDateTime":"2023-11-17 13:57:44Z"
            },
            "type":"OpenVPN Config File",
            "size":5107,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1970324836997845",
            "name":"Operation_Check_PJSC_Sberbank_18112023.pdf",
            "lastModifiedDateTime":"2023-11-18 09:50:56Z",
            "createdDateTime":"2023-11-18 09:50:58Z",
            "lastAccessedDateTime":"2023-11-19 19:55:00Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Operation_Check_PJSC_Sberbank_18112023.pdf",
               "createdDateTime":"2023-11-18 09:50:58Z",
               "lastAccessedDateTime":"2023-11-19 19:55:00Z",
               "lastModifiedDateTime":"2023-11-18 09:50:56Z"
            },
            "type":"Microsoft Edge Canary PDF Document",
            "size":172149,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1125899907113384",
            "name":"payment_wepay_gateway-9.0.1.0.0.zip",
            "lastModifiedDateTime":"2023-11-09 16:27:03Z",
            "createdDateTime":"2023-11-09 16:27:04Z",
            "lastAccessedDateTime":"2023-11-19 19:54:56Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/payment_wepay_gateway-9.0.1.0.0.zip",
               "createdDateTime":"2023-11-09 16:27:04Z",
               "lastAccessedDateTime":"2023-11-19 19:54:56Z",
               "lastModifiedDateTime":"2023-11-09 16:27:03Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":3798359,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,2251799814100725",
            "name":"PSTools.zip",
            "lastModifiedDateTime":"2023-11-13 17:40:46Z",
            "createdDateTime":"2023-11-13 17:40:44Z",
            "lastAccessedDateTime":"2023-11-27 20:01:18Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/PSTools.zip",
               "createdDateTime":"2023-11-13 17:40:44Z",
               "lastAccessedDateTime":"2023-11-27 20:01:18Z",
               "lastModifiedDateTime":"2023-11-13 17:40:46Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":5282424,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1970324837115229",
            "name":"ROBLOXCORPORATION.ROBLOX_2023.1206.2249.0_neutral_~_55nm5eh3cm0pr.Msixbundle",
            "lastModifiedDateTime":"2023-12-09 12:51:23Z",
            "createdDateTime":"2023-12-09 12:50:54Z",
            "lastAccessedDateTime":"2023-12-09 12:51:24Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/ROBLOXCORPORATION.ROBLOX_2023.1206.2249.0_neutral_~_55nm5eh3cm0pr.Msixbundle",
               "createdDateTime":"2023-12-09 12:50:54Z",
               "lastAccessedDateTime":"2023-12-09 12:51:24Z",
               "lastModifiedDateTime":"2023-12-09 12:51:23Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MSIXBUNDLE\"",
            "size":203933813,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,2814749767349148",
            "name":"settings-1699216852725.log",
            "lastModifiedDateTime":"2023-11-05 20:40:54Z",
            "createdDateTime":"2023-11-05 20:40:56Z",
            "lastAccessedDateTime":"2023-11-05 20:40:56Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/settings-1699216852725.log",
               "createdDateTime":"2023-11-05 20:40:56Z",
               "lastAccessedDateTime":"2023-11-05 20:40:56Z",
               "lastModifiedDateTime":"2023-11-05 20:40:54Z"
            },
            "type":"Text Document",
            "size":0,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,3096224744057990",
            "name":"SPBTinkoff.py",
            "lastModifiedDateTime":"2023-11-29 13:51:24Z",
            "createdDateTime":"2023-11-11 11:59:40Z",
            "lastAccessedDateTime":"2023-12-11 12:01:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/SPBTinkoff.py",
               "createdDateTime":"2023-11-11 11:59:40Z",
               "lastAccessedDateTime":"2023-12-11 12:01:34Z",
               "lastModifiedDateTime":"2023-11-29 13:51:24Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PY\"",
            "size":4127,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,7881299348287329",
            "name":"stock_data.xml",
            "lastModifiedDateTime":"2023-11-07 19:19:55Z",
            "createdDateTime":"2023-11-07 14:31:04Z",
            "lastAccessedDateTime":"2023-11-19 19:54:38Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/stock_data.xml",
               "createdDateTime":"2023-11-07 14:31:04Z",
               "lastAccessedDateTime":"2023-11-19 19:54:38Z",
               "lastModifiedDateTime":"2023-11-07 19:19:55Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"XML\"",
            "size":6196,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,34621422135468110",
            "name":"Target_LLC_2023-12-08_10-19-51.zip",
            "lastModifiedDateTime":"2023-12-08 10:20:21Z",
            "createdDateTime":"2023-12-08 10:20:02Z",
            "lastAccessedDateTime":"2023-12-10 18:13:24Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Target_LLC_2023-12-08_10-19-51.zip",
               "createdDateTime":"2023-12-08 10:20:02Z",
               "lastAccessedDateTime":"2023-12-10 18:13:24Z",
               "lastModifiedDateTime":"2023-12-08 10:20:21Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":24273415,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,844424930511143",
            "name":"test - Made with Clipchamp (1) (1).mp4",
            "lastModifiedDateTime":"2023-12-08 20:51:18Z",
            "createdDateTime":"2023-12-08 20:51:10Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/test - Made with Clipchamp (1) (1).mp4",
               "createdDateTime":"2023-12-08 20:51:10Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 20:51:18Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP4\"",
            "size":131908199,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1407374883986218",
            "name":"test - Made with Clipchamp (1) (2).mp4",
            "lastModifiedDateTime":"2023-12-08 20:55:26Z",
            "createdDateTime":"2023-12-08 20:55:28Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/test - Made with Clipchamp (1) (2).mp4",
               "createdDateTime":"2023-12-08 20:55:28Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 20:55:26Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP4\"",
            "size":53912496,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1970324837339980",
            "name":"test - Made with Clipchamp (1).mp4",
            "lastModifiedDateTime":"2023-12-08 20:46:01Z",
            "createdDateTime":"2023-12-08 20:45:30Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/test - Made with Clipchamp (1).mp4",
               "createdDateTime":"2023-12-08 20:45:30Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 20:46:01Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP4\"",
            "size":270707619,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1970324837255529",
            "name":"test - Made with Clipchamp.mp4",
            "lastModifiedDateTime":"2023-12-08 20:38:38Z",
            "createdDateTime":"2023-12-08 20:38:36Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/test - Made with Clipchamp.mp4",
               "createdDateTime":"2023-12-08 20:38:36Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 20:38:38Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP4\"",
            "size":470962661,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,12947848928734120",
            "name":"Track007.mp3",
            "lastModifiedDateTime":"2023-11-30 15:34:22Z",
            "createdDateTime":"2023-11-30 15:32:54Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Track007.mp3",
               "createdDateTime":"2023-11-30 15:32:54Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-11-30 15:34:22Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP3\"",
            "size":1887010,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1407374884055860",
            "name":"ty-vXcd3NBE.png",
            "lastModifiedDateTime":"2023-11-16 17:27:35Z",
            "createdDateTime":"2023-11-16 17:27:36Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/ty-vXcd3NBE.png",
               "createdDateTime":"2023-11-16 17:27:36Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-11-16 17:27:35Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PNG\"",
            "size":601970,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,6473924464549650",
            "name":"vcruntime140_1_app.zip",
            "lastModifiedDateTime":"2023-12-04 20:15:40Z",
            "createdDateTime":"2023-12-04 20:15:40Z",
            "lastAccessedDateTime":"2023-12-08 10:30:50Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/vcruntime140_1_app.zip",
               "createdDateTime":"2023-12-04 20:15:40Z",
               "lastAccessedDateTime":"2023-12-08 10:30:50Z",
               "lastModifiedDateTime":"2023-12-04 20:15:40Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":19885,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1407374883757846",
            "name":"vcruntime140_app.zip",
            "lastModifiedDateTime":"2023-12-04 20:07:02Z",
            "createdDateTime":"2023-12-04 20:07:04Z",
            "lastAccessedDateTime":"2023-12-08 07:14:30Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/vcruntime140_app.zip",
               "createdDateTime":"2023-12-04 20:07:04Z",
               "lastAccessedDateTime":"2023-12-08 07:14:30Z",
               "lastModifiedDateTime":"2023-12-04 20:07:02Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":49634,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,1688849860290556",
            "name":"vk_promocodes_activate-main.zip",
            "lastModifiedDateTime":"2023-11-16 16:09:31Z",
            "createdDateTime":"2023-11-16 16:09:32Z",
            "lastAccessedDateTime":"2023-11-19 19:54:38Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/vk_promocodes_activate-main.zip",
               "createdDateTime":"2023-11-16 16:09:32Z",
               "lastAccessedDateTime":"2023-11-19 19:54:38Z",
               "lastModifiedDateTime":"2023-11-16 16:09:31Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"ZIP\"",
            "size":3995,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,4503599627380241",
            "name":"x_f03efbcd.jpg",
            "lastModifiedDateTime":"2023-12-08 19:54:44Z",
            "createdDateTime":"2023-12-08 19:54:44Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/x_f03efbcd.jpg",
               "createdDateTime":"2023-12-08 19:54:44Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 19:54:44Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"JPG\"",
            "size":376586,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,29273397577936777",
            "name":"xss.png",
            "lastModifiedDateTime":"2023-12-08 20:19:29Z",
            "createdDateTime":"2023-12-08 20:19:30Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/xss.png",
               "createdDateTime":"2023-12-08 20:19:30Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 20:19:29Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PNG\"",
            "size":178,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,15199648742402402",
            "name":"xss_comment_exif_metadata_double_quote.png",
            "lastModifiedDateTime":"2023-12-08 20:14:52Z",
            "createdDateTime":"2023-12-08 20:15:46Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/xss_comment_exif_metadata_double_quote.png",
               "createdDateTime":"2023-12-08 20:15:46Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 20:14:52Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"PNG\"",
            "size":11806,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,11540474045150790",
            "name":"Ze44chcCSUpyVN1gmQ.mp4",
            "lastModifiedDateTime":"2023-12-08 19:57:37Z",
            "createdDateTime":"2023-12-08 19:57:38Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/Ze44chcCSUpyVN1gmQ.mp4",
               "createdDateTime":"2023-12-08 19:57:38Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 19:57:37Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP4\"",
            "size":230959,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         },
         {
            "id":"4007390500,11540474045178041",
            "name":"￐ﾛ￐ﾾ￐ﾺ￐ﾸ_[￐ﾟ￐ﾾ￐ﾻ￐ﾽ￐ﾾ￐ﾵ ￐ﾴ￑ﾃ￐ﾱ￐ﾻ￐ﾸ￑ﾀ￐ﾾ￐ﾲ￐ﾰ￐ﾽ￐ﾸ￐ﾵ (HDrezka Studio)]_S1_E1_360p.mp4",
            "lastModifiedDateTime":"2023-12-08 20:27:35Z",
            "createdDateTime":"2023-12-08 20:22:18Z",
            "lastAccessedDateTime":"2023-12-11 14:35:34Z",
            "fileSystemInfo":{
               "systemPath":"C:/Users/Bezzu/Downloads/￐ﾛ￐ﾾ￐ﾺ￐ﾸ_[￐ﾟ￐ﾾ￐ﾻ￐ﾽ￐ﾾ￐ﾵ ￐ﾴ￑ﾃ￐ﾱ￐ﾻ￐ﾸ￑ﾀ￐ﾾ￐ﾲ￐ﾰ￐ﾽ￐ﾸ￐ﾵ (HDrezka Studio)]_S1_E1_360p.mp4",
               "createdDateTime":"2023-12-08 20:22:18Z",
               "lastAccessedDateTime":"2023-12-11 14:35:34Z",
               "lastModifiedDateTime":"2023-12-08 20:27:35Z"
            },
            "type":"￐ﾤ￐ﾰ￐ﾹ￐ﾻ \"MP4\"",
            "size":148579289,
            "file":{
               
            },
            "parentReference":{
               "driveId":"local",
               "driveType":"local",
               "id":"4007390500,562949953454108"
            }
         }
      ],
      "@odata.count":85
   },
   null
]
```

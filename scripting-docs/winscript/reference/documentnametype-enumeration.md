---
title: "DOCUMENTNAMETYPE 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DOCUMENTNAMETYPE 列挙型"
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DOCUMENTNAMETYPE 列挙型
ついて説明します。ドキュメントのを取得するように入力します。  
  
## 構文  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,  
} DOCUMENTNAMETYPE;  
```  
  
## メンバー  
  
|メンバー|説明|  
|----------|--------|  
|DOCUMENTNAMETYPE\_APPNODE|アプリケーションのツリーに表示される名前を取得します。|  
|DOCUMENTNAMETYPE\_TITLE|ビューアーのタイトル バーに表示される名前を取得します。|  
|DOCUMENTNAMETYPE\_FILE\_TAIL|パスを指定せずにファイル名を取得します。|  
|DOCUMENTNAMETYPE\_URL|ドキュメントの URL を取得します。|  
|DOCUMENTNAMETYPE\_UNIQUE\_TITLE|タイトルを特定の列挙型が追加されます。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
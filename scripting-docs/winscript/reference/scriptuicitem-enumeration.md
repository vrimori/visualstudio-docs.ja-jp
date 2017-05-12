---
title: "SCRIPTUICITEM 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTUICITEM 列挙型
UI 項目の種類を表します。  [IActiveScriptSiteUIControl::GetUIBehavior メソッド](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)で使用します。  
  
## 構文  
  
```vb  
typedef enum tagSCRIPTUICITEM {   
    SCRIPTUICITEM_INPUTBOX = 1,   
    SCRIPTUICITEM_MSGBOX = 2,   
    } SCRIPTUICITEM;  
  
```  
  
## 列挙値  
  
|||  
|-|-|  
|SCRIPTUICITEM\_INPUTBOX|入力コントロール。|  
|SCRIPTUICITEM\_MSGBOX|メッセージ ボックス。|
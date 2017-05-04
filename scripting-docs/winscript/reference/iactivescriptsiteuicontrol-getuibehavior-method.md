---
title: "IActiveScriptSiteUIControl::GetUIBehavior メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptSiteUIControl::GetUIBehavior メソッド
を取得します [SCRIPTUICHANDLING 列挙型](../../winscript/reference/scriptuichandling-enumeration.md) 処理される UI コントロールを配置する方法を示します。  
  
## 構文  
  
```  
HRESULT GetUIBehavior(   
    [in] SCRIPTUICITEM UicItem,   
    [out] SCRIPTUICHANDLING * pUicHandling   
);  
  
```  
  
#### パラメーター  
 `UicItem`  
 コントロールの型。  
  
 `pUicHandling`  
 方法は、コントロール扱う必要があります。
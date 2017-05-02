---
title: "IDebugExpression::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.QueryIsComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::QueryIsComplete"
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::QueryIsComplete
操作が完了したかどうかを判定します。  
  
## 構文  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|成功する操作とメソッドがありません。|  
|`S_FALSE`|操作が保留中です。|  
  
## 解説  
 このメソッドは、操作が完了したかどうかを判定します。  
  
## 参照  
 [IDebugExpression インターフェイス](../../winscript/reference/idebugexpression-interface.md)
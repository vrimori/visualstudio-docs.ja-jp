---
title: "JsDebugPropertyInfo 構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsDebugPropertyInfo 構造体
プロパティに関する情報を指定します。  
  
## 構文  
  
```  
typedef struct tagJsDebugPropertyInfo  
{  
   BSTR name;  
   BSTR type;  
   BSTR value;  
   BSTR fullName;  
   JS_PROPERTY_ATTRIBUTES attr;  
} JsDebugPropertyInfo;  
```  
  
## メンバー  
 `name`  
 プロパティの名前。  
  
 `type`  
 プロパティの型。  
  
 `value`  
 プロパティの値。  
  
 `fullName`  
 プロパティの完全名。  
  
 `attr`  
 プロパティ属性を表す列挙体。  
  
## 必要条件  
 **ヘッダー:** jscript9diag.h  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)
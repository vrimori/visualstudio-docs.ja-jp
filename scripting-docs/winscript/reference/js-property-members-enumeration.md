---
title: "JS_PROPERTY_MEMBERS 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_MEMBERS
apilocation: jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JS_PROPERTY_MEMBERS 列挙型
オブジェクトのメンバーの要求で返される情報の種類を指定するフラグ。  
  
## 構文  
  
```  
enum JS_PROPERTY_MEMBERS  
{  
   JS_PROPERTY_MEMBERS_ALL = 0,  
   JS_PROPERTY_MEMBERS_ARGUMENTS = 1  
} JS_PROPERTY_MEMBERS;  
```  
  
## メンバー  
  
### 値  
  
|名前|説明|  
|--------|--------|  
|`JS_PROPERTY_MEMBERS_ALL`|すべてのメンバーを列挙する要求を表します。|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|引数だけを列挙する要求を表します。|  
  
## 必要条件  
 **ヘッダー:** jscript9diag.h  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)
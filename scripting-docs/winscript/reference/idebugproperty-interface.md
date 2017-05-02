---
title: "IDebugProperty インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugProperty インターフェイス"
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty インターフェイス
デバッグ名前、型、および値を持つエンティティの階層プロパティの説明に使用されます。  通常、`IDebugProperty` が式の評価、ステートメントの評価、または登録の評価の結果を記述するために使用されます。  
  
## Vtable 順序のメソッド  
 次の表は `IDebugProperty` のインターフェイスのメソッドを示します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|`DebugPropertyInfo` を取得します。この `IDebugProperty``.`を記述する|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|プロパティの拡張情報を取得します。|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|文字列からのプロパティの値を設定します。|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|プロパティのメンバーを列挙します。|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|プロパティの親を取得します。|  
  
## 要件  
 ヘッダー: dbgprop.h
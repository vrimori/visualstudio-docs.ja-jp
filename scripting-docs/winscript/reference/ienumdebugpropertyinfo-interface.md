---
title: "IEnumDebugPropertyInfo インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo インターフェイス"
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo インターフェイス
`DebugPropertyInfo` の構造を列挙します。  
  
## Vtable 順序のメソッド  
 `IEnumDebugPropertyInfo` のメソッドを次の表に示します。  
  
|メソッド|説明|  
|----------|--------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|列挙体シーケンスの `DebugPropertyInfo` の構造の指定した数を取得します。|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|列挙体シーケンスの `DebugPropertyInfo` の構造の指定した数の要素をスキップします。|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|現在の列挙状態と同じ列挙状態を格納する列挙子を作成します。|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|列挙子の `DebugPropertyInfo` の構造体の数を取得します。|  
  
## 要件  
 ヘッダー: dbgprop.h  
  
## 参照  
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)
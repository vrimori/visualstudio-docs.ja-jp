---
title: "IEnumDebugExtendedPropertyInfo インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo インターフェイス"
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo インターフェイス
`ExtendedDebugPropertyInfo` の構造を列挙します。  
  
## Vtable 順序のメソッド  
 `IEnumDebugExtendedPropertyInfo` のメソッドを次の表に示します。  
  
|メソッド|説明|  
|----------|--------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|現在の列挙状態と同じ列挙状態を格納する列挙子を作成します。|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|列挙子の `ExtendedDebugPropertyInfo` の構造体の数を取得します。|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|列挙体シーケンスの `ExtendedDebugPropertyInfo` の構造の指定した数を取得します。|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|列挙体シーケンスの `ExtendedDebugPropertyInfo` の構造の指定した数の要素をスキップします。|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|列挙体シーケンスを先頭にリセットします。|  
  
## 要件  
 ヘッダー: dbgprop.h  
  
## 参照  
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)
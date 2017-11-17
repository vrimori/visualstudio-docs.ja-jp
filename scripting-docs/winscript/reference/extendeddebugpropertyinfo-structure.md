---
title: "ExtendedDebugPropertyInfo 構造体 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 構造体
拡張、`DebugPropertyInfo`構造体メンバーを追加して拡張プロパティを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>メンバー  
 `dwValidFields`  
 列挙型のフィールドが初期化されますを指定するために使用します。  
  
 `bstrName`  
 コンテキスト内でプロパティ名。  
  
 `bstrType`  
 プロパティは、書式設定された文字列として入力します。  
  
 `bstrValue`  
 書式設定された文字列としてプロパティ値です。  
  
 `bstrFullName`  
 プロパティの完全名。  
  
 `dwAttrib`  
 デバッグ プロパティの属性のフラグを指定する列挙です。  
  
 `pDebugProp`  
 `IDebugProperty`これに対応するオブジェクト`ExtendedDebugPropertyInfo`です。  
  
 `nDISPID`  
 ディスパッチ id。  
  
 `nType`  
 拡張プロパティの型。  
  
 `varValue`  
 バリアント型に収まる場合は、拡張プロパティ値です。  
  
 `plbValue`  
 プロパティの値の実際のデータのバイト数。  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`これに対応するオブジェクト`ExtendedDebugPropertyInfo`です。  
  
## <a name="see-also"></a>関連項目  
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty インターフェイス](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)
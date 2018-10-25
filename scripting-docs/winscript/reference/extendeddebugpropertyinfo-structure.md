---
title: ExtendedDebugPropertyInfo 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62b9f3b5877f7919a57e9747355276e438240796
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888906"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 構造体
拡張、`DebugPropertyInfo`を特徴付ける拡張プロパティの追加メンバーを含む構造体。  
  
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
 列挙データ型フィールドが初期化されるかを指定するために使用します。  
  
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
 `IDebugProperty` これに対応するオブジェクト`ExtendedDebugPropertyInfo`します。  
  
 `nDISPID`  
 ディスパッチ id。  
  
 `nType`  
 拡張プロパティの型。  
  
 `varValue`  
 バリアントに収めることができる場合は、拡張プロパティ値。  
  
 `plbValue`  
 プロパティ値の実際のデータのバイト数。  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` これに対応するオブジェクト`ExtendedDebugPropertyInfo`します。  
  
## <a name="see-also"></a>関連項目  
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty インターフェイス](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)
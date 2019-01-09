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
ms.openlocfilehash: e0251d4b578a33a9eb5448c1ceb2b2607f82d43a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096772"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 構造体
拡張、`DebugPropertyInfo`を特徴付ける拡張プロパティの追加メンバーを含む構造体。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
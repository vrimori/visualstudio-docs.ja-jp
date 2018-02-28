---
title: "DebugPropertyInfo 構造体 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo 構造体
名前、型、および値を持つ階層的な性質のオブジェクトについて説明します。 ローカル変数やパラメーター、変数のウォッチ式のデバッグ プロパティを表すために使用し、登録します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwValidFields  
 列挙型のフィールドが初期化されますを指定するために使用します。  
  
 bstrName  
 コンテキスト内でプロパティ名。  
  
 bstrType  
 プロパティの型、書式設定された文字列。  
  
 bstrValue  
 プロパティの値を書式設定された文字列です。  
  
 bstrFullName  
 プロパティの完全名。  
  
 dwAttrib  
 デバッグ プロパティの属性のフラグを指定する列挙です。  
  
 pDebugProp  
 `IDebugProperty`この情報によって記述`DebugPropertyInfo`構造体。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)
---
title: DebugPropertyInfo 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dca3dac5c2e55e512bd4f798ca4a9bce82f7e00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874190"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo 構造体
オブジェクトの名前、型、および値を持つ階層的な性質について説明します。 ローカル変数、パラメーター、変数のウォッチ式、およびデバッグ プロパティを記述するために使用され、登録されます。  
  
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
 列挙データ型フィールドが初期化されるかを指定するために使用します。  
  
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
 `IDebugProperty`この情報が記載されている`DebugPropertyInfo`構造体。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)
---
title: DEBUG_REFERENCE_INFO |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a528f73f0a13ab2702e35212a3ba00f8c8c13378
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103332"
---
# <a name="debugreferenceinfo"></a>DEBUG_REFERENCE_INFO
参照を記述します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagDEBUG_REFERENCE_INFO {   
   DEBUGREF_INFO_FLAGS dwFields;  
   BSTR                bstrName;  
   BSTR                bstrType;  
   BSTR                bstrValue;  
   DBG_ATTRIB_FLAGS    dwAttrib;  
   REFERENCE_TYPE.     dwRefType;  
   IDebugReference2*   m_pReference;  
} DEBUG_REFERENCE_INFO;  
```  
  
```csharp  
public struct DEBUG_REFERENCE_INFO {   
   public uint             dwFields;  
   public string           bstrName;  
   public string           bstrType;  
   public string           bstrValue;  
   public ulong            dwAttrib;  
   public uint.            dwRefType;  
   public IDebugReference2 m_pReference;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwFields  
 フラグの組み合わせ、 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)のどのフィールドが埋められますを指定する列挙です。  
  
 bstrName  
 ユーザーが指定した名前、 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)オブジェクト。  
  
 bstrType  
 書式設定された文字列として参照の種類。  
  
 bstrValue  
 書式設定された文字列として参照値  
  
 dwAttrib  
 フラグの組み合わせ、 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)デバッグ プロパティの属性のフラグを指定する列挙です。  
  
 dwRefType  
 値、 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)参照型が強いか弱いかどうかを指定する列挙です。  
  
 m_pReference  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)リファレンス情報を指定するオブジェクト。  
  
## <a name="remarks"></a>コメント  
 この構造体がへの呼び出しに渡される、 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)格納するメソッド。 この構造体はからリストの一部としても返されます、 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)インターフェイス、さらへの呼び出しから返される、 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
---
title: THREADPROPERTY_FIELDS |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c5733bfa889a38c1d143fdd3bfbd8f208fed13a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125587"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
スレッドに関する情報を取得するを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>メンバー  
 TPF_ID  
 初期化/を使用して、`dwThreadId`のフィールド、 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)構造体。  
  
 TPF_SUSPENDCOUNT  
 初期化/を使用して、`dwSuspendCount`のフィールド、 `THREADPROPERTIE`S 構造体。  
  
 TPF_STATE  
 初期化/を使用して、`dwThreadState`のフィールド、 `THREADPROPERTIE`S 構造体。  
  
 TPF_PRIORITY  
 初期化/を使用して、`bstrPriority`のフィールド、 `THREADPROPERTIE`S 構造体。  
  
 TPF_NAME  
 初期化/を使用して、`bstrName`のフィールド、 `THREADPROPERTIE`S 構造体。  
  
 TPF_LOCATION  
 初期化/を使用して、`bstrLocation`のフィールド、 `THREADPROPERTIE`S 構造体。  
  
 TPF_ALLFIELDS  
 すべてのフィールドを指定します。  
  
## <a name="remarks"></a>コメント  
 これらの値が引数として渡される、 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)メソッドのどのフィールドを示すために、 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)構造が初期化するのには。  
  
 これらの値にも使用`dwFields`のメンバー、`THREADPROPERTIES`構造のどのフィールドが使用されていると有効なことを示します。  
  
 これらのフラグは、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
---
title: "THREADPROPERTIES |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 86fc5231f8d577e0456ce2d9f76c7b6d7f831280
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="threadproperties"></a>THREADPROPERTIES
スレッドのプロパティについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwFields  
 フラグの組み合わせ、 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)有効ではこの構造体のフィールドを説明する列挙です。  
  
 dwThreadId  
 スレッドの id。  
  
 dwSuspendCount  
 スレッドは、カウントを中断します。  
  
 dwThreadState  
 値、 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)操作スレッドの状態を示す列挙値。  
  
 bstrPriority  
 スレッドの優先度を指定する文字列たとえば、"上記 Normal"、"Normal"、または時間で「重大」です。  
  
 bstName  
 スレッド名。  
  
 bstrLocation  
 通常の実行が中断されているメソッドの名前として表現されるスレッドの場所 (通常、最上位のスタック フレーム)。  
  
## <a name="remarks"></a>コメント  
 この構造体への呼び出しによって入力されます、 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)メソッドです。 情報が返されます。 これが設定で通常使用される、**スレッド**ウィンドウです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
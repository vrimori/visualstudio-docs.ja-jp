---
title: THREADPROPERTIES |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2061682280ab110ee7c951ed41cf6ccd42f5c080
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814806"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

スレッドのプロパティについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 フラグの組み合わせ、 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)有効ではこの構造体のフィールドを記述する列挙。  
  
 dwThreadId  
 スレッドの id。  
  
 dwSuspendCount  
 スレッドは中断回数です。  
  
 dwThreadState  
 値、 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)動作のスレッドの状態を示す列挙値。  
  
 bstrPriority  
 スレッドの優先順位を指定する文字列たとえば、"上記 Normal"、"Normal"または「時間は重要な」。  
  
 bstName  
 スレッド名。  
  
 bstrLocation  
 通常の実行が中断されているメソッドの名前として表現されるスレッドの場所 (通常は最上位のスタック フレーム)。  
  
## <a name="remarks"></a>Remarks  
 この構造体への呼び出しによって入力されます、 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)メソッド。 そのために返される情報は通常設定で使用、**スレッド**ウィンドウ。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)


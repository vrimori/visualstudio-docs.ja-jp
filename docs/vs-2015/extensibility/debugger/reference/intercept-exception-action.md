---
title: INTERCEPT_EXCEPTION_ACTION |Microsoft Docs
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
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c36427fc7610e1f179553bde904785118feb9fba
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921822"
---
# <a name="interceptexceptionaction"></a>INTERCEPT_EXCEPTION_ACTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

例外をインターセプトするときに実行するアクションを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
typedef DWORD INTERCEPT_EXCEPTION_ACTION;  
```  
  
```csharp  
public enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
```  
  
#### <a name="parameters"></a>パラメーター  
 IEA_INTERCEPT  
 現在の例外をインターセプトできるようにします。 これは現時点ではサポートされている唯一の値であり、指定する必要があります。  
  
## <a name="remarks"></a>Remarks  
 これらの値に渡される、 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)


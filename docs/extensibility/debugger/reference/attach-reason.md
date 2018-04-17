---
title: ATTACH_REASON |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2dc7736f9210ef15cec8cece45d7899cc116a334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="attachreason"></a>ATTACH_REASON
デバッグ エンジン (DE)、[プログラム] ノードにアタッチする理由を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>メンバー  
 ATTACH_REASON_AUTO  
 プロセスがデバッグ モードでは現在のでをアタッチします。  
  
 ATTACH_REASON_LAUNCH  
 アタッチ プロセスが開始されました。  
  
 ATTACH_REASON_USER  
 ユーザーの要求のためにアタッチします。  
  
## <a name="remarks"></a>コメント  
 これらの値はパラメーターとして使用、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)と[アタッチ](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [添付](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
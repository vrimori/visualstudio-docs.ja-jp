---
title: "ATTACH_REASON |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ATTACH_REASON
helpviewer_keywords: ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 527e7a445356a46abdd6f2edb0555b7c5c9c7de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [添付](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
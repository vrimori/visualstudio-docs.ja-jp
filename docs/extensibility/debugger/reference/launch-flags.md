---
title: LAUNCH_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 74ec5b3cc02efa75e84d52910c02ea693a7ab8a6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903490"
---
# <a name="launchflags"></a>LAUNCH_FLAGS
デバッグの起動フラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_LAUNCH_FLAGS {   
   LAUNCH_DEBUG      = 0x0000,  
   LAUNCH_NODEBUG    = 0x0001,  
   LAUNCH_ENABLE_ENC = 0x0002,  
   LAUNCH_MERGE_ENV  = 0x0004  
};  
typedef DWORD LAUNCH_FLAGS;  
```  
  
```csharp  
public enum enum_LAUNCH_FLAGS {   
   LAUNCH_DEBUG      = 0x0000,  
   LAUNCH_NODEBUG    = 0x0001,  
   LAUNCH_ENABLE_ENC = 0x0002,  
   LAUNCH_MERGE_ENV  = 0x0004  
};  
```  
  
## <a name="members"></a>メンバー  
 LAUNCH_DEBUG  
 デバッグ プロセスを起動します。  
  
 LAUNCH_NODEBUG  
 デバッグを行わず、プロセスを起動します。  
  
 LAUNCH_ENABLE_ENC  
 非推奨では使用しないでください。  
  
 LAUNCH_MERGE_ENV  
 プロセスを起動し、ホストを起動すると、環境をマージします。  
  
## <a name="remarks"></a>Remarks  
 これらの値が引数として渡される、 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)メソッド。  
  
 これらのフラグは、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
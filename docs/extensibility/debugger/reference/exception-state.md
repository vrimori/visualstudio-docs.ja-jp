---
title: "EXCEPTION_STATE |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EXCEPTION_STATE
helpviewer_keywords: EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69c0f1f4f9396d57af1381962e12b0d3201aa3ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
例外状態を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>メンバー  
 EXCEPTION_NONE  
 例外では停止されません。  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 例外の最初の起動処理を停止します。 例外イベントを記述する場合、このフラグは、例外イベントが初回例外イベントを示します。  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 例外の 2 つ目の実行を停止します。 例外イベントを記述する場合は、例外イベントでは、次の例外イベントを示します。  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 ユーザー モード例外の最初の起動処理を停止します。 例外イベントを記述する場合は、例外イベントでは、ユーザーの初回例外イベントを示します。  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 ユーザー モード例外がキャッチされない場合は停止します。 例外イベントを記述する場合、例外イベントがキャッチされていないユーザー モード例外イベントことを示します。  
  
 EXCEPTION_STOP_ALL  
 すべての例外で停止します。 例外イベントを記述する場合は使用されません。  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 例外イベントを記述する場合から例外を続行することはできませんを示します。  
  
 EXCEPTION_CODE_SUPPORTED  
 例外のコードをサポートしていることを示します。 例外を表示するために使用します。  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 例外コードを 16 進数で表示することを示します。 例外を表示するために使用されます。  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 例外コードが JustMyCode をサポートしていることを示します。 例外を表示するために使用されます。  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 マネージ コードのデバッガーが例外を処理することを示します。 指定しない場合、セット、既定のデバッガーが例外を処理します。 これは渡される、 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)メソッドで使用されていないと、 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)構造体。  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 旧式で、使用しないでください。  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 旧式で、使用しないでください。  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 旧式で、使用しないでください。  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 旧式で、使用しないでください。  
  
## <a name="remarks"></a>コメント  
 として使用される、`dwState`のメンバー、 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)例外とは何を実行できる状態を示すための構造体。  
  
 これらの値が渡されるも、 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)すべての例外の状態を設定します。  
  
 これらのフラグは、ビットごとの OR と組み合わせることがあります。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
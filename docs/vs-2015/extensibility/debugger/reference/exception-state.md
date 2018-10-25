---
title: EXCEPTION_STATE |Microsoft Docs
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
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99f78b2de9b68b638feaf3f84eba4cc12c742ed0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879728"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

例外の状態を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 例外は停止されません。  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 例外の最初の実行を停止します。 例外イベントを記述する場合、このフラグは、例外イベントでは、初回の例外イベントを示します。  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 例外の 2 つ目の実行を停止します。 例外イベントを記述する場合は、例外イベントでは、次の例外イベントを示します。  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 ユーザー モードの例外の最初の実行を停止します。 例外イベントを記述する場合は、例外イベントのユーザーの初回の例外イベントであることを示します。  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 ユーザー モードの例外がキャッチされない場合は停止します。 例外イベントを記述する場合は、例外イベントのキャッチされないユーザー モード例外イベントであることを示します。  
  
 EXCEPTION_STOP_ALL  
 すべての例外で停止します。 例外イベントを記述する場合は使用されません。  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 例外イベントを記述する場合から例外を続行することはできませんを示します。  
  
 EXCEPTION_CODE_SUPPORTED  
 例外にそれをサポートするコードがあることを示します。 例外を表示するために使用  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 例外コードを 16 進数で表示することを示します。 例外を表示するために使用されます。  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 例外コード JustMyCode をサポートしていることを示します。 例外を表示するために使用されます。  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 マネージ コードのデバッガーが例外を処理することを示します。 指定しない場合、セット、既定のデバッガー、例外を処理します。 渡されます、 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)メソッドで使用されていないと、 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)構造体。  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 廃止された、使用しないでください。  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 廃止された、使用しないでください。  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 廃止された、使用しないでください。  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 廃止された、使用しないでください。  
  
## <a name="remarks"></a>Remarks  
 として使用される、`dwState`のメンバー、 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)構造については、何ができると、例外の状態を示します。  
  
 これらの値は渡されることも、 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)メソッドすべての例外の状態を設定します。  
  
 これらのフラグは、ビットごとの OR と組み合わせることがあります。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)


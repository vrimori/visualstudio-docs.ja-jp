---
title: "EXCEPTION_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_STATE"
helpviewer_keywords: 
  - "EXCEPTION_STATE 列挙型"
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

例外の状態を指定します。  
  
## 構文  
  
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
  
```c#  
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
  
## メンバー  
 EXCEPTION\_NONE  
 例外で中断しないようにします。  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE  
 例外の最初のオカレンスで停止します。  例外イベントを記述する場合はこのフラグは例外イベントの初回例外イベントであることを示します。  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE  
 例外の 2 番目の実行で停止します。  例外イベントを記述する場合は例外イベントがセカンド チャンス例外のイベントであることを示します。  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE  
 ユーザー モード例外の最初のオカレンスで停止します。  例外イベントを記述すると例外イベントの初回例外のユーザーのイベントであることを示します。  
  
 EXCEPTION\_STOP\_USER\_UNCAUGHT  
 ユーザー モード例外がキャッチされないときは停止します。  例外イベントを記述すると例外イベントの状態でユーザー モード例外イベントであることを示します。  
  
 EXCEPTION\_STOP\_ALL  
 すべての例外で停止します。  例外イベントについての場合は使用されていません。  
  
 EXCEPTION\_CAN のない \_BE\_CONTINUED  
 例外イベントを記述する場合は例外を続行できないことを示します。  
  
 EXCEPTION\_CODE\_SUPPORTED  
 例外にはをサポートするコードがあることを示します。  例外の表示で使用される  
  
 EXCEPTION\_CODE\_DISPLAY\_IN\_HEX  
 例外コードが 16 進数で表示する必要があることを示します。  例外の表示に使用します。  
  
 EXCEPTION\_JUST\_MY\_CODE\_SUPPORTED  
 例外コードの JustMyCode をサポートすることを示します。  例外の表示に使用します。  
  
 EXCEPTION\_MANAGED\_DEBUG\_ASSISTANT  
 例外処理があるとマネージ コードのデバッガー示します。  設定しないと既定のデバッガー例外を処理する場合。  これは [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) のメソッドに渡され[EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) の構造体は使用されません。  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE\_USE\_PARENT  
 互換性のため使用しないでください。  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE\_USE\_PARENT  
 互換性のため使用しないでください。  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE\_USE\_PARENT  
 互換性のため使用しないでください。  
  
 EXCEPTION\_STOP\_USER\_SECOND\_CHANCE\_USE\_PARENT  
 互換性のため使用しないでください。  
  
## 解説  
 実行できる操作については例外の状態を示すために [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) の構造体の `dwState` のメンバーとして使用することもできます。  
  
 これらの値は[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) のメソッドはすべての例外の状態を設定するために渡されます。  
  
 これらのフラグはまたはこれらのビットごとに組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
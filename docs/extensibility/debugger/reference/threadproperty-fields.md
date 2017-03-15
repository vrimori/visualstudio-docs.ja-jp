---
title: "THREADPROPERTY_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTY_FIELDS"
helpviewer_keywords: 
  - "THREADPROPERTY_FIELDS 列挙型"
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

スレッドに関してどの情報を取得するかを指定します。  
  
## 構文  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
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
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## メンバー  
 TPF\_ID  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) の構造体の初期化と `dwThreadId` のフィールドを使用します。  
  
 TPF\_SUSPENDCOUNT  
 `THREADPROPERTIE`S の構造体の初期化と `dwSuspendCount` のフィールドを使用します。  
  
 TPF\_STATE  
 `THREADPROPERTIE`S の構造体の初期化と `dwThreadState` のフィールドを使用します。  
  
 TPF\_PRIORITY  
 `THREADPROPERTIE`S の構造体の初期化と `bstrPriority` のフィールドを使用します。  
  
 TPF\_NAME  
 `THREADPROPERTIE`S の構造体の初期化と `bstrName` のフィールドを使用します。  
  
 TPF\_LOCATION  
 `THREADPROPERTIE`S の構造体の初期化と `bstrLocation` のフィールドを使用します。  
  
 TPF\_ALLFIELDS  
 すべてのフィールドを指定します。  
  
## 解説  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) の構造体のフィールドが初期化するかを示すためにこれらの値は引数 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) のメソッドに渡されます。  
  
 `THREADPROPERTIES` の構造体の `dwFields` のメンバーはこれらの値がどのフィールドが使用され有効かを示すために使用されます。  
  
 これらのフラグはビットごと `OR` に組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
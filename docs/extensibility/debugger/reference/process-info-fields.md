---
title: "PROCESS_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FIELDS"
helpviewer_keywords: 
  - "PROCESS_INFO_FIELDS 列挙型"
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロセスのために取得するような情報を指定します。  
  
## 構文  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```c#  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## メンバー  
 PIF\_FILE\_NAME  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) の構造体の初期化と `bstrFileName` のフィールドを使用します。  
  
 PIF\_BASE\_NAME  
 `PROCESS_INFO` の構造体の初期化と `bstrBaseName` のフィールドを使用します。  
  
 PIF\_TITLE  
 `PROCESS_INFO` の構造体の初期化と `bstrTitle` のフィールドを使用します。  
  
 PIF\_PROCESS\_ID  
 `PROCESS_INFO` の構造体の初期化と `ProcessId` のフィールドを使用します。  
  
 PIF\_SESSION\_ID  
 `PROCESS_INFO` の構造体の初期化と `dwSessionId` のフィールドを使用します。  
  
 PIF\_ATTACHED\_SESSION\_NAME  
 `PROCESS_INFO` の構造体の初期化と `bstrAttachedSessionName` のフィールドを使用します。  
  
 PIF\_CREATION\_TIME  
 `PROCESS_INFO` の構造体の初期化と `CreationTime` のフィールドを使用します。  
  
 PIF\_FLAGS  
 `PROCESS_INFO` の構造体の初期化と `Flags` のフィールドを使用します。  
  
 PIF\_ALL  
 すべてのフィールドに表示されます。  
  
## 解説  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) の構造体のフィールドが初期化するかを示すためにメソッドを [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) に渡されます。  
  
 フィールドを使用して有効であることを示すために `PROCESS_INFO` の構造体の `Fields` のフィールドにも使用します。  
  
 これらのフラグはビットごと `OR` に組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)
---
title: "GETHOSTNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETHOSTNAME_TYPE"
helpviewer_keywords: 
  - "GETHOSTNAME_TYPE 列挙型"
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GETHOSTNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ホスト名の種類を指定します。  
  
## 構文  
  
```cpp#  
enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
typedef DWORD GETHOSTNAME_TYPE;  
```  
  
```c#  
public enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
```  
  
## メンバー  
 GHN\_FRIENDLY\_NAME  
 ホストの表示名を指定します。  
  
 GHN\_FILE\_NAME  
 ホストのファイル名を指定します。  
  
## 解説  
 引数としてこれらの値は [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) のメソッドにさまざまな形式のホスト名を取得するために渡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
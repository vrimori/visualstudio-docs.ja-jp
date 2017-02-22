---
title: "GETNAME_TYPE | Microsoft Docs"
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
  - "GETNAME_TYPE"
helpviewer_keywords: 
  - "GETNAME_TYPE 列挙型"
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ファイル名の型を取得するように指定します。  
  
## 構文  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```c#  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## メンバー  
 GN\_NAME  
 ドキュメントまたはコンテキストの表示名を指定します。  
  
 GN\_FILENAME  
 ドキュメントまたはコンテキストの完全パスを指定します。  
  
 GN\_BASENAME  
 ドキュメントまたはコンテキストの完全パスではなく基本ファイル名を指定します。  
  
 GN\_MONIKERNAME  
 モニカーの形式でドキュメントまたはコンテキストの一意の名前を指定します。  
  
 GN\_URL  
 ドキュメントまたはコンテキストの URL の名前を指定します。  
  
 GN\_TITLE  
 が 1 の場合ドキュメントのタイトルを指定します。  
  
 GN\_STARTPAGEURL  
 プロセスの開始ページの URL を取得します。  
  
## 解説  
 パラメーターとしてこれらの値は [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) と [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) のメソッドに返されるかなど名前を指定するに渡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
---
title: "SEEK_START | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEEK_START"
helpviewer_keywords: 
  - "SEEK_START 列挙型"
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SEEK_START
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

構成ストリームの検索を開始する場所を指定します。  
  
## 構文  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```c#  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## メンバー  
 SEEK\_START\_BEGIN  
 現在のドキュメントの先頭から検索を開始します。  
  
 SEEK\_START\_END  
 現在のドキュメントの末尾に移動します。  
  
 SEEK\_START\_CURRENT  
 現在のドキュメント内の現在位置から検索を開始します。  
  
 SEEK\_START\_CODECONTEXT  
 現在のドキュメントのコード コンテキストで検索します。  
  
 SEEK\_START\_CODELOCID  
 特定のコード位置の識別子で検索します。  コード位置の識別子は [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md) を呼び出すことになります。  
  
## 解説  
 [シーク](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) のメソッドに引数として渡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [シーク](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)
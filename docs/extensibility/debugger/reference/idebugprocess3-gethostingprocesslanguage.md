---
title: "IDebugProcess3::GetHostingProcessLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetHostingProcessLanguage"
helpviewer_keywords: 
  - "IDebugProcess3::GetHostingProcessLanguage"
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::GetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md) へのメソッドの呼び出しによって設定されたこのプロセスの言語を表す `GUID`。  
  
## 構文  
  
```cpp  
HRESULT GetHostingProcessLanguage(  
   GUID* pguidLang  
);  
```  
  
```c#  
int GetHostingProcessLanguage(  
   out Guid pguidLang  
);  
```  
  
#### パラメーター  
 `pguidLang`  
 \[出力\] このプロセスの言語 `GUID`。   言語が設定されていないことを `GUID_NULL` \(C\+\+\) または \(C\#\) `Guid.Empty` を意味します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)
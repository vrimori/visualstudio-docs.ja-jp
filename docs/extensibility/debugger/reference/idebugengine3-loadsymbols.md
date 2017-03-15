---
title: "IDebugEngine3::LoadSymbols | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::LoadSymbols"
helpviewer_keywords: 
  - "IDebugEngine3::LoadSymbols"
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

\(必須\) でこのデバッグ エンジンによってデバッグ中のすべてのモジュールのシンボルを読み込みます。  
  
## 構文  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```c#  
int LoadSymbols();  
```  
  
#### パラメーター  
 なし。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コードを返します。  
  
## 解説  
 これはこのデバッグ エンジンによって参照されるすべてのモジュールのデバッグ シンボルを読み込みます。  シンボルは既に読み込まれていないときにのみ読み込まれます。  シンボルは [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) の呼び出しで設定されたパスで検索されます。  
  
## 参照  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
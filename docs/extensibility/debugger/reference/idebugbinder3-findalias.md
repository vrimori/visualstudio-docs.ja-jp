---
title: "IDebugBinder3::FindAlias | Microsoft Docs"
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
  - "IDebugBinder3::FindAlias"
helpviewer_keywords: 
  - "IDebugBinder3::FindAlias メソッド"
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは名前を持つエイリアスを検索します。  これによりプログラムのすべてのエイリアスを検索します。  
  
## 構文  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### パラメーター  
 `pcstrName`  
 \[入力\] 検索するエイリアスの名前。  
  
 `ppAlias`  
 \[入力\] エイリアスがある [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) のインターフェイスによって表される見つかりました。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` \(エイリアス\) がある場合はエラー コード。  
  
## 解説  
 このメソッドを呼び出す前にnull 値にオブジェクトを初期化します ; その後NULL 値のエイリアスが見つかったかどうかを判断するためにそのテストします。  
  
## 参照  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
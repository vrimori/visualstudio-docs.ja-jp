---
title: "IDebugProgramHost2::GetHostName | Microsoft Docs"
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
  - "IDebugProgramHost2::GetHostName"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostName"
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプログラムのホスティングプロセスのタイトル表示名またはファイル名を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```c#  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### パラメーター  
 `dwType`  
 \[入力\] [GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) の列挙体の値。  
  
 `pbstrHostName`  
 \[入力\] 要求されたホスティングプロセスの名前を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドの一般的な実装では`dwType` のパラメーターは無視されホスト コンピューターの表示名が返されます。  別の可能な実装は名前を取得するために [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) メソッドの呼び出しに `dwType` のパラメーターを渡すことです。  
  
## 参照  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
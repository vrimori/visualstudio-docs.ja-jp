---
title: "IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs"
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
  - "IDebugBinder3::GetExceptionObjectAndType"
helpviewer_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType メソッド"
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはオブジェクトに関連付けられていない場合は例外を取得します。  
  
## 構文  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### パラメーター  
 `ppException`  
 \[入力\] 例外を表すオブジェクトを返します。  
  
 `ppField`  
 \[入力\] オブジェクトを表す例外を発生させる可能性がある特定のフィールドを返します \(これは null になることがあります\)。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
> [!NOTE]
>  例外があるかどうかを確認するには`ppException` によって返される値をチェックする : このが null 値の場合は例外がこのオブジェクトに関連付けられません。  
  
## 参照  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
---
title: "IDebugAddress::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress::GetAddress"
helpviewer_keywords: 
  - "IDebugAddress:GetAddress メソッド"
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

範囲またはコンテナー内のオブジェクトと位置を示す構造体を返します。  
  
## 構文  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```c#  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### パラメーター  
 `pAddress`  
 \[入力出力\] このメソッドによって設定された [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) の構造体。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) の構造は適切な情報を入力するとこのメソッドに渡されます。  この情報がどのように解釈されるかどうかは返される情報をシンボル ハンドラーの型自体によって。  詳細については、「[DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)」を参照してください。  
  
## 参照  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
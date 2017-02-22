---
title: "IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs"
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
  - "IDebugCustomAttribute::GetAttributeBytes"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

バイトの BLOB として属性情報を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```c#  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### パラメーター  
 `ppBlob`  
 \[入力出力\] 属性のバイトが格納された配列。  
  
 `pdwLen`  
 \[入力出力\] 最大バイト数を `ppBlob` の配列で返されるように指定し配列に実際に書き込まれたバイト数を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 使用可能な属性のバイト数を返すように null 値を `ppBlob` のパラメーターを設定します。  は配列を割り当て`ppBlob` のパラメーターにその配列を渡します。  
  
 属性はカスタム属性のバイトの生データを表します。  
  
## 参照  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
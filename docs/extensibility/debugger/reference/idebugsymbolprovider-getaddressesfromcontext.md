---
title: "IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetAddressesFromContext"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext メソッド"
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはデバッグのアドレスの配列にドキュメントのコンテキストをマップします。  
  
## 構文  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### パラメーター  
 `pDocContext`  
 \[入力\] ドキュメントのコンテキスト。  
  
 `fStatmentOnly`  
 true の場合デバッグが単一のステートメントに制限 \[入力\] アドレス。  
  
 `ppEnumBegAddresses`  
 \[出力\] このステートメントまたは行に関連付けられたデバッグの開始アドレス用の列挙子を返します。  
  
 `ppEnumEndAddresses`  
 \[出力\] このステートメントまたは行に関連付けられた終了デバッグのアドレスの [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) の列挙子を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 ドキュメントのコンテキストはソース行の範囲を示します。  このメソッドはこれに関連付けられたデバッグの開始および終了アドレスを指定します。  一部の言語ではの範囲のステートメントを複数行または行使用して複数のステートメントが含まれています。  このメソッドは単一のステートメントにデバッグのアドレスを制限するにはフラグを提供します。  
  
 単一のステートメントがテンプレートの場合のように複数のデバッグのアドレスを配置することもできます。  
  
## 参照  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
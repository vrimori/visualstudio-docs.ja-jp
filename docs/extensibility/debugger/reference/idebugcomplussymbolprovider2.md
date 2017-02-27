---
title: "IDebugComPlusSymbolProvider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider2 インターフェイス"
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugComPlusSymbolProvider2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

COM\+ シンボルのプロバイダーをマネージ コードに固有の **IDebugComPlusSymbolProvider を**  表し拡張メソッドです [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)。  
  
## 構文  
  
```  
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider  
```  
  
## メソッド  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[FunctionHasLineInfo](../Topic/IDebugComPlusSymbolProvider2::FunctionHasLineInfo.md)|指定したメソッドに行情報を持つかどうかを判定します。|  
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|名前を持つ型を取得します。|  
|[GetTypeFromToken](../Topic/IDebugComPlusSymbolProvider2::GetTypeFromToken.md)|トークンの型を取得します。|  
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|デバッグのアドレス指定がシーケンス ポイントであるかどうかを判定します。|  
|[LoadSymbolsFromCallback](../Topic/IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback.md)|指定されたコールバック メソッドを使用してデバッグ シンボルを読み込みます。|  
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|**ICorDebugModule を**  持つデータ ストリームから読み込みます。デバッグ シンボルがついて説明します。|  
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|**ICorDebugModule の**  オブジェクトがある作業負荷のデバッグ シンボルです。|  
  
## 必要条件  
 ヘッダー : Sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll
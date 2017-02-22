---
title: "IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs"
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
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

シンボルの読み込みプロセスの結果を取得するイベント ハンドラーによって呼び出されます。  
  
## 構文  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```c#  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### パラメーター  
 `pModule`  
 \[入力\] IDebugModule3 表すオブジェクト シンボルが読み込まれたモジュール。  
  
 `pbstrDebugMessage`  
 \[入力出力\] モジュールからエラー メッセージの文字列を返します。  エラーがない場合この文字列はモジュール名が含まれますが空ではありません。  
  
> [!NOTE]
>  \[C\+\+\] `pbstrDebugMessage` は `NULL` である必要があり`SysFreeString` と放されなければ必要があります。  
  
 `pdwModuleInfoFlags`  
 \[入力\] のシンボルが読み込まれているかどうかを示す [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) の列挙体のフラグの組み合わせ。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  
  
## 解説  
 モジュールのデバッグ シンボルの読み込みが行われた後のイベント ハンドラーが [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) を受け取るとハンドラーはロード テストの結果を確認するに thismethod を呼び出すことができます。  
  
## 参照  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
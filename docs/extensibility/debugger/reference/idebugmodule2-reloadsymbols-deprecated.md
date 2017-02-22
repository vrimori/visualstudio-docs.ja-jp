---
title: "IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs"
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
  - "IDebugModule2::ReloadSymbols"
helpviewer_keywords: 
  - "IDebugModule2::ReloadSymbols メソッド"
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

互換性のために残されています。  使用しないでください。  このモジュールのシンボルを再読み込みします。  
  
## 構文  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```c#  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### パラメーター  
 `pszUrlToSymbols`  
 \[入力\] シンボル ストアへのパス。  
  
 `pbstrDebugMessage`  
 \[出力\] モジュールのウィンドウのモジュール名の右側に表示されるエラー メッセージまたは返しますステータスなどの情報メッセージが表示されます。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  デバッグ エンジンは`E_FAIL` を常に返す必要です。  
  
## 解説  
 このメソッドは現在サポートされていません。  [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md) の代わりにメソッドを実装します。  
  
## 参照  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)
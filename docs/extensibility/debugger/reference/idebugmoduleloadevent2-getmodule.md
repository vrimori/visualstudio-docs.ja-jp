---
title: "IDebugModuleLoadEvent2::GetModule | Microsoft Docs"
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
  - "IDebugModuleLoadEvent2::GetModule"
helpviewer_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

読み込まれたかまたはアンロードするモジュールを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```c#  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### パラメーター  
 `pModule`  
 \[入力\] 読み込みまたはアンロードしているモジュールを表す [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) のオブジェクトを返します。  
  
 `pbstrDebugMessage`  
 \[入力出力\] このイベントを表すオプションのメッセージを返します。  このパラメーターが null 値の場合メッセージは要求されません。  
  
 `pbLoad`  
 \[入力出力\] モジュールがアンロードされるとモジュールを読み込むとゼロ ゼロ以外 `TRUE`\(\)`FALSE`\(\)。  このパラメーターが null 値の場合はステータスは要求されません。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
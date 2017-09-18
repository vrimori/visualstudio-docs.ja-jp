---
title: "IDebugCustomViewer::DisplayValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer::DisplayValue"
helpviewer_keywords: 
  - "IDebugCustomViewer::DisplayValue"
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは指定された値を表示します。  
  
## 構文  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```c#  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### パラメーター  
 `hwnd`  
 \[入力\] 親ウィンドウ  
  
 `dwID`  
 \[入力\] 複数の型をサポートするカスタム ビューアーの ID。  
  
 `pHostServices`  
 \[入力\] 予約されています。  null 値は常に設定します。  
  
 `pDebugProperty`  
 \[入力\] インターフェイス。表示される値を取得するために使用できます。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  
  
## 解説  
 にこのメソッドを必要なウィンドウを作成しその値を表示入力を待ちウィンドウが閉じて呼び出し元に戻す前に 「」すべてモーダルです。  これはメソッドがウィンドウの破棄は待機作成したユーザー入力にすべての要素の属性値を出力のウィンドウで処理することを意味します。  
  
 —文字列値を表すことができます [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) の特定のオブジェクト値の変更をサポートするには[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) のメソッドを使用できます。  は同じオブジェクト メソッドのこの `DisplayValue` を実行する式エバリュエーターに対してカスタム インターフェイスを作成する必要が `IDebugProperty3` 実装するインターフェイスです。  このカスタム インターフェイスは任意のサイズや複雑さのデータを変更するためのメソッドを提供します。  
  
## 参照  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
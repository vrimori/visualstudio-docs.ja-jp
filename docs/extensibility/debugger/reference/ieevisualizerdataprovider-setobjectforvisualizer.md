---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs"
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
  - "IEEVisualizerDataProvider::SetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer メソッド"
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはビジュアライザーを表すオブジェクトを変更します。  
  
## 構文  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```c#  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### パラメーター  
 `pNewObject`  
 \[入力\] 設定するオブジェクト。  
  
 `error`  
 オブジェクトを設定するエラーがある場合は \[出力\] この文字列をエラー メッセージ。  
  
 `pException`  
 \[入力\] エラーが発生した場合このオブジェクトはその例外を保持します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 これはエラー情報を返す方法の決定を実装する必要があります。  ただしエラーが発生した例外オブジェクトがエラーが見つかりこのメソッドは例外オブジェクトを常に返す必要であることを確認するために返されたかどうかを確認するにはいくつかの呼び出し元が確認することができます。  エラー文字列が呼び出し元で利用する場合は指定する必要があります。  
  
## 参照  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
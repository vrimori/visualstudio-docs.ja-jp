---
title: "IDebugFunctionObject2::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::Evaluate"
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

関数を呼び出してオブジェクトとして結果値を返します。  
  
## 構文  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### パラメーター  
 `ppParams`  
 \[入力\] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) パラメーターを表すオブジェクトの配列。  このパラメーターにはこのインターフェイスの作成方法の 1 を使用して作成されています。  
  
 `dwParams`  
 \[入力\] `ppParams` の配列パラメーターの数。  
  
 `dwEvalFlags`  
 \[入力\] 評価がどのように実行されるかを指定する [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) の列挙体のフラグの組み合わせ。  
  
 `dwTimeout`  
 \[出力\] このメソッドから制御が戻るまで待機するミリ秒単位の最大時間を指定します。  無期限に待機するために  **無限**  を使用します。  
  
 `ppResult`  
 \[入力\] オブジェクトとして関数値を表す **IDebugObject を**  返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
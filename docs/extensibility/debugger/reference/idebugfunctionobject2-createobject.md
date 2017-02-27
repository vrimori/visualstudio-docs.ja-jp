---
title: "IDebugFunctionObject2::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::CreateObject"
  - "CreateObject"
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

評価のフラグの設定およびタイムアウト値を持つコンストラクターを使用してオブジェクトを作成します。  
  
## 構文  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### パラメーター  
 `pConstructor`  
 \[入力\] 作成されるオブジェクトのコンストラクターを表すオブジェクトの [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)。  
  
 `dwArgs`  
 \[入力\] `pArg` の配列パラメーターの数。  コンストラクターに渡されるパラメーターの数を表します。  
  
 `pArgs`  
 \[入力\] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) パラメーターを表すオブジェクトの配列はコンストラクターに渡されました。  
  
 `dwEvalFlags`  
 \[入力\] 評価がどのように実行されるかを指定する [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) の列挙体のフラグの組み合わせ。  
  
 `dwTimeout`  
 \[出力\] このメソッドから制御が戻るまで待機する最大時間 \(ミリ秒単位\)。  無期限に待機するために  **無限**  を使用します。  
  
 `ppObject`  
 \[出力\] 新しく作成されたオブジェクトを表す **IDebugObject を**  返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 クラスのインスタンスを表すパラメーターでありコンストラクターを必要とする他の複合型を呼び出してオブジェクトを作成するにはこのメソッドを示します。  
  
## 参照  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
---
title: "IJsDebugFrame::Evaluate メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::Evaluate メソッド
このスタック フレームのコンテキストで式を評価します。  
  
## 構文  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### パラメーター  
 `pExpressionText`  
 \[入力\] 評価する式。  
  
 `ppDebugProperty`  
 \[出力\] プロパティ ブラウザーを表すオブジェクト。  
  
 `pError`  
 \[出力\] エラーが発生した場合のエラーメッセージ。  
  
## 戻り値  
  
## 解説  
 次のメッセージを返します。"S\_OK: Evaluation succeeds, \*ppDebugProperty contains evaluation result."   "S\_FALSE: Evaluation throws an error \(or the evaluation operation is not supported\), \*pError contains the error message."  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)
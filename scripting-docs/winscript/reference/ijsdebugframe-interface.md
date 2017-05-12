---
title: "IJsDebugFrame インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugFrame インターフェイス
スタック フレームを表します。  
  
## 構文  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## メンバー  
  
### パブリック メソッド  
  
|名前|説明|  
|--------|--------|  
|[IJsDebugFrame::Evaluate メソッド](../../winscript/reference/ijsdebugframe-evaluate-method.md)|このスタック フレームのコンテキストで式を評価します。|  
|[IJsDebugFrame::GetDebugProperty メソッド](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|このスタック フレームのプロパティ ブラウザーを返します。|  
|[IJsDebugFrame::GetDocumentPositionWithId メソッド](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|ユーザー レベルのドキュメント内でのこのスタック フレームの現在の位置を返します。|  
|[IJsDebugFrame::GetDocumentPositionWithName メソッド](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|ユーザー レベルのドキュメント内でのこのスタック フレームの現在の位置を返します。|  
|[IJsDebugFrame::GetName メソッド](../../winscript/reference/ijsdebugframe-getname-method.md)|スタック フレームのユーザー フレンドリ名を取得します。|  
|[IJsDebugFrame::GetReturnAddress メソッド](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|フレームの "先頭" \(GetStackRange を参照\) でプッシュされるリターン アドレスを取得します。|  
|[IJsDebugFrame::GetStackRange メソッド](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|論理的な JavaScript スタック フレームの絶対アドレス範囲を返します。|  
  
## 必要条件  
 **ヘッダー:** jscript9diag.h  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)
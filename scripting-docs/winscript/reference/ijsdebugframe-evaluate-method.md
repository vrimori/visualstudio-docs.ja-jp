---
title: "Ijsdebugframe::evaluate メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38e826048e85456ca63e069de67701b1fc3e9f04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate メソッド
このスタック フレームのコンテキストで式を評価します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pExpressionText`  
 [入力] 評価する式。  
  
 `ppDebugProperty`  
 [出力] プロパティ ブラウザーを表すオブジェクト。  
  
 `pError`  
 [出力] エラーが発生した場合のエラーメッセージ。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>コメント  
 次のメッセージを返します。"S_OK: Evaluation succeeds, *ppDebugProperty contains evaluation result."  S_FALSE: Evaluation throws エラー (または評価操作はサポートされていません)、 \*pError にはエラー メッセージが含まれています。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)
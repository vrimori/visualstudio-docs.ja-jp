---
title: Ijsdebugframe::evaluate メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 574af7823add67a00fc8add922b5e352fa1b369c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091924"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate メソッド
このスタック フレームのコンテキストで式を評価します。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
  
## <a name="remarks"></a>Remarks  
 次が返されます。S_OK を返します。評価が成功すると、* ppDebugProperty には評価結果が含まれています。 S_FALSE を返します。評価がエラーをスローします (または、評価操作がサポートされていません)、 \*pError にはエラー メッセージが含まれています。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)
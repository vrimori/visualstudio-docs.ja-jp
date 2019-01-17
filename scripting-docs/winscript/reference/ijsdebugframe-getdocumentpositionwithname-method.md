---
title: Ijsdebugframe::getdocumentpositionwithname メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6333f9c52c3ab4e0cd01c34f5e5228721aa55b4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093835"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName メソッド
ユーザー レベルのドキュメント内でのこのスタック フレームの現在の位置を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pDocumentName`  
 [出力] 静的なスクリプト場合は、ドキュメントへの URL。 動的なスクリプトの場合は、スクリプトの種類を含む名前 (eval code、function code など) が返されます。  
  
 `pLine`  
 [出力] ドキュメント内の 1 から始まる行の位置。  
  
 `pColumn`  
 [出力] ドキュメント内の 1 から始まる行の位置。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)
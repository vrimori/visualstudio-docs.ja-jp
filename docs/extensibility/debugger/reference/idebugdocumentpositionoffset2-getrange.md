---
title: IDebugDocumentPositionOffset2::GetRange |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e9e09ac0106e8c7a3c643592bb180af8a21c244
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925943"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
現在のドキュメントの位置の範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwBegOffset`  
 [入力、出力]範囲の開始位置をオフセットします。 この情報が必要でない場合は、このパラメーターを null 値に設定します。  
  
 `pdwEndOffset`  
 [入力、出力]範囲の終了位置をオフセットします。 この情報が必要でない場合は、このパラメーターを null 値に設定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ブレークポイントの場所のドキュメントの位置で指定された範囲は、コードを実際に貢献するステートメントを前方に検索するデバッグ エンジン (DE) によって使用されます。 次に例を示します。  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 5 行目でコードをデバッグ中のプログラムは使用されません。 5 行目で、ブレークポイントを設定します。 デバッガーは、DE、一定量のコードを提供する最初の行を前方に検索する必要がある場合、デバッガーはブレークポイントを正しく配置可能性があります、その他の候補行が含まれている範囲を指定します。 DE、し、前方に検索を通じてこれらの行ブレークポイントを受け入れることができる行が見つかるまで。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
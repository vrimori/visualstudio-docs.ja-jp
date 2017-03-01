---
title: "IDebugDocumentPositionOffset2::GetRange |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d14c212a3cb4499996ba6cf4d73d0b2fca73f7bc
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
現在のドキュメントの位置の範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```c#  
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
 成功した場合、返す`S_OK`。 そうしないと、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ブレークポイントの位置のドキュメントの位置で指定された範囲は、実際にコードを提供するステートメントを前方に検索するデバッグ エンジン (DE) によって使用されます。 次に例を示します。  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 5 行目でコードをデバッグするプログラムは使用されません。 5 行目で、ブレークポイントを設定、デバッガーでは、DE、一定量のコードを提供する最初の行を前方に検索する必要がある場合、デバッガーは、ブレークポイントを正しく配置があるその他の候補行を含む範囲を指定します。 デはしを前方に検索それらの行からブレークポイントを受け入れることができる行が見つかるまでです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

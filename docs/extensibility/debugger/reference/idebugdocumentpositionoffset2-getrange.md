---
title: IDebugDocumentPositionOffset2::GetRange |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60d7ee73be7ccd421c7f5e0b4861e9cd935fbdb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
 [入力、出力].範囲の開始位置をオフセットします。 この情報は必要ない場合は、このパラメーターを null 値に設定します。  
  
 `pdwEndOffset`  
 [入力、出力].範囲の終了位置をオフセットします。 この情報は必要ない場合は、このパラメーターを null 値に設定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ブレークポイントの位置のドキュメントの位置で指定された範囲は、コードを実際に寄与するステートメントを前方に検索するデバッグ エンジン (DE) によって使用されます。 次に例を示します。  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 5 行目でコードをデバッグするプログラムは使用されません。 5 行目で、ブレークポイントを設定、デバッガーでは、DE、一定量のコードを達成する最初の行を前方に検索する必要がある場合、デバッガーはブレークポイントが正しく配置追加候補行を含む範囲を指定します。 デしで検索してしまいます前方それらの行からブレークポイントを受け入れることができる行が見つかるまでです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
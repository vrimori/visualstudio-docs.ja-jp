---
title: IDebugDocumentPosition2::GetRange |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4a80bebba1000c73af2d7e2cfd05e67fa44b1b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
このドキュメントの位置の範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pBegPosition`  
 [入力、出力].A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)開始位置が入力構造です。 この情報は必要ない場合は、この引数を null 値を設定します。  
  
 `pEndPosition`  
 [入力、出力].A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)終了位置が入力構造です。 この情報は必要ない場合は、この引数を null 値を設定します。  
  
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
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
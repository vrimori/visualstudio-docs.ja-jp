---
title: IDebugDocumentContext2::GetSourceRange |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73600b81c71a1337470a1975902c40292ab4dcef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540273"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugDocumentContext2::GetSourceRange](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange)します。  
  
このドキュメントのコンテキストのソース コードの範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pBegPosition`  
 [入力、出力]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)構造体の開始位置が入力されます。 この情報が必要でない場合は、この引数を null 値を設定します。  
  
 `pEndPosition`  
 [入力、出力]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)構造体の終了位置が入力されます。 この情報が必要でない場合は、この引数を null 値を設定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ソース範囲は、コードの原因である前のステートメントの直後に現在のステートメントのバックアップからのソース コードの全体の範囲です。 ソース範囲は、逆アセンブル ウィンドウでコードのコメントを含むソース ステートメントを混在させる場合の通常使用されます。  
  
 このドキュメントのコンテキスト内に含まれるコード ステートメントだけの範囲を取得する、 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)


---
title: "IApplicationDebuggerUI::BringDocumentContextToTop |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fab017ab286957cf2c4be35832b1db877b339bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
デバッガーのユーザー インターフェイスでは、最上位に指定されたドキュメントのコンテキストを含むウィンドウを表示し、コンテキストにウィンドウをスクロールします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pddc`  
 [in]デバッガー ユーザー インターフェイスで最上位に表示するドキュメントのコンテキスト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_INVALIDARG`|指定されるコンテキスト`pddc`既知ではありません。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、デバッガーのユーザー インターフェイスでは、最上位に指定されたドキュメントのコンテキストを含むウィンドウを表示し、コンテキストにウィンドウをスクロールします。  
  
## <a name="see-also"></a>関連項目  
 [IApplicationDebuggerUI インターフェイス](../../winscript/reference/iapplicationdebuggerui-interface.md)
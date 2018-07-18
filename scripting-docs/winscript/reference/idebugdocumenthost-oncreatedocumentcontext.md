---
title: IDebugDocumentHost::OnCreateDocumentContext |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55598a4191d421d3aea01d27cc7991b70bd6a019
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726722"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
新しいドキュメントのコンテキストが作成されると、必要に応じて、新しいコンテキストの不明な制御を戻すをホストできるように、ホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppunkOuter`  
 [out]新しいコンテキストを制御するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|ホストでは、コントロール オブジェクトは提供されません。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、新しい機能をヘルパーに用意されているドキュメントのコンテキストに追加するホストを許可します。 このメソッドが返す可能性があります**E_NOTIMPL**または null 外部オブジェクトで、呼び出し元の場合は、コンテキストの作成を担当します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHost インターフェイス](../../winscript/reference/idebugdocumenthost-interface.md)
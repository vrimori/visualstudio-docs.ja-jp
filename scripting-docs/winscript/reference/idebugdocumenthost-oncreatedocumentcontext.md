---
title: Idebugdocumenthost::oncreatedocumentcontext |Microsoft Docs
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
ms.openlocfilehash: c0f8ce73e05fa8dd163564184361254fd58163ee
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096338"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
新しいドキュメント コンテキストを作成中で、ホストで必要に応じて、新しいコンテキストの不明な制御を返すことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppunkOuter`  
 [out]新しいコンテキストを制御するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|ホストでは、コントロール オブジェクトは提供されません。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、新しい機能をヘルパーで提供されるドキュメントのコンテキストに追加するホストを使用します。 このメソッドが返す可能性があります**E_NOTIMPL**または null 外部オブジェクトを呼び出し元の場合は、コンテキストを作成する責任を負います。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHost インターフェイス](../../winscript/reference/idebugdocumenthost-interface.md)
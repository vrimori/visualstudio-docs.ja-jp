---
title: IProcessDebugManager::CreateDebugDocumentHelper |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateDebugDocumentHelper
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b57f941017a0eef7892d43be9ed0414645e55e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728862"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
このアプリケーションの新しいデバッグ ドキュメント ヘルパーを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `punkOuter`  
 [in]返されたオブジェクトは、集計される場合、`punkOuter`インターフェイス ポインターを制御するのには、`IUnknown`です。 それ以外の場合、null ポインターであります。  
  
 `pddh`  
 [out]このアプリケーションのデバッグ ドキュメント ヘルパー オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、このアプリケーションの新しいデバッグ ドキュメント ヘルパーを作成します。  
  
## <a name="see-also"></a>関連項目  
 [IProcessDebugManager インターフェイス](../../winscript/reference/iprocessdebugmanager-interface.md)
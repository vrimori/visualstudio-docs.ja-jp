---
title: IActiveScriptSiteDebug32::GetApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: c71e33445db7745f71e374c586d079a9665776b2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087904"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
このスクリプトのサイトに関連付けられたデバッグ アプリケーション オブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppda`  
 [out]スクリプト サイトに関連付けられたデバッグ アプリケーション オブジェクトへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|ホストでは、デバッグを直接はサポートはありません。|  
  
## <a name="remarks"></a>Remarks  
 `GetApplication`メソッドは、各スクリプトが所属するアプリケーション オブジェクトを定義するスマート ホスト方法を提供します。 含むアプリケーションを取得しには、このメソッドを呼び出すスクリプト エンジンを試みる必要がある`IProcessDebugManager::GetDefaultApplication`これが失敗した場合。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteDebug32 インターフェイス](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)
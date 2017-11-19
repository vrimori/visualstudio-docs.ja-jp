---
title: "GetAutoInsertExtensions メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d222f7b6751381ceb4ebdb27bb6a6bf223616df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions メソッド
  デバッグ中に自動的に挿入するのには、Office 用のアプリに関する情報を取得します。  
  
 このメソッドは将来使用するために予約されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*psaExtensionNames*|Office 用アプリの拡張機能名。|  
  
## <a name="return-value"></a>戻り値  
 メソッドが正常に完了したかどうかを示す HRESULT 値。  
  
## <a name="remarks"></a>コメント  
 各 Office 向けアプリを挿入するのには、Office アプリケーションの拡張機能名 HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer の下で値に対応するとして返されます。 ホストは、レジストリでこれらの値を検索し、拡張機能を自動的に挿入する必要があります。  
  
  
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a53148b0130dd05f3ffc3360a518f9b2b66002e7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
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
  
  
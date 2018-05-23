---
title: GetAutoInsertExtensions メソッド
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f8573576b40afabb5ec568a0c471e7b1d79560ba
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions メソッド
  デバッグ中に自動的に挿入するのには、Office 用のアプリに関する情報を取得します。  
  
 このメソッドは将来使用するために予約されています。  
  
## <a name="syntax"></a>構文  
  
```c  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*psaExtensionNames*|Office 用アプリの拡張機能名。|  
  
## <a name="return-value"></a>戻り値  
 メソッドが正常に完了したかどうかを示す HRESULT 値。  
  
## <a name="remarks"></a>コメント  
 各 Office 向けアプリを挿入するのには、Office アプリケーションの拡張機能名の下で値に対応するとして返されます**HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**です。 ホストは、レジストリでこれらの値を検索し、拡張機能を自動的に挿入する必要があります。  
  
  
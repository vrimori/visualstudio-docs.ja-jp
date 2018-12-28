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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a12adf6e83e58b877e36dd65d98b617cda3a39b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647211"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions メソッド
  デバッグ中に自動的に挿入される Office 用アプリに関する情報を取得します。  
  
 このメソッドは将来使用するために予約されています。  
  
## <a name="syntax"></a>構文  
  
```csharp
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
  
## <a name="remarks"></a>Remarks  
 挿入する Office の各アプリは下の値に対応する Office アプリケーションの拡張機能名として返されます**HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**します。 ホストは、レジストリでこれらの値を検索し、拡張機能を自動的に挿入する必要があります。  
  
  
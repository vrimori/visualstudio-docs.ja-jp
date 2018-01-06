---
title: "GetValidCompatibleFramework 関数 |Microsoft ドキュメント"
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
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ee5a2ae08df4649d5e551973539321164d4a8e59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework 関数
  この API は、Office インフラストラクチャをサポートしてをコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|使用しないでください。|  
|*pbstrValidFrameworkTag*|使用しないでください。|  
  
## <a name="return-value"></a>戻り値  
 関数が成功したかどうか、それを返します**S_OK**です。 関数が失敗した場合、エラー コードを返します。  
  
  
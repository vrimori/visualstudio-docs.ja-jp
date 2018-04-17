---
title: EnsureVSTOComponent 関数 |Microsoft ドキュメント
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
ms.openlocfilehash: 5561d3c046c083c1495b858d36f6c867050ed842
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent 関数
  この API は、Office インフラストラクチャをサポートしてをコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*pProject*|使用しないでください。|  
  
## <a name="return-value"></a>戻り値  
 関数が成功したかどうか、それを返します**S_OK**です。 関数が失敗した場合、エラー コードを返します。  
  
  
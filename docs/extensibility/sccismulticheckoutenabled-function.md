---
title: SccIsMultiCheckoutEnabled 関数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 883f67482881b40c9d685604e1ee30fa33d4048b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013510"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 関数
この関数は、ソース管理プラグインのファイルに複数のチェック アウトできるかどうかを確認します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 pbMultiCheckout  
 [out]このプロジェクト (0 以外の場合は複数のチェック アウトがサポートされている) 複数のチェック アウトが有効になっているかどうかを指定します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|チェックは成功しました。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 2 つのチェックかどうかファイル チェック アウトできる同時に 1 つ以上のユーザーを決定するようになります。 最初に、ソース管理システムでは、複数のチェック アウトをサポートする必要があります。 ソース管理プラグインは、初期化中にこの機能を指定することによって指定できます、`SCC_CAP_MULTICHECKOUT`します。 その後、2 番目のチェック、IDE は、現在のプロジェクトが複数のチェック アウトをサポートしているかどうかを判断するには、この関数を呼び出します。 成功した場合、プラグインを返しますがコードし、設定の選択されたプロジェクトは、複数のチェック アウトがサポートされている場合、`pbMultiCheckout`に 0 以外の場合 (`TRUE`) または`FALSE`します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)
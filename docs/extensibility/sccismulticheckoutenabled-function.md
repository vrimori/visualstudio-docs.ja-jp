---
title: SccIsMultiCheckoutEnabled 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af7102a049cd3db072506cbf492799908196df32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled 関数
この関数は、ソース管理プラグインがファイルに複数のチェック アウトを許可するかどうかを確認します。  
  
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
 [out]このプロジェクト (複数のチェック アウトがサポートされている 0 以外の場合) の複数のチェック アウトが有効にするかどうかを指定します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|チェックが正常に完了しました。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 2 つのチェックかどうかファイルがチェック アウトに同時に 1 つ以上のユーザーを決定するようになります。 最初に、ソース管理システムでは、複数のチェック アウトをサポートする必要があります。 ソース管理プラグインは、初期化中にこの機能を指定して指定できます、`SCC_CAP_MULTICHECKOUT`です。 その後、2 番目のチェック、IDE では、現在のプロジェクトが複数のチェック アウトをサポートしているかどうかを判断するには、この関数を呼び出します。 複数のチェック アウトは、選択したプロジェクトのサポートは、プラグインが返されます成功コード、その設定`pbMultiCheckout`に 0 以外 (`TRUE`) または`FALSE`です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)
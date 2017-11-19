---
title: "SccEndBatch 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccEndBatch
helpviewer_keywords: SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e45d3ea8fefad30875ee91775412e7dcf40cb28e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccendbatch-function"></a>SccEndBatch 関数
この関数は、ソース管理操作のバッチを終了します。 これらのバッチは、入れ子にできません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|操作のバッチは正常に終了します。|  
|SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 ソース コントロールのバッチは、複数のプロジェクトまたは複数のコンテキスト全体にわたって、同じソース管理操作を実行に使用されます。 バッチ操作中に、ユーザー エクスペリエンスから冗長なダイアログ ボックスを回避するのには、バッチを使用できます。 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)と`SccEndBatch`関数は、先頭と操作の終了を示すために、ペアとして使用されます。 入れ子にできません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
---
title: SccEndBatch 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ca4e829f4535018c456011654058b6c0ae5dea3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246697"
---
# <a name="sccendbatch-function"></a>SccEndBatch 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ソース管理操作のバッチを終了します。 これらのバッチは、入れ子にできません。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|操作のバッチを正常に終了しました。|  
|SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 ソース コントロールのバッチを使用して、複数のプロジェクトまたは複数のコンテキスト全体で同じソース管理操作を実行できます。 バッチを使用して、バッチ操作中に、ユーザー エクスペリエンスから冗長ダイアログ ボックスを解消できます。 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)と`SccEndBatch`を先頭と末尾の操作を示すために、ペアとして関数が使用されます。 入れ子にできません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)


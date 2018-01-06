---
title: "SccBeginBatch 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccBeginBatch
helpviewer_keywords: SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d6415953a350321cb13f2705fa2bb182c278faa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch 関数
この関数は、ソース管理操作のバッチ シーケンスを開始します。 [SccEndBatch](../extensibility/sccendbatch-function.md)バッチを終了するのには、呼び出されます。 これらのバッチは、入れ子にできません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|操作のバッチは正常に開始しました。|  
|SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 ソース コントロールのバッチを使用して、複数のプロジェクトまたは複数のコンテキストで同じ操作を実行できます。 バッチ操作中に、ユーザー エクスペリエンスから冗長なプロジェクトごとのダイアログ ボックスを回避するのには、バッチを使用できます。 `SccBeginBatch`関数および[SccEndBatch](../extensibility/sccendbatch-function.md)の先頭と末尾の操作を示すために関数のペアとして使用されます。 入れ子にできません。 `SccBeginBatch`バッチ操作が進行中であることを示すフラグを設定します。  
  
 バッチ操作の実行中に、ソース管理プラグインをユーザーに最大で質問については、1 つのダイアログ ボックスを表示し、すべての後続の演算でこのダイアログ ボックスからの応答を適用します。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
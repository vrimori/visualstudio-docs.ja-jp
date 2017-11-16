---
title: "CvReleaseProvider 関数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvReleaseProvider
helpviewer_keywords: CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a6adcdd1be3b14ec4dbb9462ebddd82d9835e4e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider 関数
マーカー プロバイダーをリリースします。 マーカー プロバイダーをリリースしても、このプロバイダーの以前に作成したマーカー系列には影響がありません。 マーカー系列は、CvReleaseMarkerSeries を呼び出すことで個別にリリースする必要があります。 プロバイダーのリリースに失敗すると、メモリ漏れが発生します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProvider`  
 プロバイダー コンテキスト。 Null は指定できません。  
  
## <a name="return-value"></a>戻り値  
 プロバイダーがリリースされると S_OK を、エラーが発生した場合はエラー コードを返します。 SUCCEEDED/FAILED マクロを使用し、エラーの状態を確認します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** cvmarkers.h  
  
## <a name="see-also"></a>関連項目  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
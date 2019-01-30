---
title: CvReleaseProvider 関数 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb47eb0bb63ca7d617e98d372f691ab4d28fec4a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969250"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider 関数
マーカー プロバイダーをリリースします。 マーカー プロバイダーをリリースしても、このプロバイダーの以前に作成したマーカー系列には影響がありません。 マーカー系列は、CvReleaseMarkerSeries を呼び出すことで個別にリリースする必要があります。 プロバイダーのリリースに失敗すると、メモリ漏れが発生します。  
  
## <a name="syntax"></a>構文  
  
```C  
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
 **ヘッダー:** *cvmarkers.h*  
  
## <a name="see-also"></a>関連項目  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
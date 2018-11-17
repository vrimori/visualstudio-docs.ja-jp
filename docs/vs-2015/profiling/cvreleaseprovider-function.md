---
title: CvReleaseProvider 関数 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c59e5516129d5712983a228f68e4e91301656c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738811"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkers.h  
  
## <a name="see-also"></a>関連項目  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)




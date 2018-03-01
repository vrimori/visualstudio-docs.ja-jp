---
title: "CvInitProvider 関数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 15abebb58382674bc7943d7949dfddbc62524c91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cvinitprovider-function"></a>CvInitProvider 関数
マーカー プロバイダーを初期化します。 他の同時実行ビジュアライザー SDK 関数の前に呼び出す必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pGuid`  
 プロバイダ GUID。 Nll は指定できません。  
  
 `ppProvider`  
 プロバイダー コンテキストを格納する出力変数のアドレス。 Nll は指定できません。  
  
## <a name="return-value"></a>戻り値  
 プロバイダーが初期化されると S_OK を、エラーが発生した場合はエラー コードを返します。 SUCCEEDED/FAILED マクロを使用し、エラーの状態を確認します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkers.h  
  
## <a name="see-also"></a>参照  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
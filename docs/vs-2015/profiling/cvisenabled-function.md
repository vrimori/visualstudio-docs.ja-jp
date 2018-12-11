---
title: CvIsEnabled 関数 | Microsoft Docs
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
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91a8a0a27456299a914b2919aaf169fa72edf540
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723892"
---
# <a name="cvisenabled-function"></a>CvIsEnabled 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

セッションにより ETW プロバイダーが有効になっているか判断します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `category`  
 カテゴリ。  
  
 `level`  
 重要度レベル。  
  
 `pProvider`  
 有効なプロバイダー オブジェクト。 Nll は指定できません。  
  
## <a name="return-value"></a>戻り値  
 プロバイダーが現在有効になっている場合は S_OK を返します。 プロバイダーが現在無効になっている場合は S_FALSE を返します。 エラーが発生した場合はエラー コードを返します。 FAILED マクロを使用し、エラーの状態を確認し、それから S_OK/S_FALSE を確認します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkers.h  
  
## <a name="see-also"></a>関連項目  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)




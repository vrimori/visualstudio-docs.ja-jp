---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider 関数 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4910a66481be1f00a0fd57e1a66c0756f11c6589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538392"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CvCreateDefaultMarkerSeriesOfDefaultProvider 関数](https://docs.microsoft.com/visualstudio/profiling/cvcreatedefaultmarkerseriesofdefaultprovider-function)します。  
  
既定のプロバイダーの既定のマーカー系列を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppProvider`  
 プロバイダー オブジェクト変数のアドレス。 アドレスには NULL を指定できません。変数には値を含めることができます。  
  
 `ppMarkerSeries`  
 マーカー系列オブジェクト変数のアドレス。 アドレスには NULL を指定できません。変数には値を含めることができます。  
  
## <a name="return-value"></a>戻り値  
 プロバイダーとマーカー系列の両方が作成されると S_OK を、エラーが発生した場合はエラー コードを返します。 SUCCEEDED/FAILED マクロを使用し、エラーの状態を確認します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** cvmarkers.h  
  
## <a name="see-also"></a>関連項目  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)




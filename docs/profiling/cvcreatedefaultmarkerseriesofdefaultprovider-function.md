---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider 関数 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6198cfc874eb8a547b77bfabe8b3fb3473fa92ef
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2018
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider 関数
既定のプロバイダーの既定のマーカー系列を作成します。  
  
## <a name="syntax"></a>構文  
  
```C  
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
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkers.h  
  
## <a name="see-also"></a>参照  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
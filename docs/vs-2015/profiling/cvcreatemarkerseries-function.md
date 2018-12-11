---
title: CvCreateMarkerSeries 関数 | Microsoft Docs
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
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52ef56d1e33ddb66a4c35f7c46596ea080478a6c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734714"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定されたプロバイダーに対してマーカー系列を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProvider`  
 CvInitProvider により以前に初期化されたプロバイダー オブジェクト。 Nll は指定できません。  
  
 `pSeriesName`  
 マーカー系列名。 NULL は指定できませんが、空の文字列は指定できます。  
  
 `ppMarkerSeries`  
 マーカー系列コンテキストを格納する出力変数のアドレス。 Nll は指定できません。  
  
## <a name="return-value"></a>戻り値  
 マーカー系列が作成されると S_OK を、エラーが発生した場合はエラー コードを返します。 SUCCEEDED/FAILED マクロを使用し、エラーの状態を確認します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## <a name="see-also"></a>関連項目  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)




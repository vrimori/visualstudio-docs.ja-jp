---
title: "CvCreateDefaultMarkerSeriesOfDefaultProvider 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider"
helpviewer_keywords: 
  - "CvCreateDefaultMarkerSeriesOfDefaultProvider メソッド"
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateDefaultMarkerSeriesOfDefaultProvider 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

既定のマーカーの一連の既定のプロバイダーを作成します。  
  
## 構文  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### パラメーター  
 `ppProvider`  
 プロバイダー オブジェクト変数のアドレス。  アドレスは変数の値を持つことができますが、空白にすることはできません。  
  
 `ppMarkerSeries`  
 マーカーのシリーズ オブジェクト変数のアドレス。  アドレスは変数の値を持つことができますが、空白にすることはできません。  
  
## 戻り値  
 エラーが発生したプロバイダーおよびマーカー シリーズの両方が正常に作成された場合はエラー コードの場合は S\_OK を返します。  エラー条件をチェックするために SUCCEEDED\/FAILED マクロを使用します。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
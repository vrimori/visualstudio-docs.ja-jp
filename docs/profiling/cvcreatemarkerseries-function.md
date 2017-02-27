---
title: "CvCreateMarkerSeries 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateMarkerSeriesA"
  - "cvmarkers/CvCreateMarkerSeriesW"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesA メソッド"
  - "CvCreateMarkerSeriesW メソッド"
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvCreateMarkerSeries 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

特定のプロバイダーのマーカーのシリーズを作成します。  
  
## 構文  
  
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
  
#### パラメーター  
 `pProvider`  
 前に CvInitProvider で初期化されるプロバイダー オブジェクト。  NULL にすることはできません。  
  
 `pSeriesName`  
 マーカーのファミリ名。  null にすることはできませんが、空の文字列は許可されます。  
  
 `ppMarkerSeries`  
 マーカーのシリーズのコンテキストを格納する出力変数のアドレス。  NULL にすることはできません。  
  
## 戻り値  
 エラーが発生したマーカーのシリーズが正常に作成された場合はエラー コードの場合は S\_OK を返します。  エラー条件をチェックするために SUCCEEDED\/FAILED マクロを使用します。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
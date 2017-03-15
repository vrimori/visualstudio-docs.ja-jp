---
title: "CvCreateMarkerSeriesWithCodePageA 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmakers/CvCreateMarkerSeriesWithCodePageA"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesWithCodePageA メソッド"
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvCreateMarkerSeriesWithCodePageA 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

特定のプロバイダーのマーカーのシリーズを作成し、コード ページをしない。  この関数がマーカー API ANSI 関数によって書き出されるテキストのコード ページを明示的に指定することもできます。  コード ページを設定すると、トレースに別のロケールとは言語によって異なるコンピューターでキャプチャし、分析すると便利です。  既定では GetACP\(\) 関数から返されたコード ページとして使用されます。  
  
## 構文  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### パラメーター  
 `pProvider`  
 前に CvInitProvider で初期化されるプロバイダー オブジェクト。  NULL にすることはできません。  
  
 `pSeriesName`  
 マーカーのファミリ名。  null にすることはできませんが、空の文字列は許可されます。  
  
 `nTextCodePage`  
 有効なコード ページ。  
  
 `ppMarkerSeries`  
 マーカーのシリーズのコンテキストを格納する出力変数のアドレス。  NULL にすることはできません。  
  
## 戻り値  
 エラーが発生したマーカーのシリーズが正常に作成された場合はエラー コードの場合は S\_OK を返します。  エラー条件をチェックするために SUCCEEDED\/FAILED マクロを使用します。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
---
title: "CvReleaseMarkerSeries 関数 | Microsoft Docs"
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
  - "cvmarkers/CvReleaseMarkerSeries"
helpviewer_keywords: 
  - "CvReleaseMarkerSeries メソッド"
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvReleaseMarkerSeries 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マーカーのシリーズを解放します。  クラッシュする可能性があるアプリケーションを別の方法で解放された後にオブジェクトがマーカーのシリーズを使用しないでください。  マーカーのシリーズを解放する場合に、メモリ リークが発生します。  
  
## 構文  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### パラメーター  
 `pMarkerSeries`  
 プロバイダー オブジェクト変数のアドレス。  アドレスは変数の値を持つことができますが、空白にすることはできません。  
  
## 戻り値  
 エラーが発生したマーカーのシリーズが正常に解放またはエラー コードの場合は S\_OK を返します。  エラー条件をチェックするために SUCCEEDED\/FAILED マクロを使用します。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
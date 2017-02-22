---
title: "CvReleaseProvider 関数 | Microsoft Docs"
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
  - "cvmarkers/CvReleaseProvider"
helpviewer_keywords: 
  - "CvReleaseProvider メソッド"
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvReleaseProvider 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マーカーのプロバイダーを解放します。  マーカーのプロバイダーを解放すると、前に作成したマーカーの一連のこのプロバイダーには影響しません。  マーカーのシリーズの呼び出しは CvReleaseMarkerSeries してリリースである必要があります。  プロバイダーの原因を解放できないメモリ リーク。  
  
## 構文  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### パラメーター  
 `pProvider`  
 プロバイダーのコンテキスト。  NULL にすることはできません。  
  
## 戻り値  
 エラーが発生したプロバイダーが正常に解放またはエラー コードの場合は S\_OK を返します。  エラー条件をチェックするために SUCCEEDED\/FAILED マクロを使用します。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
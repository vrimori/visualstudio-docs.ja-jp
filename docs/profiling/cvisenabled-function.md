---
title: "CvIsEnabled 関数 | Microsoft Docs"
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
  - "cvmarkers/CvIsEnabledEx"
  - "cvmarkers/CvIsEnabled"
helpviewer_keywords: 
  - "CvIsEnabled メソッド"
  - "CvIsEnabledEx メソッド"
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvIsEnabled 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

すべてのセッションで指定の ETW プロバイダーを有効にするかどうかを判定します。  
  
## 構文  
  
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
  
#### パラメーター  
 `category`  
 カテゴリ。  
  
 `level`  
 重要度レベル。  
  
 `pProvider`  
 有効なプロバイダー オブジェクト。  NULL にすることはできません。  
  
## 戻り値  
 プロバイダーが現在有効になっている場合は S\_OK を返します。  プロバイダーが現在無効になれば S\_FALSE。  エラーがある場合はエラー コード。  エラー条件をチェックし、S\_OK\/S\_FALSE をチェックするために FAILED マクロを使用してください。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
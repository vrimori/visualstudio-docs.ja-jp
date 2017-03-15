---
title: "CvInitProvider 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvInitProvider"
helpviewer_keywords: 
  - "CvInitProvider メソッド"
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvInitProvider 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マーカーのプロバイダーを初期化します。  他の同時実行ビジュアライザー SDK 関数の前に呼び出す必要があります。  
  
## 構文  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### パラメーター  
 `pGuid`  
 プロバイダーの GUID。  NULL にすることはできません。  
  
 `ppProvider`  
 プロバイダーのコンテキストを格納する出力変数のアドレス。  NULL にすることはできません。  
  
## 戻り値  
 エラーが発生したプロバイダーが正常に初期化されるまたはエラー コードの場合は S\_OK を返します。  エラー条件をチェックするために SUCCEEDED\/FAILED マクロを使用します。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
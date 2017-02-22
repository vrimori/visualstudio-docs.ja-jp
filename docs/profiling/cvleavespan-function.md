---
title: "CvLeaveSpan 関数 | Microsoft Docs"
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
  - "cvmarkers/CvLeaveSpan"
helpviewer_keywords: 
  - "CvLeaveSpan メソッド"
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvLeaveSpan 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

範囲の末尾をマークします。  
  
## 構文  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### パラメーター  
 `pSpan`  
 前の呼び出しによって返される CvEnterSpan\* への範囲オブジェクト。  NULL にすることはできません。  
  
## 戻り値  
 メッセージが正常に作成された場合は、S\_OK を返します。  エラーがある場合はエラー コード。  エラー条件をチェックするために SUCCEEDED\/FAILED マクロを使用します。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
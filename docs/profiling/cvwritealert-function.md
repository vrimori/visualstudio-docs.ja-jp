---
title: "CvWriteAlert 関数 | Microsoft Docs"
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
  - "cvmarkers/CvWriteAlertVA"
  - "cvmarkers/CvWriteAlertVW"
  - "cvmarkers/CvWriteAlertA"
  - "cvmarkers/CvWriteAlertW"
helpviewer_keywords: 
  - "CvWriteAlertVW メソッド"
  - "CvWriteAlertA メソッド"
  - "CvWriteAlertVA メソッド"
  - "CvWriteAlertW メソッド"
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvWriteAlert 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーのトレース ファイルに警告を書き込みます。  
  
## 構文  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### パラメーター  
 `argList`  
 引数のリスト。  
  
 `pMarkerSeries`  
 有効なマーカーのシリーズのコンテキスト。  NULL にすることはできません。  
  
 `pMessage`  
 メッセージ形式の文字列。  NULL にすることはできません。  
  
## 戻り値  
 メッセージが正常に作成された場合は、S\_OK を返します。  エラーがある場合はエラー コード。  エラー条件をチェックするために SUCCEEDED\/FAILED マクロを使用します。  
  
## 必要条件  
 **ヘッダー:** cvmarkers.h  
  
 **Unicode:** CvWriteAlertW、CvWriteAlertVW  
  
 **ANSI:** CvWriteAlertA、CvWriteAlertVA  
  
## 参照  
 [C\+\+ ライブラリ リファレンス](../profiling/cpp-library-reference.md)
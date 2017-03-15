---
title: "CvWriteMessage 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteMessageW"
  - "cvmarkers/CvWriteMessageExW"
  - "cvmarkers/CvWriteMessageVA"
  - "cvmarkers/CvWriteMessageExVW"
  - "cvmarkers/CvWriteMessageExA"
  - "cvmarkers/CvWriteMessageA"
  - "cvmarkers/CvWriteMessageExVA"
  - "cvmarkers/CvWriteMessageVW"
helpviewer_keywords: 
  - "CvWriteMessageExVA メソッド"
  - "CvWriteMessageW メソッド"
  - "CvWriteMessageVW メソッド"
  - "CvWriteMessageExVW メソッド"
  - "CvWriteMessageExW メソッド"
  - "CvWriteMessageA メソッド"
  - "CvWriteMessageVA メソッド"
  - "CvWriteMessageExA メソッド"
ms.assetid: e20ae7be-bfa7-437a-b8c1-fa0f1baa7f83
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# <a name="cvwritemessage-function"></a>CvWriteMessage 関数
同時実行ビジュアライザーのトレース ファイルにメッセージを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CvWriteMessageW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageA(  
    PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteMessageExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteMessageExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `argList`  
 引数リスト。  
  
 `category`  
 スパンのカテゴリ  
  
 `level`  
 スパンの重要度レベル。  
  
 `pMarkerSeries`  
 有効なマーカー シリーズ コンテキスト。 Nll は指定できません。  
  
 `pMessage`  
 メッセージの書式設定文字列。 Nll は指定できません。  
  
## <a name="return-value"></a>戻り値  
 メッセージが書き込まれると S_OK を返します。 エラーが発生した場合はエラー コードを返します。 SUCCEEDED/FAILED マクロを使用し、エラーの状態を確認します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** cvmarkers.h  
  
 **Unicode:** CvWriteMessageW、CvWriteMessageVW、CvWriteMessageExW、CvWriteMessageExVW  
  
 **ANSI:** CvWriteMessageA、CvWriteMessageVA、CvWriteMessageExA、CvWriteMessageExVA  
  
## <a name="see-also"></a>関連項目  
 [C++ ライブラリ リファレンス](../profiling/cpp-library-reference.md)


<!--HONumber=Feb17_HO4-->



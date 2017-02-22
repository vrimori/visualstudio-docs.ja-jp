---
title: "marker_series::write_flag メソッド | Microsoft Docs"
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
  - "cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_flag メソッド"
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::write_flag メソッド
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

同時実行ビジュアライザーのトレース ファイルにフラグを書き込みます。  
  
## 構文  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### パラメーター  
 `_Format`  
 引数リスト オブジェクトに対応する、ゼロ以上の書式指定項目がテキストが混在した複合書式指定文字列。  
  
 `_Importance`  
 重要度レベル。  
  
 `_Category`  
 カテゴリ。  
  
## 必要条件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency::diagnostic  
  
## 参照  
 [marker\_series クラス](../profiling/marker-series-class.md)
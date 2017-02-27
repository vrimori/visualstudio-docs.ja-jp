---
title: "marker_series クラス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series クラス"
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series クラス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

単一のプロバイダーによって生成されるイベントのシリアル チャネルを表します。  
  
## 構文  
  
```  
class marker_series;  
```  
  
## メンバー  
  
### パブリック コンストラクター  
  
|名前|説明|  
|--------|--------|  
|[marker\_series::marker\_series コンストラクター](../Topic/marker_series::marker_series%20Constructor.md)|`marker_series` クラスの新しいインスタンスを初期化します。|  
|[marker\_series::~marker\_series デストラクター](../profiling/marker-series-tilde-marker-series-destructor.md)|破棄の marker\_series はすべて、割り当てられているリソースを解放します。|  
  
### パブリック メソッド  
  
|名前|説明|  
|--------|--------|  
|[marker\_series::is\_enabled メソッド](../Topic/marker_series::is_enabled%20Method.md)|すべてのセッションでプロバイダーを有効にするかどうかを判定します。|  
|[marker\_series::write\_alert メソッド](../profiling/marker-series-write-alert-method.md)|同時実行ビジュアライザーのトレース ファイルに警告を書き込みます。|  
|[marker\_series::write\_flag メソッド](../profiling/marker-series-write-flag-method.md)|同時実行ビジュアライザーのトレース ファイルにフラグを書き込みます。|  
|[marker\_series::write\_message メソッド](../profiling/marker-series-write-message-method.md)|同時実行ビジュアライザーのトレース ファイルにメッセージを書き込みます。|  
  
## 継承階層  
 `marker_series`  
  
## 必要条件  
 **ヘッダー:** cvmarkersobj.h  
  
 **名前空間:** Concurrency::diagnostic  
  
## 参照  
 [diagnostic 名前空間](../profiling/diagnostic-namespace.md)
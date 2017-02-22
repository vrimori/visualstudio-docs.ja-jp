---
title: "QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**QueryCounters** オプションは、コンピューターで使用できる CPU \(ハードウェア\) パフォーマンス カウンターを一覧表示します。  
  
 **QueryCounters** は、コマンド ラインで指定する唯一のオプションである必要があります。  
  
## 構文  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### パラメーター  
 なし。  
  
## 解説  
 インストルメンテーション メソッドを使用している場合、プロファイラーは各データ コレクション イベントで 1 つ以上の CPU パフォーマンス カウンターの値を収集できます。  サンプリング プロファイル方法を使用している場合、1 つのカウンター イベントとサンプリング間隔として使用されるイベント出現回数を指定できます。  
  
 プロセッサごとに異なる CPU パフォーマンス カウンターが公開されます。  プロファイラーは、ほとんどのプロセッサで使用できる一連のジェネリック カウンターを定義します。  **QueryCounters** オプションは、汎用カウンター名とプロセッサに固有のカウンター名の両方を一覧表示します。  
  
## 参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)
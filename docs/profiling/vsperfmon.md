---
title: "VSPerfMon | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPerfMon ツール"
  - "コマンド ライン、ツール"
  - "コマンド ライン ツール、VSPerfMon ツール"
  - "データ [Visual Studio ALM]、VSPerfMon ツール"
  - "パフォーマンス データ、VSPerfMon ツール"
  - "パフォーマンス ツール、VSPerfMon ツール"
  - "プロファイリング ツール、VSPerfCmd"
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# VSPerfMon
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfMon ツールを使用すると、アプリケーションのパフォーマンス データを収集できます。通常、このツールは VSPerfCmd.exe によって起動されます。  VSPerfMon を使用した場合は、VSPerfCmd ツールでは入手できない、プロセスのアタッチやデタッチなどの追加情報を表示できます。  この情報を表示するには、VSPerfMon を別のウィンドウで起動します。  VSPerfMon を起動するには、次の構文を使用します。  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 VSPerfMon ツールのオプションの説明を次の表に示します。  
  
|オプション|説明|  
|-----------|--------|  
|**U**|リダイレクトされたコンソール出力は Unicode として書き込まれます。これは、最初に指定する必要があります。|  
|**OUTPUT:** `<` *file name* `>`|指定した名前のファイルに出力をリダイレクトします。|  
|**TRACE**|パフォーマンス モニターを起動してインストルメントされたプロファイリングを実行します。|  
|**SAMPLE**|パフォーマンス モニターを起動してサンプリング プロファイリングを実行します。|  
|**COVERAGE**|パフォーマンス モニターを起動してコード カバレッジ コレクションを実行します。|  
|**CONCURRENCY**|リソース競合プロファイルでのパフォーマンス モニターを起動します。|  
|**USER:** `[` *domain* `\]` *username*|指定したアカウントからパフォーマンス モニターへのクライアント アクセスを許可します。|  
|**CROSSSESSION**|セッション間プロファイリングを有効にします。|  
|**COUNTER** `:cfg`|インストルメンテーション \(TRACE\) プロファイリング方式を使用するときに、各インストルメンテーション ポイントで収集する CPU カウンターを指定します。  複数の COUNTER オプションを指定すると、複数のカウンター データを収集できます。<br /><br /> \(*cfg*\) オブジェクトのデータを指定するには、次の構文を使用します。:<br /><br /> CounterName\[**,**Reload\[,FriendlyName\]\]<br /><br /> -   CounterName は、VSPerfCmd \/QueryCounters コマンドによって返されるカウンターの名前です。<br />-   Reload は、カウンター イベントのサンプリング間隔です。  インストルメンテーション メソッドを *Reload* を使用しないでください。<br />-   指定すると、プロファイリング ツールのレポートの列名が CounterName から FriendlyName に置き換えられます。|  
|**WINCOUNTER** `:path`|マーク データと共に含まれる Windows パフォーマンス カウンターを指定します。  `path` は、PDH カウンター パス形式の Windows パフォーマンス カウンター文字列です。  たとえば、次のようになります。<br /><br /> \\Processor\(0\)\\% Processor Time<br /><br /> \\System\\Context Switches\/sec|  
|**AUTOMARK** `:n`|\/WINCOUNTER を使用する際の自動的なマーク間の時間間隔をミリ秒単位で指定します。  値は、500ms 単位に切り上げられます。<br /><br /> 0 を使用すると、自動的なマークは無効になります。\(指定しない場合、既定の 500 ミリ秒になります\)|  
  
## 参照  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [プロファイル ツールのレポート ビュー](../profiling/performance-report-views.md)
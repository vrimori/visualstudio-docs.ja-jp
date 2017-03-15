---
title: "方法 : プロファイリングの開始と終了 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.wizard.summarypage"
helpviewer_keywords: 
  - "プロファイリング ツール、セッションの起動"
  - "パフォーマンス セッション、起動"
  - "パフォーマンス セッション、終了"
  - "プロファイリング ツール、セッションの終了"
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# 方法 : プロファイリングの開始と終了
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロファイリングを開始する前に、プロファイリング対象のバイナリをパフォーマンス セッションに追加する必要があります。  対象を追加するには、**パフォーマンス エクスプローラー**で **\[ターゲット\]** を右クリックし、**\[ターゲット バイナリの追加\]** をクリックします。  **\[ターゲット バイナリの追加\]** ダイアログ ボックスで、ファイル名を選択して **\[開く\]** をクリックします。  新しいバイナリが追加されます。  
  
### プロファイリングを開始するには  
  
1.  **\[パフォーマンス エクスプローラー\]** ウィンドウでパフォーマンス セッションの名前を右クリックし、次のいずれかのオプションをクリックします。  
  
    -   **\[プロファイルを使用して起動\]** \- アプリケーションを開始し、プロファイリングを即座に開始します。  
  
    -   **\[プロファイルを一時停止して起動\]** \- アプリケーションを開始しますが、プロファイリングは開始しません。  プロファイリングを開始するには、**\[データ収集コントロール\]** ウィンドウで **\[収集の再開\]** を選択します。  詳細については、「[方法 : プロファイリングを一時停止および再開する](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)」を参照してください。  
  
### プロファイリングを終了するには  
  
-   プロファイリング セッションを終了する最良の方法は、アプリケーションを終了することです。  プロファイリングを即座に終了するには、**パフォーマンス エクスプローラー**のツール バーで、**\[停止\]** をクリックします。  
  
## 参照  
 [データ収集の制御](../profiling/controlling-data-collection.md)   
 [方法 : プロファイリングを一時停止および再開する](../Topic/How%20to:%20Pause%20and%20Resume%20Performance%20Data%20Collection.md)
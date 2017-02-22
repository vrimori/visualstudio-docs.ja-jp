---
title: "方法 : 開始するバイナリを指定する | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.itemlaunch"
helpviewer_keywords: 
  - "プロファイリング ツール、起動"
  - "パフォーマンス ツール、起動"
  - "パフォーマンス セッション、起動"
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : 開始するバイナリを指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DLL などのバイナリをプロファイリングするには、**\[\<ターゲット\> プロパティ ページ\]** ダイアログ ボックスに情報を入力する必要があります。  この情報は、DLL プロジェクトの呼び出し元アプリケーションの場所を示します。  
  
 **要件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### 開始する実行可能ファイルを指定するには  
  
1.  **パフォーマンス エクスプローラー**で、対象のバイナリを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[プロパティ ページ\]** ダイアログ ボックスで **\[起動\]** のプロパティをクリックします。  
  
3.  **\[プロジェクト設定のオーバーライド\]** チェック ボックスをオンにします。  
  
4.  **\[起動する実行可能ファイル\]** テキスト ボックスにファイルの場所を指定します。  
  
5.  **\[引数\]** ボックスに、アプリケーションの開始に必要な引数を指定します。  
  
6.  **\[作業ディレクトリ\]** テキスト ボックスに、ディレクトリの場所を指定します。  
  
7.  \[OK\] をクリックします。  
  
## 参照  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)
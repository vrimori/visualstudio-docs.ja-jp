---
title: "方法 : ビルド出力ディレクトリを変更する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "出力ディレクトリ, 変更"
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : ビルド出力ディレクトリを変更する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロジェクトによって生成された \(デバッグ、リリース、またはその両方の\) 構成ごとに出力の場所を指定できます。  
  
> [!NOTE]
>  **セットアップ** プロジェクトがある場合は、この記事の最後にあるメモを参照してください。  
  
## ビルド出力ディレクトリの変更  
  
#### ビルド出力ディレクトリを変更するには  
  
1.  メニュー バーで、**\[プロジェクト\]**、\[*Appname* **のプロパティ\]** の順に選択します。**ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、**\[プロパティ\]** をクリックすることもできます。  
  
2.  Visual Basic プロジェクトの場合は、**\[コンパイル\]** タブを選択します。 Visual C\# プロジェクトの場合は、**\[ビルド\]** タブを選択します。 C\+\+ プロジェクトまたは JavaScript プロジェクトの場合は、**\[全般\]** タブを選択します。  
  
3.  上部にある構成のドロップダウンで、出力ファイルの場所を変更する構成を選択します \(デバッグ、リリース、またはすべて\)。  
  
     出力パスのエントリを検索します \(Visual Basic の場合は **\[ビルド出力パス\]**、Visual C\+\+ の場合は **\[出力ディレクトリ\]**、JavaScript と C\# の場合は **\[出力パス\]**\)。 プロジェクト ディレクトリを基準として相対的に新しいビルド出力ディレクトリを指定します。  
  
> [!NOTE]
>  セットアップ プロジェクトの **\[出力ファイル名\]** ボックスは、プロジェクト ファイルの場所ではなく、Setup.exe ファイルの場所のみを変更します。 詳細については、「**配置プロジェクトの \[プロパティ ページ\] ダイアログ ボックス \(\[構成プロパティ\] \- \[ビルド\]\)**」を参照してください。  
  
## 参照  
 [\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)   
 [\[全般\] プロパティ ページ \(プロジェクト\)](../Topic/General%20Property%20Page%20\(Project\).md)   
 [Visual Studio でのアプリケーションのビルド](../ide/compiling-and-building-in-visual-studio.md)
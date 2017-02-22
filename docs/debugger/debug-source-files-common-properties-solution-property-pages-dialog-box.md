---
title: "[デバッグ ソース ファイル] ([ソリューション プロパティ ページ] ダイアログ ボックス - [共通プロパティ]) | Microsoft Docs"
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
  - "vs.debug.options.FindSource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[デバッグ ソース ファイル] プロパティ ページ"
  - "デバッグ [Visual Studio]、ソース ファイルとシンボル ファイルの指定"
  - "ソース ファイル、デバッガーでの指定"
  - "デバッガー、ソース ファイル"
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# [デバッグ ソース ファイル] ([ソリューション プロパティ ページ] ダイアログ ボックス - [共通プロパティ])
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このプロパティ ページでは、ソリューションのデバッグ時にデバッガーによってソース ファイルが検索される場所を指定します。  
  
 **\[デバッグ ソース ファイル\]** プロパティ ページを開くには、**ソリューション エクスプローラー**でソリューションを右クリックし、ショートカット メニューの **\[プロパティ\]** をクリックします。  **\[共通プロパティ\]** フォルダーを展開し、**\[デバッグ ソース ファイル\]** ページをクリックします。  
  
 **\[ソース コードを含んでいるディレクトリ\]**  
 ソリューションのデバッグ時に、デバッガーによってソース ファイルが検索されるディレクトリの一覧が表示されます。  指定されたディレクトリのサブディレクトリも検索されます。  
  
 **\[以下のソース ファイルを探さない\]**  
 デバッガーによる読み取りから除外するファイルの名前を入力できます。  デバッガーは、上で指定したディレクトリのいずれかでこれらのファイルを見つけた場合、それを無視します。  デバッグ中に **\[ソース ファイルの検索\]** ダイアログ ボックスが表示されたときに **\[キャンセル\]** をクリックすると、検索中のファイルがこの一覧に追加され、そのファイルの検索が中止されます。  
  
## 参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)
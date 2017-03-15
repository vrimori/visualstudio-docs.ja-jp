---
title: "使用できるソースはありません | Microsoft Docs"
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
  - "vs.debug.nosource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[現在の場所のソース コードを表示できません] ダイアログ ボックス"
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用できるソースはありません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示しようとしているコードのソース コードがプロジェクトに含まれていません。  原因として、**\[呼び出し履歴\] ウィンドウ**または **\[スレッド\] ウィンドウ**で、ソース コードのないモジュールをダブルクリックしたことが考えられます。  デバッグは継続できますが、ソース ウィンドウを使ってブレークポイントを設定したり、この場所で他のアクションを実行したりすることはできません。  ブレークポイントを設定する必要があるときは、代わりに **\[逆アセンブリ\] ウィンドウ**を使用します。  
  
 \[ソリューション \<ソリューション名\> プロパティ ページ\] で、デバッガーがソース ファイルを検索するディレクトリを変更したり、選択されたソース ファイルをデバッガーが無視したりするように設定できます。  「[\[デバッグ ソース ファイル\] \(\[ソリューション プロパティ ページ\] ダイアログ ボックス \- \[共通プロパティ\]\)](../Topic/Debug%20Source%20Files,%20Common%20Properties,%20Solution%20Property%20Pages%20Dialog%20Box.md)」を参照してください。  
  
 **\[参照してソースを検索\]**  
 このリンクをクリックすると、参照してソース コードを検索できるダイアログ ボックスが開きます。  
  
 **\[逆アセンブルの表示\]**  
 **\[逆アセンブル\] ウィンドウ**を起動します。  
  
 **\[見つからないソース ファイルには常に逆アセンブルを表示する\]**  
 このオプションをオンにすると、利用できるソースがない場合に **\[逆アセンブル\] ウィンドウ**が自動的に表示されます。  この設定は、**\[オプション\]** ダイアログ ボックス、**\[デバッグ\]** カテゴリ、**\[全般\]** ページで、**\[ソースがない場合は逆アセンブルの表示\]** をオンまたはオフにすることによっても変更できます。  
  
## 参照  
 [\[デバッグ ソース ファイル\] \(\[ソリューション プロパティ ページ\] ダイアログ ボックス \- \[共通プロパティ\]\)](../Topic/Debug%20Source%20Files,%20Common%20Properties,%20Solution%20Property%20Pages%20Dialog%20Box.md)   
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll \(SOS デバッガー拡張\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md)
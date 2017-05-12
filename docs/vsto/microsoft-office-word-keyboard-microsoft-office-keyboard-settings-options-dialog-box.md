---
title: "[Microsoft Office Word Keyboard] ([オプション] ダイアログ ボックス - [Microsoft Office Keyboard 設定]) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard"
  - "VST.WordOptions.KeyboardMappingScheme"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "キーボード ショートカット、Visual Studio での Office 開発"
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# [Microsoft Office Word Keyboard] ([オプション] ダイアログ ボックス - [Microsoft Office Keyboard 設定])
  Microsoft Office Word と Visual Studio のどちらにも、ショートカット キーの機能があります。  同じショートカット キーが、Word と Visual Studio でそれぞれ別々のコマンドを表していることがあります。  Visual Studio のドキュメント レベルのプロジェクト内で Word を開いているときは、一度に 1 つのアプリケーションだけがショートカット キー コマンドを受け取ります。  既定では Visual Studio がすべてのショートカット キー コマンドを受け取りますが、**\[ダイナミック キーボード スキーム\]** を選択すると、文書にフォーカスがある場合は Word にショートカット キー コマンドを受け取らせることができます。  
  
 使用したショートカット キーが、現在ショートカット キーを処理しているアプリケーションのコマンドに割り当てられていない場合、そのショートカット キーはもう 1 つのアプリケーションに渡されます。  
  
 選択したオプションは、変更するまでは Word プロジェクト内で有効です。  この選択は、Microsoft Office Excel プロジェクトには影響を与えません。Excel の設定を変更するには、Microsoft Office Excel Keyboard のオプションを使用します。  
  
## UIElement の一覧  
 **Visual Studio キーボード スキーム**  
 Word 文書にフォーカスがある場合でも、Visual Studio がすべてのショートカット キー コマンドを受け取ります。  たとえば、文書にフォーカスがあるときに F5 キーを押した場合は、Visual Studio がソリューションのデバッグを開始します。  
  
 **ダイナミック キーボード スキーム**  
 Visual Studio にフォーカスがあるときに限り、Visual Studio がショートカット キー コマンドを受け取ります。  Word 文書にフォーカスがある場合は、Word がすべてのショートカット キー コマンドを受け取ります。  たとえば、Word 文書にフォーカスがあるときに F5 キーを押した場合は、Word の **\[検索と置換\]** ダイアログ ボックスが **\[ジャンプ\]** タブを選択した状態で表示されます。  Visual Studio にフォーカスがあるときに F5 を押した場合は、Visual Studio がソリューションのデバッグを開始します。  
  
## 参照  
 [&#91;Microsoft Office Excel Keyboard&#93; &#40;&#91;オプション&#93; ダイアログ ボックス - &#91;Microsoft Office Keyboard 設定&#93;&#41;](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  
---
title: "[Microsoft Office Excel Keyboard] ([オプション] ダイアログ ボックス - [Microsoft Office Keyboard 設定]) | Microsoft Docs"
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
  - "VST.ExcelOptions.KeyboardMappingScheme"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "キーボード ショートカット、Visual Studio での Office 開発"
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# [Microsoft Office Excel Keyboard] ([オプション] ダイアログ ボックス - [Microsoft Office Keyboard 設定])
  Microsoft Office Excel と Visual Studio のどちらにも、ショートカット キーの機能があります。  同じショートカット キーが、Excel と Visual Studio でそれぞれ別々のコマンドを表していることがあります。  Visual Studio のドキュメント レベルのプロジェクト内で Excel を開いているときは、一度に 1 つのアプリケーションだけがショートカット キー コマンドを受け取ります。  既定では Visual Studio がすべてのショートカット キー コマンドを受け取りますが、**\[ダイナミック キーボード スキーム\]** を選択すると、ドキュメントにフォーカスがある場合は Excel にショートカット キー コマンドを受け取らせることができます。  
  
 使用したショートカット キーが、現在ショートカット キーを処理しているアプリケーションのコマンドに割り当てられていない場合、そのショートカット キーはもう 1 つのアプリケーションに渡されます。  
  
 選択したオプションは、変更するまで Excel プロジェクト内で有効です。  この選択は、Microsoft Office Word プロジェクトには影響を与えません。Word の設定は、Microsoft Office Word Keyboard のオプションで変更します。  
  
## UIElement の一覧  
 **Visual Studio キーボード スキーム**  
 Excel にフォーカスがある場合でも、Visual Studio がすべてのショートカット キー コマンドを受け取ります。  たとえば、Excel にフォーカスがあるときに F5 キーを押した場合は、Visual Studio がソリューションのデバッグを開始します。  
  
 **ダイナミック キーボード スキーム**  
 Visual Studio にフォーカスがあるときに限り、Visual Studio がショートカット キー コマンドを受け取ります。  Excel にフォーカスがある場合は、Excel がすべてのショートカット キー コマンドを受け取ります。  たとえば、Excel にフォーカスがあるときに F5 キーを押した場合は、Excel が **\[ジャンプ\]** ダイアログ ボックスを表示します。  Visual Studio にフォーカスがあるときに F5 を押した場合は、Visual Studio がソリューションのデバッグを開始します。  
  
## 参照  
 [&#91;Microsoft Office Word Keyboard&#93; &#40;&#91;オプション&#93; ダイアログ ボックス - &#91;Microsoft Office Keyboard 設定&#93;&#41;](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  
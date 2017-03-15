---
title: "[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト]) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VBDefaults"
helpviewer_keywords: 
  - "Option Explicit ステートメント、IDE での設定"
  - "Option Compare ステートメント、IDE での設定"
  - "Option Strict ステートメント、IDE での設定"
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# [Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Basic プロジェクトのオプションに対する既定の設定を指定します。  新しいプロジェクトを作成すると、指定したオプション ステートメントがコード エディターのプロジェクト ヘッダーに追加されます。  このオプションは、すべての Visual Basic プロジェクトに適用されます。  
  
 このダイアログ ボックスを表示するには、**\[ツール\]** メニューの **\[オプション\]** をクリックし、**\[プロジェクトおよびソリューション\]** フォルダーを展開して、**\[Visual Basic の既定値\]** をクリックします。  
  
 **Option Explicit**  
 明示的な変数の宣言が必要となるように、コンパイラの既定値を設定します。  既定では、**\[Option Explicit\]** には **\[On\]** が設定されています。  詳細については、「[\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)」を参照してください。  
  
 **Option Strict**  
 明示的な縮小変換が必要となるように、コンパイラの既定値を設定します。  既定では、**\[Option Strict\]** には **\[Off\]** が設定されています。  詳細については、「[\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)」を参照してください。  
  
 **Option Compare**  
 文字列比較でのコンパイラの既定を設定します。\[binary\] \(大文字と小文字を区別する\) または \[text\] \(大文字と小文字を区別しない\) を設定できます。 既定では、**\[Option Compare\]** には **\[Binary\]** が設定されています。  詳細については、「[\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)」を参照してください。  
  
 **\[Option Infer\]**  
 ローカル型の推論についてのコンパイラの既定値を設定します。  既定では、新しく作成されたプロジェクトの場合は **\[Option Infer\]** が **\[On\]** に設定され、以前のバージョンの Visual Basic で作成されて移行されたプロジェクトの場合は **\[Off\]** に設定されます。  詳細については、「[\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)」を参照してください。  
  
## 参照  
 [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)
---
title: "オプション ページを開く | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "オプション ページを開く"
  - "ツール オプション"
  - "オプション ページ"
ms.assetid: 6f24cbfa-288a-4a57-831b-bc82587de255
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# オプション ページを開く
プログラムを使用してオプション ページを表示し、パッケージのユーザーがセットアップ中に自分で構成するようにできます。 パッケージのインストール後に設定を変更するには、ユーザーは、**\[オプション\]** ダイアログ ボックスを使用してオプション ページにアクセスできます。  
  
### カスタム オプション ページを表示するには  
  
1.  オプション ページを作成します。 詳細については、「[\[オプション\] ページを作成します。](../Topic/Creating%20Options%20Pages.md)」を参照してください。  
  
2.  オプション ページを定義するクラスの名前に `typeof` キーワードを適用して、オプション ページの <xref:System.Type> を取得します。  
  
3.  パラメーターとしてオプション ページの <xref:System.Type> を使用して、<xref:Microsoft.VisualStudio.Shell.Package.ShowOptionPage%2A> メソッドを呼び出します。  
  
     次の例では、**HelloWorldOptions** という名前のオプション ページが表示されます。  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/CSharp/opening-an-options-page_1.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/VisualBasic/opening-an-options-page_1.vb)]  
  
### Visual Studio によって定義されているオプション ページを表示するには  
  
1.  レジストリ サブキー HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\ToolsOptionsPages\\ で、表示するオプション ページのノードを検索し、その GUID をコピーします。この GUID は Page キーの値です。  
  
2.  <xref:System.ComponentModel.Design.CommandID> インスタンスを作成し、そこに、パラメーターとして <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> 定数と <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> 定数を含めます。  
  
     これにより、**\[オプション\]** ダイアログ ボックスを指定します。  
  
3.  パラメーターとして <xref:System.ComponentModel.Design.CommandID> インスタンスと GUID ストリングを使用して、<xref:System.ComponentModel.Design.MenuCommandService.GlobalInvoke%2A> メソッドを呼び出します。  
  
     次の例では、**テキス エディター**のオプション ページの **\[全般\]** タブが表示されます。  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/CSharp/opening-an-options-page_2.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/VisualBasic/opening-an-options-page_2.vb)]
---
title: "How to: Add an Application Configuration File to a C# Project | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "app.config files, adding to C# projects"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Add an Application Configuration File to a C# Project
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

、C のプロジェクトにアプリケーション構成ファイル \(app.config ファイル\) を追加して、共通言語ランタイムがどのアセンブリ ファイルを見つけて読み込む方法をカスタマイズできます。  アプリケーション構成ファイルの詳細については、「[ランタイムがアセンブリを検索する方法](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md)」を参照してください。  
  
> [!NOTE]
>  Windows ストアは <xref:System.Configuration>をサポートしていません。  その結果、ストア apps は app.config テンプレートは含まれません。  
  
 プロジェクトをビルドすると、開発環境は自動的に app.config ファイルをコピーし、実行可能ファイルに合わせてコピーのファイル名を変更し、Bin ディレクトリにコピーを移動します。  
  
### C\# プロジェクトにアプリケーション構成ファイルを追加するには  
  
1.  メニュー バーで、**プロジェクト**、**\[新しい項目の追加\]** を選択します。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[インストール済み\]** を展開し、**\[Visual C\# アイテム\]** を展開し、を **\[アプリケーション構成ファイル\]** テンプレートを選択します。  
  
3.  **\[名前\]** のテキスト ボックスに名前を入力し、次に **\[追加\]** のボタンをクリックします。  
  
     app.config という名前のファイルがプロジェクトに追加されます。  
  
## 参照  
 [アプリケーションの設定の管理 \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [構成ファイル スキーマ](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [アプリの構成](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/ja-jp/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)
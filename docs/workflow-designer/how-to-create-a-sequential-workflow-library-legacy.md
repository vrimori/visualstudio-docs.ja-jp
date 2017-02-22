---
title: "方法: シーケンシャル ワークフロー ライブラリを作成する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "プロジェクト, シーケンシャル ワークフロー ライブラリ"
  - "シーケンシャル ワークフロー ライブラリ"
  - "シーケンシャル ワークフロー, ライブラリの作成"
  - "ワークフロー, シーケンシャル ワークフロー ライブラリ"
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 方法: シーケンシャル ワークフロー ライブラリを作成する (レガシ)
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] が備えている従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用してシーケンシャル ワークフロー ライブラリ プロジェクトを作成するには、次の手順を実行します。[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用します。  
  
### シーケンシャル ワークフロー ライブラリ プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
3.  **\[新しいプロジェクト\]** ウィンドウの上部にあるドロップダウン リストで **\[.NET Framework 3.0\]** オプションまたは **\[.NET Framework 3.5\]** オプションを選択し、従来のデザイナーにアクセスします。  
  
    > [!NOTE]
    >  [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] での既定のオプションは **\[.NET Framework 4\]** です。このオプションは、[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] を対象とする [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションを作成する場合に使用され、従来のデザイナーは使用しません。  
  
4.  **\[プロジェクトの種類\]** ウィンドウで、\[Visual C\#\] または \[Visual Basic\] \(**\[他の言語\]** を使用する場合\) を選択し、**\[ワークフロー\]** を選択します。  
  
5.  **\[テンプレート\]** ウィンドウで **\[シーケンシャル ワークフロー ライブラリ\]** をクリックします。  
  
6.  **\[プロジェクト名\]** ボックスに、プロジェクト名としてその内容を説明する分かりやすい名前を入力します。  
  
7.  **\[場所\]** ボックスにプロジェクトを保存するディレクトリを入力するか、**\[参照\]** をクリックしてディレクトリを選択します。  
  
     プロジェクト用にソリューション ディレクトリを作成する場合は、**\[ソリューション用のディレクトリを作成\]** チェック ボックスをオンにして、**\[ソリューション名\]** ボックスにディレクトリ名を入力します。  
  
8.  **\[OK\]** をクリックします。  
  
## 参照  
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Workflow Authoring Styles](http://msdn.microsoft.com/ja-jp/aacf4ec6-da05-4974-958a-974769dda739)
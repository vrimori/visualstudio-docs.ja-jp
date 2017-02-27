---
title: "方法: シーケンシャル ワークフロー コンソール アプリケーションを作成する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "コンソール アプリケーション, シーケンシャル ワークフロー"
  - "シーケンシャル ワークフロー, コンソール アプリケーション"
  - "ワークフロー, コンソール アプリケーション"
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 方法: シーケンシャル ワークフロー コンソール アプリケーションを作成する (レガシ)
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] が備えている従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用してシーケンシャル ワークフロー コンソール アプリケーション プロジェクトを作成するには、次の手順を実行します。[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用します。  
  
### シーケンシャル ワークフロー コンソール アプリケーションを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
3.  **\[新しいプロジェクト\]** ウィンドウの上部にあるドロップダウン リストで **\[.NET Framework 3.0\]** オプションまたは **\[.NET Framework 3.5\]** オプションを選択し、従来のデザイナーにアクセスします。  
  
    > [!NOTE]
    >  [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] での既定のオプションは **\[.NET Framework 4\]** です。このオプションは、[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] を対象とする [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションを作成する場合に使用され、従来のデザイナーは使用しません。  
  
4.  **\[プロジェクトの種類\]** ウィンドウで、\[Visual C\# プロジェクトまたは Visual Basic プロジェクト \(**\[他の言語\]** を使用する場合\)\] を選択して、**\[ワークフロー\]** を選択します。  
  
5.  **\[テンプレート\]** ウィンドウで **\[シーケンシャル ワークフロー コンソール アプリケーション\]** をクリックします。  
  
6.  **\[プロジェクト名\]** ボックスに、プロジェクト名としてその内容を説明する分かりやすい名前を入力します。  
  
7.  **\[場所\]** ボックスにプロジェクトを保存するディレクトリを入力するか、**\[参照\]** をクリックしてディレクトリを選択します。  
  
     Windows フォーム デザイナが開き、作成済みプロジェクトの Form1 が表示されます。  
  
8.  **\[OK\]** をクリックします。  
  
     ワークフロー デザイナが開き、作成済みシーケンシャル ワークフローのワークフロー デザイン サーフェイスが表示されます。  
  
9. **\[ツールボックス\]** からデザイン サーフェイスの **\[Drop activity\]** 指定領域までアクティビティをドラッグします。  
  
## 参照  
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Developing Workflows](http://msdn.microsoft.com/ja-jp/557bcb1f-a7ab-49f6-8df7-2706b7001301)
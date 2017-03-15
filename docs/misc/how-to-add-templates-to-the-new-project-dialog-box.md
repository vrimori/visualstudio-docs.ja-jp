---
title: "方法: [新しいプロジェクト] ダイアログ ボックスにテンプレートを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ダイアログ ボックス、プロジェクトへのテンプレートの追加"
  - "プロジェクト [Visual Studio SDK]、ダイアログ ボックスへのテンプレートの追加"
  - "テンプレート [Visual Studio]、プロジェクト ダイアログ ボックスへの追加"
ms.assetid: fd044681-e666-410d-815c-33db923ed888
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# 方法: [新しいプロジェクト] ダイアログ ボックスにテンプレートを追加する
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] をインストールすると、多数の定義済みプロジェクト テンプレートがインストールされます。 定義済みプロジェクト テンプレートの一覧については、「[NIB テンプレートからのプロジェクトの作成](http://msdn.microsoft.com/ja-jp/7c36d86a-6b79-4480-8228-0f925f1204b2)」を参照してください。 既定のプロジェクト テンプレートに加えて、カスタムまたはサブタイプ固有のプロジェクト テンプレートを作成できます。 たとえば、**スマート デバイス** サブタイプは、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] および [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロジェクトに独自のテンプレートを提供します。 カスタム テンプレートを作成する方法の手順については、「[方法 : プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)」を参照してください。  
  
## \[新しいプロジェクト\] ダイアログ ボックスへのテンプレートの追加  
  
#### \[新しいプロジェクト\] ダイアログ ボックスにテンプレートを追加するには  
  
1.  MyTemplate.vstemplate ファイルを含むテンプレートを作成します。  
  
2.  テンプレート内のファイル \(.vstemplate ファイルを含む\) を選択して右クリックし、**\[送信\]** をクリックして、**\[圧縮 \(zip 形式\) フォルダー\]** をクリックします。 前に抽出したしたファイルは .zip ファイルに圧縮されます。  
  
 .Zip テンプレート ファイルを **%USERPROFILE%\\Documents\\Visual Studio 2015\\Templates\\ProjectTemplates** に配置します。  
  
## 参照  
 [Project Subtypes](d235b47b-cf11-4d47-a63f-e33d9d16105d2044a030-0795-4940-bd65-a6e44de98a0f)   
 [NIB: Visual Studio テンプレート](http://msdn.microsoft.com/ja-jp/141fccaa-d68f-4155-822b-27f35dd94041)   
 [原因となっている、新しい項目\] ダイアログ ボックスを追加](../Topic/Contributing%20to%20the%20Add%20New%20Item%20Dialog%20Box.md)
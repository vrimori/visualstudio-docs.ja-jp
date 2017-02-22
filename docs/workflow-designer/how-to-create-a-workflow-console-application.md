---
title: "ワークフロー コンソール アプリケーションを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ワークフロー コンソール アプリケーションを作成する方法
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] を利用して、無人または有人のプロセスの実行のためのワークフローを作成できます。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]は、このようなワークフローを作成するためのデザイン サーフェイスを備えています。[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内からワークフローを作成する場合に使用でき、デザイナーを再ホストする他のアプリケーションに統合することもできます。  
  
 このトピックでは、[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用して、コンソール アプリケーションのワークフローを作成する方法について説明します。  
  
### ワークフロー コンソール アプリケーションを作成するには  
  
1.  [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト…\]** をクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
3.  **\[インストールされているテンプレート\]** ペインで、プログラミング言語の設定に応じて、**\[Visual C\#\]** または **\[Visual Basic\]** のいずれかのグループから **\[ワークフロー\]** を選択します。  
  
4.  中央のペインで、**\[ワークフロー コンソール アプリケーション\]** を選択します。  
  
5.  **\[プロジェクト名\]** ボックスに、プロジェクト名としてその内容を説明するわかりやすい名前を入力します。  
  
6.  **\[場所\]** ボックスにプロジェクトを保存するディレクトリを入力するか、**\[参照\]** をクリックしてディレクトリを選択します。  
  
7.  **\[ソリューション\]** ボックスに、新しいソリューションの名前を入力します。**\[OK\]** をクリックすると、アプリケーションが作成されます。  
  
    > [!NOTE]
    >  ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合は、そのソリューションを [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] で開いて**ソリューション エクスプローラー**で右クリックし、**\[追加\]**、**\[新しいプロジェクト…\]** の順にクリックして **\[新しいプロジェクト\]** ダイアログ ボックスを開き、上記の手順を実行します。  
  
8.  プロジェクト テンプレートで XAML のワークフロー定義が作成され、コンソール アプリケーション定義がソース コードに記述されます。[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]で、作成したワークフロー用のキャンバスが開かれて表示されます。  
  
9. ワークフローを作成するには、アクティビティなどのワークフロー項目を**\[ツールボックス\]** からワークフロー内のデザイン サーフェイスにドラッグします。  
  
## 参照  
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)
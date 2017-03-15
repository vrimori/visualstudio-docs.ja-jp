---
title: "WCF ワークフロー サービス アプリケーションを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# WCF ワークフロー サービス アプリケーションを作成する方法
[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] ワークフロー サービス アプリケーションは、そのクライアントとの間でプロセスの境界を越えてメッセージを受け渡しする分散型の通信サービスです。サービス側でのサービス コントラクトの実装は、.NET Framework 3.5 の従来のワークフロー サービスと同様に、[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] のワークフロー アクティビティを介して宣言形式で行います。  
  
### WCF ワークフロー サービス アプリケーションを作成するには  
  
1.  [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト…\]** をクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
3.  **\[インストールされているテンプレート\]** ペインで、使用しているプログラミング言語に応じて、**\[Visual C\#\]** または **\[Visual Basic\]** のいずれかのグループから **\[WCF\]** または **\[ワークフロー\]** を選択します。  
  
4.  中央のペインで、**\[WCF ワークフロー サービス アプリケーション\]** を選択します。  
  
5.  **\[プロジェクト名\]** ボックスに、プロジェクト名としてその内容を説明する分かりやすい名前を入力します。  
  
6.  **\[場所\]** ボックスにプロジェクトを保存するディレクトリを入力するか、**\[参照\]** をクリックしてディレクトリを選択します。  
  
7.  **\[ソリューション\]** ボックスで、新しいソリューションを作成するように選択して **\[OK\]** をクリックします。  
  
    > [!NOTE]
    >  ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合は、そのソリューションを [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] で開いて**ソリューション エクスプローラー**で右クリックし、**\[追加\]**、**\[新しいプロジェクト…\]** の順にクリックして **\[新しいプロジェクト\]** ダイアログ ボックスを開き、上記の手順を実行します。  
  
8.  プロジェクト テンプレートによって、サービス定義が XAML として作成されます。[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]のデザイン ビューが開かれ、<xref:System.ServiceModel.Activities.Receive> と <xref:System.ServiceModel.Activities.SendReply> のアクティビティを含む <xref:System.Activities.Statements.Sequence> アクティビティが表示されます。  
  
## 参照  
 [アクティビティを作成する方法](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)
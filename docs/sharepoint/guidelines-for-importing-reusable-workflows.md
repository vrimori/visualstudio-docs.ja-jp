---
title: "再利用可能なワークフローをインポートするためのガイドライン"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "インポート (項目を) [Visual Studio での SharePoint 開発]"
  - "再利用可能なワークフロー [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, インポート (項目を)"
  - "Visual Studio での SharePoint 開発, 再利用可能なワークフロー"
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 再利用可能なワークフローをインポートするためのガイドライン
  SharePoint Designer で作成した再利用可能なワークフローをインポートするには [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]のインポート再利用可能な SharePoint 2010 ワークフロー プロジェクト テンプレートを使用します。  このテンプレートは、*宣言型**ワークフロー*をインポートし \([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] のみ\)、それを*コード ワークフロー*に変換します。コード ワークフローは、[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] のコードで拡張できます。  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 ただし、インポートの再利用可能な SharePoint 2010 ワークフロー テンプレートは、ファーム ソリューションのみインポートできます。  ワークフローをサンドボックス ソリューションとして配置する場合は、インポートを 2010 SharePoint ソリューション パッケージのインポート テンプレートします。  ただし、この方法では、コード ワークフローに変換できないため、次のように変更することはできません。  
  
## 再利用可能なワークフローのインポート テンプレートを使用した、再利用可能なワークフローのインポート  
 インポートの再利用可能な SharePoint 2010 ワークフロー テンプレートを使用して再利用可能なワークフローをインポートする場合は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 他の SharePoint ソリューションのようにソリューションを実行または変更している項目を手動で修正する必要がある場合があります。  
  
### タスク フォームのインポート  
 インポートの再利用可能な SharePoint 2010 ワークフロー プロジェクト テンプレートは、コード ワークフロー スキーマが 1 のタスク フォームのみを割り当てるため、すべての関連付けフォームと開始フォームをインポートしますが、1 番目のタスク フォームのみをインポートします。  元のワークフロー ソリューションに含まれる他のタスク フォームは、**ソリューション エクスプローラー**の **\[インポートされた他のファイル\]** フォルダーに格納されます。  
  
## 再利用可能なワークフローをインポート SharePoint を使用してインポートする 2010 のソリューション パッケージ テンプレート  
 2010 の SharePoint ソリューション パッケージのインポート テンプレートを使用して再利用可能なワークフローをインポートする場合は、以下の問題を考慮する必要があります:  
  
-   ワークフローをインポートした後で、F5 キーを選択して、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] に配置して実行できます。  ただし、インポートしたソリューションのワークフローに変更点があると、ワークフローを配置および実行する前にプロジェクトの要素を手動で修正する必要がある場合があります。  
  
-   ワークフローは宣言型なので、コードを追加することはできません。  ワークフローをコード ワークフローに変換するには、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] にインポートの再利用可能な SharePoint 2010 ワークフロー テンプレートでインポートする必要があります。  
  
-   ワークフロー デザイナー \(.xoml\) ファイルはデザイン ビューでも編集できますが、ワークフロー デザイナーで false エラーが表示されるので、ソース ビューで編集することをお勧めします。  
  
-   ワークフローでのデバッグは、宣言型コンテンツには使用できません。  [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] で設定したブレークポイントはヒットしません。  
  
## グローバルに再利用可能なワークフロー ソリューションのインポート  
 グローバルに再利用可能なワークフローをインポートする再利用可能な SharePoint 2010 ワークフロー テンプレートを使用してインポートすることはできません。  再利用可能なワークフローを全体的にインポートするには、非再利用可能なワークフローに変換するか、または 2010 の SharePoint ソリューション パッケージのインポート テンプレートを使用する必要があります。  
  
 ワークフローを変換するには、SharePoint Designer の再利用可能なワークフローのコピーを作成します \(ワークフローのショートカット メニューを開き、**\[コピーの保存\]** をクリックしますで表されます\)。  次 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]のインポートの再利用可能な SharePoint 2010 ワークフロー テンプレートで新しい再利用可能なワークフローをインポートします。  
  
 これを変更せずに再利用可能なワークフローを全体的にインポートするには、インポート SharePoint 2010 のソリューション パッケージのテンプレートを使用します。  このメソッドを使用すると、ワークフローは、コード ワークフローに変換されず、宣言型ワークフローのままになります。  
  
## 参照  
 [既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  
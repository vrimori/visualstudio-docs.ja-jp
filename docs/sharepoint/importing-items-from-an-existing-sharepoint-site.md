---
title: "既存の SharePoint サイトからのアイテムのインポート | Microsoft Docs"
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
  - "VS.SharePointTools.WSPImport.SelectionDependency"
  - "VS.SharepointTools.WSPImport.SpecifyProjectSource"
  - "VS.SharePointTools.WSPImport.SelectionItemsToImport"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "インポート (項目を) [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, インポート (.wsp ファイルを)"
  - "Visual Studio での SharePoint 開発, インポート (項目を)"
ms.assetid: b1012eb8-5927-4522-9475-72f0ba55fcca
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 既存の SharePoint サイトからのアイテムのインポート
  SharePoint ソリューション パッケージのインポート プロジェクト テンプレートによって、新しい [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ソリューションの既存の SharePoint サイトからコンテンツ タイプやフィールドなどの要素を再利用できます。 インポートしたソリューションのほとんどは変更せずに実行できますが、それらをインポートした後にいずれかの項目を変更する場合は特に、考慮すべき特定の制限事項および問題があります。  
  
> [!NOTE]  
>  再利用可能なワークフローをインポートするには、再利用可能なワークフローのインポート プロジェクト テンプレートを使用します。[!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [再利用可能なワークフローをインポートするためのガイドライン](../sharepoint/guidelines-for-importing-reusable-workflows.md)。  
  
## サポートされる SharePoint ソリューション  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] は、[!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] および [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]で作成したソリューションのインポートを完全にサポートします。  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] では、以下のアプリケーションで作成したソリューションのインポートはサポートされません。  
  
-   [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]  
  
-   [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]  
  
-   [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]  
  
-   Microsoft SharePoint Designer 2007  
  
-   [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]  
  
 これらのアプリケーションによって作成されたソリューションを正常にインポートできる場合もありますが、その機能はテストされておらず、サポートされていません。  
  
## アイテムのインポートに関する制限事項  
 ほとんどの SharePoint アイテムは既存の .wsp ファイルからインポートできますが、次のアイテムはサポートされておらず、変更を加えないと正常に機能しない場合があります。  
  
-   BDC エンティティ  
  
-   コード ワークフロー関連の要素  
  
-   コード ワークフロー  
  
-   視覚的 Web パーツ \(.ascx\)  
  
-   Web サービス \(.asmx\)  
  
-   コンテンツ タイプのバインディング  
  
-   イベント レシーバー  
  
-   リスト定義 \(テンプレート\)  
  
-   サイト定義  
  
 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] または [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] からソリューションをエクスポートすると、これらのアイテムは .wsp ファイルから自動的に除外されます。 ただし、サポートされていないツールによって生成された他の .wsp ファイルには、これらのアイテムが含まれることがあります。 \(このトピック前半の「サポートされる SharePoint ソリューション」をご覧ください。\)  
  
## ソリューションのインポート時に実行される動作  
 SharePoint ソリューション パッケージのインポート テンプレートでソリューションをインポートする場合、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は .wsp ファイルのすべての内容をコピーして調整しますが、インポートする要素とそのファイルの間の関連付けと参照を可能な限り調整し、維持しようとします。  
  
 インポートされるすべてのアイテムは、**ソリューション エクスプローラー**の対応するフォルダーにコピーされます。 たとえば、**\[コンテンツ タイプ\]** フォルダーの下にコンテンツ タイプが表示され、**\[リスト インスタンス\]** の下にリスト インスタンスが一覧表示されます。 インポートされたアイテムに関連付けられているファイルは、そのアイテムのフォルダーにコピーされます。 たとえば、インポートしたリスト インスタンスには、そのモジュール、フォーム、ASPX ページが含まれます。  
  
### 依存アイテム  
 \[SharePoint ソリューション パッケージのインポート\] ウィザードでアイテムを選んだものの、その依存アイテムを選んでいない場合は、インポートする前に依存アイテムも選ぶ必要があることがメッセージ ボックスで通知されます。  
  
### フィーチャーとは  
 SharePoint Designer のユーザーは、**ソリューション エクスプローラー**のインポートされたソリューションに、*フィーチャー*と呼ばれる予期せぬファイルが表示されているのに気付くことがあります。フィーチャーは SharePoint Designer ソリューションに存在していましたが、表示されていませんでした。 現在では [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] にフィーチャーが表示されるようになりました。  
  
 フィーチャーは、SharePoint アイテムのコンテナーになります。 各フィーチャーは、その中に含まれているコンテンツ タイプやリスト定義などの各アイテムへの参照を保持します。 ソリューションをインポートすると、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] はインポートされた要素のすべてのフィーチャーを設定して、ファイルのフィーチャーと要素との関係を維持しようと試みます。 参照を解決できないファイルがあれば、**\[その他のインポートされたファイル\]** フォルダーに配置されます。  
  
 フィーチャーについて詳しくは、「[Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)」および「[フィーチャーの使用](http://go.microsoft.com/fwlink/?LinkID=147704)」をご覧ください。  
  
### 特殊なケースの処理  
 Visual Studio はアイテムとその依存ファイルの調整ができない場合があります。[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] が解決できないファイルは **\[その他のインポートされたファイル\]** フォルダーに表示されます。 また、その **DeploymentType** プロパティは **NoDeployment** に設定されるので、それらのファイルがソリューションと一緒に配置されることはありません。  
  
 たとえば、リスト定義 ExpenseForms をインポートする場合、その名前を持つリスト定義は、**ソリューション エクスプローラー**の **\[リスト定義\]** フォルダーに、その Elements.xml ファイルと Schema.xml ファイルと一緒に表示されます。 しかし、関連付けられた ASPX と HTML フォームは、**\[その他のインポートされたファイル\]** フォルダーの下にある **\[ExpenseForms\]** と呼ばれるフォルダーに配置される可能性があります。 インポートを完了するには、**ソリューション エクスプローラー**で ExpenseForms リスト定義の下にあるそれらのファイルを移動し、各ファイルの **DeploymentType** プロパティを **NoDeployment** から **ElementFile** に変更します。  
  
 イベント レシーバーをインポートする場合、Elements.xml ファイルは適切な場所にコピーされますが、アセンブリを手動でソリューション パッケージに含めて、ソリューションと一緒に配置されるようにする必要があります。 その方法の[!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)]「[方法: アセンブリを追加および削除する](../sharepoint/how-to-add-and-remove-additional-assemblies.md)」をご覧ください。  
  
 ワークフローをインポートすると、InfoPath フォームが **\[その他のインポートされたファイル\]** フォルダーにコピーされます。 .wsp ファイルに Web テンプレートが含まれている場合、**ソリューション エクスプローラー**のスタートアップ ページとして設定されます。  
  
## フィールドとプロパティ バッグのインポート  
 複数のフィールドを持つソリューションをインポートするときには、すべての個別のフィールド定義が単一の Elements.xml ファイルにマージされ、**ソリューション エクスプローラー**内の **Fields** と呼ばれるノードの下に置かれます。 同様に、すべてのプロパティ バッグ エントリも、**PropertyBags** と呼ばれるノードの下にある Elements.xml ファイルにマージされます。  
  
 SharePoint 内のフィールドは、テキスト、ブール値、参照などの指定したデータ型の列です。 詳しくは、「[構成要素: 列とフィールド型](http://go.microsoft.com/fwlink/?LinkId=182304)」をご覧ください。 プロパティ バッグを使用することによって、SharePoint 内のオブジェクト \(ファームから SharePoint サイト上のリストまですべて\) にプロパティを追加できます。 プロパティ バッグは、プロパティの名前と値のハッシュ テーブルとして実装されます。 詳しくは、「[SharePoint 構成の管理](http://go.microsoft.com/fwlink/?LinkId=182296)」または「[SharePoint プロパティ バッグ設定](http://go.microsoft.com/fwlink/?LinkId=182297)」をご覧ください。  
  
## プロジェクト内のアイテムの削除  
 SharePoint ソリューションのほとんどのアイテムには、1 つ以上の依存アイテムがあります。 たとえば、リスト インスタンスはコンテンツ タイプに依存します。また、コンテンツ タイプは、フィールドに依存します。 SharePoint ソリューションをインポートした後でソリューション内のアイテムを削除し、その依存アイテムを削除しない場合、ソリューションの配置を試みるまで [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は参照の問題を通知しません。 たとえば、インポートされたソリューションに、コンテンツ タイプに依存するリスト インスタンスがある場合、そのコンテンツ タイプを削除すると、配置でエラーが発生する可能性があります。 依存アイテムが SharePoint サーバー上に存在しない場合に、エラーが発生します。 同様に、削除されるアイテムにプロパティ バッグもある場合、それらのプロパティ バッグのエントリを **PropertyBags** Elements.xml ファイルから削除します。 そのため、インポートされたソリューションから何らかのアイテムを削除すると配置エラーが発生する場合は、削除が必要な配置アイテムがないか確認します。  
  
## 失われたフィーチャー属性の復元  
 ソリューションをインポートするときに、オプションのいくつかのフィーチャー属性は、インポートされたフィーチャー マニフェストから除外されます。 これらの属性を新しいフィーチャー ファイルで復元する場合は、元のフィーチャー ファイルと新しいフィーチャー マニフェストを比較して失われた属性を識別し、トピック「[方法: SharePoint フィーチャーをカスタマイズする](../sharepoint/how-to-customize-a-sharepoint-feature.md)」の指示に従います。  
  
## 組み込みのリスト インスタンスで配置競合の検出は行われない  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、組み込みのリスト インスタンス \(つまり、SharePoint に付属している既定のリスト インスタンス\) に関する配置競合の検出は実行されません。 SharePoint 上の組み込みのリスト インスタンスを上書きしないために、競合の検出は実行されません。 組み込みのリスト インスタンスは配置されたり、更新されたりしますが、削除されたり、上書きされたりすることはありません。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [SharePoint のパッケージ化と配置のトラブルシューティング](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)。  
  
## SharePoint Server 2010 のワークフローのインポート  
 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] で作成したワークフローをインポートする場合、そのワークフローを配置した後は正常に実行されません。 特定のアセンブリが不足するため、また [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] のワークフローに [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のワークフロー ソリューションで現在サポートされていない InfoPath フォームが含まれるために、ワークフローは正しく実行されません。 ただし、インポートされた [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] のワークフローは、[!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] アセンブリへの参照を追加したり、InfoPath フォームを再接続したりすることによって一部のアイテムを修正した後、正常に機能させることができます。[!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][SharePoint Server 2010 のワークフローのインポート](http://go.microsoft.com/fwlink/?LinkId=182226)。  
  
## アイテム名の文字制限  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、プロジェクトおよびプロジェクト アイテムの名前 \(パスを含む\) に合計 260 文字の制限があります。 ソリューションをインポートするときに、アイテム名がこの制限を超えると、次のエラーが発生します。  
  
 **指定されたパスかファイル名、またはその両方が長すぎます。 完全修飾ファイル名は 260 文字未満で指定し、ディレクトリ名は 248 文字未満で指定してください。**  
  
 このエラーが発生すると、アイテムは作成されません。 この問題は、インポートしたモジュールで最も頻繁に発生します。 この問題を回避するには、次の操作を行います。  
  
-   **\[新しいプロジェクトの追加\]** ダイアログ ボックスにプロジェクト名を入力するときは、短い名前を使用します。  
  
-   パスを短くために、可能な限りルート フォルダーに近い場所にプロジェクトを作成します。  
  
## SharePointProductVersion 属性  
 [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] または [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] など SharePoint の以前のバージョンで作成されたソリューションをインポートする場合、パッケージ マニフェストの SharePointProductVersion 属性の値を 12.0 に変更するか、インポートされたすべての Web ページに Script Manager コントロールを挿入して SharePointProductVersion の設定を 14.0 のままにします。 それ以外の場合、インポートされた Web フォームは、SharePoint では表示されません。  
  
### 背景  
 [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] と [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] のソリューションには SharePointProductVersion という属性が含まれています。 SharePoint はパッケージ マニフェストのこの属性を使用して、そのソリューションが設計されている SharePoint のバージョンを判別します。 正しい値は 12.0 と 14.0 の 2 つです。 値 12.0 は、アイテムが [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] または [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] 向けに設計されていることを示します。値 14.0 は、アイテムが [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] または [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] 向けに設計されていることを示します。  
  
 ASPX ページのレンダリング時のセキュリティを強化するため、[!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] と [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] では、すべての ASPX ページまたはマスター ページに Script Manager コントロールを含める必要があります。 Script Manager について詳しくは、「[ScriptManager コントロールの概要](http://go.microsoft.com/fwlink/?LinkID=169399)」をご覧ください。[!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] と [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] には Script Manager コントロールがないため、[!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] または [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] にアップグレードされる [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] または [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] のページには Script Manager コントロールを追加する必要があります。 標準のマスター ページを使用する ASPX ページでは、標準のマスター ページに既に Script Manager コントロールが 1 つ追加されているため、Script Manager コントロールは必要ありません。 ただし、マスター ページを使用しない、またはカスタム マスター ページを使用する ASPX ページでは、[!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] または [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] で作業するために Script Manager コントロールを追加する必要があります。  
  
 新しいすべてのプロジェクトの SharePointProductVersion 属性は 14.0 に設定されるため、Script Manager コントロールがないと、[!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] または [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] のプロジェクトを [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] にインポートするときに問題が発生する可能性があります。 Web フォームが存在するアップグレードされたプロジェクトを Script Manager なしで配置する場合、フォームは SharePoint に表示されません。  
  
## 参照  
 [チュートリアル: 既存の SharePoint サイトからのアイテムのインポート](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)   
 [再利用可能なワークフローをインポートするためのガイドライン](../sharepoint/guidelines-for-importing-reusable-workflows.md)   
 [チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)   
 [方法: 既存の BDC モデル ファイルを SharePoint プロジェクトに追加する](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)  
  
  
---
title: "SharePoint ワークフロー ソリューションの作成"
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
  - "VSTO.NewSharePointWorkflowWizard.Page3"
  - "VS.SharePointTools.Workflow.WorkflowName"
  - "VSTO.NewSharePointWorkflowWizard.Page2"
  - "VSTO.NewSharePointWorkflowWizard.Page1"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, ワークフロー"
  - "ワークフロー [Visual Studio での SharePoint 開発]"
ms.assetid: fe79b99a-cb7c-4a14-8d9f-bce0c0805ba0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# SharePoint ワークフロー ソリューションの作成
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には、SharePoint Web サイト内のドキュメントおよびリスト項目のライフ サイクルを管理するカスタム ワークフローを作成するためのツールが用意されています。  指定された項目は、アクティビティ コントロール デザイナー、セット、必要なアセンブリ参照などが挙げられます。  また、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には、ワークフローの作成および構成を支援する **SharePoint カスタマイズ ウィザード**が備わっています。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint プロジェクトを作成するための必要条件の一覧については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  SharePoint の詳細については、参照します[Microsoft SharePoint 製品とテクノロジ](http://go.microsoft.com/fwlink/?LinkId=178470)。  
  
## SharePoint でのワークフロー  
 SharePoint のライブラリまたはリストにワークフローを追加すると、ライブラリまたはリスト上のすべての項目にビジネス プロセスを適用することになります。  ワークフローは、システムまたはユーザーが各項目に対して実行する必要のあるアクションを説明するものです。たとえば、編集して校閲を受けるために項目を送信するアクションなどがあります。  これらのアクションは、*アクティビティ*と呼ばれ、ワークフローのビルド ブロックとなります。  
  
 SharePoint のワークフローは [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成し、SharePoint Web サイトに配置することができます。  SharePoint に配置されたワークフローは、ライブラリまたはリストに関連付けることができます。  このワークフローは、プロセスで自動的に開始できるほか、ユーザーが手動で開始することもできます。  ワークフローの操作についての詳細については、参照 [プロセスを管理するワークフローを使用する](http://go.microsoft.com/fwlink/?LinkId=79757)します。  
  
## カスタムの SharePoint ワークフローの作成  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、SharePoint ワークフロー プロジェクトとして、**シーケンシャル ワークフロー**と**ステート マシンのワークフロー**の 2 種類のプロジェクトが利用できます。  
  
 *シーケンシャル ワークフロー*は、一連の手順を表します。  最後のアクティビティが完了するまで、その一連の手順が順次実行されます。  シーケンシャル ワークフローの "シーケンシャル" とは、あくまで処理が 1 つ 1 つ実行されるという意味です。  外部のイベントを受信したり、並列的な論理の流れを表現できるため、実際の実行順序は変化する場合があります。  次の図に、シーケンシャル ワークフローの例を示します。  
  
 ![シーケンシャル ワークフロー](../sharepoint/media/sp-sequential.png "シーケンシャル ワークフロー")  
  
 *ステート マシンのワークフロー*は、一連のステート、遷移、アクションで構成されます。  ステート マシン ワークフローの手順は、非同期的に実行されます。  つまり、必ずしも 1 つ 1 つ実行されるとは限らず、アクションやステートによってトリガーされます。  ある状態を開始ステートとし、特定のイベントに基づいて別のステートへの遷移が生じます。  ステート マシンには、ワークフローの終了を決定する最終状態を与えることができます。  次の図に、ステート マシンのワークフローの例を示します。  
  
 ![ステート マシンのワークフロー](../sharepoint/media/sp-state.png "ステート マシンのワークフロー")  
  
 ワークフローの種類の詳細については、参照します [ワークフローの種類](http://go.microsoft.com/fwlink/?LinkId=178995)。  
  
### ウィザードの使用  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint ワークフロー プロジェクトを作成する際は、まず、その設定を **SharePoint カスタマイズ ウィザード**で指定します。  ウィザードは、これらの設定を基に、**ソリューション エクスプローラー**にプロジェクトを作成します。  プロジェクトには、コード ファイルのほか、ワークフローの配置に使用するいくつかのファイル、および、カスタムの SharePoint ワークフローを作成するために必要となるアセンブリへの参照が含まれています。  
  
 ワークフローの作成後は、プロパティ ウィンドウでプロパティを変更できます。  ほとんどのワークフロー プロパティはプロパティ ウィンドウで直接変更できますが、一部のプロパティに関しては、省略記号ボタン \(![ASP.NET モバイル デザイナー楕円](~/sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")\) をクリックして値を変更する必要があります。  このボタンをクリックすると、**SharePoint カスタマイズ ウィザード**が起動します。  プロパティ値の変更を加えた後、それらを終了するに **\[完了\]** ボタンをクリックします。  
  
> [!NOTE]  
>  **\[ワークフローの種類\]** プロパティは読み取り専用です。変更することはできません。  ワークフローの種類を変更する場合は、別のワークフローを作成する必要があります。  
  
## SharePoint ワークフローのデザイン  
 ビジネス プロセス内のすべての手順を定義したら、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のワークフロー デザイナーを使用して、SharePoint ワークフローをデザインします。  デザイナーを開くには、**\[ソリューション エクスプローラー\]** で Workflow1.cs または Workflow1.vb をダブルクリックするか、またはこれらのファイルのいずれかのショートカット メニューを開き、**\[開く\]** をクリックします。  
  
### アクティビティ  
 ワークフローをデザインするには、**ツールボックス**からデザイナーの*ワークフロー スケジュール*にアクティビティを追加します。  ワークフロー スケジュールには、実行すべき順序でアクティビティのシーケンスが含まれています。  
  
 アクティビティには 2 種類あります。  
  
-   *単純アクティビティ*は、"1 日遅延" や "Web サービスの開始" など、作業の 1 単位を実行します。  
  
-   *複合アクティビティ*には、2 つの分岐を含む条件付きのアクティビティなど、その他のアクティビティが含まれます。  
  
 いずれの種類のアクティビティも**ツールボックス**で利用できます。  
  
 アクティビティには、プロパティ、メソッド、イベントを設定できます。  アクティビティのプロパティの設定には、**\[プロパティ\]** ウィンドウを使用します。  
  
 カスタムのアクティビティを作成することもできます。  詳細については、「[チュートリアル: サイトのカスタム ワークフロー アクティビティの作成](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)」を参照してください。  
  
 **ツールボックス**には、アクティビティが次のタブにまとめられてます。  
  
-   **SharePoint ワークフロー**  
  
-   **Windows Workflow v3.0**  
  
-   **Windows Workflow v3.5**  
  
 すべてのコア ワークフロー アクティビティが SharePoint でサポートされているわけではありません。  詳細については、参照します [Windows SharePoint Services のワークフロー アクティビティの概要](http://go.microsoft.com/fwlink/?LinkID=156094)。  
  
#### SharePoint ワークフロー アクティビティ  
 **\[SharePoint ワークフロー\]** タブには、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 用に特化したアクティビティが含まれています。  これらのアクティビティによって、ドキュメントのライフ サイクルを管理するワークフローの開発を簡素化し、効率化できます。  **\[SharePoint ワークフロー\]** タブに表示されるアクティビティの詳細についてを参照します[Windows SharePoint Services のワークフロー アクティビティの概要](http://go.microsoft.com/fwlink/?LinkID=156094)。  
  
#### Windows Workflow アクティビティ  
 **\[Windows Workflow\]** タブには、[!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] で提供されるアクティビティが含まれます。  これらのアクティビティを使用して、任意の種類の Windows Workflow アプリケーションのワークフロー スケジュールを作成できます。  
  
 **\[Windows Workflows\]** タブに表示されるアクティビティの詳細についてを参照します [Windows Workflow Foundation アクティビティ](http://go.microsoft.com/fwlink/?LinkID=156096)。  Windows Workflow Foundation に関する詳細については、参照 [Windows Workflow Foundation の概要](http://go.microsoft.com/fwlink/?LinkID=128632)します。  
  
### デザイナーでのアクティビティの操作  
 ワークフロー スケジュールには、Windows Workflow アクティビティと SharePoint ワークフロー アクティビティを組み合わせて含めることができます。  
  
 デザイナーには、ビジュアル キューが表示されるため、アクティビティを正確に位置付けて構成することができます。  ワークフローのスケジュールにアクティビティをドラッグするか、コピーすると、デザイナーは、そのワークフロー アクティビティの有効な位置を示すアイコン緑色の正符号 \(\+\) が表示されます。  有効ではない場所にアクティビティを配置することはできません。  たとえば、待機 \(Listen\) のアクティビティ分岐点の最初のアクティビティとして 送信 \(Send\) アクティビティを配置することはできません。  詳細については、参照します [SharePoint Designer Developer Center](http://go.microsoft.com/fwlink/?LinkId=178476)。  
  
## ワークフローにおける情報収集  
 ワークフローにあらかじめ定義されているタイミングで、ユーザーから情報を収集することができます。  情報の収集には、フォームや項目のプロパティを使用します。  
  
### フォーム  
 フォームは、質問を提起し、回答を導く方法をユーザーに提供するダイアログ ボックスのようなものです。  
  
 ワークフローに作成できるフォームには、次の 4 種類があります。  
  
-   関連付け  
  
-   開始  
  
-   変更  
  
-   タスク  
  
 このうち、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] に含まれているのは、関連付けフォーム用と開始フォーム用の項目テンプレートです。  *関連付けフォーム*の例としては、ワークフローをインストールする管理者が、そのワークフローに関連したパラメーター \(経費ワークフローの支出制限など\) を入力するためのフォームが挙げられます。  *開始フォーム* の例としては、経費のワークフローのユーザーが、自分がワークフローに支払った金額を入力できる 1 です。  フォームのこれらの型の詳細については、「[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)」を参照してください。  
  
### 項目のプロパティ  
 ユーザーから情報を収集するときに、SharePoint のライブラリ項目またはリスト項目のプロパティを使用することもできます。  メイン コード ファイル \(Workflow1.cs または Workflow1.vb\) には、`workflowProperties` という名前の Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties クラスのインスタンスが宣言されています。  `workflowProperties` オブジェクトを使用して、コード内のライブラリまたはリストのプロパティにアクセスします。  例については、「[チュートリアル : SharePoint ワークフロー ソリューションの作成とデバッグ](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)」を参照してください。  
  
## SharePoint ワークフロー テンプレートのデバッグ  
 SharePoint ワークフロー プロジェクトは、Web ベースの他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトと同様にデバッグできます。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッガーを起動すると、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は **SharePoint カスタマイズ ウィザード**に指定された設定を使用して、適切な SharePoint Web サイトを開き、適切なライブラリまたはリストにワークフロー テンプレートを自動的に関連付けます。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッガーを w3wp.exe という名前の [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] プロセスにアタッチする処理も実行します。  
  
 ワークフローをテストするには、ワークフローを手動で開始する必要があります。  詳細については、「[SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)」の「デバッグのワークフロー」を参照してください。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Web アプリケーションのデバッグの詳細については、「[Web アプリケーションとスクリプトのデバッグ](../debugger/debugging-web-applications-and-script.md)」を参照してください。  
  
## SharePoint ワークフロー テンプレートの配置  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ワークフロー プロジェクトは、他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトと同様に配置できます。  詳細については、「[SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)」を参照してください。  
  
## グローバルに再利用可能なワークフローのインポート  
 サイト固有の再利用可能なワークフローの作成に加えて、SharePoint Designer では、*グローバルに再利用可能なワークフロー*を作成できます。これは、すべての SharePoint サイトで使用できるワークフローです。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の再利用可能なワークフローのインポート プロジェクトは現在の再利用可能なワークフローを全体的にインポートしません。  ただし、SharePoint Designer を使用してグローバルに再利用可能なワークフローを再利用可能なワークフローに変換すること、または変換されていない宣言型ワークフローとしてワークフローをインポートすることはできます。  詳細については、「[既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[チュートリアル : SharePoint ワークフロー ソリューションの作成とデバッグ](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|単純な [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ワークフローを作成し、デバッグするための手順について説明します。|  
|[チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|関連付けフォームと開始フォームを備えた本格的な [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ワークフローの作成手順について説明します。|  
|[チュートリアル: ワークフローへのアプリケーション ページの追加](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|「[チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)」のトピックで作成したワークフローの応用です。.aspx のアプリケーション ページを追加して、ワークフローに入力されたデータを表示できるようにします。|  
|[チュートリアル: サイトのカスタム ワークフロー アクティビティの作成](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|サイト レベルのワークフローの作成とカスタム ワークフロー アクティビティの作成という、2 つの重要な作業の方法について説明します。|  
|[チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint Designer 2010 で作成した再利用可能な宣言型のワークフローを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトにインポートする方法について説明します。|  
  
## 参照  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
  
---
title: SharePoint ワークフロー ソリューションの作成 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4e808d93d2ae3039d4c5d79d1c14c65360bba32
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892312"
---
# <a name="create-sharepoint-workflow-solutions"></a>SharePoint ワークフロー ソリューションを作成します。

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ドキュメントとリスト アイテム、SharePoint Web サイトでのライフ サイクルを管理するカスタム ワークフローを作成するためのツールを提供します。 用意されている項目には、デザイナー、一連のアクティビティのコントロール、および必要なアセンブリ参照が含まれます。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 含まれています、 **SharePoint カスタマイズ ウィザード**、作成や、ワークフローを構成します。

SharePoint の詳細については、次を参照してください。 [Microsoft SharePoint 製品およびテクノロジ](http://go.microsoft.com/fwlink/?LinkId=178470)します。

## <a name="workflows-in-sharepoint"></a>SharePoint でのワークフロー
 ワークフローを SharePoint ライブラリまたはリストに追加する場合は、ライブラリまたはリスト内のすべてのアイテムでのビジネス プロセスを適用します。 ワークフローでは、システムまたはユーザーを編集し、確認し、項目を送信するなど、各アイテムに対して実行する必要がありますアクションを説明します。 呼ばれるこれらのアクション*アクティビティ*は、ワークフローの構成要素です。

 SharePoint ワークフローを作成する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]し、SharePoint Web サイトに展開します。 ワークフローは、SharePoint に配置される後、は、ライブラリまたはリストに関連付けます。 開始できます、自動的にプロセスが、またはユーザーによって手動でします。 ワークフロー操作の詳細については、次を参照してください。 [Visual Studio を使用して SharePoint の開発ワークフロー](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio)します。

## <a name="create-custom-sharepoint-workflows"></a>カスタムの SharePoint ワークフローを作成します。
 2 つの SharePoint ワークフロー プロジェクトで使用できる[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]:**シーケンシャル ワークフロー**と**ステート マシン ワークフロー**します。

 A*シーケンシャル ワークフロー*一連の手順を表します。 最後のアクティビティが完了するまで、手順は 1 つずつで実行されます。 シーケンシャル ワークフローは、実行の厳密な逐次は常にします。 外部のイベントを受信し、並列ロジック フローを含めるいてできるため、実際の実行順序が異なる場合があります。 次の図は、シーケンシャル ワークフローの例を示します。

 ![シーケンシャル ワークフロー](../sharepoint/media/sp-sequential.png "シーケンシャル ワークフロー")

 A*ステート マシン ワークフロー*状態、遷移、およびアクションのセットを表します。 ステート マシン ワークフローの手順は、非同期的に実行します。 つまりは必ずしも実行される 1 つずつが代わりに、アクションと状態によってトリガーされます。 1 つの状態が開始状態として割り当てられているし、次に、イベントに基づき、状態が変わる別の状態にします。 ステート マシン ワークフローの終了を決定する最終の状態を持つことができます。 次の図は、ステート マシン ワークフローの例を示します。

 ![ステート マシン ワークフロー](../sharepoint/media/sp-state.png "マシンのワークフローの状態")

 ワークフローの種類の詳細については、次を参照してください。[ワークフロー型](http://go.microsoft.com/fwlink/?LinkId=178995)します。

### <a name="use-the-wizard"></a>ウィザードの使用
 SharePoint ワークフロー プロジェクトを作成するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、最初にその設定を指定する、 **SharePoint カスタマイズ ウィザード**します。 ウィザードでは、これらの設定を使用でプロジェクトを作成して**ソリューション エクスプ ローラー**します。 このプロジェクトは、コード ファイルでは、ワークフローの配置に使用されるいくつかのファイルが含まれていて、カスタム SharePoint ワークフローを作成するために必要なアセンブリへの参照します。

 ワークフローを作成した後は、[プロパティ] ウィンドウでそのプロパティを変更できます。 省略記号ボタンをクリックする必要がいくつかが、ほとんどのワークフロー プロパティをプロパティ ウィンドウで直接変更できます (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) するその値を変更します。 このボタンの再起動、 **SharePoint カスタマイズ ウィザード**します。 プロパティ値の変更、選択を行った後、**完了**ボタンをクリックして確定します。

> [!NOTE]
>  **ワークフロー型**プロパティは読み取り専用であり変更ことはできません。 ワークフローの種類を変更する場合は、別のワークフローを作成する必要があります。

## <a name="design-a-sharepoint-workflow"></a>SharePoint ワークフローを設計します。
 使用して、ビジネス プロセスのすべての手順を定義した後、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ワークフロー デザイナーの SharePoint ワークフローを設計します。 デザイナーを開くには、Workflow1.cs workflow1.vb でダブルクリックして**ソリューション エクスプ ローラー**、またはそれらのファイルのいずれかのショートカット メニューを開きし、選択**開く**します。

### <a name="activities"></a>アクティビティ
 ワークフローを設計するには、アクティビティを追加、**ツールボックス**を*ワークフロー スケジュール*デザイナー。 ワークフローのスケジュールには、実行する必要がありますの順序で活動のシーケンスが含まれています。

 2 種類のアクティビティがあります。

- *単純なアクティビティ*「1 日の遅延」または「Web サービスを開始します。」など、作業の 1 つの単位を実行します。

- *複合アクティビティ*他のアクティビティを含めることが。 たとえば、条件付きアクティビティが 2 つの分岐を含めることができます。

  両方の種類のアクティビティが表示されます、**ツールボックス**します。

  アクティビティには、プロパティ、メソッド、およびイベントを持つことができます。 使用して、**プロパティ**アクティビティのプロパティを設定するウィンドウ。

  カスタム アクティビティを作成することもできます。 詳細については、次を参照してください。[チュートリアル: サイトのカスタム ワークフロー アクティビティを作成する](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)します。

  アクティビティは、次のタブでに編成、**ツールボックス**:

- **SharePoint ワークフロー**

- **Windows Workflow v3.0**

- **Windows Workflow v3.5**

  すべての主要なワークフロー活動は、SharePoint でサポートされます。 詳細については、次を参照してください。[ワークフロー アクティビティの Windows SharePoint Services の概要](http://go.microsoft.com/fwlink/?LinkID=156094)します。

#### <a name="sharepoint-workflow-activities"></a>SharePoint ワークフロー アクティビティ
 **SharePoint ワークフロー**タブで使用するための特殊な活動を含む[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]します。 これらのアクティビティは、簡略化し、ドキュメントのライフ サイクル ワークフローの開発を合理化します。 表示されているアクティビティの詳細については、 **SharePoint ワークフロー**  タブを参照してください[ワークフロー アクティビティの Windows SharePoint Services の概要](http://go.microsoft.com/fwlink/?LinkID=156094)します。

#### <a name="windows-workflow-activities"></a>Windows ワークフロー アクティビティ
 **Windows ワークフロー**タブが用意されているアクティビティを含む、[!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]します。 これらのアクティビティを使用すると、あらゆる種類の Windows ワークフロー アプリケーションのワークフローのスケジュールを作成します。

 表示されているアクティビティの詳細については、 **Windows ワークフロー**  タブを参照してください[Windows Workflow Foundation アクティビティ](http://go.microsoft.com/fwlink/?LinkID=156096)します。 詳細については、Windows Workflow Foundation は、次を参照してください。 [Windows Workflow Foundation の概要](http://go.microsoft.com/fwlink/?LinkID=128632)します。

### <a name="work-with-activities-in-the-designer"></a>デザイナーでアクティビティを使用します。
 ワークフローのスケジュールは、Windows ワークフロー アクティビティおよび SharePoint ワークフロー アクティビティの組み合わせを含めることができます。

 デザイナーでは、配置およびアクティビティを正しく構成するための視覚的な手掛かりが表示されます。 ドラッグしたり、ワークフローのスケジュールにアクティビティをコピーする場合、デザイナーには、ワークフローでそのアクティビティの有効な場所を示す緑色のプラス記号 (+) アイコンが表示されます。 いることは有効な場所でアクティビティを配置することはできません。 たとえば、Listen アクティビティの分岐で最初のアクティビティとして Send アクティビティを配置することはできません。 詳細については、次を参照してください。 [SharePoint Designer デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=178476)します。

## <a name="collect-information-during-the-workflow"></a>ワークフローの間に情報を収集します。
 ユーザーから情報を収集する時間にワークフローの定義済みにします。 フォームまたはアイテムのプロパティを使用して情報を収集することができます。

### <a name="forms"></a>フォーム
 フォームは、質問を含み、ユーザーが応答を提供する方法を提供できるダイアログ ボックスに似ています。

 ワークフローで使用できるフォームの 4 つの種類があります。

- 関連付け

- 開始

- 変更

- タスク

  これらのうち、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]アソシエーションと開始フォーム項目テンプレートが含まれています。 例、*関連付けフォーム*経費ワークフローの使用制限など、ワークフローに関連するパラメーターを入力できるように、管理者のワークフローをインストールする 1 つです。 例、*開始フォーム*経費ワークフローのユーザーがワークフローに費やされた金額を入力できる 1 つです。 この種類のフォームの詳細については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)します。

### <a name="item-properties"></a>項目のプロパティ
 SharePoint ライブラリまたはリスト内の項目のプロパティを使用して、ユーザーから情報を収集することもできます。 メイン コード ファイル (Workflow1.cs workflow1.vb) という名前の Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties クラスのインスタンスを宣言します`workflowProperties`します。 使用して、`workflowProperties`ライブラリまたはコードの一覧のプロパティにアクセスするオブジェクト。 例については、次を参照してください。[チュートリアル: を作成し、SharePoint ワークフロー ソリューションのデバッグ](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)します。

## <a name="debug-a-sharepoint-workflow-template"></a>SharePoint ワークフロー テンプレートをデバッグします。
 できますプロジェクトをデバッグする SharePoint ワークフローと同じ他のデバッグ時に[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Web ベースのプロジェクト。 開始すると、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デバッガー、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で指定した設定を使用して、 **SharePoint カスタマイズ ウィザード**を適切な SharePoint Web サイトを開き、ワークフロー テンプレートを自動的に関連付ける適切なライブラリまたはリスト。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] アタッチしても、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デバッガーを[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]という名前のプロセス*w3wp.exe*します。

 ワークフローをテストするにする必要があります手動で開始します。 詳細については、「ワークフローのデバッグ」セクションを参照してください[SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)します。 詳細については[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Web アプリケーションのデバッグを参照してください[web アプリケーションとスクリプトをデバッグ](../debugger/debugging-web-applications-and-script.md)します。

## <a name="deploy-a-sharepoint-workflow-template"></a>SharePoint ワークフロー テンプレートをデプロイします。
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ワークフロー プロジェクトを他のような展開[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint プロジェクト。 詳細については、次を参照してください。[パッケージと SharePoint のデプロイ ソリューション](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)します。

## <a name="import-globally-reusable-workflows"></a>グローバルに再利用可能なワークフローをインポートします。
 サイト固有の再利用可能なワークフローを作成するだけでなく SharePoint Designer を使用すると、作成*グローバルに再利用可能なワークフロー*、任意の SharePoint サイトで使用できるワークフローであります。 再利用可能なワークフローのインポート プロジェクト[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]現在グローバルに再利用可能なワークフローをインポートしません。 ただし、SharePoint Designer を使用して、グローバルに再利用可能なワークフローを再利用可能なワークフローに変換するか、または、未変換の宣言型ワークフローとワークフローをインポートすることができます。 詳細については、次を参照してください。[既存の SharePoint サイトからアイテムをインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)します。

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[チュートリアル: 作成し、SharePoint ワークフロー ソリューションのデバッグ](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|作成して、単純なデバッグ手順について説明[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ワークフロー。|
|[チュートリアル: 関連付けフォームと開始フォームとワークフローを作成します。](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|手順について説明するフル機能の作成に[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ワークフロー関連付けフォームと開始フォームを完了します。|
|[チュートリアル: ワークフローへのアプリケーション ページを追加します。](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|トピックに基づいて[チュートリアル: アソシエーションと開始フォームでワークフローを作成する](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)を追加して *.aspx*アプリケーション ページでは、ワークフローに入力されたデータを報告します。|
|[チュートリアル: サイトのカスタム ワークフロー アクティビティを作成します。](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|2 つの主要タスクを実行する方法について説明します。 サイト レベルのワークフローを作成し、カスタム ワークフロー アクティビティを作成します。|
|[チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポートします。](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint Designer 2010 で作成、再利用可能な宣言型ワークフローをインポートする方法を示します、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクト。|

## <a name="see-also"></a>関連項目

- [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [For SharePoint アプリケーション ページを作成します。](../sharepoint/creating-application-pages-for-sharepoint.md)
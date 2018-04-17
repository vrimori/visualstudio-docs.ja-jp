---
title: SharePoint ソリューションのトラブルシューティング |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba8f84db31cbe41e8bd3f62a7806de0a6d2ea58e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-sharepoint-solutions"></a>SharePoint ソリューションのトラブルシューティング
  以下の問題または警告は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッガーを使用して SharePoint ソリューションをデバッグするときに発生することがあります。 詳細については、次を参照してください。 [SharePoint 2007 ワークフロー ソリューションのデバッグ](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247)です。
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>サンドボックス視覚的 Web パーツでのトークンの制約  
 サンドボックス ソリューションの視覚的 Web パーツは、SharePoint ランタイムでサポートされる $SPUrl などの標準トークンを処理できません。 そのため、URL は解決されず、次の例のように、スクリプト要素でこのトークンを直接参照する場合、視覚的 Web パーツ デザイナーのデザイン ビューでコンテンツをプレビューできません。  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 この制限を回避し、トークンを解決するには、次のようにリテラルを使用してトークンを参照します。  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>プロジェクトとプロジェクト アイテムの名前の文字制限  
 プロジェクトとプロジェクト アイテムの名前には、SharePoint 2010 の配置パスで有効な文字だけを使用できます。 他の文字は使用できません。  
  
### <a name="error-message"></a>エラー メッセージ  
 「無効な文字」エラー メッセージ。  
  
### <a name="resolution"></a>解像度  
 SharePoint のプロジェクトとプロジェクト アイテムの名前では、次の文字だけを使用してください。  
  
-   ASCII 英数字  
  
-   スペース  
  
-   ピリオド (.)  
  
-   コンマ (,)  
  
-   アンダースコア (_)  
  
-   ダッシュ (-)  
  
-   円記号 (\\)  
  
 プロジェクトがパッケージされるとき、検証規則により、配置される各ファイルの配置パス プロパティに有効な文字だけが含まれていることが確認されます。  
  
## <a name="errors-when-creating-custom-fields"></a>カスタム フィールド作成時のエラー  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、カスタム フィールドは、XML で定義されます。 フィールドが特定の形式で定義または参照されていない場合、エラーが発生する可能性があります。  
  
### <a name="error-message"></a>エラー メッセージ  
 パッケージ実行時の「無効な文字」エラー メッセージ。  
  
### <a name="resolution"></a>解像度  
 フィールド定義の ID には、次の例のように、中かっこで囲まれた GUID を指定する必要があります。  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 空の要素の形式を使用してコンテンツ タイプ内のフィールド参照を定義する必要が次の例に示す (\<FieldRef/>)、開始/終了要素を使用していない (\<FieldRef >\</FieldRef >)。  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 フィールドのソース XML の形式が間違っている場合、有効な XML ファイルでない場合、またはその他の問題がある場合、"ファイルを解析できません" エラーが発生します。  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>英語以外の新しいサイト定義が配置後にサイトの作成ページに表示されない  
 英語以外のバージョンを使用してサイト定義を展開して作成した後に[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (ロケールでのバージョンは、 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 1033 以外) では、 **SharePoint のカスタマイズ**タブが表示されず、 **テンプレートの選択**ボックスと、新しいサイト テンプレートに表示されない、**新しい SharePoint サイト**ページ。  
  
### <a name="error-message"></a>エラー メッセージ  
 なし。  
  
### <a name="resolution"></a>解像度  
 この問題は発生で値が正しくないため、**パス**webtemp サイト定義構成ファイル (webtemp_SiteDefinitionProject1.xml など) のプロパティです。 **パス**の下にある、webtemp ファイルのプロパティ、**配置場所**、1033 を適切なロケールに変更[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]です。 たとえば、使用する日本語のロケール値を変更を 1041 にします。 詳細については、次を参照してください。 [Microsoft によるロケール Id 割り当て](http://go.microsoft.com/fwlink/?LinkID=165561)MSDN Web サイトです。  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>ワークフロー プロジェクトをクリーン システムに配置するとエラーが表示される  
 この問題は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のワークフロー プロジェクトをクリーン システムに配置した場合に発生します。 クリーン システムとは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] と SharePoint の新しいインストールが含まれているが、ワークフロー プロジェクトは配置されていないコンピューターです。  
  
### <a name="error-message"></a>エラー メッセージ  
 SharePoint リストが見つかりません: ワークフローの履歴。  
  
### <a name="resolution"></a>解像度  
 このエラーが発生するのは、ワークフローの履歴リストがないからです。 開発環境がクリーン システムの場合、ワークフローが配置されていないため、ワークフローの履歴リストはまだ存在しません。 この問題を解決するには、ワークフロー ウィザードをもう一度開きます。これにより、ワークフローの履歴リストが作成されます。  
  
##### <a name="to-reenter-the-workflow-wizard"></a>ワークフロー ウィザードを再実行するには  
  
1.  **ソリューション エクスプ ローラー**、ワークフロー ノードを選択します。  
  
2.  **プロパティ**ウィンドウで、省略記号ボタンが任意のプロパティに対して省略記号 (...) ボタンをクリックします。  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>デバッグ中に更新されたイメージを表示するにはブラウザーでアプリケーション ページを更新する必要がある  
 デバッグしている SharePoint ソリューションに、イメージを表示するコントロール ([!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] Image コントロールなど) を含むアプリケーション ページが含まれている場合に、そのイメージに対して行われた変更を表示するには、ブラウザーでページを更新する必要があります。  
  
## <a name="error-the-site-location-is-not-valid"></a>エラー: サイトの場所が有効ではありません  
 この問題は、[!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] がインストールされていない場合に発生することがあります。 指定されている SharePoint Web サイトに管理者アクセスできない場合も発生可能性があります、 **SharePoint カスタマイズ ウィザード**です。  
  
### <a name="error-message"></a>エラー メッセージ  
  
-   入力されている SharePoint サイトの場所が有効ではありません。  
  
### <a name="resolution"></a>解像度  
  
-   [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] をインストールします。  
  
-   SharePoint Web サイトに対する管理者の権限があることを確認します。 詳細については、次を参照してください。、[!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)]オンラインの記事[ポータル サイトへのアクセス許可](http://go.microsoft.com/fwlink/?LinkId=98310)です。  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>イベント レシーバー プロジェクトでサイト削除 Web イベントが発生しない  
 イベント レシーバー プロジェクトを作成し、"サイトが削除されています" などの特定の Web イベントを選択すると、イベントは発生しません。  
  
### <a name="error-message"></a>エラー メッセージ  
 なし。  
  
### <a name="resolution"></a>解像度  
 この問題は、サイト レベルのイベントを処理するにはフィーチャーのスコープが "サイト" である必要があるのに、イベント レシーバー プロジェクトの既定のフィーチャー スコープが "Web" になっているために発生します。 影響を受ける Web イベントは次のとおりです。  
  
-   サイトが削除されています (WebDeleting)  
  
-   サイトが削除されました (WebDeleted)  
  
-   サイトが移動されています (WebMoving)  
  
-   サイトが移動されました (WebMoved)  
  
 この問題を修正するには、イベント レシーバーのフィーチャー スコープを次のように変更します。  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>イベント レシーバーのフィーチャー スコープを変更するには  
  
1.  **ソリューション エクスプ ローラー**でイベント レシーバーの .feature ファイルを開く、**フィーチャー デザイナー**ファイルをダブルクリックするか、そのショートカット メニューをクリックして、開き**を開く**.  
  
2.  横の矢印を選択**スコープ**を選択し**サイト**表示される一覧にします。  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>ビジネス データ接続モデル プロジェクトで識別子の名前を変更すると配置エラーが発生する  
 この問題は、ビジネス データ接続 (BDC) モデルでエンティティの識別名を変更した後、ソリューションを配置しようとすると発生します。  
  
### <a name="error-messages"></a>エラー メッセージ  
  
-   \<*モデル名*> 次の外部コンテンツ タイプ アクティブ化エラーが発生しています.  
  
-   名前 IMetadataObject は、'\<*モデル名*>' の値フィールド 'name' が重複しています.  
  
### <a name="resolution"></a>解像度  
 この問題を解決するには、モデルを手動で削除した後、ソリューションを再び配置します。  モデルを削除するには、次のどちらかのツールを使用します。  
  
-   SharePoint 2010 サーバーの全体管理。 詳細については、次を参照してください。 [BDC モデル管理](http://go.microsoft.com/fwlink/?LinkID=181472)、Microsoft TechNet Web サイトにします。  
  
-   Windows PowerShell。 コマンド プロンプトでこのコマンドを入力して、モデルを削除することができます:**削除 SPBusinessDataCatalogModel**です。 詳細については、次を参照してください。[全般コマンドレット (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) 、Microsoft TechNet Web サイトにします。  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>可視 Web パーツを SharePoint で表示しようとするとエラーが表示される  
 この問題が発生したときに、**パス**ユーザー コントロールのプロパティが文字列で始まらない"全体について\\"です。  
  
### <a name="error-messages"></a>エラー メッセージ  
  
-   ファイル '/_CONTROLTEMPLATES/*\<プロジェクト名 >*/*\<Web パーツの名前 >*/*\<ユーザー コントロール名前 >*.ascx' がありません。  
  
-   '/' アプリケーションにサーバー エラーがあります。  
  
### <a name="resolution"></a>解像度  
  
##### <a name="to-resolve-this-issue"></a>この問題を解決するには  
  
1.  **ソリューション エクスプ ローラー**、ユーザー コントロール ファイルを持つファイル名拡張子が .ascx に選択します。  
  
2.  メニュー バーで、次のように選択します。**ビュー**、**プロパティ ウィンドウ**します。  
  
3.  **プロパティ**ウィンドウで、展開、**配置場所**ノード。  
  
4.  値を確認してください、**パス**プロパティが文字列で始まる"全体について\\"です。  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>インポートしたタスク フォーム フィールドを含む再使用可能なワークフローを実行するとエラーが表示される  
 この問題は、フィールドを含むタスク フォームが存在するワークフローをインポートした後、ワークフローのインポート元と同じシステム上で新しいワークフローを実行したときに発生します。  
  
### <a name="error-message"></a>エラー メッセージ  
 配置手順"機能のアクティブ化でエラーが発生しました: Id を持つフィールド [*Guid*] 機能で定義されている [*Guid*] 現在のサイト コレクションまたはサブサイト内に見つかりました。  
  
### <a name="resolution"></a>解像度  
 このエラーは、再利用可能なワークフローのインポート プロジェクトでは、フィールド ID の競合の結果[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]タスク フォームのフィールド Id は変わりません。 元のワークフローが含まれる同じサーバーにインポートしたワークフローを展開する場合は、フィールド ID の競合が発生します。  
  
 この問題を解決するには、検索置換機能を使用して、インポートしたすべてのワークフロー ファイル内のフィールド ID 属性の値を変更する必要があります。  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>インポートして名前を変更したリスト インスタンスを実行するとエラーが表示される  
 この問題は、インポートしたリスト インスタンスの名前を変更した後、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で実行した場合に発生します。  
  
### <a name="error-message"></a>エラー メッセージ  
 ビルド エラー: 配置手順"機能のアクティブ化でエラーが発生しました: ファイル Template\Features\\[*プロジェクトのインポート**機能**名前*] \Files\Lists\\[*古い * * リスト名*] \Schema.xml が存在しません。  
  
### <a name="resolution"></a>解像度  
 リスト インスタンスをインポートすると、CustomSchema という名前の属性がリスト インスタンスの Elements.xml ファイルに追加されます。 Elements.xml には、リスト インスタンス用のカスタム schema.xml のパスが含まれます。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でリスト インスタンスの名前を変更すると、カスタム schema.xml の配置パスは変更されますが、CustomSchema 属性のパス値は更新されません。 この結果、機能がアクティブ化されるときに、リスト インスタンスは、CustomSchema 属性に指定された古いパスでは schema.xml ファイルを検出できません。  
  
 この問題を解決するには、CustomSchema 属性の schema.xml ファイルの配置場所のパスを更新します。  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint デバッグ セッションが IIS によって終了する  
 この問題にブレークポイントを設定する場合に発生、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ソリューションでは、F5 キーを実行し、90 秒より長いブレークポイントの位置のままになります。  
  
### <a name="error-message"></a>エラー メッセージ  
 デバッグ対象の Web サーバー プロセスは、インターネット インフォメーション サービス (IIS) によって停止されました。 IIS のアプリケーション プールの ping の設定を構成することによって、この問題を回避できます。 詳細については、ヘルプを参照してください。  
  
### <a name="resolution"></a>解像度  
 既定では、IIS アプリケーション プールは、アプリケーションから応答が返るまで 90 秒間待機した後、アプリケーションを閉じます。 このプロセスは、アプリケーションの "ping" として知られています。 この問題を解決するには、待機時間を増やすか、アプリケーションの ping を完全に無効にします。  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>IIS アプリケーション プールの設定にアクセスするには  
  
1.  IIS マネージャーを開きます。  
  
2.  **接続** ウィンドウで、SharePoint サーバー ノードを展開しを選択し、**アプリケーション プール**ノード。  
  
3.  **アプリケーション プール**ページで、SharePoint アプリケーション プール (通常"SharePoint - 80") を選択し、[、**アクション**] ウィンドウで、選択、**詳細設定**リンクします。  
  
4.  IIS がタイムアウトまでの待機時間を大きくには、値を変更**Ping 最大応答時間 (秒)** 90 秒よりも大きい値にします。  
  
5.  IIS の ping を無効にする設定**Ping の有効化**に**False**です。  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>自動取り消しで孤立状態のリスト インスタンスが SharePoint に残る  
 この問題は、次の手順に従った場合に発生します。  
  
1.  リスト インスタンスがあるリスト定義を [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成します。  
  
2.  F5 キーを押してソリューションを実行します。  
  
3.  デバッグを停止するか、SharePoint サイトを閉じます。  
  
4.  SharePoint サイトを再度開き、リスト インスタンスを開きます。  
  
### <a name="error-message"></a>エラー メッセージ  
 '/' アプリケーションにサーバー エラーがあります。  
  
### <a name="resolution"></a>解像度  
 このエラーは、SharePoint ソリューションのデバッグ セッションを閉じた後、自動取り消し機能によってソリューションが取り消されたために発生します。 取り消しにより、リスト定義は SharePoint から削除されますが、リスト インスタンスは削除されません。 リスト インスタンスは、基になるリスト定義を必要とします。  
  
 この問題を解決するには、メニュー バーで、ソリューションの配置**ビルド**、**展開**です。 (F5 キーを選択してソリューションをデバッグないでください)。次に、SharePoint 内のリスト インスタンスを削除します。  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>元の SharePoint ソリューションがエクスポートしたバージョンによって置換される  
 エクスポートした SharePoint ソリューションを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] にインポートした後、そのソリューションをエクスポート元のサイトに配置した場合、元の SharePoint ソリューションが置換されます。 この問題は、ソリューションの配置先を元のソリューションがアクティブ化されていないサーバーにすると、発生しません。  
  
### <a name="error-message"></a>エラー メッセージ  
 なし。  
  
### <a name="resolution"></a>解像度  
 エクスポート元のサイトでソリューションが上書きされないようにするには、ソリューション ID の GUID と [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトにインポートしたすべての機能の機能 ID を変更します。  
  
## <a name="error-appears-when-debugging-starts"></a>デバッグ開始時にエラーが表示される  
 Visual Studio で SharePoint ソリューションのデバッグを開始すると、特定のキーがディクショナリに存在しないので Visual Studio で Web.config ファイルを読み込むことができないというエラーが発生します。  
  
### <a name="error-message"></a>エラー メッセージ  
 Web.config 構成ファイルを読み込むことができませんでした。 ファイルをチェックして、形式が正しくない XML 要素を修正した後、再試行してください。 次のエラーが発生しています: 特定のキーがディクショナリに存在しません。  
  
### <a name="resolution"></a>解像度  
 この問題を解決するには、Visual Studio 内の SharePoint プロジェクトの [サイト URL] プロパティの値が、Web アプリケーションの代替アクセス マッピング用の既定のゾーンに割り当てられた URL と一致することを確認します。 URL でイントラネットなどの他のゾーンを使用すると、エラーは解消されません。 プロジェクトのサイト URL と既定のゾーンの URL は一致している必要があります。 代替アクセス マッピングにアクセスするには、SharePoint 2010 サーバーの全体管理ユーティリティを開きを選択、**アプリケーション管理**リンクし、 **Web アプリケーション**、選択、 **代替アクセス マッピングを構成する**リンクします。 詳細については、次を参照してください。 [Web アプリケーションのゾーンを作成する](http://go.microsoft.com/fwlink/?LinkId=192274)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint のパッケージ化と配置のトラブルシューティング](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)  
  
  

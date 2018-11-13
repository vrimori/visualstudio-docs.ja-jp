---
title: SharePoint ソリューションのトラブルシューティング |Microsoft Docs
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
ms.openlocfilehash: f68f6e50be569df6130f7e6c6f3aa4bc7c107214
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296048"
---
# <a name="troubleshoot-sharepoint-solutions"></a>SharePoint ソリューションをトラブルシューティングします。
  以下の問題または警告は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッガーを使用して SharePoint ソリューションをデバッグするときに発生することがあります。 詳細については、次を参照してください。 [SharePoint 2007 ワークフロー ソリューションのデバッグ](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247)します。
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>サンド ボックス視覚的 web パーツでトークンの制限
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
  
- ASCII 英数字  
  
- スペース  
  
- ピリオド (.)  
  
- コンマ (,)  
  
- アンダースコア (_)  
  
- ダッシュ (-)  
  
- 円記号 (\\)  
  
  プロジェクトがパッケージされるとき、検証規則により、配置される各ファイルの配置パス プロパティに有効な文字だけが含まれていることが確認されます。  
  
## <a name="errors-when-creating-custom-fields"></a>カスタム フィールドを作成するときにエラー
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、カスタム フィールドは、XML で定義されます。 フィールドが特定の形式で定義または参照されていない場合、エラーが発生する可能性があります。  
  
### <a name="error-message"></a>エラー メッセージ
 パッケージ化時に「無効な文字」エラー メッセージ。  
  
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
  
 空の要素の形式を使用してコンテンツの種類で、フィールドの参照を定義する必要があります、次の例に示すように (\<FieldRef/>)、開始/終了要素を使用してではなく (\<FieldRef >\</FieldRef >)。  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 フィールドのソース XML の形式が間違っている場合、有効な XML ファイルでない場合、またはその他の問題がある場合、"ファイルを解析できません" エラーが発生します。  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>デプロイ後にサイトの作成 ページに新しい英語以外のサイト定義は表示されません。
 作成しの英語以外のバージョンを使用してサイト定義を展開すると[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](ロケールとバージョンは、 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 1033 以外)、 **SharePoint のカスタマイズ**タブが表示されず、 **テンプレートの選択**にボックスと、新しいサイト テンプレートがない、**新しい SharePoint サイト**ページ。  
  
### <a name="error-message"></a>エラー メッセージ
 なし。  
  
### <a name="resolution"></a>解像度  
 値が不適切なため、この問題が発生します、**パス**webtemp サイト定義の構成のプロパティ ファイルなど、 *webtemp_SiteDefinitionProject1.xml*します。 **パス**の下にある、webtemp ファイルのプロパティ、**配置場所**、1033 を適切なロケールに変更[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]します。 たとえば、使用する日本語のロケール値に変更 1041。 詳細については、次を参照してください。 [Microsoft によるロケール Id 割り当て](http://go.microsoft.com/fwlink/?LinkID=165561)します。  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>ワークフロー プロジェクトがクリーン システムにデプロイした場合、エラーが表示されます。
 この問題は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のワークフロー プロジェクトをクリーン システムに配置した場合に発生します。 クリーン システムとは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] と SharePoint の新しいインストールが含まれているが、ワークフロー プロジェクトは配置されていないコンピューターです。  
  
### <a name="error-message"></a>エラー メッセージ
 SharePoint リストが見つかりません: ワークフローの履歴。  
  
### <a name="resolution"></a>解像度  
 このエラーが発生するのは、ワークフローの履歴リストがないからです。 開発環境がクリーン システムの場合、ワークフローが配置されていないため、ワークフローの履歴リストはまだ存在しません。 この問題を解決するには、ワークフロー ウィザードをもう一度開きます。これにより、ワークフローの履歴リストが作成されます。  
  
##### <a name="to-reenter-the-workflow-wizard"></a>ワークフロー ウィザードを再実行するには  
  
1.  **ソリューション エクスプ ローラー**でワークフロー ノードを選択します。  
  
2.  **プロパティ**ウィンドウで、省略記号ボタンがある任意のプロパティに対して省略記号 (...) ボタンをクリックします。  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>ユーザーは、更新された画像を表示するデバッグ中にブラウザーでアプリケーション ページを更新する必要があります。
 デバッグしている SharePoint ソリューションに、イメージを表示するコントロール ([!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] Image コントロールなど) を含むアプリケーション ページが含まれている場合に、そのイメージに対して行われた変更を表示するには、ブラウザーでページを更新する必要があります。  
  
## <a name="error-the-site-location-is-not-valid"></a>エラー: サイトの場所が無効です。
 この問題は、[!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] がインストールされていない場合に発生することがあります。 指定されている SharePoint Web サイトに管理者アクセスできない場合も発生可能性があります、 **SharePoint カスタマイズ ウィザード**します。  
  
### <a name="error-message"></a>エラー メッセージ
  
-   入力されている SharePoint サイトの場所が有効ではありません。  
  
### <a name="resolution"></a>解像度  
  
-   [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]をインストールします。  
  
-   SharePoint Web サイトに対する管理者の権限があることを確認します。 詳細については、次を参照してください。、[!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)]オンライン記事[割り当てまたは SharePoint サーバーのサービス アプリケーションの管理者を削除](https://docs.microsoft.com/sharepoint/administration/assign-or-remove-administrators-of-service-applications)します。  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>イベント レシーバー プロジェクトでサイト削除 web イベントは発生しません
 イベント レシーバー プロジェクトを作成し、"サイトが削除されています" などの特定の Web イベントを選択すると、イベントは発生しません。  
  
### <a name="error-message"></a>エラー メッセージ
 なし。  
  
### <a name="resolution"></a>解像度  
 この問題は、サイト レベルのイベントを処理するにはフィーチャーのスコープが "サイト" である必要があるのに、イベント レシーバー プロジェクトの既定のフィーチャー スコープが "Web" になっているために発生します。 影響を受ける Web イベントは次のとおりです。  
  
- サイトが削除されています (WebDeleting)  
  
- サイトが削除されました (WebDeleted)  
  
- サイトが移動されています (WebMoving)  
  
- サイトが移動されました (WebMoved)  
  
  この問題を修正するには、イベント レシーバーのフィーチャー スコープを次のように変更します。  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>イベント レシーバーのフィーチャー スコープを変更するには  
  
1.  **ソリューション エクスプ ローラー**、開く、イベント レシーバーの *.feature*ファイル、**フィーチャー デザイナー**ファイルをダブルクリックするか、そのショートカット メニューを開きし、選択**オープン**します。  
  
2.  横にある矢印を選択**スコープ**を選び、**サイト**で表示される一覧。  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>ビジネス データ接続モデル プロジェクト内の識別子の名前を変更した後、展開エラーが表示されます。
 この問題は、ビジネス データ接続 (BDC) モデルでエンティティの識別名を変更した後、ソリューションを配置しようとすると発生します。  
  
### <a name="error-messages"></a>エラー メッセージ
  
-   \<*モデル名*> 次の外部コンテンツ タイプ アクティブ化エラーが発生しています.  
  
-   名前 IMetadataObject は、'\<*モデル名*>' の値フィールド 'name' が重複しています.  
  
### <a name="resolution"></a>解像度  
 この問題を解決するには、モデルを手動で削除した後、ソリューションを再び配置します。  モデルを削除するには、次のどちらかのツールを使用します。  
  
-   SharePoint 2010 サーバーの全体管理。 詳細については、次を参照してください。 [BDC モデル管理](http://go.microsoft.com/fwlink/?LinkID=181472)、Microsoft TechNet Web サイト。  
  
-   Windows PowerShell。 コマンド プロンプトで次のコマンドを入力して、モデルを削除することができます:**削除 SPBusinessDataCatalogModel**します。 詳細については、次を参照してください。[全般のコマンドレット (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) 、Microsoft TechNet Web サイト。  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>SharePoint で視覚的 web パーツを表示するときにエラーが表示されます。
 この問題が発生したときに、**パス**ユーザー コントロールのプロパティが文字列で始まらない"CONTROLTEMPLATES\\"。  
  
### <a name="error-messages"></a>エラー メッセージ
  
-   ファイル '/_controltemplates/*\<プロジェクト名 >*/*\<Web パーツの名前 >*/*\<ユーザー コントロール名前 >*.ascx' が存在しません。  
  
-   '/' アプリケーションにサーバー エラーがあります。  
  
### <a name="resolution"></a>解像度  
  
##### <a name="to-resolve-this-issue"></a>この問題を解決するには  
  
1.  **ソリューション エクスプ ローラー**のファイル名拡張子は、ユーザー コントロール ファイルを選択 *.ascx*します。  
  
2.  メニュー バーで、**ビュー** > **プロパティ ウィンドウ**します。  
  
3.  **プロパティ**ウィンドウで、展開、**配置場所**ノード。  
  
4.  値を必ず、**パス**プロパティが文字列で始まる"CONTROLTEMPLATES\\"。  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>タスク フォームのフィールドを含む、インポートした再利用可能なワークフローの実行時にエラーが表示されます。
 この問題は、フィールドを含むタスク フォームが存在するワークフローをインポートした後、ワークフローのインポート元と同じシステム上で新しいワークフローを実行したときに発生します。  
  
### <a name="error-message"></a>エラー メッセージ
 配置手順 ' 機能のアクティブ化でエラーが発生しました。 id フィールド [*Guid*] 機能で定義される [*Guid*] 現在のサイト コレクションまたはサブサイトが見つかりました。  
  
### <a name="resolution"></a>解像度  
 このエラーが発生するため、再利用可能なワークフローのインポート プロジェクト フィールド ID の競合の結果は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]タスク フォームのフィールド Id は変わりません。 元のワークフローが含まれる同じサーバーにインポートしたワークフローを展開する場合は、フィールド ID の競合が発生します。  
  
 この問題を解決するには、検索置換機能を使用して、インポートしたすべてのワークフロー ファイル内のフィールド ID 属性の値を変更する必要があります。  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>エラーが表示される、名前が変更されたインポートされるときにリスト インスタンスの実行
 この問題は、インポートしたリスト インスタンスの名前を変更した後、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で実行した場合に発生します。  
  
### <a name="error-message"></a>エラー メッセージ
 ビルド エラー: 配置手順 ' 機能のアクティブ化でエラーが発生しました: ファイル Template\Features\\[*プロジェクトのインポート*<em>機能</em>*名前*] \Files\Lists\\[*古い*<em>リスト名</em>] \Schema.xml が存在しません。  
  
### <a name="resolution"></a>解像度  
 リスト インスタンスをインポートすると、CustomSchema という名前の属性がリスト インスタンスの Elements.xml ファイルに追加されます。 Elements.xml には、リスト インスタンス用のカスタム schema.xml のパスが含まれます。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でリスト インスタンスの名前を変更すると、カスタム schema.xml の配置パスは変更されますが、CustomSchema 属性のパス値は更新されません。 その結果、リスト インスタンスが見つかりません、 *schema.xml*機能がアクティブな場合は、CustomSchema 属性で指定された古いパス内のファイル。  
  
 この問題を解決するには、更新の展開場所のパス、 *schema.xml* CustomSchema 属性内のファイル。  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint のデバッグ セッションが IIS によって終了しました
 ブレークポイントを設定する場合、この問題が発生します、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ソリューションの場合は、選択、 **F5**を実行し、90 秒より長くブレークポイントで維持するキー。  
  
### <a name="error-message"></a>エラー メッセージ
 デバッグ対象の Web サーバー プロセスは、インターネット インフォメーション サービス (IIS) によって停止されました。 IIS のアプリケーション プールの ping の設定を構成することによって、この問題を回避できます。 詳細については、ヘルプを参照してください。  
  
### <a name="resolution"></a>解像度  
 既定では、IIS アプリケーション プールは、アプリケーションから応答が返るまで 90 秒間待機した後、アプリケーションを閉じます。 このプロセスは、アプリケーションの "ping" として知られています。 この問題を解決するには、待機時間を増やすか、アプリケーションの ping を完全に無効にします。  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>IIS アプリケーション プールの設定にアクセスするには  
  
1.  IIS マネージャーを開きます。  
  
2.  **接続**ウィンドウでは、SharePoint サーバーのノードを展開して、選択し、**アプリケーション プール**ノード。  
  
3.  **アプリケーション プール**] ページで、SharePoint アプリケーション プール (通常は"SharePoint - 80") を選択し、[、**アクション**ウィンドウで、選択、**詳細設定**リンク。  
  
4.  IIS がタイムアウトまでの待機時間を大きくには、値を変更**Ping 最大応答時間 (秒)** 90 秒よりも大きい値にします。  
  
5.  IIS の ping を無効にするには設定**Ping の有効化**に**False**します。  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>SharePoint リストの孤立したインスタンスのまま自動取り消し
 この問題は、次の手順に従った場合に発生します。  
  
1.  リスト インスタンスがあるリスト定義を [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成します。  
  
2.  選択、 **F5**キーをソリューションを実行します。  
  
3.  デバッグを停止するか、SharePoint サイトを閉じます。  
  
4.  SharePoint サイトを再度開き、リスト インスタンスを開きます。  
  
### <a name="error-message"></a>エラー メッセージ
 '/' アプリケーションにサーバー エラーがあります。  
  
### <a name="resolution"></a>解像度  
 このエラーは、SharePoint ソリューションのデバッグ セッションを閉じた後、自動取り消し機能によってソリューションが取り消されたために発生します。 取り消しにより、リスト定義は SharePoint から削除されますが、リスト インスタンスは削除されません。 リスト インスタンスは、基になるリスト定義を必要とします。  
  
 この問題を解決するには、メニュー バーで、ソリューションの配置**ビルド** > **デプロイ**します。 (選択して、ソリューションをデバッグないでください、 **F5**キー)。次に、SharePoint 内のリスト インスタンスを削除します。  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>元の SharePoint ソリューションは、エクスポートされたバージョンに置き換え
 エクスポートした SharePoint ソリューションを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] にインポートした後、そのソリューションをエクスポート元のサイトに配置した場合、元の SharePoint ソリューションが置換されます。 この問題は、ソリューションの配置先を元のソリューションがアクティブ化されていないサーバーにすると、発生しません。  
  
### <a name="error-message"></a>エラー メッセージ
 なし。  
  
### <a name="resolution"></a>解像度  
 エクスポート元のサイトでソリューションが上書きされないようにするには、ソリューション ID の GUID と [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトにインポートしたすべての機能の機能 ID を変更します。  
  
## <a name="error-appears-when-debugging-starts"></a>デバッグの開始時にエラーが表示されます。
 Visual Studio で SharePoint ソリューションのデバッグを開始すると、特定のキーがディクショナリに存在しないので Visual Studio で Web.config ファイルを読み込むことができないというエラーが発生します。  
  
### <a name="error-message"></a>エラー メッセージ
 Web.config 構成ファイルを読み込むことができませんでした。 ファイルをチェックして、形式が正しくない XML 要素を修正した後、再試行してください。 次のエラーが発生しています: 特定のキーがディクショナリに存在しません。  
  
### <a name="resolution"></a>解像度  
 この問題を解決するには、Visual Studio 内の SharePoint プロジェクトの [サイト URL] プロパティの値が、Web アプリケーションの代替アクセス マッピング用の既定のゾーンに割り当てられた URL と一致することを確認します。 URL でイントラネットなどの他のゾーンを使用すると、エラーは解消されません。 プロジェクトのサイト URL と既定のゾーンの URL は一致している必要があります。 代替アクセス マッピングにアクセスするには、SharePoint 2010 サーバーの全体管理ユーティリティを開き、**アプリケーション管理**リンクし、 **Web アプリケーション**、選択、 **代替アクセス マッピングを構成する**リンク。 詳細については、次を参照してください。 [Web アプリケーションのゾーンを作成する](http://go.microsoft.com/fwlink/?LinkId=192274)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint のパッケージ化とデプロイをトラブルシューティングします。](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [ビルドし、SharePoint ソリューションのデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)  
  
  

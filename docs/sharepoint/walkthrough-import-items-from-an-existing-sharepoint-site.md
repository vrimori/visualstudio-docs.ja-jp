---
title: 'チュートリアル: 既存の SharePoint サイトからのアイテムのインポート |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: acd471ca33b0b3dc5057744e22c9d7e5a4c25980
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>チュートリアル: 既存の SharePoint サイトからのアイテムのインポート
  このチュートリアルに既存の SharePoint サイトからアイテムをインポートする方法を示します、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクト。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   カスタムのサイト内の列を追加することによって、SharePoint サイトをカスタマイズする (とも呼ばれる、*フィールド*です。  
  
-   SharePoint サイトを .wsp ファイルにエクスポートします。  
  
-   .Wsp ファイルをインポートする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].wsp インポート プロジェクトを使用して SharePoint。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
## <a name="customizing-a-sharepoint-site"></a>SharePoint サイトをカスタマイズします。  
 この例では作成されを新しいサイト内の列を追加し、後で使用するための別のサブサイトを作成することで、SharePoint サブサイトをカスタマイズします。 後で、最初のサブサイトを .wsp ファイルにエクスポートされ、2 番目のサブサイトに .wsp インポート プロジェクトを使用してカスタムのサイト内の列をインポートします。  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>作成し、SharePoint サイトをカスタマイズします。  
  
1.  Http:// などの Web ブラウザーを使用して SharePoint サイトを開きます。*システム名*/SitePages/Home.aspx です。  
  
2.  開くことによって、メインの SharePoint サイトに対してサブサイトを作成、**サイトの操作**メニュー選択して**新しいサイト**です。  
  
3.  サイトの **[作成]** ダイアログ ボックスで、選択、**空のサイト**型です。  
  
4.  **タイトル**ボックスに、入力**サイト列テスト 1**; で、 **URL 名**ボックスに、入力**columntest1**;、既定の他の設定をそのまま値。選択し、**作成**ボタンをクリックします。  
  
5.  メインのサイトにブラウザー内を移動する、サイトの作成後、http://*システム名*/SitePages/Home.aspx です。  
  
6.  ここでも、開くことによって、メインの SharePoint サイトに対して空白サブサイトを作成、**サイトの操作** メニューを選択する**新しいサイト**、選択し、**空のサイト**型です。  
  
7.  **タイトル**ボックスに、入力**サイト列テスト 2**; で、 **URL 名**ボックスに、入力**columntest2**;、既定の他の設定をそのまま値。選択し、**作成**ボタンをクリックします。  
  
8.  最初のサブサイトに戻る http://*SystemName*/columntest1/default.aspx です。  
  
9. **サイトの操作** メニューの 選択**サイトの設定**サイトの設定 ページを表示します。  
  
10. **ギャラリー**セクションで、選択、**サイト列**リンクします。  
  
11. 上部にある、**サイト内の列ギャラリー**ページで、選択、**作成**ボタンをクリックします。  
  
12. **列名**ボックスに、入力**テスト列**、他の既定値を保持し、、 **OK**ボタンをクリックします。  
  
13. **テスト列**列 カスタム列見出しギャラリーに表示されます、サイト列です。  
  
## <a name="exporting-the-sharepoint-site"></a>SharePoint サイトをエクスポートします。  
 SharePoint プロジェクト項目およびにインポートする要素を含んだ SharePoint セットアップ (.wsp) ファイルを次に、取得、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクト。 .Wsp ファイルがあるまだない場合、既存の SharePoint サイトから 1 つを作成する必要があります。 この例では、.wsp ファイルに既定の SharePoint サイトをエクスポートします。  
  
> [!IMPORTANT]  
>  次の手順を実行する実行時エラーが発生した場合は、SharePoint サイトにアクセス権があるシステム上の手順を実行する必要があります。  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>既存の SharePoint サイトをエクスポートするには  
  
1.  SharePoint サイトで次のように選択します。**サイト設定**上、**サイトの操作**サイト設定 ページを表示するタブです。  
  
2.  **サイトの操作**セクションで、サイトの設定ページの選択、**テンプレートとして保存サイト**リンクします。  
  
3.  **ファイル名**ボックスに、入力**ExampleSite**、し、、**テンプレート名**ボックスに、入力**例サイト**です。  
  
4.  この例では、選択したままに、**コンテンツを含む**チェック ボックスをオフします。  
  
     このボックスを選択した場合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].wsp ファイルにすべてのリストとドキュメント ライブラリ、およびその内容を保存します。 これはいくつかの状況で便利ですが、この例で必要はありません。  
  
5.  操作が正常に完了すると、選択、**ソリューション ギャラリー** .wsp ファイルを表示するリンクです。  
  
     後で、開いているソリューション ギャラリー ページを表示する、**サイトの操作** メニューの 選択**サイト設定**を選択、**トップ レベルのサイト設定 に移動**内のリンク、 **サイト コレクション管理**セクションで、クリックして、**ソリューション**内のリンク、**ギャラリー**セクションです。  
  
6.  ソリューション ギャラリーを選択して、 **ExampleSite**リンクします。  
  
7.  **ファイルのダウンロード** ダイアログ ボックスで、選択、**保存**ダウンロード フォルダーで、既定では、ローカル システム上のファイルを保存するボタンをクリックします。  
  
## <a name="importing-the-wsp-file"></a>.Wsp ファイルをインポートします。  
 (テスト列カスタム サイト列) を再利用する項目を含む .wsp ファイルがある場合は、これで、.wsp ファイルへのアクセスをインポートします。  
  
#### <a name="to-import-a-wsp-file"></a>.Wsp ファイルをインポートするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。 IDE は、Visual Basic 開発設定を使用して、メニュー バーでに設定されている場合は、選択**ファイル**、**新しいプロジェクト**です。  
  
2.  展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し、 **2010**ノード。  
  
3.  選択、 **SharePoint 2010 ソリューション パッケージのインポート**でテンプレート、**テンプレート**] ウィンドウで、WspImportProject1、として、プロジェクトの名前のままにし、[、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
4.  **デバッグのサイトとセキュリティ レベルを指定して** ページで、入力、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]先ほど作成した 2 番目の SharePoint サブサイトのです。 新しいカスタムの追加フィールド項目、http://*システム名*/columntest2、そのサブサイトにします。  
  
5.  **この SharePoint ソリューションの信頼レベルとは?**セクションで、として、選択を受け入れ**サンド ボックス ソリューションとして配置**。  
  
6.  **新しいプロジェクトのソースを指定** ページで以前で、.wsp ファイルを保存する、システム上の場所を参照して選択し、**次**ボタンをクリックします。  
  
    > [!NOTE]  
    >  選択した場合、**完了**.wsp ファイル内のすべての利用可能な項目は、このページのボタンがインポートされます。  
  
7.  **をインポートする項目の選択**ボックスで、すべてのリストを除くのチェック ボックスをオフに**テスト列**を選択し、**完了**ボタンをクリックします。  
  
     一覧には、多くのアイテムが含まれています、できますをすべてのチェック ボックスをオフに Space キーを選択し、チェック ボックスのみを横に、ctrl キーを一覧で、すべての項目を選択、**テスト列**項目。  
  
     インポート操作が完了したら、という名前の新しいプロジェクト**WspImportProject1**が作成されるという名前のフォルダーを格納している**フィールド**です。 このフォルダーにカスタム サイト内の列は、**テスト列**と Elements.xml 定義ファイルです。  
  
## <a name="deploying-the-project"></a>プロジェクトを配置します。  
 さらに、配置**WspImportProject1**サブサイト カスタム サイト内の列を表示するために以前作成したことの 2 番目の SharePoint にします。  
  
#### <a name="to-deploy-the-project"></a>プロジェクトを配置するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、F5 キーを展開し、.wsp インポート プロジェクトを実行します。  
  
2.  SharePoint サイトで開く、**サイトの操作** メニューを選択し**サイトの設定**サイト設定 ページを表示します。  
  
3.  **ギャラリー**セクションで、選択、**サイト列**リンクします。  
  
4.  下方向にスクロール、 **Custom Columns**セクションです。  
  
     最初の SharePoint サイトからインポートしたカスタムのサイト内の列が一覧に表示されることに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  
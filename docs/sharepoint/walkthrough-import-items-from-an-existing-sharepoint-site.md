---
title: 'チュートリアル: 既存の SharePoint サイトからアイテムをインポート |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 93e475a82ab862627c957a53ed2b3e2acae88b2d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834036"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>チュートリアル: 既存の SharePoint サイトからアイテムをインポートします。
  アイテムを既存の SharePoint サイトからインポートする方法についても説明、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクト。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
- カスタムのサイト内の列を追加することで、SharePoint サイトのカスタマイズ (とも呼ばれる、*フィールド*します。  
  
- SharePoint サイトを .wsp ファイルにエクスポートしています。  
  
- .Wsp ファイルをインポートする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].wsp プロジェクトのインポートを使用して SharePoint。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。  
  
-   Visual Studio  
  
## <a name="customize-a-sharepoint-site"></a>SharePoint サイトをカスタマイズします。
 この例では作成されを新しいサイト内の列を追加し、後で使用するための別のサブサイトを作成して SharePoint サブサイトをカスタマイズします。 後で、最初のサブサイトを .wsp ファイルにエクスポートされ、.wsp プロジェクトのインポートを使用して 2 つ目のサブサイトにカスタムのサイト内の列をインポートします。  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>作成して SharePoint サイトをカスタマイズするには  
  
1. Http:// などの Web ブラウザーを使用して SharePoint サイトを開きます。<em>システム名</em>/SitePages/Home.aspx します。  
  
2. 開き、メインの SharePoint サイトに対してサブサイトを作成、**サイトの操作**メニューを**新しいサイト**します。  
  
3. サイトの**作成** ダイアログ ボックスで、選択、**空のサイト**型。  
  
4. **タイトル**ボックスに、入力**サイト列テスト 1**; で、 **URL 名**ボックスに、入力**columntest1**; 他の設定を既定のままにします値。選択し、**作成**ボタンをクリックします。  
  
5. メインのサイトにブラウザー内を移動する、サイトを作成すると、 http://<em>システム名</em>/SitePages/Home.aspx します。  
  
6. 開き、メインの SharePoint サイトから空白サブサイトを作成、**サイトの操作**] メニューの [選択**新しいサイト**、クリックして、**空のサイト**型。  
  
7. **タイトル**ボックスに、入力**サイト列 Test 2**; で、 **URL 名**ボックスに、入力**columntest2**; 他の設定を既定のままにします値。選択し、**作成**ボタンをクリックします。  
  
8. 最初のサブサイトに戻る http://<em>SystemName</em>/columntest1/default.aspx します。  
  
9. **サイトの操作** メニューの 選択**サイト設定**サイト設定 ページを表示します。  
  
10. **ギャラリー**セクションで、選択、**サイト列**リンク。  
  
11. 上部にある、**サイト内の列ギャラリー**ページで、選択、**作成**ボタンをクリックします。  
  
12. **列名**ボックスに、入力**テスト列**、他の既定値を保持し、、 **OK**ボタン。  
  
13. **テスト列**列 カスタム列見出しギャラリーに表示、サイト列。  
  
## <a name="exporting-the-sharepoint-site"></a>SharePoint サイトをエクスポートします。
 SharePoint プロジェクト項目およびにインポートする要素を含む、SharePoint セットアップ (.wsp) ファイルを次に、取得、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクト。 .Wsp ファイルがあるまだない場合、既存の SharePoint サイトから 1 つを作成する必要があります。 この例では、.wsp ファイルに既定の SharePoint サイトをエクスポートします。  
  
> [!IMPORTANT]  
>  SharePoint サイトにアクセス権があるシステム上の手順を実行する必要が、次の手順を実行するランタイム エラーが発生した場合。  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>既存の SharePoint サイトをエクスポートするには  
  
1.  SharePoint サイトで次のように選択します。**サイト設定**上、**サイトの操作**サイト設定 ページを表示するタブ。  
  
2.  **サイトの操作**セクション サイト設定 ページの選択、**テンプレートとして保存サイト**リンク。  
  
3.  **ファイル名**ボックスに、入力**ExampleSite**、し、**テンプレート名**ボックスに、入力**例サイト**します。  
  
4.  この例では、選択したままに、**コンテンツを含む**チェック ボックスをオフします。  
  
     このボックスを選択した場合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].wsp ファイルにすべてのリストとドキュメント ライブラリ、およびその内容を保存します。 この機能は、いくつかの状況で役に立ちますが、この例では必要はありません。  
  
5.  操作が正常に完了すると、選択、**ソリューション ギャラリー** .wsp ファイルを表示するリンク。  
  
     以降では、開いているソリューション ギャラリー ページを表示する、**サイトの操作** メニューの 選択**サイト設定**、選択、**トップ レベルのサイト設定 に移動**のリンクを**サイト コレクションの管理**セクションで、クリックして、**ソリューション**のリンクを**ギャラリー**セクション。  
  
6.  ソリューション ギャラリーを選択して、 **ExampleSite**リンク。  
  
7.  **ファイルのダウンロード** ダイアログ ボックスで、選択、**保存**ダウンロード フォルダーで、既定で、ローカルのシステム上のファイルを保存するボタンをクリックします。  
  
## <a name="import-the-wsp-file"></a>.Wsp ファイルのインポート
 したので、 *.wsp* (テスト列カスタム サイト列) を再利用するには、インポートする項目を含むファイル、 *.wsp*ファイルへのアクセスします。  
  
#### <a name="to-import-a-wsp-file"></a>.Wsp ファイルをインポートするには  
  
1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、メニュー バーで、**ファイル** > **新規** > **プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。 お使いの IDE が Visual Basic 開発設定を使用して、メニュー バーに設定されている場合は、選択**ファイル** > **新しいプロジェクト**します。  
  
2. 展開、 **SharePoint**のどちらかのノード**Visual c#** または**Visual Basic**を選択し、 **2010**ノード。  
  
3. 選択、 **SharePoint 2010 ソリューション パッケージのインポート**テンプレート、**テンプレート**ウィンドウとして WspImportProject1、プロジェクトの名前のままにし、、 **OK**ボタンをクリックします。  
  
    **SharePoint カスタマイズ ウィザード**が表示されます。  
  
4. **デバッグのサイトとセキュリティのレベルを指定**ページで、入力、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]先ほど作成した 2 番目の SharePoint サブサイトの。 新しいカスタムの追加フィールド http:// で項目を<em>システム名</em>/columntest2、そのサブサイトにします。  
  
5. **この SharePoint ソリューションの信頼レベルとは何ですか?** セクションで、何も選択のままに**サンド ボックス ソリューションとして配置**します。  
  
6. **新しいプロジェクトのソースを指定** ページで、保存されているシステム上の場所を参照、 *.wsp*クリックして、ファイルの以前、**次**ボタン。  
  
   > [!NOTE]  
   >  選択した場合、**完了**で利用可能なすべての項目は、このページのボタン、 *.wsp*ファイルがインポートされます。  
  
7. **をインポートする項目の選択**ボックスに、すべてのリストを除くのチェック ボックスをオフに**テスト列**、選択し、**完了**ボタン。  
  
    選択することができます、一覧に多数の項目が含まれているため、 **Ctrl**+**A**一覧で、すべての項目を選択するキーがすべてのチェック ボックスをオフに Space キーを選択し、チェックのみを選択し、ボックスの横に、**テスト列**項目。  
  
    インポート操作が完了したら、という名前の新しいプロジェクト**WspImportProject1**が作成されるという名前のフォルダーを格納している**フィールド**します。 このフォルダーには、カスタムのサイト列**テスト列**とその定義ファイル*Elements.xml*します。  
  
## <a name="deploy-the-project"></a>プロジェクトを配置します。
 最後に、デプロイ**WspImportProject1** 2 番目の SharePoint にサブサイトをカスタムのサイト内の列を表示する前に作成しました。  
  
#### <a name="to-deploy-the-project"></a>プロジェクトを配置するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、選択、 **F5**デプロイして実行するキー、 *.wsp*プロジェクトをインポートします。  
  
2.  SharePoint サイトで開く、**サイトの操作** メニューの 選び、**サイト設定**サイト設定 ページを表示します。  
  
3.  **ギャラリー**セクションで、選択、**サイト列**リンク。  
  
4.  下へスクロールして、 **Custom Columns**セクション。  
  
     最初の SharePoint サイトからインポートしたカスタムのサイト内の列が一覧に表示されることに注意してください。  
  
## <a name="see-also"></a>関連項目
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成します。](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  

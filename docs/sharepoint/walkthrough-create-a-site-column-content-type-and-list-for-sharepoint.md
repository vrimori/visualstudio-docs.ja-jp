---
title: "チュートリアル: サイト内の列、コンテンツ タイプ、および SharePoint のリストを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 59dafe640428059b4c6772f79a23d5f0ccceaac7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成
  次の手順は、カスタムの SharePoint サイト列を作成する方法をデモンストレーション — または*フィールド*— だけでなく、サイト内の列を使用するコンテンツの種類。 新しいコンテンツの種類を使用するリストを作成する方法も示しています。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   [カスタムのサイト列を作成する](#BKMK_CreatingCustSiteCols)です。  
  
-   [カスタム コンテンツ タイプを作成する](#BKMK_CreateCustContType)です。  
  
-   [一覧を作成する](#BKMK_CreateList)です。  
  
-   [一覧を作成する](#BKMK_CreateList)です。  
  
-   [アプリケーションのテスト](#BKMK_TestApp)です。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows と SharePoint 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
##  <a name="BKMK_CreatingCustSiteCols"></a>カスタムのサイト列を作成します。  
 この例では、患者を病院で管理するために、リストを作成します。 最初に、SharePoint プロジェクトを作成する必要があります[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]サイト内の列を追加して、次のようにします。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ファイル**] メニューの [選択**新規**、**プロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、 **Visual c#**または**Visual Basic**、展開、 **SharePoint**ノード、をクリックして**2010**です。  
  
3.  **テンプレート** ウィンドウで、選択**SharePoint 2010 プロジェクト**、するプロジェクトの名前を変更**クリニック**を選択し、 **OK**ボタンをクリックします。  
  
     SharePoint 2010 プロジェクト テンプレートは、この例ではサイト内の列および後で追加される他のプロジェクト アイテムを格納するために使用する空のプロジェクトです。  
  
4.  **デバッグのサイトとセキュリティ レベルを指定して**ページで、新しい項目のカスタム フィールドを追加するローカル SharePoint サイトの URL を入力するか、既定の場所を使用して (`http://<`*SystemName*`>/)`.  
  
5.  **この SharePoint ソリューションの信頼レベルは何ですか。**セクションで、既定値を使用**サンド ボックス ソリューションとして配置**。  
  
     サンド ボックスの詳細については、ファーム ソリューションを参照してください[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
6.  選択、**完了**ボタンをクリックします。 プロジェクト一覧されるはずで**ソリューション エクスプ ローラー**です。  
  
#### <a name="to-add-site-columns"></a>サイト内の列を追加するには  
  
1.  新しいサイト内の列を追加します。 これを行うで**ソリューション エクスプ ローラー**、ショートカット メニューを開き、**クリニック**を選択し**追加**、**新しい項目の**です。  
  
2.  **新しい項目の追加** ダイアログ ボックスで、選択**Site Column**、名に変更**患者名**を選択し、**追加**ボタンをクリックします。  
  
3.  サイト内の列の Elements.xml ファイルをそのまま使用、**型**として設定**テキスト**、し、変更、**グループ**設定**クリニック サイト内の列**です。 完了したら、サイト内の列の Elements.xml ファイルは次の例のようになります。  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  同じ手順を使用して 2 つのサイト列プロジェクトに追加:**患者の ID** (種類 =「整数」) と**医師名前**(型 ="Text") です。 そのグループの値を設定**クリニック サイト内の列**です。  
  
##  <a name="BKMK_CreateCustContType"></a>カスタム コンテンツ タイプを作成します。  
 次に、コンテンツの種類を作成-連絡先コンテンツの種類に基づいて-前の手順で作成したサイト内の列が含まれています。 コンテンツの種類を既存のコンテンツの種類に基づいて、によって基本コンテンツの種類には、いくつかのサイト列、新しいコンテンツ タイプで使用するための時間を節約できます。  
  
#### <a name="to-create-a-custom-content-type"></a>カスタム コンテンツ タイプを作成するには  
  
1.  コンテンツ タイプをプロジェクトに追加します。 これを行うで**ソリューション エクスプ ローラー**、プロジェクト ノードを選択  
  
2.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
3.  いずれかで**Visual c#**または**Visual Basic**、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
4.  **テンプレート** ウィンドウを選択、**コンテンツ タイプ**テンプレート名に変更**患者情報**を選択し、**追加**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が開きます。  
  
5.  **このコンテンツの種類がから継承される基本コンテンツ タイプ**一覧で、選択**連絡先**でを選択し、新しいコンテンツ タイプを基になるコンテンツの種類として、 **を完了**ボタンをクリックします。  
  
     これを行うには、以前に定義したサイト内の列だけでなく、連絡先のコンテンツ タイプの他の役立つ可能性のあるサイト内の列にアクセスできます。  
  
6.  コンテンツ型の後にデザイナーが表示されたら、[、**列**] タブで、3 つのサイトの前に定義した列を追加:**患者名**、**患者 ID**、および**医師名前**です。 これらの列を追加するには、サイト列リストで最初のリスト ボックスを選択**表示名**、一度にいずれかの一覧で各サイト内の列を選択します。  
  
    > [!TIP]  
    >  サイト内の列をよりすばやくを選択するには、列の名前の最初の数文字を入力して一覧をフィルター処理します。  
  
7.  次の 3 つのカスタムのサイト列のほかにも追加、**コメント**サイト列 一覧からサイト内の列です。  
  
8.  選択、**必要**のチェック ボックスを**患者名**と**患者 ID**ようにするサイト内の列は必須フィールドです。  
  
9. **コンテンツ タイプ** タブで、コンテンツの種類名があるかどうかを確認**患者情報**に説明を変更および**患者の情報カード**です。  
  
10. 変更**グループ名**に**クリニックのコンテンツの種類**、し、他の設定が既定値のままにします。  
  
11. メニュー バーで、次のように選択します。**ファイル**、**すべて保存**、し、コンテンツ タイプ デザイナーを閉じます。  
  
##  <a name="BKMK_CreateList"></a>一覧を作成します。  
 ここで、新しいコンテンツの種類とサイト列を使用するリストを作成します。  
  
#### <a name="to-create-a-list"></a>一覧を作成するには  
  
1.  一覧をプロジェクトに追加します。 これを行うで**ソリューション エクスプ ローラー**、プロジェクト ノードを選択します。  
  
2.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
3.  いずれかで**Visual c#**または**Visual Basic**、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
4.  **テンプレート** ウィンドウを選択、**リスト**テンプレート名に変更**患者**を選択し、**追加**ボタンをクリックします。  
  
5.  ままにして、**に基づいてリストをカスタマイズする**として設定**既定 (空白)**を選択し、**完了**ボタンをクリックします。  
  
6.  リスト デザイナーで、**コンテンツの種類**を表示するボタン、**コンテンツの種類の設定** ダイアログ ボックス。  
  
7.  新しい行をクリックし、**患者情報**コンテンツのコンテンツの種類の一覧を入力し、選択、 **[ok]**ボタンをクリックします。  
  
     すべてのサイト列の追加これを行う、**患者情報**コンテンツの種類の一覧にします。  
  
8.  すべてのサイトの次を除く一覧内の列を削除します。  
  
    -   患者の ID  
  
    -   患者の名前  
  
    -   自宅電話番号  
  
    -   電子メール  
  
    -   医師名前  
  
    -   コメント  
  
9. **列の表示名**、空の行を選択して、カスタム リストで列を追加および名前を付けます**病院**です。 そのデータ型のままにして**単一行のテキスト**です。  
  
     カスタム リストの列は、この一覧にのみ適用されます。 カスタム リストの列を一覧に追加すると、新しいリスト コンテンツ タイプ、リストに追加されたすべての列を含むが作成され、既定のリストとして設定します。  
  
    > [!TIP]  
    >  サイト内の列の一覧から列を選択すると、既存のサイト列が使用されます。 ただし、リスト内の列を選択することがなく、列名の値を入力すると、カスタム リストの列が作成、一覧に同じ名前の列が既に存在する場合でもされます。  
  
     カスタム リストで列のデータ型の設定ではなく、必要に応じて、**単一行のテキスト**テーブルまたは別のリストからその値を取得するようを参照して、代わりにこの列のデータ型を設定できます。 参照列については、次を参照してください。 [SharePoint 2010 でリレーションシップを一覧](http://go.microsoft.com/fwlink/?LinkId=224994)と[参照やリスト リレーションシップ](http://go.microsoft.com/fwlink/?LinkID=224995)です。  
  
10. 横に、**患者の ID**と**患者名**ボックスで、**ために必要な**チェック ボックスをオンします。  
  
11. **ビュー**  タブで、ビューを作成する空の行を選択します。 入力**患者の詳細**です。  
  
     **ビュー**  タブで、SharePoint リストに表示する列を指定することができます。  
  
12. 新しい選択**患者の詳細**行をクリックして、**既定として設定**ボタンをクリックします。  
  
     新しいビューは、一覧の既定のビューで、ようになりました。  
  
13. 次の列を追加、**選択されている列**次の順序で一覧。  
  
    -   患者の ID  
  
    -   患者の名前  
  
    -   自宅電話番号  
  
    -   電子メール  
  
    -   医師名前  
  
    -   病院  
  
    -   コメント  
  
14. **プロパティ**一覧で、選択、**並べ替えやグループ化**プロパティの省略記号ボタンをクリックして![省略記号アイコン](../sharepoint/media/ellipsisicon.gif "省略記号アイコン")を表示する、**並べ替えやグループ化** ダイアログ ボックス。  
  
15. **列名**一覧で、選択**患者名**、ことを確認して、**並べ替え**に設定されている列**昇順**、をクリックして**[Ok]**ボタンをクリックします。  
  
##  <a name="BKMK_TestApp"></a>アプリケーションのテスト  
 カスタムのサイト列、コンテンツ タイプ、および一覧は、準備ができたら、SharePoint に配置したり、アプリケーション テストを実行できます。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  メニュー バーで、**[ファイル]**、**[すべてを保存]** の順に選択します。  
  
2.  F5 キーを選択してアプリケーションを実行します。  
  
     アプリケーションをコンパイルすると、およびその機能は、SharePoint に配置し、アクティブ化します。  
  
3.  クイック ナビゲーション バーで、選択、**患者**表示へのリンク、**患者** ボックスの一覧です。  
  
     リスト内の列名に入力したものと一致する必要があります、**ビュー** ] タブの [[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
4.  選択、**新しい項目の追加**患者の情報カードを作成するリンクです。  
  
5.  フィールドに情報を入力し、、**保存**ボタンをクリックします。  
  
     一覧に新しいレコードが表示されます。  
  
## <a name="see-also"></a>参照  
 [SharePoint のサイト列、コンテンツの種類、およびリストの作成](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [方法: カスタム フィールドの種類を作成します。](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [コンテンツの種類](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [列](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  
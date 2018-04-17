---
title: 'チュートリアル: SharePoint の Web パーツを作成する |Microsoft ドキュメント'
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
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e0659c354980eb302beb903d0107024882c6b160
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint"></a>チュートリアル: SharePoint の Web パーツを作成する

Web パーツを使用すると、ブラウザーから SharePoint サイト ページのコンテンツ、外観、および動作を直接変更できます。 このチュートリアルを使用して、Web パーツを作成する方法、 **Web パーツ**Visual Studio 2010 での項目テンプレート。

この Web パーツのデータ グリッドには従業員が表示されます。 従業員データを格納するファイルの場所を指定します。 また、マネージャーである従業員のみが一覧に表示されるように、データ グリッドにフィルターをかけることもできます。

このチュートリアルでは、次の作業について説明します。

- Visual Studio を使用して Web パーツを作成する**Web パーツ**項目テンプレート。

- Web パーツのユーザーが設定できるプロパティを作成する。 このプロパティでは、従業員データ ファイルの場所を指定します。

- コントロールを Web パーツ コントロール コレクションに追加することで Web パーツにコンテンツをレンダリングする。

- 呼ばれる、新しいメニュー項目を作成する、*動詞、*レンダリングされた Web パーツの動詞メニューに表示されます。 動詞を使用すると、Web パーツに表示されるデータを変更できます。

- SharePoint の Web パーツをテストする。

    > [!NOTE]
    > 次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- サポート対象エディションの Microsoft Windows および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。

- Visual Studio 2017 またはエディションの Visual Studio アプリケーション ライフ サイクル管理 (ALM)。

## <a name="creating-an-empty-sharepoint-project"></a>空の SharePoint プロジェクトの作成

まず、空の SharePoint プロジェクトを作成します。 使用して、後で、プロジェクトに Web パーツを追加するが、 **Web パーツ**項目テンプレート。

1. 開始[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を使用して、**管理者として実行**オプション。

2. メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。

3. **新しいプロジェクト**] ダイアログ ボックスで、展開、 **SharePoint** [クリックしてを使用する言語のノード、 **2010**ノード。

4. **テンプレート** ウィンドウで、選択**SharePoint 2010 プロジェクト**を選択し、 **OK**ボタンをクリックします。

     **SharePoint カスタマイズ ウィザード**が表示されます。 このウィザードを使用すると、プロジェクトのデバッグに使用するサイトや、ソリューションの信頼レベルを選択できます。

5. 選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックして既定のローカル SharePoint サイトです。

## <a name="adding-a-web-part-to-the-project"></a>Web パーツのプロジェクトへの追加

追加、 **Web パーツ**プロジェクト項目です。 **Web パーツ**項目は、Web パーツ コード ファイルを追加します。 後で、Web パーツ コード ファイルにコードを追加して、Web パーツのコンテンツをレンダリングします。

1. メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。

2. **新しい項目の追加** ダイアログ ボックスで、**インストールされたテンプレート** ウィンドウで、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。

3. SharePoint テンプレートの一覧で選択、 **Web パーツ**テンプレートを選択し、**追加**ボタンをクリックします。

     **Web パーツ**項目に表示されます**ソリューション エクスプ ローラー**です。

## <a name="rendering-content-in-the-web-part"></a>Web パーツのコンテンツのレンダリング

Web パーツに表示するコントロールを指定するには、Web パーツ クラスのコントロール コレクションにコントロールを追加します。

1. **ソリューション エクスプ ローラー**WebPart1.vb (Visual Basic) または WebPart1.cs (C# の場合) を開きます。

     コード エディターで Web パーツ コード ファイルが開きます。

2. Web パーツ コード ファイルの先頭に次のステートメントを追加します。

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. `WebPart1` クラスに次のコードを追加します。 このコードは、次のフィールドを宣言します。

    - Web パーツに従業員を表示するデータ グリッド。

    - データ グリッドのフィルターに使用するコントロール上に表示するテキスト。

    - データ グリッドでデータを表示できない場合、エラーを表示するラベル。

    - 従業員データ ファイルのパスを含む文字列。

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. `WebPart1` クラスに次のコードを追加します。 このコードで、`DataFilePath` というカスタム プロパティが Web パーツに追加されます。 カスタム プロパティとは、ユーザーが SharePoint で設定できるプロパティです。 このプロパティでは、データ グリッドの設定に使用される XML データ ファイルの場所を取得および設定します。

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. `CreateChildControls` メソッドを次のコードに置き換えます。 このコードは次のタスクを実行します。

    - 前の手順で宣言したデータ グリッドとラベルを追加します。

    - 従業員データを格納する XML ファイルにデータ グリッドをバインドします。

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. `WebPart1` クラスに次のメソッドを追加します。 このコードは次のタスクを実行します。

    - レンダリングされた Web パーツの Web パーツ動詞メニューに表示する動詞を作成します。

    - 動詞メニューの動詞を選択すると発生するイベントを処理します。 このコードでは、データ グリッドに表示される従業員一覧にフィルターをかけます。

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="testing-the-web-part"></a>Web パーツのテスト

プロジェクトを実行すると、SharePoint サイトが開きます。 Web パーツは SharePoint の Web パーツ ギャラリーに自動的に追加されます。 Web パーツは任意の Web パーツ ページに追加できます。

1. 次の XML をメモ帳ファイルに貼り付けます。 この XML ファイルには、Web パーツに表示されるサンプル データが含まれます。

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. メモ帳で、メニュー バーで、選択**ファイル**、**名前を付けて保存**です。

3. **名前を付けて保存** ダイアログ ボックスで、**型として保存**一覧で、選択**すべてのファイル**です。

4. **ファイル名**ボックスに、入力**data.xml**です。

5. 使用して任意のフォルダーを選択して、**フォルダーの参照**ボタンをクリックしを選択し、**保存**ボタンをクリックします。

6. Visual Studio で、選択、 **f5 キーを押して**キー。

     SharePoint サイトが開きます。

7. **サイトの操作**] メニューの [選択**オプションより**です。

8. **作成**ページで、選択、 **Web パーツ ページ**型をクリックし、**作成**ボタンをクリックします。

9. **新しい Web パーツ ページ** ページで、ページの名前を付けます**SampleWebPartPage.aspx**を選択し、**作成**ボタンをクリックします。

     [Web パーツ] ページが表示されます。

10. [Web パーツ] ページ上のゾーンを選択します。

11. ページの上部には、選択、**挿入** タブをクリックして、 **Web パーツ**ボタンをクリックします。

12. **カテゴリ** ウィンドウを選択、**カスタム**フォルダーを選択、 **WebPart1** Web パーツを選択し、**追加**ボタンをクリックします。

     ページに Web パーツが表示されます。

## <a name="testing-the-custom-property"></a>カスタム プロパティのテスト

Web パーツに表示するデータ グリッドを設定するには、各従業員に関するデータが格納された XML ファイルのパスを指定します。

1. Web パーツの右側に表示される矢印を選択し、 **Web パーツの編集**表示されるメニューから。

     Web パーツのプロパティを含むペインがページの右側に表示されます。

2. ウィンドウで、展開、 **その他**  ノードで、先ほど作成した XML ファイルのパスを入力、選択、**適用**ボタンをクリックしを選択し、 **ok**ボタンをクリックします。

     Web パーツに従業員一覧が表示されることを確認します。

## <a name="testing-the-web-part-verb"></a>Web パーツの動詞のテスト

Web パーツ動詞メニューに表示される項目をクリックすると、マネージャーではない従業員の表示と非表示が切り替わります。

1. Web パーツの右側に表示される矢印を選択し、 **マネージャーのみ**表示されるメニューから。

     Web パーツにマネージャーである従業員のみが表示されます。

2. もう一度、矢印を選択し、 **すべての従業員**表示されるメニューから。

     Web パーツにすべての従業員が表示されます。

## <a name="see-also"></a>関連項目

[SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)  
[方法: SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
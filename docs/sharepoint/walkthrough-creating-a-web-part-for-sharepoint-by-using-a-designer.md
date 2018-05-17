---
title: 'チュートリアル: デザイナーを使用して、SharePoint の Web パーツを作成する |Microsoft ドキュメント'
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: edc9665882caae64e0548a00507022f32f3b2bd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成

SharePoint サイトの Web パーツを作成すれば、ユーザーはブラウザーを使用して、そのサイトを構成するページのコンテンツ、外観、動作を直接変更できます。 このチュートリアルは、SharePoint を使用して web パーツを視覚的に作成する方法を示します**視覚的 Web パーツ**Visual Studio でのプロジェクト テンプレート。

ここで作成する Web パーツには、月間カレンダー ビューと、サイトで使用する各カレンダー リストのチェック ボックスが表示されます。 ユーザーがチェック ボックスをオンにすると、それに対応するカレンダー リストが月間カレンダー ビューに追加されます。

このチュートリアルでは、次の作業について説明します。

- 使用して web パーツを作成する、**視覚的 Web パーツ**プロジェクト テンプレート。
- Visual Studio の Visual Web Developer デザイナーを使用して Web パーツをデザインする
- Web パーツに配置したコントロールのイベントを処理するコードを追加する
- SharePoint で Web パーツをテストする

    > [!NOTE]
    > このチュートリアルに記載されている Visual Studio ユーザー インターフェイスの一部の要素は、お使いのコンピューターに実際に表示される名前や場所と異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- サポート対象エディションの Windows と SharePoint 参照してください[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。

## <a name="creating-a-web-part-project"></a>Web パーツ プロジェクトを作成する

使用して web パーツ プロジェクトを最初に、作成、**視覚的 Web パーツ**プロジェクト テンプレート。

1. 開始[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を使用して、**管理者として実行**オプション。

2. メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. **新しいプロジェクト** ダイアログ ボックスで、 **Visual c#** または**Visual Basic**、展開**Office/sharepoint**をクリックして**SharePoint ソリューション**カテゴリ。

4. テンプレートの一覧で選択、 **SharePoint 2013 - 視覚的 Web パーツ**テンプレートを選択し、 **[ok]** ボタンをクリックします。

     **SharePoint カスタマイズ ウィザード**が表示されます。 このウィザードでは、プロジェクトのデバッグ時に使用するサイトやソリューションの信頼レベルを指定できます。

5. **この SharePoint ソリューションの信頼レベルは何ですか?** セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。

6. 選択、**完了**ボタンをクリックして既定のローカル SharePoint サイトです。

## <a name="designing-the-web-part"></a>Web パーツをデザインする

コントロールを追加して web パーツをデザイン、**ツールボックス**Visual Web Developer デザイナーの画面にします。

1. Visual Web Developer デザイナーで、選択、**デザイン**デザイン ビューに切り替えるにはタブ。

2. メニュー バーで **[表示]**、**[ツールボックス]** の順に選択します。

3. **標準**のノード、**ツールボックス**を選択、 **CheckBoxList**を制御して、次の手順のいずれかを実行します。

    - ショートカット メニューを開き、 **CheckBoxList**コントロール を選択**コピー**デザイナーで、最初の行のショートカット メニューを開くしを選択し、**貼り付け**です。

    - ドラッグ、 **CheckBoxList**から制御、**ツールボックス**デザイナーで最初の行にコントロールを接続します。

4. 前の手順を繰り返します。ただし、ここでは、デザイナーの次の行へボタンを移動します。

5. デザイナーで、選択、 **Button1**ボタンをクリックします。

6. メニュー バーで、次のように選択します。**ビュー**、**プロパティ ウィンドウ**します。

     **プロパティ**ウィンドウが開きます。

7. **テキスト**、ボタンのプロパティを入力**更新**です。

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Web パーツ上のコントロールのイベントを処理する

ユーザーがマスター カレンダー ビューにカレンダーを追加できるようにするコードを追加します。

1. 次のいずれかの操作を実行します。

    - デザイナーをダブルクリックして、**更新**ボタンをクリックします。

    - **プロパティ**のウィンドウ、**更新** ボタンを選択して、**イベント**ボタンをクリックします。 **をクリックして**プロパティ、入力**Button1_Click**、し、Enter キーを押します。

     ユーザー コントロール コード ファイルがコード エディターで開き、`Button1_Click` イベント ハンドラーが表示されます。 その後、このイベント ハンドラーにコードを追加します。

2. ユーザー コントロール コード ファイルの先頭に次のステートメントを追加します。

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. `VisualWebPart1` クラスに次のコード行を追加します。 このコードでは、月間カレンダー ビュー コントロールを宣言します。

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. `Page_Load` クラスの `VisualWebPart1` メソッドを次のコードに置き換えます。 このコードは次のタスクを実行します。

    - 月間カレンダー ビューをユーザー コントロールに追加します。

    - サイト上の各カレンダー リストにチェック ボックスを追加します。

    - カレンダー ビューに表示される項目の種類ごとにテンプレートを指定します。

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. `Button1_Click` クラスの `VisualWebPart1` メソッドを次のコードに置き換えます。 このコードでは、選択したカレンダーの項目をマスター カレンダー ビューに追加します。

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="testing-the-web-part"></a>Web パーツをテストする

プロジェクトを実行すると、SharePoint サイトが開きます。 SharePoint の Web パーツ ギャラリーに Web パーツが自動的に追加されます。 このプロジェクトをテストするには次のタスクを実行します。

- 2 つのカレンダー リストそれぞれにイベントを追加します。
- Web パーツを Web パーツ ページに追加します。
- 月間カレンダー ビューに含めるリストを指定します。

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>サイト上のカレンダー リストにイベントを追加するには

1. Visual Studio で F5 キーを押します。

     SharePoint サイトが開き、および[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ページでクイック起動バーが表示されます。

2. クイック起動バーで、**を一覧表示**、選択、**カレンダー**リンクします。

     **カレンダー**ページが表示されます。

     した予定表のリンクが表示されない場合、クイック起動バーで、選択、**サイト コンテンツ**リンクします。 [サイト コンテンツ] ページが表示されていない場合、**カレンダー**項目は、1 つを作成します。

3. 予定表 ページで、1 日を選択し、、**追加**イベントを追加する、選択した日にリンクします。

4. **タイトル**ボックスに、入力**で既定のカレンダー イベント**を選択し、**保存**ボタンをクリックします。

5. 選択、**サイト コンテンツ**リンクをクリックして、**アプリの追加**を並べて表示します。

6. **作成**ページで、選択、**カレンダー** 、カレンダーの名前を順に選択して、**作成**ボタンをクリックします。

7. 新しいカレンダーにイベントを追加、イベントの名前を付けます**カスタム カレンダー イベント**を選択し、**保存**ボタンをクリックします。

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Web パーツを Web パーツ ページに追加するには

1. **サイト コンテンツ** ページで、開く、**サイト ページ**フォルダーです。

2. リボンで、次のように選択します。、**ファイル** タブで、開く、**新しいドキュメント** メニューを選択し、 **Web パーツ ページ**コマンド。

3. **新しい Web パーツ ページ** ページで、ページの名前を付けます**SampleWebPartPage.aspx**を選択し、**作成**ボタンをクリックします。

     Web パーツ ページが表示されます。

4. Web パーツ ページの最上位のゾーンを選択して、**挿入** タブをクリックして、 **Web パーツ**ボタンをクリックします。

5. 選択、**カスタム**フォルダーを選択、 **VisualWebPart1** web パーツをクリックして、**追加**ボタンをクリックします。

     ページに Web パーツが表示されます。 Web パーツに次のコントロールが表示されます。

    - 月間カレンダー ビュー

    - **更新**ボタンをクリックします。

    - A**カレンダー**チェック ボックスをオンします。

    - A**カスタム カレンダー**チェック ボックスをオンします。

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>月間カレンダー ビューに追加するリストを指定するには

Web パーツで、月間カレンダー ビューに含めるし、順に選択するカレンダーを指定、**更新**ボタンをクリックします。

指定したすべてのカレンダーのイベントが月間カレンダー ビューに表示されます。

## <a name="see-also"></a>関連項目

[SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)  
[方法: SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[チュートリアル: SharePoint の Web パーツを作成する](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)

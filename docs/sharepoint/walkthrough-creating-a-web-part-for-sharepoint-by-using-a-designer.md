---
title: 'チュートリアル: デザイナーを使用して、SharePoint の Web パーツの作成 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 146a1722f240895e0f508b0474df72f6f5f84ece
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870914"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>チュートリアル: デザイナーを使用して、SharePoint の web パーツを作成します。

SharePoint サイトの Web パーツを作成すれば、ユーザーはブラウザーを使用して、そのサイトを構成するページのコンテンツ、外観、動作を直接変更できます。 このチュートリアルは、SharePoint を使用して web パーツを視覚的に作成する方法を示します**視覚的 Web パーツ**Visual Studio でプロジェクト テンプレート。

ここで作成する Web パーツには、月間カレンダー ビューと、サイトで使用する各カレンダー リストのチェック ボックスが表示されます。 ユーザーがチェック ボックスをオンにすると、それに対応するカレンダー リストが月間カレンダー ビューに追加されます。

このチュートリアルでは、次の作業について説明します。

- 使用して web パーツの作成、**視覚的 Web パーツ**プロジェクト テンプレート。
- Visual Studio の Visual Web Developer デザイナーを使用して Web パーツをデザインする
- Web パーツに配置したコントロールのイベントを処理するコードを追加する
- SharePoint で Web パーツをテストする

    > [!NOTE]
    > このチュートリアルに記載されている Visual Studio ユーザー インターフェイスの一部の要素は、お使いのコンピューターに実際に表示される名前や場所と異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- サポート対象エディションの Windows と SharePoint

## <a name="create-a-web-part-project"></a>Web パーツのプロジェクトを作成します。

使用して web パーツ プロジェクトを最初に、作成、**視覚的 Web パーツ**プロジェクト テンプレート。

1. 開始[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を使用して、**管理者として実行**オプション。

2. メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. **新しいプロジェクト** ダイアログ ボックスで、いずれかで**Visual c#** または**Visual Basic**、展開**Office/sharepoint**、を選択し、**SharePoint ソリューション**カテゴリ。

4. テンプレートの一覧で選択、 **SharePoint 2013 - 視覚的 Web パーツ**テンプレートを選択し、 **[ok]** ボタンをクリックします。

     **SharePoint カスタマイズ ウィザード**が表示されます。 このウィザードでは、プロジェクトのデバッグ時に使用するサイトやソリューションの信頼レベルを指定できます。

5. **この SharePoint ソリューションの信頼レベルとは何ですか?** セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。

6. 選択、**完了**を既定のローカル SharePoint サイトを受け入れるようにボタンをクリックします。

## <a name="designing-the-web-part"></a>Web パーツをデザインする

コントロールを追加して web パーツをデザイン、**ツールボックス**Visual Web Developer デザイナーの画面にします。

1. Visual Web Developer デザイナーで、選択、**デザイン** タブのデザイン ビューに切り替えます。

2. メニュー バーで **[表示]**、**[ツールボックス]** の順にクリックします。

3. **標準**のノード、**ツールボックス**、選択、 **CheckBoxList**を制御して、次の手順のいずれかを実行します。

    - ショートカット メニューを開き、 **CheckBoxList**コントロールを選択**コピー**デザイナーで、最初の行のショートカット メニューを開き、選択し、**貼り付け**します。

    - ドラッグ、 **CheckBoxList**コントロールから、**ツールボックス**デザイナーで最初の行にコントロールを接続します。

4. 前の手順を繰り返します。ただし、ここでは、デザイナーの次の行へボタンを移動します。

5. デザイナーで、選択、 **Button1**ボタンをクリックします。

6. メニュー バーで、**ビュー** > **プロパティ ウィンドウ**します。

     **プロパティ**ウィンドウが開きます。

7. **テキスト**、ボタンのプロパティを入力**Update**します。

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Web パーツ上のコントロールのイベントを処理する

ユーザーがマスター カレンダー ビューにカレンダーを追加できるようにするコードを追加します。

1. 次のいずれかの操作を実行します。

   - デザイナーで、ダブルクリック、 **Update**ボタンをクリックします。

   - **プロパティ**のウィンドウ、 **Update**  ボタンを選択、**イベント**ボタンをクリックします。 **をクリックして**プロパティ、入力**Button1_Click**、し、Enter キーを押します。

     ユーザー コントロール コード ファイルがコード エディターで開き、`Button1_Click` イベント ハンドラーが表示されます。 後で、このイベント ハンドラーにコードを追加します。

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

## <a name="test-the-web-part"></a>Web パーツをテストします。

プロジェクトを実行すると、SharePoint サイトが開きます。 SharePoint の Web パーツ ギャラリーに Web パーツが自動的に追加されます。 このプロジェクトをテストするには、次のタスクを実行します。

- 2 つのカレンダー リストそれぞれにイベントを追加します。
- Web パーツを Web パーツ ページに追加します。
- 月間カレンダー ビューに含めるリストを指定します。

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>サイト上のカレンダー リストにイベントを追加するには

1. Visual Studio で、選択、 **F5**キー。

     SharePoint サイトが開き、および[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]クイック起動バーが、ページに表示されます。

2. クイック起動バーで **一覧**、選択、**カレンダー**リンク。

     **カレンダー**ページが表示されます。

     予定表のリンクが表示されない場合、クイック起動バーで、選択、**サイト コンテンツ**リンク。 [サイト コンテンツ] ページが表示されない場合は、**カレンダー**項目は、1 つを作成します。

3. [カレンダー] ページで、1 日を選択してから、**追加**イベントを追加する、選択した日にリンクします。

4. **タイトル**ボックスに、入力**既定の暦でイベント**、選択し、**保存**ボタンをクリックします。

5. 選択、**サイト コンテンツ**リンクをクリックして、**アプリの追加**を並べて表示します。

6. **作成**ページで、選択、**カレンダー**入力、カレンダーの名前を選択します、**作成**ボタンをクリックします。

7. 新しいカレンダーにイベントを追加、イベントの名前**カスタム カレンダー イベント**、選択し、**保存**ボタンをクリックします。

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Web パーツを Web パーツ ページに追加するには

1. **サイト コンテンツ** ページで、開く、**サイト ページ**フォルダー。

2. リボンで、選択、**ファイル** タブで、開く、**新しいドキュメント** メニューの 選択し、 **Web パーツ ページ**コマンド。

3. **新しい Web パーツ ページ** ページで、ページの名前**SampleWebPartPage.aspx**、選択し、**作成**ボタンをクリックします。

     Web パーツ ページが表示されます。

4. Web パーツ ページの最上位のゾーンの選択、**挿入**、タブをクリックして、 **Web パーツ**ボタンをクリックします。

5. 選択、**カスタム**フォルダーを選択、 **VisualWebPart1** web パーツを選び、**追加**ボタンをクリックします。

     ページに Web パーツが表示されます。 Web パーツに次のコントロールが表示されます。

    - 月間カレンダー ビュー

    - **Update**ボタンをクリックします。

    - A**カレンダー**チェック ボックスをオンします。

    - A**カスタム カレンダー**チェック ボックスをオンします。

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>月間カレンダー ビューに追加するリストを指定するには

Web パーツの指定が月間カレンダー ビューに含めるし、選択するカレンダー、 **Update**ボタン。

指定したすべてのカレンダーのイベントが月間カレンダー ビューに表示されます。

## <a name="see-also"></a>関連項目

[For SharePoint の web パーツを作成します。](../sharepoint/creating-web-parts-for-sharepoint.md)  
[方法: SharePoint web パーツを作成します。](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[チュートリアル: For SharePoint の web パーツを作成します。](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)

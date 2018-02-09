---
title: "Blend におけるオブジェクト スタイルの変更 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3073255564f81273fb6c6001538abf98d78766f7
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="modify-the-style-of-objects-in-blend"></a>Blend におけるオブジェクト スタイルの変更

オブジェクトをカスタマイズする最も簡単な方法は、**[プロパティ]** ペインにプロパティを設定することです。

設定または設定のグループを再利用する場合は、再利用可能なリソースを作成します。 再利用可能なリソースは、*スタイル*、*テンプレート*、またはカスタムの色のような簡単なものになります。 また、コントロールをその状態に基づいて異なる方法で表示することもできます。 たとえば、ユーザーがボタンをクリックするとボタンが緑色に変わるなどです。

## <a name="brushes-modify-the-appearance-of-an-object"></a>ブラシ: オブジェクトの外観を変更する

外観を変更する場合は、オブジェクトにブラシを適用します。

**短いビデオを見る:** ![再生ボタン](../designers/media/bldadminconsoleinitialconfigicon.PNG) [ブラシ エディター](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor)

### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>繰り返しイメージまたはパターンでオブジェクトを塗りつぶします。

繰り返しイメージやパターンでオブジェクトを塗りつぶすには、*タイル ブラシ*を使用します。

タイル ブラシを作成するには、初めに*イメージ ブラシ*、*描画ブラシ*、または*ビジュアル ブラシ*の各リソースを作成します。

イメージ ブラシを作成するには、イメージを使用します。 次の図は、イメージ ブラシ、並べて表示されたイメージ ブラシ、反転させたイメージ ブラシを示しています。

![イメージ ブラシ](../designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png) ![イメージ ブラシ (並べて表示)](../designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png) ![イメージ ブラシ (反転)](../designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png)

パスや図形など、ベクター描画を使用して、描画ブラシを作成します。 次の図は、描画ブラシ、並べて表示された描画ブラシ、反転させた描画ブラシを示しています。

![描画ブラシ](../designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png) ![描画ブラシ (並べて表示)](../designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png) ![描画ブラシ (反転)](../designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png)

ボタンなどのコントロールから、ビジュアル ブラシを作成します。 次の図は、ビジュアル ブラシと並べて表示されたビジュアル ブラシを示しています。

![表示ブラシ](../designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png) ![表示ブラシ (並べて表示)](../designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png)

**短いビデオを見る:** ![再生ボタン](../designers/media/bldadminconsoleinitialconfigicon.PNG) [タイル ブラシ](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes)

## <a name="styles-and-templates-create-a-consistent-look-and-feel-across-controls"></a>スタイルとテンプレート: コントロール全体で一貫したルック アンド フィールを作成する

コントロールの外観と動作を一度にデザインし、個別に維持しなくてもよいように、そのデザインを他のコントロールにも適用することができます。

**スタイルを使用する必要がありますか?**: 既定のプロパティ (ボタンの色など) を設定する場合は、*スタイル*を使用します。 スタイルを適用した後でも、コントロールを変更することができます。

**テンプレートを使用する必要がありますか?**: コントロールの構造を変更する場合は、*テンプレート*を使用します。 グラフィックまたはロゴをボタンに変換することを想像してください。 テンプレートを適用した後でコントロールを変更することはできません。

### <a name="create-a-template-or-style"></a>テンプレートまたはスタイルを作成する

テンプレートを作成する方法は 2 つあります。 アートボード上のオブジェクトをコントロールに変換したり、既存のコントロールをテンプレートのベースにすることができます。

任意のオブジェクトをコントロール テンプレートに変換するには、オブジェクトを選択してから、**[ツール]** メニューの **[コントロールの作成]** を選択します。

既存のコントロールをテンプレートのベースにする場合は、アートボード上のオブジェクトを選択します。 次に、アートボードの上部にある [階層リンク] ボタン、**[テンプレートの編集]**、**[コピーして編集]** または **[空アイテムの作成]** の順に選択します。

![[テンプレートの編集] メニュー](../designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png)

スタイルを作成するには、オブジェクトを選択してから、**[オブジェクト]** メニューで **[スタイルの編集]**、**[コピーして編集]** または **[空アイテムの作成]** の順に選択します。

- **[コピーして編集]** を選択すると、コントロールの既定のスタイルまたはテンプレートから開始します。

- **[空アイテムの作成]** を選択すると、最初から開始します。

**[現在のテンプレートの編集]** オプションは、既に作成したスタイルやテンプレートを編集する場合のみ表示されます。 まだ既定のシステム テンプレートを使用しているコントロールの場合は表示されません。

**[スタイル リソースの作成]** ダイアログ ボックスで、スタイルやテンプレートを後で使えるように指定するか、スタイルやテンプレートを特定の種類のコントロールすべてに適用することができます。

![[Style リソースの作成] ダイアログ ボックス](../designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png)

> [!NOTE]
> スタイルやテンプレートを全種類のコントロールに対して作成することはできません。 コントロールがスタイルやテンプレートをサポートしていない場合、[階層リンク] ボタンはアートボード上部に表示されません。
> メイン ドキュメントのスコープの編集に戻るには、**[スコープを**  に戻す]![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png) をクリックします。

### <a name="apply-a-style-or-template-to-a-control"></a>コントロールにスタイルまたはテンプレートを適用する

[[オブジェクトとタイムライン]](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-objects-and-timeline-panel) パネルでオブジェクトを右クリックして、**[テンプレートの編集]**、**[リソースの適用]** の順に選択します。

![[リソースの適用] メニュー](../designers/media/dc12debc-7711-47d9-84ce-10322a384397.png)

### <a name="restore-the-default-style-or-template-of-a-control"></a>コントロールの既定のスタイルまたはテンプレートを復元する

コントロールを選択し、[[プロパティ]](../designers/creating-a-ui-by-using-blend-for-visual-studio.md#tour-of-the-properties-panel) パネルで **[スタイル]** または **[テンプレート]** のプロパティの場所を探します。 **[詳細オプション]** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png) を選択して、ショートカット メニューで **[リセット]** をクリックします。

## <a name="visual-states-change-the-appearance-of-a-control-based-on-its-state"></a>表示状態: コントロールの状態に基づき、コントロールの外観を変更する

ユーザーとの対話に基づいて、コントロールの視覚的外観が異なります。 たとえば、ユーザーがボタンをクリックするとボタンが緑色になる、アニメーションを実行できるなどです。 遷移を使用すると、表示状態の間の時間を短縮または延長することができます。

![マウス ポイント状態](../designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png)

**短いビデオを見る:** ![再生ボタン](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF コントロールの状態を管理する](https://www.youtube.com/watch?v=m0PlkF5i6uw)

##  <a name="Resources"></a> リソース: 色、スタイル、テンプレートを作成し、後で再利用する

プロジェクトにあるあらゆるものをリソースに変換できます。 リソースは、 アプリケーションのさまざまな場所で再利用できるオブジェクトです。 たとえば、1 回色を作成し、リソースにしてから、その色を複数のオブジェクトに使用することができます。 これらすべてのオブジェクトの色を変更するには、単に色リソースを変更します。

![[色をリソースに変換] ボタン](../designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png) ![[色リソースの作成] ダイアログ ボックス](../designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png)

**短いビデオを見る:** ![再生ボタン](../designers/media/bldadminconsoleinitialconfigicon.PNG) [リソースの簡単なタッチ](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources)

## <a name="see-also"></a>関連項目

[Blend for Visual Studio を使用して UI を作成する](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
---
title: UI の作成 - Blend for Visual Studio
titleSuffix: ''
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e0a39bee4f44f0cf62c237ec9bb62135637a957
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923793"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Blend for Visual Studio を使用して UI を作成する

Blend for Visual Studio を使用すると、XAML ベースの Windows および Web アプリケーションを設計できます。 Visual Studio と同じ基本的な XAML デザイン環境を提供しているほか、アニメーションやビヘイビアーなどの高度なタスクを視覚的にデザインする機能が追加されています。 Blend と Visual Studio の比較については、[Visual Studio と Blend for Visual Studio で XAML をデザインする](../designers/designing-xaml-in-visual-studio.md)方法に関するページを参照してください。

Blend for Visual Studio は、Visual Studio のコンポーネントです。 Blend をインストールするには、**Visual Studio インストーラー**で、**[ユニバーサル Windows プラットフォーム開発]** または **[.NET デスクトップ開発]** のいずれかのワークロードを選択します。 これらの両方のワークロードに、Blend for Visual Studio コンポーネントが含まれます。

![UWP のワークロード コンポーネント](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![.NET デスクトップ開発のワークロード コンポーネント](media/installer-dotnet-desktop.png)

Blend for Visual Studio を初めてご使用になる場合は、このワークスペース特有の機能に慣れるために少し時間を取ってください。 このトピックでは、短いツアーにお連れします。

> [!NOTE]
> アートボード、**[ドキュメント アウトライン]** ウィンドウ、**[デバイス]** ウィンドウなどの共有デザイン機能のツアーについては、「[XAML デザイナーを使用した UI の作成](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)」を参照してください。

## <a name="tour-of-the-tools-panel"></a>[ツール] パネルのツアー

Blend for Visual Studio の **[ツール]** パネルは、アプリケーションのオブジェクトの作成と変更に使用します。 パネルにあるツールを選択してアートボード上でマウスを動かすと、オブジェクトを描画できます。

![ツール パネル](../designers/media/blend5toolspanel.png)

|||||
|-|-|-|-|
|![選択ツール](../designers/media/b1_1.png)|**選択ツール** オブジェクトとパスを選択します。<br /><br /> **個別選択**ツールを使用すると、入れ子状のオブジェクトやパス セグメントを選択できます。|![吹き出し A](../designers/media/b5_label_a.png)|**グラデーション ツールとブラシ ツール**|
|![ビュー ツール](../designers/media/b1_2.png)|**表示ツール** 手のひらツールでの移動、ズームなど、アートボードの表示の調整を行います。|![吹き出し B](../designers/media/b5_label_b.png)|**パス ツール**|
|![ブラシ ツール](../designers/media/b1_3.png)|**ブラシ ツール** ブラシの変換や、オブジェクトのペイントを行ったり、あるオブジェクトの属性を選択して別のオブジェクトに適用するなど、オブジェクトの表示属性を操作します。|![吹き出し C](../designers/media/b5_label_c.png)|**シェイプ ツール**|
|![オブジェクト ツール](../designers/media/b1_4.png)|**オブジェクト ツール** パス、図形、レイアウト パネル、テキスト、コントロールなど、よく使用するオブジェクトをアートボード上で描画します。|![吹き出し D](../designers/media/b5_label_d.png)|**レイアウト パネル**|
|![アセット ツール](../designers/media/b1_5.png)|**アセット ツール** **[アセット]** パネルにアクセスし、ライブラリから最近使用したアセットを表示します。|![吹き出し E](../designers/media/b5_label_e.png)|**テキスト コントロール**|
|||![吹き出し F](../designers/media/b5_label_f.png)|**コモン コントロール**|

**短いビデオを見る:**![インストール済みフィーチャーの構成](../designers/media/bldadminconsoleinitialconfigicon.png) [ツール バー](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4)。

## <a name="tour-of-the-assets-panel"></a>[アセット] パネルのツアー

**[アセット]** パネルには、すべてのコントロールが用意されています (Visual Studio の **[ツールボックス]** に似ています)。 また、コントロールのほかに、スタイル、メディア、ビヘイビアー、効果など、アートボードに追加できるすべてのものが **[アセット]** パネルに用意されています。

![アセット パネル](../designers/media/blend5_assets_panel.png)

|||
|-|-|
|![](../designers/media/b1_1.png)|**[検索] ボックス** **[検索]** ボックスに入力することにより、アセットの一覧を絞り込みます。|
|![グリッド モードとリスト モード](../designers/media/b1_2.png)|**グリッド モードとリスト モード** アセットの表示モードを、**グリッド モード**または**リスト モード**に切り替えます。|
|![アセットのカテゴリ](../designers/media/b1_3.png)|**アセットのカテゴリ** カテゴリまたはサブカテゴリをクリックすると、そのカテゴリに属するアセットが表示されます。|
|![スタイル](../designers/media/b1_4.png)|**スタイル** リソース ディクショナリに含まれるすべてのスタイルを表示します。|
|![説明](../designers/media/b1_5.png)|**説明** 選択したカテゴリまたはサブカテゴリの説明が表示されます。|

## <a name="tour-of-the-objects-and-timeline-panel"></a>[オブジェクトとタイムライン] パネルのツアー

このパネルを使用すると、アートボード上のオブジェクトを整理して、必要な場合はアニメーション化できます。

![アニメーション モードの [オブジェクトとタイムライン] パネル](../designers/media/b5_object_timeline_animation.png)

|||
|-|-|
|![オブジェクト ビュー](../designers/media/b1_1.png)|**オブジェクト ビュー** ドキュメントをツリー表示します。 さまざまなレベルの詳細にドリル ダウンできます。 さらに、アートボード上のオブジェクトを整理するレイヤーを追加することもできます。 そのように、グループとしてロックし、非表示にすることができます。|
|![記録モードのインジケーター](../designers/media/b1_2.png)|**記録モード インジケーター** タイムラインでプロパティの変更を記録中かどうかを表示します。|
|![ストーリーボードの一覧](../designers/media/b1_3.png)|**ストーリーボードの一覧** 作成済みのストーリーボードが一覧表示されます。|
|![ストーリーボードを閉じる](../designers/media/b1_4.png)|**ストーリー ボードを閉じる** 現在のストーリー ボードを閉じます。|
|![ストーリーボードのオプション](../designers/media/b1_5.png)|**ストーリー ボードのオプション** ストーリー ボードの作成、複製、動作の取り消し、削除、名前の変更を行ったり、ストーリー ボードを閉じます。|
|![再生コントロール](../designers/media/b1_6.png)|**再生コントロール** タイムライン上を移動します。 再生ヘッドは、ドラッグしてタイムライン上を移動する (*スクラブする*) こともできます。|
|![スコープを戻す](../designers/media/b1_7.png)|**スコープを戻す** オブジェクト ビューのスコープを前のルート オブジェクトまたは前のスコープに戻します。 スタイルまたはテンプレートを変更する場合にのみ、これを実行できます。|
|![キーフレームの記録](../designers/media/b1_8.png)|**キーフレームの記録** 現時点で選択されているオブジェクトのプロパティのスナップショットを記録します。|
|![スナップ オプション](../designers/media/b1_9.png)|**スナップ オプション** タイムラインのスナップ、スナップの精度を設定し、タイムラインのスナップをオフにします。|
|![表示/非表示、ロック/ロック解除](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**表示/非表示**、**ロック/ロック解除** オブジェクト ビューの表示と非表示、ロックとロック解除を切り替えます。|
|![タイムライン上の再生ヘッドの位置](../designers/media/b1_11.png)|**タイムライン上の再生ヘッドの位置** 現在の時刻をミリ秒単位で表示します。 このフィールドに時間値を直接入力し、特定の時点に移動することもできます。 精度は **[スナップ オプション]** に設定したスナップ精度によって決まります。|
|![再生ヘッド](../designers/media/b1_12.png)|**再生ヘッド** アニメーションがどの時点にあるかを示します。 タイムラインで再生ヘッドをドラッグして、アニメーションをプレビューできます。|
|![タイムラインに設定されたキーフレーム](../designers/media/b1_13.png)|**タイムラインに設定されたキーフレーム** 特定の時点でのプロパティの値を変更します。|
|![オブジェクトの順序の変更](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**オブジェクトの順序の変更** オブジェクトの表示順序を設定します。 構造ビューのオブジェクトを Z 軸を基準 (手前から奥)、またはマークアップ順 (**XAML** での表示順) に整列させるには、このボタンをクリックします。|
|![タイムラインのズーム](../designers/media/b1_15.png)|**タイムラインのズーム** タイムラインのズーム解像度を設定します。 ズーム インでは、アニメーションを詳細に編集できます。ズーム アウトすると、長い再生時間にわたる動作の概要が表示されます。 ズーム インしても、目的の位置にキーフレームを設定できない場合は、スナップ精度が十分高く設定されていることを確認してください。|
|![吹き出し 16](../designers/media/b5_label_16.png)|**タイムライン構成領域** タイムラインを表示するとともに、キーフレームをドラッグするかショートカット メニューを使用してキーフレームを移動します。|

## <a name="tour-of-the-properties-panel"></a>[プロパティ] パネルのツアー

オブジェクトのプロパティを表示して変更するには、このパネルを使用します。 また、アートボード上で直接設定することもできます。 この場合、プロパティの変更が **[プロパティ]** パネルに反映されます。

![プロパティ パネル](../designers/media/blend5_properties_panel.png)

**[カテゴリ]** プロパティのカテゴリを展開し、折りたたみます。 カテゴリの詳細を表示するには **[展開]** ![展開](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png) をクリックし、非表示にするには **[折りたたみ]** ![折りたたみ](../designers/media/b5_collapse_button.png) をクリックします。

|||
|-|-|
|![名前と種類](../designers/media/b1_1.png)|**[名前] と [種類]** 選択したオブジェクトのアイコン、名前、種類が表示されます。|
|![並べ替え](../designers/media/b1_2.png)|**[並べ替え]** プロパティを名前、ソース、またはカテゴリごとにアルファベット順に並べ替えます。|
|![ブラシのプロパティ](../designers/media/b1_3.png)|**ブラシのプロパティ** Fill、Stroke、Foreground など、ブラシの視覚的なプロパティを設定します。|
|![カラー エディター](../designers/media/b1_4.png)|**カラー エディター** 単色ブラシおよびグラデーション ブラシで使用します。|
|![カラー ピッカー](../designers/media/b1_5.png)|**カラー ピッカー** 色を選択します。|
|![カラー チップ](../designers/media/b1_6.png)|**カラー チップ** 初期の色、現在の色、および最後の色が表示されます。|
|![スポイト ツール](../designers/media/b1_7.png)|**スポイト ツール** 画面上の任意の要素の色を使用します。 **色スポイト**は、**単色ブラシ**が選択されているときに使用できます。 **[グラデーションのスポイト]** は、**[グラデーション ブラシ]** が選択されているときに使用できます。|
|![プロパティおよびイベント](../designers/media/b1_8.png)|**プロパティとイベント** 選択された要素に対してプロパティを設定したり、イベントを選択します。|
|![検索ボックス](../designers/media/b1_9.png)|**[検索] ボックス** プロパティを検索します。 **[検索]** ボックスに入力することで、表示されるプロパティをフィルター処理します。|
|![ブラシ エディターのタブ](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**ブラシ エディターのタブ** ブラシ エディターを選択する場合に使用します。 **ブラシなし**、**単色ブラシ**、**グラデーション ブラシ**、**タイル ブラシ**、または**ブラシ リソース**から選択できます。|
|![色リソース](../designers/media/b1_11.png)|**色リソース** 異なるプロパティにまったく同じ色を適用します。 **[色リソース]** タブには、**[ローカル リソース]** と **[システム リソース]** が表示されます。|
|![RGB 色空間](../designers/media/b1_12.png)|**RGB 色空間** **[R]**、**[G]**、または **[B]** (赤、緑、青) の各数値エディターの値を調整して色を変更します。|
|![アルファ チャネル](../designers/media/b1_13.png)|**アルファ チャネル** **[A]** の横にある数値エディターを使用してアルファ値を変更します。|
|![色をリソースに変換](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**色をリソースに変換** 選択した色を色リソースに変換します。 色リソースは、[色リソース] タブをクリックした場合に使用できます。|
|![](../designers/media/b1_15.png)|**16 進数値** 表示されている色を表す 16 進数値が表示されます。|
|![吹き出し 16](../designers/media/b5_label_16.png)|**グラデーション スライダー** グラデーション ブラシが選択されている場合にのみ表示されます。|
|![詳細設定プロパティの表示](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png)|**詳細設定プロパティの表示** 使用頻度が低いプロパティのカテゴリを表示します。|

**短いビデオを見る:**![インストール済みフィーチャーの構成](../designers/media/bldadminconsoleinitialconfigicon.png) [[プロパティ] パネル](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7)。

## <a name="see-also"></a>関連項目

- [コントロールの挿入およびそのビヘイビアーの変更](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [オブジェクトのアニメーション化](../designers/animate-objects-in-xaml-designer.md)
- [図形とパスの描画](../designers/draw-shapes-and-paths.md)
- [Visual Studio および Blend for Visual Studio での XAML の設計](../designers/designing-xaml-in-visual-studio.md)

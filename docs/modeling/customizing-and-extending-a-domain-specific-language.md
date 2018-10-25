---
title: ドメイン固有言語のカスタマイズおよび拡張
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a49d9998aa319e66c22baa345864bc473f733c87
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816703"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>ドメイン固有言語のカスタマイズおよび拡張
Visual Studio のモデリングと視覚エフェクト SDK (VMSDK) は、いくつかのレベルをモデリング ツールを定義することができますを提供します。

1.  DSL 定義図を使用して、ドメイン固有言語 (DSL) を定義します。 図の表記法、読み取り可能な XML 形式では、コードとその他の成果物を生成するために必要な基本的なツールと DSL をすばやく作成できます。

     詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。

2.  DSL 定義のより高度な機能を使用して DSL を細かく調整します。 たとえば、ユーザーが要素を作成するときに表示されるその他のリンクを行うことができます。 これらの手法は、DSL 定義で実現されるほとんどの場合と、数行プログラム コードの一部が必要です。

3.  プログラム コードを使用して、モデリング ツールを拡張します。 VMSDK は特に、DSL 定義から生成されるコードにより、拡張機能を容易に統合できるようにすることを目的としています。  詳細については、次を参照してください。[ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)します。

> [!NOTE]
>  DSL 定義ファイルを更新したら、忘れずにクリックして**すべてのテンプレートの変換**ソリューションの再構築する前に、ソリューション エクスプ ローラーのツールバー。

## <a name="customShapes"></a> このセクションでは

|この効果を実現するには|このトピックを参照してください。|
|-|-|
|図形の色とスタイルのプロパティを設定するユーザーを許可します。|シェイプまたはコネクタ クラスを右クリックし、**公開追加**項目をクリックします。<br /><br /> 参照してください[ダイアグラムの外観のカスタマイズ](../modeling/customizing-presentation-on-the-diagram.md)します。|
|モデル要素の種類のクラス ダイアグラムで、初期の高さと幅、色、ツールヒントなどのプロパティを共有するようになります。|図形またはコネクタ クラス間の継承を使用します。 派生図形と派生ドメイン クラス間のマッピングは、親のマッピングの詳細を継承します。<br /><br /> または、同じ図形クラスに別のドメイン クラスをマップします。|
|モデル要素のクラスは、さまざまな図形のコンテキストで表示されます。|同じドメイン クラスには、複数の図形クラスをマップします。 ソリューションをビルドするときに次のエラー レポートと使用するには、どのような形状を決定する、要求されたコードを指定します。|
|図形の色やフォントなどの他の機能は、現在の状態を示します。|参照してください[モデルへの反映には、図形とコネクタの更新](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)します。<br /><br /> 公開されているプロパティを更新するルールを作成します。 参照してください[ルールには、モデル内の変更が反映されるまで](../modeling/rules-propagate-changes-within-the-model.md)します。<br /><br /> または、OnAssociatedPropertyChanged() を使用して、リンクの矢印やフォントなどに公開されている機能を更新します。|
|図形の変更状態を示すためのアイコン。|[DSL 詳細] ウィンドウでマッピング デコレーターの可視性を設定します。 同じ位置にいくつかのイメージ デコレーターを見つけます。 参照してください[モデルへの反映には、図形とコネクタの更新](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)します。<br /><br /> または、オーバーライド`ImageField.GetDisplayImage()`します。 例を参照してください。<xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>します。|
|任意の図形の背景イメージを設定します。|固定の ImageField を追加する InitializeInstanceResources() をオーバーライドします。 参照してください[ダイアグラムの外観のカスタマイズ](../modeling/customizing-presentation-on-the-diagram.md)します。|
|任意の深さに入れ子になったシェイプ|再帰的なツリーの埋め込みを設定します。 図形を含む BoundsRules を定義します。 参照してください[ダイアグラムの外観のカスタマイズ](../modeling/customizing-presentation-on-the-diagram.md)します。|
|要素の境界に固定のポイントにコネクタをアタッチします。|図上の小さなポートによって表される、埋め込みターミナル要素を定義します。 BoundsRules を使用して、場所に、ポートを修正します。 回路図のサンプルを参照してください。 [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)します。|
|テキスト フィールドには、その他の値から派生した値が表示されます。|テキスト デコレータを計算またはカスタム ストレージ ドメイン プロパティにマップします。 詳細については、次を参照してください。[計算とストレージのカスタム プロパティ](../modeling/calculated-and-custom-storage-properties.md)します。|
|モデル要素間、または図形間の変更を反映します。|参照してください[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)です。|
|ストアの外部の他の Visual Studio 拡張機能などのリソースに変更を反映します。|参照してください[イベント ハンドラーには、モデルの外部で変更が反映されるまで](../modeling/event-handlers-propagate-changes-outside-the-model.md)します。|
|[プロパティ] ウィンドウには、関連する要素のプロパティが表示されます。|プロパティの転送を設定します。 参照してください[プロパティ ウィンドウのカスタマイズ](../modeling/customizing-the-properties-window.md)します。|
|プロパティのカテゴリ|[プロパティ] ウィンドウは、カテゴリと呼ばれるセクションに分かれています。 設定、**カテゴリ**のドメインのプロパティ。 同じカテゴリの名前を持つプロパティは、同じセクションに表示されます。 設定することも、**カテゴリ**のリレーションシップのロール。|
|ドメインのプロパティへのユーザー アクセスの制御|設定**参照可能**ドメイン プロパティが実行時に、[プロパティ] ウィンドウに表示されていることを防止する場合は false。 テキスト デコレータにもマップできます。<br /><br /> **Is UI Read Only**ドメイン プロパティを変更できないようにします。<br /><br /> ドメイン プロパティにプログラムのアクセスは影響はありません。|
|名前、アイコン、および DSL のモデル エクスプ ローラー内のノードの可視性を変更します。|参照してください[モデル エクスプ ローラーのカスタマイズ](../modeling/customizing-the-model-explorer.md)します。|
|コピー、切り取りと貼り付けを有効にします。|設定、**コピー貼り付けを有効にする**のプロパティ、**エディター** DSL エクスプ ローラーでノード。|
|要素がコピーされるたびに、参照のリンクとそのターゲットをコピーします。 たとえば、項目に添付されたコメントをコピーします。|設定、**コピーの伝達**(DSL 定義図で、ドメイン リレーションシップの一方の側にある行で表されます)、ソース ロールのプロパティ。<br /><br /> 複雑な効果を実現する ProcessOnCopy をオーバーライドするコードを記述します。<br /><br /> 参照してください[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。|
|削除、親の変更、または要素が削除されたときに、関連する要素を再リンクします。|設定、**削除の伝達**リレーションシップ ロールの値。 複雑な効果は、オーバーライド`ShouldVisitRelationship`と`ShouldVisitRolePlayer`メソッド、`MyDslDeleteClosure`で定義されたクラス**DomainModel.cs**<br /><br /> 参照してください[削除動作のカスタマイズ](../modeling/customizing-deletion-behavior.md)|
|図形のレイアウトと外観をコピーし、ドラッグ アンド ドロップが保持されます。|シェイプとコネクタを追加、コピーする`ElementGroupPrototype`します。 オーバーライドする最も便利なメソッドは `ElementOperations.CreateElementGroupPrototype()`<br /><br /> 参照してください[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。|
|現在のカーソル位置など、選択した場所に図形を貼り付けます。|オーバーライド`ClipboardCommandSet.ProcessOnCopy()`の場所に固有のバージョンを使用する`ElementOperations.Merge().`を参照してください[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。|
|貼り付け時にその他のリンクを作成します。|Override ClipboardCommandSet.ProcessOnPasteCommand()|
|ドラッグを有効にして、この図は、その他の Dsl と Windows から要素を削除します。|参照してください[方法: ドラッグ アンド ドロップ ハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|親をドラッグした場合とは、図形やポートなどの子の図形にドラッグしたりするためのツールを許可します。|ターゲット オブジェクト クラスの親にドロップされたオブジェクトを転送するには、要素マージ ディレクティブを定義します。 参照してください[要素の作成と移動をカスタマイズする](../modeling/customizing-element-creation-and-movement.md)します。|
|図形またはその他のリンクを図形にドラッグするツールを許可するか、作成されたオブジェクト。 たとえば、リンクすることが項目上にドロップされるコメントを許可するには、です。|ターゲット ドメイン クラスに要素マージ ディレクティブを定義し、生成するリンクを定義します。 複雑な場合は、カスタム コードを追加することができます。 参照してください[要素の作成と移動をカスタマイズする](../modeling/customizing-element-creation-and-movement.md)します。|
|1 つのツールを使用して要素のグループを作成します。 たとえば、固定ポートのセットを持つコンポーネント。|ToolboxHelper.cs 内のツールボックスの初期化メソッドをオーバーライドします。 要素グループ プロトタイプ (EGP) が、要素とそのリレーションシップ リンクを含むを作成します。 参照してください[ツールおよびツールボックスのカスタマイズ](../modeling/customizing-tools-and-the-toolbox.md)します。<br /><br /> EGP にプリンシパルとポート図形を含めるか、EGP がインスタンス化されるときに、ポート シェイプを配置する BoundsRules を定義します。 参照してください[BoundsRules によってシェイプの位置とサイズが制限](../modeling/boundsrules-constrain-shape-location-and-size.md)します。|
|1 つの接続ツールを使用して、複数の種類のリレーションシップのインスタンスを作成します。|リンク接続ディレクティブ (LCD) をツールによって呼び出される接続ビルダーに追加します。 Lcd では、2 つの要素の型からリレーションシップの種類を決定します。 この要素の状態に依存性を高めるには、カスタム コードを追加することができます。 参照してください[ツールおよびツールボックスのカスタマイズ](../modeling/customizing-tools-and-the-toolbox.md)します。|
|固定ツール - ユーザーは、連続して多くの図形またはコネクタを作成する任意のツールをダブルクリックすることができます。|DSL エクスプ ローラーで選択、`Editor`ノード。 [プロパティ] ウィンドウで次のように設定します。**ツールボックス アイテムの固定を使用して**します。|
|メニュー コマンドを定義します。|参照してください[方法: 標準メニュー コマンドを修正](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|検証規則を使って、モデルを制限します。|参照してください[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)|
|DSL からコード、構成ファイル、またはドキュメントを生成します。|[ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)|
|モデルを保存する方法をカスタマイズするファイル。|参照してください[ファイル格納処理および XML シリアル化をカスタマイズします。](../modeling/customizing-file-storage-and-xml-serialization.md)|
|モデルをデータベースまたはその他のメディアに保存します。|オーバーライド*YourLanguage*DocData<br /><br /> 参照してください[ファイル格納処理および XML シリアル化をカスタマイズします。](../modeling/customizing-file-storage-and-xml-serialization.md)|
|1 つのアプリケーションの一部として動作するために、いくつかの Dsl を統合します。|参照してください[Visual Studio modelbus によるモデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)します。|
|サード パーティが拡張する DSL を許可して、拡張機能を制御します。|[MEF による DSL の拡張](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL ライブラリによる DSL 間でのクラスの共有](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [ロック ポリシーの定義と読み取り専用セグメントの作成](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>関連項目

- [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
---
title: "カスタマイズとドメイン固有言語を拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7617deb73ecaec835b0100d243b75bc26fd54a17
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>ドメイン固有言語のカスタマイズおよび拡張
Visual Studio のモデリングと視覚エフェクト SDK (VMSDK) は、いくつかのレベルをモデリング ツールを定義することができますを提供します。  
  
1.  DSL 定義ダイアグラムを使用してドメイン固有言語 (DSL) を定義します。 DSL は図形式の表記法、読み取り可能な XML 形式では、コードおよびその他の成果物を生成するために必要な基本的なツールとすばやく作成できます。  
  
     詳細については、次を参照してください。[ドメイン固有言語の定義方法](../modeling/how-to-define-a-domain-specific-language.md)です。  
  
2.  DSL 定義のより高度な機能を使用して、DSL を微調整します。 たとえば、ユーザーが要素を作成するときに表示されるその他のリンクを行うことができます。 DSL 定義ではこれらの手法を行うほとんどの場合は、数行プログラム コードの一部が必要です。  
  
3.  プログラム コードを使用して、モデリング ツールを拡張します。 VMSDK は特に、DSL 定義から生成されるコードにより、拡張機能を容易に統合できるようにすることを目的としています。  詳細については、次を参照してください。[ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)です。  
  
> [!NOTE]
>  DSL 定義ファイルを更新したら、忘れずにをクリックして**すべてのテンプレートの変換**ソリューションを再構築する前にソリューション エクスプ ローラーのツールバーにします。  
  
##  <a name="customShapes"></a>このセクションの内容  
  
|この特殊効果を実現するために|このトピックを参照してください。|  
|----------------------------|-------------------------|  
|図形の色とスタイルのプロパティを設定できます。|図形またはコネクタ クラスを右クリックし、**公開追加**、し、項目をクリックします。<br /><br /> 参照してください[図上のプレゼンテーションをカスタマイズする](../modeling/customizing-presentation-on-the-diagram.md)です。|  
|モデル要素のさまざまなクラス ダイアグラムで、初期の高さと幅、色、ツールヒントなどのプロパティを共有するようになります。|シェイプまたはコネクタ クラス間の継承を使用します。 派生図形と派生ドメイン クラス間のマッピングは、親のマッピングの詳細を継承します。<br /><br /> または、別のドメイン クラスが同じ図形クラスをマップします。|  
|モデル要素のクラスは、さまざまな図形のコンテキストで表示されます。|同じドメイン クラスに複数の図形のクラスをマップします。 ソリューションをビルドして次のエラー レポートを使用するには、どのような図形を決定する、要求されたコードを提供します。|  
|図形の色またはフォントなどの機能は、現在の状態を示します。|参照してください[図形とコネクタ、モデルを反映するように更新](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)です。<br /><br /> 公開されたプロパティを更新するルールを作成します。 参照してください[ルールは、モデル内の変更を反映](../modeling/rules-propagate-changes-within-the-model.md)です。<br /><br /> または、OnAssociatedPropertyChanged() を使用して、リンクの矢印やフォントなどの機能の非表示を更新します。|  
|アイコンの状態を示すために図形変わります。|[DSL 詳細] ウィンドウで、デコレータ マッピングの可視性を設定します。 同じ位置でのいくつかのイメージ デコレーターを見つけます。 参照してください[図形とコネクタ、モデルを反映するように更新](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)です。<br /><br /> または、オーバーライド`ImageField.GetDisplayImage()`です。 例を参照して<xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>です。|  
|任意の図形の背景イメージを設定します。|アンカー ImageField を追加する InitializeInstanceResources() をオーバーライドします。 参照してください[図上のプレゼンテーションをカスタマイズする](../modeling/customizing-presentation-on-the-diagram.md)です。|  
|任意の深さに入れ子の図形|再帰的なツリーの埋め込みを設定します。 図形を含む BoundsRules を定義します。 参照してください[図上のプレゼンテーションをカスタマイズする](../modeling/customizing-presentation-on-the-diagram.md)です。|  
|要素の境界に固定の時点でのコネクタに接続します。|図上の小さなポートによって表される、埋め込みのターミナル要素を定義します。 BoundsRules を使用して、場所、ポートを修正します。 回路図サンプルを参照して[Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)です。|  
|テキスト フィールドには、その他の値から派生した値が表示されます。|テキスト デコレータを計算またはカスタムの記憶域のドメイン プロパティにマップします。 詳細については、次を参照してください。[記憶域のカスタム プロパティして計算された](../modeling/calculated-and-custom-storage-properties.md)です。|  
|モデルの要素間または図形間の変更を反映します。|参照してください[ドメイン固有言語で検証](../modeling/validation-in-a-domain-specific-language.md)です。|  
|他のなどのリソースに変更を反映[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ストアの外部の拡張機能です。|参照してください[イベント ハンドラーには、モデルの外部で変更が反映されるまで](../modeling/event-handlers-propagate-changes-outside-the-model.md)です。|  
|[プロパティ] ウィンドウには、関連する要素のプロパティが表示されます。|プロパティの転送を設定します。 参照してください[プロパティ ウィンドウをカスタマイズする](../modeling/customizing-the-properties-window.md)です。|  
|プロパティのカテゴリ|[プロパティ] ウィンドウは、カテゴリと呼ばれるセクションに分かれています。 設定、**カテゴリ**のドメインのプロパティです。 同じカテゴリの名前を持つプロパティは、同じセクションに表示されます。 設定することも、**カテゴリ**リレーションシップ ロールのです。|  
|ドメインのプロパティへのユーザー アクセスの制御|設定**は参照可能な**ドメイン プロパティが実行時に、[プロパティ] ウィンドウに表示されないようにするのには false。 テキスト デコレーターにまだマップできます。<br /><br /> **読み取り専用 UI**ユーザー ドメインのプロパティを変更できないようにします。<br /><br /> ドメイン プロパティにプログラムのアクセスは影響はありません。|  
|名前、アイコン、および DSL のモデル エクスプ ローラー内のノードの可視性を変更します。|参照してください[モデル エクスプ ローラーのカスタマイズ](../modeling/customizing-the-model-explorer.md)です。|  
|コピー、切り取りと貼り付けを有効にします。|設定、**コピーの貼り付けを有効にする**のプロパティ、**エディター** DSL のエクスプ ローラーでノード。|  
|要素がコピーされるたびに、参照先のリンクとターゲットをコピーします。 たとえば、項目に添付されたコメントをコピーします。|設定、**伝達コピー** (DSL 定義ダイアグラム内のドメイン リレーションシップの一方の側にある行で表される)、ソース ロールのプロパティです。<br /><br /> 複雑な効果を実現する ProcessOnCopy をオーバーライドするコードを記述します。<br /><br /> 参照してください[コピー動作をカスタマイズする](../modeling/customizing-copy-behavior.md)です。|  
|削除、親の変更、または要素が削除されたときに、関連する要素をリンクし直します。|設定、**削除伝達**リレーションシップ ロールの値。 複雑な効果は、オーバーライド`ShouldVisitRelationship`と`ShouldVisitRolePlayer`内のメソッド、`MyDslDeleteClosure`で定義されたクラス**DomainModel.cs**<br /><br /> 参照してください[削除動作をカスタマイズします。](../modeling/customizing-deletion-behavior.md)|  
|図形のレイアウトと外観にコピーし、ドラッグ アンド ドロップを保持します。|コピーする図形とコネクタを追加`ElementGroupPrototype`です。 オーバーライドする最も便利な方法します。`ElementOperations.CreateElementGroupPrototype()`<br /><br /> 参照してください[コピー動作をカスタマイズする](../modeling/customizing-copy-behavior.md)です。|  
|現在のカーソル位置など、選択した場所に図形を貼り付けます。|オーバーライド`ClipboardCommandSet.ProcessOnCopy()`の場所に固有のバージョンを使用する`ElementOperations.Merge().`を参照してください[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)です。|  
|貼り付け時にその他のリンクを作成します。|ClipboardCommandSet.ProcessOnPasteCommand() をオーバーライドします。|  
|ドラッグを有効にして、この図は、他の Dsl や Windows から要素を削除します。|参照してください[する方法: ドラッグ アンド ドロップのハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|親をドラッグした場合と、図形やポートなどの子の図形にドラッグすることをツールを許可します。|ターゲット オブジェクト クラスの親にドロップされたオブジェクトを転送するには、要素のマージ ディレクティブを定義します。 参照してください[要素の作成および移動をカスタマイズする](../modeling/customizing-element-creation-and-movement.md)です。|  
|図形やツールを図形にドラッグし、その他のリンクがあるを許可するか、作成されたオブジェクト。 たとえば、リンクされているあるアイテムの上にドロップされるコメントを許可するには、です。|クラスを定義する要素のマージ ディレクティブ、ターゲット ドメイン、およびを生成するリンクを定義します。 複雑な場合は、カスタム コードを追加することができます。 参照してください[要素の作成および移動をカスタマイズする](../modeling/customizing-element-creation-and-movement.md)です。|  
|1 つのツールを使用して要素のグループを作成します。 たとえば、固定ポートのセットを持つコンポーネントです。|ToolboxHelper.cs でツールボックスの初期化メソッドをオーバーライドします。 要素グループ プロトタイプ (EGP) を含む、要素とそのリレーションシップ リンクを作成します。 参照してください[ツールと、ツールボックスのカスタマイズ](../modeling/customizing-tools-and-the-toolbox.md)です。<br /><br /> EGP にプリンシパルとポート図形を含めるか、EGP がインスタンス化されるときに、ポート図形を配置する BoundsRules を定義します。 参照してください[BoundsRules 図形の位置とサイズの制限](../modeling/boundsrules-constrain-shape-location-and-size.md)です。|  
|リレーションシップの複数の種類のインスタンスを作成するには、1 つの接続のツールを使用します。|接続ビルダー ツールによって呼び出されるをリンク接続ディレクティブ (LCD) を追加します。 Lcd では、2 つの要素の型からのリレーションシップの種類を決定します。 要素の状態に依存してこれを行うには、カスタム コードを追加することができます。 参照してください[ツールと、ツールボックスのカスタマイズ](../modeling/customizing-tools-and-the-toolbox.md)です。|  
|注釈ツールのユーザーには、任意のツールを連続的に多くのシェイプまたはコネクタを作成することができますをダブルクリックします。|DSL のエクスプ ローラーで選択、`Editor`ノード。 [プロパティ] ウィンドウで次のように設定します。**ツールボックス アイテムの付箋を使用して**です。|  
|メニュー コマンドを定義します。|参照してください[する方法: 標準メニュー コマンドの変更](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|検証規則を使用してモデルを制限します。|参照してください[ドメイン固有言語での検証](../modeling/validation-in-a-domain-specific-language.md)|  
|DSL からコード、構成ファイル、またはドキュメントを生成します。|[ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)|  
|モデルを保存する方法をカスタマイズするファイル。|参照してください[ファイル記憶域および XML シリアル化をカスタマイズします。](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|モデルは、データベースまたはその他のメディアに保存します。|オーバーライド*YourLanguage*DocData<br /><br /> 参照してください[ファイル記憶域および XML シリアル化をカスタマイズします。](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|1 つのアプリケーションの一部として動作させることは、いくつかの Dsl を統合します。|参照してください[Visual Studio Modelbus を使用してモデルを統合する](../modeling/integrating-models-by-using-visual-studio-modelbus.md)です。|  
|DSL をサード パーティによって拡張することを許可して、拡張機能を制御します。|[MEF による DSL の拡張](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL ライブラリによる DSL 間でのクラスの共有](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [ロック ポリシーの定義と読み取り専用セグメントの作成](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
  
## <a name="see-also"></a>関連項目

[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)   
[ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
[Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
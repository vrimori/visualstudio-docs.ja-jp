---
title: "カスタマイズして、ドメイン固有言語を拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 48
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 00a120fc470393f8ab843636ca5d3400b004232b
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-and-extending-a-domain-specific-language"></a>ドメイン固有言語のカスタマイズおよび拡張
Visual Studio のモデリングと視覚化 SDK (VMSDK) は、モデリング ツールの定義をいくつかのレベルを提供します。  
  
1.  DSL 定義図を使用して、ドメイン固有言語 (DSL) を定義します。 図の表記法、読み取り可能な XML 形式では、コードおよびその他の成果物を生成するために必要な基本的なツールと、DSL をすばやく作成できます。  
  
     詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。  
  
2.  DSL 定義のより高度な機能を使用して DSL を細かく調整します。 たとえば、ユーザーが要素を作成するときに表示されるその他のリンクを行うことができます。 DSL 定義でこれらの手法が実現されるほとんどの場合と、プログラム コードを数行記述が必要です。  
  
3.  プログラム コードを使用して、モデリング ツールを拡張します。 VMSDK は特に、DSL 定義から生成されるコードにより、拡張機能を容易に統合できるようにすることを目的としています。  詳細については、次を参照してください。[ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)します。  
  
> [!NOTE]
>  DSL 定義ファイルを更新したら、忘れずにをクリックして**すべてのテンプレートの変換**ソリューションの再構築する前に、ソリューション エクスプ ローラーのツールバーにします。  
  
##  <a name="a-namecustomshapesa-in-this-section"></a><a name="customShapes"></a>このセクションの  
  
|この効果を実現するには|このトピックを参照してください。|  
|----------------------------|-------------------------|  
|図形の色とスタイルのプロパティを設定できます。|シェイプまたはコネクタ クラスを右クリックし、**公開されている追加**項目をクリックします。<br /><br /> 参照してください[図の外観をカスタマイズする](../modeling/customizing-presentation-on-the-diagram.md)です。|  
|モデル要素のさまざまなクラス ダイアグラムで、初期の高さと幅、色、ツールヒントなどのプロパティを共有するようになります。|シェイプまたはコネクタ クラス間の継承を使用します。 派生の図形と派生ドメイン クラス間のマッピングは、親のマッピングの詳細を継承します。<br /><br /> または、別のドメイン クラスを同じ図形クラスにマップします。|  
|モデル要素のクラスは、さまざまな図形のコンテキストで表示されます。|1 つ以上のシェイプ クラスを同じドメイン クラスにマップします。 ソリューションをビルドするときに次のエラー報告し、使用するには、どのような形状を決定する、要求されたコードを提供します。|  
|図形の色またはフォントなどの機能には、現在の状態が示されます。|参照してください[図形とコネクタ、モデルを反映するように更新](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)します。<br /><br /> 公開されたプロパティを更新するルールを作成します。 参照してください[ルールには、モデル内の変更が反映されるまで](../modeling/rules-propagate-changes-within-the-model.md)します。<br /><br /> または、OnAssociatedPropertyChanged() を使用して、リンクの矢印やフォントなどの機能の非表示を更新します。|  
|図形の変更状態を示すためのアイコン。|[DSL 詳細] ウィンドウで、デコレータ マッピングの可視性を設定します。 同じ位置にいくつかのイメージ デコレータを探します。 参照してください[図形とコネクタ、モデルを反映するように更新](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)します。<br /><br /> または、オーバーライド`ImageField.GetDisplayImage()`します。 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>。</xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>例を参照してください。|  
|任意の図形の背景イメージを設定します。|固定された ImageField を追加する InitializeInstanceResources() をオーバーライドします。 参照してください[図の外観をカスタマイズする](../modeling/customizing-presentation-on-the-diagram.md)です。|  
|任意の深さに入れ子図形|再帰的なツリーの埋め込みを設定します。 図形を含む BoundsRules を定義します。 参照してください[図の外観をカスタマイズする](../modeling/customizing-presentation-on-the-diagram.md)です。|  
|要素の境界に固定の時点でのコネクタに接続します。|図上の小さなポートによって表される、埋め込みのターミナル要素を定義します。 BoundsRules を使用して、場所にポートを修正することができます。 回路図のサンプルを参照して[Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)します。|  
|テキスト フィールドには、その他の値から派生した値が表示されます。|テキスト デコレータを計算またはカスタム ストレージ ドメイン プロパティにマップします。 詳細については、次を参照してください。[計算し、カスタム ストレージ プロパティ](../modeling/calculated-and-custom-storage-properties.md)します。|  
|モデル要素間または図形間の変更を反映します。|参照してください[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)します。|  
|などその他のリソースに変更を反映[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ストア以外の拡張機能です。|参照してください[イベント ハンドラーには、モデルの外部で変更が反映されるまで](../modeling/event-handlers-propagate-changes-outside-the-model.md)します。|  
|[プロパティ] ウィンドウには、関連する要素のプロパティが表示されます。|プロパティの転送を設定します。 参照してください[プロパティ ウィンドウのカスタマイズ](../modeling/customizing-the-properties-window.md)します。|  
|プロパティのカテゴリ|[プロパティ] ウィンドウは、カテゴリと呼ばれるセクションに分かれています。 設定、**カテゴリ**のドメインのプロパティです。 同じカテゴリの名前を持つプロパティは、同じセクションに表示されます。 設定することも、**カテゴリ**リレーションシップ ロールのです。|  
|ドメインのプロパティへのユーザー アクセスの制御|設定**はブラウズ可能な**ドメイン プロパティが実行時に、[プロパティ] ウィンドウに表示されないようにするのには false。 テキスト デコレータにまだマップできます。<br /><br /> **読み取り専用 UI**ドメイン プロパティを変更できないようにします。<br /><br /> ドメイン プロパティにプログラムのアクセスは影響はありません。|  
|名前、アイコン、および DSL のモデル エクスプ ローラー内のノードの表示/非表示を変更します。|参照してください[モデル エクスプ ローラーをカスタマイズする](../modeling/customizing-the-model-explorer.md)です。|  
|コピー、切り取りおよび貼り付けを有効にします。|設定、**コピー貼り付けを有効にする**のプロパティ、**エディター** DSL エクスプ ローラーのノードです。|  
|要素がコピーされるたびに、リンクを参照し、これらのターゲットをコピーします。 たとえば、項目に添付されたコメントをコピーします。|設定、**コピーの伝達**(DSL 定義図で、ドメイン リレーションシップの一方の側で、その行によって表される)、ソース ロールのプロパティです。<br /><br /> さらに複雑な効果を実現する ProcessOnCopy をオーバーライドするコードを記述します。<br /><br /> 参照してください[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。|  
|削除、親を変更すると、または要素を削除すると、関連する要素を再リンクします。|設定、**削除の伝達**顧客間関係のロールの値。 さらに複雑な効果は、オーバーライド`ShouldVisitRelationship`と`ShouldVisitRolePlayer`内のメソッド、`MyDslDeleteClosure`で定義されたクラス**DomainModel.cs**<br /><br /> 参照してください[削除動作のカスタマイズ](../modeling/customizing-deletion-behavior.md)|  
|図形のレイアウトとコピー、ドラッグ アンド ドロップの外観を維持します。|追加の図形とコネクタ、コピーした`ElementGroupPrototype`します。 オーバーライドする最も便利なメソッドは`ElementOperations.CreateElementGroupPrototype()`<br /><br /> 参照してください[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。|  
|現在のカーソル位置など、選択した場所に図形を貼り付けます。|オーバーライド`ClipboardCommandSet.ProcessOnCopy()`の場所に固有のバージョンを使用する`ElementOperations.Merge().`を参照してください[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。|  
|貼り付け時にその他のリンクを作成します。|ClipboardCommandSet.ProcessOnPasteCommand() をオーバーライドします。|  
|ドラッグを有効にして、この図は、その他の Dsl と Windows から要素を削除します。|参照してください[方法: ドラッグ アンド ドロップ ハンドラーを追加します。](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|親の上にドラッグされた場合と、図形やツール、ポートなどの子の図形にドラッグすることを許可します。|ターゲット オブジェクト クラスの親を削除したオブジェクトを転送するには、要素マージ ディレクティブを定義します。 参照してください[要素の作成と移動をカスタマイズする](../modeling/customizing-element-creation-and-movement.md)です。|  
|図形または図形にドラッグして、その他のリンクがあるツールを許可するか、作成されたオブジェクト。 たとえば、リンクするには項目の上にドロップされるコメントを許可します。|ターゲット ドメイン クラス、要素マージ ディレクティブを定義し、生成されるリンクを定義します。 複雑なケースでは、カスタム コードを追加できます。 参照してください[要素の作成と移動をカスタマイズする](../modeling/customizing-element-creation-and-movement.md)です。|  
|1 つのツールを使用して要素のグループを作成します。 たとえば、ポートの固定セットを持つコンポーネントです。|ToolboxHelper.cs 内のツールボックスの初期化メソッドをオーバーライドします。 要素グループ プロトタイプ (EGP) が、要素とそのリレーションシップ リンクを含むを作成します。 参照してください[ツールおよびツールボックスのカスタマイズ](../modeling/customizing-tools-and-the-toolbox.md)します。<br /><br /> EGP にプリンシパルおよびポート図形を含めるか、EGP がインスタンス化されるときに、ポート シェイプを配置する BoundsRules を定義します。 参照してください[BoundsRules シェイプの位置とサイズの制限](../modeling/boundsrules-constrain-shape-location-and-size.md)します。|  
|1 つの接続ツールを使用すると、いくつかの種類のリレーションシップのインスタンスを作成できます。|接続ビルダーは、ツールによって開始するには、リンク接続ディレクティブ (LCD) を追加します。 Lcd では、2 つの要素の型からリレーションシップの種類を決定します。 この要素の状態に依存させるには、カスタム コードを追加できます。 参照してください[ツールおよびツールボックスのカスタマイズ](../modeling/customizing-tools-and-the-toolbox.md)します。|  
|注釈ツール-ユーザーは、連続的に多くのシェイプまたはコネクタを作成する任意のツールをダブルクリックすることができます。|DSL エクスプ ローラーで、選択、`Editor`ノードです。 [プロパティ] ウィンドウで次のように設定します。**ツールボックス アイテムの注釈を使用して**します。|  
|メニュー コマンドを定義します。|参照してください[方法: 標準のメニュー コマンドの変更](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|検証規則を使用してモデルを制限します。|参照してください[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)|  
|DSL からコード、構成ファイル、またはドキュメントを生成します。|[ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)|  
|モデルを保存する方法をカスタマイズするファイルです。|参照してください[ファイル記憶域および XML シリアル化をカスタマイズします。](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|データベースまたはその他のメディアには、モデルを保存します。|オーバーライド*YourLanguage*DocData<br /><br /> 参照してください[ファイル記憶域および XML シリアル化をカスタマイズします。](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|1 つのアプリケーションの一部として動作させることは、いくつかの Dsl を統合します。|参照してください[Visual Studio Modelbus を使用して、モデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)します。|  
|拡張は、サード パーティが DSL を許可し、拡張機能を制御します。|[MEF による DSL の拡張](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [DSL ライブラリによる DSL 間でのクラスの共有](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [ロック ポリシーの定義と読み取り専用セグメントの作成](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)   
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]



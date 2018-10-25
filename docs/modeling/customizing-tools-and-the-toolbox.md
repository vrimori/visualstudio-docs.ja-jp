---
title: ツールおよびツールボックスのカスタマイズ
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: c840ed268e8e5aaa70dcc83eb9a0eeff3a2eb33f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815574"
---
# <a name="customizing-tools-and-the-toolbox"></a>ツールおよびツールボックスのカスタマイズ

ユーザーがモデルに追加可能な要素についてツールボックス項目を定義する必要があります。 ツールには要素ツールと接続ツールの 2 種類があります。 生成されたデザイナーで、ユーザーは要素ツールを選択して図形を図へドラッグすることができ、接続ツールを選択して図形間のリンクを描画できます。 一般にユーザーは、要素ツールを使用するとドメイン クラスのインスタンスをモデルに追加することができ、接続ツールを使用するとドメイン リレーションシップのインスタンスを追加できます。

## <a name="ToolboxDef"></a> ツールボックスの定義方法
 DSL エクスプローラーで、エディター ノードとその下のノードを展開します。 一般に、次のような階層が表示されます。

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

DSL エクスプローラーのこの部分で、次の操作を実行できます。

-   新しいタブを作成します。 タブはツールボックス内のセクション見出しを定義します。

-   新しいツールを作成します。

-   ツールをコピーして貼り付けます。

-   一覧内のツールを上下に移動します。

-   タブとツールを削除します。

> [!IMPORTANT]
> DSL エクスプローラー内の項目を追加または貼り付けるには、新しいノードの親の親を右クリックします。 たとえば、ツールを追加する、タブを右クリックしないと、**ツール**ノード。 タブを追加するを右クリックし、**エディター**ノード。

**ツールボックス アイコン**すべてのツールのプロパティは、16 x 16 ビットマップ ファイルを参照します。 これらのファイルは通常保持、 **dsl \resources**フォルダー。

**クラス**要素ツールのプロパティは具象ドメイン クラスを参照します。 既定では、ツールはこのクラスのインスタンスを作成します。 ただし、コードを作成して、ツールに要素のグループまたはさまざまな種類の要素を作成させることができます。

**接続ビルダー**接続ツールのプロパティは、ツールで接続可能な要素の種類、および間に作成されるリレーションシップを定義する接続ビルダーを参照します。 DSL エクスプローラーで、接続ビルダーはノードとして定義されます。 接続ビルダーは、ドメイン リレーションシップを定義すると自動的に作成されますが、コードを作成してカスタマイズできます。

#### <a name="to-add-a-tool-to-the-toolbox"></a>ツールボックスにツールを追加するには

1.  通常、図形クラスを作成し、それをドメイン クラスにマップした後で、要素ツールを作成します。

     通常、コネクタ クラスを作成し、それを参照リレーションシップにマップした後で、コネクタ ツールを作成します。

2.  DSL エクスプ ローラーで、**エディター**ノードと**ツールボックス タブ**ノード。

     ツールボックス タブ ノードを右クリックし、**新しい要素ツールの追加**または**新規接続ツールの追加**します。

3.  設定、**ツールボックス アイコン**プロパティを 16 x 16 ビットマップを参照してください。

     新しいアイコンを定義する場合は、ソリューション エクスプ ローラーでビットマップ ファイルを作成、 **dsl \resources**フォルダー。 次のプロパティ値があります:**ビルド アクション** = **コンテンツ**;**出力ディレクトリにコピー** = **コピーしない**します。

4.  **要素ツール:** 設定、**クラス**図形にマップされる具象ドメイン クラスを参照するツールのプロパティ。

     **コネクタ ツール:** 設定、**接続ビルダー**ドロップダウン リストで提供されている項目のいずれかのツールのプロパティ。 接続ビルダーは、コネクタをドメイン リレーションシップにマップすると、自動的に作成されます。 最近、コネクタを作成した場合、通常、関連する接続ビルダーを選択しています。

5.  DSL をテストするには、f5 キーまたは CTRL + F5 キーを押して、Visual Studio の実験用インスタンスのサンプル モデル ファイルを開きます。 ツールボックスに新しいツールが表示されます。 それを図の上にドラッグし、新しい要素が作成されることを確認します。

     ツールが表示されない場合は、実験用の Visual Studio を停止します。 Windows で**開始**] メニューの [実行 **、Microsoft Visual Studio 2010 実験用インスタンスをリセット**します。 **ビルド** メニューのをクリックして**ソリューションのリビルド**します。 再度 DSL をテストします。

## <a name="customizing"></a> 要素ツールのカスタマイズ
 既定では、ツールは指定されたクラスの単一インスタンスを作成しますが、次の 2 つの方法で変更できます。

-   他のクラスで要素マージ ディレクティブを定義し、このクラスの新しいインスタンスが受け入れられ、新しい要素が作成されるときに追加のリンクが作成されるようにします。 たとえば、ユーザーが別の要素にコメントをドロップし、両者の間に参照リンクを作成可能にすることができます。

     これらのカスタマイズは、ユーザーが要素を貼り付けたりドラッグ アンド ドロップしたりするときに発生することにも影響します。

     詳細については、次を参照してください。[をカスタマイズする要素の作成と移動](../modeling/customizing-element-creation-and-movement.md)します。

-   コードを作成して、ツールをカスタマイズし、要素のグループを作成可能にします。 ツールはオーバーライド可能な ToolboxHelper.cs 内のメソッドにより初期化されます。 詳細については、次を参照してください。[グループの要素の作成ツールから](#groups)します。

## <a name="groups"></a> ツールからの要素のグループを作成します。
 各要素ツールは作成する要素のプロトタイプを含みます。 既定では、各要素ツールは単一の要素を作成しますが、1 つのツールで関連するオブジェクトのグループを作成することも可能です。 そのためには、関連項目を含む <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> を使用してツールを初期化します。

 次の例は、型 Transistor がある DSL から取得しています。 各 Transistor には名前の付いた Terminal が 3 つあります。 Transistor の要素ツールは、4 つのモデル要素と 3 つのリレーションシップ リンクを含むプロトタイプを格納します。 ユーザーがツールを図の上にドラッグすると、プロトタイプはインスタンス化され、モデル ルートにリンクされます。

 このコードで定義されているメソッドをオーバーライドする**Dsl\GeneratedCode\ToolboxHelper.cs**します。

 プログラム コードを使用して、モデルをカスタマイズする方法の詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }
```

## <a name="connections"></a> 接続ツールのカスタマイズ
 通常、新しいコネクタ クラスを作成するときに要素ツールを作成します。 または、両端の種類でリレーションシップの種類を確認可能にすることで、1 つのツールをオーバーロードできます。 たとえば、Person-Person リレーションシップと Person-Town リレーションシップの両方を作成可能な 1 つの接続ツールを定義できます。

 接続ツールは接続ビルダーを呼び出します。 接続ビルダーを使用して、ユーザーが生成されたデザイナー内で要素をリンク可能な方法を指定します。 接続ビルダーは、リンク可能な要素と要素間に作成されるリンクの種類を指定します。

 ドメイン クラス間に参照リレーションシップを作成すると、接続ビルダーは自動的に作成されます。 接続ツールをマップするときにこの接続ビルダーを使用します。 接続ツールを作成する方法の詳細については、次を参照してください。[ツールボックスの構成](../modeling/customizing-tools-and-the-toolbox.md)します。

 既定の接続ビルダーを変更して、異なる範囲のソース型とターゲット型を扱い、異なる種類のリレーションシップを作成できます。

 接続ビルダー用にカスタム コードを作成し、接続用のソース クラスとターゲット クラスの指定、作成される接続の種類の定義、および接続の作成に関連するその他の処理を実行できます。

### <a name="the-structure-of-connection-builders"></a>接続ビルダーの構造
 接続ビルダーには 1 つ以上のリンク接続ディレクティブが含まれ、それによってドメイン リレーションシップとソース要素およびターゲット要素が指定されます。 たとえば、Task Flow ソリューション テンプレートで確認できます、 **CommentReferencesSubjectsBuilder**で、 **DSL エクスプ ローラー**します。 この接続ビルダーには、1 つのリンクが含まれています。 接続ディレクティブ**CommentReferencesSubjects**、ドメイン リレーションシップに割り当て先となる**CommentReferencesSubjects**します。 このリンク接続ディレクティブには、`Comment` ドメイン クラスを指し示すソース ロール ディレクティブと `FlowElement` ドメイン クラスを指し示すターゲット ロール ディレクティブが含まれます。

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>接続ビルダーを使用したソース ロールとターゲット ロールの制限
 接続ビルダーを使用して、指定されたドメイン リレーションシップのソース ロールまたはターゲット ロールのどちらかで、特定のクラスの出現を制限できます。 たとえば、別のドメイン クラスへのドメイン リレーションシップを伴う基底ドメイン クラスがあるが、そのリレーションシップにおいて、その基底クラスのすべての派生クラスのロールが同じロールになるのは望ましくないという場合があるかもしれません。 Task Flow ソリューションでは、4 つの具象ドメイン クラス (**StartPoint**、**エンドポイント**、 **MergeBranch**、および**同期**) 抽象ドメイン クラスから直接継承した**FlowElement**、2 つの具象ドメイン クラスと (**タスク**と**ObjectInState**) します。そこから直接継承できません。 **フロー**参照リレーションシップを受け取る**FlowElement**ソース ロールとターゲット ロールの両方でのドメイン クラス。 ただしのインスタンス、**エンドポイント**ドメイン クラスのインスタンスのソースがすることはできません、**フロー**リレーションシップのインスタンスには、 **StartPoint**クラスを指定する、インスタンスのターゲットを**フロー**リレーションシップ。 **FlowBuilder**接続ビルダーにリンク接続ディレクティブ**フロー**どのドメイン クラスは、ソースの役割を果たすことができますを指定する (**タスク**、 **MergeBranch**、 **StartPoint**、および**同期**) およびターゲット ロールを再生することができます (**MergeBranch**、 **エンドポイント**、および**同期**)。

### <a name="connection-builders-with-multiple-link-connect-directives"></a>複数のリンク接続ディレクティブを持つ接続ビルダー
 接続ビルダーには複数のリンク接続ディレクティブを追加できます。 これは、ヘルプのユーザーから、ドメイン モデルの複雑さの一部を非表示にし続けることができます、**ツールボックス**が煩雑です。 単一の接続ビルダーにいくつかの異なるドメイン リレーションシップのリンク接続ディレクティブを追加できます。 ただし、ほぼ同一の関数を実行するときはドメイン リレーションシップを結合する必要があります。

 Task Flow ソリューションで、**フロー**接続ツールが両方のインスタンスを描画するために使用される、**フロー**と**ObjectFlow**ドメイン リレーションシップ。 **FlowBuilder**接続ビルダーは、さらに、**フロー**リンク接続ディレクティブの前に説明した、2 つのリンク接続ディレクティブを名前付き**ObjectFlow**します。 これらのディレクティブを指定するのインスタンス、 **ObjectFlow**のインスタンス間の関係を描画する場合があります、 **ObjectInState**ドメイン クラス、またはのインスタンスから、 **ObjectInState**のインスタンスに、**タスク**が 2 つのインスタンス間ではなく、**タスク**、またはのインスタンスから、**タスク**のインスタンスに**ObjectInState**します。 ただしのインスタンスを**フロー**の 2 つのインスタンス間の関係を描画する場合があります、**タスク**します。 コンパイルして、Task Flow ソリューションを実行する場合は、その図面を表示できます、**フロー**のインスタンスから、 **ObjectInState**のインスタンスに、**タスク**のインスタンスを作成します。**ObjectFlow**、描画ですが、**フロー**の 2 つのインスタンス間、**タスク**のインスタンスを作成、**フロー**します。

### <a name="custom-code-for-connection-builders"></a>接続ビルダーのカスタム コード
 ユーザー インターフェイスには接続ビルダーの異なる種類のカスタマイズを定義する 4 つのチェック ボックスがあります。

- **カスタム受け入れ**ソースまたはターゲット ロール ディレクティブ上のチェック ボックス

- **カスタム接続**ソースまたはターゲット ロール ディレクティブ上のチェック ボックス

- **カスタム接続を使用**接続ディレクティブ上のチェック ボックス

- **カスタム**接続ビルダーのプロパティ

  これらのカスタマイズを実施するためにプログラム コードを準備する必要があります。 どのようなコードを準備する必要があるのかを知るためには、これらのボックスのいずれかをチェックし、[すべてのテンプレートの変換] をクリックして、ソリューションをビルドします。 エラー レポートが生成されます。 エラー レポートをダブルクリックし、追加する必要があるコードを説明しているコメントを確認します。

> [!NOTE]
>  カスタム コードを追加するには、GeneratedCode フォルダー内のコード ファイルとは別のコード ファイルに部分クラス定義を作成します。 作業内容を失わないために、生成されたコード ファイルを編集しないでください。 詳細については、次を参照してください。[をオーバーライドすると、生成されたクラスを拡張する](../modeling/overriding-and-extending-the-generated-classes.md)します。

#### <a name="creating-custom-connection-code"></a>カスタム接続コードの作成
 各リンク接続ディレクティブで、**ソース ロール ディレクティブ** タブの定義からな型をドラッグできます。 同様に、**ターゲット ロール ディレクティブ**へのタブを定義する型をドラッグできます。 種類ごとに、さらに指定できます (そのリンク接続ディレクティブです) の接続を許可するを設定するかどうか、**カスタム受け入れ**フラグを設定し、余分なコードを指定します。

 接続が確立されたときに発生することをカスタマイズすることもできます。 たとえば、特定のクラスに対してドラッグが発生するただ 1 つのケース、あるリンク接続ディレクティブが規定するすべてのケース、または FlowBuilder 接続ビルダー全体をカスタマイズできます。 これらの各オプションについて、適切なレベルでカスタム フラグを設定できます。 すべてのテンプレートを変換し、ソリューションのビルドを試みると、エラー メッセージから生成されたコード内のコメントに誘導されます。 これらのコメントにより、提供する必要のあるものが特定されます。

 コンポーネント図のサンプルで、Connection ドメイン リレーションシップの接続ビルダーはポート間に作成可能な接続を制限するようにカスタマイズされています。 次の図は、`OutPort` 要素から `InPort` 要素への接続のみ可能であること、しかし互いの内部でコンポーネントを入れ子にすることが可能であることを示しています。

 **入れ子になったコンポーネントから OutPort へ着信接続**

 ![接続ビルダー](../modeling/media/connectionbuilder_3.png)

 したがって、入れ子になったコンポーネントから OutPort への接続が可能であることを指定するのが適切です。 このような接続を指定する設定**カスタム受け入れを使用**上、 **InPort**ソース ロールとしての型と**OutPort**ターゲット ロールとして型、 **DSL の詳細**ウィンドウが次の図に示すようにします。

 **DSL エクスプ ローラーにおけるリンク接続ディレクティブ**

 ![接続ビルダー イメージ](../modeling/media/connectionbuilder_4a.png)

 **DSL 詳細ウィンドウにおけるリンク接続ディレクティブ**

 ![](../modeling/media/connectionbuilder_4b.png)

 次に、ConnectionBuilder クラスにメソッドを入力する必要があります。

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 プログラム コードを使用して、モデルをカスタマイズする方法の詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。

 たとえば、同様のコードを使用して、ユーザーによる親子リンクを含むループの作成を防ぐことができます。 これらの制限は、ユーザーはいつでもそれらを超えることはできませんので、'ハード」な制約と見なされます。 保存できない無効な構成を作成して、ユーザーが一時的に迂回可能 'soft' の検証チェックを作成することもできます。

### <a name="good-practice-in-defining-connection-builders"></a>接続ビルダーを定義する際の適切なプラクティス
 異なる種類のリレーションシップを作成するために、それらが概念的に関連する場合にのみ、1 つの接続ビルダーを定義する必要があります。 タスク フローのサンプルでは、同じビルダーを使用して、タスク間のフローのほか、タスクとオブジェクト間のフローも作成します。 ただし、コメントとタスク間のリレーションシップを作成するために同じビルダーを使用することは混乱を招くことがあります。

 複数の種類のリレーションシップに対して接続ビルダーを定義する場合、ソース オブジェクトとターゲット オブジェクトの同じペアから複数の型が一致しないことを確認する必要があります。 そうでない場合、結果は予測不可能になります。

 カスタム コードを使用して、'ハード」な制約を適用するが、ユーザーが一時的に無効な接続を作成できるかどうかを検討してください。 その必要がある場合、制約を変更して、ユーザーが変更内容を保存しようとするまで、接続が検証されないようにすることができます。

## <a name="see-also"></a>関連項目

- [要素作成処理および要素移動処理のカスタマイズ](../modeling/customizing-element-creation-and-movement.md)
- [コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)
- [方法: ドラッグ アンド ドロップ ハンドラーを追加する](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [回路図のサンプル DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
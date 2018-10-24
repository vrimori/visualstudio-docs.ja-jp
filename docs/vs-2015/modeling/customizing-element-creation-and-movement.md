---
title: 要素の作成と移動のカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
ms.assetid: cbd28f15-dfd7-46bd-ab79-5430e3ed83c8
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 470ff89dfd864443206c1d9131fb126d58280859
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853832"
---
# <a name="customizing-element-creation-and-movement"></a>要素作成処理および要素移動処理のカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

要素をツールボックスから、または貼り付けでは、別にドラッグするか、操作を移動することができます。 指定したリレーションシップを使用して移動された要素をターゲット要素にリンクされていることができます。  
  
 要素マージ ディレクティブ (EMD) は、1 つのモデル要素が場合の動作を指定します*マージ*別のモデル要素にします。 これは、ような場合。  
  
- ユーザーは、ツールボックスから図や図形にドラッグします。  
  
- ユーザーは、エクスプ ローラーまたはコンパートメント シェイプで、[追加] メニューを使用して要素を作成します。  
  
- ユーザーは、1 つのレーンから項目を移動します。  
  
- ユーザーは、要素を貼り付けます。  
  
- プログラム コードでは、要素マージ ディレクティブを呼び出します。  
  
  作成操作は、別のコピー操作に見える可能性があります、動作は同じ方法でが実際に表示します。 要素が追加されると、たとえば、ツールボックスからそのプロトタイプはレプリケートされます。 プロトタイプは、モデルの別の部分からコピーされた要素と同様に、モデルにマージされます。  
  
  EMD の責任では、オブジェクトまたはオブジェクトのグループをモデルの特定の場所にマージする必要がある方法を決定します。 具体的には、モデルにマージされたグループをリンクするどのようなリレーションシップをインスタンス化する必要がありますを決定します。 プロパティを設定して、その他のオブジェクトを作成することをカスタマイズすることもできます。  
  
  ![DSL&#45;EMD&#95;マージ](../modeling/media/dsl-emd-merge.png "DSL EMD_Merge")  
  要素マージ ディレクティブの役割  
  
  EMD は、埋め込みリレーションシップを定義するときに自動的に生成されます。 この既定 EMD は、ユーザーが親に子の新しいインスタンスを追加するときに、リレーションシップのインスタンスを作成します。 カスタム コードを追加してたとえば既定入力例: でこれらを変更できます。  
  
  ユーザーがドラッグするか、マージされた側と受信側のクラスのさまざまな組み合わせを貼り付けできるように、DSL 定義で、独自の入力例: を追加することもできます。  
  
## <a name="defining-an-element-merge-directive"></a>要素マージ ディレクティブを定義します。  
 要素マージ ディレクティブは、ドメイン クラス、ドメイン リレーションシップ、図形、コネクタ、およびダイアグラムを追加できます。 追加したり、受信側のドメイン クラスの下の DSL エクスプ ローラーで確認できます。 受信側のクラスは、モデルでは、新規またはコピーした要素をマージするのには、既に要素のドメイン クラス。  
  
 ![DSL&#45;EMD&#95;詳細](../modeling/media/dsl-emd-details.png "DSL EMD_Details")  
  
 **クラスのインデックス作成**受信側のクラスのメンバーにマージできる要素のドメイン クラスです。 設定していない場合も、インデックス作成クラスのサブクラスのインスタンスを結合によって、この EMD は**サブクラスに適用**を False にします。  
  
 マージ ディレクティブの 2 つの種類があります。  
  
- A**プロセス マージ**ディレクティブがリレーションシップをツリーに新しい要素をリンクする必要がありますを指定します。  
  
- A**転送マージ**ディレクティブは、受信側の別の要素、親では通常に新しい要素をリダイレクトします。  
  
  ディレクティブを結合するカスタム コードを追加することができます。  
  
- 設定**はカスタム受け入れ**インデックス作成の要素の特定のインスタンスがターゲット要素にマージするかどうかを判断するコードを追加します。 ユーザーは、ツールボックスからドラッグした、コードのマージは許可しません「が無効です」ポインターが表示されます。  
  
   たとえば、受信側の要素が、特定の状態の場合にのみ、マージを許可する可能性があります。  
  
- 設定**カスタム マージを使用して**を追加する、マージが実行されると、モデルに加えられた変更を定義する独自のコードを提供します。  
  
   たとえば、モデル内の新しい場所からデータを使用してマージされた要素のプロパティを設定でした。  
  
> [!NOTE]
>  カスタム マージのコードを記述する場合は、この EMD を使用して実行される唯一の結合に影響します。 他の入力例: 同じ種類のオブジェクトをマージする場合、または、EMD を使用せずにこれらのオブジェクトを作成する他のカスタム コードがある場合は、は受けませんマージのカスタム コード。  
>   
>  新しい要素または新しいリレーションシップが常に処理される、カスタム コードを確認する場合は、定義することを検討してください、`AddRule`埋め込みリレーションシップに対して、`DeleteRule`要素のドメイン クラス。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)します。  
  
## <a name="example-defining-an-emd-without-custom-code"></a>例: カスタム コードなし EMD を定義します。  
 次の例では、既存の図形には、ツールボックスからドラッグして、同時に要素とコネクタを作成できます。 例では、DSL 定義に EMD を追加します。 この変更では、前にユーザーは、図に、既存の図形の上にないツールをドラッグできます。  
  
 ユーザーは、その他の要素の上に要素を貼り付けることができますも。  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>ユーザーが同時に、要素とコネクタを作成できるようにするには  
  
1. 使用して、新しい DSL を作成、**最小言語**ソリューション テンプレート。  
  
    この DSL を実行すると、図形と図形の間のコネクタを作成することができます。 新しいをドラッグすることはできません**ExampleElement**既存の図形には、ツールボックスから図形。  
  
2. 要素をマージしてもらうために`ExampleElement`、図形の作成で新しい EMD、`ExampleElement`ドメイン クラス。  
  
   1.  **DSL エクスプ ローラー**、展開**ドメイン クラス**します。 右クリックして`ExampleElement` をクリックし、**新しい要素マージ ディレクティブの追加**します。  
  
   2.  必ず、 **DSL の詳細**新しい EMD の詳細を表示することは、ウィンドウが開いて。 (メニュー:**ビュー**、**他の Windows**、 **DSL の詳細**)。  
  
3. 設定、**クラスのインデックス作成**DSL 詳細 ウィンドウの上にマージできる要素のクラスを定義する`ExampleElement`オブジェクト。  
  
    この例では、次のように選択します。`ExampleElements`されるため、ユーザーは既存の要素に新しい要素をドラッグすることができます。  
  
    インデックス作成クラスは DSL エクスプ ローラーで EMD の名前になることに注意してください。  
  
4. **リンクを作成してマージを処理**、2 つのパスを追加します。  
  
   1. 1 つのパスは、新しい要素を親モデルにリンクします。 パス式を入力する必要のあるに移動します、既存の要素からを埋め込みリレーションシップを介して親モデル。 最後に、新しい要素の割り当てられた新しいリンクで、ロールを指定します。 パスは次のとおりです。  
  
       `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
   2. その他のパスは、新しい要素を既存の要素にリンクします。 パス式では、参照リレーションシップと、新しい要素の割り当てられたロールを指定します。 このパスは次のとおりです。  
  
       `ExampleElementReferencesTargets.Sources`  
  
      パスのナビゲーション ツールを使用すると、各パスを作成します。  
  
   3. [**パスにリンクを作成してマージを処理**、] をクリックして**\<パスの追加 >** します。  
  
   4. リスト項目の右側の下矢印をクリックします。 ツリー ビューが表示されます。  
  
   5. 指定するパスを形成するツリーのノードを展開します。  
  
5. DSL をテストします。  
  
   1.  F5 キーを押して、ソリューションをリビルドして実行します。  
  
        生成されたコードは、新しい DSL 定義に準拠するようにテキスト テンプレートから更新されるため、再構築が通常より長くがかかります。  
  
   2.  ときの実験用インスタンス[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]が最初に、DSL のモデル ファイルを開きます。 いくつかの例の要素を作成します。  
  
   3.  ドラッグして、**要素例**ツールには、既存の図形。  
  
        新しい図形が表示されたら、および既存の図形とコネクタにリンクされます。  
  
   4.  既存の図形をコピーします。 別の図形を選択し、貼り付けます。  
  
        最初の図形のコピーが作成されます。  新しい名前し、2 番目の図形とコネクタにリンクされています。  
  
   このプロシージャから、次の点に注意してください。  
  
-   要素マージ ディレクティブを作成すると、その他の操作をそのまま使用する要素の任意のクラスを許可できます。 受信側のドメイン クラスに、EMD が作成され、承認済みドメイン クラスがで指定された、 **Index クラス**フィールド。  
  
-   パスを定義すると、どのようなリンクにする必要がありますを指定できます、既存のモデルに新しい要素の接続に使用します。  
  
     指定したリンクは、1 つの埋め込みリレーションシップを含める必要があります。  
  
-   EMD は、両方の作成にツールボックスおよびも貼り付け操作に影響します。  
  
     使用して、EMD を明示的に呼び出す場合、新しい要素を作成するカスタム コードを記述する、`ElementOperations.Merge`メソッド。 これにより、コードが、その他の操作と同様に、モデルに新しい要素をリンクすることを確認します。 詳細については、次を参照してください。[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>例: EMD へのカスタム受け入れコードの追加  
 EMD にカスタム コードを追加することより複雑な結合の動作を定義できます。 この簡単な例では、ユーザーが要素の固定数よりも多く、ダイアグラムに追加できなくなります。 例では、既定の埋め込みリレーションシップに付属している EMD を変更します。  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>カスタム受け入れをユーザーの追加を制限するコードを記述するには  
  
1.  使用して DSL を作成、**最小言語**ソリューション テンプレート。 DSL 定義図を開きます。  
  
2.  DSL エクスプ ローラーで、**ドメイン クラス**、 `ExampleModel`、**要素マージ ディレクティブ**します。 という名前の要素マージ ディレクティブを選択します。`ExampleElement`します。  
  
     この EMD は、ユーザーを新規作成方法を制御`ExampleElement`など、ツールボックスからドラッグすることによって、モデル内のオブジェクト。  
  
3.  **DSL の詳細**ウィンドウで、**はカスタム受け入れ**します。  
  
4.  ソリューションをリビルドします。 生成されたコードは、モデルから更新されるため、通常よりも長くかかります。  
  
     報告されるのと同様に、ビルド エラーが表示されます:「Company.ElementMergeSample.ExampleElement は定義を含んでいない CanMergeExampleElement の...」  
  
     メソッドを実装する必要があります`CanMergeExampleElement`します。  
  
5.  新しいコード ファイルを作成、 **Dsl**プロジェクト。 その内容を次のコードに置き換え、プロジェクトの名前空間の名前空間を変更します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace Company.ElementMergeSample // EDIT.  
    {  
      partial class ExampleModel  
      {  
        /// <summary>  
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.  
        /// This happens when the user pastes an ExampleElement  
        /// or drags from the toolbox.  
        /// Determines whether the merge is allowed.  
        /// </summary>  
        /// <param name="rootElement">The root element in the merging EGP.</param>  
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>  
        /// <returns>True if the merge is allowed</returns>  
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)  
        {  
          // Allow no more than 4 elements to be added:  
          return this.Elements.Count < 4;  
        }  
      }  
    }  
  
    ```  
  
     この簡単な例では、親モデルにマージできる要素の数を制限します。 さらに興味深い条件については、メソッドは、プロパティのいずれかと受信側のオブジェクトのリンクを検査できます。 伝達される結合の要素のプロパティが調べることもできます、<xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>します。 詳細については`ElementGroupPrototypes`を参照してください[コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)します。 モデルを読み取るコードを記述する方法の詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。  
  
6.  DSL をテストします。  
  
    1.  F5 キーを押して、ソリューションをリビルドします。 ときの実験用インスタンス[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]が開いたら、DSL のインスタンスを開きます。  
  
    2.  いくつかの方法では、新しい要素を作成します。  
  
        1.  ドラッグして、**要素例**ツールを図にします。  
  
        2.  **例モデル エクスプ ローラー**ルート ノードを右クリックし、クリックして**新しい例の Add 要素**します。  
  
        3.  コピーして、ダイアグラムの要素を貼り付けます。  
  
    3.  モデルに複数の 4 つの要素を追加する方法はこれらのいずれか使用できないことを確認します。 これは、要素マージ ディレクティブを使用するためです。  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>例: EMD にカスタムのマージのコードを追加します。  
 カスタム マージのコードでは、ユーザーがツールをドラッグまたは要素に貼り付けますときの動作を定義できます。 カスタム マージを定義する 2 つの方法はあります。  
  
1. 設定**を使用してカスタム マージ**し、必要なコードを指定します。 生成されたマージのコードをコードに置き換えます。 マージが何を完全に再定義する場合は、このオプションを使用します。  
  
2. 上書き、`MergeRelate`メソッド、および必要に応じて、`MergeDisconnect`メソッド。 これを行うには、設定する必要があります、 **Double Derived の生成**ドメイン クラスのプロパティ。 コードでは、基底クラスで生成されたマージのコードを呼び出すことができます。 マージが実行された後、追加の操作を実行する場合は、このオプションを使用します。  
  
   これらの方法では、この EMD を使用して実行されるマージのみに影響します。 定義する代わりには、マージされた要素を作成できるすべての方法に影響する場合、`AddRule`埋め込みリレーションシップに対して、`DeleteRule`マージされたドメイン クラス。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)します。  
  
#### <a name="to-override-mergerelate"></a>MergeRelate をオーバーライドするには  
  
1.  DSL 定義では、コードを追加する EMD が定義されていることを確認します。 する場合は、パスを追加および定義ユーザー設定は、前のセクションで説明したコードをそのまま使用します。  
  
2.  DslDefinition の図では、マージの受信側のクラスを選択します。 通常、埋め込みリレーションシップのソース エンドにあるクラスです。  
  
     たとえば、最小言語ソリューションから生成された DSL で次のように選択します。`ExampleModel`します。  
  
3.  **プロパティ**ウィンドウで、設定**Double Derived の生成**に**true**します。  
  
4.  ソリューションをリビルドします。  
  
5.  内容を調べる**Dsl\Generated Files\DomainClasses.cs**します。 という名前のメソッドを検索`MergeRelate`の内容を調べる。 独自のバージョンを作成するのに役立ちます。  
  
6.  新しいコード ファイルでは、受信側のクラスの部分クラスを記述し、オーバーライド、`MergeRelate`メソッド。 基本メソッドを呼び出してに注意してください。 例えば:  
  
    ```csharp  
    partial class ExampleModel  
    {  
      /// <summary>  
      /// Called when the user drags or pastes an ExampleElement onto the diagram.  
      /// Sets the time of day as the name.  
      /// </summary>  
      /// <param name="sourceElement">Element to be added</param>  
      /// <param name="elementGroup">Elements to be merged</param>  
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)  
      {  
        // Connect the element according to the EMD:  
        base.MergeRelate(sourceElement, elementGroup);  
  
        // Custom actions:   
        ExampleElement mergingElement = sourceElement as ExampleElement;  
        if (mergingElement != null)  
        {  
          mergingElement.Name = DateTime.Now.ToLongTimeString();  
        }  
      }  
    }  
  
    ```  
  
#### <a name="to-write-custom-merge-code"></a>カスタムのマージのコードを記述するには  
  
1. **Dsl\Generated Code\DomainClasses.cs**、という名前のメソッドを検査`MergeRelate`します。 これらのメソッドは、新しい要素と、既存のモデル間のリンクを作成します。  
  
    という名前のメソッドを調べることも、`MergeDisconnect`します。 これらのメソッドは、削除するときに、モデルの要素をリンク解除します。  
  
2. **DSL エクスプ ローラー**を選択するかをカスタマイズする要素マージ ディレクティブを作成します。 **DSL の詳細**ウィンドウで、設定**を使用してカスタム マージ**します。  
  
    このオプションを設定すると、**プロセス マージ**と**転送マージ**オプションは無視されます。 コードは、代わりに使用されます。  
  
3. ソリューションをリビルドします。 モデルから生成されるコード ファイルが更新されるため、通常よりも長くかかります。  
  
    エラー メッセージが表示されます。 生成されたコードの指示を表示するエラー メッセージをダブルクリックします。 これらの手順では、2 つの方法を指定するよう求められます`MergeRelate` *YourDomainClass*と`MergeDisconnect` *YourDomainClass*  
  
4. 別のコード ファイルの部分クラス定義でメソッドを記述します。 前に検査する例は、必要なものをお勧めします必要があります。  
  
   カスタム マージのコードを直接オブジェクトとリレーションシップを作成するコードには影響しませんし、その他の入力例: 影響を受けません。 要素を作成する方法に関係なく、追加の変更が実装されていることを確認するには、書き込みを検討してください。、`AddRule`と`DeleteRule`代わりにします。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)します。  
  
## <a name="redirecting-a-merge-operation"></a>マージ操作をリダイレクトします。  
 転送マージ ディレクティブは、マージ操作の対象をリダイレクトします。 通常、新しいターゲットは、最初のターゲットの埋め込みの親です。  
  
 たとえば、コンポーネント図のテンプレートで作成した DSL では、ポートはコンポーネントに埋め込まれます。 ポートは、コンポーネント図形の端にある小さなシェイプとして表示されます。 ユーザーは、コンポーネント図形にポート ツールをドラッグして、ポートを作成します。 場合によっては、誤って、ユーザーは、コンポーネントの代わりに、既存のポートにポート ツールをドラッグし、操作は失敗します。 これは、いくつかの既存のポートがある場合、という、簡単な誤りです。 この妨害を回避するために、ユーザーのため、既存のポートにドラッグすることが、親コンポーネントにリダイレクトするアクションへのポートを許可できます。 操作は、ターゲット要素が、コンポーネントであるかのように動作します。  
  
 転送マージ ディレクティブは、コンポーネント モデルのソリューションで作成できます。 コンパイルして、元のソリューションを実行する場合、ユーザーが任意の数をドラッグできますを参照する必要があります**入力ポート**または**出力ポート**要素から、**ツールボックス**に**コンポーネント**要素。 ただし、既存のポートにポートをドラッグ、ことはできません。 利用不可ポインターは、この移行が有効でないことに警告します。 あるように、ポートが意図せずに、転送マージ ディレクティブを作成するただし、既存の上にドロップ**入力ポート**に転送されます、**コンポーネント**要素。  
  
#### <a name="to-create-a-forward-merge-directive"></a>転送マージ ディレクティブを作成するには  
  
1.  作成、[!INCLUDE[dsl](../includes/dsl-md.md)]コンポーネント モデル テンプレートを使用してソリューション。  
  
2.  表示、 **DSL エクスプ ローラー**を DslDefinition.dsl を開きます。  
  
3.  **DSL エクスプ ローラー**、展開**ドメイン クラス**します。  
  
4.  **ComponentPort**抽象ドメイン クラスは両方の基本クラス**InPort**と**OutPort**します。 右クリックして**ComponentPort**  をクリックし、**新しい要素マージ ディレクティブの追加**します。  
  
     新しい**要素マージ ディレクティブ**ノードが表示されます、**要素マージ ディレクティブ**ノード。  
  
5.  選択、**要素マージ ディレクティブ**ノードとオープン、 **DSL の詳細**ウィンドウ。  
  
6.  インデックス作成クラスの一覧で選択**ComponentPort**します。  
  
7.  選択**別のドメイン クラスへのマージを転送**します。  
  
8.  パスの選択 ボックスの一覧で  **ComponentPort**、展開**ComponentHasPorts**、し、**コンポーネント**します。  
  
     新しいパスでは、このようになります。  
  
     **ComponentHasPorts.Component/!Component**  
  
9. ソリューションを保存し、一番右のボタンをクリックして、テンプレートを変換、**ソリューション エクスプ ローラー**ツールバー。  
  
10. ソリューションをビルドして実行します。 新しいインスタンス[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]が表示されます。  
  
11. **ソリューション エクスプ ローラー**Sample.mydsl を開きます。 図は、および**ComponentLanguage ツールボックス**が表示されます。  
  
12. ドラッグ、**入力ポート**から、**ツールボックス**間**ポートを入力します。** 次に、ドラッグ、 **OutputPort**を**InputPort**にもう**OutputPort**します。  
  
     利用不可のポインターが表示されないはずし、新しいドロップできる**入力ポート**既存のものにします。 新しい**入力ポート**の別のポイントにドラッグして、**コンポーネント**します。  
  
## <a name="see-also"></a>関連項目  
 [移動して、プログラム コードでモデルを更新しています](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [ツールおよびツールボックスのカスタマイズ](../modeling/customizing-tools-and-the-toolbox.md)   
 [回路図のサンプル DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)




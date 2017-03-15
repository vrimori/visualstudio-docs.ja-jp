---
title: "ドメイン固有言語の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 16
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 8bd2f054db2c69a99218af05ca8d12465731ebca
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-domain-specific-languages"></a>ドメイン固有言語の概要
このトピックを定義すると、Visual Studio Modeling SDK で作成したドメイン固有言語 (DSL) を使用して基本的な概念を説明します。  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 作業に使用することをお勧めの Dsl に慣れていない場合、 **DSL ツール ラボ**、このサイトで見つけることができます: [Visualizaton and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>ドメイン固有言語では、何をことができますか。  
 ドメイン固有言語は、表記法、通常、グラフィック、特定の目的で使用するために設計されています。 これに対し、UML などの言語は、汎用的なです。 DSL では、モデル要素とそれらの関係と、画面に表示するかの種類を定義できます。  
  
 DSL を設計するときに、Visual Studio Integration Extension (VSIX) パッケージの一部として配布できます。 ユーザーの操作で DSL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
 ![ファミリ ツリー ダイアグラム、ツールボックス、およびエクスプ ローラー](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 表記法は、DSL の一部のみです。 と共に、表記法では、VSIX パッケージには、ユーザーが編集し、そのモデルから情報を生成するために適用可能なツールが含まれています。  
  
 Dsl のプリンシパルのアプリケーションの&1; つは、プログラム コード、構成ファイル、および他の成果物を生成します。 特に大規模なプロジェクトと製品ライン、製品の複数のバリアントを作成する Dsl から多くの可変部分を生成することができますを提供が大幅に増加信頼性と要件の変更に対して非常に迅速に対応します。  
  
 この概要の残りの部分は、作成と使用にドメイン固有言語の基本操作について説明したチュートリアルが[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 DSL を定義するには、以下のコンポーネントをインストールしておく必要があります。  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Modeling SDK for Visual Studio||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-dsl-solution"></a>DSL ソリューションを作成します。  
 新しいドメイン固有言語を作成する新規に作成する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ドメイン固有言語プロジェクト テンプレートを使用してソリューションです。  
  
#### <a name="to-create-a-dsl-solution"></a>DSL ソリューションを作成するには  
  
1.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。  
  
2.  [**プロジェクトの種類**、展開、**その他のプロジェクトの種類**] ノードをクリック**拡張**します。  
  
3.  クリックして**ドメイン固有言語デザイナー**します。  
  
     ![DSL ダイアログの作成](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
4.  **名**ボックスに、入力**FamilyTree**します。 **[OK]** をクリックします。  
  
     **ドメイン固有言語ウィザード**開き、テンプレート DSL ソリューションの一覧が表示されます。  
  
     各テンプレートの説明を表示する をクリックします。  
  
     テンプレートは、便利な開始点です。 それぞれは、完全な作業、ニーズに合わせて編集できます DSL を提供します。 通常、作成する最も近いテンプレートを選択します。  
  
5.  このチュートリアルでは、選択、**最小言語**テンプレートです。  
  
6.  該当するウィザード ページに DSL のファイル名拡張子を入力します。 これは、DSL インスタンスを含むファイルに使用される拡張子です。  
  
    -   自分のコンピューターで、または DSL をインストールするすべてのコンピューターで任意のアプリケーションに関連付けられていない拡張機能を選択します。 たとえば、 **docx**と**htm**はファイ名拡張子。  
  
    -   入力した拡張子が DSL として使用されている場合は、ウィザードから警告が出されます。 別のファイル名拡張子の使用を検討してください。 また、古い実験デザイナーをクリアするために Visual Studio SDK 実験用インスタンスをリセットできます。 をクリックして**開始**、 をクリックして**すべてのプログラム**、 **Microsoft Visual Studio 2010 SDK**、**ツール**、し**Microsoft Visual Studio 2010 実験用インスタンスをリセット**します。  
  
7.  他のページを検査し、クリックして**完了**します。  
  
     2 つのプロジェクトを含むソリューションが生成されます。 Dsl および DslPackage 指定します。 ダイアグラム ファイルは、つまり名前付き DslDefinition.dsl が開きます。  
  
    > [!NOTE]
    >  2 つのプロジェクト内のフォルダーに表示されるコードのほとんどは、DslDefinition.dsl から生成されます。 このため、このファイルで DSL にほとんどの変更が行われます。  
  
 ユーザー インターフェイスは次の図のようになります。  
  
 ![dsl デザイナー](../modeling/media/dsl_designer.png "dsl_designer")  
  
 このソリューションはドメイン固有言語を定義します。 詳細については、次を参照してください。[ドメイン固有言語ツールのユーザー インターフェイスの概要](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)します。  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>DSL ソリューションの重要な要素  
 新しいソリューションの次の側面に注目してください。  
  
-   **Dsl\DslDefinition.dsl** DSL ソリューションを作成すると表示されているファイルです。 このファイルから、ソリューション内のほぼすべてのコードが生成され、DSL 定義に加えた変更の大部分はここで行われます。 詳細については、操作をご覧ください、 [DSL 定義図の操作](../modeling/working-with-the-dsl-definition-diagram.md)します。  
  
-   **Dsl プロジェクト**このプロジェクトには、ドメイン固有言語を定義するコードが含まれています。  
  
-   **DslPackage プロジェクト**このプロジェクトには、開きで編集する DSL のインスタンスを許可するコードが含まれている[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
##  <a name="a-namedebugginga-running-the-dsl"></a><a name="Debugging"></a>DSL を実行しています。  
 作成するとすぐには、DSL ソリューションを実行できます。 後を変更、DSL 定義徐々 に、各変更後にもう一度ソリューションを実行します。  
  
#### <a name="to-experiment-with-the-dsl"></a>DSL をテストするには  
  
1.  クリックして**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー。 これには、DslDefinition.dsl からソース コードの大部分が再生成します。  
  
    > [!NOTE]
    >  クリックする必要があります DslDefinition.dsl を変更するたびに**すべてのテンプレートの変換**ソリューションを再構築する前にします。 このステップは自動化できます。 詳細については、次を参照してください。[すべてのテンプレートの変換を自動化する方法](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)します。  
  
2.  F5 キーを押すか、**デバッグ** メニューのをクリックして**デバッグ開始**します。  
  
     DSL をビルドの実験用インスタンスにインストールされている[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用のインスタンスが開始します。 実験用インスタンスが、レジストリの別個のサブツリーからその設定を受け取り、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]デバッグのための拡張機能を登録します。 通常のインスタンスの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]登録されている拡張子にアクセスする必要はありません。  
  
3.  実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、という名前のモデル ファイルを開く**テスト**から**ソリューション エクスプ ローラー**します。  
  
     \- または  
  
     デバッグ プロジェクトを右クリックし、順にポイント**追加**、クリックして**項目**します。 **項目の追加**ダイアログ ボックスで、DSL のファイルの種類を選択します。  
  
     モデル ファイルは、空白のダイアグラムとして開きます。  
  
     ツールボックスが開き、ダイアグラムの種類に適したツールを表示します。  
  
4.  ツールを使用すると、ダイアグラムで図形とコネクタを作成できます。  
  
    1.  図形を作成するには、ダイアグラムに図形の例のツールからドラッグします。  
  
    2.  2 つの図形を接続をクリックして、例のコネクタ ツールをクリックし、最初の図形をクリックして、2 番目の図形をクリックします。  
  
5.  それらを変更する図形のラベルをクリックします。  
  
 実験用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]は次の例のようになります。  
  
 ![](../modeling/media/dsl_min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>モデルのコンテンツ  
 DSL のインスタンスであるファイルの内容と呼ばれる、*モデル*します。 モデルに含まれる*モデル**要素*と*リンク*要素の間です。 DSL 定義は、モデル要素の種類を指定し、リンクがモデル内に存在します。 たとえば、最小言語テンプレートから作成された、DSL では&1; 種類のモデル要素およびリンクの&1; つの種類。  
  
 DSL 定義では、モデルのダイアグラムの表示方法を指定できます。 さまざまな図形とコネクタのスタイルから選択することができます。 その他の図形内の一部の図形が表示されることを指定することができます。  
  
 ツリーとしてモデルを表示する、**エクスプ ローラー**モデルを編集している間に表示します。 ダイアグラムに図形を追加すると、モデル要素は、エクスプ ローラーでも表示されます。 ダイアグラムが存在しない場合でも、エクスプ ローラーを使用できます。  
  
 表示されないかどうかは、エクスプ ローラーのデバッグ インスタンスの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]の**ビュー**  メニューをポイント**その他のウィンドウ**、 をクリックし、 * \<Your 言語 >* **エクスプ ローラー**します。  
  
### <a name="the-api-of-your-dsl"></a>DSL の API  
 DSL には、読み取りおよび、DSL のインスタンスであるモデルを更新できるようにする API が生成されます。 API の&1; つのアプリケーションでは、モデルからテキスト ファイルを生成します。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して、デザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)します。  
  
 デバッグ ソリューションでは、拡張子が".tt"テンプレート ファイルを開きます。 これらのサンプルでは、モデルからテキストを生成し、DSL の API をテストすることを許可する方法を示しています。 記述されたサンプルの&1; つ[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]でその他の[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]です。  
  
 [テンプレート] で各ファイルは、これによって生成されるファイルです。 ソリューション エクスプ ローラーで、テンプレート ファイルを展開し、生成されたファイルを開きます。  
  
 テンプレート ファイルには、モデル内のすべての要素を一覧表示するコードの短いセグメントが含まれています。  
  
 生成されたファイルには、結果が含まれています。  
  
 モデル ファイルを変更するときに、ファイルを再生成した後は、生成されたファイルに対応する変更が表示されます。  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>モデル ファイルを変更した後、テキスト ファイルを再生成するには  
  
1.  実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、モデル ファイルを保存します。  
  
2.  各 .tt ファイルのファイル名のパラメーターは、実験を使用しているモデル ファイルを指すことを確認します。 .Tt ファイルを保存します。  
  
3.  クリックして**すべてのテンプレートの変換**のツールバーで**ソリューション エクスプ ローラー**します。  
  
     \- または  
  
     クリックして、再生成するテンプレートを右クリックして**カスタム ツールの実行**します。  
  
 テキスト テンプレート ファイルの任意の数は、プロジェクトに追加できます。 各テンプレートには、1 つの結果ファイルが生成されます。  
  
> [!NOTE]
>  DSL 定義を変更すると、サンプル テキスト テンプレートのコードは機能しません、更新する場合を除き。  
  
 詳細については、次を参照してください。[ドメイン固有言語からコードを生成する](../modeling/generating-code-from-a-domain-specific-language.md)と[ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)します。  
  
## <a name="customizing-the-dsl"></a>DSL のカスタマイズ  
 実験用インスタンスを閉じて、DSL 定義を変更する場合は、メインの定義を更新[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]インスタンス。  
  
> [!NOTE]
>  DSL 定義を変更した後は、以前のバージョンを使用して作成したテスト モデル内の情報を失う可能性があります。  たとえば、デバッグ ソリューションには、いくつかの図形とコネクタを含むサンプルをという名前のファイルが含まれています。 DSL 定義の作成を開始してから、表示されている可能性し、が失われる、ファイルを保存するとします。  
  
 DSL には、さまざまな拡張機能を行うことができます。 次の例では、可能性のような印象を提供します。  
  
 各変更後に、DSL 定義を保存 をクリックして**すべてのテンプレートの変換**で**ソリューション エクスプ ローラー**、キーを押します**f5 キーを押して**変更された DSL をテストします。  
  
### <a name="rename-the-types-and-tools"></a>名前の変更の種類とツール  
 既存のドメイン クラスとリレーションシップの名前を変更します。 たとえば、最小言語テンプレートから作成される Dsl 定義から開始する可能性があります行うファミリ ツリーを表す DSL を作成する、次の名前の変更操作。  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>ドメイン クラス、リレーションシップ、およびツールの名前を変更するには  
  
1.  DslDefinition ダイアグラムで名前を変更**ExampleModel**に**FamilyTreeModel**、 **ExampleElement**に**人**、**ターゲット**に**親**、および**ソース**に**子**します。 変更するには、各ラベルをクリックすることができます。  
  
     ![DSL 定義ダイアグラム - ファミリ ツリー モデル](../modeling/media/familyt_person.png "FamilyT_Person")  
  
2.  要素とコネクタ ツールの名前を変更します。  
  
    1.  ソリューション エクスプ ローラーの下にあるタブをクリックして、DSL エクスプ ローラー ウィンドウを開きます。 表示されない場合、**ビュー**  メニューから **その他のウィンドウ** をクリックし、 **DSL エクスプ ローラー**します。 DSL エクスプ ローラーは、DSL 定義図が作業中のウィンドウである場合にのみ表示されます。  
  
    2.  [プロパティ] ウィンドウを開き、DSL エクスプ ローラーとプロパティを同時に表示できるように配置します。  
  
    3.  DSL エクスプ ローラーで、**エディター**、**ツールボックス タブ**、 * \<DSL >*、し**ツール**します。  
  
    4.  クリックして**ExampleElement**します。 これは、ツールボックス項目要素を作成するために使用します。  
  
    5.  [プロパティ] ウィンドウで変更、**名**プロパティを**人**します。  
  
         注意して、**キャプション**プロパティも変更します。  
  
    6.  同じ方法での名前変更、 **ExampleConnector**ツールに**ParentLink**します。 Alter、**キャプション**プロパティことは、Name プロパティのコピーではないようにします。 たとえば、入力**親リンク**します。  
  
3.  DSL を再構築します。  
  
    1.  DSL 定義ファイルを保存します。  
  
    2.  クリックして**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー  
  
    3.  F5 キーを押します。 実験用インスタンスまで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]が表示されます。  
  
4.  実験用インスタンスでデバッグ ソリューションで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、テスト モデル ファイルを開きます。 ツールボックスから、そこに要素をドラッグします。 ツールのキャプションと DSL エクスプ ローラー内の型名が変更されたことに注意してください。  
  
5.  モデル ファイルを保存します。  
  
6.  .Tt ファイルを開き、古い型とプロパティの名前の新しい名前で置換します。  
  
7.  .Tt ファイルで指定されているファイル名がテスト モデルを指定することを確認します。  
  
8.  .Tt ファイルを保存します。 .Tt ファイルで、コードの実行の結果を表示する、生成されたファイルを開きます。 正しいことを確認します。  
  
### <a name="add-domain-properties-to-classes"></a>ドメインのプロパティをクラスに追加します。  
 たとえばを生年月日年と個人の死を表すためのドメイン クラスにプロパティを追加します。  
  
 図上の新しいプロパティを表示にするに追加する必要があります*デコレータ*図形に、モデル要素が表示されます。 プロパティは、デコレータにマップすることも必要があります。  
  
##### <a name="to-add-properties-and-display-them"></a>プロパティを追加し、それらを表示するには  
  
1.  プロパティを追加します。  
  
    1.  DSL 定義図で右クリックし、**人**ドメイン クラスを指す**追加**、 をクリックし、**ドメイン プロパティ**します。  
  
    2.  新しいプロパティ名の一覧を入力します。**生年月日**と**死**します。 キーを押して**Enter**ごとにします。  
  
2.  図形のプロパティを表示するデコレータを追加します。  
  
    1.  ダイアグラムのもう一方の側にユーザーのドメイン クラスから拡張する灰色の線に従います。 これは、図要素マップです。 ドメイン クラスを shape クラスにリンクします。  
  
    2.  この図形クラスを右クリックし、**追加**、クリックして**テキスト デコレータ**します。  
  
    3.  などの名前を持つ&2; つのデコレータを追加**BirthDecorator**と**DeathDecorator**します。  
  
    4.  新しいデコレータごとを選択し、[プロパティ] ウィンドウで、設定、**位置**フィールドです。 これは、図形のドメイン プロパティの値が表示される場所を決定します。 たとえば、設定**InnerBottomLeft**と**InnerBottomRight**します。  
  
         ![コンパートメント図形の定義](../modeling/media/familyt_compartment.png "FamilyT_Compartment")  
  
3.  プロパティに、デコレータにマップします。  
  
    1.  [DSL 詳細] ウィンドウを開きます。 それは、通常の出力ウィンドウの横にあるタブをクリックします。 表示されない場合、**ビュー**  メニューをポイント**その他のウィンドウ**、 をクリックし、 **DSL 詳細**します。  
  
    2.  DSL 定義図で、を結ぶ線をクリックして、**人**ドメイン クラスとシェイプ クラスです。  
  
    3.  **DSL 詳細**の**デコレータ マップ** タブで、マップされていないデコレータにあるチェック ボックスをクリックします。 **表示プロパティ**、するマッピング、ドメイン プロパティを選択します。 たとえば、マップ**BirthDecorator**に**生年月日**します。  
  
4.  DSL を保存して [すべてのテンプレートの変換] をクリックし、f5 キーを押してください。  
  
5.  サンプルのモデル図いることを確認することができます今すぐ選択した位置 をクリックしての値を入力します。 さらに、選択、**人**図形、[プロパティ] ウィンドウには、生年月日と死の新しいプロパティが表示されます。  
  
6.  .Tt ファイルでは、各ユーザーのプロパティを取得するコードを追加できます。  
  
 ![ファミリ ツリー ダイアグラム、ツールボックス、およびエクスプ ローラー](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>新しいクラスを定義します。  
 モデルには、ドメイン クラスとリレーションシップを追加できます。 たとえば、町、および個人が町で生活ことを表す新しいリレーションシップを表す新しいクラスを作成できます。  
  
 さまざまな種類のモデル図に、さまざまな種類の図形、または別の geometry 型および色を使用して図形は、ドメイン クラスをマップできます。  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>追加し、新しいドメイン クラスを表示するには  
  
1.  ドメイン クラスを追加し、モデル ルートの子を作成します。  
  
    1.  DSL 定義図をクリックして、**に埋め込みリレーションシップ**ツールで、ルート クラス をクリックして**FamilyTreeModel**、クリックし、図の空白部分をクリックします。  
  
         新しいドメイン クラスが表示されます、埋め込みリレーションシップと FamilyTreeModel に接続されています。  
  
         たとえば、名前、設定**町**します。  
  
        > [!NOTE]
        >  モデルのルートを除くすべてのドメイン クラスは、少なくとも&1; つの埋め込みリレーションシップのターゲットである必要がありますか、埋め込みの対象であるクラスから継承する必要があります。 このためは、埋め込みリレーションシップ ツールを使用してドメイン クラスを作成する多くの場合に便利です。  
  
    2.  たとえば、新しいクラスにドメイン プロパティを追加**名前**します。  
  
2.  Person および Town 間に参照リレーションシップを追加します。  
  
    1.  クリックして、**参照リレーションシップ**ツールを ユーザー をクリックし、町 をクリックします。  
  
         ![DSL 定義フラグメント: ファミリ ツリー ルート](../modeling/media/familyt_root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  参照リレーションシップは、モデル ツリーの&1; つの部分から間の相互参照を表します。  
  
3.  モデル図の町を表す図形を追加します。  
  
    1.  ドラッグ、**ジオメトリ シェイプ**の図は、ツールボックスからなど、名前に変更**TownShape**します。  
  
    2.  [プロパティ] ウィンドウでは、塗りつぶしの色とジオメトリなどの新しい図形の外観のフィールドを設定します。  
  
    3.  都市の名前を表示するデコレータを追加し、NameDecorator 名前を変更します。 位置プロパティを設定します。  
  
4.  町ドメイン クラスを TownShape にマップします。  
  
    1.  クリックして、**図要素マップ**ツールを町のドメイン クラスと、TownShape shape クラス をクリックします。  
  
    2.  **デコレータ マップ**のタブ、 **DSL 詳細**マップ コネクタでウィンドウを選択し、NameDecorator を確認し、設定**表示プロパティ**名にします。  
  
5.  人と町間のリレーションシップを表示するためのコネクタを作成します。  
  
    1.  図に、ツールボックスから、コネクタをドラッグします。 名前を変更し、その外観プロパティを設定します。  
  
    2.  使用して、**図要素マップ**Person および Town 間のリレーションシップを新しいコネクタをリンクするツールです。  
  
         ![追加された図形マップを使用したファミリ ツリー定義](../modeling/media/familyt_shapemap.png "FamilyT_ShapeMap")  
  
6.  新規町を行うため、要素ツールを作成します。  
  
    1.  **DSL エクスプ ローラー**、展開**エディター**し**ツールボックス タブ**します。  
  
    2.  右クリック* \<DSL >*  をクリックし、**新しい要素ツールの追加**します。  
  
    3.  設定、**名**プロパティの新しいツールと設定、**クラス**町へのプロパティです。  
  
    4.  設定、**ツールボックス アイコン**プロパティです。 Click **[...]**し、、**ファイル名**フィールドで、アイコン ファイルを選択します。  
  
7.  町とユーザー間のリンクを行うためのコネクタ ツールを作成します。  
  
    1.  右クリック* \<DSL >*  をクリックし、**新しいコネクタ ツールを追加**します。  
  
    2.  新しいツールの [名前] プロパティを設定します。  
  
    3.  **ConnectionBuilder**プロパティには、Person-town リレーションシップの名前を含むビルダーを選択します。  
  
    4.  設定、**ツールボックス アイコン**します。  
  
8.  DSL 定義を保存 をクリックして**すべてのテンプレートの変換**、キーを押します**f5 キーを押して**します。  
  
9. 実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、テスト モデル ファイルを開きます。 新しいツールを使用すると、都市、町および担当者の間のリンクを作成できます。 通知は、正しい種類の要素の間のリンクを作成することのみできます。  
  
10. それぞれの人が住んでいる都市を一覧表示するコードを作成します。 テキスト テンプレートは、このようなコードを実行する場所の&1; つです。 たとえば、次のコードが含まれるようにデバッグ ソリューション内の既存の Sample.tt ファイルを変更する可能性があります。  
  
    ```  
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>  
    <#@ output extension=".txt" #>  
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>  
  
    <#  
      foreach (Person person in this.FamilyTreeModel.People)  
      {  
    #>  
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>  
  
    <#  
          foreach (Person child in person.Children)  
      {  
    #>  
                <#= child.Name #>  
    <#  
      }  
      }  
    #>  
  
    ```  
  
     *.Tt ファイルを保存するときに、ユーザーと、ほとんどの一覧を含む従属ファイルを作成します。 詳細については、次を参照してください。[ドメイン固有言語からコードを生成する](../modeling/generating-code-from-a-domain-specific-language.md)です。  
  
## <a name="validation-and-commands"></a>検証とコマンド  
 検証制約を追加することでさらに、この DSL を開発する可能性があります。 これらの制約は、モデルが正しい状態であるかどうかを確認する方法を定義することができます。 たとえば、する制約を定義できることを確認する子の生年月日がその親の場合よりも後のです。 検証機能では、DSL のユーザーが、制約に違反するモデルを保存しようとすると、警告が表示されます。 詳細については、次を参照してください。[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)します。  
  
 ユーザーが呼び出すことのできるメニュー コマンドを定義することもできます。 コマンドは、モデルを変更できます。 操作では、その他のモデルでも[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]外部リソースを使用しています。 詳細については、次を参照してください。[方法: 標準メニュー コマンドを変更](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)します。  
  
## <a name="deploying-the-dsl"></a>DSL を展開します。  
 ドメイン固有言語を使用するには、他のユーザーを許可するように配布する、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension (VSIX) ファイルです。 DSL ソリューションをビルドするときに作成されます。  
  
 ソリューションの bin フォルダー内には、.vsix ファイルを見つけます。 これをインストールするコンピューターにコピーします。 そのコンピューターで VSIX ファイルをダブルクリックします。 すべてのインスタンスで、DSL を使用できます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]そのコンピューターにします。  
  
 実験用インスタンスを使用する必要はありませんので、自分のコンピューターに、DSL をインストールする同じ手順を使用する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
 詳細については、次を参照してください。[ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)します。  
  
##  <a name="a-namereseta-removing-old-experimental-dsls"></a><a name="Reset"></a>古い実験的な Dsl を削除します。  
 実験的な Dsl を作成した場合は、必要がなくなった、削除できますに自分のコンピューターからリセットすることで、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]実験用インスタンス。  
  
 すべての実験的な Dsl およびその他の実験的なコンピューターから削除されます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能です。 これらは、デバッグ モードで実行された拡張機能です。  
  
 この手順では、Dsl またはその他は削除されません[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX ファイルを実行することによって完全にインストールされている拡張機能です。  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Visual Studio 実験用インスタンスをリセットするには  
  
1.  をクリックして**開始**、 をクリックして**すべてのプログラム**、 **Microsoft Visual Studio 2010 SDK**、**ツール**、し**Microsoft Visual Studio 2010 実験用インスタンスをリセット**します。  
  
2.  すべての実験的な Dsl またはその他の実験を再構築[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]引き続き使用する拡張機能です。  
  
## <a name="see-also"></a>関連項目  
 [モデルの理解、クラスとリレーションシップ](../modeling/understanding-models-classes-and-relationships.md)   
 [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)   

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]



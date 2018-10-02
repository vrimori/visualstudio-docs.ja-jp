---
title: UML クラス図からコードを生成 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8874e5aa1c2dcf440c7cfed1cc2ce42c4187bdc1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533563"
---
# <a name="generate-code-from-uml-class-diagrams"></a>UML クラス ダイアグラムからコードを生成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[UML クラス図からコードを生成](https://docs.microsoft.com/visualstudio/modeling/generate-code-from-uml-class-diagrams)します。  
  
Visual Studio で UML クラス図から Visual c# .NET コードを生成するには、使用、**コードの生成**コマンド。 既定では、このコマンドにより、選択したそれぞれの UML 型に対して C# の型が生成されます。 コードを生成するテキスト テンプレートを変更またはコピーすることで、この動作を変更および拡張できます。 モデルの異なるパッケージに含まれる型に対して、異なる動作を指定することもできます。  
  
 **コードの生成**要素のユーザーの選択からコードを生成し、各 UML クラスまたはその他の要素の 1 つのファイルを生成するのには、コマンドは特に適しています。 たとえば、次のスクリーンショットには、2 つの UML クラスから生成された 2 つの C# ファイルが示されています。  
  
 代わりに、UML 要素と 1 対 1 の関係は、生成されたファイルがないコードを生成する場合を考えてで呼び出されるテキスト テンプレートの記述、**すべてのテンプレートの変換**コマンド。 その方法の詳細については、次を参照してください。 [UML モデルからファイルを生成](../modeling/generate-files-from-a-uml-model.md)します。  
  
 ![UML クラス図および生成された C&#35;クラス ファイル。](../modeling/media/oob-gencode1.png "oob_GenCode1")  
  
 Visual Studio での UML クラス図の詳細については、次のトピックを参照してください。  
  
-   [UML クラス図: リファレンス](../modeling/uml-class-diagrams-reference.md)  
  
-   [UML クラス図: ガイドライン](../modeling/uml-class-diagrams-guidelines.md)  
  
 UML クラス図をサポートする Visual Studio のバージョンを確認するを参照してください。[アーキテクチャとモデリング ツールのバージョンのサポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)します。  
  
## <a name="using-the-generate-code-command"></a>[コードの生成] コマンドの使用  
 次の手順の説明の既定の動作、**コードの生成**コマンド。  
  
#### <a name="to-generate-a-separate-file-for-each-element"></a>要素ごとに異なるファイルを生成するには  
  
1.  クラスを含む UML モデルを作成します。 モデル要素にはステレオタイプを適用できます。  
  
     詳細については、次を参照してください。[コード生成の変換の既定の](#default)します。  
  
2.  クラス図または**UML モデル エクスプ ローラー**コードを生成する要素を選択します。 次のいずれかを選択できます。  
  
    -   要素の特定のセット。  
  
    -   パッケージまたはモデル。その内容からコードを生成します。  
  
    -   図。図のすべての要素を選択します。  
  
3.  選択された要素のショートカット メニューを開き、選択し、**コードの生成**します。  
  
     初めて使用する**コードの生成**特定のモデル ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、モデルのコード生成パラメーターを編集できます。  
  
     選択**OK**これらのパラメーターを変更することがわかっていない限り、します。  
  
     後でこのダイアログ ボックスに戻り、開く**UML モデル エクスプ ローラー**します。 開く、モデリング プロジェクトのショートカット メニューを選び、**コード生成の設定**します。 詳細については、次を参照してください。[コードの生成コマンドのカスタマイズ](#custom)します。  
  
 C# コードが含まれるファイルが生成されます。 既定の設定では、C# クラス ライブラリ プロジェクトに、型ごとのファイルが生成されます。 ただし、この動作はカスタマイズできます。 詳細については、次を参照してください。[コードの生成コマンドのカスタマイズ](#custom)します。  
  
 いくつかの検証テストがモデルに適用されて、C# に変換できることが確認されます。 テストが失敗した場合は、エラー メッセージが表示され、コードの生成は実行されません。 検証メニュー コマンドを作成してある場合は、検証コマンドが失敗した要素に対してはコードが生成されません。 詳細については、次を参照してください。 [UML モデルの検証制約を定義](../modeling/define-validation-constraints-for-uml-models.md)します。  
  
##  <a name="default"></a> 既定のコード生成の変換  
 このセクションでは、によって生成される結果をまとめたものです、**コードの生成**コマンド、コマンドをカスタマイズする場合を除き、します。 詳細については、次を参照してください。[コードの生成コマンドのカスタマイズ](#custom)します。  
  
-   UML モデルで選択した型ごとに 1 つの C# 型が生成されます。 各型は、個別のコード ファイルに配置されます、 **GeneratedCode**フォルダー。  
  
-   UML の型がパッケージに含まれる場合、生成される C# 型は名前空間の内部に格納され、ファイルは名前空間と同じ名前のフォルダーに生成されます。  
  
-   UML クラスの `Attribute` ごとに、C# のプロパティが生成されます。  
  
-   UML 型の各 `Operation` に対して、C# のメソッドが生成されます。  
  
-   クラスが参加している誘導可能な関連付けごとに、C# のフィールドが生成されます。  
  
 各 UML 型にステレオタイプを追加することで、生成される C# 型の他のプロパティを制御できます。  
  
|**この c# の型を作成するには**|**作成する UML 型**|**このステレオタイプを適用します。**|  
|---------------------------------|----------------------------|-------------------------------|  
|クラス|クラス|\<none > または<br /><br /> C# class|  
|Interface|Interface|\<none > または<br /><br /> C# interface|  
|列挙型|列挙|\<none > または<br /><br /> C# enum|  
|Delegate|クラス|C# delegate|  
|構造体|クラス|C# struct|  
  
#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>型または他の要素にステレオタイプを設定するには  
  
1.  図または要素のショートカット メニューを開く**UML モデル エクスプ ローラー**を選び、**プロパティ**します。  
  
2.  **プロパティ**ウィンドウで、ドロップダウン矢印をクリックして、**ステレオタイプ**プロパティ、および適用するステレオタイプのチェック ボックスを選択します。  
  
    > [!TIP]
    >  C# のステレオタイプが表示されない場合は、対象のモデル要素が含まれるモデルまたはパッケージの C# プロファイルを有効にします。 パッケージまたはモデルのルート選択**UML モデル エクスプ ローラー**します。 次に、**プロパティ**ウィンドウで、選択**プロファイル**、c# プロファイルを有効にします。  
  
3.  展開、**ステレオタイプ**プロパティを設定できる追加のプロパティを参照してください。  
  
 **説明**型、属性、操作、および関連付けのプロパティに書き込まれる`<summary>`生成されたコード内のコメント。 型にリンクされているコメント要素は、`<remarks>` コメントに書き込まれます。  
  
## <a name="varying-the-generated-code"></a>生成されたコードの変更  
 生成されるコードは、各型、属性、または操作のプロパティによって異なります。 たとえば、設定した場合、 **Is Abstract**を true に、クラスのプロパティ、`abstract`キーワードは、生成されたクラスに表示されます。 設定した場合、**多重度**に属性の**0.\***、生成されたプロパティの場合は、`IEnumerable<>`型。  
  
 さらに、それぞれのステレオタイプでは、設定できる追加のプロパティが提供されます。 これらの値は、C# コードでは適切なキーワードに変換されます。 たとえば、クラスで `Is Static` プロパティを設定した場合、C# クラスは `static` になります。  
  
 これらの追加プロパティを設定するには、図でクラスまたは他の要素を選択します。 プロパティ ウィンドウで **ステレオタイプ**など、c# ステレオタイプを展開し**c# クラス**します。  クラスの場合、次のような追加プロパティがあります。  
  
-   CLR 属性  
  
-   Is Partial  
  
-   Is Static  
  
-   Is Unsafe  
  
-   パッケージの可視性  
  
 各属性と操作にも、設定できるステレオタイプ プロパティがあります。 新しい属性のプロパティが表示されない場合は、実行**コードの生成**します。  
  
##  <a name="custom"></a> コードの生成 コマンドをカスタマイズします。  
 **コードの生成**コマンドのテキスト テンプレートの設定を使用してモデル要素を変換することにより動作します。 テキスト テンプレートの詳細については、次を参照してください。[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。  
  
 テンプレートが一連の指定された*テキスト テンプレート バインディング*します。 テキスト テンプレートのバインドは、生成された出力を配置する場所、どのようなテンプレートを適用するか、およびの他のパラメーターを指定します、**コードの生成**コマンド。  
  
 実行すると、**コードの生成**コマンド、特定のモデルをモデルのルートにテンプレート バインディングの既定のセットをアタッチします。 これらのバインディングは、モデルのすべての要素に適用されます。  
  
 ただし、パッケージ、クラス、または他の要素に独自のバインディングをアタッチすることで、既定のバインディングをオーバーライドし、既定のバインディングに追加できます。 バインディングは、アタッチされている要素に含まれるすべての要素に適用されます。 たとえば、特定のパッケージに含まれるすべての型を、異なるテンプレートのセットで変換する場合、または異なるフォルダーに出力する場合は、パッケージにテンプレート バインディングをアタッチできます。  
  
 モデル要素にアタッチされているテンプレート バインディングを検査するには、省略記号をクリックして **[...]** で、**テキスト テンプレート バインディング**プロパティ ウィンドウでプロパティ。  
  
 **コードの生成**コマンドでは、選択した各モデル要素にテンプレートが適用されます。 各要素に対して適用されるテンプレートのセットは、モデルのルートに至るまで (ルートを含む) の上位コンテナーにアタッチされているテンプレートの組み合わせです。  
  
 このセットに同じ名前のテンプレート バインディングがある場合は、小さいコンテナーのバインディングによって大きいコンテナーのバインディングがオーバーライドされます。 たとえば、名前でバインドするにはモデル ルート**クラス テンプレート**します。 特定のパッケージの内容に適用される、独自のテンプレートには、定義された名前を持つ独自のテンプレート バインディング**クラス テンプレート**します。  
  
 1 つのモデル要素に複数のテンプレートを適用できます。 各モデル要素から複数のファイルを生成できます。  
  
> [!NOTE]
>  モデルのルートにアタッチされているバインディングは、そのモデルのすべての要素に対する既定値になります。 これらの既定のバインドを表示するには、開く**UML モデル エクスプ ローラー**します。 モデリング プロジェクトのショートカット メニューを開き、選択**コード生成の設定**します。 また、UML モデル エクスプローラーで、モデルのルートを選択することもできます。 [プロパティ] ウィンドウで次のように選択します **[...]。** で、**テキスト テンプレート バインディング**プロパティ。 バインドは、使用するまでは表示されません、**コードの生成**を少なくとも 1 回コマンドします。 テンプレート バインディングを図にアタッチすることはできません。  
  
#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>テキスト テンプレート バインディングをパッケージまたは他のモデル要素にアタッチするには  
  
1.  **UML モデル エクスプ ローラー**をモデル要素のショートカット メニューを開き、選択し、**プロパティ**します。 通常は、パッケージまたはモデルのルートに対してテキスト テンプレート バインディングをアタッチします。  
  
2.  **プロパティ**ウィンドウで、省略記号ボタン (**[...]**) で、**テキスト テンプレート バインディング**プロパティ。  
  
     **テキスト テンプレート バインディング** ダイアログ ボックスが表示されます。  
  
3.  選択**追加**新しいテキスト テンプレート バインディングを作成します。  
  
     \- または -  
  
     既存のバインディングを選択して編集します。  
  
     各テンプレート バインディングでは、指定したテンプレートを選択したモデル要素に適用する方法、および含まれる他のモデル要素が定義されています。  
  
4.  ダイアログ ボックスで、テキスト テンプレート バインディングのプロパティを設定します。  
  
    |**Property**|**説明**|  
    |------------------|---------------------|  
    |名前|このバインディングの名前。 上位のパッケージまたはモデルから継承されたバインディングをオーバーライドするには、オーバーライド対象のバインディングと同じ名前を使用します。|  
    |上書き|true の場合、既存のコードを上書きします。|  
    |ターゲット名|生成されるファイルの名前。<br /><br /> などの式をこの文字列に挿入できる`{Name}`または`{Owner.Name}`します。 たとえば、作成する:`{Owner.Name}_{Name}`します。 式は、モデル要素に対して評価されます。 要素のプロパティは使用できますが、メソッドのプロパティは使用できません。 型のプロパティに場所をどのようなプロパティを使用できるを検索する**Microsoft.VisualStudio.Uml\* 。**. **重要:** `{Name}`または`{Owner.Name}`でのみ使用できます、**ターゲット名**プロパティ。   生成されるクラスの名前を変更するには、テンプレートを変更する必要があります。 詳細については、次を参照してください。[テキスト テンプレートの作成](#writing)です。|  
    |プロジェクト パス|変換の出力ファイルを格納する [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトへのパスを指定します。 新しいプロジェクトを作成するには、型指定された値を使用します。 省略記号ボタン (**[...]**) を既存のプロジェクトを選択します。<br /><br /> 存在しない場合は、新しいプロジェクトが作成されます。 作成されるプロジェクトは、C# クラス ライブラリ プロジェクトになります。<br /><br /> そのためには、プロジェクト ディレクトリを入力する必要があります。 %ProgramFiles% や %LocalAppData% などの環境変数マクロを使用できます。|  
    |ターゲット ディレクトリ|ターゲット ファイルが生成されるフォルダー。 このパスはプロジェクト フォルダーが基準になります。<br /><br /> 上位のパッケージの名前に対応するパスを挿入するには、`{PackageStructure}` 式を使用できます。 既定値は `\GeneratedCode\{PackageStructure}` です。 %TEMP% や %HomePath% などの環境変数を使用することもできます。 **重要:** `{PackageStructure}`でのみ使用できます、**ターゲット ディレクトリ**プロパティ。  |  
    |テンプレート ファイル パス|変換を実行するテンプレート。<br /><br /> 提供されているテンプレートを使用することも、独自に作成することもできます。 提供されているテンプレートは、次の場所にあります。<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\|  
  
5.  必要なだけいくつでもバインディングを要素にアタッチできます。  
  
##  <a name="writing"></a> テキスト テンプレートの作成  
 独自のテキスト テンプレートを作成できます。 テキスト テンプレートでは、プログラム コードまたは他の任意の種類のテキスト ファイルを生成できます。  
  
 標準テンプレートのコピーを変更することをお勧めします。 テンプレートは次の場所からコピーできます。  
  
 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  
  
 テキスト テンプレートの詳細については、次のトピックを参照してください。  
  
-   テキスト テンプレートは生成されるファイルのプロトタイプであり、生成されるテキストと、モデルを読み取るプログラム コードの両方が含まれます。 詳細については、次を参照してください。[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。  
  
-   プログラム コードで UML モデル内を移動するには、UML API を使用する必要があります。 詳細については、次を参照してください。 [UML モデル内を移動](../modeling/navigate-the-uml-model.md)と[UML モデリング機能拡張の API リファレンス](../modeling/api-reference-for-uml-modeling-extensibility.md)します。  
  
 テンプレートを使用して、**コードの生成**コマンド、Modeling ディレクティブを含める必要があります。 例えば:  
  
 `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  
  
 `ElementType` 属性では、このテンプレートを適用する UML 要素の種類を定義します。  
  
 テンプレートでは、`this` は次のプロパティを持つ一時クラスに属します。  
  
-   `Element` = テンプレートが適用されている UML の <xref:Microsoft.VisualStudio.Uml.Classes.IElement>。  
  
-   `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  
  
-   `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
-   `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>。 詳細については、次を参照してください。[を他のモデルおよびツールとの統合の UML モデル](../modeling/integrate-uml-models-with-other-models-and-tools.md)します。  
  
-   `ProfileName` = "C#Profile"  
  
-   `ServiceProvider`: <xref:System.IServiceProvider>  
  
-   `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>。  
  
-   `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>。 これは、UML ModelStore が実装されている Visualization and Modeling SDK ストアです。 UML の <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore> を取得するには、`this.Element.GetModelStore()` を使用します。  
  
 テキスト テンプレートを作成するときは、以下のことが役に立つ場合があります。 この情報がで詳しく説明されている[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。  
  
-   生成されるファイル名の拡張子は、`Output` ディレクティブで設定できます。 すべてのテキスト テンプレートに `Output` ディレクティブが 1 つ必要です。  
  
-   一部のアセンブリはテンプレートで自動的に参照されます。 このようなアセンブリの例としては、System.dll や Microsoft.VisualStudio.Uml.Interfaces.dll などがあります。  
  
     生成用のプログラム コードで他のアセンブリを使用するには、`Assembly` ディレクティブを使用します。 次に例を示します。  
  
     `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  
  
-   `System` などの一部の名前空間は、プログラム コードに自動的にインポートされます。 他の名前空間については、`Import` ディレクティブを `using` ステートメントと同じ方法で使用できます。 次に例を示します。  
  
     `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  
  
     `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  
  
-   別のファイルのテキストを参照するには、`Include` ディレクティブを使用します。  
  
-   角かっこで囲まれたテンプレートのパーツ`<# ... #>`によって実行される、**コードの生成**コマンド。 かっこの外側にあるテンプレートの部分は、生成されるファイルにコピーされます。 生成するコードと生成されるテキストを区別することが重要です。 生成されるテキストには任意の言語を使用できます。  
  
-   `<#= Expressions #>` は評価されて、文字列に変換されます。  
  
## <a name="see-also"></a>関連項目  
 [UML クラス図: リファレンス](../modeling/uml-class-diagrams-reference.md)   
 [UML クラス図: ガイドライン](../modeling/uml-class-diagrams-guidelines.md)   
 [UML モデルからファイルを生成する](../modeling/generate-files-from-a-uml-model.md)




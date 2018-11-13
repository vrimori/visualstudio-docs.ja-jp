---
title: Microsoft ヘルプ ビューアー SDK |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37512da136348a15792c11aae02bab9250c43670
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000901"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft ヘルプ ビューアー SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

この記事には、Visual Studio ヘルプ ビューアーのインテグレーターの次のタスクが含まれています。

-   (F1 サポート) トピックの作成

-   ヘルプ ビューアーのコンテンツ ブランド パッケージを作成します。

-   一連の記事を展開します。

-   Visual Studio shell (統合または分離) に追加のヘルプ

-   その他のリソース

### <a name="creating-a-topic-f1-support"></a>(F1 サポート) トピックの作成
 このセクションでは、表示されるトピックで、トピックの要件、(F1 サポート要件を含む) のトピックと、最後に、例のトピックをその表示された結果を作成する方法の簡単な説明のコンポーネントの概要を示します。

 **ヘルプ ビューアーのトピックの概要**

 ヘルプ ビューアーがインストールまたは XHTML、トピックと共に、最後の更新時にトピックに関連付けられているブランド パッケージ要素を取得し、提示されたコンテンツ ビューに結果として、2 つの結合トピックは、レンダリングが呼び出されると、(データをブランド化 +トピックの「データの場合)。  ブランド パッケージには、ロゴ、コンテンツの動作、およびブランド化テキスト (著作権など) のサポートが含まれています。  パッケージのブランド化要素の詳細については、以下の「ブランド パッケージの作成」を参照してください。  イベント トピックに関連付けられているブランド パッケージはありませんが、ヘルプ ビューアーはヘルプ ビューアーのアプリケーション ルート (Branding_en US.mshc) にあるフォールバック ブランド パッケージを使用します。

 **ヘルプ ビューアーのトピックの要件**

 ヘルプ ビューアー内に正しくレンダリングされる、生のトピックのコンテンツは、W3C の基本的な 1.1 XHTML する必要があります。

 通常、トピックには、2 つのセクションが含まれます。

- メタデータ (コンテンツのメタデータ参照を参照してください)。 トピックの「一意の ID、キーワードの値、トピックの目次の ID などのトピックについてのデータは親ノードの ID などです。

- 本文のコンテンツ: 1.1 XHTML の基本的な W3C に準拠しているが含まれています (折りたたみ可能な領域、コード スニペットなどコンテンツの動作をサポートです。完全な一覧は、次に示します)。

  Visual Studio ブランド パッケージには、コントロールがサポートされています。

- リンク

- CodeSnippet

- CollapsibleArea

- 継承されたメンバー

- LanguageSpecificText

  サポートされている言語の文字列 (いない大文字小文字を区別):

- javascript

- csharp または (c#)

- cplusplus visualc++ または c + +

- jscript

- visual basic または vb

- f# または fsharp または fs

- – 他の言語の名前を表す文字列

  **ビューアーのヘルプ トピックの作成**

  ContosoTopic4.htm、という名前の新しい XHTML ドキュメントを作成し、title タグ (下記) を含めます。

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 次に、どのトピックを (単独かどうかをブランド化された)、表示の方法を定義するデータを追加 (その他のトピックでリンク参照) をその ID、TOC 内のこのトピックでの存在、f1 キーをこのトピックを参照するなど。サポートされているメタデータの完全な一覧については、次の表「コンテンツ メタデータ」を参照してください。

- この場合は、独自のブランド化パッケージを Visual Studio ヘルプ ビューアーのブランド パッケージの一種を使用します。

- F1 メタデータの名前と値の追加 ("Microsoft.Help.F1"コンテンツ"ContosoTopic4"=) は、IDE のプロパティ バッグ内の指定された F1 値と一致します。  (詳細については、f1 キーのサポート セクションを参照してください)。 これは、f1 キーに一致する値、IDE で f1 キーを選択すると、このトピックを表示する IDE 内から呼び出します。

- トピック ID を追加します。 このトピックにリンクするその他のトピックで使用される文字列です。  これは、このトピックではヘルプ ビューアー ID です。

- 目次のこのトピックの目次ノードが表示される場所を定義する、このトピックの親ノードを追加します。

- 目次のこのトピックのノードの順序を追加します。 親ノードに子ノードの n の数が設定されているときは、このトピックの場所の子ノードの順序で定義します。 たとえば、このトピックでは、4 つの子トピックの数 4)。

  メタデータ セクションの例:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>

```

 **トピックの本文**

 ページのリンク、注のセクションで、折りたたみ可能な領域、コード スニペットでは、および言語の特定のテキストのセクションのトピックの本文 (ヘッダーとフッターは含まれません) が含まれます。  これらの領域については、表示されるトピックのブランド化のセクションを参照してください。

1.  トピックの「title タグを追加します。  `<div class="title">Contoso Topic 4</div>`

2.  注」セクションを追加します。 `<div class="alert"> add your table tag and text </div>`

3.  折りたたみ可能な領域を追加します。  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4.  コード スニペットを追加します。  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5.  コード言語の特定のテキストの追加: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` devLangnu ことに注意してください = その他の言語を入力することができます。 DevLangnu など ="Fortran"Fortran が表示されるときに、コード スニペット DisplayLanguage Fortran を =

6.  ページのリンクを追加します。 `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
>  注: のサポートされていない新しい「表示言語」(例では、 F#、Cobol、Fortran) コードの色付け、コード スニペットでは白黒になります。

 **ビューアーのヘルプ トピックを例**コードは、メタデータ、コード スニペット、折りたたみ可能な領域、および特定のテキストの言語を定義する方法を示しています。

```
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>

```

 **F1 サポート**

 Visual Studio で、f1 キーを選択すると、IDE 内でカーソルの位置から指定された値を生成し、入力します「プロパティ バッグ」と指定された値 (カーソル位置に基づきます。 カーソルが機能 x の上にあるときは、機能 x はアクティブ/にフォーカスし、値を持つプロパティ バッグを入力します。  F1 キーを選択すると、プロパティ バッグが設定され、顧客の既定のヘルプ ソースがローカルまたはオンラインかどうかを次のコードを Visual Studio の F1 (オンラインの既定値)、ユーザーの設定に基づく適切な文字列を作成し (オンラインは、既定値): シェルの実行(ヘルプ管理者ガイド exe の起動パラメーターを参照してください)、ローカルのヘルプ ビューアーとローカルのヘルプが既定値、またはパラメーター リストでキーワードを使って MSDN URL の場合は、プロパティ バッグからキーワードのパラメーターを使用します。

 複数値の文字列として実行する最初の用語では、参照、ヒットのと呼ばれる場合は、f1 キーを 3 つの文字列が返されるかどうかが見つかると、完了です。ない場合は、次の文字列に移動します。  順序は重要です。 複数値キーワードのプレゼンテーションを最も短い文字列の最大長の文字列があります。  複数値キーワードの場合は、これを確認するには、オンラインの F1 URL の文字列は、選択したキーワードが含まれますで確認できます。

 Visual Studio 2012 で意図的に行いましたより強力な除算オンラインとオフラインの間でオンラインの場合、ユーザーの設定は、単に渡すように F1 要求、クエリのオンライン サービスに直接ヘルプ ライブラリ エージェントを介してルーティングするのではなく、MSDN にVisual Studio 2010 にありました。 後の状態に依存して"インストールされている仕入先のコンテンツ = true"をそのコンテキストで異なる処理を実行するかどうかを判断します。 True の場合、お客様のサポートを希望に応じて、この解析およびルーティング ロジックを実行します。 False の場合、し、ここに移動する MSDN です。 ユーザーの設定がローカルにある場合は、し、すべての呼び出しは、ローカル ヘルプのエンジンに移動します。

 F1 フロー ダイアグラム:

 ![F1 フロー](../../extensibility/internals/media/f1flow.png "F1flow")

 ヘルプ ビューアーの既定のヘルプ コンテンツ ソースをオンライン (ブラウザーで起動) を設定するとします。

- Visual Studio パートナー (VSP) 機能は、F1 プロパティ バッグ (プロパティ バッグ prefix.keyword と、レジストリで見つかったプリフィックスの online の URL) に値を出力: F1 VSP URL + パラメーターをブラウザーに送信します。

- Visual Studio の機能 (言語のエディター、Visual Studio の特定のメニュー項目など): F1 は、Visual Studio の URL をブラウザーに送信します。

  ヘルプ ビューアーの既定のヘルプ コンテンツ ソースをローカルのヘルプ (ヘルプ ビューアーで起動) を設定すると。

- F1 プロパティ バッグとローカル ストアのインデックス間のキーワードの一致する VSP 機能 (プロパティ バッグ prefix.keyword は、ローカル ストアのインデックス内で見つかった値を =): F1 ヘルプ ビューアーでトピックを表示します。

- Visual Studio の機能 (Visual Studio の機能から生成されたプロパティ バッグをオーバーライドする VSP のオプションはありません): F1 ヘルプ ビューアーでの Visual Studio のトピックを表示します。

  ヘルプ コンテンツの仕入先の F1 フォールバックを有効にするのには、次のレジストリ値を設定します。 フォールバックの F1 ヘルプ ビューアーがオンラインでの F1 ヘルプ コンテンツを検索する設定を仕入先のコンテンツをローカル ユーザーのハード ドライブにインストールを意味します。 場合でも、オンライン ヘルプの既定の設定は、ローカル ヘルプ コンテンツのヘルプ ビューアーになります。

1. 設定、 **VendorContent**ヘルプ 2.1 のレジストリ キー値。

   -   32 ビット オペレーティング システム。

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent"= dword:00000001

   -   64 ビット オペレーティング システム。

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent"= dword:00000001

2. 2.1 のヘルプのレジストリ キーの下のパートナーの名前空間を登録します。

   - 32 ビット オペレーティング システム。

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Partner<em>\\< 名前空間\></em>

      「場所"=」オフライン"

   - 64 ビット オペレーティング システム。

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner<em>\\< 名前空間\></em>

      「場所"=」オフライン"

   **解析する基本のネイティブ Namespace**

   ネイティブのベース名前空間の解析を有効にするレジストリに新しい DWORD して追加の名前: BaseNativeNamespaces 1 (をサポートする、カタログ キー) の下にその値を設定します。  たとえば、Visual Studio のカタログを使用する場合は、パスにキーを追加できます。

   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   ヘッダー/メソッドが検出された形式で、F1 キーワード、ときの '/' 文字は次の構成体は、その結果、解析されます。

- ヘッダー: は、レジストリに登録するために使用する名前空間になります

- 方法: このなりますを介して渡されたキーワード。

  たとえば、CustomLibrary と呼ばれるカスタム ライブラリと、f1 キーを要求を受け取ったこととして書式設定するときに、MyTestMethod に呼び出されるメソッドを指定`CustomLibrary/MyTestMethod`します。

  ユーザーがパートナー hive では、下の名前空間として CustomLibrary を登録し、および状況が該当する任意の場所のキーを指定でき、クエリに渡されるキーワード MyTestMethod になります。

  **デバッグ ツール、IDE のヘルプを有効にします。**

  次のレジストリ キーと値を追加します。

  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\Dynamic ヘルプ キー: 小売価格でのデバッグ出力を表示します [はい]。

  [ヘルプ] メニュー項目で、IDE で「ヘルプ コンテキストのデバッグ」を選択します。

  **コンテンツのメタデータ**

  次の表では、角かっこの間に表示される任意の文字列は認識されている値で置き換える必要があるプレース ホルダーです。 たとえば、\<メタ name="Microsoft.Help.Locale"コンテンツ =「[言語コード]」/>、「[言語コード]」をなどの値で置換する必要があります"en-米国"。

|プロパティ (HTML 形式)|説明|
|--------------------------------------|-----------------|
|\< メタ name="Microsoft.Help.Locale"内容 =「[言語コード]」/>|このトピックでは、ロケールを設定します。 トピックでは、このタグを使用する場合は、1 回だけ使用する必要がありには、他の Microsoft ヘルプのタグの上に挿入する必要があります。 このタグを使用しない場合、トピックの本文が指定されている場合、製品のロケールに関連付けられているワード ブレーカーを使用してインデックスが作成します。それ以外の場合、en-私たちのワード ブレーカーを使用します。 このタグは、ISOC RFC 4646 に準拠します。 Microsoft ヘルプが正しく動作することを確認するには、するには、一般的な言語属性の代わりにこのプロパティを使用します。|
|\< メタ name="Microsoft.Help.TopicLocale"内容 =「[言語コード]」/>|その他のロケールを使用しても、このトピックでは、ロケールを設定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 カタログには、1 つ以上の言語でコンテンツが含まれている場合は、このタグを使用します。 カタログ内の複数のトピックでは、同じ ID を使用できますが、それぞれ一意 TopicLocale を指定する必要があります。 カタログのロケールに一致する TopicLocale を示すトピックでは、目次に表示されるトピックです。 ただし、トピックのすべての言語バージョンは、検索結果に表示されます。|
|\< タイトル > [Title]\</title >|このトピックのタイトルを指定します。 このタグが必要、トピックの 1 回だけ使用する必要があります。 トピックの本文にタイトルが含まれていないかどうかは\<div > とコンテンツのテーブルのトピックのセクションでは、このタイトルが表示されます。|
|\< メタデータ名 ="Microsoft.Help.Keywords"内容 ="[aKeywordPhrase]"/>|ヘルプ ビューアーのインデックスのウィンドウに表示されるリンクのテキストを指定します。 リンクがクリックされたときに、トピックが表示されます。トピックでは、複数のインデックス キーワードを指定するか、インデックスに表示するには、このトピックにリンクしたくない場合は、このタグを省略できます。 以前のバージョンのヘルプ キーワードを"K"は、このプロパティに変換できます。|
|\< メタ name="Microsoft.Help.Id"内容 ="[TopicID]"/>|このトピックの識別子を設定します。 このタグが必要、トピックの 1 回だけ使用する必要があります。 ID は、カタログを同じロケールの設定を持つトピックの間で一意である必要があります。 別のトピックでは、この ID を使用して、このトピックへのリンクを作成できます。|
|\< メタ name="Microsoft.Help.F1"content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|このトピックでは、F1 キーワードを指定します。 トピックでは、複数の F1 キーワードを指定するか、アプリケーション ユーザーが f1 キーを押したときに表示するには、このトピックしたくない場合は、このタグを省略することができます。 通常は、トピックの 1 つだけの F1 キーワードを指定します。 以前のバージョンのヘルプ キーワードを"F"は、このプロパティに変換できます。|
|\< メタデータ名"Description"のコンテンツを = =「[トピックの説明]」/>|このトピックの内容の簡単な概要を提供します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 このプロパティは、クエリ ライブラリによって直接アクセスします。インデックス ファイルには格納されません。|
 メタ name="Microsoft.Help.TocParent"内容 ="[parent_Id]"/>|このトピックの親トピックの目次を指定します。 このタグが必要、トピックの 1 回だけ使用する必要があります。 値は、親の Microsoft.Help.Id です。 トピックには、コンテンツのテーブルの 1 つの場所を持つことができます。 「-1」では、目次のルートのトピックの「ID をと見なされます。 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]、そのページは、ヘルプ ビューアー ホーム ページ。 これは、同様の理由が表示されること上部にあるレベルを確認するいくつかのトピックを具体的には TocParent = 1 を追加します。ヘルプ ビューアーのホーム ページは、システム ページと置き換え可能なためです。 コンテンツのセットに加わることがありますが、ヘルプ ビューアーのヘルプ ビューアー ホーム – システムのページを常に使用する場合、VSP が-1 の ID を持つページを追加しようとすると、|
|\< メタ name="Microsoft.Help.TocOrder"内容 =「[正の整数]」/>|目次の内容でこのトピックが表示される場所のピアのトピックを基準を指定します。 このタグが必要、トピックの 1 回だけ使用する必要があります。 値は、整数です。 トピックでは高い値の整数を指定します、小さい方の値の整数を指定するトピックが表示されます。|
|\< メタ name="Microsoft.Help.Product"内容 =「[製品コード]」/>|このトピックで説明する製品を指定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 この情報は、ヘルプのインデクサーに渡されるパラメーターとしても指定することができます。|
|\< メタ name="Microsoft.Help.ProductVersion"内容 =「[バージョン番号]」/>|このトピックで説明する製品のバージョンを指定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 この情報は、ヘルプのインデクサーに渡されるパラメーターとしても指定することができます。|
|\< メタ name="Microsoft.Help.Category"内容 ="[string]"/>|コンテンツのサブセクションを識別するために、製品で使用します。 トピックでは、複数のサブセクションを識別するまたは任意のサブセクションを識別するためにリンクしたくない場合は、このタグを省略できます。 このタグを使用して、以前のバージョンのヘルプからトピックが変換されるとき、TargetOS と TargetFrameworkMoniker 属性を格納します。 コンテンツの形式は、AttributeName:AttributeValue です。|
|\< メタ name="Microsoft.Help.TopicVersion コンテンツ ="[トピックの「バージョン番号]"/>|複数のバージョンがカタログに存在する場合は、このバージョンのトピックを指定します。 このタグはトピックの 1 つ以上のバージョンに存在する場合、カタログ、たとえば、カタログでは、.NET Framework 3.5 とトピックのトピックを含む、.NET Framework 4 のどちらも同じマイクロときに、必要なため、一意である Microsoft.Help.Id は限りませんが、します。ソフトです。Help.Id します。|
|\< メタデータ名"SelfBranded"コンテンツを = =「TRUE または FALSE」/>|ここでは、ヘルプ ライブラリ マネージャーのスタートアップのブランド パッケージまたはトピックに固有のブランド パッケージかどうかを指定します。 このタグは TRUE である必要がありますまたは FALSE。 場合は、関連するトピックのブランド パッケージは、ヘルプ ライブラリ マネージャーを開始するので、その他のコンテンツのレンダリングとは異なる場合でもを意図したとおり、トピックが表示されるときに設定されているブランド パッケージをオーバーライドし、TRUE になります。 FALSE の場合は、ヘルプ ライブラリ マネージャーの開始時に設定されているブランド パッケージに従って、現在のトピックが表示されます。 既定では、ヘルプ ライブラリ マネージャー前提を false に SelfBranded 変数が TRUE であると宣言されない限り自己ブランド化そのため、宣言する必要はない\<メタ名"SelfBranded"コンテンツを = ="FALSE"/>。|

### <a name="creating-a-branding-package"></a>ブランド パッケージを作成します。
 Visual Studio のリリースには、Visual Studio パートナーの統合シェルと分離を含む別の Visual Studio 製品数が含まれます。  各製品には、ある程度のサポート、製品に固有のブランド化トピック ベースのヘルプ コンテンツが必要です。  たとえば、Visual Studio のトピックが必要です、一貫性のあるブランド プレゼンテーション ISO シェルをラップする SQL Studio は、独自固有のヘルプ コンテンツのブランド化の各トピックが必要です。  統合の Shell パートナーは、ブランド化、独自のトピックを維持しながら Visual Studio 製品のヘルプ コンテンツの親内に、ヘルプ トピックを必要があります。

 ブランド パッケージは、ヘルプ ビューアーを格納している製品によってインストールされます。  Visual Studio 製品。

- フォールバック ブランド パッケージ (Branding_\<ロケール > .mshc)、ヘルプ ビューアー 2.1 アプリのルートにインストールされている (例: C:\Program Files (x86) \Microsoft Help Viewer\v2.1) によって、ヘルプ ビューアー言語パック。  これはパッケージをブランド化のいずれかの製品がインストールされていない場合に使用されます (コンテンツがインストールされていない) か、インストールされているブランド パッケージが壊れています。  Visual Studio の要素 (ロゴとフィードバック) には、アプリケーション ルートのフォールバック ブランド パッケージを使用する場合は無視されます。

- コンテンツ パッケージ サービスから Visual Studio コンテンツがインストールされている、ブランド パッケージは (最初の時間のコンテンツのインストール シナリオ) にもインストールされます。  ブランド パッケージの更新プログラムがある場合は、次のコンテンツの更新または追加のパッケージのインストール操作が発生したときに更新プログラムがインストールします。

  Microsoft ヘルプ ビューアーでは、トピックの「メタデータに基づいてトピックのブランド化をサポートします。

- トピックの「メタデータを定義してブランド セルフ = true レンダリングのトピックでは、(ブランド) に関して何もしません。

- = False のトピックでメタデータを定義してブランド セルフ TopicVendor メタデータの値に関連付けられているブランド パッケージを使用します。

- コンテンツの場所のトピックのメタデータには、name="Microsoft.Help.TopicVendor が定義されています"=\<ベンダー MSHA でブランド パッケージ名 >、コンテンツの値で定義されているブランド パッケージを使用します。

- Visual Studio カタログはブランド パッケージの優先度のアプリケーションがあります。  最初の Visual Studio の既定ブランドが適用され、次でサポートされ、トピックの「メタデータで定義されている場合 (インストール msha で定義) された関連付けられているブランド パッケージ、、オーバーライドとして定義されているベンダーをブランド化が適用されます。

  ブランド化要素は、通常、次の 3 つの主なカテゴリに分類されます。

- (例については、[フィードバック] リンク、条件付きの免責、ロゴ) ヘッダー要素

- コンテンツの動作 (例は、展開/折りたたみコントロールのテキスト要素を含めるし、コード スニペットの要素)

- フッター要素 (著作権情報の例)

  項目のブランド化された要素を含めると見なされます (この仕様に記載)。

- カタログ/製品のロゴ (例、Visual Studio)

- フィードバックのリンクと電子メールの要素

- 免責事項

- 著作権テキスト

  Visual Studio ヘルプ ビューアーのブランド パッケージのサポート ファイルは次のとおりです。

- グラフィックス (ロゴ、アイコンなど。)

- Branding.js – スクリプト ファイルのコンテンツの動作をサポート

- Branding.xml – カタログ コンテンツの間で一貫して使用される文字列。  注: Visual Studio、branding.xml 内のテキスト要素のローカリゼーション インクルード _locID ="\<一意の値 >"

- Branding.css – プレゼンテーション一貫性を保つのためのスタイルの定義

- Printing.css – の一貫性のあるプレゼンテーションの印刷スタイルの定義

  前述のように、ブランド パッケージは、トピックに関連付けられました。

- ときに SelfBranded = false がメタデータで定義されている、トピックは、パッケージをブランド化カタログを継承

- または SelfBranded = false と一意のブランド パッケージに定義されて、MSHA 使用可能なコンテンツがインストールされている場合

  カスタム ブランド パッケージを実装する Vsp (VSP コンテンツ、SelfBranded = True)、続行する方法の 1 つは、(ヘルプ ビューアーを使用したインストール)、フォールバック ブランド パッケージから開始し、適切なファイルの名前を変更します。  Branding_\<ロケール > .mshc ファイルは、.mshc に変更されたファイル拡張子を持つ zip ファイル、単純に .mshc から拡張子を .zip に変更し、コンテンツを抽出します。  ブランド パッケージ要素の下を参照してくださいし、必要に応じて変更 (VSP ロゴおよび Branding.xml ファイル内のロゴへの参照にロゴを変更する、VSP 仕様など 1 Branding.xml を更新など。)。

  すべての変更が完了すると、目的のブランド化要素を含む zip ファイルを作成し、拡張機能を .mshc に変更します。

  カスタム ブランド パッケージに関連付けるには、コンテンツの mshc (トピックを含む) とブランド化 mshc ファイルへの参照を含む、MSHA を作成します。  基本的な MSHA を作成する方法については、"MSHA"の下を参照してください。

  Branding.xml ファイルには、一貫してトピックが含まれている場合、トピックの特定のアイテムの描画に使用リストの要素が含まれています。\<メタ name="Microsoft.Help.SelfBranded"内容 ="false"/>。  Visual Studio の Branding.xml ファイル内の要素の一覧は、以下に記載されています。  この一覧は、ニーズの ISO シェル採用者を満たす製品のブランドの独自のこれらの要素 (たとえばロゴ、フィードバック、および著作権) を変更するためのテンプレートを使用する対象としています。

  注:"{n}"の先の変数は、コードの依存関係を持つ – を削除するか、これらの値を変更すると、エラーおよびアプリケーション クラッシュの原因の可能性があります。Visual Studio ブランド パッケージには、ローカリゼーション識別子 (例 _locID="codesnippet.n") が含まれます。

  **Branding.xml**

|||
|-|-|
|機能:|**CollapsibleArea**|
|使用:|折りたたまれてコンテンツ コントロールのテキストを展開します。|
|**要素**|**[値]**|
|ExpandText|Expand|
|CollapseText|折りたたむ|
|機能:|**CodeSnippet**|
|使用:|コード スニペットのコントロールのテキスト。  注:「改行」領域でのコード スニペットのコンテンツは、スペースに変更されます。|
|**要素**|**[値]**|
|CopyToClipboard|クリップボードにコピー|
|ViewColorizedText|色付きテキストで表示|
|CombinedVBTabDisplayLanguage|Visual Basic (サンプル)|
|VBDeclaration|宣言|
|VBUsage|使用法|
|機能:|**フィードバック、フッター、およびロゴ**|
|使用:|電子メールを使用して現在のトピックに関するフィードバックを提供する顧客のフィードバック コントロールを提供します。  コンテンツの著作権テキスト。  ロゴの定義。|
|**要素**|**値 (これらの文字列はコンテンツの導入者のニーズを満たすために変更できます)。**|
|著作権情報|© 2013 Microsoft Corporation. All rights reserved.|
|SendFeedback|\<a ="{0}" {1}> フィードバックの送信\</a > を Microsoft には、このトピックでします。|
|FeedbackLink||
|LogoTitle|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk.gif|
|LogoFileNameHC|vs_logo_wh.gif|
|機能:|**免責事項**|
|使用:|一連のマシンのケースに関する免責事項に翻訳されたコンテンツを指定します。|
|**要素**|**[値]**|
|MT_Editable|この記事では、機械翻訳されたものでした。 インターネット接続があれば、同時に元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|
|MT_NonEditable|この記事では、機械翻訳されたものでした。 インターネット接続があれば、同時に元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|
|MT_QualityEditable|この記事では手動翻訳されたものです。 インターネット接続があれば、同時に元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|
|MT_QualityNonEditable|この記事では手動翻訳されたものです。 インターネット接続があれば、同時に元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|
|MT_BetaContents|この記事では、機械翻訳、暫定版用でした。 インターネット接続があれば、同時に元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|
|MT_BetaRecycledContents|この記事では、暫定版用手動翻訳されたものです。 インターネット接続があれば、同時に元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|
|機能:|**LinkTable**|
|使用:|オンラインのトピックへのリンクのサポート|
|**要素**|**[値]**|
|LinkTableTitle|リンク テーブル|
|TopicEnuLinkText|英語版が表示\</a > のこのトピックでは、コンピューターで使用します。|
|TopicOnlineLinkText|このトピックを表示\<、href ="{0}" {1}> オンライン\</a >|
|OnlineText|Online|
|機能:|**ビデオのオーディオ コントロール**|
|使用:|要素およびビデオ コンテンツのテキストを表示します。|
|**要素**|**[値]**|
|MultiMediaNotSupported|サポートするには、Internet Explorer 9 またはインストール中に大きくする必要があります。{0}コンテンツ。|
|VideoText|ビデオの表示|
|AudioText|オーディオのストリーミング|
|OnlineVideoLinkText|\<p > このトピックに関連付けられているビデオを表示するには、次のようにクリックします{0} \<、href ="{1}">{2}ここ\</a >。\< 。/p >|
|OnlineAudioLinkText|\<p > をクリックすると、このトピックに関連付けられているオーディオを聴く{0} \<、href ="{1}">{2}ここ\</a >.\</p >|
|機能:|**コンテンツのインストールされていないコントロール**|
|使用:|Contentnotinstalled.htm のレンダリングに使用するテキスト要素 (文字列)|
|**要素**|**[値]**|
|ContentNotInstalledTitle|コンピューターにコンテンツが見つかりませんでした。|
|ContentNotInstalledDownloadContentText|\<p >、コンピューターにコンテンツをダウンロードする\<、href ="{0}" {1}>、[管理] タブをクリックします\</a >。\< 。/p >|
|ContentNotInstalledText|\<p > お使いのコンピューターにコンテンツがインストールされていません。 ローカル ヘルプ コンテンツのインストールは、管理者を参照してください。\</p >|
|機能:|**トピックが見つかりません。 コントロール**|
|使用:|Topicnotfound.htm のレンダリングに使用するテキスト要素 (文字列)|
|**要素**|**[値]**|
|TopicNotFoundTitle|コンピューターには、要求されたトピックを見つけることができません。|
|TopicNotFoundViewOnlineText|\<p > 要求されたトピックは、コンピューターにありませんでしたが\<、href ="{0}" {1}> オンライン トピックを参照して\</a >.\</p >|
|TopicNotFoundDownloadContentText|\<p > と同様のトピックへのリンクのナビゲーション ウィンドウを参照してくださいまたは\<a ="{0}" {1}>、[管理] タブをクリックします。\</a > をコンピューターにコンテンツをダウンロードする。\< 。/p >|
|TopicNotFoundText|\<p > 要求されたトピックがコンピューターに見つかりませんでした。\</p >|
|機能:|**トピックには、コントロールが破損しています**|
|使用:|Topiccorrupted.htm のレンダリングに使用するテキスト要素 (文字列)|
|**要素**|**[値]**|
|TopicCorruptedTitle|要求されたトピックを表示することができません。|
|TopicCorruptedViewOnlineText|\<p > ヘルプ ビューアーは、要求されたトピックを表示できません。 トピックのコンテンツまたは基になるシステム依存関係のエラーである可能性があります。\</p >|
|機能:|**ホーム ページのコントロール**|
|使用:|ヘルプ ビューアーの最上位ノードのコンテンツの表示をサポートしているテキスト。|
|**要素**|**[値]**|
|HomePageTitle|ヘルプ ビューアー ホーム|
|HomePageIntroduction|\<p > Microsoft ヘルプのビューアー、重要な Microsoft ツール、製品、テクノロジ、およびサービスを使用するすべての情報ソースへようこそ。 ヘルプ ビューアーでは、方法や参考情報、サンプル コード、技術記事、およびアクセスできます。 目次の内容の参照が必要なコンテンツを検索するには、フルテキスト検索を使用またはキーワード インデックスを使用してコンテンツを移動します。\</p >|
|HomePageContentInstallText|\<p >\<br/> 使用、 \<a ="{0}" {1}> コンテンツの管理\</a > に、次の操作 タブ:\<ul >\<li > お使いのコンピューターにコンテンツを追加します\<。/li >\<li > ローカル コンテンツへの更新プログラムを確認します\<。/li >\<li > お使いのコンピューターからコンテンツを削除します\<。/li >\</ul >\</p >|
|HomePageInstalledBooks|インストールされているブック|
|HomePageNoBooksInstalled|コンピューターにコンテンツが見つかりませんでした。|
|HomePageHelpSettings|ヘルプ コンテンツの設定|
|HomePageHelpSettingsText|\<p > 現在の設定は、ローカルのヘルプ。 ヘルプ ビューアーには、コンピューターにインストールされているコンテンツが表示されます。\<br/> Visual Studio のメニュー バーで、上のヘルプ コンテンツのソースを変更する\<span style ="{0}"> ヘルプ設定のため、\</span >.\<br/>\</p >|
|メガバイト数|MB|

 **branding.js**

 Branding.js ファイルには、Visual Studio ヘルプ ビューアーのブランド化要素で使用される JavaScript が含まれています。  ブランド化要素とサポートの JavaScript 関数の一覧を以下に示します。  このファイルをローカライズするすべての文字列は、このファイルの上部にある「ローカライズ可能な文字列」のセクションで定義されます。  Branding.js ファイル内の loc 文字列 ICL ファイルが作成されました。

||||
|-|-|-|
|**ブランド化機能**|**JavaScript 関数**|**説明**|
|Var.||変数を定義します。|
|ユーザー コードの言語を取得します。|setUserPreferenceLang|インデックスをマップ # コード言語を|
|設定して、cookie の値を取得|getCookie、setCookie||
|継承されたメンバー|changeMembersLabel|継承されたメンバーの展開/折りたたみ|
|ときに SelfBranded = False|onLoad|かどうかは、印刷要求をチェックするクエリ文字列を読み取ります。  ユーザーの優先 タブを集中するすべての codesnippets を設定します。印刷要求がある場合、isPrinterFriendly を true に設定します。 ハイ コントラスト モードを確認します。|
|コード スニペット|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|リストに折りたたみ可能なコントロールのすべてのオブジェクトを記述します。|
||CA_Click|折りたたみ可能な領域の状態に基づいて、どのイメージとを表示するテキストを定義します。|
|ロゴのコントラストのサポート|isBlackBackground()|背景が黒であるか判断と呼ばれます。  ハイ コントラスト モードでのみの精度が。|
||isHighContrast()|色付きのスパンを使用してハイ コントラスト モードを検出するには|
||onHighContrast(black)|ハイ コントラストが検出されたときに呼び出されます|
|LST 機能|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|マルチ メディア機能|キャプション (開始、終了、テキスト、スタイル)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify (styleName、styleValue)||
||showCC(id)||
||subtitle(id)||

 **HTM ファイル**

 ブランド パッケージには、一連シナリオをサポートするコンテンツのセットがインストールされている説明したセクションとトピックできないときにユーザーに示すページが含まれています、ホーム ページのヘルプ コンテンツのユーザーにキー情報を伝達する HTM ファイルにはが含まれています。ローカルの一連のトピックを記載されてください。 HTM ファイルは、製品ごとに変更できます。  ISO シェル ベンダーは、既定のブランド パッケージを実行し、動作とこれらのページの内容を変更 suite 必要性。  これらのファイルは、ブランド タグ branding.xml ファイルから対応するコンテンツを取得するために、それぞれブランド パッケージを参照してください。

||||
|-|-|-|
|**ファイル**|**使用**|**コンテンツ ソースの表示**|
|homepage.htm|これは、現在インストールされているコンテンツは、およびその内容についてユーザーに適切なその他のすべてのメッセージを表示するページです。  このファイルには、追加のメタ データ属性"Microsoft.Help.Id"コンテンツはこのローカル コンテンツの目次の上部にあるコンテンツの「-1」を = です。||
||&LT; META_HOME_PAGE_TITLE_ADD/&GT;|Branding.xml、タグ\<HomePageTitle >|
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD/&GT;|Branding.xml、タグ\<HomePageIntroduction >|
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/&GT;|Branding.xml、タグ\<HomePageContentInstallText >|
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/&GT;|Branding.xml タグ セクションの見出し\<HomePageInstalledBooks >、アプリケーションから生成されたデータ\<HomePageNoBooksInstalled > ブックがインストールしません。|
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD/&GT;|Branding.xml タグ セクションの見出し\<HomePageHelpSettings >、テキストのセクション\<HomePageHelpSettingsText >。|
|topiccorrupted.htm|何らかの理由を表示することはできませんが、ローカルのセット内のトピックが存在する場合 (コンテンツが破損しています)。||
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD/&GT;|Branding.xml、タグ\<TopicCorruptedTitle >|
||&LT; TOPIC_CORRUPTED_SECTION_ADD/&GT;|Branding.xml、タグ\<TopicCorruptedViewOnlineText >|
|topicnotfound.htm|ときに、トピックに含まれていないローカル コンテンツ使用されず、設定、オンライン||
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD/&GT;|Branding.xml、タグ\<TopicNotFoundTitle >|
||&LT; META_TOPIC_NOT_FOUND_ID_ADD/&GT;|Branding.xml、タグ\<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||&LT; TOPIC_NOT_FOUND_SECTION_ADD/&GT;|Branding.xml、タグ\<TopicNotFoundText >|
|contentnotinstalled.htm|製品のインストールされているローカルのコンテンツがない場合。||
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD/&GT;|Branding.xml、タグ\<ContentNotInstalledTitle >|
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD/&GT;|Branding.xml、タグ\<ContentNotInstalledDownloadContentText >|
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD/&GT;|Branding.xml、タグ\<ContentNotInstalledText >|

 **CSS ファイル**

 Visual Studio ヘルプ ビューアー ブランド パッケージには、一貫性のある Visual Studio ヘルプ コンテンツのプレゼンテーションをサポートするために 2 つの css ファイルが含まれています。

- Branding.css: に場所を表示するための css 要素が含まれています SelfBranded = false

- Printer.css: に場所を表示するための css 要素が含まれています SelfBranded = false

  Branding.css ファイルには、Visual Studio のトピックの「プレゼンテーションの定義にはが含まれています (注意点ありますが、Branding_ branding.css が含まれている\<ロケール > パッケージ サービスから .mshc が変わる可能性があります)。

  **グラフィック ファイル**

  Visual Studio コンテンツには、Visual Studio ロゴおよびその他のグラフィックスが表示されます。  Visual Studio ヘルプ ビューアーのブランド パッケージ内のグラフィック ファイルの完全な一覧は、以下に示します。

||||
|-|-|-|
|**ファイル**|**使用**|**例**|
|clear.gif|折りたたみ可能な領域を表示するために使用||
|footer_slice.gif|フッターのプレゼンテーション||
|info_icon.gif|情報を表示するときに使用|免責情報|
|online_icon.gif|このアイコンは、オンラインのリンクに関連付ける||
|tabLeftBD.gif|コード スニペットのコンテナーを表示するために使用||
|tabRightBD.gif|コード スニペットのコンテナーを表示するために使用||
|vs_logo_bk.gif|Branding.xml タグで定義されている標準コントラスト ロゴの参照に使用される\<LogoFileName >。  Visual Studio 製品では、ロゴの名前は vs_logo_bk.gif です。||
|vs_logo_wh.gif|Branding.xml タグで定義されている高ロゴの通常の参照に使用される\<LogoFileNameHC >。  Visual Studio 製品では、ロゴの名前は vs_logo_wh.gif です。||
|ccOff.png|キャプションのグラフィック||
|ccOn.png|キャプションのグラフィック||
|ImageSprite.png|折りたたみ可能な領域を表示するために使用|展開または折りたたむグラフィック|

### <a name="deploying-a-set-of-topics"></a>トピックのセットを展開します。
 これは、MSHA ファイルと cab ファイルまたはトピックを含む MSHCs のセットで構成されるヘルプ ビューアーのコンテンツ展開セットを作成するためのシンプルで簡単なチュートリアルです。 MSHA は、cab ファイルのセットを表す XML ファイルまたは MSHC ファイルです。 ヘルプ ビューアーは、(、コンテンツの一覧を取得する MSHA を読み取ることができます。CAB またはします。MSHC ファイル) のローカル インストールに使用できます。

 これは、非常に基本的な XML スキーマを記述する、ヘルプ ビューアー MSHA の入門書のみです。  この簡単な概要とサンプル HelpContentSetup.msha の下の実装例があります。

 この入門書では、ため、MSHA の名前は HelpContentSetup.msha (ファイルの名前できます拡張子を持つもの。MSHA)。 HelpContentSetup.msha (次の例) は、cab ファイルまたは使用可能な MSHCs の一覧を含める必要があります。  ファイルの種類は、(MSHA と CAB ファイルの種類の組み合わせをサポートしません) MSHA 内で一貫性のあるである必要があります。 各 CAB または MSHC あります、 \<div クラス =「パッケージ」>.\</div > (次の例を参照してください)。

 注: 次の実装の例で扱った、ブランド パッケージ。 これが、必要な Visual Studio のコンテンツの表示要素とコンテンツの動作を取得するためには、重要です。

 HelpContentSetup.msha ファイルのサンプル: (「コンテンツは、名前の 1 を設定」を置換し、"コンテンツ セット name 2" など、ファイル名)。

```
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.

```

1. "C:\SampleContent"のようなもののローカル フォルダーを作成します。

2. この例では、トピックを含む、MSHC ファイルを使用します。  MSHC を .zip から変更されたファイル拡張子を持つ zip ファイルです。MSHC します。

3. 作成、テキスト ファイルとして HelpContentSetup.msha 以下 (メモ帳は、ファイルの作成に使用された) 上記の付いているフォルダーに保存 (手順 1 を参照してください)。

   「ブランド化」が存在し、一意のクラスです。 インストールされているコンテンツのブランドになり、MSHCs に含まれているコンテンツの動作はブランド パッケージに含まれる適切なサポート要素ように、この入門書でブランド化 mshc が含まれます。 これは、システムがサポートの項目は取り込んだ (インストール) の一部のコンテンツを探すときにエラーが発生します。

   パッケージをブランド化、Visual Studio を入手するには、作業フォルダーにある C:\Program Files (x86) \Microsoft Help Viewer\v2.1\ Branding_en US.mshc ファイルをコピーします。

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>

```

 **まとめ**

 使用して、上記の手順の拡張は、Visual Studio ヘルプ ビューアーのコンテンツのセットをデプロイする Vsp を有効になります。

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Visual Studio Shell (Integrated および分離プロセス) に追加のヘルプ
 **はじめに**

 このチュートリアルでは、Visual Studio Shell アプリケーションにヘルプ コンテンツを組み込むし、デプロイする方法を示します。

 **必要条件**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Visual Studio 2013 Shell 再頒布可能パッケージの分離](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)

   **概要**

   [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]シェルは、のバージョン、 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] IDE をアプリケーションを作成できます。 このようなアプリケーションには、作成した拡張機能と分離シェルが含まれます。 含まれている分離シェル プロジェクト テンプレートを使用して、 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] SDK、拡張機能を作成します。

   分離シェル ベースのアプリケーションとそのヘルプを作成するための基本的な手順:

3. 取得、 [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] ISO Shell 再頒布可能パッケージ (Microsoft ダウンロード)。

4. Visual Studio で、ヘルプの拡張機能に基づいている Isolated Shell には、このチュートリアルの後半で説明されている Contoso ヘルプ拡張機能を作成します。

5. 拡張機能と ISO Shell の MSI (アプリケーションのセットアップ) のデプロイに再頒布可能パッケージをラップします。 このチュートリアルでは、セットアップ手順は含まれません。

   Visual Studio のコンテンツ ストアを作成します。 統合シェルのシナリオで、次のように製品のカタログ名を Visual Studio12 を変更します。

- C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 フォルダーを作成します。

- CatalogType.xml という名前のファイルを作成し、フォルダーに追加します。 ファイルには、次のコード行を含める必要があります。

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  レジストリのコンテンツ ストアを定義します。 統合シェル VisualStudio12 を製品カタログの名前に変更します。

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   キー: LocationPath 文字列の値: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US

   キー: CatalogName 文字列の値:[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]ドキュメント

  **プロジェクトの作成**

  分離シェルの拡張機能を作成します。

1. Visual Studio で、**ファイル**、選択**新しいプロジェクト****その他のプロジェクトの種類**選択**Extensibility**を選択し**Visual Studio Shell Isolated**します。 プロジェクトに名前を`ContosoHelpShell`) Visual Studio 分離シェル テンプレートに基づいて、拡張機能プロジェクトを作成します。

2. ソリューション エクスプ ローラーでのリソース ファイル フォルダーで、ContosoHelpShellUI プロジェクトで ApplicationCommands.vsct を開きます。 この行がコメント アウト ("No_Help"を検索) を確認します。 `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. F5 キーをコンパイルして実行する**デバッグ**します。 分離シェル IDE の実験用インスタンスの選択、**ヘルプ**メニュー。 確認、**ヘルプの表示**、**ヘルプ コンテンツの削除と追加**、および**ヘルプ設定**コマンドが表示されます。

4. ソリューション エクスプ ローラーでのシェルのカスタマイズ フォルダーで、ContosHelpShell プロジェクトで ContosoHelpShell.pkgdef を開きます。 Contoso ヘルプ カタログを定義するには、次の行を追加します。

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. ソリューション エクスプ ローラーでのシェルのカスタマイズ フォルダーで、ContosHelpShell プロジェクトで ContosoHelpShell.Application.pkgdef を開きます。 F1 ヘルプを有効にするには、次の行を追加します。

   ```
   // F1 Help Provider

   [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="13407"
   "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
   @="Help3 Provider"
   [$RootKey$\HelpProviders]
   @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
   [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="Help3 Provider"
   @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
   ```

6. ソリューション エクスプ ローラーで、ContosoHelpShell ソリューションのコンテキスト メニューの選択、**プロパティ**メニュー項目。 **構成プロパティ**、 **Configuration Manager**します。 **構成**列、"Debug"のすべての値を「リリース」に変更します。

7. ソリューションをビルドします。 これは、次のセクションで使用されるリリースのフォルダーに一連のファイルを作成します。

   展開されているかのようにテスト。

8. コンピューターで、ダウンロードした ISO シェル、(上記) をインストールする Contoso を展開します。

9. フォルダーを作成\\\Program Files (x86)\\、名前を付けます`Contoso`します。

10. ContosoHelpShell リリース フォルダーの内容をコピー \\\Program Files (x86) \Contoso\ フォルダー。

11. レジストリ エディターを選択して開始**実行**で、**開始**メニューと入力する`Regedit`します。 レジストリ エディターで次のように選択します。**ファイル**、し**インポート**します。 ContosoHelpShell プロジェクト フォルダーに移動します。 ContosoHelpShell サブフォルダーでは、ContosoHelpShell.reg を選択します。

12. コンテンツ ストアを作成します。

     ISO shell - C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 Contoso コンテンツ ストアを作成します。

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]統合シェル C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 フォルダーを作成します。

13. CatalogType.xml を作成し、格納されている (前の手順) のコンテンツ ストアに追加します。

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. 次のレジストリ キーを追加します。

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: LocationPath 文字列値。

     ISO シェル。

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] 統合シェル:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-米国

     キー: CatalogName 文字列の値:[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]ドキュメント。 ISO シェルでは、これは、カタログの名前です。

15. (Cabs または MSHC および MSHA) コンテンツをローカル フォルダーにコピーします。

16. 統合シェル コマンドラインの例のコンテンツ ストアをテストします。 ISO のシェルの製品と一致する適切なカタログと launchingApp の値を変更します。

      "C:\Program Files (x86) \Microsoft Help Viewer\v2.1\HlpViewer.exe"/catalogName VisualStudio12/helpQuery メソッド ="ページ"&"id = ContosoTopic0"/launchingApp Microsoft VisualStudio、12.0

17. (Contoso アプリのルート) から Contoso アプリケーションを起動します。 ISO のシェル内で選択、**ヘルプ**メニュー項目と変更、**ヘルプ設定**に**ローカル ヘルプの使用**します。

18. シェル内で選択、**ヘルプ**し、メニュー項目**ヘルプの表示**します。 ローカルのヘルプ ビューアーを起動する必要があります。 **[コンテンツの管理]** タブを選択します。**インストール ソース**、選択、**ディスク**オプション ボタンをクリックします。 選択、 **.** ボタンをクリックし、Contoso のコンテンツ (前の手順でローカル フォルダーにコピー) を含むローカル フォルダーを参照します。 HelpContentSetup.msha を選択します。 Contoso は、オプションの書籍で書籍として表示されます。 選択**追加**を選択し、**更新**ボタン (右下隅)。

19. Contoso、IDE 内で f1 キー機能をテストする、F1 キーを選択します。

### <a name="additional-resources"></a>その他のリソース

ランタイム API では、次を参照してください。 [Windows API のヘルプ](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)します。

API のヘルプを活用する方法の詳細については、次を参照してください。[ヘルプ ビューアーのコード例](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)します。

上の問題の重大な更新プログラムは、次を参照してください。、[ヘルプ ビューアーの Readme](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)します。
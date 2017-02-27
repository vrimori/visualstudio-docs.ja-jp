---
title: "Microsoft ヘルプ ビューアー SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# Microsoft ヘルプ ビューアー SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

この記事には、Visual Studio ヘルプ ビューアーのインテグレーターの次のタスクが含まれています。  
  
-   トピック \(F1 サポート\) を作成します。  
  
-   ヘルプ ビューアーのコンテンツのブランド化パッケージを作成します。  
  
-   記事のセットを展開します。  
  
-   Visual Studio シェル \(統合または分離された\) に追加のヘルプ  
  
-   その他のリソース  
  
### トピック \(F1 サポート\) を作成します。  
 このセクションでは、提示されたトピック、トピックの要件、レンダリングされた結果で \(F1 サポート要件を含む\) のトピックと、最後に、例のトピックを作成する方法の簡単な説明のコンポーネントの概要を示します。  
  
 **ヘルプ ビューアーのトピックの概要**  
  
 トピックが表示するために呼び出されると、ヘルプ ビューアーのインストールや、XHTML トピックと共に、最後の更新時に、トピックに関連付けられているブランド化のパッケージ要素を取得しは 2 つ \(ブランド化データ \+ トピック データ\) は、提示されたのコンテンツ ビューに結果を結合します。  ブランド化のパッケージには、ロゴ、コンテンツの動作、およびブランド化のテキスト \(著作権など\) のサポートが含まれています。  ブランド化のパッケージ要素の詳細については、下「ブランド化パッケージを作成する」を参照してください。  イベントと、そのトピックに関連付けられているブランド化のパッケージがない場合、ヘルプ ビューアーは、ヘルプ ビューアーのアプリケーション ルート \(Branding\_en US.mshc\) にあるフォールバックのブランド化パッケージを使用します。  
  
 **ヘルプ ビューアーのトピックの要件**  
  
 ヘルプ ビューアー内で正しくレンダリングされる生のトピックのコンテンツは、W3C の基本的な 1.1 XHTML する必要があります。  
  
 通常、トピックには、2 つのセクションが含まれます。  
  
-   メタデータ \(コンテンツのメタデータ参照を参照してください\): トピック一意の ID、キーワードの値、トピック目次 ID などのトピックについてのデータは親ノードの ID などです。  
  
-   本文のコンテンツ: 1.1 XHTML の基本的な W3C に準拠してを含むサポートされているコンテンツの動作 \(折りたたみ可能な領域、コード スニペットなどです。完全な一覧は、次に示します\)。  
  
 Visual Studio ブランドのパッケージには、コントロールがサポートされています。  
  
-   リンク  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   継承されたメンバー  
  
-   LanguageSpecificText  
  
 言語識別文字列 \(いない大文字小文字を区別\) がサポートされています。  
  
-   javascript  
  
-   csharp または c\# の場合  
  
-   cplusplus visualc\+\+ または c \+ \+  
  
-   jscript  
  
-   visual basic または vb  
  
-   f\# または fsharp または fs  
  
-   – 他の言語の名前を表す文字列  
  
 **ビューアーのヘルプ トピックを作成します。**  
  
 ContosoTopic4.htm、という名前の新しい XHTML 文書を作成し、title タグ \(下記\) を含めます。  
  
```html  
<html> <head> <title>Contoso Topic 4</title> </head> <body> </body> </html>  
  
```  
  
 データを定義する方法、トピック \(自社製か\) を表示する方法を次に、追加 F1、目次、その ID \(その他のトピックでリンクの参照\) 内でこのトピックが存在するためには、このトピックを参照するなどです。サポートされているメタデータの完全な一覧については、次の表「コンテンツ メタデータ」を参照してください。  
  
-   この場合は、当社のブランド化パッケージを Visual Studio ヘルプ ビューアーのブランド化パッケージのバリアントを使用します。  
  
-   F1 メタ名前と値の追加 \("Microsoft.Help.F1"コンテンツ"ContosoTopic4"\=\) IDE プロパティ バッグ内の指定された F1 値に一致します。  \(詳細については、F1 サポート セクションを参照してください\)。   これは、f1 キーと一致する値を IDE で f1 キーを選択すると、このトピックを表示する IDE 内から呼び出します。  
  
-   トピック ID を追加します。 これは、このトピックにリンクするその他のトピックで使用される文字列です。  このトピックのヘルプ ビューアー ID です。  
  
-   目次には、このトピックの目次ノードが表示される場所を定義する、このトピックの親ノードを追加します。  
  
-   目次には、このトピックのノードの順序を追加します。 親ノードに n 個の子ノードがある場合は、\[子ノードの順序でこのトピックの場所を定義します。 たとえば、このトピックでは、4 つの子トピックの数 4 です\)。  
  
 メタデータの例」のセクション:  
  
```html  
<html> <head> <title>Contoso Topic 4</title> <meta name="SelfBranded" content="false" /> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> </head> <body> </body> </html>  
  
```  
  
 **トピックの本文**  
  
 ページのリンク、注のセクションで、折りたたみ可能な領域、コード スニペットでは、および言語の特定のテキストのセクションで、トピックの本文 \(ヘッダーとフッターは含まれない\) が含まれます。  提示されたトピックのこれらの領域に関する情報については、ブランド化セクションを参照してください。  
  
1.  トピックの title タグを追加します。  `<div class="title">Contoso Topic 4</div>`  
  
2.  注」セクションを追加します。 `<div class="alert"> add your table tag and text </div>`  
  
3.  折りたたみ可能な領域を追加します。  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  コード スニペットを追加します。  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  コード言語の特定のテキストを追加します。  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` devLangnu ことに注意してください \= その他の言語を入力することができます。 DevLangnu など \="Fortran"Fortran が表示されるときにコード スニペット DisplayLanguage Fortran \=  
  
6.  ページのリンクを追加します。 `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  注意: コード スニペットのコードの色付けがサポートされていない新しい"の表示言語の"\(例、f\#、Cobol、Fortran\) モノクロ、されます。  
  
 **ビューアーのヘルプ トピックを例** コードは、メタデータ、コード スニペット、折りたたみ可能な領域、および特定のテキストの言語を定義する方法を示しています。  
  
```  
<?xml version="1.0" encoding="utf-8"?> <html> <head> <title>Contoso Topic 4</title> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> <meta name="SelfBranded" content="false" /> </head> <body> <div class="title">Contoso Topic 4</div> <div id="header"> <table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%"> <tr id="headerTableRow2"><td align="left"> <span id="nsrTitle">Contoso Topic 1</span> </td> <td align="right"> </td></tr> <tr id="headerTableRow1"><td align="left"> <span id="runningHeaderText">Contoso Widgets & Sprockets</span> </td></tr> </table> </div> <h2>Table of Contents</h2> <ul class="toc"> <li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li> <li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li> </ul> <div class="topic"> <div id="mainSection"> <div id="mainBody"> <a name="introduction"></a> <h2>1.0 Introduction</h2> <p>[This documentation is for sample purposes only.]</p> <p>Contoso Topic 1 contains examples of: <ul> <li>Collapsible Area</li> <li>Bookmark ("See also")</li> <li>Code Snippets from Branding Package</li> </ul> </p> <div class="alert"><table><tr><th> <strong>Note </strong></th></tr> <tr><td> <p>This is an example of a <span class="label">Note </span>section. Call out important items for your reader in this <span class="label">Note </span>box. </p></td></tr> </table> </div> </div> <CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> <a id="sectionToggle0"><!----></a> <div> Example of Collapsible Area <br/> Lorem ipsum dolor sit amet... </div> </CollapsibleArea> <div id="snippetGroup" > <CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" > Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip Dim messageBoxVB as New System.Text.StringBuilder() messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds) messageBoxVB.AppendLine() ... MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event") End Sub </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e) { System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder(); messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds ); messageBoxCS.AppendLine(); ... MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" ); } </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" > some F# code </CodeSnippet> </div> <h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" /> <a name="seealso"></a> <h1 class="heading">See Also</h1> <div id="seeAlsoSection" class="section"> <div class="seeAlsoStyle"> <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a> </div> </div> </div> </div> </body> </html>  
  
```  
  
 **F1 サポート**  
  
 Visual Studio で f1 キーを選択すると、IDE 内でカーソルの位置から指定された値を生成し、設定が含まれる「プロパティ バッグ」指定された値 \(カーソル位置に基づいています。 カーソルが機能 x の上にあるときは、機能 x はアクティブ\/にフォーカスが置かれてし、値を持つプロパティ バッグを設定します。  F1 キーを選択すると、プロパティ バッグが設定され、Visual Studio の f1 キー コードは顧客の既定のヘルプ ソースがローカルまたはオンラインかどうかを次の \(online は、既定値\)、ユーザーの設定に基づく適切な文字列を作成 \(オンラインは、既定値\): シェルの実行 \(ヘルプ管理者ガイド exe 起動パラメーターを参照してください\)、ローカルのヘルプ ビューアーとローカルのヘルプが既定の場合は、プロパティ バッグからのキーワードのパラメーターを使用して、またはパラメーターの一覧でキーワードを使って MSDN URL です。  
  
 複数値の文字列としてに対して実行する最初の用語では、検索ヒットは、f1 キーを 3 つの文字列が返される場合が参照されるかどうかは、完了です。それ以外の場合は、次の文字列に移動します。  順序は重要です。 複数値キーワードのプレゼンテーションでは、最も長い文字列を短い文字列をする必要があります。  複数値キーワードの場合はこれを確認するには、オンラインの F1 URL の文字列は、選択したキーワードが含まれますを確認します。  
  
 Visual Studio 2012 では意図的により強力な除算オンラインとオフラインの間でようにされてオンラインの場合、ユーザーの設定は、私たちだけで渡されます F1 要求、クエリのオンライン サービスに直接 Visual Studio 2010 に含まれているヘルプ ライブラリ エージェント経由のルーティングのではなく、MSDN います。 状態にし、信頼しています"インストールされているベンダー コンテンツ \= true"をそのコンテキストで異なる処理を実行するかどうかを判断します。 True の場合、次に、お客様のサポートの対象によってこの解析およびルーティング ロジックを実行します。 False の場合、私たちに移動する MSDN です。 ユーザーの設定がローカルにある場合は、すべての呼び出しだけに進みますローカル ヘルプ エンジンです。  
  
 F1 フロー図に示します。  
  
 ![F1 flow](../../extensibility/internals/media/f1flow.png "F1flow")  
  
 ヘルプ ビューアーの既定のヘルプ コンテンツ ソースをオンライン \(ブラウザーで起動\)\] を設定するとします。  
  
-   Visual Studio パートナー \(VSP\) 機能は、F1 プロパティ バッグ \(プロパティ バッグ prefix.keyword と、レジストリで見つかったプリフィックスのオンラインの URL\) に値を出力します。 F1 VSP URL \+ パラメーターをブラウザーに送信します。  
  
-   Visual Studio の機能 \(言語のエディター、Visual Studio の特定のメニュー項目など\)。 F1 は、Visual Studio の URL をブラウザーに送信します。  
  
 ヘルプ ビューアーの既定のヘルプ コンテンツ ソースをローカルのヘルプ \(ヘルプ ビューアーの起動\) を設定するとします。  
  
-   キーワードが F1 プロパティ バッグとローカル ストアのインデックスの間で一致する VSP 機能 \(プロパティ バッグ prefix.keyword は、ローカル ストアのインデックス内で見つかった値 \=\): F1 は、ヘルプ ビューアーでトピックを表示します。  
  
-   Visual Studio の機能 \(Visual Studio の機能から生成されたプロパティ バッグをオーバーライドする VSP のオプションがありません\)。 F1 は、ヘルプ ビューアーで Visual Studio のトピックをレンダリングします。  
  
 ヘルプ コンテンツの仕入先の F1 フォールバックを有効にする次のレジストリ値を設定します。 F1 フォールバックでは、ヘルプ ビューアーがオンラインでの F1 ヘルプ コンテンツの表示に設定されてし、ユーザーのハード ドライブに仕入先のコンテンツがローカルでインストールされていることを示します。 場合でも、オンライン ヘルプの既定値は、ヘルプ ビューアーは、コンテンツのローカル ヘルプのはずです。  
  
1.  設定、 **VendorContent** ヘルプ 2.1 レジストリ キーの下の値。  
  
    -   32 ビット オペレーティング システム。  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent"\= dword:00000001  
  
    -   64 ビット オペレーティング システム。  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent"\= dword:00000001  
  
2.  ヘルプ 2.1 レジストリ キーの下で、パートナーの名前空間を登録します。  
  
    -   32 ビット オペレーティング システム。  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Partner*\\ \< 名前空間 \>*  
  
         「場所"\=」オフライン"  
  
    -   64 ビット オペレーティング システム。  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Partner*\\ \< 名前空間 \>*  
  
         「場所"\=」オフライン"  
  
 **解析ネイティブ名前空間の基本**  
  
 解析にネイティブ名前空間のベースにするには、レジストリに追加する新しい DWORD の名前: BaseNativeNamespaces \(をサポートするカタログ キー\) の下に 1 をその値を設定します。  たとえば、Visual Studio のカタログを使用する場合は、パスにキーを追加でした。  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
 ヘッダー\/メソッドが検出された形式で F1 キーワード、ときの '\/' 文字は次の構成体に、解析されます。  
  
-   ヘッダー: は、レジストリに登録するために使用する名前空間になります  
  
-   方法: このなりますを通じて渡されるキーワード。  
  
 たとえば、CustomLibrary と呼ばれるカスタム ライブラリと要求を受信して、F1 として書式設定するときに、MyTestMethod に呼び出されるメソッドが指定された `CustomLibrary/MyTestMethod`します。  
  
 ユーザー パートナー ハイブ下にある名前空間として CustomLibrary を登録し、どのような場所のキーを指定してクエリに渡すキーワード MyTestMethod になります。  
  
 **デバッグ、IDE でツールのヘルプを有効にします。**  
  
 次のレジストリ キーと値を追加します。  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\12.0\\Dynamic ヘルプ キー: 小売価格でのデバッグ出力を表示します \[はい\]。  
  
 Ide のヘルプのメニュー項目の下で、\[デバッグのヘルプのコンテキスト\] を選択します  
  
 **コンテンツのメタデータ**  
  
 次の表では、かっこに囲まれて表示される任意の文字列は認識可能な値で置き換える必要があるプレース ホルダーです。 などで \< meta name\="Microsoft.Help.Locale"コンテンツ \=「\[言語コード\]」\/\>、「\[言語コード\]」をなどの値で置き換える必要があります"en\-私たち"です。  
  
|プロパティ \(HTML 形式\)|説明|  
|-----------------------|--------|  
|\< meta name\="Microsoft.Help.Locale"内容 \=「\[言語コード\]」\/\>|このトピックのロケールを設定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要がありには、その他の Microsoft ヘルプ タグ上に挿入する必要があります。 トピックの本文が指定されている場合、製品のロケールに関連付けられているワード ブレーカーを使用してインデックスを作成このタグを使用しない場合それ以外の場合、en\-私たちのワード ブレーカーを使用します。 このタグは、ISOC RFC 4646 に準拠します。 Microsoft ヘルプが正しく動作するためには、このプロパティを使用して、一般的な言語属性の代わりにします。|  
|\< meta name\="Microsoft.Help.TopicLocale"内容 \=「\[言語コード\]」\/\>|その他のロケールがいるために、このトピックのロケールを設定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 カタログには、1 つ以上の言語でコンテンツが含まれている場合は、このタグを使用します。 カタログ内の複数のトピックでは、同じ ID を使用できますをそれぞれ一意 TopicLocale を指定する必要があります。 カタログのロケールに対応する TopicLocale を示すトピックでは、コンテンツのテーブルに表示されるトピックです。 ただし、トピックのすべての言語バージョンは、検索結果に表示されます。|  
|\< title \> \[タイトル\] \<\/title \>|このトピックのタイトルを指定します。 このタグは、必要なし、トピック内で 1 回だけ使用する必要があります。 タイトル \< div \> セクションが、トピックの本文に含まれていない場合は、トピックおよびコンテンツのテーブルでこのタイトルが表示されます。|  
|\< meta name \="Microsoft.Help.Keywords"内容 \="\[aKeywordPhrase\]"\/\>|ヘルプ ビューアーの \[インデックス\] ウィンドウに表示されるリンクのテキストを指定します。 リンクをクリックすると、トピックが表示されます。、トピックの、複数のインデックス キーワードを指定することも、インデックスに表示するには、このトピックにリンクしたくない場合は、このタグを省略できます。 以前のバージョンのヘルプの"K"キーワードは、このプロパティに変換できます。|  
|\< meta name\="Microsoft.Help.Id"内容 \="\[TopicID\]"\/\>|このトピックの識別子を設定します。 このタグは、必要なし、トピック内で 1 回だけ使用する必要があります。 ID は、同じロケールの設定のトピック、カタログでの間で一意である必要があります。 別のトピックでは、この ID を使用して、このトピックへのリンクを作成できます。|  
|\< meta name\="Microsoft.Help.F1"content\="\[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator\]"\/\>|このトピックの F1 キーワードを指定します。 、トピックの、複数の F1 キーワードを指定することも、アプリケーション ユーザーは、f1 キーを押したときに表示するには、このトピックしたくない場合は、このタグを省略できます。 通常は、トピックの 1 つだけの F1 キーワードを指定します。 以前のバージョンのヘルプの"F"キーワードは、このプロパティに変換できます。|  
|\< meta name \="Description"内容 \=「\[トピックの説明\]」\/\>|このトピックの内容の短い概要を示します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 このプロパティは、クエリ ライブラリによって直接アクセスします。インデックス ファイルには格納されません。|  
|\< meta name\="Microsoft.Help.TocParent"内容 \="\[parent\_Id\]"\/\>|コンテンツのテーブルでは、このトピックの親トピックを指定します。 このタグは、必要なし、トピック内で 1 回だけ使用する必要があります。 値は、親の Microsoft.Help.Id です。 トピックには、テーブル内の 1 つの場所の内容のことができます。 「\-1」では、TOC 根本トピック ID と見なされます。[!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)], 、そのページは、ヘルプ ビューアーのホーム ページです。 これは、同じ理由で、表示されることが上部にあるレベルを確認するいくつかのトピックを具体的には TocParent \= 1 を追加しました。ヘルプ ビューアーのホーム ページには、\[システム\] ページと置き換え可能なためです。 コンテンツのセットに加わることがありますが、ヘルプ ビューアーのシステム ページ – ヘルプ ビューアーのホームを常に使用する場合は、VSP が\-1 の ID を持つページを追加しようとすると、|  
|\< meta name\="Microsoft.Help.TocOrder"内容 \=「\[正の整数\]」\/\>|コンテンツのテーブルにこのトピック基準表示する位置のピアのトピックを指定します。 このタグは、必要なし、トピック内で 1 回だけ使用する必要があります。 値は整数です。 価値の高い整数を指定するトピック上に小さい方の値の整数を指定するトピックが表示されます。|  
|\< meta name\="Microsoft.Help.Product"内容 \=「\[製品コード\]」\/\>|このトピックで説明する製品を指定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 この情報は、ヘルプのインデクサーに渡されるパラメーターとして指定できます。|  
|\< meta name\="Microsoft.Help.ProductVersion"内容 \=「\[バージョン番号\]」\/\>|このトピックで説明する製品のバージョンを指定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 この情報は、ヘルプのインデクサーに渡されるパラメーターとして指定できます。|  
|\< meta name\="Microsoft.Help.Category"内容 \="\[string\]"\/\>|製品で使用すると、コンテンツのサブセクションを識別します。 トピックのための複数のサブセクションがわかります。 または任意のサブセクションを識別するためにリンクしたくない場合は、このタグを省略できます。 このタグを使用して、以前のバージョンのヘルプからトピックを変換するとき、TargetOS な TargetFrameworkMoniker 属性を格納します。 コンテンツの形式は、AttributeName:AttributeValue です。|  
|\< meta name\="Microsoft.Help.TopicVersion 内容 \=「\[トピックのバージョン番号\]」\/\>|複数のバージョンがカタログに存在する場合は、トピックのこのバージョンを指定します。 Microsoft.Help.Id は、一意であることが保証されず、このタグの値が 1 つ以上のバージョンのトピックに存在する場合、カタログ、たとえば、カタログは、.NET Framework 4 向けの .NET Framework 3.5 とトピックにあるトピックに含まれます。 保ち、両者が、同じ Microsoft.Help.Id ときに必要です。|  
|\< meta name \="SelfBranded"内容 \=「\[TRUE または false の場合\]」\/\>|このトピックが、ヘルプ ライブラリ マネージャーのスタートアップ ブランディング パッケージと、トピックに固有であるブランド化パッケージを使用するかを指定します。 このタグは真である必要がありますか、false を指定します。 TRUE の場合は、ブランド化パッケージに関連するトピックは、ヘルプ ライブラリ マネージャーを開始するので、他のコンテンツのレンダリングとは異なる場合でもを意図したとおりにトピックが表示されるときに設定されているブランド化パッケージを上書きします。 FALSE の場合は、ヘルプ ライブラリ マネージャーの起動時に設定されているブランディング パッケージに従って、現在のトピックが表示されます。 既定では、ヘルプ ライブラリ マネージャーは自己 SelfBranded 変数が TRUE であると宣言されている限り、false であるブランド化そのため、宣言する必要はありません \< meta name \="SelfBranded"コンテンツ \="FALSE"\/\>。|  
  
### ブランド化パッケージを作成します。  
 Visual Studio のリリースには、Visual Studio パートナーの分離性と統合シェルを含む別の Visual Studio 製品の数が含まれます。  各製品には、ある程度のサポート、製品に固有のブランド化トピック ベースのヘルプ コンテンツが必要です。  たとえば、Visual Studio のトピック必要一貫性のあるブランドのプレゼンテーションでは、SQL Studio は、ISO のシェルをラップする独自固有のヘルプ コンテンツのブランド化の各トピックで必要のあります。  統合のシェル パートナーは、独自のトピックのブランド化を維持しながら、Visual Studio 製品のヘルプ コンテンツの親内であること、ヘルプ トピックを必要があります。  
  
 ブランド化パッケージは、ヘルプ ビューアーが含まれている製品によってインストールされます。  Visual Studio 製品。  
  
-   フォールバックのブランド化パッケージ \(Branding\_ \< ロケール \> の .mshc\) は、ヘルプ ビューアー 2.1 アプリのルートにインストール \(例: C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\) ヘルプ ビューアーの言語パックにします。  これは、パッケージをブランド化のいずれかの製品がインストールされていない場合に使用 \(コンテンツがインストールされていません\) またはインストール済みのブランド化パッケージが破損しています。  パッケージをブランド化、アプリケーション ルートのフォールバックを使用する場合に Visual Studio の要素 \(ロゴおよびフィードバック\) を無視することに注意してください。  
  
-   Visual Studio コンテンツがコンテンツ パッケージ サービスからインストールされている場合、ブランド化パッケージは \(用時の最初のコンテンツのインストール シナリオで\) もインストールされます。  ブランド化のパッケージに更新プログラムがある場合は、次のコンテンツの更新または追加のパッケージのインストール操作が発生したときに、更新がインストールします。  
  
 Microsoft ヘルプ ビューアーでは、トピックのメタデータに基づいて、トピックのブランド化をサポートします。  
  
-   トピックのメタデータを定義してブランド化されていない自己 \= true、レンダリングは、トピック、\(ブランド\) に関して何も行いません。  
  
-   False の場合、トピックのメタデータを定義してブランド化されていない自己 \= TopicVendor メタデータ値に関連付けられているブランド化パッケージを使用します。  
  
-   コンテンツの場所トピック メタデータを定義 name\="Microsoft.Help.TopicVendor"\= \< ブランド パッケージ名仕入先 MSHA \> をブランド化にコンテンツの値で定義されているパッケージを使用します。  
  
-   Visual Studio カタログ内であることのブランド化パッケージの優先度のアプリケーションに注意してください。  最初の Visual Studio の既定ブランドが適用され、トピック メタデータで定義されでサポートされている場合は \(で定義されているインストール msha\) にパッケージ化、関連付けられているブランド化、オーバーライドとして定義されているベンダーをブランド化が適用される次に、します。  
  
 ブランド化要素は、通常、3 つのカテゴリに分類されます。  
  
-   \(例については、\[フィードバック\] リンク、条件付きの免責事項のテキスト、ロゴを含める\) ヘッダー要素  
  
-   コンテンツの動作 \(例については、展開\/折りたたみコントロールのテキスト要素を含めるし、コード スニペットの要素\)  
  
-   フッター要素 \(例: Copyright\)  
  
 項目のブランド化された要素を含めると見なされます \(この仕様の詳細設定\)。  
  
-   カタログ\/製品のロゴ \(例、Visual Studio\)  
  
-   フィードバックのリンクと電子メールの要素  
  
-   免責事項のテキスト  
  
-   著作権テキスト  
  
 関連ファイルを Visual Studio ヘルプ ビューアーのブランド化パッケージには次のとおりです。  
  
-   グラフィックス \(ロゴ、アイコンなど\)  
  
-   Branding.js – スクリプト ファイルをサポートするコンテンツの動作  
  
-   Branding.xml: カタログのコンテンツにまたがる一貫して使用する文字列。  注: branding.xml で Visual Studio のローカライズ テキスト要素には、\_locID が含まれている \="\< 一意 value \>"  
  
-   Branding.css – プレゼンテーション一貫性を保つのためのスタイルの定義  
  
-   Printing.css – 一貫性のあるプレゼンテーションの印刷スタイルの定義  
  
 前述のように、そのパッケージのブランド化は、トピックに関連付けられました。  
  
-   ときに SelfBranded \= false がメタデータで定義されている、パッケージをブランド化カタログを継承するトピック  
  
-   または SelfBranded \= false と一意のブランド化パッケージに定義されて、MSHA 利用可能なコンテンツがインストールされている場合  
  
 カスタム ブランド版のパッケージを実装する Vsp \(VSP コンテンツ、SelfBranded \= True\)、続行する方法の 1 つは、フォールバックのブランド化パッケージを \(ヘルプ ビューアーでのインストール\) から開始し、必要に応じてファイルの名前を変更します。  Branding\_ \< ロケール \> の .mshc ファイルは、変更の .mshc ファイル拡張子を持つ zip ファイル、するだけで .mshc から拡張子を .zip に変更し、コンテンツを抽出します。  以下をご覧くださいパッケージ要素をブランド化し、必要に応じて変更 \(たとえば、VSP ロゴと Branding.xml ファイル内のロゴへの参照にロゴを変更する、VSP 仕様など 1 Branding.xml を更新\) します。  
  
 すべての変更を行うときに、目的のブランド化要素を含む zip ファイルを作成し、拡張機能を .mshc に変更します。  
  
 カスタムのブランド化パッケージを関連付けるには、\(トピックを含む\) コンテンツ mshc と共にブランド mshc ファイルへの参照を含む MSHA を作成します。  基本的な MSHA を作成する方法については、"MSHA"の下を参照してください。  
  
 Branding.xml ファイルには、一貫した方法、トピックが含まれているトピックの特定のアイテムの描画に使用リストの要素が含まれています。 \< meta name\="Microsoft.Help.SelfBranded"内容 \="false"\/\>。  Visual Studio の Branding.xml ファイル内の要素の一覧を以下にするとします。  このリスト テンプレートとして使用して、ISO シェルの採用にこれらを独自の製品ブランドのニーズを満たすためのこれらの要素 \(ロゴ、フィードバック、および著作権など\) を変更するためのものことに注意してください。  
  
 注:"{n}"によって示された変数は、コードの依存関係を持つ – 削除するか、これらの値を変更すると、エラーまたはアプリケーションがクラッシュします。Visual Studio のブランド化のパッケージでは、ローカリゼーション識別子 \(例 \_locID\="codesnippet.n"\) が含まれています。  
  
 **Branding.xml**  
  
|||  
|-|-|  
|次の機能。|**CollapsibleArea**|  
|使用します。|折りたたまれてコンテンツ コントロールのテキストを展開します。|  
|**要素**|**値**|  
|ExpandText|展開|  
|CollapseText|折りたたむ|  
|次の機能。|**CodeSnippet**|  
|使用します。|コード スニペットのコントロールのテキスト。  注:「改行」領域でコード スニペットのコンテンツは、スペースに変更されます。|  
|**要素**|**値**|  
|置き|クリップボードにコピー|  
|ViewColorizedText|色付きテキストで表示|  
|CombinedVBTabDisplayLanguage|Visual Basic \(サンプル\)|  
|VBDeclaration|宣言|  
|VBUsage|使用法|  
|次の機能。|**フィードバック、フッター、およびロゴ**|  
|使用します。|電子メールを使用して、現在のトピックに関するフィードバックを提供する顧客のフィードバック コントロールを提供します。  コンテンツの著作権テキストです。  ロゴの定義。|  
|**要素**|**値 \(これらの文字列はコンテンツの導入者のニーズを満たすために変更できます\)。**|  
|著作権情報|© 2013 Microsoft Corporation. All rights reserved.|  
|SendFeedback|\<、href \="0"} \\{1\\} \> \[フィードバックの送信 \<\/a \> Microsoft にお送りします。|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]|  
|LogoFileName|vs\_logo\_bk.gif|  
|LogoFileNameHC|vs\_logo\_wh.gif|  
|次の機能。|**免責情報**|  
|使用します。|マシンの特定免責条項をケースのセットに翻訳されたコンテンツを指定します。|  
|**要素**|**値**|  
|MT\_Editable|この記事は、機械翻訳されたものでした。 インターネット接続があれば、同時に、元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT\_NonEditable|この記事は、機械翻訳されたものでした。 インターネット接続があれば、同時に、元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT\_QualityEditable|この記事が翻訳されたものです。 インターネット接続があれば、同時に、元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT\_QualityNonEditable|この記事が翻訳されたものです。 インターネット接続があれば、同時に、元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT\_BetaContents|この記事は、機械、暫定版用に翻訳されたものでした。 インターネット接続があれば、同時に、元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT\_BetaRecycledContents|この記事は、準備段階のリリースに対して手動で変換されました。 インターネット接続があれば、同時に、元の英語コンテンツを編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|次の機能。|**LinkTable**|  
|使用します。|オンラインのトピックへのリンクのサポート|  
|**要素**|**値**|  
|LinkTableTitle|リンク テーブル|  
|TopicEnuLinkText|コンピューターで使用できるはこのトピックの英語版 \<\/a \> を表示します。|  
|TopicOnlineLinkText|このトピックを表示 \<、href \="0"} \\{1\\} \> online \<\/a \>|  
|OnlineText|オンライン|  
|次の機能。|**ビデオのオーディオ コントロール**|  
|使用します。|要素とビデオ コンテンツのテキストを表示します。|  
|**要素**|**値**|  
|MultiMediaNotSupported|{0} コンテンツをサポートするために Internet Explorer 9 以上をインストールする必要があります。|  
|VideoText|ビデオを表示します。|  
|AudioText|オーディオのストリーミング|  
|OnlineVideoLinkText|このトピックに関連付けられているビデオを表示するには、\< p \> {0} をクリックして \<、href \=「\\\\ 1 \\\\」\> \\{2\\}here \<\/a \>. \<\/p \>|  
|OnlineAudioLinkText|\< p \> このトピックに関連付けられているオーディオを聴く {0} をクリックして \<、href \=「\\\\ 1 \\\\」\> \\{2\\}here \<\/a \>. \<\/p \>|  
|次の機能。|**コンテンツのインストールされていないコントロール**|  
|使用します。|Contentnotinstalled.htm の表示に使用するテキストの要素 \(文字列\)|  
|**要素**|**値**|  
|ContentNotInstalledTitle|コンテンツがコンピューターに見つかりませんでした。|  
|ContentNotInstalledDownloadContentText|コンピューターにコンテンツをダウンロードするには、\< p \> \<、href \="0"} \\{1\\} \> \<\/a \> \[管理\] タブをクリックします \<\/p \>。|  
|ContentNotInstalledText|\< p \> いいえコンテンツは、コンピューターにインストールします。 ローカル ヘルプ コンテンツのインストール。 \<\/p \> 管理者に問い合わせてください。|  
|次の機能。|**トピックが見つかりません。 コントロール**|  
|使用します。|Topicnotfound.htm の表示に使用するテキストの要素 \(文字列\)|  
|**要素**|**値**|  
|TopicNotFoundTitle|お使いのコンピューターに要求されたトピックが見つかりません。|  
|TopicNotFoundViewOnlineText|\< p \> 要求されたトピックが見つかりませんでした、コンピューターにすることができます \<、href \="0"} \\{1\\} \>、トピック online \<\/a \> を表示します \<\/p \>。|  
|TopicNotFoundDownloadContentText|\< p \> のようなトピックへのリンクのナビゲーション ウィンドウを表示するか、\<、href \="0"} \\{1\\} \> コンテンツをダウンロードするには、コンピューターです \<\/p \> \<\/a \> の \[管理\] タブをクリック。|  
|TopicNotFoundText|\< p \> 要求されたトピックが見つかりませんでしたがコンピューターに \<\/p \>|  
|次の機能。|**トピックには、コントロールが破損しています。**|  
|使用します。|Topiccorrupted.htm の表示に使用するテキストの要素 \(文字列\)|  
|**要素**|**値**|  
|TopicCorruptedTitle|要求されたトピックを表示できません。|  
|TopicCorruptedViewOnlineText|\< p \> ヘルプ ビューアーでは、要求されたトピックを表示できません。 トピックの内容または、基になるシステムの依存関係です。 \<\/p \> にエラーがある可能性があります。|  
|次の機能。|**ホーム ページのコントロール**|  
|使用します。|ヘルプ ビューアーの最上位ノードのコンテンツの表示をサポートするテキストです。|  
|**要素**|**値**|  
|HomePageTitle|ヘルプ ビューアーのホーム|  
|HomePageIntroduction|\< p \> は、Microsoft ヘルプ ビューアー、重要な Microsoft ツール、製品、テクノロジ、およびサービスを使用するすべての情報のソースを開始します。 ヘルプ ビューアーでは、に関する「方法」および参照情報、サンプル コード、技術記事、およびにアクセスできます。 コンテンツを見つける必要があります、目次を参照、フルテキスト検索を使用して移動したりするコンテンツを使用して、キーワード インデックスです。 \<\/p \>|  
|HomePageContentInstallText|\< p \>\< br\/\> を使用して、\<、href \="0"} \\{1\\} \> \[コンテンツの管理 \<\/a \>、次の操作\] タブ: \< ul \>\< li \> 追加のコンテンツをコンピューター \<\/li \>\< li \> チェックの更新するには、ローカル コンテンツ。 \<\/li \>\< li \> コンテンツを削除して、コンピューターから \<\/li \>\<\/ul \>\<\/p \>。|  
|HomePageInstalledBooks|インストールされているブック|  
|HomePageNoBooksInstalled|コンテンツがコンピューターに見つかりませんでした。|  
|HomePageHelpSettings|ヘルプ コンテンツの設定|  
|HomePageHelpSettingsText|\< p \> 現在の設定は、ローカルのヘルプ。 ヘルプ ビューアーがコンピューターにインストールされているコンテンツを表示する \< br\/\> を Visual Studio のメニュー バーで、ヘルプ コンテンツのソースを変更するには、\< span \="0"} \> ために、ヘルプ設定 \<\/span \>. \< br\/\>\<\/p \>|  
|メガバイト数|MB|  
  
 **branding.js**  
  
 Branding.js ファイルには、Visual Studio ヘルプ ビューアーのブランド化要素に使用される JavaScript が含まれています。  ブランド化要素とサポートの JavaScript 関数の一覧を以下に示します。  このファイルのローカライズ対象のすべての文字列は、このファイルの上部にある「ローカライズ可能な文字列」のセクションで定義されます。  Branding.js ファイル内のローカライズ済み文字列の ICL ファイルが作成されたことに注意してください。  
  
||||  
|-|-|-|  
|**ブランド化機能**|**JavaScript 関数**|**説明**|  
|Var.||変数を定義します。|  
|ユーザー コードの言語を取得します。|setUserPreferenceLang|インデックスのマップのコードの言語に \#|  
|設定および cookie の値を取得します。|getCookie setCookie||  
|継承されたメンバー|changeMembersLabel|継承されたメンバーの展開\/折りたたみ|  
|ときに SelfBranded \= False|onLoad|印刷要求かを確認するクエリ文字列を読み取ります。  対象ユーザーの優先\] タブのすべての codesnippets を設定します。  場合は、印刷要求が、isPrinterFriendly を true に設定します。 ハイ コントラスト モードを確認します。|  
|コード スニペット|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||置き||  
|CollapsibleArea|addToCollapsibleControlSet|一覧には、折りたたみ可能なコントロールのすべてのオブジェクトを書き込みます。|  
||CA\_Click|折りたたみ可能な領域の状態に基づいて、どのイメージと表示するテキストを定義します|  
|ロゴのコントラストのサポート|isBlackBackground\(\)|背景が黒であるかどうかに呼び出されます。  ハイ コントラスト モードである正確なときのみです。|  
||isHighContrast\(\)|色の範囲を使用してハイ コントラスト モードを検出するには|  
||onHighContrast\(black\)|ハイ コントラストが検出されたときに呼び出されます|  
|LST 機能|||  
||addToLanSpecTextIdSet\(id\)||  
||updateLST\(currentLang\)||  
||getDevLangFromCodeSnippet\(lang\)||  
|マルチ メディア機能|キャプション \(開始、終了すると、テキスト、スタイル\)||  
||findAllMediaControls\(normalizedId\)||  
||getActivePlayer\(normalizedId\)||  
||captionsOnOff\(id\)||  
||toSeconds\(t\)||  
||getAllComments\(node\)||  
||styleRectify \(styleName、styleValue\)||  
||showCC\(id\)||  
||subtitle\(id\)||  
  
 **HTM ファイル**  
  
 ブランド化のパッケージには、どのコンテンツ セットがインストールされている説明したセクションとトピックは、ローカルの一連のトピックで見つからないときにユーザーに示すページが含まれています、ホーム ページのヘルプ コンテンツのユーザーに重要な情報を通信するためのシナリオをサポートする HTM ファイルのセットが含まれています。 製品ごとにこれらの HTM ファイルを変更できることに注意してください。  ISO シェル ベンダーは、既定のブランド化パッケージを実行し、変更動作とこれらのページの内容をスイートに必要です。  これらのファイルは、ブランド化タグ branding.xml ファイルから対応するコンテンツを取得するために、関連するブランド化パッケージを参照してください。  
  
||||  
|-|-|-|  
|**ファイル**|**使用**|**コンテンツ ソースの表示**|  
|homepage.htm|これは、現在インストールされているコンテンツは、およびその内容についてユーザーに提示する適切なその他のメッセージを表示するページです。  このファイルには、追加のメタ データ属性"Microsoft.Help.Id"コンテンツ \=「\-1」はこのローカル コンテンツ TOC の上部にあるコンテンツです。||  
||\< META\_HOME\_PAGE\_TITLE\_ADD\/\>|Branding.xml タグ \< HomePageTitle \>|  
||\< HOME\_PAGE\_INTRODUCTION\_SECTION\_ADD\/\>|Branding.xml タグ \< HomePageIntroduction \>|  
||\< HOME\_PAGE\_CONTENT\_INSTALL\_SECTION\_ADD\/\>|Branding.xml タグ \< HomePageContentInstallText \>|  
||\< HOME\_PAGE\_BOOKS\_INSTALLED\_SECTION\_ADD\/\>|Branding.xml タグ \< HomePageInstalledBooks \> \< HomePageNoBooksInstalled \> ブックがインストールされていないときに、アプリケーションから生成されたデータ\] セクションの見出しです。|  
||\< HOME\_PAGE\_SETTINGS\_SECTION\_ADD\/\>|Branding.xml タグ \< HomePageHelpSettings \> \< HomePageHelpSettingsText \> セクションのテキストのセクションの見出しです。|  
|topiccorrupted.htm|何らかの理由を表示することはできませんが、ローカルのセット内のトピックが存在する場合 \(コンテンツが破損している\)。||  
||\< META\_TOPIC\_CORRUPTED\_TITLE\_ADD\/\>|Branding.xml タグ \< TopicCorruptedTitle \>|  
||\< TOPIC\_CORRUPTED\_SECTION\_ADD\/\>|Branding.xml タグ \< TopicCorruptedViewOnlineText \>|  
|topicnotfound.htm|トピックが存在しないときローカル コンテンツに設定された場合、または使用可能なオンライン||  
||\< META\_TOPIC\_NOT\_FOUND\_TITLE\_ADD\/\>|Branding.xml タグ \< TopicNotFoundTitle \>|  
||\< META\_TOPIC\_NOT\_FOUND\_ID\_ADD\/\>|Branding.xml、タグ \< TopicNotFoundViewOnlineText \> \+ \< TopicNotFoundDownloadContentText \>|  
||\< TOPIC\_NOT\_FOUND\_SECTION\_ADD\/\>|Branding.xml タグ \< TopicNotFoundText \>|  
|contentnotinstalled.htm|製品のインストールされているローカルのコンテンツがない場合。||  
||\< META\_CONTENT\_NOT\_INSTALLED\_TITLE\_ADD\/\>|Branding.xml タグ \< ContentNotInstalledTitle \>|  
||\< META\_CONTENT\_NOT\_INSTALLED\_ID\_ADD\/\>|Branding.xml タグ \< ContentNotInstalledDownloadContentText \>|  
||\< CONTENT\_NOT\_INSTALLED\_SECTION\_ADD\/\>|Branding.xml タグ \< ContentNotInstalledText \>|  
  
 **CSS ファイル**  
  
 Visual Studio ヘルプ ビューアーのブランド化パッケージには、一貫性のある Visual Studio のヘルプ コンテンツの表示をサポートするために 2 つの css ファイルが含まれています。  
  
-   Branding.css – には、場所を表示するため、css の要素が含まれています SelfBranded \= false。  
  
-   Printer.css – には、場所を表示するため、css の要素が含まれています SelfBranded \= false。  
  
 Branding.css ファイルには、Visual Studio のトピックのプレゼンテーション用の定義が含まれます \(注意点は、パッケージ サービスから Branding\_ \< ロケール \> の .mshc に含まれている branding.css を変更できます\)。  
  
 **グラフィック ファイル**  
  
 Visual Studio コンテンツには、Visual Studio ロゴおよびその他のグラフィックスが表示されます。  Visual Studio ヘルプ ビューアーのブランド化パッケージにグラフィック ファイルの完全な一覧は、次に示します。  
  
||||  
|-|-|-|  
|**ファイル**|**使用**|**例**|  
|clear.gif|折りたたみ可能な領域をレンダリングするために使用||  
|footer\_slice.gif|フッターのプレゼンテーション||  
|info\_icon.gif|情報を表示するときに使用|免責情報|  
|online\_icon.gif|このアイコンは、オンラインのリンクに関連する||  
|tabLeftBD.gif|コード スニペットのコンテナーをレンダリングするために使用||  
|tabRightBD.gif|コード スニペットのコンテナーをレンダリングするために使用||  
|vs\_logo\_bk.gif|Branding.xml タグ \< LogoFileName \> で定義されている通常のコントラスト ロゴの参照に使用されます。  Visual Studio 製品のロゴの名前は vs\_logo\_bk.gif です。||  
|vs\_logo\_wh.gif|Branding.xml タグ \< LogoFileNameHC \> で定義されている通常の高いロゴの参照に使用されます。  Visual Studio 製品のロゴの名前は vs\_logo\_wh.gif です。||  
|ccOff.png|キャプションのグラフィック||  
|ccOn.png|キャプションのグラフィック||  
|ImageSprite.png|折りたたみ可能な領域をレンダリングするために使用|展開または折りたたむグラフィック|  
  
### トピックのセットを展開します。  
 これは、ヘルプ ビューアーのコンテンツ展開 MSHA ファイルと cab ファイルのセットの構成設定を作成するための非常にシンプルでクイック チュートリアルまたは MSHC にはトピックが含まれています。 MSHA は、cab ファイルのセットを記述した XML ファイルまたは MSHC ファイルです。 ヘルプ ビューアーは、\(、コンテンツの一覧を取得する MSHA を読み取ることができます。CAB またはです。MSHC ファイル\) ローカルのインストールに使用します。  
  
 これは、ヘルプ ビューアー MSHA の非常に基本的な XML スキーマを記述する入門書だけです。  この簡単な概要の下の実装例があることに注意してくださいし、HelpContentSetup.msha をサンプリングします。  
  
 この入門のため、MSHA の名前は HelpContentSetup.msha \(ファイルの名前できる拡張子を持つもの。MSHA\)。 HelpContentSetup.msha 以下の例では、cab ファイルまたは使用可能な MSHCs の一覧を含める必要があります。  注 \(は MSHA と CAB ファイルの種類の組み合わせをサポートしていません\) MSHA 内で一貫性のあるファイルの種類である必要があります。 CAB または MSHC ごとに存在する必要があります、\< div クラス \=「パッケージ」\>... \<\/div \> \(次の例を参照してください\)。  
  
 注: 次の実装例に記載しましたブランディング パッケージ。 これは、含めること、必要な要素を Visual Studio コンテンツの表示とコンテンツの動作を取得するために重要です。  
  
 HelpContentSetup.msha ファイルのサンプル: \(置換"コンテンツ セットの名前 1" と"コンテンツのファイル名を持つ 2" などセットの名前です\)。  
  
```  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div>.  
  
```  
  
1.  "C:\\SampleContent"のようなもののローカル フォルダーを作成します。  
  
2.  この例では、トピックを含む、MSHC ファイルを使用します。  MSHC を .zip から変更されたファイル拡張子を持つ zip です。MSHC します。  
  
3.  作成、テキスト ファイルとして HelpContentSetup.msha 下 \(メモ帳は、ファイルの作成に使用しました\) 上記に説明したようにフォルダーに保存し、\(手順 1. を参照してください\)。  
  
 注意してください「ブランド化」が存在して、一意のクラスです。 インストールされているコンテンツは、ブランド化が、MSHCs に含まれるコンテンツの動作は、ブランド化パッケージに含まれる適切なサポート要素に、この入門でブランド化 mshc が含まれています。 これは、システムがサポートされていない項目が取り込んだ \(インストール\) の一部のコンテンツを探すときにエラーが発生します。  
  
 パッケージをブランド化、Visual Studio を入手するには、作業フォルダーにある C:\\Program Files \(x86\) \\Microsoft Help Viewer\\v2.1\\ Branding\_en US.mshc ファイルをコピーします。  
  
```html  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div> <div class="package"> <span class="packageType">branding</span> <span class="name">Branding_en-US</span> <span class="deployed">True</span> <a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a> </div> </div> </body> </html>  
  
```  
  
 **まとめ**  
  
 使用して、上記の手順を拡張するには、Visual Studio ヘルプ ビューアーのコンテンツのセットを展開する Vsp は有効にします。  
  
### Visual Studio Shell \(Integrated および分離プロセス\) のヘルプの追加  
 **はじめに**  
  
 このチュートリアルでは、ヘルプ コンテンツを Visual Studio Shell アプリケーションに組み込むし、展開する方法を示します。  
  
 **必要条件**  
  
1.  [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 Shell 再頒布可能パッケージの分離](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
 **概要**  
  
 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] シェルのバージョンとは、 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] IDE アプリケーションを作成することができます。 このようなアプリケーションでは、分離シェルを作成する拡張機能と共にを含んでいます。 含まれている、分離シェル プロジェクト テンプレートを使用して、 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] SDK、拡張機能を作成します。  
  
 分離シェル ベースのアプリケーションとそのヘルプを作成するための基本的な手順:  
  
1.  取得、 [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] ISO Shell 再頒布可能パッケージ \(Microsoft ダウンロード\) します。  
  
2.  Visual Studio では、ヘルプの拡張機能に基づいている、分離シェル、たとえば、このチュートリアルの後半で説明されている Contoso ヘルプ拡張機能を作成します。  
  
3.  拡張機能と展開用の MSI \(アプリケーションのセットアップ\) に再配布可能な ISO シェルをラップします。 このチュートリアルでは、セットアップ手順は含まれません。  
  
 Visual Studio のコンテンツ ストアを作成します。 統合シェルでは、次のように、製品のカタログ名を Visual Studio12 を変更します。  
  
-   C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\] フォルダーを作成します。  
  
-   CatalogType.xml という名前のファイルを作成し、フォルダーに追加します。 ファイルには、次のコード行を含める必要があります。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
 レジストリのコンテンツ ストアを定義します。 Integrated Shell VisualStudio12 を製品カタログの名前に変更します。  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
     キー: LocationPath 文字列の値: C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12\\en\-US  
  
     キー: CatalogName 文字列の値: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] ドキュメント  
  
 **プロジェクトを作成します。**  
  
 分離シェル拡張機能を作成します。  
  
1.  Visual Studio で、\[ **ファイル**, を選択 **新しいプロジェクト**, \[ **その他のプロジェクトの種類** 選択 **機能拡張**, を選択し  **Visual Studio シェルの分離**します。 プロジェクトに名前を `ContosoHelpShell`\) を Visual Studio の分離シェル テンプレートに基づいて、拡張機能プロジェクトを作成します。  
  
2.  ソリューション エクスプ ローラーで、\[リソース ファイル\] フォルダー内の ContosoHelpShellUI プロジェクトに ApplicationCommands.vsct を開きます。 この行はコメント アウト \("No\_Help"を検索\) されていることを確認します。 `<!-- <define name=“No_HelpMenuCommands”/> -->`  
  
3.  F5 キーをコンパイルして実行する **デバッグ**します。 分離シェル IDE の実験用インスタンスで、 **ヘルプ** メニュー。 確認して、 **\[ヘルプの表示**, 、**ヘルプ コンテンツを削除して追加**, 、および **ヘルプ設定** コマンドが表示されます。  
  
4.  ソリューション エクスプ ローラーでのシェルのカスタマイズ\] フォルダーで、ContosHelpShell プロジェクトで ContosoHelpShell.pkgdef を開きます。 Contoso ヘルプ カタログを定義するには、次の行を追加します。  
  
    ```  
    [$RootKey$\Help] "Product"="Contoso" "Catalog"="Contoso" “Version"="100" "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  ソリューション エクスプ ローラーでのシェルのカスタマイズ\] フォルダーで、ContosHelpShell プロジェクトで ContosoHelpShell.Application.pkgdef を開きます。 F1 ヘルプを有効にするには、次の行を追加します。  
  
    ```  
    // F1 Help Provider [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="13407" "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}" @="Help3 Provider" [$RootKey$\HelpProviders] @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}" [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="Help3 Provider" @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  ソリューション エクスプ ローラーで \[ContosoHelpShell ソリューションのコンテキスト メニューを選択、 **プロパティ** メニュー項目です。**構成プロパティ**, \[ **Configuration Manager**します。**構成** \] 列で、"Debug"のすべての値を「リリース」に変更します。  
  
7.  ソリューションをビルドします。 これには、次のセクションで使用されるリリース フォルダーのファイルのセットが作成されます。  
  
 展開されている場合に、これをテストします。  
  
1.  コンピューターで、ダウンロードした ISO シェル \(より\) をインストールする Contoso を展開します。  
  
2.  \\\\Program Files \(\(x86\) にフォルダーを作成 \\ と名付けます `Contoso`します。  
  
3.  ContosoHelpShell リリース フォルダーから \\\\Program Files \(86\) \\Contoso\\ フォルダーへの内容をコピーします。  
  
4.  レジストリ エディターを選択して開始します。  **実行** で、 **開始** メニュー」と入力して `Regedit`します。 レジストリ エディターで **ファイル**, 、し **インポート**します。 ContosoHelpShell プロジェクト フォルダーに移動します。 ContosoHelpShell サブフォルダーでは、ContosoHelpShell.reg を選択します。  
  
5.  コンテンツ ストアを作成します。  
  
     ISO シェルの Contoso コンテンツ ストア C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\ContosoDev12 を作成します。  
  
     [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 統合シェル フォルダー C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12 を作成します。  
  
6.  CatalogType.xml を作成し、格納先 \(前の手順\) のコンテンツ ストアに追加します。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
7.  次のレジストリ キーを追加します。  
  
     HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12Key: LocationPath 文字列の値:  
  
     ISO シェルの場合。  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
     [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] 統合シェル。  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\\\en\-US  
  
     キー: CatalogName 文字列の値: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] ドキュメントです。 ISO シェルでは、これは、カタログの名前です。  
  
8.  \(Cab ファイルまたは MSHC と MSHA\) コンテンツをローカル フォルダーにコピーします。  
  
9. 統合シェル コマンドラインの例のコンテンツ ストアをテストします。 ISO シェル、製品と一致する適切なカタログと launchingApp の値を変更します。  
  
     "C:\\Program Files \(\(x86\) \\Microsoft Help Viewer\\v2.1\\HlpViewer.exe"\/catalogName VisualStudio12\/helpQuery メソッド \="ページ"&"id \= ContosoTopic0"\/launchingApp Microsoft VisualStudio、12.0  
  
10. \(Contoso アプリのルート\) から Contoso アプリケーションを起動します。 ISO シェル内で選択、 **ヘルプ** メニュー項目と変更、 **ヘルプ設定** に **を使用してローカル強化**します。  
  
11. シェルの中から選択、 **ヘルプ** し、メニュー項目 **\[ヘルプの表示**します。 ローカルのヘルプ ビューアーを起動する必要があります。**\[コンテンツの管理\]** タブを選択します。**インストール ソース**, 、選択、 **ディスク** オプション ボタンをクリックします。 選択、 **...** ボタンをクリックし、Contoso のコンテンツ \(前の手順でローカル フォルダーにコピー\) を含むローカル フォルダーに移動します。 HelpContentSetup.msha を選択します。 Contoso 書籍の書籍の選択項目として表示されます。 選択 **追加**, を選択し、 **更新** ボタン \(右下隅\)。  
  
12. Contoso IDE 内で f1 キー機能をテストする F1 キーを押します。  
  
### その他のリソース  
 ランタイム API を参照してください。 [Windows API のヘルプ](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)します。  
  
 API のヘルプを活用する方法の詳細については、を参照してください [ヘルプ ビューアーのコード例](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
 これらのコンポーネントに関するフィードバックを提供するには使用 [Microsoft Connect](http://connect.microsoft.com/)します。  
  
 する機能の候補を提出してください [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
 追加のヘルプを取得すると、 [MSDN 開発者向けドキュメントおよびヘルプ システムのフォーラム](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
 更新の最新の問題を参照してください、 [ヘルプ ビューアーの Readme](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
 ヘルプ ビューアーの PM チームを直接にアクセスするには、hlpfdbk@microsoft.com に電子メールを送信します。
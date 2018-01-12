---
title: "Microsoft ヘルプ ビューアー SDK |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c15956bc861f9eb20267dc97446cf5ea49cae31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft ヘルプ ビューアー SDK
この記事には、Visual Studio ヘルプ ビューアー インテグレーターの次のタスクが含まれています。  
  
-   トピック (F1 サポート) を作成します。  
  
-   ヘルプ ビューアーのコンテンツ ブランド パッケージを作成します。  
  
-   記事のセットを展開します。  
  
-   Visual Studio shell (integrated または分離) に追加のヘルプ  
  
-   その他のリソース  
  
### <a name="creating-a-topic-f1-support"></a>トピック (F1 サポート) を作成します。  
このセクションでは、記載されたトピック、トピックの要件、その表示された結果と共に (F1 サポート要件を含む) のトピックと最後に、例トピックを作成する方法の簡単な説明のコンポーネントの概要を示します。  
  
**ヘルプ ビューアーのトピックの概要**  
  
ヘルプ ビューアーがのインストールや、トピック、XHTML と共に、最後の更新時に、トピックに関連付けられているブランド パッケージ要素を取得して、提示されたコンテンツ ビューに発生する 2 つの結合トピックが表示するために呼び出されると (データをブランド化 +トピックのデータの場合)。  ブランド パッケージには、ロゴ、コンテンツの動作、およびブランド化のテキスト (著作権など) のサポートが含まれています。  ブランド パッケージ要素の詳細については、下「ブランド パッケージを作成する」を参照してください。  トピックに関連付けられているブランド パッケージがない場合に、ヘルプ ビューアーはフォールバック ブランド パッケージ (Branding_en US.mshc) ヘルプ ビューアー アプリケーションのルートにあるを使用します。  
  
**ヘルプ ビューアーのトピックの要件**  
  
ヘルプ ビューアー内で正しく表示される生のトピックのコンテンツは、W3C 基本 1.1 XHTML をする必要があります。  
  
通常、トピックには、2 つのセクションが含まれます。  
  
-   メタデータ (コンテンツのメタデータ参照を参照してください): トピック一意の ID、キーワードの値、トピック目次 ID など、そのトピックについてのデータは親ノード ID などです。  
  
-   本文のコンテンツ: 1.1 XHTML の基本的な W3C に準拠しているが含まれているサポートされるコンテンツの動作 (折りたたみ可能な領域、コード スニペットなどです。完全な一覧は、次に示します)。  
  
Visual Studio のブランド パッケージには、コントロールがサポートされています。  
  
-   リンク  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   継承されたメンバー  
  
-   LanguageSpecificText  
  
言語識別文字列 (いない大文字小文字を区別) がサポートされています。  
  
-   Javascript  
  
-   csharp または c# の場合  
  
-   cplusplus visualc++ または c + +  
  
-   jscript  
  
-   visual basic または vb  
  
-   f# fsharp または fs  
  
-   その他の言語の名前を表す文字列です。  
  
**ビューアーのヘルプ トピックの作成**  
  
ContosoTopic4.htm をという名前の新しい XHTML ドキュメントを作成し、タイトル タグ (下記) を含めます。  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
データを定義する方法のトピック (自社ブランドか) を表示する方法を次に、追加などの ID (その他のトピックでリンクの参照)、TOC 内でこのトピックの内容が存在する、f1 キーをこのトピックを参照します。サポートされているメタデータの完全な一覧については、次の表「コンテンツのメタデータ」を参照してください。  
  
-   この例では、自社ブランド パッケージ、Visual Studio ヘルプ ビューアーのブランド パッケージのバリアント型を使用します。  
  
-   F1 メタ名前と値を追加 ("Microsoft.Help.F1"コンテンツ"ContosoTopic4"= =) IDE プロパティ バッグ内の指定された F1 値に一致するされます。  (詳細については、F1 サポート セクションを参照してください)。 これは、f1 キーに一致する値、IDE で f1 キーを選択するときに、このトピックの内容を表示するための IDE 内から呼び出します。  
  
-   トピック ID を追加します。 これは、このトピックにリンクするその他のトピックで使用される文字列です。  これは、このトピックのヘルプ ビューアー ID です。  
  
-   目次のこのトピックの目次ノードが表示される場所を定義する、このトピックの親ノードを追加します。  
  
-   目次のこのトピックのノードの順序を追加します。 親ノードに n 個の子ノードがある場合は、子ノードの順序でこのトピックの場所を定義します。 たとえば、このトピックでは、4 4 子トピック数です)。  
  
メタデータの例」のセクション:  
  
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
  
ページのリンク、注のセクションで、折りたたみ可能な領域、コード スニペットでは、および言語固有のテキストのセクションで、このトピックの本文 (ヘッダーとフッターを含むされません) が含まれます。  これらの領域については、記載されたトピックのブランド化のセクションを参照してください。  
  
1.  トピック タイトルのタグを追加します。`<div class="title">Contoso Topic 4</div>`  
  
2.  注」セクションを追加します。`<div class="alert"> add your table tag and text </div>`  
  
3.  折りたたみ可能な領域を追加します。`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  コード スニペットを追加します。`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  コード言語の特定のテキストを追加:`<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />`その devLangnu に注意してください = その他の言語を入力することができます。 たとえば、devLangnu ="Fortran"Fortran が表示されるときに DisplayLanguage のコード スニペット Fortran を =  
  
6.  ページのリンクを追加します。`<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  注意: コード スニペットでコードの色付けがサポートされていない新しい"の表示言語の"(例、f#、Cobol、Fortran) モノクロ、されます。  
  
**ビューアーのヘルプ トピックを例**コードは、メタデータ、コード スニペットである、折りたたみ可能な領域、および特定のテキストの言語を定義する方法を示しています。  
  
```html
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
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>  
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
  
Visual Studio で、f1 キーを選択すると、ide のカーソルの位置から指定された値を生成し、入力「プロパティ バッグ」指定した値を (カーソル位置に基づいています。 機能 x の上にカーソルがある場合、x の機能はアクティブ/にフォーカスが置かれてし、値を持つプロパティ バッグを設定します。  F1 キーを選択すると、プロパティ バッグが設定され、Visual Studio の F1 コードは顧客の既定のヘルプ ソースがローカルまたはオンラインかどうかを次の (オンラインは既定値)、ユーザーの設定に基づく適切な文字列を作成し (オンラインは、既定値) のシェルの実行(ヘルプ管理者ガイド exe の起動パラメーターを参照してください)、ローカルのヘルプ ビューアー + 場合は、ローカルのヘルプ、既定値または URL では、MSDN パラメーター リスト内のキーワードを使用してプロパティ バッグからのキーワードのパラメーターを使用します。  
  
F1 キーを 3 つの文字列が返される場合、複数値文字列としてに対して実行する最初の用語では、検索、ヒットと呼ばれます。 場合が見つかると、完了です。ない場合は、次の文字列に移動します。  順序は重要です。 複数値のキーワードのプレゼンテーションには、最も長い文字列を短い文字列をする必要があります。  複数値のキーワードの場合はこれを確認するには、オンラインの F1 URL の文字列は、選択したキーワードを含める見てください。  
  
Visual Studio 2012 で意図的に行いましたより強力な除算オンラインとオフラインの間で渡されるように online の場合、ユーザーの設定であった場合、お単に F1 要求、クエリのオンライン サービスに直接ヘルプ ライブラリ エージェントを介してルーティングするのではなく、MSDN でVisual Studio 2010 で必要があります。 状態にし、依存しています"インストールされているベンダー コンテンツ = true"をそのコンテキストで異なる処理を実行するかどうかを判断します。 True の場合、顧客のため、サポートするに応じてこの解析およびルーティング ロジックを実行します。 False の場合、し、ここに移動する MSDN です。 場合は、ユーザーの設定は、ローカルには、すべての呼び出しだけに進みますローカル ヘルプのエンジンです。  
  
F1 フロー図に示します。  
  
![F1 フロー](../../extensibility/internals/media/f1flow.png "F1flow")  
  
ときに、ヘルプ ビューアー既定ヘルプ コンテンツのソースは、オンライン (ブラウザーで起動) に設定されます。  
  
-   Visual Studio パートナー (VSP) 機能は、F1 プロパティ バッグ (プロパティ バッグ prefix.keyword と、レジストリで見つかったプレフィックスの online の URL) に値を出力: F1 VSP URL + パラメーター ブラウザーに送信します。  
  
-   Visual Studio の機能 (言語のエディター、Visual Studio の特定のメニュー項目など): F1 が Visual Studio の URL をブラウザーに送信します。  
  
ヘルプ ビューアーの既定のヘルプ コンテンツ ソースをローカル ヘルプ (ヘルプ ビューアーの起動) を設定するとします。  
  
-   VSP 機能 F1 プロパティ バッグとローカル ストア インデックスの間でキーワードが一致する (プロパティ バッグ prefix.keyword は、ローカル ストア インデックス内で見つかった値を =): F1 ヘルプ ビューアーでトピックを表示します。  
  
-   Visual Studio の機能 (Visual Studio の機能から送出された、プロパティ バッグをオーバーライドする VSP のオプションはありません): F1 ヘルプ ビューアーでの Visual Studio のトピックを表示します。  
  
ヘルプ コンテンツの仕入先の F1 フォールバックを有効にするのには、次のレジストリ値を設定します。 F1 フォールバックは、ヘルプ ビューアーがオンラインでの F1 ヘルプ コンテンツの検索に設定されており、仕入先のコンテンツがユーザーのハード ドライブにローカルにインストールされていることを意味します。 場合でも、既定の設定は、オンライン ヘルプについては、ヘルプ ビューアーはローカル ヘルプ コンテンツをはずです。  
  
1.  設定、 **VendorContent** 2.3 のヘルプのレジストリ キーの下の値。  
  
    -   32 ビット オペレーティング システム。  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent"= dword:00000001  
  
    -   64 ビット オペレーティング システム。  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent"= dword:00000001  
  
2.  2.3 のヘルプのレジストリ キーの下のパートナーの名前空間を登録します。  
  
    -   32 ビット オペレーティング システム。  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< 名前空間\>*  
  
         「場所"=」オフライン"  
  
    -   64 ビット オペレーティング システム。  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< 名前空間\>*  
  
         「場所"=」オフライン"  
  
**基本のネイティブ Namespace 解析**  
  
ネイティブのベース名前空間を解析中にするには、レジストリで新しい DWORD にして追加の名前: BaseNativeNamespaces (キーの下、カタログをサポートする) の 1 にその値を設定します。  たとえば、Visual Studio のカタログを使用する場合は、パスに、キーを追加できます。  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
ヘッダーまたはメソッドが検出された形式で F1 キーワード、ときに '/' 文字は解析されます、次の構成体の結果として得られます。  
  
-   ヘッダー: は、レジストリに登録するために使用する名前空間になります  
  
-   方法: このなりますを介して渡されたキーワード。  
  
たとえば、CustomLibrary と呼ばれるカスタム ライブラリおよび MyTestMethod を f1 キーを要求が届くこととして書式設定するときに呼び出されるメソッドを指定`CustomLibrary/MyTestMethod`です。  
  
ユーザーがパートナー ハイブの下の名前空間として CustomLibrary を登録し、および、必要に応じて、どのような場所のキーを指定でき、MyTestMethod がクエリに渡されるキーワードになります。  
  
**デバッグ ツール、IDE のヘルプを有効にします。**  
  
次のレジストリ キーと値を追加します。  
  
HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic ヘルプ キー: 小売値でのデバッグ出力を表示します [はい]。  
  
IDE では、ヘルプ メニュー項目の下位選択"ヘルプ コンテキストのデバッグ  
  
**コンテンツのメタデータ**  
  
次の表では、かっこ間に表示される任意の文字列は、認識可能な値で置き換える必要があるプレース ホルダーがします。 たとえば、\<メタ name="Microsoft.Help.Locale"コンテンツ =「[言語コード]」/>、「[言語コード]」をなど、値で置換する必要があります"en-us"です。  
  
|プロパティ (HTML 形式)|説明|  
|--------------------------------------|-----------------|  
|\<メタ name="Microsoft.Help.Locale"コンテンツ「[言語コード]」/>|このトピックのロケールを設定します。 トピックでは、このタグを使用する場合は、1 回だけ使用する必要がありは、その他の Microsoft ヘルプ タグ上に挿入する必要があります。 このタグを使用しない場合、このトピックの本文が指定されている場合、製品のロケールに関連付けられているワード ブレーカーを使用して、インデックスが作成します。それ以外の場合、en-us ワード ブレーカーが使用されます。 このタグは、ISOC RFC 4646 に準拠します。 Microsoft ヘルプが正しく動作することを確認するには、するには、一般的な Language 属性ではなくこのプロパティを使用します。|  
|\<メタ name="Microsoft.Help.TopicLocale"コンテンツ「[言語コード]」/>|その他のロケールを使用しても、このトピックのロケールを設定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 カタログには、1 つ以上の言語でコンテンツが含まれている場合は、このタグを使用します。 カタログ内の複数のトピックでは、同じ ID を使用できますが、それぞれ一意 TopicLocale を指定する必要があります。 カタログのロケールに対応する TopicLocale を示すトピックでは、コンテンツのテーブルに表示されるトピックです。 ただし、このトピックのすべての言語バージョンは、検索結果に表示されます。|  
|\<タイトル > [タイトル]\</title >|このトピックのタイトルを指定します。 このタグは、必要ですが、トピック内で 1 回だけ使用する必要があります。 トピックの本文にタイトルが含まれていないかどうかは\<div > と内容のテーブルのトピックのセクションで、このタイトルが表示されます。|  
|\<meta name ="Microsoft.Help.Keywords"コンテンツ ="[aKeywordPhrase]"/>|ヘルプ ビューアーの [インデックス] ウィンドウに表示されるリンクのテキストを指定します。 リンクがクリックされたときに、トピックが表示されます。トピックに対して、複数のインデックス キーワードを指定するか、インデックスに表示するには、このトピックにリンクしたくない場合は、このタグを省略できます。 以前のバージョンのヘルプの"K"キーワードは、このプロパティに変換できます。|  
|\<メタ name="Microsoft.Help.Id"コンテンツ ="[TopicID]"/>|このトピックの識別子を設定します。 このタグは、必要ですが、トピック内で 1 回だけ使用する必要があります。 ID のトピックでは、カタログを同じロケール設定を持つ間で一意にする必要があります。 別のトピックでは、この ID を使用して、このトピックの内容へのリンクを作成できます。|  
|\<メタ name="Microsoft.Help.F1"content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|このトピックの F1 キーワードを指定します。 、トピックの、複数の F1 キーワードを指定するか、アプリケーション ユーザーが f1 キーを押したときに表示するには、このトピックしたくない場合は、このタグを省略することができます。 通常は、トピックの 1 つだけの F1 キーワードを指定します。 以前のバージョンのヘルプの"F"キーワードは、このプロパティに変換できます。|  
|\<メタデータ名"Description"のコンテンツを = =「[トピックの説明]」/>|このトピックの内容の短い概要を示します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 このプロパティは、クエリ ライブラリによって直接アクセスします。インデックス ファイルは格納されません。|  
 メタ name="Microsoft.Help.TocParent"コンテンツ ="[parent_Id]"/>|このトピックの親トピック目次を指定します。 このタグは、必要ですが、トピック内で 1 回だけ使用する必要があります。 値は、親の Microsoft.Help.Id です。 トピックには、コンテンツのテーブルの 1 つの場所を持つことができます。 「-1」では、TOC ルート トピック ID と見なされます。 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]、そのページは、ヘルプ ビューアーのホーム ページです。 これは、同じ理由で具体的にはいくつかのトピックを表示、上部のレベルを確認するに TocParent = 1 を追加します。ヘルプ ビューアーのホーム ページは、システム ページと置き換え可能なためです。 VSP が-1 の ID でページを追加しようとすると場合に、コンテンツのセットに追加された取得可能性がありますが、ヘルプ ビューアーのシステム ページ - ヘルプ ビューアーのホームを常に使用します。|  
|\<メタ name="Microsoft.Help.TocOrder"コンテンツ =「[正の整数]」/>|目次でこのトピックの内容が表示される場所のピア トピックに対して相対的を指定します。 このタグは、必要ですが、トピック内で 1 回だけ使用する必要があります。 値は整数です。 価値の高い整数を指定するトピック上、小さい方の値の整数を指定するトピックが表示されます。|  
|\<メタ name="Microsoft.Help.Product"コンテンツ「[製品コード]」/>|このトピックで説明する製品を指定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 この情報は、ヘルプのインデクサーに渡されるパラメーターとしても指定することができます。|  
|\<メタ name="Microsoft.Help.ProductVersion"コンテンツ ="[バージョン number]"/>|このトピックで説明する製品のバージョンを指定します。 トピックでは、このタグを使用する場合、1 回だけ使用する必要があります。 この情報は、ヘルプのインデクサーに渡されるパラメーターとしても指定することができます。|  
|\<メタ name="Microsoft.Help.Category"コンテンツ ="[string]"/>|製品で使用すると、コンテンツのサブセクションを識別します。 複数のサブセクションでは、トピックがわかります。 またはへのリンクを任意のサブセクションを識別したくない場合は、このタグを省略することができます。 このタグを使用して、以前のバージョンのヘルプからトピックを変換するとき、TargetOS な TargetFrameworkMoniker 属性を格納します。 コンテンツの形式は、AttributeName:AttributeValue です。|  
|\<メタ name="Microsoft.Help.TopicVersion コンテンツ =「[トピックのバージョン番号]」/>|カタログ内に複数のバージョンが存在する場合は、このトピックのバージョンを指定します。 このタグは 1 つ以上のバージョンのトピックに存在する場合、カタログ、たとえば、ときに、カタログにはによって、.NET Framework 3.5 とトピックの .NET Framework 4 のトピックが含まれます。 どちらも同じ Micro、必要な Microsoft.Help.Id は一意であることは保証されない、ためソフトです。Help.Id です。|  
|\<メタデータ名"SelfBranded"コンテンツを = =「[TRUE または false の場合]」/>|このトピックには、ヘルプ ライブラリ マネージャーのスタートアップ ブランド パッケージまたはトピックに固有であるブランド パッケージが使用しているかどうかを指定します。 このタグは真である必要がありますまたは FALSE です。 TRUE の場合、関連するトピックのブランド パッケージには、ヘルプ ライブラリ マネージャーが起動し、その他のコンテンツのレンダリングと異なる場合でも意図されたように、トピックが表示されるときに設定されているブランド パッケージがよりも優先し、します。 FALSE の場合は、ヘルプ ライブラリ マネージャーの起動時に設定されているブランド パッケージに基づいて、現在のトピックが表示されます。 既定では、ヘルプ ライブラリ マネージャーが想定 SelfBranded 変数が TRUE であると宣言されている場合は false に自己ブランド化そのため、宣言する必要はいない\<メタ名"SelfBranded"コンテンツを = ="FALSE"/>。|  
  
### <a name="creating-a-branding-package"></a>ブランド パッケージを作成します。  
Visual Studio リリースには、Visual Studio のパートナーの分離性と統合シェルを含む別の Visual Studio 製品の数が含まれます。  各製品には、ある程度のサポート、製品に固有のブランド化トピック ベースのヘルプ コンテンツが必要です。  たとえば、Visual Studio のトピックが必要、一貫性のあるブランド プレゼンテーションし、ISO シェルをラップする SQL Studio は、独自一意ヘルプ コンテンツのブランド化の各トピックです。  統合のシェル パートナーは、ブランド化、独自のトピックを維持しながら、親 Visual Studio 製品のヘルプ コンテンツに収まるように、ヘルプ トピックを必要があります。  
  
ブランド パッケージは、ヘルプ ビューアーが含まれている製品によってインストールされます。  Visual Studio 製品。  
  
-   フォールバック ブランド パッケージ (Branding_\<ロケール > .mshc) ヘルプ ビューアー 2.3 アプリのルートにインストールされます (例: C:\Program Files (x86) \Microsoft Help Viewer\v2.3)、ヘルプ ビューアー言語パックでします。  これは、パッケージのブランド化、いずれかの製品がインストールされていない場合に使用 (コンテンツがインストールされていない) か、インストールされているブランド パッケージが壊れています。  ブランド パッケージ アプリのルート フォールバックを使用する場合に、Visual Studio 要素 (ロゴとフィードバック) を無視することに注意してください。  
  
-   Visual Studio コンテンツがコンテンツ パッケージ サービスからインストールされている場合、ブランド パッケージは (の時間の最初のコンテンツのインストール シナリオで) もインストールされます。  ブランド パッケージの更新がある場合、更新プログラムがインストールされている場合、次のコンテンツの更新または追加のパッケージのインストール アクション。  
  
Microsoft ヘルプ ビューアーでは、トピックのメタデータに基づいて、トピックのブランド化をサポートします。  
  
-   トピックのメタデータを定義してブランド self = true、現状有姿のトピックを表示、何もしない (ブランド) 枝葉と同じです。  
  
-   False = トピック メタデータを定義してブランド self TopicVendor メタデータの値に関連付けられているブランド パッケージを使用します。  
  
-   コンテンツの場所トピック メタデータを定義 name="Microsoft.Help.TopicVendor"=\<ベンダー MSHA でブランド パッケージ名 >、コンテンツの値で定義されているブランド パッケージを使用します。  
  
-   Visual Studio カタログ内ではブランド パッケージの優先度のアプリケーションに注意してください。  最初の Visual Studio 既定ブランド化が適用され、次に、トピック メタデータで定義されている、場合ではサポートされて (で定義されているインストール msha) 関連付けられているブランド パッケージは、ブランド化ベンダー定義が上書きとして適用されます。  
  
ブランド化要素は、通常、3 つのカテゴリに分類されます。  
  
-   (例については、[フィードバック] リンク、条件付きの免責事項のテキスト、ロゴを含める) のヘッダー要素  
  
-   コンテンツの動作 (例については、展開/折りたたみコントロールのテキスト要素を含めるし、コード スニペットの要素)  
  
-   ページ フッター要素 (例: Copyright)  
  
アイテムのブランド要素を含めると見なされます (この仕様に記載)。  
  
-   カタログ/製品のロゴ (例、Visual Studio)  
  
-   フィードバックのリンク、および電子メールの要素  
  
-   免責事項  
  
-   著作権テキスト  
  
Visual Studio ヘルプ ビューアーのブランド パッケージ内のサポート ファイルは次のとおりです。  
  
-   グラフィックス (ロゴ、アイコンなど)  
  
-   Branding.js - スクリプト ファイルをサポートするコンテンツの動作  
  
-   Branding.xml、カタログ コンテンツ全体で一貫して使用される文字列。  注意: Visual Studio、branding.xml 内のテキスト要素のローカリゼーション インクルード _locID ="\<一意の値 >"  
  
-   Branding.css - プレゼンテーション一貫性を保つのためのスタイルの定義  
  
-   Printing.css の一貫したプレゼンテーションの印刷のスタイルの定義  
  
前述のように、ブランド パッケージは、トピックに関連付けられました。  
  
-   ときに SelfBranded = false がメタデータで定義されている、パッケージをブランド化カタログを継承するトピック  
  
-   または SelfBranded = false と一意のブランド パッケージに定義されて、MSHA 使用可能なコンテンツがインストールされている場合  
  
カスタム ブランド パッケージを実装する Vsp の (VSP コンテンツ、SelfBranded = True)、続行するには (ヘルプ ビューアーでのインストール) フォールバック ブランド パッケージを起動し、必要に応じて、ファイルの名前を変更します。  Branding_\<ロケール > .mshc ファイルが zip ファイル .mshc に変更されたファイル拡張子を持つ、するだけで .mshc から拡張子を .zip に変更し、コンテンツを抽出します。  ブランド パッケージ要素の下を参照してくださいおよび、必要に応じて変更 (たとえば、VSP ロゴと Branding.xml ファイル内のロゴへの参照にロゴを変更するなど、VSP 仕様あたり Branding.xml を更新) します。  
  
すべての変更が完了すると、目的のブランド化要素を含む zip ファイルを作成し、拡張機能を .mshc に変更します。  
  
カスタム ブランド パッケージを関連付けるには、(トピックを含む) コンテンツ mshc と共にブランド mshc ファイルへの参照を含む MSHA を作成します。  基本的な MSHA を作成する方法については、"MSHA"の下を参照してください。  
  
Branding.xml ファイルには、一貫してトピックが含まれているトピックの特定のアイテムを表示するために使用されるリストの要素が含まれています。\<メタ name="Microsoft.Help.SelfBranded"コンテンツ ="false"/>。  Branding.xml ファイル内の要素の Visual Studio の一覧は、以下に記載されています。  このリスト テンプレートとして使用する、ISO シェル採用者のニーズをブランド化、独自の製品を満たすのこれらの要素 (たとえばロゴ、フィードバック、および著作権) を変更するためのものことに注意してください。  
  
注:"{n}"によって示された変数は、コードの依存関係を持つ - 削除するか、これらの値を変更すると、エラーと可能性のあるアプリケーションがクラッシュします。Visual Studio のブランド パッケージでは、ローカリゼーション識別子 (例 _locID="codesnippet.n") が含まれています。  
  
**Branding.xml**  
  
|||  
|-|-|  
|機能:|**CollapsibleArea**|  
|使用:|折りたたまれてコンテンツ コントロールのテキストを展開します。|  
|**要素**|**[値]**|  
|ExpandText|Expand|  
|CollapseText|折りたたむ|  
|機能:|**CodeSnippet**|  
|使用:|コード スニペットのコントロールのテキスト。  注:「改行しない」領域でのコード スニペットのコンテンツは、スペースに変更されます。|  
|**要素**|**[値]**|  
|CopyToClipboard|クリップボードにコピー|  
|ViewColorizedText|色分け表示ビュー|  
|CombinedVBTabDisplayLanguage|Visual Basic (サンプル)|  
|VBDeclaration|宣言|  
|VBUsage|使用法|  
|機能:|**フィードバック、フッター、およびロゴ**|  
|使用:|電子メール経由で現在のトピックに関するフィードバックを提供する顧客のフィードバック コントロールを提供します。  コンテンツの著作権テキストです。  ロゴの定義です。|  
|**要素**|**値 (これらの文字列は、コンテンツの導入者のニーズを変更することができます)。**|  
|著作権情報|© 2013 Microsoft Corporation. All rights reserved.|  
|SendFeedback|\<href ="0"} {1} > フィードバックの送信\</a > Microsoft にお送りします。|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|機能:|**免責事項**|  
|使用:|一連のマシンのケースに関する免責事項は、コンテンツを変換します。|  
|**要素**|**[値]**|  
|MT_Editable|この記事は機械翻訳をでした。 インターネット接続があれば、同時に元の英語コンテンツを使用して、編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT_NonEditable|この記事は機械翻訳をでした。 インターネット接続があれば、同時に元の英語コンテンツを使用して、編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT_QualityEditable|この記事は手動翻訳されたものです。 インターネット接続があれば、同時に元の英語コンテンツを使用して、編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT_QualityNonEditable|この記事は手動翻訳されたものです。 インターネット接続があれば、同時に元の英語コンテンツを使用して、編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT_BetaContents|この記事は機械翻訳ベータ リリースをでした。 インターネット接続があれば、同時に元の英語コンテンツを使用して、編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|MT_BetaRecycledContents|この記事は、ベータ リリースの手動翻訳されたものです。 インターネット接続があれば、同時に元の英語コンテンツを使用して、編集可能モードでこのページを表示する「このトピックをオンラインでの表示」を選択します。|  
|機能:|**LinkTable**|  
|使用:|オンライン トピックは、リンクのサポート|  
|**要素**|**[値]**|  
|LinkTableTitle|リンク テーブル|  
|TopicEnuLinkText|英語版が表示\</a > お使いのコンピューターで利用可能なこのトピックのです。|  
|TopicOnlineLinkText|このトピックの内容を表示\<、href ="0"} {1} > オンライン\</a >|  
|OnlineText|Online|  
|機能:|**ビデオのオーディオ コントロール**|  
|使用:|要素とビデオのコンテンツのテキストを表示します。|  
|**要素**|**[値]**|  
|MultiMediaNotSupported|{0} コンテンツをサポートするためには、Internet Explorer 9 以降をインストールする必要があります。|  
|VideoText|ビデオを表示します。|  
|AudioText|オーディオのストリーミング|  
|OnlineVideoLinkText|\<p > このトピックに関連付けられているビデオを表示するには、クリックして {0}\<、href =「\ \<」> {2}here\</a >.\</p >|  
|OnlineAudioLinkText|\<p > このトピックに関連付けられているオーディオを聴く {0} をクリックして\<、href =「\ \<」> {2}here\</a >.\</p >|  
|機能:|**コンテンツがインストールされていないコントロール**|  
|使用:|Contentnotinstalled.htm の表示に使用するテキスト要素 (文字列)|  
|**要素**|**[値]**|  
|ContentNotInstalledTitle|コンテンツがコンピューターに見つかりませんでした。|  
|ContentNotInstalledDownloadContentText|\<p >、コンピューターにコンテンツをダウンロードする\<、href ="0"} {1} > 管理 タブをクリックして\</a >.\</p >|  
|ContentNotInstalledText|\<p > お使いのコンピューターにコンテンツがインストールされていません。 ローカル ヘルプ コンテンツのインストールは、管理者を参照してください。\</p >|  
|機能:|**トピックが見つかりません。 コントロール**|  
|使用:|Topicnotfound.htm の表示に使用するテキスト要素 (文字列)|  
|**要素**|**[値]**|  
|TopicNotFoundTitle|コンピューターには、要求されたトピックを見つけることができません。|  
|TopicNotFoundViewOnlineText|\<p > することは要求されたトピックがコンピューターに見つかりませんでした\<、href ="0"} {1} > オンライン トピックを参照して\</a >。\< 。/p >|  
|TopicNotFoundDownloadContentText|\<p > 類似トピックへのリンクのナビゲーション ウィンドウを参照してくださいまたは\<、href ="0"} {1} > 管理 タブをクリックして\</a > お使いのコンピューターにコンテンツをダウンロードする\<。/p >|  
|TopicNotFoundText|\<p > 要求されたトピックがコンピューターに見つかりませんでした。\</p >|  
|機能:|**トピックには、コントロールが破損しています**|  
|使用:|Topiccorrupted.htm の表示に使用するテキスト要素 (文字列)|  
|**要素**|**[値]**|  
|TopicCorruptedTitle|要求されたトピックを表示できません。|  
|TopicCorruptedViewOnlineText|\<p > ヘルプ ビューアーが要求されたトピックを表示することはできません。 トピックの内容や、基になるシステム依存関係のエラーである可能性があります。\</p >|  
|機能:|**ホーム ページのコントロール**|  
|使用:|ヘルプ ビューアーの最上位ノードのコンテンツの表示をサポートするテキストです。|  
|**要素**|**[値]**|  
|HomePageTitle|ヘルプ ビューアーのホーム|  
|HomePageIntroduction|\<p > は、Microsoft ヘルプ ビューアーのすべての Microsoft ツール、製品、テクノロジ、およびサービスを使用してユーザー情報の重要なソースへようこそ。 ヘルプ ビューアーでは、操作方法に関する説明とリファレンスの情報、サンプル コード、技術記事、および詳細にアクセスできます。 コンテンツのテーブルを参照、目的のコンテンツを検索するには、フルテキスト検索を使用してまたはキーワード インデックスを使用してコンテンツ内を移動します。\</p >|  
|HomePageContentInstallText|\<p >\<br/> を使用して、 \<、href ="0"} {1} > コンテンツの管理\</a > タブでは、次の操作を:\<ul >\<li > お使いのコンピューターにコンテンツを追加します\<。/li >\<li > ローカル コンテンツに更新プログラムを確認します\<。/li >\<li > お使いのコンピューターからコンテンツを削除します\<。/li >\</ul >\</p >|  
|HomePageInstalledBooks|インストールしたブック|  
|HomePageNoBooksInstalled|コンテンツがコンピューターに見つかりませんでした。|  
|HomePageHelpSettings|ヘルプ コンテンツの設定|  
|HomePageHelpSettingsText|\<p > 現在の設定は、ローカルのヘルプ。 ヘルプ ビューアーには、コンピューターにインストールされているコンテンツが表示されます。\<br/> を Visual Studio のメニュー バーで、上のヘルプ コンテンツのソースを変更する\<span style ="0"} > ヘルプ設定のため、\</span >.\<br/>\</p >|  
|メガバイト数|MB|  
  
**branding.js**  
  
Branding.js ファイルには、JavaScript Visual Studio ヘルプ ビューアーのブランド要素によって使用にはが含まれています。  ブランド化要素とサポートの JavaScript 関数の一覧を次に示します。  すべての文字列をこのファイル用にローカライズするのには、このファイルの上部にある「ローカライズ可能な文字列」セクションで定義されます。  Branding.js ファイル内の loc 文字列に ICL ファイルが作成されたことに注意してください。  
  
||||  
|-|-|-|  
|**ブランド化機能**|**JavaScript 関数**|**説明**|  
|Var しています.||変数を定義します。|  
|ユーザー コードの言語を取得します。|setUserPreferenceLang|インデックスをマップ # コード言語を|  
|設定および cookie の値を取得|getCookie、setCookie||  
|継承されたメンバー|changeMembersLabel|継承されたメンバーの展開/折りたたみ|  
|ときに SelfBranded = False|onLoad|かどうかは、印刷要求をチェックするクエリ文字列を読み取ります。  ユーザーの優先 タブの重点を置くすべての codesnippets を設定します。場合は、印刷要求が、isPrinterFriendly を true に設定します。 ハイ コントラスト モードを確認します。|  
|コード スニペット|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||ChangeTab||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|一覧には、折りたたみ可能なコントロールのすべてのオブジェクトを書き込みます。|  
||CA_Click|折りたたみ可能な領域の状態に基づいて、どのイメージおよび表示するテキストを定義します|  
|ロゴのコントラストのサポート|isBlackBackground()|背景が黒色かどうかを判断するには、呼び出されます。  正確な場合にのみハイ コントラスト モードにします。|  
||isHighContrast()|色の範囲を使用してハイ コントラスト モードを検出するには|  
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
  
ブランド パッケージには、どのコンテンツ セットがインストールされている説明したセクションとトピックできないときにユーザーに示すページが含まれています、ホームページなどのヘルプ コンテンツのユーザーに重要な情報を通信するためのシナリオをサポートする HTM ファイルのセットが含まれています。ローカルの一連のトピックにあります。 製品ごとにこれらの HTM ファイルを変更できることに注意してください。  ISO シェル ベンダーは、既定のブランド パッケージを実行し、変更の動作とこれらのページのコンテンツ スイートに、必要なできます。  これらのファイルは、ブランド タグ branding.xml ファイルから対応するコンテンツを取得するために、それぞれのブランド パッケージを参照してください。  
  
||||  
|-|-|-|  
|**ファイル**|**使用します。**|**コンテンツ ソースの表示**|  
|homepage.htm|これは、現在インストールされているコンテンツ、およびその内容についてユーザーに提示する適切な他のメッセージを表示するページです。  このファイルに追加メタ データ属性の"Microsoft.Help.Id"コンテンツ「-1」配置このローカル コンテンツ TOC の上部にあるコンテンツを = です。||  
||< META_HOME_PAGE_TITLE_ADD/>|Branding.xml、タグ\<HomePageTitle >|  
||< HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding.xml、タグ\<HomePageIntroduction >|  
||< HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Branding.xml、タグ\<HomePageContentInstallText >|  
||< HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|Branding.xml タグ セクションの見出し\<HomePageInstalledBooks >、アプリケーションから生成されるデータ\<HomePageNoBooksInstalled > ときにブックがインストールされていません。|  
||< HOME_PAGE_SETTINGS_SECTION_ADD/>|Branding.xml タグ セクションの見出し\<HomePageHelpSettings >、テキストのセクション\<HomePageHelpSettingsText >。|  
|topiccorrupted.htm|何らかの理由を表示することはできませんが、ローカルのセットにトピックが存在する場合 (コンテンツが破損している)。||  
||< META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding.xml、タグ\<TopicCorruptedTitle >|  
||< TOPIC_CORRUPTED_SECTION_ADD/>|Branding.xml、タグ\<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|トピックが存在しないときのローカル コンテンツで使用されず、設定された場合、オンライン||  
||< META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding.xml、タグ\<TopicNotFoundTitle >|  
||< META_TOPIC_NOT_FOUND_ID_ADD/>|Branding.xml、タグ\<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||< TOPIC_NOT_FOUND_SECTION_ADD/>|Branding.xml、タグ\<TopicNotFoundText >|  
|contentnotinstalled.htm|製品のインストールされているローカルのコンテンツがない場合。||  
||< META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding.xml、タグ\<ContentNotInstalledTitle >|  
||< META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding.xml、タグ\<ContentNotInstalledDownloadContentText >|  
||< CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding.xml、タグ\<ContentNotInstalledText >|  
  
**CSS ファイル**  
  
Visual Studio ヘルプ ビューアーのブランド パッケージには、一貫性のある Visual Studio のヘルプ コンテンツの表示をサポートするために 2 つの css ファイルが含まれています。  
  
-   Branding.css - には、場所を表示するための css 要素が含まれています SelfBranded = false。  
  
-   Printer.css - には、場所を表示するための css 要素が含まれています SelfBranded = false。  
  
Branding.css ファイルには、Visual Studio トピック プレゼンテーションの定義が含まれています。 (注意点は、branding.css 含まれること、Branding_\<ロケール > パッケージ サービスから .mshc を変更することがあります)。  
  
**グラフィック ファイル**  
  
Visual Studio コンテンツには、ロゴを Visual Studio およびその他のグラフィックスが表示されます。  Visual Studio ヘルプ ビューアーのブランド パッケージでのグラフィックス ファイルの完全な一覧は、以下に示します。  
  
||||  
|-|-|-|  
|**ファイル**|**使用します。**|**例**|  
|clear.gif|折りたたみ可能な領域を表示するために使用します。||  
|footer_slice.gif|フッター プレゼンテーション||  
|info_icon.gif|情報を表示するときに使用|免責情報|  
|online_icon.gif|このアイコンはオンラインへのリンクに関連付けるには||  
|tabLeftBD.gif|コード スニペットのコンテナーを表示するために使用します。||  
|tabRightBD.gif|コード スニペットのコンテナーを表示するために使用します。||  
|vs_logo_bk.gif|Branding.xml タグで定義されているように、通常のコントラスト ロゴ参照に使用される\<LogoFileName >。  Visual Studio 製品のロゴの名前は vs_logo_bk.gif です。||  
|vs_logo_wh.gif|Branding.xml タグで定義されている、通常の高いロゴ参照に使用される\<LogoFileNameHC >。  Visual Studio 製品のロゴの名前は vs_logo_wh.gif です。||  
|ccOff.png|キャプションのグラフィック||  
|ccOn.png|キャプションのグラフィック||  
|ImageSprite.png|折りたたみ可能な領域を表示するために使用します。|展開または折りたたむグラフィック|  
  
### <a name="deploying-a-set-of-topics"></a>トピックのセットを展開します。  
これは、ヘルプ ビューアーのコンテンツ展開 MSHA ファイルおよび cab ファイルのセットの構成設定を作成するための非常に単純でクイック チュートリアルまたは MSHC にはトピックが含まれています。 MSHA は、cab ファイルのセットを記述する XML ファイルまたは MSHC ファイルです。 ヘルプ ビューアーは、(、コンテンツの一覧を取得する MSHA を読み取ることができます。CAB またはします。MSHC ファイル) のローカル インストールに使用できます。  
  
これは、ヘルプ ビューアー MSHA の非常に基本的な XML スキーマを記述する入門書だけです。  この概要の下の実装例があることに注意してください、HelpContentSetup.msha のサンプルです。  
  
この入門のための MSHA の名前は HelpContentSetup.msha (ファイルの名前、何でもかまいません拡張子を持つ。MSHA)。 HelpContentSetup.msha (次の例) は、cab ファイルまたは使用可能な MSHCs のリストを含める必要があります。  ファイルの種類 (は MSHA および CAB ファイルの種類の組み合わせをサポートしていません) MSHA 内で一貫している必要がありますに注意してください。 CAB または MSHC ごとに存在する必要があります、 \<div クラス =「パッケージ」>.\</div > (次の例を参照してください)。  
  
注: 次の実装例を記載しましたブランド パッケージです。 これは、含めること、必要な Visual Studio のコンテンツのレンダリング要素とコンテンツの動作を取得するために重要です。  
  
HelpContentSetup.msha ファイルのサンプル: (「コンテンツは、名前の 1 を設定」を置換し、"セット name 2" など、ファイル名でコンテンツです)。  
  
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
</div>.  
  
```  
  
1.  "C:\SampleContent"次のように、ローカル フォルダーを作成します。  
  
2.  この例では、トピックを格納するのに、MSHC ファイルを使用します。  MSHC は、ファイルの拡張子を .zip から変更を zip です。MSHC です。  
  
3.  作成、テキスト ファイルとして HelpContentSetup.msha 下 (メモ帳は、ファイルの作成に使用された) 上に表示されるフォルダーに保存して (手順 1. を参照してください)。  
  
なお「ブランド化」が存在して、一意では、クラスです。 インストールされているコンテンツのブランドになり、MSHCs に含まれているコンテンツの動作は、ブランド パッケージに含まれる適切なサポート要素できるように、この入門でブランド mshc が含まれます。 これを行わない場合は、システムがサポートされていない項目が取り込んだ (インストール) の一部のコンテンツを探すときにエラーが発生します。  
  
パッケージのブランド化、Visual Studio を入手するには、作業フォルダーに C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ で Branding_en US.mshc ファイルをコピーします。  
  
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
  
使用して、上記の手順の拡張は、Visual Studio ヘルプ ビューアーのコンテンツのセットを展開する Vsp を有効になります。  
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Visual Studio Shell (Integrated および分離プロセス) に追加のヘルプ  
**はじめに**  
  
このチュートリアルでは、ヘルプ コンテンツを Visual Studio Shell アプリケーションに組み込むし、それを展開する方法を示します。  
  
**必要条件**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 シェル再頒布可能パッケージの分離](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**概要**  
  
[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]シェルは、バージョンの[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]IDE をアプリケーションを作成できます。 このようなアプリケーションでは、作成した拡張機能と共に Isolated Shell を含んでいます。 含まれている、Isolated Shell プロジェクト テンプレートを使用して、 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK、拡張機能を作成します。  
  
Isolated Shell ベースのアプリケーションとそのヘルプを作成するための基本的な手順:  
  
1.  取得、 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO のシェルの再頒布可能パッケージ (Microsoft ダウンロード)。  
  
2.  Visual Studio で、ヘルプの拡張機能に基づいている分離シェル、たとえば、このチュートリアルの後半で説明されている、Contoso ヘルプ用の拡張機能を作成します。  
  
3.  拡張機能と展開 MSI (アプリケーションのセットアップ) に再配布可能な ISO シェルをラップします。 このチュートリアルでは、セットアップ手順は含まれません。  
  
Visual Studio のコンテンツ ストアを作成します。 Integrated Shell シナリオでは、次のように、製品のカタログ名を Visual Studio12 を変更します。  
  
-   C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 フォルダーを作成します。  
  
-   CatalogType.xml をという名前のファイルを作成し、フォルダーに追加します。 ファイルは、次のコード行を含める必要があります。  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
レジストリのコンテンツ ストアを定義します。 Integrated Shell、VisualStudio15 を製品カタログの名前に変更します。  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     キー: LocationPath 文字列の値: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     キー: CatalogName 文字列の値:[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]ドキュメント  
  
**プロジェクトの作成**  
  
分離シェル拡張機能を作成します。  
  
1.  Visual Studio で、**ファイル**、選択**新しいプロジェクト****その他のプロジェクトの種類**選択**機能拡張**を選択し**Visual Studio Isolated Shell**です。 プロジェクトに名前を`ContosoHelpShell`) を Visual Studio Isolated Shell テンプレートに基づいて、拡張機能プロジェクトを作成します。  
  
2.  ソリューション エクスプ ローラーで、ContosoHelpShellUI のプロジェクトで、[リソース ファイル] フォルダー ApplicationCommands.vsct を開きます。 この行はコメント アウト ("No_Help"の検索) されていることを確認します。`<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  F5 キーをコンパイルして実行する**デバッグ**です。 分離シェル IDE の実験用インスタンスの選択、**ヘルプ**メニュー。 確認して、 **ヘルプの表示**、**ヘルプ コンテンツを削除して追加**、および**ヘルプ設定**コマンドが表示されます。  
  
4.  ソリューション エクスプ ローラーで、ContosHelpShell のプロジェクトで、シェルのカスタマイズ フォルダー ContosoHelpShell.pkgdef を開きます。 Contoso ヘルプ カタログを定義するのには、次の行を追加します。  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  ソリューション エクスプ ローラーで、ContosHelpShell のプロジェクトで、シェルのカスタマイズ フォルダー ContosoHelpShell.Application.pkgdef を開きます。 F1 ヘルプを有効にするには、次の行を追加します。  
  
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
  
6.  ソリューション エクスプ ローラーで、ContosoHelpShell ソリューションのコンテキスト メニューを選択、**プロパティ**メニュー項目。 **構成プロパティ** **Configuration Manager**です。 **構成**列、"Release"すべて"Debug"の値に変更します。  
  
7.  ソリューションをビルドします。 これには、次のセクションで使用されるリリース フォルダーで、一連のファイルが作成されます。  
  
展開されている場合に、これをテストします。  
  
1.  コンピューターで、ダウンロードした ISO シェル (から) をインストールする Contoso を展開します。  
  
2.  フォルダーを作成\\\Program Files (x86)\\、名前を付けます`Contoso`です。  
  
3.  ContosoHelpShell リリース フォルダーの内容をコピー \\\Program Files (x86) \Contoso\ フォルダーです。  
  
4.  レジストリ エディターを選択して開始**実行**で、**開始**メニュー」と入力して`Regedit`です。 レジストリ エディターで、次のように選択します。**ファイル**、し**インポート**です。 ContosoHelpShell プロジェクト フォルダーに移動します。 ContosoHelpShell のサブフォルダーに ContosoHelpShell.reg を選択します。  
  
5.  コンテンツ ストアを作成します。  
  
     ISO shell - C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 Contoso コンテンツ ストアを作成します。  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrated Shell、C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 フォルダーを作成します。  
  
6.  CatalogType.xml を作成し、ある (前の手順) のコンテンツ ストアに追加します。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  次のレジストリ キーを追加します。  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath 文字列値。  
  
     ISO シェルには。  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Integrated Shell:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-u. s.  
  
     キー: CatalogName 文字列の値:[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]ドキュメント。 ISO シェルには、これは、カタログの名前です。  
  
8.  (Cabs または MSHC および MSHA) コンテンツをローカル フォルダーにコピーします。  
  
9. Integrated Shell コマンドラインの例のコンテンツ ストアをテストします。 ISO シェルには、製品に一致するように適切なカタログと launchingApp の値を変更します。  
  
     "C:\Program Files (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe"/catalogName VisualStudio15/helpQuery メソッド ="ページ"&"id = ContosoTopic0"/launchingApp Microsoft VisualStudio、12.0  
  
10. (Contoso アプリケーション ルート) から Contoso アプリケーションを起動します。 ISO シェル内で選択、**ヘルプ**メニュー項目と変更、**ヘルプ設定**に**ローカル ヘルプの使用**です。  
  
11. シェル内で選択、**ヘルプ**し、メニュー項目**ヘルプの表示**です。 ローカルのヘルプ ビューアーを起動する必要があります。 **[コンテンツの管理]** タブを選択します。**インストール ソース**、選択、**ディスク**オプション ボタンをクリックします。 選択、**しています.**ボタンをクリックし、Contoso コンテンツ (上記の手順でローカル フォルダにコピー) を含むローカル フォルダーに移動します。 HelpContentSetup.msha を選択します。 Contoso は、本の選択で帳に表示されるはずです。 選択**追加**を選択し、**更新**ボタン (右下隅)。  
  
12. Contoso IDE 内で f1 キー機能をテストする、F1 キーを選択します。  
  
### <a name="additional-resources"></a>その他のリソース  
ランタイム API を参照してください。 [Windows ヘルプ API](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx)です。  
  
ヘルプの API を活用する方法の詳細については、次を参照してください[ヘルプ ビューアーのコード例。](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
これらのコンポーネントに関するフィードバックを提供する使用[Microsoft Connect](http://connect.microsoft.com/)です。  
  
機能の提案を送信してください[Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
追加のヘルプを取得するには、次のようにしてください、 [MSDN デベロッパー ドキュメントおよびヘルプ システムのフォーラム。](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
最新の問題、更新プログラムを参照してください、[ヘルプ ビューアーの Readme](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
ヘルプ ビューアー PM チームに直接連絡にメールを送信します。hlpfdbk@microsoft.com
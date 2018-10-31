# <a name="metadata-and-markdown-template"></a>メタデータとマークダウン テンプレート

このコア ドキュメント テンプレートには、メタデータの設定に関するガイドラインだけでなく、マークダウン構文の例が含まれています。 これを最大限に活用するには、[生のマークダウン](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)と[表示ビュー](https://github.com/dotnet/docs/blob/master/styleguide/template.md)の両方を表示する必要があります (たとえば、生のマークダウンにはメタデータ ブロックが表示されますが、表示ビューには表示されません)。

マークダウン ファイルを作成する場合、このテンプレートを新しいファイルにコピーして、下記のようにメタデータを記入し、上の H1 見出しを記事のタイトルに設定して、コンテンツを削除します。 


## <a name="metadata"></a>メタデータ 

完全なメタデータ ブロックは上部 ([生のマークダウン](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)の) にあり、必須フィールドとオプション フィールドに分割されています。 次に注意事項をいくつか示します。

- コロン (:) とメタデータ要素の値の間にはスペースが**必要です**。
- オプション メタデータ要素に値がない場合は、# を使用して要素をコメントにするか、削除します (空白のままにしたり、"na" を使用したりしないでください)。コメントにした要素に値を追加する場合は、# を必ず削除してください。
- 値 (タイトルなど) にコロンが含まれていると、メタデータ パーサーが中断します。 この場合は、タイトルを二重引用符で囲みます (例: `title: "Writing .NET Core console apps: An advanced step-by-step guide"`)。
- **title**: このタイトルは検索エンジンの結果に表示されます。 パイプ (|) の後に製品名を追加することもできます (例: `title: Developing Libraries with Cross Platform Tools | .NET Core`)。 タイトルは H1 見出しのタイトルと同一でなくてもかまいません。65 文字以下にする必要があります (| 製品名を含む)。
- **author**、**manager**、**ms.reviewer**: "author" フィールドには、作成者のエイリアスではなく、**GitHub ユーザー名**を含める必要があります。  一方、"manager" フィールドと "ms.reviewer" フィールドには Microsoft エイリアスを含める必要があります。 ms.reviewer は、記事または機能に関連付けられている PM/開発者の名前を指定します。
- **ms.devlang** はテクノロジを定義します。 サポートされている値には、dotnet、cpp、csharp、fsharp、vb、xml などがあります。
- **ms.assetid**: これは、ビジネス インテリジェンス (BI) などの内部追跡を目的に使用される記事の GUID です。 新しいマークダウン ファイルを作成する場合は、[https://www.guidgenerator.com](https://www.guidgenerator.com) から GUID を取得します。 

## <a name="basic-markdown-gfm-and-special-characters"></a>基本マークダウン、GFM、特殊文字

すべての基本マークダウンと GitHub Flavored Markdown (GFM) がサポートされています。 それらの詳細については、次を参照してください。

- [Baseline Markdown syntax (ベースライン マークダウン構文)](https://daringfireball.net/projects/markdown/syntax)
- [GFM documentation (GFM ドキュメント)](https://guides.github.com/features/mastering-markdown)

マークダウンでは書式設定に \*、\`、\# などの特殊文字を使用します。 これらの文字のいずれかをコンテンツに含める場合は、次の 2 つのどちらかを行う必要があります。

- 特殊文字の前にバックスラッシュを入力して、"エスケープ" する (たとえば、\* の場合は `\*`)
- 文字の [HTML エンティティ コード](http://www.ascii.cl/htmlcodes.htm)を使用する (たとえば、&#42 の場合は `&#42;`)。

## <a name="file-name"></a>ファイル名

ファイル名には次の規則を使用します。
* 小文字、数字、ハイフンのみを使用する。
* スペースや句読点を使用しない。 ハイフンを使用して、ファイル名の単語と数字を区切る。
* develop (開発)、buy (購入)、build (ビルド)、troubleshoot (トラブルシューティング) など、具体的な動作動詞を使用する。 -ing 形の語は使用しません。
* 小さな単語を使用しない。a、and、the、in、or などは含めません。
* マークダウンで記述し、.md ファイル拡張子を使用する必要がある。
* ファイル名を極力短くする。 記事の URL の一部となるためです。  



## <a name="headings"></a>見出し

文スタイルで大文字化します。 次のものは必ず大文字にします。
- 見出しの最初の文字。 
- タイトルまたは見出し内のコロンの後に続く文字 (たとえば、"How to: Sort an array" のようにします)。 

見出しは atx スタイルを使用して作成する必要があります。つまり、見出しを示すために行の先頭に 1 から 6 文字のハッシュ文字 (#) を使用します。これは、HTML 見出しレベルの H1 〜 H6 に対応します。 レベル 1 とレベル 2 のヘッダーの例が上で使用されています。 

トピックのレベル 1 の見出し (H1) は 1 つだけにする**必要があります**。これがページ上のタイトルとして表示されます。

見出しが `#` 文字で終わる場合は、タイトルを正しく表示するために末尾に余分の `#` 文字を追加する必要があります。 たとえば、`# Async Programming in F# #` のようにします。     

レベル 2 の見出しは、ページ上タイトルの下にある "この記事内" セクションに表示されるページ上の目次を生成します。

### <a name="third-level-heading"></a>レベル 3 の見出し
#### <a name="fourth-level-heading"></a>レベル 4 の見出し
##### <a name="fifth-level-heading"></a>レベル 5 の見出し
###### <a name="sixth-level-heading"></a>レベル 6 の見出し
 
## <a name="text-styling"></a>テキストのスタイル指定

*斜体* ファイル、フォルダー、パス (長い項目の場合は独立した行に分割)、新しい用語、URL (既定ではリンクとして表示されますが、それ以外の場合) に使用します。

**太字** UI 要素に使用します。

## <a name="links"></a>リンク

### <a name="internal-links"></a>内部リンク

同じマークダウン ファイル内のヘッダーにリンクする (アンカー リンクとも呼ばれます) には、リンク先のヘッダーの ID を確認する必要があります。 ID を確認するには、表示された記事のソースを表示して、ヘッダーの ID (例: `id="blockquote"`) を検索し、# に ID をつなげたものを使用してリンクします (例: `#blockquote`)。
ID はヘッダー テキストに基づいて自動生成されます。 そのため、たとえば、`## Step 2` という名前の一意のセクションの場合、ID は `id="step-2"` のようになります。

- 例: [Chapter 1](#chapter-1)

同じリポジトリ内のマークダウン ファイルにリンクするには、ファイル名の末尾に ".md" を含めた[相対リンク](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)を使用します。

- 例: [Readme ファイル](../readme.md)
- 例: [.NET にようこそ](../docs/welcome.md)

同じリポジトリ内のマークダウン ファイルのヘッダーにリンクするには、相対リンクとハッシュタグ リンクを使用します。

- 例: [.NET コミュニティ](../docs/welcome.md#community)

### <a name="external-links"></a>外部リンク

外部ファイルにリンクするには、完全な URL をリンクとして使用します。

- 例: [GitHub](http://www.github.com)

URL がマークダウン ファイルに表示されると、クリック可能なリンクに変換されます。

- 例 : http://www.github.com

### <a name="links-to-apis"></a>API へのリンク

ビルド システムには、外部リンクを使用せずに .NET Core API にリンクできるようにするいくつかの拡張機能が備えられています。  
API にリンクする場合は、ソース コードから自動生成される一意識別子 (UID) を使用できます。

次のいずれかの構文を使用できます。
1. マークダウン リンク: `[link_text](xref:UID)`
2. 自動リンク: `<xref:UID>`
3. 短縮形: `@UID`

- 例 : `@System.String`
- 例 : `[String class](xref:System.String)` 

この表記の使用に関する詳細は、「[Using cross reference (相互参照の使用)](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference)」を参照してください。

> 現時点では、UID を検索する簡単な方法はありません。 API の UID を検索する最善の方法は、このリポジトリ [docascode/coreapi](https://github.com/docascode/coreapi) 内で検索する方法です。 将来的により優れたシステムを提供できるように取り組んでいます。

UID に特殊文字 \` または \# が含まれている場合は、UID 値は次の例のようにそれぞれ %60 と %23 として HTML エンコードする必要があります。
- 例: @System.Threading.Tasks.Task\`1 は `@System.Threading.Tasks.Task%601` になります
- 例: @System.Exception \#ctor は `@System.Exception.%23ctor` になります

## <a name="lists"></a>表示内容

### <a name="ordered-lists"></a>番号付きリスト

1. This 
1. Is
1. An
1. 順序あり
1. リスト  


#### <a name="ordered-list-with-an-embedded-list"></a>埋め込みリストを含む番号付きリスト

1. Here
1. comes
1. 1 つ
1. embedded
    1. Miss Scarlett
    1. Professor Plum
1. ordered
1. リスト


### <a name="unordered-lists"></a>記号付きリスト

- This
- is
- a
- bulleted
- リスト


##### <a name="unordered-list-with-an-embedded-list"></a>埋め込みリストを含む記号付きリスト

- This 
- bulleted 
- リスト
    - Mrs. Peacock
    - Mr. Green
- 次の値を含む  
- その他
    1. Colonel Mustard
    1. Mrs. White
- 一覧


## <a name="horizontal-rule"></a>水平線

---

## <a name="tables"></a>[テーブル]

| [テーブル]        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| 列 3 は      | 右揃え | $1600 |
| 列 2 は      | 中央揃え      |   $12 |
| 列 1 は既定の | 左揃え     |    $1 |

[Markdown Table Generator ツール](http://www.tablesgenerator.com/markdown_tables)を使用して、より簡単にテーブルを作成できます。 

## <a name="code"></a>コード

コードを含める最善の方法は、実際に動作するサンプルからのスニペットを含める方法です。 [貢献に関するガイド](../CONTRIBUTING.md#contributing-to-samples)の指示に従って、サンプルを作成します。

包含の構文を使用して、コードを含めることができます。

```
[!code-csharp[<title>](<pathToFile>#<RegionName)]
```

上記の例は C# 構文を示していますが、その他の言語もサポートされています。
F# のサンプルでは `code-fsharp` を、Visual Basic のサンプルでは `code-vbnet` を使用します。
サポートされている他の言語は次のとおりです。
* C++: `code-cpp`
* HTML: `code-html`
* JavaScript: `code-javascript`
* Powershell: `code-ps`
* SQL: `code-sql`
* XML: `code-xml`



`<title>` に配置するテキストは、テキスト上でロールオーバーとして表示されます。 `<pathToFile>` はソース ファイルへのパスです。 `<RegionName>` には、ソース コード内の含める領域を指定する必要があります。 `#region` と `#endregion` のプリプロセッサ構文を使用して、含めるコードの領域を指定します。

領域が機能しない場合は、単一行のコメントで XML 要素名を使用してスニペットの開始と終了を指定できます。 たとえば、C# では次のように記述できます。

```csharp
// <CodeToInclude>
int j = 5;
int i ; 10;
int sum = i + j;
// </CodeToInclude>
```

他の言語では、その言語のコメント構文を使用します。
最後に、行番号を使用できます。`#L1-L10` では行 1 から 行 10 が含まれます。 行番号は非常に不安定であるため、お勧めしません。

完全なプログラムからのスニペットを含めることで、すべてのコードが確実に継続的インテグレーション (CI) システムで処理されたものになります。 ただし、コンパイル時のエラーやランタイム エラーの原因を表示する必要がある場合は、インライン コード ブロックを使用できます。

### <a name="inline-code-blocks-with-language-identifier"></a>言語識別子を持つインライン コード ブロック

3 つのバッククォート (\`\`\`) と言語 ID を使用して、言語固有のカラー コーディングをコード ブロックに適用します。 以下に [GFM 言語 ID](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs) のリスト全体を示します。

##### <a name="c9839"></a>C&#9839;

```c#
using System;
namespace HelloWorld
{
    class Hello 
    {
        static void Main() 
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```
#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```
#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>汎用のコード ブロック

汎用のコード ブロック コーディングには、3 つのバッククォート (&#96;&#96;&#96;) を使用します。   

> お勧めする方法は、前のセクションで説明したようにコード ブロックを言語識別子と併用して、ドキュメント サイトで構文が正しく強調表示されるようにすることです。 汎用のコード ブロックは、必要な場合にのみ使用します。

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

### <a name="inline-code"></a>インライン コード

`inline code` には、バッククォート (&#96;) を使用します。 コマンド ライン コマンド、データベース テーブルと列名、言語キーワードには、インラインコードを使用します。

## <a name="blockquotes"></a>ブロック引用

> 1000 万年続いた干ばつにより、とうに恐竜の天下は終わっていた。 いつかアフリカと呼ばれるであろう大陸の、ここ赤道上では、生存を賭けた戦いは激しさを増した新たなクライマックスを迎え、勝利者が誰になるのかまだ分からなかった。 不毛で乾燥したこの地では、小型か敏捷かどう猛でなければ、栄えることはおろか、生き残る希望さえ持てなかった。

## <a name="images"></a>イメージ

### <a name="static-image-or-animated-gif"></a>静的イメージまたはアニメーション GIF

![これは代替テキストです](../images/Logo_DotNet.png)

### <a name="linked-image"></a>リンク画像

[![リンク画像の代替テキスト](../images/Logo_DotNet.png)](https://dot.net) 

## <a name="videos"></a>ビデオ

### <a name="channel-9"></a>Channel 9

<iframe src="https://channel9.msdn.com/Shows/On-NET/Shipping-NET-Core-RC2--Tools-Preview-1/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/g2a4W6Q7aRw" frameborder="0" allowfullscreen></iframe>

## <a name="docsmicrosoft-extensions"></a>docs.microsoft 拡張機能

docs.microsoft により、GitHub Flavored Markdown にいくつかの拡張機能が追加されます。 

### <a name="alerts"></a>アラート

ドキュメント サイトに適切なスタイルで表示できるようにするため、次のアラート スタイルを使用することが重要です。 ただし、GitHub のレンダリング エンジンではこれらは区別されません。     

#### <a name="note"></a>メモ

> [!NOTE]
> これはメモです

#### <a name="warning"></a>警告

> [!WARNING]
> これは警告です

#### <a name="tip"></a>ヒント

> [!TIP]
> これはヒントです

#### <a name="important"></a>重要

> [!IMPORTANT]
> これは重要です

また、これらは次のように表示されます: ![アラート スタイル](../images/alerts.png)

### <a name="buttons"></a>ボタン

> [!div class="button"]
[ボタン リンク](../docs/core/index.md)

ボタンが実際に動作している例を、[Intune ドキュメント](https://docs.microsoft.com/intune/get-started/choose-how-to-enroll-devices)でご覧ください。 

### <a name="selectors"></a>セレクター

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Windows](../docs/core/tutorials/using-on-windows.md)

セレクターが実際に動作している例を、[Intune ドキュメント](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune#how-your-end-users-get-their-apps)でご覧ください。

### <a name="step-by-steps"></a>操作手順

>[!div class="step-by-step"]
[前へ](../docs/csharp/expression-trees-interpreting.md)
[次へ](../docs/csharp/expression-trees-translating.md)

操作手順が実際に動作している例を、[Advanced Threat Analytics のドキュメント](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/install-ata-step2)でご覧ください。
---
title: "チュートリアル: コード スニペットの実装 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# チュートリアル: コード スニペットの実装
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コード スニペットを作成し、エディター拡張機能に含める拡張機能のユーザーが独自のコードを追加できるようにできます。  
  
 コード スニペットでは、コードまたはその他のテキスト ファイルに組み込むことができるフラグメントを示します。 特定のプログラミング言語では、登録されているすべてのスニペットを表示する、 **ツール** \] メニューのをクリックして **コード スニペット マネージャー**します。 ファイルを右クリックして、スニペットを先にスニペットを挿入するクリックして **スニペットの挿入** または **ブロックの挿入**, 、スニペットを見つけて、ダブルクリックします。 スニペットの関連する部分を変更し、ENTER キーまたは esc キーを受け入れるには、タブまたは shift キーを押しながら TAB キーを押します。 詳細については、「[コード スニペット](../ide/code-snippets.md)」を参照してください。  
  
 コード スニペットは、.snippet ファイル名拡張子を持つ XML ファイルに含まれます。 コード スニペットは、ユーザーが検索してそれらを変更できるように、スニペットの挿入後に強調表示されているフィールドを含めることができます。 スニペット ファイルに関する情報も提供する、 **コード スニペット マネージャー** 正しいカテゴリにスニペット名を表示できるようにします。 スニペットのスキーマについては、次を参照してください。 [コード スニペット スキーマ リファレンス](../ide/code-snippets-schema-reference.md)します。  
  
 このチュートリアルでは、これらのタスクを実行する方法について説明します。  
  
1.  作成し、特定の言語のコード スニペットを登録します。  
  
2.  追加、 **スニペットの挿入** コマンドをショートカット メニューにします。  
  
3.  スニペットの拡張を実装します。  
  
 このチュートリアルに基づいて [チュートリアル: 候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)します。  
  
## 必須コンポーネント  
 このチュートリアルに従うと、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## 作成して、コード スニペットを登録します。  
 通常、コード スニペットは、登録されている言語サービスに関連付けられます。 ただし、実装する必要はありません、 <xref:Microsoft.VisualStudio.Package.LanguageService> コード スニペットを登録します。 代わりに、スニペットのインデックス ファイルの GUID を指定するだけとで同じ GUID を使用して、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> プロジェクトに追加します。  
  
 次の手順では、コード スニペットを作成し、特定の GUID に関連付ける方法を示します。  
  
1.  次のディレクトリ構造を作成します。  
  
     **%InstallDir%\\TestSnippets\\Snippets\\1033\\**  
  
     ここで *%installdir%* Visual Studio のインストール フォルダーです。 \(このパスは、コード スニペットがインストールに使用されることは通常がパスを指定できます、。\)  
  
2.  \\1033\\ フォルダーに .xml ファイルを作成し、名前を付けます **TestSnippets.xml**します。 \(この名前は、通常、スニペットのインデックス ファイルの使用が指定できます任意の名前 .xml ファイル名拡張子がある限り、。\) 次のテキストを追加するプレース ホルダーの GUID を削除して、独自に追加します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <SnippetCollection> <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}"> <SnippetDir> <OnOff>On</OnOff> <Installed>true</Installed> <Locale>1033</Locale> <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath> <LocalizedName>Snippets</LocalizedName> </SnippetDir> </Language> </SnippetCollection>  
    ```  
  
3.  スニペット フォルダーにファイルを作成、名前を付けます **テスト**`.snippet`, 、し、次のテキストを追加します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet"> <CodeSnippet Format="1.0.0"> <Header> <Title>Test replacement fields</Title> <Shortcut>test</Shortcut> <Description>Code snippet for testing replacement fields</Description> <Author>MSIT</Author> <SnippetTypes> <SnippetType>Expansion</SnippetType> </SnippetTypes> </Header> <Snippet> <Declarations> <Literal> <ID>param1</ID> <ToolTip>First field</ToolTip> <Default>first</Default> </Literal> <Literal> <ID>param2</ID> <ToolTip>Second field</ToolTip> <Default>second</Default> </Literal> </Declarations> <References> <Reference> <Assembly>System.Windows.Forms.dll</Assembly> </Reference> </References> <Code Language="TestSnippets"> <![CDATA[MessageBox.Show("$param1$"); MessageBox.Show("$param2$");]]> </Code> </Snippet> </CodeSnippet> </CodeSnippets>  
    ```  
  
 次の手順では、コード スニペットを登録する方法を示します。  
  
#### 特定の GUID のコード スニペットを登録する.  
  
1.  開いている、 **CompletionTest** プロジェクトです。 このプロジェクトを作成する方法については、次を参照してください。 [チュートリアル: 候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)します。  
  
2.  プロジェクトでは、次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   microsoft.msxml  
  
3.  プロジェクトの source.extension.vsixmanifest ファイルを開きます。  
  
4.  確認して、 **資産** \] タブには、 **VsPackage** コンテンツの種類とに **プロジェクト** プロジェクトの名前に設定されています。  
  
5.  CompletionTest プロジェクトを選択し、\[プロパティ\] ウィンドウで次のように設定します。 **Pkgdef ファイルの生成** に **true**します。 プロジェクトを保存します。  
  
6.  静的に追加 `SnippetUtilities` クラスをプロジェクトです。  
  
     [!code-cs[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  SnippetUtilities クラスでは、GUID を定義し、SnippetsIndex.xml ファイルで使用する値を指定します。  
  
     [!code-cs[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  追加、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> に、 `TestCompletionHandler` クラスです。 この属性は、プロジェクト内のパブリックまたは内部にある \(静的ではない\) クラスに追加できます。 \(追加する必要があります、 `using` Microsoft.VisualStudio.Shell 名前空間のステートメントです\)。  
  
     [!code-cs[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. プロジェクトをビルドして実行します。 プロジェクトの実行時に起動する Visual Studio の実験用インスタンスを登録したスニペットを表示するか、 **コード スニペット マネージャー** 下にある、 **TestSnippets** 言語です。  
  
## スニペットの挿入\] コマンドをショートカット メニューに追加します。  
 **スニペットの挿入** テキスト ファイルのショートカット メニューでコマンドが含まれていません。 そのため、コマンドを有効にする必要があります。  
  
#### ショートカット メニューに \[スニペットの挿入\] コマンドを追加するには  
  
1.  開いている、 `TestCompletionCommandHandler` クラス ファイルです。  
  
     このクラスが実装されているため <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, 、アクティブ化すること、 **スニペットの挿入** コマンドを <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドです。 コマンドを有効にする前に確認して、このメソッドがない呼び出されるオートメーション関数内ためと、 **スニペットの挿入** コマンドがクリックされると、スニペット ピッカーのユーザー インターフェイス \(UI\) が表示されます。  
  
     [!code-cs[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  プロジェクトをビルドして実行します。 実験用インスタンスで .zzz ファイル名拡張子を持つファイルを開きに任意の場所を右クリックします。**スニペットの挿入** コマンドは、ショートカット メニューに表示する必要があります。  
  
## スニペット ピッカー UI でスニペットの拡張を実装します。  
 このセクションでは、スニペット ピッカー UI が実行されるようにコード スニペットの展開を実装する方法を示しています。 場合に表示される **スニペットの挿入** 、ショートカット メニューをクリックします。 コード スニペットは、ユーザーでコード スニペットのショートカットの種類、タブを押したときにも拡張されます。  
  
 スニペット ピッカー UI を表示し、ナビゲーションと後の挿入スニペットの同意を有効にするを使用して、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドです。 挿入自体は、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> メソッドです。  
  
 コード スニペットの展開の実装はレガシ <xref:Microsoft.VisualStudio.TextManager.Interop> インターフェイスです。 レガシ コードを現在のエディターのクラスから変換するときは、従来のインターフェイスでは、行番号と列番号の組み合わせを使用して、テキスト バッファー内の場所を指定が、現在のクラスが 1 つのインデックスを使用することに注意してください。 そのため場合は、バッファーには、それぞれが 10 文字を持つ 3 つの行 \(および 1 文字としてカウントされる改行\)、3 番目の行の 4 番目の文字は、現在の実装の 27 の位置にあるが、2 行目は、以前の実装に 3 を配置します。  
  
#### スニペットの拡張を実装するには  
  
1.  含むファイルを `TestCompletionCommandHandler` クラスで、次の追加を `using` ステートメントです。  
  
     [!code-cs[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  作成、 `TestCompletionCommandHandler` クラスの実装、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> インターフェイスです。  
  
     [!code-cs[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  `TestCompletionCommandHandlerProvider` クラスで、インポート、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>です。  
  
     [!code-cs[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  コードの拡張インターフェイスの一部のプライベート フィールドを追加し、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。  
  
     [!code-cs[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  コンス トラクターで、 `TestCompletionCommandHandler` 、次のフィールドを設定します。  
  
     [!code-cs[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  ユーザーがクリックしたときに、スニペット ピッカーを表示する、 **スニペットの挿入** コマンドで、次のコードを追加、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドです。 \(この説明を読みやすくするには、ステートメント入力候補として使用されている Exec\(\) コードは表示されません。 既存のメソッドにコードのブロックを追加する代わりに、\)。 文字をチェックするコードの後に、次のコード ブロックを追加します。  
  
     [!code-cs[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  展開が明示的に受け入れられるまでに拡張セッションを開いているを保持スニペットに移動するフィールドがある場合は、セッションが閉じられ、として返されるフィールド、スニペットがない場合は、 `null` によって、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> メソッドです。<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッド、スニペット ピッカーの UI コードを前の手順で追加した後に次のコード スニペットのナビゲーションを処理する \(押したときにタブ区切りまたは shift キーを押しながら TAB スニペットの挿入後に\) を追加します。  
  
     [!code-cs[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  ユーザーが対応するショートカットの種類\] タブを押したときに、コード スニペットを挿入するコードを追加、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドです。 スニペットを挿入するプライベート メソッドは、後の手順で表示されます。 前の手順で追加したナビゲーション コードの後に、次のコードを追加します。  
  
     [!code-cs[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. メソッドの実装、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> インターフェイスです。 この実装で関心のある唯一の方法が <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>です。 その他のメソッドが返す必要がありますだけ <xref:Microsoft.VisualStudio.VSConstants.S_OK>します。  
  
     [!code-cs[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> メソッドを実装します。 実際には、その展開を挿入するヘルパー メソッドは、後の手順で説明します。<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> から入手できる行と列の情報を提供、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。  
  
     [!code-cs[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. 次のプライベート メソッドは、ショートカット、またはタイトルとパスに基づいて、コード スニペットを挿入します。 呼び出して、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> メソッドのコードにします。  
  
     [!code-cs[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## ビルドとテストのコード スニペットの展開  
 スニペットの拡張は、プロジェクトで機能するかどうかをテストすることができます。  
  
1.  ソリューションをビルドします。 デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
2.  テキスト ファイルを開き、テキストを入力します。  
  
3.  テキストのどこかを右クリックし、をクリックして **スニペットの挿入**します。  
  
4.  UI がというポップアップをと共に表示されます。 スニペット ピッカー **テスト置換フィールド**します。 ポップアップをダブルクリックします。  
  
     次のスニペットを挿入する必要があります。  
  
    ```  
    MessageBox.Show("first"); MessageBox.Show("second");  
    ```  
  
     ENTER キーまたは esc キーを押さないでください。  
  
5.  切り替えるには、タブと shift キーを押しながら TAB キーを押します「先頭」と「秒」の間です。  
  
6.  ENTER または esc キーを押して、カーソルをそのまま使用します。  
  
7.  テキストの部分によって異なる、"test"を入力し、TAB キーを押します。 "Test"がコード スニペットのショートカットであるため、もう一度、スニペットを挿入する必要があります。  
  
## 次の手順
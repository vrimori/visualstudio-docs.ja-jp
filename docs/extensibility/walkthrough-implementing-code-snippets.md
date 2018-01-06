---
title: "チュートリアル: コード スニペットの実装 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2a9ef9fcce1a02820b2855b6e39c5da2d3a7cc48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-implementing-code-snippets"></a>チュートリアル: コード スニペットの実装
コード スニペットを作成し、エディターの拡張機能に含める拡張機能のユーザーが独自のコードを追加できるようにできます。  
  
 コード スニペットは、コードまたはその他のファイルに組み込むことができるテキストの一部です。 特定のプログラミング言語では、登録されているすべてのスニペットを表示する、**ツール** メニューのをクリックして**コード スニペット マネージャー**です。 ファイルを右クリックして、スニペットを挿入する位置にスニペットを挿入するクリックして**スニペットの挿入**または**ブロックの挿入**スニペットを見つけて、ダブルクリックします。 スニペットの関連部分を変更し、ENTER キーまたは esc キーを受け入れるには、タブまたは shift キーを押しながら TAB キーを押します。 詳細については、「[Code Snippets](../ide/code-snippets.md)」を参照してください。  
  
 コード スニペットは、.snippet ファイル名拡張子を持つ XML ファイルに含まれます。 スニペットは、ユーザーが検索して、それらを変更できるように、スニペットの挿入後に強調表示されているフィールドを含めることができます。 スニペット ファイルに関する情報も提供する、**コード スニペット マネージャー**適切なカテゴリでスニペット名を表示できるようにします。 スニペットのスキーマについては、次を参照してください。[コード スニペット スキーマ リファレンス](../ide/code-snippets-schema-reference.md)です。  
  
 このチュートリアルでこれらのタスクを実行する方法について説明します。  
  
1.  作成し、特定の言語のコード スニペットを登録します。  
  
2.  追加、**スニペットの挿入**ショートカット メニューにコマンド。  
  
3.  スニペットの拡張を実装します。  
  
 このチュートリアルに基づいて[チュートリアル: ステートメント入力候補を表示する](../extensibility/walkthrough-displaying-statement-completion.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-and-registering-code-snippets"></a>作成して、コード スニペットを登録します。  
 通常、コード スニペットは、登録されている言語サービスに関連付けられます。 ただし、実装する必要はありません、<xref:Microsoft.VisualStudio.Package.LanguageService>コード スニペットを登録します。 代わりに、スニペット インデックス ファイルの GUID を指定するだけとで同じ GUID を使用して、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>プロジェクトに追加します。  
  
 次の手順では、コード スニペットを作成し、特定の GUID に関連付ける方法を示します。  
  
1.  次のディレクトリ構造を作成します。  
  
     **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
     ここで*%installdir%*は Visual Studio インストール フォルダーです。 (はこのパスは、コード スニペットをインストールする通常使用されますが、パスを指定できます、します。)  
  
2.  \1033\ フォルダーに .xml ファイルを作成し、名前**TestSnippets.xml**です。 (はこの名前は、インデックス ファイルのスニペット通常使用されますが、指定できます任意の名前、.xml ファイル名拡張子がある限り。)次のテキストを追加しプレース ホルダーの GUID を削除し、独自に追加します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <SnippetCollection>  
        <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
            <SnippetDir>  
                <OnOff>On</OnOff>  
                <Installed>true</Installed>  
                <Locale>1033</Locale>  
                <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
                <LocalizedName>Snippets</LocalizedName>  
            </SnippetDir>  
        </Language>  
    </SnippetCollection>  
    ```  
  
3.  スニペット フォルダーにファイルを作成、名前を付けます**テスト**`.snippet`、し、次のテキストを追加します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
        <CodeSnippet Format="1.0.0">  
            <Header>  
                <Title>Test replacement fields</Title>  
                <Shortcut>test</Shortcut>  
                <Description>Code snippet for testing replacement fields</Description>  
                <Author>MSIT</Author>  
                <SnippetTypes>  
                    <SnippetType>Expansion</SnippetType>  
                </SnippetTypes>  
            </Header>  
            <Snippet>  
                <Declarations>  
                    <Literal>  
                      <ID>param1</ID>  
                        <ToolTip>First field</ToolTip>  
                        <Default>first</Default>  
                    </Literal>  
                    <Literal>  
                        <ID>param2</ID>  
                        <ToolTip>Second field</ToolTip>  
                        <Default>second</Default>  
                    </Literal>  
                </Declarations>  
                <References>  
                   <Reference>  
                       <Assembly>System.Windows.Forms.dll</Assembly>  
                   </Reference>  
                </References>  
                <Code Language="TestSnippets">  
                    <![CDATA[MessageBox.Show("$param1$");  
         MessageBox.Show("$param2$");]]>  
                </Code>    
            </Snippet>  
        </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
 次の手順では、コード スニペットを登録する方法を示します。  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>特定の GUID のコード スニペットを登録するには  
  
1.  開く、 **CompletionTest**プロジェクト。 このプロジェクトを作成する方法については、次を参照してください。[チュートリアル: ステートメント入力候補を表示する](../extensibility/walkthrough-displaying-statement-completion.md)です。  
  
2.  プロジェクトでは、次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   microsoft.msxml  
  
3.  プロジェクトの source.extension.vsixmanifest ファイルを開きます。  
  
4.  確認して、**資産** タブには、 **VsPackage**コンテンツの種類とに**プロジェクト**プロジェクトの名前に設定されています。  
  
5.  CompletionTest プロジェクトを選択し、[プロパティ] ウィンドウで次のように設定します。 **Pkgdef ファイルの生成**に**true**です。 プロジェクトを保存します。  
  
6.  静的なを追加`SnippetUtilities`をプロジェクトにクラスです。  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  SnippetUtilities クラスでは、GUID を定義し、SnippetsIndex.xml ファイルで使用する値を付けます。  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  追加、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>を`TestCompletionHandler`クラスです。 この属性は、プロジェクト内のパブリックまたは内部にある (静的ではない) クラスに追加できます。 (追加する必要があります、 `using` Microsoft.VisualStudio.Shell 名前空間のステートメント)。  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. プロジェクトをビルドして実行します。 プロジェクトを実行時に起動する Visual Studio の実験用インスタンスを登録したスニペットを表示するか、**コード スニペット マネージャー**下にある、 **TestSnippets**言語です。  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>ショートカット メニューにスニペットの挿入 コマンドを追加します。  
 **スニペットの挿入**テキスト ファイルのショートカット メニューでコマンドが含まれていません。 そのため、コマンドを有効にする必要があります。  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>スニペットの挿入 コマンドのショートカット メニューを追加するには  
  
1.  開く、`TestCompletionCommandHandler`クラス ファイルです。  
  
     このクラスが実装されているため<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>、アクティブ化することができます、**スニペットの挿入**コマンドを<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドです。 コマンドを有効にする前に確認して、このメソッドが呼び出されていないオートメーション関数の内部ためと、**スニペットの挿入**コマンドをクリックして、スニペット ピッカーのユーザー インターフェイス (UI) が表示されます。  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  プロジェクトをビルドして実行します。 実験用インスタンスの .zzz ファイル名拡張子を持つファイルを開きで任意の場所を右クリックします。 **スニペットの挿入**コマンドがショートカット メニューに表示する必要があります。  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>スニペット ピッカー UI でスニペットの拡張を実装します。  
 このセクションでは、スニペット ピッカー UI が実行されるようにコード スニペットの展開を実装する方法を示しています。 ときに表示される**スニペットの挿入**、ショートカット メニューをクリックします。 コード スニペットは、ユーザーがコード スニペット ショートカットを入力し、タブを押してときにも拡張されます。  
  
 スニペット ピッカー UI を表示し、ナビゲーションと後の挿入スニペットの同意を有効にするを使用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッドです。 挿入自体はによって処理される、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>メソッドです。  
  
 コード スニペットの拡張の実装はレガシ<xref:Microsoft.VisualStudio.TextManager.Interop>インターフェイスです。 レガシ コードを現在のエディターのクラスから変換するときは、従来のインターフェイスでは、行番号と列番号の組み合わせを使用して、テキスト バッファー内の場所を指定が、現在のクラスが 1 つのインデックスを使用することに注意してください。 したがって場合、バッファーには、それぞれが 10 文字を持つ 3 つの行 (および 1 文字としてカウント改行文字)、3 番目の行の 4 番目の文字は、現在の実装で位置 27 は 2 行目は、以前の実装に 3 を置きます。  
  
#### <a name="to-implement-snippet-expansion"></a>スニペットの拡張を実装するには  
  
1.  含むファイルを`TestCompletionCommandHandler`クラス、次の追加`using`ステートメントです。  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  ように、`TestCompletionCommandHandler`クラスの実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>インターフェイスです。  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  `TestCompletionCommandHandlerProvider`クラス、インポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>です。  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  コードの拡張インターフェイスのプライベート フィールドをいくつか追加され、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  コンス トラクターで、`TestCompletionCommandHandler`クラスは、次のフィールドを設定します。  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  ユーザーがクリックしたときに、スニペット ピッカーを表示する、**スニペットの挿入**コマンドで、次のコードを追加、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッドです。 (この説明を読みやすくするためには、ステートメント入力候補として使用されている Exec() コードは表示されません。 代わりに、コードのブロックは、既存のメソッドに追加されます)文字をチェックするコードの後に、次のコード ブロックを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  展開が明示的に受け入れられるまでに、拡張セッションを開いているは保持スニペットに移動できるフィールドがある場合は、セッションが閉じられ、として返されるフィールドのスニペットがない場合は、`null`によって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A>メソッドです。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッド、スニペット ピッカー UI コードを前の手順で追加した後に (ときに、ユーザーは、スニペットの挿入後にタブまたは SHIFT キーを押しながら TAB キーを押す)、スニペットのナビゲーションを処理する次のコードを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  ユーザーが対応するショートカットの種類 タブを押したときに、コード スニペットを挿入するコードを追加、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッドです。 スニペットを挿入するプライベート メソッドは、後の手順で表示されます。 前の手順で追加したナビゲーション コードの後に、次のコードを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. メソッドの実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>インターフェイスです。 この実装では、関心のあるメソッドだけは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>です。 他のメソッドが返す必要がありますだけ<xref:Microsoft.VisualStudio.VSConstants.S_OK>です。  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> メソッドを実装します。 実際には、拡張を挿入するヘルパー メソッドは、後の手順で取り上げます。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>から取得できる行と列の情報を提供、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>です。  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. 次のプライベート メソッドでは、ショートカット、またはタイトルとパスに基づいて、コード スニペットを挿入します。 呼び出して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A>スニペットを持つメソッドです。  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>ビルドとコード スニペットの展開のテスト  
 スニペットの展開は、プロジェクトで機能するかどうかをテストすることができます。  
  
1.  ソリューションをビルドします。 デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
2.  テキスト ファイルを開くし、いくつかのテキストを入力します。  
  
3.  テキストの任意の場所を右クリックし、をクリックして**スニペットの挿入**です。  
  
4.  UI は、ことを示すポップアップで表示されます、スニペット ピッカー**テスト置換フィールド**です。 ポップアップをダブルクリックします。  
  
     次のスニペットを挿入する必要があります。  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     ENTER キーまたは esc キーを押さないでください。  
  
5.  切り替えるには、タブと shift キーを押しながら TAB キーを押して「先頭」と「秒」の間です。  
  
6.  か、ENTER キーまたは ESC を押して、カーソルをそのまま使用します。  
  
7.  テキストの部分によって異なる、"test"を入力し、TAB キーを押します。 "Test"が、コード スニペット ショートカットであるため、もう一度、スニペットの挿入する必要があります。  
  
## <a name="next-steps"></a>次の手順
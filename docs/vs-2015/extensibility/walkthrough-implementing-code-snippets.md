---
title: 'チュートリアル: コード スニペットの実装 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86d0ef82422b5f9cd419bf31e8b92b789fac1226
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547404"
---
# <a name="walkthrough-implementing-code-snippets"></a>チュートリアル: コード スニペットの実装
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[チュートリアル: コード スニペットを実装する](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-implementing-code-snippets)します。  
  
コード スニペットを作成し、拡張機能のユーザーが、独自のコードを追加できるようにエディター拡張機能に含めることができます。  
  
 コード スニペットは、コードまたはその他のファイルに組み込むことのできるテキストの一部です。 特定のプログラミング言語では、登録されているすべてのスニペットを表示する、**ツール** メニューのをクリックして**コード スニペット マネージャー**します。 スニペットは、先を右クリックして、ファイルのスニペットを挿入する次のようにクリックします。**スニペットの挿入**または**ブロックの挿入**、スニペットを見つけて、ダブルクリックします。 スニペットの関連する部分を変更し、そのまま使用するには、」と入力または esc キーを押しますのタブまたは shift キーを押しながら TAB キーを押します。 詳細については、「[Code Snippets](../ide/code-snippets.md)」を参照してください。  
  
 コード スニペットは、.snippet ファイル名拡張子を持つ XML ファイルに含まれています。 スニペットは、ユーザーが検索され、それらを変更できるように、スニペットの挿入後に強調表示されているフィールドを含めることができます。 スニペット ファイルの情報も提供する、**コード スニペット マネージャー**適切なカテゴリでスニペット名を表示できるようにします。 スニペットのスキーマについては、次を参照してください。[コード スニペット スキーマ リファレンス](../ide/code-snippets-schema-reference.md)します。  
  
 このチュートリアルでは、これらのタスクを実行する方法について説明します。  
  
1.  作成し、特定の言語のコード スニペットを登録します。  
  
2.  追加、**スニペットの挿入**ショートカット メニューにコマンド。  
  
3.  スニペットの展開を実装します。  
  
 このチュートリアルに基づいて[チュートリアル: 候補を表示する](../extensibility/walkthrough-displaying-statement-completion.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-and-registering-code-snippets"></a>作成して、コード スニペットを登録します。  
 通常、コード スニペットは、登録済みの言語サービスに関連付けられます。 ただし、実装する必要はありません、<xref:Microsoft.VisualStudio.Package.LanguageService>コード スニペットを登録します。 代わりに、スニペット インデックス ファイルの GUID を指定するだけですとで同じ GUID を使用して、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>プロジェクトに追加します。  
  
 次の手順では、コード スニペットを作成し、特定の GUID に関連付ける方法を示します。  
  
1.  次のディレクトリ構造を作成します。  
  
     **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
     場所 *%installdir%* は Visual Studio インストール フォルダーです。 (コード スニペットがインストールには、このパスは使用は、通常、パスを指定できます、します。)  
  
2.  \1033\ フォルダーには、.xml ファイルを作成し、名前**TestSnippets.xml**します。 (この名前は通常、スニペットのインデックス ファイルの使用を指定できます任意の名前、.xml ファイル名拡張子がある限り。)次のテキストを追加およびプレース ホルダーの GUID を削除して、独自に追加します。  
  
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
  
1.  開く、 **CompletionTest**プロジェクト。 このプロジェクトを作成する方法については、次を参照してください。[チュートリアル: 候補を表示する](../extensibility/walkthrough-displaying-statement-completion.md)します。  
  
2.  プロジェクトで、次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   microsoft.msxml  
  
3.  プロジェクトの source.extension.vsixmanifest ファイルを開きます。  
  
4.  確認します、**資産** タブには、 **VsPackage**コンテンツの種類とに**プロジェクト**プロジェクトの名前に設定されます。  
  
5.  CompletionTest プロジェクトを選択し、[プロパティ] ウィンドウで次のように設定します。 **Pkgdef ファイルの生成**に**true**します。 プロジェクトを保存します。  
  
6.  追加の静的な`SnippetUtilities`クラスをプロジェクト。  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7.  SnippetUtilities クラスでは、GUID を定義し、SnippetsIndex.xml ファイルで使用した値を付けます。  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8.  追加、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>を`TestCompletionHandler`クラス。 この属性は、プロジェクト内のパブリックまたは内部にある (静的ではない) クラスに追加できます。 (追加する必要があります、 `using` Microsoft.VisualStudio.Shell 名前空間のステートメント)。  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. プロジェクトをビルドして実行します。 プロジェクトの実行時に起動する Visual Studio の実験用インスタンスを登録したスニペットを表示するか、**コード スニペット マネージャー**下、 **TestSnippets**言語。  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>スニペットの挿入 コマンドをショートカット メニューに追加します。  
 **スニペットの挿入**テキスト ファイルのショートカット メニューでコマンドが含まれていません。 そのため、コマンドを有効にする必要があります。  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>スニペットの挿入コマンドのショートカット メニューを追加するには  
  
1.  開く、`TestCompletionCommandHandler`クラス ファイル。  
  
     このクラスを実装するため、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>、アクティブ化することができます、**スニペットの挿入**コマンド、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッド。 コマンドを有効にする前に確認して、このメソッドが呼び出されていない automation 関数の内側ためと、**スニペットの挿入**コマンドがクリックされると、スニペット ピッカーのユーザー インターフェイス (UI) が表示されます。  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2.  プロジェクトをビルドして実行します。 実験用インスタンスの .zzz ファイル名拡張子を持つファイルを開きで任意の場所を右クリックします。 **スニペットの挿入**ショートカット メニューに表示する必要があります。  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>スニペット ピッカー UI でスニペットの展開を実装します。  
 このセクションでは、スニペット ピッカー UI が実行されるようにコード スニペットの展開を実装する方法を示しています。 ときに表示される**スニペットの挿入**、ショートカット メニューをクリックします。 コード スニペットは、ユーザーが型のコード スニペットのショートカットとキーを押す タブにも拡張されます。  
  
 スニペット ピッカー UI を表示し、ナビゲーションと後の挿入スニペットの受け入れを有効にするには、使用、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッド。 によって挿入自体が処理される、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>メソッド。  
  
 コード スニペット拡張の実装はレガシ<xref:Microsoft.VisualStudio.TextManager.Interop>インターフェイス。 レガシ コードを現在のエディター クラスから変換するときは、従来のインターフェイスを行番号と列番号の組み合わせを使用して、テキスト バッファーに場所を指定するが、現在のクラスを使用して、1 つのインデックスに注意してください。 そのため、バッファーがそれぞれが 10 文字を持つ 3 つの行 (および、改行は、1 文字としてカウントされます)、3 番目の行の 4 番目の文字が現在の実装では 27 の位置が、2 行目は、以前の実装に 3 を配置します。  
  
#### <a name="to-implement-snippet-expansion"></a>スニペットの展開を実装するには  
  
1.  含むファイルを`TestCompletionCommandHandler`クラスで、次の追加`using`ステートメント。  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2.  ように、`TestCompletionCommandHandler`クラスの実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>インターフェイス。  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3.  `TestCompletionCommandHandlerProvider`クラスは、インポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>します。  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4.  コードの拡張インターフェイスのいくつかのプライベート フィールドを追加し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>します。  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5.  コンス トラクター、`TestCompletionCommandHandler`クラスで、次のフィールドを設定します。  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6.  ユーザーがクリックしたときに、スニペット ピッカーを表示する、**スニペットの挿入**コマンドで、次のコードを追加、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッド。 (Exec() コード ステートメント入力候補に使用されるこの説明を読みやすくするためにこの変更は表示されません。 代わりに、コードのブロックが、既存のメソッドを追加します)。文字をチェックするコードの後に、次のコード ブロックを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7.  展開が明示的に受け入れられるまで、スニペットに移動できるフィールドがある場合は、拡張セッションが開いたままです。セッションが閉じられ、として返されるフィールドのスニペットがない場合は、`null`によって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A>メソッド。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッド、スニペット ピッカー UI コードを前の手順で追加した後に (ユーザーは、スニペットの挿入後にタブまたは SHIFT キーを押しながら TAB キーを押した) ときに、スニペットのナビゲーションを処理するために次のコードを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8.  ユーザーは、対応するショートカットの型し、タブ キーを押すときに、コード スニペットを挿入するにするコードを追加、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッド。 スニペットを挿入するプライベート メソッドは、後の手順で表示されます。 前の手順で追加したナビゲーション コードの後に、次のコードを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. メソッドの実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>インターフェイス。 関心のある唯一のメソッドは、この実装で<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>します。 その他のメソッドが返す必要がありますのみ<xref:Microsoft.VisualStudio.VSConstants.S_OK>します。  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> メソッドを実装します。 実際には、拡張を挿入するヘルパー メソッドは、後の手順で説明します。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>から取得できる行と列の情報を提供します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>します。  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. 次のプライベート メソッドは、ショートカット、またはタイトルとパスに基づいて、コード スニペットを挿入します。 呼び出して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A>メソッドは、スニペットを使用します。  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>ビルドとテストのコード スニペットの展開  
 スニペットの展開は、プロジェクトで機能するかどうかをテストすることができます。  
  
1.  ソリューションをビルドします。 デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
2.  テキスト ファイルを開き、いくつかのテキストを入力します。  
  
3.  テキストのどこかを右クリックし、クリックして**スニペットの挿入**します。  
  
4.  示すポップアップを使用した UI が表示されます、スニペット ピッカー**テスト置換フィールド**します。 ポップアップをダブルクリックします。  
  
     次のスニペットを挿入する必要があります。  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     ENTER キーまたは esc キーを押さないでください。  
  
5.  切り替えるには、タブと shift キーを押しながら TAB キーを押します"first"と「秒」の間。  
  
6.  ENTER または esc キーを押して、カーソルをそのまま使用します。  
  
7.  テキストの部分によって異なる、"test"を入力し、し、TAB キーを押します。 "Test"は、コード スニペットのショートカットであるため、スニペットを再び挿入する必要があります。  
  
## <a name="next-steps"></a>次の手順


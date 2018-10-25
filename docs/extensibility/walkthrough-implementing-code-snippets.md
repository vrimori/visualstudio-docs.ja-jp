---
title: 'チュートリアル: コード スニペットの実装 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bd4a22dc63f0304cc8afa98e35c5f7afd6cac011
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921994"
---
# <a name="walkthrough-implement-code-snippets"></a>チュートリアル: 実装のコード スニペット
コード スニペットを作成し、拡張機能のユーザーが、独自のコードを追加できるようにエディター拡張機能に含めることができます。  
  
 コード スニペットは、コードまたはその他のファイルに組み込むことのできるテキストの一部です。 特定のプログラミング言語では、登録されているすべてのスニペットを表示する、**ツール** メニューのをクリックして**コード スニペット マネージャー**します。 スニペットは、先を右クリックして、ファイルのスニペットを挿入するスニペットの挿入 をクリックしてまたは**ブロックの挿入**スニペットを見つけて、ダブルクリックします。 キーを押します**タブ**または**Shift**+**タブ**スニペットの関連する部分を変更し、キーを押します **」と入力**または**Esc**をそのまま使用します。 詳細については、次を参照してください。[コード スニペット](../ide/code-snippets.md)します。  
  
 コード スニペットは、.snippet * ファイル名拡張子を持つ XML ファイルに含まれています。 スニペットは、ユーザーが検索され、それらを変更できるように、スニペットの挿入後に強調表示されているフィールドを含めることができます。 スニペット ファイルの情報も提供する、**コード スニペット マネージャー**適切なカテゴリでスニペット名を表示できるようにします。 スニペットのスキーマについては、次を参照してください。[コード スニペット スキーマ リファレンス](../ide/code-snippets-schema-reference.md)します。  
  
 このチュートリアルでは、これらのタスクを実行する方法について説明します。  
  
1. 作成し、特定の言語のコード スニペットを登録します。  
  
2. 追加、**スニペットの挿入**ショートカット メニューにコマンド。  
  
3. スニペットの展開を実装します。  
  
   このチュートリアルに基づいて[チュートリアル: ステートメント入力候補を表示](../extensibility/walkthrough-displaying-statement-completion.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="create-and-register-code-snippets"></a>作成し、コード スニペットの登録  
 通常、コード スニペットは、登録済みの言語サービスに関連付けられます。 ただし、実装する必要はありません、<xref:Microsoft.VisualStudio.Package.LanguageService>コード スニペットを登録します。 代わりに、スニペット インデックス ファイルの GUID を指定するだけですとで同じ GUID を使用して、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>プロジェクトに追加します。  
  
 次の手順では、コード スニペットを作成し、特定の GUID に関連付ける方法を示します。  
  
1. 次のディレクトリ構造を作成します。  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    場所 *%installdir%* は Visual Studio インストール フォルダーです。 (コード スニペットがインストールには、このパスは使用は、通常、パスを指定できます、します。)  
  
2. \1033\ フォルダー内に作成、 *.xml*ファイルし、名前を付けます**TestSnippets.xml**します。 (がある限り、任意の名前を指定できますが、この名前は通常、スニペットのインデックス ファイルの使用、 *.xml*ファイル名拡張子)。次のテキストを追加およびプレース ホルダーの GUID を削除して、独自に追加します。  
  
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
  
3. スニペット フォルダーにファイルを作成、名前を付けます**テスト**`.snippet`、し、次のテキストを追加します。  
  
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
  
### <a name="to-register-code-snippets-for-a-specific-guid"></a>特定の GUID のコード スニペットを登録するには  
  
1.  開く、 **CompletionTest**プロジェクト。 このプロジェクトを作成する方法については、次を参照してください。[チュートリアル: ステートメント入力候補を表示](../extensibility/walkthrough-displaying-statement-completion.md)します。  
  
2.  プロジェクトで、次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   microsoft.msxml  
  
3.  プロジェクトで、開く、 **source.extension.vsixmanifest**ファイル。  
  
4.  確認します、**資産** タブには、 **VsPackage**コンテンツの種類とに**プロジェクト**プロジェクトの名前に設定されます。  
  
5.  CompletionTest プロジェクトを選択し、[プロパティ] ウィンドウで次のように設定します。 **Pkgdef ファイルの生成**に**true**します。 プロジェクトを保存します。  
  
6.  追加の静的な`SnippetUtilities`クラスをプロジェクト。  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  SnippetUtilities クラスの GUID を定義しで使用される値を指定する、 *SnippetsIndex.xml*ファイル。  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  追加、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>を`TestCompletionHandler`クラス。 この属性は、プロジェクト内のパブリックまたは内部にある (静的ではない) クラスに追加できます。 (追加する必要があります、 `using` Microsoft.VisualStudio.Shell 名前空間のステートメント)。  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. プロジェクトをビルドして実行します。 プロジェクトの実行時に起動する Visual Studio の実験用インスタンスを登録したスニペットを表示するか、**コード スニペット マネージャー**下、 **TestSnippets**言語。  
  
## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>ショートカット メニューに スニペットの挿入コマンドを追加します。  
 **スニペットの挿入**テキスト ファイルのショートカット メニューでコマンドが含まれていません。 そのため、コマンドを有効にする必要があります。  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>スニペットの挿入コマンドのショートカット メニューを追加するには  
  
1.  開く、`TestCompletionCommandHandler`クラス ファイル。  
  
     このクラスを実装するため、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>、アクティブ化することができます、**スニペットの挿入**コマンド、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッド。 コマンドを有効にする前に確認して、このメソッドが呼び出されていない automation 関数の内側ためと、**スニペットの挿入**コマンドがクリックされると、スニペット ピッカーのユーザー インターフェイス (UI) が表示されます。  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  プロジェクトをビルドして実行します。 実験用のインスタンスを持つファイルを開く、 *.zzz*ファイル名拡張子とでは、任意の場所を右クリックします。 **スニペットの挿入**ショートカット メニューに表示する必要があります。  
  
## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>スニペット ピッカーの UI でスニペットの展開を実装します。  
 このセクションでは、スニペット ピッカー UI が実行されるようにコード スニペットの展開を実装する方法を示しています。 ときに表示される**スニペットの挿入**、ショートカット メニューをクリックします。 ユーザーのコード スニペットのショートカットを入力してキーを押すと、コード スニペットが展開されても**タブ**します。  
  
 スニペット ピッカー UI を表示し、ナビゲーションと後の挿入スニペットの受け入れを有効にするには、使用、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッド。 によって挿入自体が処理される、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>メソッド。  
  
 コード スニペット拡張の実装はレガシ<xref:Microsoft.VisualStudio.TextManager.Interop>インターフェイス。 レガシ コードを現在のエディター クラスから変換するときは、従来のインターフェイスを行番号と列番号の組み合わせを使用して、テキスト バッファーに場所を指定するが、現在のクラスを使用して、1 つのインデックスに注意してください。 そのため、バッファーがそれぞれが 10 文字を持つ 3 つの行 (および、改行は、1 つの文字としてカウントされます)、3 番目の行の 4 番目の文字が現在の実装では 27 の位置が、2 行目は、以前の実装に 3 を配置します。  
  
#### <a name="to-implement-snippet-expansion"></a>スニペットの展開を実装するには  
  
1.  含むファイルを`TestCompletionCommandHandler`クラスで、次の追加`using`ステートメント。  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  ように、`TestCompletionCommandHandler`クラスの実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>インターフェイス。  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  `TestCompletionCommandHandlerProvider`クラスは、インポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>します。  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  コードの拡張インターフェイスのいくつかのプライベート フィールドを追加し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>します。  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  コンス トラクター、`TestCompletionCommandHandler`クラスで、次のフィールドを設定します。  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  ユーザーがクリックしたときに、スニペット ピッカーを表示する、**スニペットの挿入**コマンドで、次のコードを追加、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッド。 (この説明を読みやすくする、`Exec()`ステートメント入力候補に対して使用されるコードが示されていません代わりに、コードのブロックが、既存のメソッドを追加します。)。文字をチェックするコードの後に、次のコード ブロックを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  展開が明示的に受け入れられるまで、スニペットに移動できるフィールドがある場合は、拡張セッションが開いたままです。セッションが閉じられ、として返されるフィールドのスニペットがない場合は、`null`によって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A>メソッド。 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッドのスニペット ピッカー UI コードを前の手順で追加した後に、スニペットのナビゲーションを処理するために次のコードを追加 (ユーザーが押したとき**タブ**または**Shift** +**タブ**スニペットの挿入後)。  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  ユーザーが対応するショートカットを入力して、キーを押すと、コード スニペットを挿入する**タブ**、コードを追加して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッド。 スニペットを挿入するプライベート メソッドは、後の手順で表示されます。 前の手順で追加したナビゲーション コードの後に、次のコードを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. メソッドの実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>インターフェイス。 関心のある唯一のメソッドは、この実装で<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>します。 その他のメソッドが返す必要がありますのみ<xref:Microsoft.VisualStudio.VSConstants.S_OK>します。  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> メソッドを実装します。 実際には、拡張を挿入するヘルパー メソッドは、後の手順について説明します。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>から取得できる行と列の情報を提供します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>します。  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. 次のプライベート メソッドは、ショートカット、またはタイトルとパスに基づいて、コード スニペットを挿入します。 呼び出して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A>メソッドは、スニペットを使用します。  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="build-and-test-code-snippet-expansion"></a>ビルドし、テストのコード スニペットの展開  
 スニペットの展開は、プロジェクトで機能するかどうかをテストすることができます。  
  
1.  ソリューションをビルドします。 デバッガーでこのプロジェクトを実行する場合は、Visual Studio の 2 番目のインスタンスが開始します。  
  
2.  テキスト ファイルを開き、いくつかのテキストを入力します。  
  
3.  テキストのどこかを右クリックし、クリックして**スニペットの挿入**します。  
  
4.  示すポップアップを使用した UI が表示されます、スニペット ピッカー**テスト置換フィールド**します。 ポップアップをダブルクリックします。  
  
     次のスニペットを挿入する必要があります。  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     キーを押さない**Enter**または**Esc**します。  
  
5.  キーを押して**タブ**と**shift キーを押し**+**タブ**"first"と「秒」の間で切り替えをします。  
  
6.  押すことによって、カーソルをそのまま使用**Enter**または**Esc**します。  
  
7.  テキストの部分によって異なる、"test"を入力し、キーを押します**タブ**します。"Test"は、コード スニペットのショートカットであるため、スニペットを再び挿入する必要があります。  
  
## <a name="next-steps"></a>次の手順
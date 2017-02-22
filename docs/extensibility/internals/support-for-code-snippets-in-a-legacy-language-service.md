---
title: "従来の言語サービスでのコード スニペットのサポート | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スニペットの言語サービスでのサポート"
  - "言語サービス [マネージ パッケージ フレームワーク] でサポートする、コード スニペット"
  - "コード スニペットをサポートする言語サービス [マネージ パッケージ framework]"
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスでのコード スニペットのサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コード スニペットは、ソース ファイルに挿入するコードの一部です。 自体は、一連のフィールドの XML ベースのテンプレートです。 これらのフィールドには、スニペットが挿入され、スニペットを挿入するコンテキストに応じて異なる値を持つことができますが強調表示されます。 スニペットの挿入後にすぐに、言語サービスは、スニペットを書式設定できます。  
  
 TAB キーを使用して、移動できない場合にスニペットのフィールドを許可する特別な編集モードでは、スニペットの挿入します。 フィールドには、IntelliSense スタイルのドロップダウン メニューをサポートできます。 ユーザーは、入力、または ESC キーを入力して、ソース ファイルにスニペットをコミットします。 スニペットの詳細については、次を参照してください [コード スニペット](../../ide/code-snippets.md)します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 詳細については、次を参照してください。 [チュートリアル: コード スニペットの実装](../../extensibility/walkthrough-implementing-code-snippets.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## マネージ コード スニペットのパッケージ フレームワークのサポート  
 特別なを有効にすると編集モードをマネージ パッケージ フレームワーク \(MPF\) は、スニペットを挿入するテンプレートを読み取る、スニペットのほとんどの機能をサポートします。 サポートを管理、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> クラスです。  
  
 ときに、 <xref:Microsoft.VisualStudio.Package.Source> クラスをインスタンス化、 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> メソッドで、 <xref:Microsoft.VisualStudio.Package.LanguageService> クラスを呼び出して取得、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> オブジェクト \(ことに注意してください、ベース <xref:Microsoft.VisualStudio.Package.LanguageService> クラスは常に新しいを返します <xref:Microsoft.VisualStudio.Package.ExpansionProvider> オブジェクトごとに <xref:Microsoft.VisualStudio.Package.Source> オブジェクト\)。  
  
 MPF は拡張機能をサポートしていません。 拡張関数では、スニペット テンプレートに埋め込まれている、フィールドに格納される 1 つ以上の値を返す名前付き関数です。 言語によって、値を返すサービス自体から、 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> オブジェクトです。<xref:Microsoft.VisualStudio.Package.ExpansionFunction> オブジェクトは、拡張機能をサポートする言語サービスによって実装する必要があります。  
  
## コード スニペットのサポートを提供します。  
 コード スニペットのサポートを有効にするには、提供か、スニペットがインストールする必要があり、ユーザーはそのスニペットを挿入するための手段を提供する必要があります。 コード スニペットのサポートを有効にする 3 つのステップがあります。  
  
1.  スニペット ファイルをインストールします。  
  
2.  言語サービスのコード スニペットを有効にします。  
  
3.  呼び出す、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> オブジェクトです。  
  
### スニペット ファイルをインストールします。  
 言語のすべてのスニペットは、ファイルごとに 1 つスニペット テンプレート通常を XML ファイルのテンプレートとして保存されます。 コード スニペット テンプレート用に使用する XML スキーマの詳細については、「 [コード スニペット スキーマ リファレンス](../../ide/code-snippets-schema-reference.md)します。 各スニペット テンプレートは、言語 ID を持つ識別します。 この言語 ID は、レジストリで指定に、 `Language` テンプレート内の \< コード \> タグの属性です。  
  
 通常は、スニペット テンプレート ファイルが格納されている 2 つの場所: 1\) の言語がインストールされていると、ユーザーのフォルダーに 2\)。 これらの場所がレジストリに追加ようにする Visual Studio **コード スニペット マネージャー** 、スニペットを見つけることができます。 ユーザーのフォルダーには、ユーザーによって作成されたスニペットを格納します。  
  
 次のようにインストールされているスニペット テンプレート ファイルのフォルダーの一般的なレイアウト: *\[として「installroot」\]*\\*\[TestLanguage\]*\\Snippets\\*\[LCID\]*\\Snippets します。  
  
 *\[として「installroot」\]* で使用する言語がインストールされているフォルダーです。  
  
 *\[TestLanguage\]* フォルダー名として使用する言語の名前を指定します。  
  
 *\[LCID\]* ロケール ID です。 これは、スニペットのどのローカライズ版は格納されます。 たとえば、1033 の場合は、英語版のロケール ID をので *\[LCID\]* 1033年は置き換えられます。  
  
 ある追加のファイルを渡す必要があることをお SnippetsIndex.xml または ExpansionsIndex.xml \(.xml で終わる有効なファイル名を使用することができます\) と通常呼ばれる、インデックス ファイルです。 このファイルは通常に格納されている、 *\[として「installroot」\]*\\*\[TestLanguage\]* フォルダー snippets フォルダーだけでなく、言語 ID の正確な場所と、スニペットを使用する言語サービス GUID を指定します。 インデックス ファイルの正確なパスは、「のレジストリ エントリをインストールする」で後述するように、レジストリに格納されます。 SnippetsIndex.xml ファイルの例を次に示します。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 \< 言語 \> タグは、言語 ID を指定 \(、 `Lang` 属性\) と言語サービスの GUID。  
  
 この例では、Visual Studio インストール フォルダーに、言語サービスをインストールするいると仮定します。 LCID % は、ユーザーの現在のロケール ID に置き換えられます 複数の \< SnippetDir \> タグを追加できます、別のディレクトリおよびロケールごとに 1 つ。 さらに、スニペット フォルダーには、\< SnippetDir \> タグに埋め込まれている \< SnippetSubDir \> タグを持つインデックス ファイルで識別されるそれぞれのサブフォルダーを含めることができます。  
  
 ユーザーは、言語の独自のスニペットを作成できます。 たとえば、ユーザーの設定\] フォルダーに格納するは通常これら *\[TestDocs\]*\\Code Snippets\\*\[TestLanguage\]*\\Test コード スニペット、 *\[TestDocs\]* Visual Studio のユーザーの設定\] フォルダーの場所は、です。  
  
 次の置換要素は、インデックス ファイルの \< か、指定 \> タグに格納されたパスに配置することができます。  
  
|要素|説明|  
|--------|--------|  
|LCID %|ロケール id。|  
|% として「installroot」|たとえば、C:\\Program 個の \\microsoft Visual Studio の 8、Visual Studio のルート インストール フォルダーです。|  
|ProjDir %|現在のプロジェクトを含むフォルダー。|  
|ProjItem %|現在のプロジェクト項目を含むフォルダー。|  
|TestDocs %|ユーザーの設定\] フォルダー、たとえば、C:\\Documents and settings \\ フォルダー*\[username\]*\\My Documents\\Visual Studio\\8 します。|  
  
### 言語サービスのコード スニペットを有効にします。  
 追加することで、言語サービスのコード スニペットを有効にしたことができます、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 属性、VSPackage を \(を参照してください [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md) 詳細\)。<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> と <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> パラメーターは省略可能で、含める必要がありますが、 `SearchPaths` 名前付きパラメーターを通知するために、 **コード スニペット マネージャー** 、スニペットの場所。  
  
 この属性を使用する方法の例を次に示します。  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### 拡張プロバイダーの呼び出し  
 言語サービスは、カーソルが呼び出される方法と同様にすべてのコード スニペットの挿入を制御します。  
  
## コード スニペットの拡張プロバイダーの呼び出し  
 拡張プロバイダーを呼び出す方法の 2 つの方法があります: メニュー コマンドを使用するか、コンプリート リストからショートカットを使用しています。  
  
### メニュー コマンドを使用して、コード スニペットの挿入  
 スニペットのブラウザーを表示するメニュー コマンドを使用するメニュー コマンドを追加しを呼び出す、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> メソッドに、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> インターフェイス メニュー コマンドに応答します。  
  
1.  .Vsct ファイルをコマンドとボタンを追加します。 そのために行うための手順を参照して [チュートリアル: Visual Studio パッケージ テンプレートを使用してメニュー コマンドを作成する](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)します。  
  
2.  クラスを派生、 <xref:Microsoft.VisualStudio.Package.ViewFilter> クラスさせ、 <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> メソッドを新しいメニュー コマンドのサポートを示します。 この例には、メニュー コマンドが常に有効にします。  
  
    ```c#  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  オーバーライド、 <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> メソッドで、 <xref:Microsoft.VisualStudio.Package.ViewFilter> を取得するクラス、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> オブジェクトと呼び出し、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> そのオブジェクトでメソッドです。  
  
    ```c#  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     以下の方法で、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> のスニペットを挿入するプロセス中に特定の順序での \[Visual Studio によって、クラスが呼び出されます。  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     後に、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> メソッドが呼び出されると、スニペットが挿入された、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> オブジェクトが挿入された直後のスニペットを変更するために使用される特殊な編集モードにします。  
  
### ショートカットを使用してコード スニペットの挿入  
 コンプリート リストからショートカットの実装は、メニュー コマンドを実装するよりも複雑です。 まず、IntelliSense の単語の入力候補一覧にスニペットのショートカットを追加する必要があります。 スニペット ショートカット名を入力候補の結果として挿入されているときを検出する必要があります。 最後に、スニペットのタイトルとショートカット名を使用して、パスを取得してその情報を渡す、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> メソッドを <xref:Microsoft.VisualStudio.Package.ExpansionProvider> メソッドです。  
  
 単語の入力候補リストにスニペットのショートカットを追加するを追加、 <xref:Microsoft.VisualStudio.Package.Declarations> 内のオブジェクト、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> クラスです。 スニペット名としてのショートカット キーを確認することを確認する必要があります。 例については、「[チュートリアル: インストールされているコード スニペット \(従来の実装\) の一覧を取得します。](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)」を参照してください。  
  
 内のコード スニペットのショートカットのカーソルを検出する、 <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> のメソッド、 <xref:Microsoft.VisualStudio.Package.Declarations> クラスです。 ソース ファイルに、スニペット名は既に挿入されて、ため、拡張が挿入されたときに削除してください。<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> メソッドは、スニペットの挿入ポイントを説明する範囲を受け取ります。 範囲には、ソース ファイルの全体のスニペット名が含まれているその名前が、スニペットに置き換えられます。  
  
 バージョンをここでは、 <xref:Microsoft.VisualStudio.Package.Declarations> ショートカット名を指定したスニペットの挿入を処理するクラスです。 他の方法で、 <xref:Microsoft.VisualStudio.Package.Declarations> クラスは、わかりやすくするために省略されています。 このクラスのコンス トラクターは、メモ、 <xref:Microsoft.VisualStudio.Package.LanguageService> オブジェクトです。 これは、バージョンからに渡すことが、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> オブジェクト \(の実装など、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> クラスがかかる場合があります、 <xref:Microsoft.VisualStudio.Package.LanguageService> コンス トラクター内のオブジェクトし、そのオブジェクトに渡す、 `TestDeclarations` クラスのコンス トラクター\)。  
  
```  
[C#]  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 呼び出す言語サービス ショートカット名を取得すると、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> ファイル名とコード スニペットのタイトルを取得します。 言語サービス、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> メソッドで、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> コード スニペットを挿入するクラス。 次のメソッドで特定の順序で Visual Studio によって呼び出されます、 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> プロセス中に、スニペットを挿入するクラス。  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 言語サービスのインストール済みのコード スニペットの一覧の取得の詳細については、次を参照してください。 [チュートリアル: インストールされているコード スニペット \(従来の実装\) の一覧を取得します。](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)します。  
  
## ExpansionFunction クラスを実装します。  
 拡張関数では、スニペット テンプレートに埋め込まれている、フィールドに格納される 1 つ以上の値を返す名前付き関数です。 言語サービスで拡張機能をサポートするためには派生クラスを <xref:Microsoft.VisualStudio.Package.ExpansionFunction> クラスし、実装、 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> メソッドです。 オーバーライドする必要がありますし、 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> メソッドに、 <xref:Microsoft.VisualStudio.Package.LanguageService> のバージョンの新しいインスタンスを返すために、 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 各拡張機能をサポートするためのクラスです。 またをオーバーライドする必要がある拡張機能を使用できる値のリストをサポートする場合、 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> メソッドに、 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> クラスをそれらの値の一覧を返します。  
  
 引数を受け取るか、その他のフィールドにアクセスする必要がある拡張機能は必要がありますように拡張プロバイダーは、拡張関数が呼び出された時点では完全に初期化しないされる可能性があります編集可能なフィールドに関連付けできません。 その結果、拡張機能は、引数またはその他のフィールドの値を取得できません。  
  
### 例  
 シンプルな拡張関数を呼び出す方法の例を次に示します `GetName` が実装されています。 この拡張機能に番号が追加基底クラス名の拡張関数がインスタンス化されるたびに \(これに相当するたびに関連付けられているコード スニペットが挿入されます\)。  
  
```c#  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## 参照  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [コード スニペット](../../ide/code-snippets.md)   
 [チュートリアル: インストールされているコード スニペット \(従来の実装\) の一覧を取得します。](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
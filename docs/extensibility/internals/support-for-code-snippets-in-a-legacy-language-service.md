---
title: "従来の言語サービスでのコード スニペットのサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6102a5bb6298cd6403285e3d36842424b0be3412
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>従来の言語サービスでのコード スニペットのサポート
コード スニペットは、ソース ファイルに挿入するコードの一部です。 自体は、一連のフィールドに XML ベースのテンプレートです。 これらのフィールドは、スニペットが挿入され、スニペットを挿入するコンテキストに応じて異なる値を持つことができますに強調表示されます。 スニペットの挿入後にすぐに、言語サービスは、スニペットを書式設定できます。  
  
 TAB キーを使用して、移動できない場合に、スニペットのフィールドを許可する特別な編集モードでは、スニペットの挿入します。 フィールドには、IntelliSense スタイルのドロップダウン メニューをサポートできます。 ユーザーは、入力、または ESC キーを入力してソース ファイルにスニペットをコミットします。 スニペットの詳細については、次を参照してください[コード スニペット](../../ide/code-snippets.md)です。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 詳細については、次を参照してください。[チュートリアル: コード スニペットを実装する](../../extensibility/walkthrough-implementing-code-snippets.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>マネージ パッケージ フレームワークのサポートのコード スニペット  
 Managed package framework (MPF) は、スニペットを挿入するテンプレートを読み取る、ほとんどのスニペット機能をサポートし、編集モードの特別なを有効にします。 サポートを使って管理、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>クラスです。  
  
 ときに、<xref:Microsoft.VisualStudio.Package.Source>クラスをインスタンス化、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスを呼び出して取得、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>オブジェクト (ことに注意してください、ベース<xref:Microsoft.VisualStudio.Package.LanguageService>クラスは常に、新しいを返します<xref:Microsoft.VisualStudio.Package.ExpansionProvider>ごとにオブジェクト<xref:Microsoft.VisualStudio.Package.Source>オブジェクトの場合)。  
  
 MPF は、拡張機能をサポートしていません。 拡張関数は、スニペット テンプレートに埋め込まれているし、フィールドに格納される 1 つ以上の値を返す名前付きの機能です。 この言語で、値を返すサービスを通じて自体、<xref:Microsoft.VisualStudio.Package.ExpansionFunction>オブジェクト。 <xref:Microsoft.VisualStudio.Package.ExpansionFunction>オブジェクトは、拡張機能をサポートする言語サービスによって実装する必要があります。  
  
## <a name="providing-support-for-code-snippets"></a>コード スニペットのサポートを提供します。  
 コード スニペットのサポートを有効にするには、提供またはスニペットをインストールする必要があり、ユーザーはそのスニペットを挿入するための手段を提供する必要があります。 コード スニペットのサポートを有効にする手順は次の 3 つです。  
  
1.  スニペット ファイルをインストールします。  
  
2.  言語サービスのコード スニペットを有効にします。  
  
3.  呼び出す、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>オブジェクト。  
  
### <a name="installing-the-snippet-files"></a>スニペット ファイルをインストールします。  
 言語のすべてのスニペットは、通常 1 つスニペット テンプレートはファイルごとに XML ファイル内のテンプレートとして保存されます。 コード スニペット テンプレートに使用される XML スキーマの詳細については、「[コード スニペット スキーマ リファレンス](../../ide/code-snippets-schema-reference.md)です。 各スニペット テンプレートは、言語 ID で識別されます。 この言語 ID は、レジストリで指定に、`Language`の属性、\<コード >、テンプレート内のタグ。  
  
 通常は、スニペット テンプレート ファイルが格納される 2 つの場所: 1)、言語がインストールされていると、ユーザーのフォルダーに 2)。 これらの場所はレジストリに追加ようにする、Visual Studio**コード スニペット マネージャー**スニペットを見つけることができます。 ユーザーのフォルダーには、ユーザーによって作成されたスニペットを格納します。  
  
 次のようなインストールされているスニペット テンプレート ファイルの一般的なフォルダーのレイアウト: *[として「installroot」]*\\*[TestLanguage]*\Snippets\\*の[LCID]*\Snippets です。  
  
 *[として「installroot」]*で使用する言語がインストールされているフォルダーです。  
  
 *[TestLanguage]*フォルダー名として使用する言語の名前を指定します。  
  
 *[LCID]*ロケール ID です。 これは、スニペットのどのローカライズ版は格納します。 たとえば、英語版のロケール ID はこの 1033、ため*[LCID]* 1033 は置き換えられます。  
  
 1 つの追加ファイルを指定する必要があり、SnippetsIndex.xml または ExpansionsIndex.xml (任意の有効なファイル名 .xml で終わるを使用することができます) と通常呼ばれる、インデックス ファイルであります。 このファイルは通常に格納されている、 *[として「installroot」]*\\*[TestLanguage]*フォルダー snippets フォルダーだけでなく、言語 ID の正確な場所と言語の GUID を指定しますスニペットを使用するサービスです。 インデックス ファイルの正確なパスは、「のレジストリ エントリのインストール」で後述するように、レジストリに配置されます。 SnippetsIndex.xml ファイルの例を次に示します。  
  
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
  
 \<言語 > タグは、言語 ID を指定 (、`Lang`属性) と、言語サービス GUID です。  
  
 この例では、Visual Studio インストール フォルダーに、言語サービスをインストールしている前提としています。 %Lcid は、ユーザーの現在のロケール ID に置き換えられます 複数\<SnippetDir > タグを追加できる別のディレクトリおよびロケールごとに 1 つです。 さらに、スニペット フォルダーがの索引ファイルで指定されたそれぞれのサブフォルダーを含めることができます、 \<SnippetSubDir > タグに埋め込まれている、 \<SnippetDir > タグです。  
  
 ユーザー、対象の言語が独自のスニペットを作成できます。 たとえば、ユーザーの設定 フォルダーに格納するは通常これら*[TestDocs]*\Code スニペット\\*[TestLanguage]*\Test コード スニペットでは、ここで*[TestDocs]* Visual Studio のユーザーの設定 フォルダの場所です。  
  
 格納されているパスに次の置換要素を配置することができます、\<か、指定 > インデックス ファイルのタグ。  
  
|要素|説明|  
|-------------|-----------------|  
|LCID %|ロケール id です。|  
|% として「installroot」|たとえば、C:\Program 個の \microsoft Visual Studio の 8、Visual Studio のルート インストール フォルダーです。|  
|ProjDir %|現在のプロジェクトを含むフォルダー。|  
|ProjItem %|現在のプロジェクト項目を含むフォルダー。|  
|TestDocs %|ユーザーの設定 フォルダー、たとえば、C:\Documents and Settings フォルダー\\*[username]*\My Documents\Visual Studio\8 です。|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>言語サービスのコード スニペットを有効にします。  
 追加することで、言語サービスのコード スニペットを有効にすることができます、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>属性、VSPackage を (を参照してください[レガシ言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)詳細)。 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A>と<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A>パラメーターは省略可能で、含める必要があります、`SearchPaths`名前付きパラメーターを通知するために、**コード スニペット マネージャー**スニペットの場所。  
  
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
  
### <a name="calling-the-expansion-provider"></a>拡張プロバイダーの呼び出し  
 言語サービスは、カーソルが呼び出される方法と同様にすべてのコード スニペットの挿入を制御します。  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>コード スニペットの拡張プロバイダーの呼び出し  
 拡張プロバイダーを呼び出す 2 つの方法: メニュー コマンドを使用するか、コンプリート リストからショートカットを使用しています。  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>メニュー コマンドを使用して、コード スニペットの挿入  
 スニペット ブラウザーを表示するメニュー コマンドを使用するメニュー コマンドを追加し、呼び出し、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>インターフェイス メニュー コマンドに応答します。  
  
1.  .Vsct ファイルにコマンドとボタンを追加します。 そのために行うための手順を参照して[メニュー コマンドを使用して、拡張機能の作成](../../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  クラスを派生、<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスし、オーバーライド、<xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A>メソッドを新しいメニュー コマンドのサポートを示します。 この例では、メニュー コマンドが常に有効です。  
  
    ```csharp  
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
  
3.  上書き、<xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスを取得する、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>オブジェクトと呼び出し、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>そのオブジェクトのメソッドです。  
  
    ```csharp  
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
  
     以下の方法で、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>スニペットの挿入の処理中に特定の順序でクラスを Visual Studio によって呼び出さは。  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     後に、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>メソッドが呼び出されると、スニペットが挿入された、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>は挿入されているスニペットを変更するために使用される特殊な編集モードでは、オブジェクトです。  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>ショートカットを使用してコード スニペットの挿入  
 コンプリート リストから、ショートカットの実装は、メニュー コマンドを実装するよりも複雑です。 IntelliSense の単語補完リストに、まずスニペットのショートカットを追加する必要があります。 スニペット ショートカット名が入力候補の結果として挿入されたときを検出する必要があります。 最後には、スニペットのタイトルとショートカット名を使用してパスを取得し、その情報を<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>メソッドを<xref:Microsoft.VisualStudio.Package.ExpansionProvider>メソッドです。  
  
 スニペットのショートカットに追加する単語補完リストに追加する、<xref:Microsoft.VisualStudio.Package.Declarations>内のオブジェクト、<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラスです。 スニペット名としてのショートカット キーを確認することを確認する必要があります。 例については、次を参照してください。[チュートリアル:、のインストールされているコード スニペットの一覧 (レガシ実装) を取得する](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)です。  
  
 内のコード スニペット ショートカットの挿入を検出することができます、<xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A>のメソッド、<xref:Microsoft.VisualStudio.Package.Declarations>クラスです。 スニペット名は、ソース ファイルには既に挿入されて、ために、拡張を挿入するときに削除する必要があります。 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>メソッドにはスニペットの挿入ポイントを説明するスパン; スパンには、ソース ファイル内のスニペット全体の名前が含まれている場合、その名前は、スニペットで置き換えられます。  
  
 ここでは、バージョン、<xref:Microsoft.VisualStudio.Package.Declarations>ショートカット名を指定したスニペットの挿入を処理するクラスです。 他の方法で、<xref:Microsoft.VisualStudio.Package.Declarations>わかりやすくするためのクラスが省略されています。 このクラスのコンス トラクターを<xref:Microsoft.VisualStudio.Package.LanguageService>オブジェクト。 これは、バージョンからに渡すことができます、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト (の実装など、<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラスがかかる場合があります、<xref:Microsoft.VisualStudio.Package.LanguageService>コンス トラクター内のオブジェクトし、そのオブジェクトに渡す、`TestDeclarations`クラスのコンス トラクター)。  
  
```csharp  
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
  
 言語サービスは、ショートカット名を取得と、が呼び出されて、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A>ファイル名とコード スニペットのタイトルを取得します。 言語サービスを呼び出すし、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>コード スニペットを挿入するクラス。 特定の順序で Visual Studio によって、次のメソッドが呼び出される、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>プロセス中に、スニペットの挿入のクラス。  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 言語サービスのインストールされているコード スニペットの一覧の取得の詳細については、次を参照してください。[チュートリアル:、のインストールされているコード スニペットの一覧 (レガシ実装) を取得する](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)です。  
  
## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction クラスの実装  
 拡張関数は、スニペット テンプレートに埋め込まれているし、フィールドに格納される 1 つ以上の値を返す名前付きの機能です。 言語サービスで拡張機能をサポートするためからクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.ExpansionFunction>クラスし、実装、<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A>メソッドです。 オーバーライドする必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>のバージョンの新しいインスタンスを返すために、<xref:Microsoft.VisualStudio.Package.ExpansionFunction>各拡張機能をサポートするためのクラスです。 またをオーバーライドする必要がある拡張機能を使用できる値のリストをサポートする場合、<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.ExpansionFunction>クラスをそれらの値の一覧を返します。  
  
 引数を受け取るか、他のフィールドにアクセスする必要がある拡張関数いないに関連付けることは編集可能なフィールド拡張プロバイダーは、拡張関数が呼び出された時点では完全に初期化できませんする可能性があります。 その結果、拡張関数は、引数またはその他のフィールドの値を取得できません。  
  
### <a name="example"></a>例  
 単純な拡張関数を呼び出す方法の例を次に示します`GetName`実装する場合があります。 この拡張機能に番号が追加、基本クラスの名前、拡張関数がインスタンス化されるたび (のどに対応するたびに、関連付けられているコード スニペットが挿入されます)。  
  
```csharp  
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
  
## <a name="see-also"></a>参照  
 [レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [レガシ言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [コード スニペット](../../ide/code-snippets.md)   
 [チュートリアル: インストールされているコード スニペットの一覧の取得 (従来の実装)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
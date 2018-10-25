---
title: 従来の言語サービスでのコード スニペットのサポート |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7ad314e5a160ae280b33586fb7dfe1b42ec470f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858109"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>従来の言語サービスでのコード スニペットのサポート
コード スニペットは、ソース ファイルに挿入するコードの一部です。 スニペット自体とは、一連のフィールドの XML ベースのテンプレートです。 これらのフィールドには、スニペットが挿入され、スニペットを挿入するコンテキストに応じて異なる値を持つことができますが強調表示されます。 スニペットの挿入後にすぐに、言語サービスは、スニペットを書式設定できます。  
  
 TAB キーを使用してナビゲートするスニペットのフィールドを許可する特別な編集モードでは、スニペットが挿入されます。 フィールドには、IntelliSense スタイルのドロップダウン メニューをサポートできます。 ユーザーを入力してください、または ESC キーを入力して、ソース ファイルにスニペットをコミットします。 スニペットの詳細については、次を参照してください[コード スニペット](../../ide/code-snippets.md)します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 詳細については、次を参照してください。[チュートリアル: コード スニペットを実装する](../../extensibility/walkthrough-implementing-code-snippets.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Managed Package Framework のコード スニペットのサポート  
 Managed package framework (MPF) は、スニペットを挿入するテンプレートの読み取りから、ほとんどのスニペット機能をサポートし、編集モードの特殊なを有効にするとします。 サポートを使って管理、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>クラス。  
  
 ときに、<xref:Microsoft.VisualStudio.Package.Source>クラスをインスタンス化、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>メソッド、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスを呼び出して取得、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>オブジェクト (注意ベース<xref:Microsoft.VisualStudio.Package.LanguageService>クラスは常に新しいを返します<xref:Microsoft.VisualStudio.Package.ExpansionProvider>オブジェクトごとに<xref:Microsoft.VisualStudio.Package.Source>オブジェクトの場合)。  
  
 MPF は、拡張機能をサポートしていません。 拡張する機能は、スニペット テンプレートに埋め込まれているし、フィールドに配置することの 1 つまたは複数の値を返す名前付きの機能です。 言語によって、値が返されるサービス自体から、<xref:Microsoft.VisualStudio.Package.ExpansionFunction>オブジェクト。 <xref:Microsoft.VisualStudio.Package.ExpansionFunction>オブジェクトは、拡張機能をサポートする言語サービスで実装する必要があります。  
  
## <a name="providing-support-for-code-snippets"></a>コード スニペットのサポートを提供します。  
 コード スニペットのサポートを有効にするには、提供またはスニペットをインストールする必要があり、ユーザーをこれらのスニペットを挿入するための手段を提供する必要があります。 コード スニペットのサポートを有効にする 3 つの手順があります。  
  
1.  スニペット ファイルをインストールします。  
  
2.  言語サービスのコード スニペットを有効にします。  
  
3.  呼び出す、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>オブジェクト。  
  
### <a name="installing-the-snippet-files"></a>スニペット ファイルをインストールします。  
 言語のすべてのスニペットは、ファイルごとに 1 つスニペット テンプレート通常、XML ファイルにテンプレートとして格納されます。 コード スニペットのテンプレートを使用する XML スキーマの詳細については、「[コード スニペット スキーマ リファレンス](../../ide/code-snippets-schema-reference.md)します。 各スニペット テンプレートは、言語 ID で識別されます。 この言語の ID レジストリで指定され、に、`Language`の属性、\<コード > テンプレートのタグ。  
  
 通常は、スニペット テンプレート ファイルが格納される 2 つの場所: 1)、言語がインストールされていると、2) のユーザーのフォルダー。 これらの場所はレジストリに追加、これを Visual Studio**コード スニペット マネージャー**スニペットを見つけることができます。 ユーザーのフォルダーには、ユーザーによって作成されたスニペットを格納します。  
  
 次のようなインストールされているスニペット テンプレート ファイルの一般的なフォルダー レイアウト: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets します。  
  
 *[InstallRoot]* でお使いの言語がインストールされているフォルダーです。  
  
 *[TestLanguage]* フォルダー名として使用する言語の名前を指定します。  
  
 *[LCID]* はロケール ID です。 これは、スニペットのどのローカライズ版格納されます。 たとえば、1033 の場合は、英語のロケール ID のため *[LCID]* 1033 は置き換えられます。  
  
 1 つのファイルを指定する必要があり、SnippetsIndex.xml または ExpansionsIndex.xml (任意の有効なファイル名 .xml で終わるを使用することができます) と通常呼ばれる、インデックス ファイルです。 このファイルは通常に格納されている、 *[InstallRoot]*\\ *[TestLanguage]* フォルダー スニペットのフォルダーだけでなく、言語 ID の正確な場所と言語の GUID を指定しますスニペットを使用するサービスです。 インデックス ファイルの正確なパスは、「のレジストリ エントリをインストールする」で後述するようレジストリに配置されます。 SnippetsIndex.xml ファイルの例を次に示します。  
  
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
  
 \<言語 > タグは、言語 ID を指定します (、`Lang`属性) と言語サービスの GUID。  
  
 この例では、Visual Studio のインストール フォルダーに、言語サービスをインストールしている前提としています。 %Lcid は、ユーザーの現在のロケール ID に置き換えられます 複数\<SnippetDir > タグを追加できる別のディレクトリおよびロケールごとに 1 つ。 さらに、スニペット フォルダーは、インデックス ファイルで識別されるそれぞれのサブフォルダーを含めることができます、 \<SnippetSubDir > タグに埋め込まれている、 \<SnippetDir > タグです。  
  
 ユーザーは、独自のスニペットの言語にも作成できます。 たとえば、ユーザーの設定 フォルダーに格納するは通常これら *[TestDocs]* \Code スニペット\\ *[TestLanguage]* \Test、コード スニペットを *[TestDocs]* は Visual Studio のユーザーの設定 フォルダーの場所です。  
  
 次の置換要素に格納されているパスに配置できる、\<か、指定 > インデックス ファイルのタグ。  
  
|要素|説明|  
|-------------|-----------------|  
|LCID %|ロケール id。|  
|InstallRoot %|たとえば、C:\Program 個の \microsoft Visual Studio の 8、Visual Studio のルート インストール フォルダーです。|  
|ProjDir %|現在のプロジェクトを含むフォルダー。|  
|ProjItem %|現在のプロジェクト項目を含むフォルダー。|  
|TestDocs %|ユーザーの設定 フォルダー、たとえば、C:\Documents and Settings フォルダー\\ *[username]* \My Documents\Visual Studio\8 します。|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>言語サービスのコード スニペットを有効にします。  
 追加して、言語サービスのコード スニペットを有効にすることができます、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>属性、VSPackage を (を参照してください[従来の言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md)詳細については)。 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A>と<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A>パラメーターは省略可能ですが、含める必要があります、`SearchPaths`名前付きパラメーターを通知するために、**コード スニペット マネージャー**スニペットの場所。  
  
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
 言語サービスでは、挿入が呼び出される方法と同様に、すべてのコード スニペットの挿入を制御します。  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>コード スニペットの拡張プロバイダーの呼び出し  
 拡張プロバイダーを呼び出す方法の 2 つの方法: メニュー コマンドを使用するか、入力候補一覧からショートカットを使用しています。  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>メニュー コマンドを使用してコード スニペットの挿入  
 スニペットのブラウザーを表示するメニュー コマンドを使用するメニュー コマンドの追加を呼び出して、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>インターフェイス メニュー コマンドに応答します。  
  
1.  .Vsct ファイルにコマンドとボタンを追加します。 そのために行うための手順を確認できます[メニュー コマンドを使用して拡張機能の作成](../../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  派生クラスを<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスし、オーバーライド、<xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A>新しいメニュー コマンドのサポートを示すためのメソッド。 この例では、メニュー コマンドが常に有効です。  
  
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
  
3.  上書き、<xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.ViewFilter>を取得するクラス、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>オブジェクトと呼び出し、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>そのオブジェクトのメソッド。  
  
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
  
     次のメソッドは、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>スニペットの挿入の処理中に特定の順序での Visual Studio によって、クラスが呼び出されます。  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     後に、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>メソッドが呼び出されると、スニペットが挿入された、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>オブジェクトが挿入されたスニペットを変更するために使用される特殊な編集モードにします。  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>ショートカットを使用してコード スニペットの挿入  
 入力候補一覧から、ショートカットの実装は、メニュー コマンドを実装するよりもはるかに複雑です。 まず、IntelliSense の単語補完リストにスニペットのショートカットを追加する必要があります。 スニペットのショートカット名が入力候補の結果として挿入されたときを検出する必要があります。 最後に、スニペットのタイトルとショートカット名を使用してパスを取得してその情報を渡す、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>メソッドを<xref:Microsoft.VisualStudio.Package.ExpansionProvider>メソッド。  
  
 スニペットのショートカットを単語の入力候補一覧に追加するを追加、<xref:Microsoft.VisualStudio.Package.Declarations>オブジェクト、<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラス。 スニペット名としてのショートカット キーを確認することを確認する必要があります。 例については、次を参照してください。[チュートリアル:、のインストールされているコード スニペットの一覧 (従来の実装) を取得する](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)します。  
  
 内のコード スニペットのショートカットの挿入を検出することができます、<xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A>のメソッド、<xref:Microsoft.VisualStudio.Package.Declarations>クラス。 ソース ファイルには、スニペット名が既に挿入されている、ために、拡張が挿入されたときに削除する必要があります。 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>メソッドは、スニペットの挿入ポイントを説明する範囲を受け取ります。 その名前は、スニペットに置き換え、スパンには、ソース ファイルの全体のスニペット名が含まれている場合。  
  
 バージョンを次に示します、<xref:Microsoft.VisualStudio.Package.Declarations>処理スニペットの挿入をショートカット名を指定するクラスです。 他の方法で、<xref:Microsoft.VisualStudio.Package.Declarations>クラスはわかりやすくするために省略されています。 このクラスのコンス トラクターはメモ、<xref:Microsoft.VisualStudio.Package.LanguageService>オブジェクト。 これは、バージョンからに渡すことが、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト (の実装など、<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラスがかかる場合があります、<xref:Microsoft.VisualStudio.Package.LanguageService>コンス トラクター内のオブジェクトし、そのオブジェクトに渡す、`TestDeclarations`クラスのコンス トラクター)。  
  
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
  
 言語サービスでは、ショートカットの名前を取得、ときに呼び出す、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A>ファイル名とコード スニペットのタイトルを取得します。 言語サービスを呼び出して、<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>コード スニペットを挿入するクラス。 特定の順序で、次のメソッドが Visual Studio によってと呼ばれる、<xref:Microsoft.VisualStudio.Package.ExpansionProvider>スニペットの挿入の処理中にクラス。  
  
1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
   言語サービスのインストールされているコード スニペットの一覧の取得の詳細については、次を参照してください。[チュートリアル:、のインストールされているコード スニペットの一覧 (従来の実装) を取得する](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)します。  
  
## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction クラスを実装します。  
 拡張する機能は、スニペット テンプレートに埋め込まれているし、フィールドに配置することの 1 つまたは複数の値を返す名前付きの機能です。 で、言語サービスの拡張機能をサポートするためには、からクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.ExpansionFunction>クラスし、実装、<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A>メソッド。 オーバーライドする必要がありますし、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>メソッド、<xref:Microsoft.VisualStudio.Package.LanguageService>のバージョンの新しいインスタンスを返すために、<xref:Microsoft.VisualStudio.Package.ExpansionFunction>各拡張機能をサポートするためのクラス。 オーバーライドする必要がある拡張機能を使用できる値のリストをサポートする場合、<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.ExpansionFunction>クラスをそれらの値の一覧を返します。  
  
 拡張プロバイダーは、拡張関数が呼び出された時点では完全に初期化されませんする可能性があります、拡張関数の引数を受け取り、または他のフィールドにアクセスする必要がありますが編集可能なフィールドに関連付けられてできません必要があります。 その結果、拡張機能は、引数または他のフィールドの値を取得できません。  
  
### <a name="example"></a>例  
 単純な拡張関数を呼び出す方法の例を次に示します`GetName`実装場合があります。 この拡張機能に数字を追加の基本クラスの名前、拡張関数がインスタンス化されるたび (関連付けられているコード スニペットは、各時間に対応が挿入されます)。  
  
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
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [従来の言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [コード スニペット](../../ide/code-snippets.md)   
 [チュートリアル: インストールされているコード スニペットの一覧の取得 (従来の実装)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
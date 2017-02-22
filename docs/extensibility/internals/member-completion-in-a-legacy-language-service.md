---
title: "従来の言語サービスでのメンバーの完了 | Microsoft Docs"
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
  - "IntelliSense、ツール ヒントのメンバーの完了"
  - "メンバー完了すると、言語サービス [マネージ パッケージ フレームワーク] でのサポート"
  - "言語サービス [マネージ パッケージ フレームワーク] IntelliSense のメンバーの完了"
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスでのメンバーの完了
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IntelliSense のメンバーの完了は、クラス、構造体、列挙体、または名前空間などの特定のスコープの可能なメンバーの一覧を表示するツール ヒントです。 たとえば、C\# の場合は、ユーザーが"this"に続けて、ピリオドを入力した場合すると、クラスまたは現在のスコープで構造体のすべてのメンバーの一覧は、ユーザーが選択できるリスト表示で表示されます。  
  
 マネージ パッケージ フレームワーク \(MPF\) は、ツール ヒントとツールヒントの; リストの管理をサポート一覧に表示されるデータを提供するパーサーの協力が必要なことだけです。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 詳細については、次を参照してください。 [エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## これは、しくみ  
 MPF クラスを使用するメンバーの一覧が表示される 2 つの方法を次に示します。  
  
-   識別子の上またはメンバーの終了文字の後にキャレットを配置し、選択 **メンバーの一覧** から、 **IntelliSense** メニュー。  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner> スキャナーがメンバーの終了文字を検出し、トークンのトリガーを設定 <xref:Microsoft.VisualStudio.Package.TokenTriggers> その文字にします。  
  
 メンバーの補完機能文字は、クラス、構造体、列挙体のメンバーが次のことを示します。 たとえば、c\# または Visual Basic でメンバーの補完機能文字は、 `.`, 文字では C\+\+ では、いずれかになる一方で、 `.` または `->`です。 トリガー値は、メンバーの選択の文字をスキャンする場合は設定されます。  
  
### IntelliSense のメンバーの一覧表示コマンド  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> コマンドへの呼び出しを開始する、 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> メソッドを <xref:Microsoft.VisualStudio.Package.Source> クラスおよび <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> メソッドの呼び出しを <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 解析理由が付いているメソッドのパーサー <xref:Microsoft.VisualStudio.Package.ParseReason>します。  
  
 パーサーでは、現在の位置として、または現在の位置の直前に、トークンのコンテキストを決定します。 このトークンに基づき、宣言の一覧が表示されます。 たとえば、c\# でクラスのメンバーと選択にキャレットを配置する場合 **メンバーの一覧**, 、クラスのすべてのメンバーの一覧を取得します。 オブジェクト変数に続くピリオドの後にキャレットを配置する場合は、オブジェクトが表すクラスのすべてのメンバーの一覧を取得します。 メンバーの一覧が表示されているときにメンバーのキャレットが配置されている場合がキャレットの一覧でいずれかであるメンバーを置換する一覧からメンバーを選択することを確認します。  
  
### トークンのトリガー  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> トリガーへの呼び出しを開始する、 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> メソッドを <xref:Microsoft.VisualStudio.Package.Source> クラスおよび <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> メソッドを呼び出す解析理由が付いているパーサー <xref:Microsoft.VisualStudio.Package.ParseReason> \(トークンのトリガーも含まれている場合、 <xref:Microsoft.VisualStudio.Package.TokenTriggers> フラグは、解析理由は、 <xref:Microsoft.VisualStudio.Package.ParseReason> 結合するメンバーの選択と中かっこが強調表示\)。  
  
 パーサーは、現在のコンテキストを判断、メンバーは、文字を選択する前にどのような入力されただけでなく配置します。 この情報からは、パーサーは、要求のスコープのすべてのメンバーの一覧を作成します。 この宣言の一覧に入っている、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> から返されるオブジェクト、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドです。 すべての宣言が返された場合は、メンバー完了ツール ヒントが表示されます。 ツール ヒントがのインスタンスによって管理されている、 <xref:Microsoft.VisualStudio.Package.CompletionSet> クラスです。  
  
## メンバーの完了のサポートを有効にします。  
 必要があります、 `CodeSense` 、IntelliSense の操作をサポートするために、レジストリ エントリが 1 に設定します。 渡された名前付きパラメーターでこのレジストリ エントリを設定できる、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 言語パッケージに関連付けられているユーザーの属性です。 言語サービス クラスからは、このレジストリ エントリの値の読み取り、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> プロパティを <xref:Microsoft.VisualStudio.Package.LanguagePreferences> クラスです。  
  
 スキャナーのトークンのトリガーが返された場合 <xref:Microsoft.VisualStudio.Package.TokenTriggers>, 、し、パーサーが宣言の一覧を返す、メンバーのコンプリート リストが表示されます。  
  
## スキャナーのメンバーの完了をサポートします。  
 スキャナーは、メンバーの終了文字を検出し、トークンのトリガーを設定することである必要があります <xref:Microsoft.VisualStudio.Package.TokenTriggers> その文字の解析時です。  
  
### 例  
 メンバーの終了文字を検出し、適切な設定の簡単な例を次に示します <xref:Microsoft.VisualStudio.Package.TokenTriggers> フラグ。 この例では、説明の目的でのみです。 スキャナーにメソッドが含まれていると想定して `GetNextToken` を識別し、テキストの行からトークンを返します。 コード例は、適切な文字がときだけで、トリガーを設定します。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## パーサーでメンバーの完了をサポートします。  
 メンバーの完了、 <xref:Microsoft.VisualStudio.Package.Source> クラスの呼び出し、 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> メソッドです。 派生したクラスで、リストを実装する必要があります、 <xref:Microsoft.VisualStudio.Package.Declarations> クラスです。 参照してください、 <xref:Microsoft.VisualStudio.Package.Declarations> クラスの詳細についてはメソッドを実装する必要があります。  
  
 パーサーが呼び出された <xref:Microsoft.VisualStudio.Package.ParseReason> または <xref:Microsoft.VisualStudio.Package.ParseReason> メンバーの選択の文字は型指定されています。 指定されている位置、 <xref:Microsoft.VisualStudio.Package.ParseRequest> メンバーは、文字を選択した後すぐにオブジェクトをします。 パーサーは、ソース コードで特定の時点のメンバー リストに表示されるすべてのメンバーの名前を収集する必要があります。 パーサーは、ユーザーがメンバー選択文字に関連付けられたスコープを決定するのには、現在の行を解析する必要があります。  
  
 メンバーは、文字を選択する前に、このスコープは、識別子の型に基づきます。 たとえば、C\# の場合、メンバー変数を指定 `languageService` の型を持つ `LanguageService`, 入力、 **languageService。** のすべてのメンバーの一覧を作成、 `LanguageService` クラスです。 C\# でも」と入力 **この。** 、現在のスコープ内のクラスのすべてのメンバーの一覧を作成します。  
  
### 例  
 次の例では、設定する方法の 1 つ、 <xref:Microsoft.VisualStudio.Package.Declarations> \] ボックスの一覧です。 このコードでは、パーサーが宣言を構築してを呼び出して、一覧に追加する、 `AddDeclaration` メソッドを `TestAuthoringScope` クラスです。  
  
```c#  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```
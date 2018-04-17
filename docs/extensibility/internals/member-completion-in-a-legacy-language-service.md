---
title: 従来の言語サービスでメンバー補完 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cc22190c9228d2e166be94ed0d5cc78105e2404
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="member-completion-in-a-legacy-language-service"></a>従来の言語サービスでメンバーの完了
IntelliSense のメンバーの補完は、クラス、構造体、列挙型、または名前空間などの特定のスコープの可能なメンバーの一覧を表示するツール ヒントです。 たとえば、C# の場合、ユーザーの種類"this"、ピリオドが続く場合クラスまたは現在のスコープで構造体のすべてのメンバーの一覧でが表示されます、ユーザーが選択できるリスト。  
  
 Managed package framework (MPF) は、サポート ツール ヒントとツールヒント; の一覧を管理します。必要なは、一覧に表示されるデータを提供するためにパーサーから協調です。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 詳細については、次を参照してください。[エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="how-it-works"></a>しくみ  
 MPF クラスを使用するメンバーの一覧が表示される 2 つの方法を次に示します。  
  
-   識別子の上またはメンバー完了文字の後にキャレットを配置しを選択すると**メンバーの一覧**から、 **IntelliSense**メニュー。  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner>スキャナーがメンバーの終了文字を検出し、トークンのトリガーを設定<xref:Microsoft.VisualStudio.Package.TokenTriggers>その文字にします。  
  
 メンバーの入力候補の文字は、クラス、構造体、列挙体のメンバーが次のことを示します。 たとえば、c# または Visual Basic でメンバー入力候補の文字は、 `.`C++ では、文字は、いずれかになる一方で、`.`または`->`です。 トリガー値は、メンバー選択文字をスキャンするときに設定されます。  
  
### <a name="the-intellisense-member-list-command"></a>IntelliSense のメンバー一覧のコマンド  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>コマンドへの呼び出しを開始する、<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>メソッドを<xref:Microsoft.VisualStudio.Package.Source>クラスおよび<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>メソッドを呼び出す、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッド パーサーの解析の理由で<xref:Microsoft.VisualStudio.Package.ParseReason>です。  
  
 パーサーでは、下にある、または現在の位置の直前に、トークンと同様に、現在の位置のコンテキストを決定します。 このトークンに基づき、宣言の一覧が表示されます。 たとえば、c# では、クラスのメンバーと選択にキャレットを配置する場合**メンバーの一覧**クラスのすべてのメンバーの一覧を取得します。 オブジェクト変数に続くピリオドの後にキャレットを配置する場合は、オブジェクトが表すクラスのすべてのメンバーの一覧を取得します。 カレットがメンバーのメンバーの一覧が表示されると場合、に、一覧からメンバーを選択すると、キャレットの一覧でいずれかであるメンバーが置き換えられますことに注意してください。  
  
### <a name="the-token-trigger"></a>トークンのトリガー  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers>トリガーへの呼び出しを開始する、<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>メソッドを<xref:Microsoft.VisualStudio.Package.Source>クラスおよび<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>メソッドを呼び出す解析理由をつけて、パーサー <xref:Microsoft.VisualStudio.Package.ParseReason> (トークンのトリガーにも含まれている場合、<xref:Microsoft.VisualStudio.Package.TokenTriggers>フラグは、解析の理由は<xref:Microsoft.VisualStudio.Package.ParseReason>組み合わせるメンバーの選択と中かっこが強調表示)。  
  
 パーサーは、現在のコンテキストを判断に加えて新機能に型指定されたメンバーは、文字を選択する前に配置します。 この情報からは、パーサーは、要求されたスコープの全メンバーのリストを作成します。 この宣言の一覧が格納されている、<xref:Microsoft.VisualStudio.Package.AuthoringScope>から返されるオブジェクト、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドです。 すべての宣言が返される場合はメンバー完了ツール ヒントが表示されます。 ツール ヒントがのインスタンスによって管理されている、<xref:Microsoft.VisualStudio.Package.CompletionSet>クラスです。  
  
## <a name="enabling-support-for-member-completion"></a>メンバーの完了のサポートを有効にします。  
 必要があります、 `CodeSense` IntelliSense の操作をサポートするために、レジストリ エントリが 1 に設定します。 渡される名前付きパラメーターを持つこのレジストリ エントリを設定することができます、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>言語パッケージに関連付けられているユーザーの属性です。 言語サービス クラスからは、このレジストリ エントリの値の読み取り、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>プロパティを<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラスです。  
  
 スキャナーのトークンのトリガーを返す場合<xref:Microsoft.VisualStudio.Package.TokenTriggers>、し、パーサーは、宣言の一覧を返します、メンバーのコンプリート リストが表示されます。  
  
## <a name="supporting-member-completion-in-the-scanner"></a>スキャナーのメンバーの完了をサポートします。  
 スキャナーは、メンバーの終了文字を検出し、トークンのトリガーを設定することである必要があります<xref:Microsoft.VisualStudio.Package.TokenTriggers>その文字が解析されます。  
  
### <a name="example"></a>例  
 メンバーの終了文字を検出して、適切な設定の簡単な例を次に示します<xref:Microsoft.VisualStudio.Package.TokenTriggers>フラグ。 この例では、わかりやすくするためだけです。 スキャナーにメソッドが含まれていると想定`GetNextToken`を識別し、テキストの行からトークンを返します。 コード例は、正しい種類の文字を認識するたびにトリガーを単に設定します。  
  
```csharp  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>パーサーでメンバーの完了をサポートします。  
 メンバーの完了、<xref:Microsoft.VisualStudio.Package.Source>クラスの呼び出し、<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>メソッドです。 派生したクラスの一覧を実装する必要があります、<xref:Microsoft.VisualStudio.Package.Declarations>クラスです。 参照してください、<xref:Microsoft.VisualStudio.Package.Declarations>クラスの詳細については、メソッドを実装する必要があります。  
  
 パーサーがで呼び出された<xref:Microsoft.VisualStudio.Package.ParseReason>または<xref:Microsoft.VisualStudio.Package.ParseReason>メンバー選択文字が入力した場合。 指定された場所、<xref:Microsoft.VisualStudio.Package.ParseRequest>メンバーは、文字を選択した後すぐにオブジェクトをします。 パーサーは、特定の時点のソース コードで、メンバー リストに含まれるすべてのメンバーの名前を収集する必要があります。 パーサーは、ユーザーがメンバー選択文字に関連付けられたスコープを決定するのには、現在の行を解析する必要があります。  
  
 このスコープは、メンバーは、文字を選択する前に、識別子の型に基づいています。 たとえば、C# の場合、メンバー変数を指定`languageService`の型を持つ`LanguageService`次に、「 **languageService です。** すべてのメンバーの一覧を作成、`LanguageService`クラスです。 また c# では、入力**これです。** 現在のスコープ内のクラスのすべてのメンバーの一覧を生成します。  
  
### <a name="example"></a>例  
 次の例を設定する方法を示しています、 <xref:Microsoft.VisualStudio.Package.Declarations>  ボックスの一覧です。 このコードでは、パーサーが宣言を構築し、呼び出すことによって、一覧に追加前提としています、`AddDeclaration`メソッドを`TestAuthoringScope`クラスです。  
  
```csharp  
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
---
title: レガシ言語の Service2 の実装 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee151375cfff8977249ca5e21255401235987886
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513362"
---
# <a name="implementing-a-legacy-language-service"></a>従来の言語サービスを実装します。
Managed package framework (MPF) を使用して、言語サービスを実装するからクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスし、次の抽象メソッドとプロパティを実装します。  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> メソッド  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> メソッド  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッド  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> プロパティ  
  
 これらのメソッドとプロパティを実装する方法の詳細については、以下の適切なセクションを参照してください。  
  
 その他の機能をサポートするために、言語サービスは、MPF 言語サービス クラスの 1 つからクラスを派生する必要があります。たとえば、追加のメニュー コマンドをサポートするためにする必要がありますからクラスを派生、<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスし、メソッドを処理するコマンドのいくつかのオーバーライド (を参照してください<xref:Microsoft.VisualStudio.Package.ViewFilter>詳細については)。 <xref:Microsoft.VisualStudio.Package.LanguageService>クラスは、多数のさまざまなクラスの新しいインスタンスを作成すると呼び出されるメソッドを提供し、クラスのインスタンスを提供する適切な作成メソッドをオーバーライドします。 たとえば、オーバーライドする必要があります、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス独自のインスタンスを返す<xref:Microsoft.VisualStudio.Package.ViewFilter>クラス。 詳細については、「カスタム クラスをインスタンス化する」セクションを参照してください。  
  
 言語サービスでは、多くの場所で使用される独自のアイコンも指定できます。 リスト内の各項目は、項目をマークするメソッド、クラス、名前空間、プロパティ、それに関連付けられているアイコンを持つことができます、IntelliSense 入力候補一覧が表示されるときや、言語の必要なことすべてなど。 これらのアイコンが使用されるすべての IntelliSense の一覧で、**ナビゲーション バー**、し、**エラー一覧**タスク ウィンドウ。 詳細については、以下の「言語サービス イメージ」セクションを参照してください。  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences メソッド  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>メソッドは常の同じインスタンスを返します、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラス。 ベースを使用する<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラスの場合は、追加の設定、言語サービスの必要はありません。 MPF 言語サービスのクラスは、少なくともの存在を想定していますベース<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラス。  
  
### <a name="example"></a>例  
 この例の一般的な実装を示しています、<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>メソッド。 この例は、ベースを使用して<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラス。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## <a name="getscanner-method"></a>GetScanner メソッド  
 このメソッドのインスタンスを返します、<xref:Microsoft.VisualStudio.Package.IScanner>スキャナー トークンとその型およびトリガーを取得するために使用される行指向のパーサーを実装するオブジェクト。 このスキャナーがで使用される、<xref:Microsoft.VisualStudio.Package.Colorizer>色づけに対するクラスのスキャナーより複雑な解析操作の準備として、トークンの種類とトリガーを取得するためも使用できます。 実装するクラスを指定する必要があります、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイスとのすべてのメソッドを実装する必要があります、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイス。  
  
### <a name="example"></a>例  
 この例の一般的な実装を示しています、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>メソッド。 `TestScanner`クラスが実装する、<xref:Microsoft.VisualStudio.Package.IScanner>インターフェイス (表示されません)。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## <a name="parsesource-method"></a>ParseSource メソッド  
 さまざまな理由数に基づいてソース ファイルを解析します。 このメソッドが指定された、<xref:Microsoft.VisualStudio.Package.ParseRequest>特定の解析操作からが期待を記述するオブジェクト。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドは、トークンの機能とスコープを決定するより複雑なパーサーを呼び出します。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドは、IntelliSense の操作とかっこの一致のサポートに使用されます。 このような高度な操作をサポートしない場合でもも返す必要がある、有効な<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクトとを実装するクラスを作成するを求め、<xref:Microsoft.VisualStudio.Package.AuthoringScope>インターフェイスし、そのインターフェイスのすべてのメソッドを実装します。 すべてのメソッドから null 値を返すことができますが、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト自体を null 値よりもする必要があります。  
  
### <a name="example"></a>例  
 この例の最小限の実装を示しています、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドと<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラス、言語サービスをコンパイルし、実際より高度な機能をサポートせずに機能させるのには不十分です。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## <a name="name-property"></a>Name プロパティ  
 このプロパティは、言語サービスの名前を返します。 これは、言語サービスの登録時に指定された同じ名前でなければなりません。 これの最も顕著なは、場所の数でこの名前が使用される、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラスの名前が、レジストリへのアクセスに使用されます。 レジストリにレジストリ エントリは、キー名を使用するため、このプロパティによって返される名前をローカライズされていない必要があります。  
  
### <a name="example"></a>例  
 この例の 1 つの考えられる実装を示しています、<xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>プロパティ。 ここに名前がハードコーディングに注意してください: 言語サービスの登録に使用できるように、リソース ファイルから実際の名前を取得する必要があります (を参照してください[従来の言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service1.md))。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## <a name="instantiating-custom-classes"></a>カスタム クラスをインスタンス化します。  
 各クラスの独自のバージョンのインスタンスを提供する、指定したクラスに次のメソッドをオーバーライドできます。  
  
### <a name="in-the-languageservice-class"></a>LanguageService クラス  
  
|メソッド|返されるクラス|説明|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|テキスト ビューにカスタムの追加機能をサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|カスタム ドキュメント プロパティをサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|サポートするために、**ナビゲーション バー**します。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|コード スニペット テンプレートで関数をサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|(このメソッドは通常、オーバーライドされていない) のコード スニペットをサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|カスタマイズをサポートする、<xref:Microsoft.VisualStudio.Package.ParseRequest>構造 (このメソッドは通常はオーバーライドされません)。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|ソース コードの書式設定、コメント文字を指定して、メソッド シグネチャのカスタマイズをサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|追加のメニュー コマンドをサポートします。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|(このメソッドは通常、オーバーライドされていない) 構文の強調表示をサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|言語設定へのアクセスをサポートします。 このメソッドは、実装する必要がありますが、基底クラスのインスタンスを返すことができます。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|行にトークンの種類を識別するために使用されるパーサーを提供します。 このメソッドを実装する必要がありますと<xref:Microsoft.VisualStudio.Package.IScanner>から派生する必要があります。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|機能と、全体のソース ファイル全体のスコープを識別するために使用されるパーサーを提供します。 このメソッドが実装する必要がありますのバージョンのインスタンスを返す必要があります、<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラス。 すべてをサポートする場合は、構文の強調表示 (する必要があります、<xref:Microsoft.VisualStudio.Package.IScanner>パーサーから返される、<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>メソッド)、しないことも戻り値以外には、このメソッドでのバージョン、<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラスのすべてのメソッドは、null 値を返します。|  
  
### <a name="in-the-source-class"></a>ソース クラス  
  
|メソッド|返されるクラス|説明|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|(このメソッドは通常、オーバーライドされていない)、IntelliSense 入力候補一覧の表示をカスタマイズします。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|エラー一覧 にマーカーをサポートするためのタスク一覧です。具体的には、ファイルを開くと、エラーが発生した行にジャンプすること以外の機能のサポート。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense のパラメーター ヒントのツールヒントの表示をカスタマイズします。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|コメント コードをサポートします。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|解析操作中に情報を収集します。|  
  
### <a name="in-the-authoringscope-class"></a>AuthoringScope クラス  
  
|メソッド|返されるクラス|説明|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|メンバーまたは型などの宣言の一覧を示します。 このメソッドは、実装する必要がありますが、null 値を返すことができます。 オブジェクトのバージョンのインスタンスである必要がありますこのメソッドは、有効なオブジェクトを返す場合、<xref:Microsoft.VisualStudio.Package.Declarations>クラス。|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|指定したコンテキストをメソッド シグネチャの一覧を提供します。 このメソッドは、実装する必要がありますが、null 値を返すことができます。 オブジェクトのバージョンのインスタンスである必要がありますこのメソッドは、有効なオブジェクトを返す場合、<xref:Microsoft.VisualStudio.Package.Methods>クラス。|  
  
## <a name="language-service-images"></a>言語サービスのイメージ  
 言語サービス全体で使用するアイコンの一覧を提供するには、オーバーライド、<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスを返す、<xref:System.Windows.Forms.ImageList>アイコンを格納しています。 基本<xref:Microsoft.VisualStudio.Package.LanguageService>クラスは、既定のアイコンのセットを読み込みます。 アイコンを必要としている場所の正確なイメージのインデックスを指定するため、独自のイメージ リストの配置方法を決めします。  
  
### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense のコンプリート リストで使用されるイメージ  
 各項目に対して、IntelliSense のコンプリート リストのイメージのインデックスが指定された、<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>のメソッド、<xref:Microsoft.VisualStudio.Package.Declarations>クラスは、イメージのインデックスを指定する場合にオーバーライドする必要があります。 返される値、<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>メソッドは、インデックスに指定されたイメージの一覧に、<xref:Microsoft.VisualStudio.Package.CompletionSet>クラスのコンス トラクターとは、同じイメージのリストから返されます、<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>メソッドで、 <xref:Microsoft.VisualStudio.Package.LanguageService> (を変更するイメージ リスト クラス使用して、<xref:Microsoft.VisualStudio.Package.CompletionSet>をオーバーライドする場合、<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.Source>別のイメージの一覧を提供するクラス)。  
  
### <a name="images-used-in-the-navigation-bar"></a>ナビゲーション バーで使用されるイメージ  
 **ナビゲーション バー**型およびメンバーの一覧が表示され、使用の迅速なナビゲーション アイコンを表示することができます。 これらのアイコンがから取得した、<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスで、専用のオーバーライドすることはできません、**ナビゲーション バー**します。 コンボ ボックスを表すリストがいっぱいになるためのコンボ ボックス内の各項目のインデックスが指定されて、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>クラス (を参照してください[従来の言語サービスでのナビゲーションバーのサポート](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). これらのイメージのインデックスは、のバージョンのでは通常、パーサーから何らかの方法で取得した、<xref:Microsoft.VisualStudio.Package.Declarations>クラス。 完全に依存するは、インデックスを取得する方法です。  
  
### <a name="images-used-in-the-error-list-task-window"></a>エラー一覧の [タスク] ウィンドウで使用されるイメージ  
 たびに、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッド パーサー (を参照してください[レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) エラーが発生し、そのエラーを<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.AuthoringSink>クラス、エラーは、 **エラー一覧**タスク ウィンドウ。 アイコンがタスク一覧 ウィンドウに表示される各項目を関連付けることができ、そのアイコンが同じイメージのリストから返される、<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。 MPF クラスの既定の動作では、エラー メッセージを使用してイメージを表示しないようにします。 ただしからクラスを派生させることでこの動作をオーバーライドすることができます、<xref:Microsoft.VisualStudio.Package.Source>クラスとオーバーライドを行う、<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>メソッド。 メソッドには、作成した新しい<xref:Microsoft.VisualStudio.Package.DocumentTask>オブジェクト。 そのオブジェクトを返す前に使用することができます、<xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A>プロパティを<xref:Microsoft.VisualStudio.Package.DocumentTask>イメージのインデックスを設定するオブジェクト。 次の例のようになります。 なお`TestIconImageIndex`列挙一覧のすべてのアイコンが表示され、この例に固有です。 言語サービスでのアイコンを識別するさまざまな方法があります。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TaskPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## <a name="the-default-image-list-for-a-language-service"></a>言語サービスの既定のイメージ リスト  
 基本の MPF 言語サービス クラスで提供される既定のイメージ リストには、さまざまな一般的な言語要素に関連付けられたアイコンが含まれています。 これらのアイコンの大部分は、public、internal、protected、private、友人、およびショートカットのアクセスの概念に対応する 6 つのバリエーションのセットに配置されます。 たとえば、さまざまなアイコンによって、パブリック、プロテクト、またはプライベート メソッドのことができます。  
  
 次の列挙型では、各アイコン セットの一般的な名前を指定し、関連するインデックスを指定します。 たとえば、列挙型に基づき、指定できます、イメージのインデックスとして保護されているメソッドの`(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`します。 必要に応じて、この列挙体の名前を変更することができます。  
  
```csharp  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [従来の言語サービスの概要](../../extensibility/internals/legacy-language-service-overview.md)   
 [従来の言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [従来の言語サービスのパーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
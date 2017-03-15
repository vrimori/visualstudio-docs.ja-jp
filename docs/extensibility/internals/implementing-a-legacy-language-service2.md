---
title: "レガシ言語 Service2 の実装 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "実装する言語サービス [マネージ パッケージ framework]"
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# 従来の言語サービスを実装します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

マネージ パッケージのフレームワーク \(MPF\) を使用する言語サービスを実行するには<xref:Microsoft.VisualStudio.Package.LanguageService> のクラスからクラスを派生させて次の抽象メソッドとプロパティを実装する必要があります :  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> メソッド  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> メソッド  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッド  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> プロパティ  
  
 これらのメソッドとプロパティの実装の詳細については該当のセクションを参照してください。  
  
 他の機能をサポートするには言語サービスは MPF の言語サービスのクラスの 1 つがからクラスを派生させる必要があります。; たとえばさらにメニュー コマンドをサポートするために<xref:Microsoft.VisualStudio.Package.ViewFilter> のクラスからクラスを派生しメソッドを処理する複数のコマンドをオーバーライドする必要があります \(詳細については <xref:Microsoft.VisualStudio.Package.ViewFilter> を参照してください。  <xref:Microsoft.VisualStudio.Package.LanguageService> のクラスはさまざまなクラスの新しいインスタンスを作成するために呼び出されるクラスのインスタンスを提供する適切なメソッドをオーバーライドして作成の一部のメソッドを提供します。  たとえば<xref:Microsoft.VisualStudio.Package.ViewFilter> の独自のクラスのインスタンスを返すように <xref:Microsoft.VisualStudio.Package.LanguageService> クラスの <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> のメソッドをオーバーライドする必要があります。  詳細については区分するカスタム クラスに 「」のインスタンス化を参照してください。  
  
 言語サービスは多くの場所で使用される独自のアイコンを指定できます。  たとえばIntelliSense コンプリート リストが表示されたら一覧の各項目は言語に必要な処理を行わなくても場合は項目を関連付けられているアイコンは名前空間クラスプロパティメソッドとしてマークします。  これらのアイコンはIntelliSense のすべてのリスト  **ナビゲーション バー**  と **エラー一覧**  のタスク ウィンドウで使用されます。  詳細については後の 「言語サービス イメージ」を参照してください。  
  
## GetLanguagePreferences のメソッド  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> のメソッドは <xref:Microsoft.VisualStudio.Package.LanguagePreferences> クラスの同じインスタンスを常に返します。  言語サービスの追加のユーザー設定が必要とする <xref:Microsoft.VisualStudio.Package.LanguagePreferences> の基本クラスを使用できます。  MPF の言語サービス クラスは少なくとも <xref:Microsoft.VisualStudio.Package.LanguagePreferences> の基本クラスが存在することを前提としています。  
  
### 例  
 この例では <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> のメソッドの一般的な実装を示しています。  この例では <xref:Microsoft.VisualStudio.Package.LanguagePreferences> の基本クラスを使用します。  
  
```c#  
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
  
## GetScanner のメソッド  
 実装がトークンおよび型およびトリガー取得する直線型のパーサーやスキャナー使用したこのメソッドは <xref:Microsoft.VisualStudio.Package.IScanner> オブジェクトのインスタンス。  このスキャナーは色づけに <xref:Microsoft.VisualStudio.Package.Colorizer> のスキャナー クラスではより複雑な解析操作にプレリュードとしてトークンの種類およびトリガーの取得に使用できるが使用されます。  <xref:Microsoft.VisualStudio.Package.IScanner> のインターフェイスを実装する <xref:Microsoft.VisualStudio.Package.IScanner> インターフェイスのすべてのメソッドを実装するクラスを指定します。  
  
### 例  
 この例では <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> のメソッドの一般的な実装を示しています。  `TestScanner` のクラスは <xref:Microsoft.VisualStudio.Package.IScanner> のインターフェイスを実装します \(表示されていません\)。  
  
```c#  
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
  
## ParseSource のメソッド  
 複数の種類の原因に基づいてソース ファイルを解析します。  このメソッドは予期されたものを特定の解析操作で説明する <xref:Microsoft.VisualStudio.Package.ParseRequest> のオブジェクトです。  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> のメソッド トークンは機能と範囲を決定する複雑なパーサーを開始します。  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> のメソッドはIntelliSense 操作またはかっこの一致機能のサポートで使用されます。  このような高度な操作をサポートしない場合でも<xref:Microsoft.VisualStudio.Package.AuthoringScope> の有効なオブジェクトを返す<xref:Microsoft.VisualStudio.Package.AuthoringScope> のインターフェイスをクラスの作成を実行する要求しそのインターフェイスのすべてのメソッドを実装します。  すべてのメソッドに null 値を返すことができます <xref:Microsoft.VisualStudio.Package.AuthoringScope> のオブジェクト自体は null にする必要があります。  
  
### 例  
 この例では言語サービスを実際にはの高度な機能をサポートせずにコンパイルして機能することを許可するために十分な <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> のメソッドと <xref:Microsoft.VisualStudio.Package.AuthoringScope> クラスの最小限の実装を示しています。  
  
```c#  
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
  
## Name プロパティ  
 このプロパティは言語サービスの名前を返します。  これは言語サービスを登録したときに指定した名前と同じである必要があります。  この名前はいくつかの場所 \(最も重要でレジストリにアクセスするには名前が使用されている <xref:Microsoft.VisualStudio.Package.LanguagePreferences> のクラスであるを使用します。  このプロパティによって返される名前はレジストリ エントリおよびキーの名前にはレジストリで使用されるたびにローカライズする必要があります。  
  
### 例  
 この例では <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> のプロパティの 1 とおりの実装を示します。  次の名前はハード コーディングされていることに注意してください : 実際の名前はリソース ファイルから取得されるため言語サービスの登録に使用することができます。[言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md) を参照してください。  
  
```c#  
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
  
## カスタム クラスのインスタンス化  
 指定したクラスのメソッドはクラスで独自のバージョンのインスタンスを提供するためにオーバーライドできます。  
  
### LanguageService のクラス  
  
|メソッド|返されるクラス|Description|  
|----------|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|カスタム テキスト ビューに追加をサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|カスタム ドキュメント プロパティをサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|**ナビゲーション バー**  をサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|コードスニペットのテンプレート関数をサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|コードスニペットをサポートします。このメソッドは通常はオーバーライドされません\)。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|<xref:Microsoft.VisualStudio.Package.ParseRequest> の構造のカスタマイズをサポートします。このメソッドは通常はオーバーライドされません\)。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|コメント文字を指定しメソッド シグネチャをカスタマイズする形式のソース・コードをサポートします。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|さらにメニュー コマンドをサポートします。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|構文の強調表示をサポートします。このメソッドは通常はオーバーライドされません\)。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|言語の優先順位へのアクセスをサポートします。  このメソッドを実装する必要があります。基本クラスのインスタンスを返すことができます。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|トークンの種類を識別するために使用されるパーサーの行に指定します。  このメソッドは実装されて <xref:Microsoft.VisualStudio.Package.IScanner> はから派生する必要があります。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|すべてのソース ファイルの機能およびスコープを識別するために使用されるパーサーを提供します。  このメソッドが実行され<xref:Microsoft.VisualStudio.Package.AuthoringScope> クラスのバージョンのインスタンスを返す必要があります。  強調表示しサポートするのが戻り値 \(<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> のメソッドから返される <xref:Microsoft.VisualStudio.Package.IScanner> パーサーを必要とする\) 構文このメソッドは何も実行しない場合は <xref:Microsoft.VisualStudio.Package.AuthoringScope> クラスのメソッドのバージョンすべての NULL 値のみの場合は。|  
  
### ソース クラス  
  
|メソッド|返されるクラス|Description|  
|----------|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|IntelliSense コンプリート リストの表示をカスタマイズする場合はこのメソッドはオーバーライドされません\)。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|エラー一覧のタスク リスト内でマーカー。; 具体的にはファイルを開きエラーが発生した行にジャンプ以外の機能のサポート。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense の \[パラメーター ヒント\] のツールヒントの表示をカスタマイズする。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|サポート コードのコメントを参照してください。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|解析操作中に関する情報を収集する。|  
  
### AuthoringScope のクラス  
  
|メソッド|返されるクラス|Description|  
|----------|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|型またはメンバーの宣言などの一覧を示します。  このメソッドを実装する必要があります。null 値を返すことができます。  このメソッドから制御が有効なオブジェクトオブジェクト <xref:Microsoft.VisualStudio.Package.Declarations> クラスのバージョンのインスタンスである必要があります。|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|特定のコンテキスト シグネチャの一覧を示します。  このメソッドを実装する必要があります。null 値を返すことができます。  このメソッドから制御が有効なオブジェクトオブジェクト <xref:Microsoft.VisualStudio.Package.Methods> クラスのバージョンのインスタンスである必要があります。|  
  
## 言語サービスのイメージ  
 言語サービスで使用するアイコンの一覧を表示するには <xref:Microsoft.VisualStudio.Package.LanguageService> クラスの <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> のメソッドをオーバーライドしアイコンを含む <xref:System.Windows.Forms.ImageList> を返します。  基本クラスの読み込み <xref:Microsoft.VisualStudio.Package.LanguageService> のアイコンの既定のセット。  アイコンが必要な場所で正確なイメージのインデックスを指定する場合はどのように配置するか独自のイメージ リストはください。  
  
### IntelliSense コンプリート リストで使用されるイメージ  
 IntelliSense コンプリート リストではイメージのインデックスはオーバーライドする必要 <xref:Microsoft.VisualStudio.Package.Declarations> クラスの <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> のメソッドで各項目のイメージのインデックスを指定する場合指定されます。  <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> のメソッドから返される値は <xref:Microsoft.VisualStudio.Package.CompletionSet> のクラス コンストラクターに指定されたイメージ リストにインデックスであり<xref:Microsoft.VisualStudio.Package.LanguageService> のクラス \(別のイメージ リストを指定するに <xref:Microsoft.VisualStudio.Package.Source> クラスの <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> のメソッドをオーバーライドする場合\) <xref:Microsoft.VisualStudio.Package.CompletionSet> に使用するイメージのリストできます <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> のメソッドから返される同じイメージ リストに変更されます。  
  
### ナビゲーション バーで使用されるイメージ  
 **ナビゲーション バー**  は型とメンバーの一覧を表示しすばやく検索のアイコンを表示できます使用されます。  これらのアイコンは <xref:Microsoft.VisualStudio.Package.LanguageService> クラスの <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> のメソッドから派生し **ナビゲーション バー**  に対してオーバーライドできません。  ComboBox の各項目に使用するインデックスはを表すリストが <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> クラスのメソッド <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> の入力時に指定されます \([従来の言語サービス内のナビゲーション バーのサポート](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) を参照してください。  これらのイメージのインデックスを <xref:Microsoft.VisualStudio.Package.Declarations> クラスのバージョンを使用してパーサーで通常把握して取得されます。  インデックスがどのようにすることも完全に設定してください。  
  
### \[エラー一覧\] ウィンドウのタスクで使用されるイメージ  
 メソッド <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> のパーサー \([従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md) を参照してください\) <xref:Microsoft.VisualStudio.Package.AuthoringSink> クラスの <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> のメソッドにエラーが  **エラー一覧**  のタスク ウィンドウでエラー報告されるエラーおよびパスが発生するたびにします。  アイコンが表示されるタスク ウィンドウのアイコンが <xref:Microsoft.VisualStudio.Package.LanguageService> クラスの <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> のメソッドから返される同じイメージ リストからダウンロードされ各項目に関連付けることができます。  MPF クラスの既定の動作ではエラー メッセージにイメージを表示できないことです。  ただしクラスを <xref:Microsoft.VisualStudio.Package.Source> のクラスから派生し<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> のメソッドをオーバーライドすることでこの動作をオーバーライドできます。  このメソッドでは<xref:Microsoft.VisualStudio.Package.DocumentTask> の新しいオブジェクトを作成します。  そのオブジェクトを返す前にイメージのインデックスを設定するに <xref:Microsoft.VisualStudio.Package.DocumentTask> のオブジェクトの <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> のプロパティを使用できます。  これは次の例のようになります。  `TestIconImageIndex` がすべてのアイコンの一覧でこの例に固有の列挙体ことに注意してください。  言語サービスのアイコンを識別するためのさまざまな方法があります。  
  
```c#  
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
            TastPriority      priority,  
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
  
## 言語サービスの既定のイメージ リスト  
 MPF ベースの言語サービス クラスに用意されている既定のイメージ リストは多くの共通言語要素に関連付けられているいくつかのアイコンが含まれています。  これらのアイコンの大部分はパブリックプロテクトプライベート内部 Friends とショートカットのアクセスの概念に対応する 6 種類の設定で配置されます。  たとえばパブリックであるかどうかまたはプライベート メソッドに対して異なるアイコンによって保護することができます。  
  
 次の列挙型では各アイコンの設定の通常の名前を指定し対応するインデックスを指定します。  たとえば列挙型に基づいて`(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` としてプロテクト メソッドのイメージのインデックスを指定できます。  必要な場所にこの列挙体の名前を変更できます。  
  
```c#  
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
  
## 参照  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [従来の言語サービスの概要](../../extensibility/internals/legacy-language-service-overview.md)   
 [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
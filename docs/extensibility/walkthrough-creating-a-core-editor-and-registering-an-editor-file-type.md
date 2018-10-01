---
title: コア エディターを作成してエディター ファイルの種類を登録する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ee391ce1200cce03e83f80b6f345ead4cd03199
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495246"
---
# <a name="walkthrough-create-a-core-editor-and-registering-an-editor-file-type"></a>チュートリアル: コア エディターとエディター ファイルの種類の登録を作成します。
このチュートリアルを開始する VSPackage を作成する方法について説明、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターでファイルがいつ、 *.myext*ファイル名拡張子が読み込まれます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio パッケージ プロジェクト テンプレートの場所  
 Visual Studio パッケージのプロジェクト テンプレートは、 **[新しいプロジェクト]** ダイアログの次の 3 つの場所にあります。  
  
1.  **Visual Basic の拡張機能**の下。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  **C# の拡張機能**の下。 プロジェクトの既定の言語は C# です。  
  
3.  **その他のプロジェクトの種類の拡張機能**の下。 プロジェクトの既定の言語は C++ です。  
  
### <a name="to-create-the-vspackage"></a>VSPackage を作成するには  
  
-   開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を作成し、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]という名前の VSPackage `MyPackage`」の説明に従って、[チュートリアル: メニュー コマンド VSPackage を作成する](https://msdn.microsoft.com/library/d699c149-5d1e-47ff-94c7-e1222af02c32)します。  
  
### <a name="to-add-the-editor-factory"></a>エディター ファクトリを追加するには  
  
1.  右クリックし、 **MyPackage**プロジェクトをポイントして、**追加**、 をクリックし、**クラス**します。  
  
2.  **新しい項目の追加** ダイアログ ボックスに、必ず、**クラス**テンプレートを選択すると、型`EditorFactory.cs`名、およびクリック**追加**をプロジェクトにクラスを追加します。  
  
     *EditorFactory.cs*ファイルが自動的に開く必要があります。  
  
3.  コードから、次のアセンブリを参照します。  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  追加するのには、GUID、`EditorFactory`クラスを追加することで、`Guid`クラス宣言の直前の属性。  
  
     使用して、新しい GUID を生成することができます、 *guidgen.exe*でプログラムを[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コマンド プロンプトでは、またはをクリックして**GUID の作成**上、**ツール**メニュー。 ここで使用される GUID はほんの一例です。プロジェクトでは使用しないでください。  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  クラスの定義では、親パッケージとサービス プロバイダーを格納するための 2 つのプライベート変数を追加します。  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  型の 1 つのパラメーターを受け取るパブリック クラスのコンス トラクターを追加<xref:Microsoft.VisualStudio.Shell.Package>:  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  変更、`EditorFactory`クラスから派生する宣言、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイス。  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  右クリック<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>、 をクリックして**インターフェイスの実装**、 をクリックし、**インターフェイスを明示的に実装**します。  
  
     この手順で実装する必要がある 4 つのメソッドを追加します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイス。  
  
9. `IVsEditorFactory.Close` メソッドの内容を次のコードに置き換えます。  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. 内容を置き換える、`IVsEditorFactory.SetSite`を次のコード。  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. `IVsEditorFactory.MapLogicalView` メソッドの内容を次のコードに置き換えます。  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. `IVsEditorFactory.CreateEditorInstance` メソッドの内容を次のコードに置き換えます。  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. プロジェクトをコンパイルし、エラーがないかどうかを確認します。  
  
### <a name="to-register-the-editor-factory"></a>エディター ファクトリを登録するには  
  
1.  **ソリューション エクスプ ローラー**をダブルクリック、 **Resources.resx**これで、文字列テーブルを開くファイルをエントリ**String1 が**選択されています。  
  
2.  識別子の名前を変更`IDS_EDITORNAME`とテキストを**MyPackage エディター。** この文字列は、エディターの名前として表示されます。  
  
3.  開く、 **VSPackage.resx**ファイル、新しい文字列を追加、名前に設定します**101**、値を設定および`IDS_EDITORNAME`します。 この手順では、作成した文字列にアクセスするリソース ID を持つパッケージを提供します。  
  
    > [!NOTE]
    >  場合、 **VSPackage.resx**ファイルを含む別の文字列を`name`属性に設定**101**では、次の手順は、別の一意の数値の値を置き換えてください。  
  
4.  **ソリューション エクスプ ローラー**、オープン、 **MyPackagePackage.cs**ファイル。  
  
     このファイルは、メイン パッケージ ファイルです。  
  
5.  直前に次のユーザー属性を追加、`Guid`属性。  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>属性に関連付け、 *.myext*ファイル エディター ファクトリは、拡張機能にいつでも拡張機能が読み込まれる、エディター ファクトリが呼び出されることを持つファイル。  
  
6.  プライベート変数の追加、 `MyPackage` 、コンス トラクターの直前に、クラスし、型を付けます`EditorFactory`します。  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7.  検索、`Initialize`メソッド (を開く必要があります、`Package Members`非表示の領域) を呼び出した後、次のコードを追加および`base.Initialize()`します。  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  プログラムをコンパイルして、エラーがないかどうかを確認します。  
  
     この手順の実験用のレジストリ ハイブでエディター ファクトリを登録します[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 オーバーライドするメッセージが表示されたら、 *resource.h*ファイルで、をクリックして**OK**します。  
  
9. という名前のサンプル ファイルを作成する*TextFile1.myext*します。  
  
10. キーを押して**F5**の実験用インスタンスを開く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
11. 実験用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]の**ファイル**メニューで、**オープン**順にクリックします**ファイル**します。  
  
12. 検索**TextFile1.myext**  をクリックし、**オープン**します。  
  
     ファイルを読み込むようになりました必要があります。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のコア エディターがさまざまな構文の強調表示、かっこの一致、および IntelliSense の単語補完などの機能の豊富なセットを提供するには、テキスト ベースのファイルの種類と言語サービスと密接に連携を処理し、メンバー入力候補が一覧表示されます。 テキスト ベースのファイルを使用すると、特定のファイルの種類をサポートするカスタムの言語サービスのコア エディターを使用することができます。  
  
 VSPackage が呼び出すことができます、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディター ファクトリを指定することによって、コア エディター。 このエディターのファクトリは、それに関連付けられているファイルが読み込まれるたびに使用されます。 ファイルがプロジェクトの一部である場合は、VSPackage によってオーバーライドされない限り、コア エディターが自動的に起動します。 ただし、プロジェクトの外側で、ファイルを読み込んだ場合、コア エディターする必要があります明示的に呼び出す、VSPackage によって。  
  
 コア エディターの詳細については、次を参照してください。[コア エディター内で](../extensibility/inside-the-core-editor.md)します。  
  
## <a name="see-also"></a>関連項目  
 [コア エディター](../extensibility/inside-the-core-editor.md)   
 [従来の API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
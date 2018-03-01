---
title: "コア エディターを作成して、エディター ファイルの種類を登録する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ace475cb94920a5c0470c1d16265349edfa441f4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>チュートリアル: コア エディターを作成して、エディター ファイルの種類を登録します。
このチュートリアルを開始する VSPackage を作成する方法を示しています、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターと .myext ファイル名拡張子を持つファイルが読み込まれています。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio パッケージ プロジェクト テンプレートの場所  
 Visual Studio パッケージのプロジェクト テンプレートは、 **[新しいプロジェクト]** ダイアログの次の 3 つの場所にあります。  
  
1.  Visual Basic の機能拡張の下。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  C# の機能拡張の下。 プロジェクトの既定の言語は C# です。  
  
3.  その他のプロジェクトの種類の機能拡張の下。 プロジェクトの既定の言語は C++ です。  
  
### <a name="to-create-the-vspackage"></a>VSPackage を作成するには  
  
-   開始[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を作成し、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]いう名前の VSPackage `MyPackage`」の説明に従って、[チュートリアル: メニュー コマンドの VSPackage を作成する](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32)です。  
  
### <a name="to-add-the-editor-factory"></a>エディター ファクトリを追加するには  
  
1.  右クリックし、 **MyPackage**プロジェクトをポイントし、**追加** をクリックし、**クラス**です。  
  
2.  **新しい項目の追加** ダイアログ ボックスで確認、**クラス**テンプレートが選択されている型`EditorFactory.cs` をクリックし、名前の**追加**をプロジェクトにクラスを追加します。  
  
     EditorFactory.cs ファイルを自動的に開く必要があります。  
  
3.  コードから次のアセンブリを参照します。  
  
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
  
4.  GUID の追加、`EditorFactory`クラスを追加して、`Guid`クラス宣言の直前の属性です。  
  
     Guidgen.exe プログラムを使用して、新しい GUID を生成することができます、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コマンド プロンプトでは、やをクリックして**GUID の作成**上、**ツール**メニュー。 ここで使用される GUID は一例です。プロジェクトでは使用しないでください。  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  クラス定義では、親パッケージと、サービス プロバイダーを格納する 2 つのプライベート変数を追加します。  
  
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
  
7.  変更、`EditorFactory`クラスから派生する宣言、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイスです。  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  右クリック<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>をクリックして**インターフェイスの実装**、順にクリック**インターフェイスを明示的に実装**です。  
  
     これにより、追加で実装する必要がある 4 つのメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイスです。  
  
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
  
1.  **ソリューション エクスプ ローラー**、Resources.resx ファイルを文字列テーブルを開くことをダブルクリックしてエントリ**String1 が**選択します。  
  
2.  識別子の名前を変更`IDS_EDITORNAME`および**MyPackage エディターです。** この文字列は、エディターの名前として表示されます。  
  
3.  VSPackage.resx ファイルを開き、新しい追加文字列の名前を設定します**101**し、値を`IDS_EDITORNAME`です。 これは、作成した文字列にアクセスするリソース ID を持つパッケージを提供します。  
  
    > [!NOTE]
    >  場合は、VSPackage.resx ファイルが含まれる別の文字列を`name`属性に設定**101**、セクションと、次の手順では、別の一意の数値の値を置き換えます。  
  
4.  **ソリューション エクスプ ローラー**、MyPackagePackage.cs ファイルを開きます。  
  
     これは、メイン パッケージ ファイルです。  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>属性関連付けます .myext ファイル拡張子、エディター ファクトリを拡張機能が読み込まれ、エディター ファクトリが呼び出されるを持つファイルをいつでもできるようにします。  
  
6.  プライベート変数の追加、`MyPackage`クラス、コンス トラクターの直前にし、型を付けます`EditorFactory`です。  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7.  検索、`Initialize`メソッド (を開く必要があります、`Package Members`非表示の領域) を呼び出した後、次のコードを追加および`base.Initialize()`です。  
  
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
  
     この手順では、エディター ファクトリを登録の実験用レジストリ ハイブ[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 Resource.h ファイルを上書きするメッセージが表示されたら、クリックして**OK**です。  
  
9. TextFile1.myext をという名前のサンプル ファイルを作成します。  
  
10. キーを押して**f5 キーを押して**の実験用インスタンスを開く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
11. 実験用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]の**ファイル** メニューのをポイント**開く** をクリックし、**ファイル**です。  
  
12. TextFile1.myext を見つけてクリックして**開く**です。  
  
     ファイルを読み込むようになりました。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターは、さまざまなテキスト ベースのファイルの種類とかっこの照合、構文の強調表示などの機能の豊富なセットを提供する言語サービスと IntelliSense の単語補完とメンバー完了リストと密接に連携を処理します。 テキスト ベースのファイルで作業している場合、特定のファイルの種類をサポートするカスタム言語サービスと共にコア エディターを使用できます。  
  
 VSPackage が呼び出すことができます、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディター ファクトリを指定することによってコア エディターです。 このエディター ファクトリはそれに関連付けられているファイルが読み込まれるたびに使用します。 ファイルがプロジェクトの一部である場合は、コア エディターが自動的に呼び出され、VSPackage によってオーバーライドされない限り、します。 ただし、ファイルがプロジェクトの外側で読み込まれている場合、コア エディター必要があります明示的に呼び出す、VSPackage によってです。  
  
 コア エディターの詳細については、次を参照してください。 [、コア エディター内](../extensibility/inside-the-core-editor.md)です。  
  
## <a name="see-also"></a>参照  
 [コア エディター内](../extensibility/inside-the-core-editor.md)   
 [レガシ API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
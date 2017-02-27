---
title: "方法: エディター ファイルの種類の登録 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] の従来のファイルの種類を登録します。"
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 方法: エディター ファイルの種類の登録
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターでファイルの種類を登録する最も簡単な方法は[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] のマネージ パッケージ フレームワーク \(MPF\) クラスの一部として指定されたレジスタの属性を使用します。  ネイティブ [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] パッケージを実行する場合エディターと関連付けられた拡張子を登録するレジストリ スクリプトを記述できます。  
  
## MPF のクラスを使用して登録  
  
#### エディターでファイルの種類を MPF のクラスを使用して登録するには  
  
1.  VSPackage のクラスのエディター適切なパラメーターを <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> のクラスに指定します。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     「 where。この例では」エディター用に登録し「 32 " は優先順位が拡張機能です。  
  
     `projectGuid` は <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject> で定義されているそのほかのファイルの種類の GUID です。  そのほかの種類のファイルは生成されたファイルはビルド処理の一部であることを実行しないように提供されます。  
  
     `TemplateDir` はマネージ基本的なエディターの例に含まれているテンプレート ファイルを含むフォルダーを表します。  
  
     `NameResourceID` は BasicEditorUI プロジェクトの Resources.h ファイルで定義され「 My 」エディターとしてエディターを指定します。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> メソッドをオーバーライドします。  
  
     <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> のメソッドの実装では<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> のメソッドを呼び出して以下に示すようにエディターのファクトリのインスタンスを渡します。  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     この手順ではエディターのファクトリとエディターでファイル拡張子の両方を登録します。  
  
3.  エディターのファクトリの登録を解除します。  
  
     エディターのファクトリは自動的に VSPackage が破棄されるときに登録が解除されます。  エディターのファクトリ オブジェクトが <xref:System.IDisposable> のインターフェイスを実装する場合は`Dispose` のはファクトリ メソッドが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に登録解除された後に呼び出されます。  
  
## レジストリ スクリプトを使用して登録  
 ネイティブ [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] エディターのファクトリとファイルの種類を登録するにはレジストリ スクリプトを使用すると次に示すようにウィンドウにレジストリを作成するためです。  
  
#### レジストリ エディターを使用してのファイルの種類を登録するにはスクリプトを作成します  
  
1.  レジストリ スクリプトでは次のレジストリ スクリプトの `GUID_BscEditorFactory` のセクションで説明したエディターのファクトリとエディターのファクトリの GUID 文字列を定義します。  またエディター拡張子の拡張や優先順位の定義 :  
  
    ```  
  
                NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions             {                 val rtf = d 50             }  
        }  
    }  
    ```  
  
     この例のエディターの .rtf ファイル拡張子は 「」および優先度が 「 50 " であるとして識別されます。  GUID 文字列は BscEdit サンプル プロジェクトの Resource.h ファイルで定義されます。  
  
2.  VSPackage を登録します。  
  
3.  エディターのファクトリを登録します。  
  
     エディターのファクトリは <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> の実装に登録されます。  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     GUID 文字列は BscEdit プロジェクトの Resource.h ファイルで定義されます。
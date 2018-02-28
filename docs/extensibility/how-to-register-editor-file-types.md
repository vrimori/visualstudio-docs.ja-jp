---
title: "方法: エディター ファイルの種類の登録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 679223f21bd839a8d94b299319ad22c6701bc407
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-editor-file-types"></a>方法: エディター ファイルの種類の登録
エディターのファイルの種類を登録する最も簡単な方法は、の一部として定義されている登録属性を使用して、 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] managed package framework (MPF) クラス。 ネイティブに、パッケージを実装する場合は[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]エディターと関連付けられている拡張機能を登録するレジストリ スクリプトを記述することもできます。  
  
## <a name="registration-using-mpf-classes"></a>MPF クラスを使用して登録  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>MPF クラスを使用するエディター ファイルの種類を登録するには  
  
1.  提供、 <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> VSPackage のクラスで、エディターの適切なパラメーターを持つクラス。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     ここで"です。サンプル"は、このエディターに対して登録されている拡張機能と、「32」が、優先順位。  
  
     `projectGuid`で定義されているその他のファイルの種類の guid<xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>です。 その他のファイルの種類が提供されるため、結果として得られるファイルは、ビルド プロセスの一部であるしません。  
  
     `TemplateDir`管理対象の基本的なエディターのサンプルに含まれているテンプレート ファイルを含むフォルダーを表します。  
  
     `NameResourceID`BasicEditorUI プロジェクトの Resources.h ファイルで定義し、「My エディター」としてエディターを識別します。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> メソッドをオーバーライドします。  
  
     実装で、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッドを呼び出し、<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>メソッドおよびパスとして、エディター ファクトリのインスタンスを以下に示します。  
  
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
  
     このステップでは、エディター ファクトリとエディター ファイルの拡張機能の両方を登録します。  
  
3.  エディター ファクトリの登録を解除します。  
  
     VSPackage が破棄されるときにエディター ファクトリは自動的に登録を解除します。 エディター ファクトリ オブジェクトを実装する場合、<xref:System.IDisposable>インターフェイス、その`Dispose`メソッドが呼び出されると、ファクトリが登録解除されて[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="registration-using-a-registry-script"></a>レジストリ スクリプトを使用して登録  
 エディター ファクトリおよびファイルの種類のネイティブ登録[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]はで、次に示すように、windows レジストリに書き込むレジストリ スクリプトを使用しています。  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>レジストリ スクリプトを使用してエディター ファイルの種類を登録するには  
  
1.  レジストリ スクリプト エディター ファクトリおよび定義エディター ファクトリ GUID 文字列で示すように、`GUID_BscEditorFactory`次のレジストリ スクリプトのセクションでします。 また、拡張機能およびエディター拡張機能の優先度を定義します。  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     この例では、エディターのファイル拡張子は".rtf"として識別され、その優先度が「50」です。 GUID の文字列は、Resource.h ファイル BscEdit サンプル プロジェクトで定義されます。  
  
2.  VSPackage を登録します。  
  
3.  エディター ファクトリを登録します。  
  
     エディター ファクトリが登録されている、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>実装します。  
  
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
  
     GUID の文字列は、Resource.h ファイルの BscEdit プロジェクトで定義されます。
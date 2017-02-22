---
title: "プロジェクト オブジェクトを公開します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "公開するプロジェクト オブジェクト"
  - "プロジェクトのオブジェクトの機能拡張"
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクト オブジェクトを公開します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

カスタムのプロジェクトの種類は、オートメーション インターフェイスを使用して、プロジェクトにアクセスできるようにするために、オートメーション オブジェクトを提供できます。 全種類のプロジェクトは、標準を提供する必要 <xref:EnvDTE.Project> からアクセスされるオートメーション オブジェクト <xref:EnvDTE.Solution>, 、IDE で開かれているすべてのプロジェクトのコレクションを格納します。 によって公開される、プロジェクト内の各項目が期待どおり、 <xref:EnvDTE.ProjectItem> オブジェクトを使用してアクセス <xref:Project.ProjectItems>します。 これらの標準的なオートメーション オブジェクトだけでなくプロジェクト固有のオートメーション オブジェクトを提供する、プロジェクトを選択できます。  
  
 オブジェクトを作成できるカスタムの自動化をルート レベル アクセスできるルート DTE オブジェクトを使用して、遅延バインディング `DTE.<customeObjectName>` または `DTE.GetObject(“<customObjectName>”)`です。 たとえば、Visual C では、DTE を使用してアクセスできる"VCProjects"と呼ばれる C\+\+ プロジェクトに固有のプロジェクト コレクションを作成します。VCProjects または DTE します。GetObject\("VCProjects"\) します。 プロジェクトの種類の ProjectItem ProjectItem.Object と、ProjectItem.FileCodeModel を公開するのに最も多く派生のオブジェクトに対してクエリを行うことができる Project.CodeModel 一意となる、Project.Object を作成することもできます。  
  
 それは、プロジェクト、プロジェクト固有のカスタムのプロジェクト コレクションを公開する一般的な規則です。 たとえば、 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] を使用してアクセスすることができますし、C\+\+ の特定のプロジェクト コレクションを作成 `DTE.VCProjects` または `DTE.GetObject("VCProjects")`です。 作成することも、 `Project.Object`, 、プロジェクトの種類に対して一意である、 `Project.CodeModel`, がその最派生オブジェクトに対してクエリを行うことができます、 `ProjectItem`, を公開 `ProjectItem.Object`, 、および `ProjectItem.FileCodeModel`します。  
  
### プロジェクトの VSPackage に固有のオブジェクトを投稿するには  
  
1.  適切なキーを VSPackage の .pkgdef ファイルに追加します。  
  
     たとえば、ここでは C 言語プロジェクト .pkgdef 設定です。  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation] "VCProjects"="" [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents] "VCProjectEngineEventsObject"=""  
    ```  
  
2.  内のコードを実装する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> メソッドを次の例に示すようにします。  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject( /* [in]  */ LPCOLESTR       pszPropName, /* [out] */ IDispatch **    ppIDispatch) { ExpectedPtrRet(pszPropName); ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (m_fZombie) return E_UNEXPECTED; if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0) { return GetAutomationProjects(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } return E_INVALIDARG; }   
    ```  
  
     コードでは、 `g_wszAutomationProjects` 、プロジェクト コレクションの名前を指定します。`GetAutomationProjects` メソッドを実装するオブジェクトを作成、 `Projects` インターフェイスを返す、 `IDispatch` 次のコード例に示すように、呼び出し元のオブジェクトへのポインター。  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch) { ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (!m_srpAutomationProjects) { HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects); IfFailRet(hr); ExpectedExprRet(m_srpAutomationProjects != NULL); } return m_srpAutomationProjects.CopyTo(ppIDispatch); }  
    ```  
  
     オートメーション オブジェクトの一意の名前を選択してください。 名前の競合が予測可能なではなく、競合が発生する場合は、複数のプロジェクトの種類が同じ名前を使用して任意にスローされる競合しているオブジェクト名。 会社名、またはオートメーション オブジェクトの名前には、その製品名の一部の一意な側面を含める必要があります。  
  
     カスタム `Projects` コレクション オブジェクトは、プロジェクト オートメーション モデルの残りの部分のための便利なエントリ ポイントです。 プロジェクト オブジェクトはからもアクセス、 <xref:EnvDTE.Solution> プロジェクト コレクション。 コンシューマーを提供する適切なコードやレジストリ エントリを作成した後 `Projects` コレクション オブジェクトの場合、残りのプロジェクト モデルの標準的なオブジェクトの実装が提供する必要があります。 詳細については、「[プロジェクトのモデリング](../../extensibility/internals/project-modeling.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
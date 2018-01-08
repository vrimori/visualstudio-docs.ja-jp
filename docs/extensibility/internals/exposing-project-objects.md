---
title: "プロジェクト オブジェクトを公開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 668287dc8b0b5ac9dd37cb450582e3a56fb7f25e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-project-objects"></a>プロジェクト オブジェクトを公開します。
カスタム プロジェクトの種類は、オートメーション インターフェイスを使用してプロジェクトへのアクセスを許可するために、オートメーション オブジェクトを提供できます。 標準を提供するすべてのプロジェクトの種類が期待どおり<xref:EnvDTE.Project>からアクセスされるオートメーション オブジェクト<xref:EnvDTE.Solution>IDE で開かれているすべてのプロジェクトのコレクションを含むです。 プロジェクト内の各項目をによって公開されると予想される、<xref:EnvDTE.ProjectItem>オブジェクトを使用してアクセス`Project.ProjectItems`です。 これらの標準的なオートメーション オブジェクトだけでなくプロジェクト固有のオートメーション オブジェクトを提供する、プロジェクトを選択できます。  
  
 カスタム ルートレベルのオートメーション オブジェクトにアクセスできる、DTE オブジェクトを使用したルートからの遅延バインディングを作成する`DTE.<customeObjectName>`または`DTE.GetObject("<customObjectName>")`です。 たとえば、Visual C では、DTE を使用してアクセスできる"VCProjects"と呼ばれる C++ プロジェクトに固有のプロジェクト コレクションを作成します。VCProjects または DTE します。GetObject("VCProjects") です。 Project.Object では、一意で、プロジェクトの種類、Project.CodeModel では、その最派生オブジェクトを ProjectItem、ProjectItem.Object と、ProjectItem.FileCodeModel を公開するためにクエリできるは、作成することもできます。  
  
 これは、プロジェクト、プロジェクト固有のカスタムのプロジェクト コレクションを公開する一般的な規則です。 たとえば、[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]を使用し、アクセスできる C++ の特定のプロジェクト コレクションを作成`DTE.VCProjects`または`DTE.GetObject("VCProjects")`です。 作成することも、 `Project.Object`、これは、プロジェクトの種類に対して一意で、`Project.CodeModel`がその最派生オブジェクトのクエリを実行できます、`ProjectItem`を公開`ProjectItem.Object`、および`ProjectItem.FileCodeModel`です。  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>プロジェクトの VSPackage に固有のオブジェクトを投稿するには  
  
1.  VSPackage の .pkgdef ファイルに適切なキーを追加します。  
  
     たとえば、C 言語プロジェクトの .pkgdef 設定を次に示します。  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  内のコードを実装する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッドは、次の例に示すようにします。  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     コードでは、`g_wszAutomationProjects`プロジェクト コレクションの名前を指定します。 `GetAutomationProjects`メソッドを実装するオブジェクトを作成、`Projects`インターフェイスを返す、`IDispatch`次のコード例に示すように、呼び出し元のオブジェクトへのポインター。  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     オートメーション オブジェクトの一意の名前を選択する必要があります。 競合が発生する場合は、複数のプロジェクトの種類が同じ名前を使用して任意にスローされる競合するオブジェクト名と名前の競合は、予測可能ではありません。 会社名またはオートメーション オブジェクトの名前、製品名の一部の一意な側面を含める必要があります。  
  
     カスタム`Projects`コレクション オブジェクトは、プロジェクトのオートメーション モデルの残りの部分の利便性のためのエントリ ポイントです。 プロジェクトのオブジェクトはからアクセスも、<xref:EnvDTE.Solution>プロジェクト コレクションです。 コンシューマーを提供する適切なコードとレジストリ エントリを作成した後`Projects`オブジェクト コレクションを実装が残りのプロジェクトのモデルの標準的なオブジェクトを提供する必要があります。 詳細については、次を参照してください。[プロジェクトがモデリング](../../extensibility/internals/project-modeling.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
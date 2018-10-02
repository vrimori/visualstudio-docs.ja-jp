---
title: プロジェクト オブジェクトを公開する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5514589660df1850dc2f5d9fce3079f6769ec06e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533493"
---
# <a name="exposing-project-objects"></a>プロジェクト オブジェクトの公開
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロジェクト オブジェクトを公開する](https://docs.microsoft.com/visualstudio/extensibility/internals/exposing-project-objects)します。  
  
カスタム プロジェクトの種類は、オートメーション インターフェイスを使用して、プロジェクトにアクセスできるようにするには、オートメーション オブジェクトを提供できます。 すべてのプロジェクトの種類は、標準を提供する必要が<xref:EnvDTE.Project>からアクセスされるオートメーション オブジェクト<xref:EnvDTE.Solution>IDE で開いているすべてのプロジェクトのコレクションを含むです。 によって公開される、プロジェクト内の各項目が必要です、<xref:EnvDTE.ProjectItem>オブジェクトを使用してアクセス<xref:EnvDTE.Project.ProjectItems>します。 これらの標準的なオートメーション オブジェクトだけでなくプロジェクト固有のオートメーション オブジェクトを提供するプロジェクトを選択できます。  
  
 オブジェクトを作成できるカスタム ルート レベルの自動化アクセスできる使用してルート DTE オブジェクトから遅延バインディング`DTE.<customeObjectName>`または`DTE.GetObject(“<customObjectName>”)`します。 たとえば、Visual C は、DTE を使用してアクセスできる"VCProjects"と呼ばれる C++ プロジェクトに固有のプロジェクト コレクションを作成します。VCProjects または DTE します。GetObject("VCProjects") します。 、プロジェクトの種類、ProjectItem、ProjectItem.Object と、ProjectItem.FileCodeModel を公開するのに最も多く派生のオブジェクトのクエリを実行できる Project.CodeModel、一意である、Project.Object を作成することもできます。  
  
 カスタムのプロジェクトに固有のプロジェクト コレクションを公開するプロジェクトの一般的な規則になります。 たとえば、[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]を使用して、アクセス可能な C++ の特定のプロジェクト コレクションを作成します。`DTE.VCProjects`または`DTE.GetObject("VCProjects")`します。 作成することもできます、 `Project.Object`、プロジェクトの種類に対して一意である、 `Project.CodeModel`、その最派生オブジェクトを照会できる、 `ProjectItem`、公開する`ProjectItem.Object`と`ProjectItem.FileCodeModel`します。  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>プロジェクトの VSPackage に固有のオブジェクトを投稿するには  
  
1.  VSPackage の .pkgdef ファイルに適切なキーを追加します。  
  
     たとえば、C++ 言語のプロジェクトの .pkgdef 設定次に示します。  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  コードでは、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>メソッドは、次の例のようにします。  
  
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
  
     コードでは、`g_wszAutomationProjects`プロジェクト コレクションの名前を指定します。 `GetAutomationProjects`メソッドを実装するオブジェクトを作成、`Projects`インターフェイスを返します、`IDispatch`に次のコード例に示すように、呼び出し元のオブジェクトへのポインター。  
  
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
  
     オートメーション オブジェクトの一意の名前を選択する必要があります。 名前の競合が予測可能なではなく、競合が発生する場合は、同じ名前を使用して、複数のプロジェクトの種類任意にスローされる競合するオブジェクト名。 会社名またはオートメーション オブジェクトの名前には、その製品名の一部の一意の側面を含める必要があります。  
  
     カスタム`Projects`コレクション オブジェクトは、プロジェクト オートメーション モデルの残りの部分の利便性のためのエントリ ポイント。 プロジェクト オブジェクトがからアクセスできることも、<xref:EnvDTE.Solution>プロジェクト コレクション。 コンシューマーに提供する適切なコードとレジストリ エントリを作成した後`Projects`コレクション オブジェクトの場合、残りのプロジェクト モデルの標準的なオブジェクトの実装が提供する必要があります。 詳細については、次を参照してください。[プロジェクトのモデリング](../../extensibility/internals/project-modeling.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>


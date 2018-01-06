---
title: "プロジェクトのサブタイプの初期化シーケンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: db259b7bc5f9935b229f4f6522ae14a4496f0e15
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="initialization-sequence-of-project-subtypes"></a>プロジェクトのサブタイプの初期化シーケンス
環境の基本プロジェクト ファクトリの実装を呼び出すことによって、プロジェクトを構築する<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>です。 環境では、プロジェクト ファイルの拡張子のプロジェクト型 GUID の一覧が空でないことが判断した場合のプロジェクト サブタイプの構築を開始します。 プロジェクト ファイルの拡張子とプロジェクト GUID を指定するかどうか、プロジェクト、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]または[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]プロジェクトの種類。 .Vbproj ファイルの拡張機能など、{F184B08F-C81C-45F6-A57F-5ABD9991F28F} を識別し、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクト。  
  
## <a name="environments-initialization-of-project-subtypes"></a>プロジェクトのサブタイプの環境の初期化  
 次の手順では、複数のプロジェクト サブタイプごとに集計されたプロジェクト システムの初期化順序について説明します。  
  
1.  環境は、基本プロジェクトを呼び出します<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>、集計のプロジェクトの種類の Guid のリストがないことが検出されたプロジェクトは、そのプロジェクト ファイルを解析中に`null`です。 プロジェクトでは、直接そのプロジェクトの作成を停止します。  
  
2.  プロジェクトの呼び出し`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>の環境の実装を使用してプロジェクトのサブタイプを作成するサービスを<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>メソッドです。 このメソッド内で、環境での実装を再帰的な関数呼び出しが行わ<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>、`M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)`と<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>メソッドは、プロジェクトは、リスト中に、最も外側にあるプロジェクトのサブタイプで始まる Guid の型します。  
  
     次の例は、初期化手順を詳しく説明します。  
  
    1.  環境の実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>メソッドの呼び出し 'HrCreateInnerProj' ' 次の関数の宣言とメソッド。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         この関数が呼び出されたとき、最初には、最も外側のプロジェクト サブタイプのパラメーター`pOuter`と`pOwner`として渡された`null`関数は、最も外側にあるプロジェクトのサブタイプを設定および`IUnknown`に`pOuter`です。  
  
    2.  次に、環境を呼び出す`HrCreateInnerProj`一覧に 2 つ目のプロジェクト タイプ GUID を持つ関数です。 この GUID での集計のシーケンスの基本プロジェクトに向かってステップ実行 2 つ目の内部のプロジェクト サブタイプに対応しています。  
  
    3.  `pOuter`を指すようになりましたが、`IUnknown`の最も外側のプロジェクト サブタイプのおよび`HrCreateInnerProj`の実装を呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>の実装への呼び出しを続けて<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>です。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>制御を渡すメソッド`IUnknown`の最も外側のプロジェクト サブタイプの`pOuter`します。 所有されているプロジェクト (内部プロジェクトのサブタイプ) では、ここに、その集計プロジェクト オブジェクトを作成する必要があります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>メソッドの実装へのポインターを渡す、`IUnknown`集計されている内部のプロジェクトのです。 これら 2 つの方法が集約オブジェクトを作成し、実装をそれ自体に参照カウントを保持するプロジェクトのサブタイプが終わらないことを確認する COM 集計規則に従う必要があります。  
  
    4.  `HrCreateInnerProj`実装を呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>です。 このメソッドでは、プロジェクトのサブタイプは、初期化作業を行います。 ソリューションのイベントを登録することができます、たとえば、<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>です。  
  
    5.  `HrCreateInnerProj`リスト内の最後 GUID (基本プロジェクト) に到達するまで再帰的に呼び出されます。 これらの呼び出しごとに、c、d から手順が繰り返されます。 `pOuter`最も外側にあるプロジェクトのサブタイプを指す`IUnknown`集計の各レベル。  
  
 次の例のおおよその表記でプログラムによるプロセスの詳細、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>メソッドは、環境によって実装されます。 コードは単なる例です。コンパイルするものではありませんし、わかりやすくするために削除されたすべてのエラー チェックします。  
  
## <a name="example"></a>例  
  
### <a name="code"></a>コード  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)
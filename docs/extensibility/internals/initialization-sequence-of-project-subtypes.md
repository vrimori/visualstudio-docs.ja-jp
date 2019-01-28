---
title: プロジェクト サブタイプの初期化シーケンス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18a60e5589671101471bbb5f82877ce5234215d8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920190"
---
# <a name="initialization-sequence-of-project-subtypes"></a>プロジェクト サブタイプの初期化シーケンス
環境の基本プロジェクト ファクトリの実装を呼び出すことでプロジェクトを構築する<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>します。 環境では、プロジェクト ファイルの拡張子のプロジェクト型 GUID の一覧が空でないことが判断した場合、プロジェクトのサブタイプの構築が開始されます。 プロジェクト ファイルの拡張子とプロジェクト GUID を指定するかどうか、プロジェクトを[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]または[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]プロジェクトの種類。 拡張子 .vbproj などと {F184B08F-C81C-45F6-A57F-5ABD9991F28F} 識別、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクト。

## <a name="environments-initialization-of-project-subtypes"></a>プロジェクト サブタイプの環境の初期化
 次の手順では、複数のプロジェクト サブタイプごとに集計されたプロジェクト システムの初期化順序について説明します。

1.  環境が、基本プロジェクトを呼び出します<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>、集約プロジェクト型 Guid のリストがないことが検出されたプロジェクトは、そのプロジェクト ファイルを解析中に`null`します。 プロジェクトでは、直接そのプロジェクトの作成は中止します。

2.  プロジェクト呼び出し`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>の環境の実装を使用してプロジェクト サブタイプを作成するサービス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>メソッド。 このメソッド内では、環境、再帰関数呼び出しの実装を<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>プロジェクトは、リスト中は、メソッドは最も外側にあるプロジェクトのサブタイプで始まる Guid を入力します。

     次に、初期化の手順について説明します。

    1.  環境の実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>メソッドの呼び出し、`HrCreateInnerProj`メソッドと次の関数宣言。

         <CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         この関数が呼び出されたとき、最初に、最も外側にあるプロジェクトのサブタイプのパラメーター`pOuter`と`pOwner`として渡される`null`関数は、最も外側のプロジェクト サブタイプの設定と`IUnknown`に`pOuter`します。

    2.  次に、環境を呼び出す`HrCreateInnerProj`リストの 2 つ目のプロジェクト型 GUID を持つ関数です。 この GUID は、集計順番ベースのプロジェクトへステップ実行 2 つ目の内部プロジェクト サブタイプに対応します。

    3.  `pOuter`が現在指して、`IUnknown`の最も外側のプロジェクト サブタイプ、および`HrCreateInnerProj`の実装を呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>の実装への呼び出し後に<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>制御を渡すメソッド`IUnknown`最も外側にあるプロジェクトのサブタイプの`pOuter`します。 所有プロジェクト (内部のプロジェクト サブタイプ) は、ここで、その集計プロジェクト オブジェクトを作成する必要があります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>メソッドの実装へのポインターを渡す、`IUnknown`集計される内部のプロジェクトの。 これら 2 つのメソッドは、集約オブジェクトを作成し、実装は、プロジェクトのサブタイプは、自体への参照カウントを保持しているは終了しないようにする COM 集計の規則に従う必要があります。

    4.  `HrCreateInnerProj` 実装を呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>します。 このメソッドは、プロジェクトのサブタイプはその初期化作業を行います。 ソリューションのイベントを登録することができます、たとえば、<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>します。

    5.  `HrCreateInnerProj` 一覧で最後の GUID (ベースのプロジェクト) に達するまで再帰的に呼び出されます。 これらの呼び出しごとに、c、d から手順が繰り返されます。 `pOuter` 最も外側にあるプロジェクトのサブタイプが指す`IUnknown`集計の各レベル。

## <a name="example"></a>例

次の例のおおよその表記でプログラムによるプロセスの詳細、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>メソッドとして、環境によって実装されます。 コードはほんの一例です。コンパイルするものではありませんし、わかりやすくするために削除されたすべてのエラー チェックします。

```cpp
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

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)
---
title: "プロジェクトのサブタイプの初期化シーケンス | Microsoft Docs"
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
  - "プロジェクトのサブタイプで初期化シーケンス"
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトのサブタイプの初期化シーケンス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

環境は <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>Foundation プロジェクト ファクトリの実装を呼び出してプロジェクトを作成します。  プロジェクト ファイルの拡張機能用のプロジェクト タイプの GUID の一覧が空でないと環境を判断するときにプロジェクトのサブタイプのコンストラクターを指定します。  プロジェクト ファイルの拡張子とプロジェクトの GUID はプロジェクトが [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] または  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] のプロジェクトの種類であるかどうかを指定します。  たとえば.vbproj 拡張子は F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F {} [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] プロジェクトを特定します。  
  
## 環境のプロジェクトのサブタイプの初期化  
 次の手順はプロジェクトのサブタイプから集計するプロジェクト システムの初期化処理の順序について詳しく説明します。  
  
1.  環境は集計の種類のプロジェクト GUID の一覧が `null` ではないことをプロジェクトにはプロジェクト ファイルを解析するとき基本プロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> を呼び出して検出します。  プロジェクトを直接プロジェクトの作成を停止します。  
  
2.  プロジェクトでは環境の <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> のメソッドの実装を使用してプロジェクトのサブタイプを作成するに <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> サービスの `QueryService` を呼び出します。  このメソッド内で環境 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> は`M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` と <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> のメソッドの実装の一番外側のプロジェクトのサブタイプからリスト プロジェクトの GUID 歩いて中に再帰関数の呼び出しが行われます。  
  
     次の事項の初期化手順。  
  
    1.  環境の次の関数宣言が含まれる <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> のメソッド呼び出しの `HrCreateInnerProj``` のメソッド実装 :  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         この関数が最も外側のプロジェクトのサブタイプの場合つまり初めて呼び出されたときにパラメーター `pOuter` と `pOwner` は `pOuter` に `null` と関数のセットとして最も外側のプロジェクトのサブタイプ `IUnknown` 渡されます。  
  
    2.  次にリストの 2 番目の種類のプロジェクトの GUID の呼び出しの `HrCreateInnerProj` の関数。  この GUID は集計のシーケンスの基本プロジェクトに向かって実行する 2 番目の内部のプロジェクトのサブタイプに対応します。  
  
    3.  `pOuter` は最も外側のプロジェクトのサブタイプの `IUnknown` にポイントして<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> の実装が <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> の実装を呼び出すことで実行 `HrCreateInnerProj` を呼び出します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> のメソッドで最も外側のプロジェクトのサブタイプ制御 `IUnknown``pOuter` を渡します。  集約プロジェクトのオブジェクトを所有するここで作成されたプロジェクト \(内側のプロジェクトのサブタイプ\) 必要があります。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> のメソッドの実装で集計される内部のプロジェクトの `IUnknown` へのポインターに渡されます。  この二つのメソッドは集約オブジェクトを作成し実装はプロジェクトのサブタイプを終了することを確認する COM の集計の規則に従う必要があります。それ自体に参照カウントを保持します。  
  
    4.  `HrCreateInnerProj` は <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> の実装を呼び出します。  このメソッドではプロジェクトのサブタイプは作業を初期化します。  たとえば<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> ソリューションのイベントを登録できます。  
  
    5.  `HrCreateInnerProj` はリストの最後の GUID \(基本プロジェクト\) に到達するまで再帰的に呼び出されます。  これらの呼び出しごとに手順ではcd 繰り返されます。  集計の各レベルの最も外側のプロジェクトのサブタイプ `IUnknown` への `pOuter` のポインター。  
  
 次の例では環境で実行されるたびに <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> のメソッドのおおよその表現をプログラム的なプロセスについて詳しく説明します。  コードはその例です。; コンパイル使用してすべてのエラー チェックをオフにするに削除されました。  
  
## 例  
  
### コード  
  
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
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [プロジェクトのサブタイプ](../../extensibility/internals/project-subtypes.md)
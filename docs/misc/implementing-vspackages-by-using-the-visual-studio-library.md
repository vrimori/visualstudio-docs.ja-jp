---
title: "Visual Studio ライブラリを使用した VSPackage の実装 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio ライブラリ、VSPackageの実装"
ms.assetid: 4cbac13f-2a9d-4955-b411-dad79081fdeb
caps.latest.revision: 7
caps.handback.revision: 7
manager: "douge"
---
# Visual Studio ライブラリを使用した VSPackage の実装
Visual Studio のライブラリ `IVsPackageImpl` のクラスは <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> インターフェイスの最小限の実装を提供します。  `IVsPackageImpl` は <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> の保守のメソッドのほとんど同じように処理します。  有効な実装を提供するためにオーバーライドできるようにする必要があるそのほかのメソッドには以下のものが含まれています :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.CreateTool%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] パッケージのテンプレートはここで説明するすべてのコードを生成します。  にはVSPackage を生成するためにテンプレートを使用することで時間を節約できます。  
  
 Visual Studio でライブラリを使用して実装されたパッケージはATL [CComObjectRootEx クラス](/visual-cpp/atl/reference/ccomobjectrootex-class) と [CComCoClass クラス](/visual-cpp/atl/reference/ccomcoclass-class) と Visual Studio のライブラリ IVsPackageImpl から VSPackage のクラスを継承します。  たとえば次のように Reference.Package サンプルの VSPackage のクラス宣言があります :  
  
```  
class ATL_NO_VTABLE BasicPackage :   
    public CComObjectRootEx<CComSingleThreadModel>,  
    public CComCoClass<BasicPackage, &CLSID_BasicPackage>,  
    public IVsPackageImpl<BasicPackage, &CLSID_BasicPackage>,  
    ...  
```  
  
 次の `IVsPackageImpl` テンプレート パラメーターはVSPackage を識別する GUID へ VSPackage のクラス自体とのポインターです。  
  
## COM マップとの QueryInterface  
 `QueryInterface` に対する ATL のサポートを取得するにはCOM マップはクラスインターフェイスの実装を記述する必要があります。  たとえばは次の例の Reference.Package VSPackage のクラスの COM マップです :  
  
```  
BEGIN_COM_MAP(BasicPackage)  
    COM_INTERFACE_ENTRY(IVsPackage)  
    ...  
END_COM_MAP()  
```  
  
 COM マップの詳細については[CComObjectRootEx の実装](/visual-cpp/atl/implementing-ccomobjectrootex) と [COM\_INTERFACE\_ENTRY に関するマクロ](../Topic/COM_INTERFACE_ENTRY%20Macros.md) を参照してください。  
  
## レジストリのマップとの登録  
 Visual Studio のライブラリはCOM オブジェクトの登録をサポートするために ATL スタイル .RGS ファイルを使用します。  .RGS のファイル トークン置換をサポートするにはVisual Studio のライブラリはレジストリのマップを使用します。  レジストリのマップは置換されるシンボルとストリング テーブル リソースの ID を使用できます。  
  
 たとえばは次の例の Reference.Package VSPackage のクラスのレジストリのマップです :  
  
```  
VSL_BEGIN_REGISTRY_MAP(IDR_BASICPACKAGE_RGS)  
    VSL_REGISTRY_MAP_GUID_ENTRY(CLSID_BasicPackage)  
    VSL_REGISTRY_RESOURCE_STRING_ENTRY(IDS_BASICPACKAGE_REGISTRY_NAME)  
    ...  
VSL_END_REGISTRY_MAP()  
```  
  
## 参照  
 [VSSDK のサンプル](../misc/vssdk-samples.md)
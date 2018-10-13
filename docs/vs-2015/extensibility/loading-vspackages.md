---
title: Vspackage の読み込み |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2294f40158c37b404a9e0301a5204b022c7f1fa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173018"
---
# <a name="loading-vspackages"></a>VSPackage の読み込み
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage は、それらの機能が必要な場合にのみ、Visual Studio に読み込まれます。 たとえば、Visual Studio がプロジェクト ファクトリや VSPackage を実装するサービスを使用するときに VSPackage が読み込まれます。 この機能には、パフォーマンスを向上させるために可能な場合に使用される、遅延読み込みが呼び出されます。  
  
> [!NOTE]
>  Visual Studio では、VSPackage を読み込むことがなく、VSPackage を提供するコマンドなどの VSPackage の情報を確認できます。  
  
 Vspackage に設定できます、特定のユーザー インターフェイス (UI) のコンテキストでの自動読み込みなど、ソリューションが開いているとき。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>属性は、このコンテキストを設定します。  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>特定のコンテキストで VSPackage を自動読み込み  
  
-   追加、 `ProvideAutoLoad` VSPackage 属性に属性します。  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     列挙型のフィールドを参照してください。 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> UI コンテキストとその GUID 値の一覧についてはします。  
  
-   ブレークポイントを設定、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッド。  
  
-   VSPackage をビルドしてデバッグを開始します。  
  
-   ソリューションを読み込むか、1 つを作成します。  
  
     VSPackage では、読み込みをブレークポイントで停止します。  
  
## <a name="forcing-a-vspackage-to-load"></a>強制的に VSPackage を読み込む  
 状況によっては、VSPackage を強制的に別の VSPackage を読み込む必要があります。 たとえば、軽量の VSPackage では、つまり、CMDUIContext として使用できないコンテキストでより大きな VSPackage を読み込む可能性があります。  
  
 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>をロードするために VSPackage を強制する方法。  
  
-   次のコードを挿入、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッドの VSPackage を読み込む別の VSPackage を強制します。  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     により、VSPackage が初期化されると、`PackageToBeLoaded`を読み込めません。  
  
     強制読み込みは、VSPackage 通信しないに使用する必要があります。 使用[を使用して、サービスを提供する](../extensibility/using-and-providing-services.md)代わりにします。  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>カスタム属性を使用して、VSPackage を登録するには  
 場合によっては、拡張機能の新しい登録属性を作成する必要があります。 新しいレジストリ キーを追加したり既存のキーに新しい値を追加する登録属性を使用することができます。 新しい属性が派生する必要があります<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>、それをオーバーライドする必要があり、<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>と<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>メソッド。  
  
## <a name="creating-a-registry-key"></a>レジストリ キーの作成  
 次のコードでは、カスタム属性を作成、**カスタム**登録される VSPackage のキーの下のサブキー。  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>既存のレジストリ キーの下の新しい値を作成します。  
 カスタム値は、既存のキーを追加できます。 次のコードでは、VSPackage の登録キーを新しい値を追加する方法を示します。  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)


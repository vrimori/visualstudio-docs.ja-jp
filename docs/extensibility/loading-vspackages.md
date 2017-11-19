---
title: "Vspackage を読み込む |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94db8d3bb95e254a3fa528a424048162916fce99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="loading-vspackages"></a>Vspackage を読み込む
Vspackage は、それらの機能が必要な場合にのみ、Visual Studio に読み込まれます。 たとえば、Visual Studio はプロジェクト ファクトリまたは VSPackage を実装するサービスを使用する場合、VSPackage が読み込まれます。 この機能は、パフォーマンスを向上させるために可能な場合に使用される、遅延読み込みと呼ばれます。  
  
> [!NOTE]
>  Visual Studio は、VSPackage を読み込むことがなく、VSPackage を提供するコマンドなど、特定の VSPackage の情報を確認できます。  
  
 Vspackage に設定できます autoload コンテキストでは特定のユーザー インターフェイス (UI)、たとえば、ソリューションが開いているときにします。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>属性はこのコンテキストを設定します。  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>特定のコンテキストで VSPackage 自動読み込み  
  
-   追加、 `ProvideAutoLoad` VSPackage の属性に属性します。  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     フィールドの列挙を参照してください<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>UI コンテキストとその GUID 値の一覧についてはします。  
  
-   ブレークポイントを設定、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッドです。  
  
-   VSPackage をビルドしてデバッグを開始します。  
  
-   ソリューションを読み込むか、1 つを作成します。  
  
     VSPackage を読み込んで、ブレークポイントで停止します。  
  
## <a name="forcing-a-vspackage-to-load"></a>強制的に VSPackage を読み込む  
 状況によっては、VSPackage を強制的に読み込まれる別の VSPackage 必要があります。 たとえば、軽量の VSPackage、CMDUIContext としては使用できませんのコンテキストでより大きな VSPackage を読み込むことがします。  
  
 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>を読み込むために VSPackage を強制する方法です。  
  
-   このコードに挿入、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>強制的に別の VSPackage を読み込む、VSPackage のメソッド。  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     VSPackage の初期化時に強制されます`PackageToBeLoaded`を読み込めません。  
  
     強制読み込みは、VSPackage の通信には使用されません。 使用して[を使用してサービスを提供する](../extensibility/using-and-providing-services.md)代わりにします。  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>カスタム属性を使用して、VSPackage を登録するには  
 特定の状況では、拡張機能の新しい登録属性を作成する必要があります。 新しいレジストリ キーを追加したり既存のキーに新しい値を追加するには、登録属性を使用することができます。 新しい属性が派生する必要があります<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>、それをオーバーライドする必要があります、<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>と<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>メソッドです。  
  
## <a name="creating-a-registry-key"></a>レジストリ キーを作成します。  
 次のコードでは、カスタム属性を作成、**カスタム**登録される VSPackage のキーの下のサブキーです。  
  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>既存のレジストリ キーの下で新しい値を作成します。  
 カスタム値は、既存のキーを追加できます。 次のコードは、VSPackage の登録キーを新しい値を追加する方法を示しています。  
  
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
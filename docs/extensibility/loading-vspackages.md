---
title: "Vspackage を読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage の自動読み込み"
  - "VSPackage、読み込み"
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Vspackage を読み込む
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages は、それらの機能が必要な場合にのみ、Visual Studio に読み込まれます。 たとえば、Visual Studio は、プロジェクトの工場出荷時や、VSPackage を実装するサービスを使用するときに VSPackage が読み込まれます。 この機能には、パフォーマンスを向上させるために可能な場合に使用される遅延読み込みは呼び出されます。  
  
> [!NOTE]
>  Visual Studio では、VSPackage を読み込むことがなく、VSPackage を提供するコマンドなど、特定の vs パッケージ情報を確認できます。  
  
 VSPackages に設定できます、特定のユーザー インターフェイス \(UI\) のコンテキストでの自動読み込みなど、ソリューションを開いている場合。<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 属性はこのコンテキストを設定します。  
  
### 特定のコンテキストで VSPackage 自動読み込み  
  
-   追加、 `ProvideAutoLoad` VSPackage 属性に属性します。  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     列挙型のフィールドを参照してください <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> UI コンテキストとその GUID 値のリスト。  
  
-   ブレークポイントを設定、 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> メソッドです。  
  
-   VSPackage をビルドしてデバッグを開始します。  
  
-   ソリューションを読み込むか、1 つを作成します。  
  
     VSPackage を読み込んではブレークポイントで停止します。  
  
## 強制的に VSPackage を読み込む  
 状況によっては、VSPackage を強制的に読み込まれる別の VSPackage 必要があります。 たとえば、軽量 VSPackage には、CMDUIContext として記載されていないコンテキストでより大きな VSPackage によって読み込まれます。  
  
 使用することができます、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> を読み込む VSPackage を強制する方法です。  
  
-   このコードに挿入、 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> VSPackage を読み込む別 VSPackage を強制する方法。  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     強制的に VSPackage が初期化されると、 `PackageToBeLoaded` を読み込めません。  
  
     強制読み込みの VSPackage 通信を指定しないでください。 代わりに、[使用して、サービスを提供します。](../extensibility/using-and-providing-services.md) を使用してください。  
  
## カスタム属性を使用して、VSPackage を登録するには  
 特定の場合に、拡張機能の新しい登録属性を作成する必要があります。 新しいレジストリ キーを追加したり既存のキーに新しい値を追加するには、登録属性を使用することができます。 新しい属性から派生する必要があります <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, 、ファイルは上書きする必要があり、 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> と <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> メソッドです。  
  
## レジストリ キーを作成します。  
 次のコードでは、カスタム属性を作成、 **カスタム** が登録されている VSPackage のキーの下のサブキーです。  
  
```c#  
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
  
## 既存のレジストリ キーの下の新しい値を作成します。  
 カスタム値は、既存のキーを追加できます。 次のコードは、VSPackage 登録キーを新しい値を追加する方法を示しています。  
  
```c#  
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
  
## 参照  
 [Vspackages にあります。](../extensibility/internals/vspackages.md)
---
title: Vspackage を読み込む |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 008cd31bc3d9f909477089e608393f596bfb0682
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)

---
title: Vspackage の読み込み |Microsoft Docs
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
ms.openlocfilehash: 26bd199a688b1b47728aac561720224a71f1583b
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638148"
---
# <a name="load-vspackages"></a>Vspackage を読み込む
Vspackage は、それらの機能が必要な場合にのみ、Visual Studio に読み込まれます。 たとえば、Visual Studio がプロジェクト ファクトリや VSPackage を実装するサービスを使用するときに VSPackage が読み込まれます。 この機能には、パフォーマンスを向上させるために可能な場合に使用される、遅延読み込みが呼び出されます。  
  
> [!NOTE]
>  Visual Studio では、VSPackage を読み込むことがなく、VSPackage を提供するコマンドなどの VSPackage の情報を確認できます。  
  
 Vspackage に設定できます、特定のユーザー インターフェイス (UI) のコンテキストでの自動読み込みなど、ソリューションが開いているとき。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>属性は、このコンテキストを設定します。  
  
### <a name="autoload-a-vspackage-in-a-specific-context"></a>特定のコンテキストで VSPackage を自動読み込み  
  
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
  
## <a name="force-a-vspackage-to-load"></a>強制的に VSPackage を読み込む  
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
  
     強制読み込みは、VSPackage 通信しないに使用する必要があります。 使用[使用してサービスを提供および](../extensibility/using-and-providing-services.md)代わりにします。
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../extensibility/internals/vspackages.md)

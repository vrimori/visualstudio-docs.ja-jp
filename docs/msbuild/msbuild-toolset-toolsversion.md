---
title: "MSBuild ツールセット (ToolsVersion) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: "30"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 85d570564ba3e82808f0876ead938f535368ec29
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild ツールセット (ToolsVersion)
MSBuild は、タスク、ターゲット、およびツールのツールセットを使用して、アプリケーションをビルドします。 通常、MSBuild ツールセットには、microsoft.common.tasks ファイル、microsoft.common.targets ファイル、および csc.exe や vbc.exe などのコンパイラが含まれています。 ほとんどのツールセットは、複数のバージョンの .NET Framework や複数のシステム プラットフォームを対象としてアプリケーションをコンパイルするために使用できます。 ただし、MSBuild 2.0 ツールセットは .NET Framework 2.0 のみを対象として使用できます。  
  
## <a name="toolsversion-attribute"></a>ToolsVersion 属性  
 プロジェクト ファイルにある [Project](../msbuild/project-element-msbuild.md) 要素の `ToolsVersion` 属性でツールセットを指定します。 次の例では、MSBuild 15.0 ツールセットを使用してプロジェクトをビルドすることを指定します。  
  
```xml  
<Project ToolsVersion="15.0" ... </Project>  
```  
  
## <a name="how-the-toolsversion-attribute-works"></a>ToolsVersion 属性の動作  
 Visual Studio でプロジェクトを作成するとき、または既存のプロジェクトをアップグレードするときに、`ToolsVersion` という名前の属性が自動的にプロジェクト ファイルに含まれ、その値は、Visual Studio エディションに付属している MSBuild のバージョンに対応します。 詳細については、「[対象となる特定の .NET Framework のバージョンの指定](../ide/targeting-a-specific-dotnet-framework-version.md)」を参照してください。  
  
 `ToolsVersion` の値をプロジェクト ファイルで定義すると、MSBuild ではその値に基づいて、プロジェクトで使用できるツールセットのプロパティの値を判別します。 ツールセットのプロパティの 1 つに `$(MSBuildToolsPath)` があります。このプロパティは、.NET Framework ツールのパスを指定します。 このツールセットのプロパティ (または `$(MSBuildBinPath)`) は、唯一の必須のプロパティです。  
  
 Visual Studio 2013 以降、MSBuild ツールセットのバージョンは Visual Studio のバージョン番号と同じになりました。 プロジェクト ファイルで指定されたツールセットのバージョンにかかわりなく、MSBuild は Visual Studio 内とコマンド ラインでこのツールセットを既定として使用します。  この動作は、/ToolsVersion フラグを使用してオーバーライドできます。 詳細については、「[ToolsVersion 設定をオーバーライドする](../msbuild/overriding-toolsversion-settings.md)」を参照してください。  
  
 次の例では、MSBuild は `MSBuildToolsPath` 予約済みプロパティを使用して Microsoft.CSharp.targets ファイルを検索します。  
  
```xml  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 `MSBuildToolsPath` の値を変更するには、カスタム ツールセットを定義します。 詳細については、「[標準ツールセット構成とカスタム ツールセット構成](../msbuild/standard-and-custom-toolset-configurations.md)」を参照してください。  
  
 ソリューションをコマンド ラインでビルドするとき、msbuild.exe に対して `ToolsVersion` を指定すると、すべてのプロジェクトとそのプロジェクト間の依存関係がその `ToolsVersion` に基づいてビルドされます。ソリューション内の各プロジェクトで固有の `ToolsVersion` が指定されていても、その値は無視されます。 プロジェクトごとに `ToolsVersion` 値を定義する場合は、「[ToolsVersion 設定のオーバーライド](../msbuild/overriding-toolsversion-settings.md)」を参照してください。  
  
 `ToolsVersion` 属性はプロジェクトの移行でも使用されます。 たとえば、Visual Studio 2010 で Visual Studio 2008 プロジェクトを開く場合、プロジェクト ファイルは ToolsVersion="4.0" を含むように更新されます。 次に、そのプロジェクトを Visual Studio 2008 で開こうとすると、アップグレードされた `ToolsVersion` は認識されないため、プロジェクトは属性が 3.5 に設定された場合と同様にビルドされます。  
  
 Visual Studio 2010 と Visual Studio 2012 は、4.0 の ToolsVersion を使用します。 Visual Studio 2013 は、12.0 の ToolsVersion を使用します。 Visual Studio 2015 は ToolsVersion 14.0 を使用し、Visual Studio 2017 は ToolsVersion 15.0 を使用します。 多くの場合、複数のバージョンの Visual Studio でプロジェクトを開くことができます。変更する必要はありません。 Visual Studio は常に正しいツールセットを使用しますが、使用されているバージョンがプロジェクト ファイルのバージョンと一致しない場合は、そのことが通知されます。 ほとんどの場合、ツールセットには互換性があるため、この警告は問題にはなりません。  
  
 このトピックの後半で説明するサブツールセットを使用すると、MSBuild では、ビルドが実行されるコンテキストに基づいて、使用するツールのセットを自動的に切り替えることができます。 たとえば、プロジェクト ファイルを明示的に変更しなくても、MSBuild では、Visual Studio 2010 での実行時に Visual Studio 2010 での実行時よりも新しいツールのセットを使用できるようになります。  
  
## <a name="toolset-implementation"></a>ツールセットの実装  
 ツールセットを実装するには、ツールセットを構成するさまざまなツール、ターゲット、およびタスクのパスを選択します。 MSBuild で定義されるツールセットに含まれるツールは、次のソースから取得されます。  
  
-   .NET Framework フォルダー  
  
-   追加のマネージ ツール  
  
 マネージ ツールには ResGen.exe と TlbImp.exe があります。  
  
 MSBuild には、ツールセットにアクセスするための 2 つの方法が用意されています。  
  
-   ツールセットのプロパティの使用  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper> メソッドの使用  
  
 ツールセットのプロパティは、ツールのパスを指定します。 MSBuild はプロジェクト ファイル内にある `ToolsVersion` 属性の値を使用して、対応するレジストリ キーを検索します。その後で、レジストリ キーの情報を使用して、ツールセットのプロパティを設定します。 たとえば、`ToolsVersion` の値が `12.0` である場合、MSBuild は、レジストリ キー (HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0) に従ってツールセットのプロパティを設定します。  
  
 ツールセットのプロパティを次に示します。  
  
-   `MSBuildToolsPath`: MSBuild のバイナリのパスを指定します。  
  
-   `SDK40ToolsPath` は、MSBuild 4.x (4.0 または 4.5) に必要な追加のマネージ ツールのパスを指定します。  
  
-   `SDK35ToolsPath`: MSBuild 3.5 に必要な追加のマネージ ツールのパスを指定します。  
  
 また、<xref:Microsoft.Build.Utilities.ToolLocationHelper> クラスのメソッドを呼び出すことによって、ツールセットをプログラムで確認することもできます。 このクラスには、次のメソッドが含まれています。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A>: .NET Framework フォルダーのパスを返します。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A>: .NET Framework フォルダーに格納されているファイルのパスを返します。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A>: マネージ ツール フォルダーのパスを返します。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A>: マネージ ツール フォルダーに通常格納されているファイルのパスを返します。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> は、ビルド ツールのパスを返します。  
  
### <a name="sub-toolsets"></a>サブツールセット  
 このトピックで既に説明したように、MSBuild ではレジストリ キーを使用して、基本ツールのパスを指定します。 キーにサブキーがある場合、MSBuild ではそのサブキーを使用して、追加のツールを含むサブツールセットのパスを指定します。 この場合、ツールセットは両方のキーで定義されたプロパティ定義を組み合わせることによって定義されます。  
  
> [!NOTE]
>  ツールセットのプロパティ名が競合する場合、サブキーのパスに対して定義された値が、ルート キーのパスに対して定義された値よりも優先されます。  
  
 サブツールセットは、`VisualStudioVersion` ビルド プロパティがある場合にアクティブになります。 このプロパティは、次の値のいずれか 1 つを使用できます。  
  
-   "10.0": .NET Framework 4 のサブツールセットを指定します。  
  
-   "11.0": .NET Framework 4.5 のサブツールセットを指定します。  
  
-   "12.0": .NET Framework 4.5.1 のサブツールセットを指定します。  
  
 サブツールセット 10.0 および 11.0 は ToolsVersion 4.0 と一緒に使用する必要があります。 それ以降のバージョンでは、サブツールセットのバージョンとToolsVersion は一致しています。  
  
 ビルド中に、MSBuild は `VisualStudioVersion` プロパティの既定値を自動的に決定し、設定します (このプロパティがまだ定義されていない場合)。  
  
 MSBuild には、`ToolLocationHelper` 列挙値をパラメーターとして追加する `VisualStudioVersion` メソッド用のオーバーロード機能が用意されています。  
  
 サブツールセットは .NET Framework 4.5 で導入されました。  
  
## <a name="see-also"></a>関連項目  
 [標準ツールセット構成とカスタム ツールセット構成](../msbuild/standard-and-custom-toolset-configurations.md)   
 [マルチ ターゲット](../msbuild/msbuild-multitargeting-overview.md)

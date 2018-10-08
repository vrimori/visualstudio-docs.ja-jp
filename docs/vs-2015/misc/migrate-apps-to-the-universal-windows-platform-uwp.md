---
title: アプリ、ユニバーサル Windows プラットフォーム (UWP) を移行する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: c9675cbb25d9f968a170484c9ec33e3af11e074d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547006"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>アプリを Universal Windows Platform (UWP) へ移行する
Visual Studio 2015 RC で作成された Windows Store 8.1 アプリ、Windows Phone 8.1 アプリ、またはユニバーサル Windows アプリ用の既存のプロジェクト ファイルに必要な変更を手動で加え、Visual Studio 2015 RTM で使用できるようにします。 (Windows アプリのプロジェクトと Windows Phone プロジェクトの両方を備えた Windows 8.1 ユニバーサル アプリがある場合、各プロジェクトを移行するための手順に従う必要があります。)  
  
 ユニバーサル Windows プラットフォームの場合は、今すぐにアプリのターゲットを 1 つ以上のデバイス ファミリにします。 ユニバーサル Windows アプリについて詳しくは、この「 [プラットフォーム ガイド](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx)」を参照してください。  
  
-   [既存の C#/VB の Windows ストア 8.1 または Windows Phone 8.1 アプリを移行して](#MigrateCSharp) ユニバーサル Windows プラットフォームを使用するようにします。  
  
-   [既存の C++ の Windows ストア 8.1 または Windows Phone 8.1 アプリを移行して](#MigrateCPlusPlus) ユニバーサル Windows プラットフォームを使用するようにします。  
  
-   [Visual Studio 2015 RC で作成された既存のユニバーサル Windows アプリに必要な変更](#PreviousVersions)。  
  
-   [Visual Studio 2015 RC で作成されたユニバーサル Windows アプリの既存の単体テスト プロジェクトに必要な変更](#MigrateUnitTest)。  
  
 これらのすべての変更を加えない場合は、新しいユニバーサル Windows プロジェクトに [既存のアプリを移植する方法](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) を参照してください。  
  
##  <a name="MigrateCSharp"></a> ユニバーサル Windows プラットフォームを使用して C #/vb Windows ストア 8.1 または Windows Phone 8.1 アプリを移行します。  
  
#### <a name="migrate-your-cvb-project-files"></a>C#/VB プロジェクト ファイルを移行する  
  
1.  インストールされているユニバーサル Windows プラットフォームを見つけるには、次のフォルダーを開きます: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**。 これには、インストールされているユニバーサル Windows プラットフォームごとのフォルダーの一覧が含まれています。 フォルダー名は、インストールされているユニバーサル Windows プラットフォームのバージョンです。 たとえば、この Windows 10 デバイスには、ユニバーサル Windows プラットフォームのバージョン 10.0.10240.0 がインストールされています。  
  
     ![インストールされているバージョンを表示するフォルダーを開く](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     ユニバーサル Windows プラットフォームの複数のバージョンをインストールすることができます。 アプリに対応した最新バージョンを使用することをお勧めします。  
  
2.  ファイル エクスプローラーを使用して、UWP プロジェクトが保存されているフォルダーに移動します。 このフォルダー内に .json ファイルを作成します。 ファイルの名前を project.json にして、次の内容をこのファイルに追加します。  
  
    ```json  
    {  
      "dependencies": {  
        "Microsoft.ApplicationInsights": "1.0.0",  
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
      },  
      "frameworks": {  
        "uap10.0": {}  
      },  
      "runtimes": {  
        "win10-arm": {},  
        "win10-arm-aot": {},  
        "win10-x86": {},  
        "win10-x86-aot": {},  
        "win10-x64": {},  
        "win10-x64-aot": {}  
      }  
    }  
  
    ```  
  
3.  以下の内容で、default.rd.xml という名前のファイルを作成します。 VB プロジェクトがある場合、このファイルをプロジェクトのマイ プロジェクト ディレクトリに追加します。 C# プロジェクトがある場合、このファイルをプロジェクトのプロパティ ディレクトリに追加します。  
  
    ```xml  
    <?xml version="1.0"?>  
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>  
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->  
    <Assembly Dynamic="Required All" Name="*Application*"/>  
    <!-- Add your application specific runtime directives here. -->  
    </Application></Directives>  
    ```  
  
4.  Visual Studio で、既存の Windows Store 8.1 アプリまたは Windows Phone 8.1 アプリを含むソリューションを開きます。  
  
5.  ソリューション エクスプローラーで、アプリの既存のプロジェクトを右クリックし、 **[プロジェクトのアンロード]** を選択します。 プロジェクトをアンロードした後、プロジェクト ファイルを再度右クリックして、.csproj または .vbproj ファイルの編集を選択します。  
  
     ![プロジェクトを右クリックして、編集](../misc/media/uap-editproject.png "UAP_EditProject")  
  
6.  検索、 \<PropertyGroup > 要素を含む、 \<TargetPlatformVersion > 8.1 の値を持つ要素。 これは、次の手順を行う\<PropertyGroup > 要素。  
  
    1.  値を設定、 \<Platform > 要素を: **x86**します。  
  
    2.  追加、 \<TargetPlatformIdentifier > 要素に値を設定および: **UAP**します。  
  
    3.  既存の値の変更、 \<TargetPlatformVersion > 要素をインストールしたユニバーサル Windows プラットフォームのバージョンの値になります。 追加も、 \<TargetPlatformMinVersion > 要素と同じ値を指定します。  
  
    4.  値を変更、 \<MinimumVisualStudioVersion > 要素を: **14**します。  
  
    5.  置換、 \<ProjectTypeGuids > 要素の下に示すようにします。  
  
         C# の場合 :  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        ```  
  
         VB の場合:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        ```  
  
    6.  追加、 \<EnableDotNetNativeCompatibleProfile > 要素に値を設定および: **true**します。  
  
    7.  ユニバーサル Windows アプリの既定のアセット スケールは 200 です。 追加する必要がありますが、プロジェクトには、200 で縮小しないアセットが含まれている場合、 \<UapDefaultAssetScale > この PropertyGroup に資産の小数点以下桁数の値を持つ要素。 詳細については、「 [資産とスケール](http://msdn.microsoft.com/library/jj679352.aspx)」を参照してください。  
  
         これで、 \<PropertyGroup > 要素にこの例のようになります。  
  
        ```xml  
        <PropertyGroup>  
            …  
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>  
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>  
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>  
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
7.  現在使用している Visual Studio のバージョンを反映するように、12.0 のすべてのインスタンスを 14.0 に置き換えます。 たとえば、以下のインスタンスです。  
  
    ```xml  
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
    ```  
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">  
        <VisualStudioVersion>14.0</VisualStudioVersion>  
    ```  
  
8.  検索\<PropertyGroup > 要素の Condition 属性の一部として AnyCPU プラットフォーム用に構成されています。 これらの要素と、そのすべての子を削除します。 Visual Studio 2015 RC において、AnyCPU は Windows 10 アプリではサポートされていません。 たとえば、削除する必要があります\<PropertyGroup > 要素が以下のようにします。  
  
    ```xml  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
    ```  
  
9. 残りの\<PropertyGroup > 要素で要素が、リリース構成での Condition 属性を確認します。 含まれていない場合、 \<UseDotNetNativeToolchain > 要素、1 つを追加します。 値を設定、 \<UseDotNetNativeToolchain > 要素を次のように、true にします。  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">  
        <OutputPath>bin\x64\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <Optimize>true</Optimize>  
        <NoWarn>;2008</NoWarn>  
        <DebugType>pdbonly</DebugType>  
        <PlatformTarget>x64</PlatformTarget>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
        <ErrorReport>prompt</ErrorReport>  
        <Prefer32Bit>true</Prefer32Bit>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
10. Windows Phone プロジェクトのみ、削除、 \<PropertyGroup > 要素を含む、 \<TargetPlatformIdentifier > WindowsPhoneApp の値を持つ要素。 また、この要素の子をすべて削除します。  
  
    ```xml  
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">  
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>  
    </PropertyGroup>  
    ```  
  
11. 検索、 \<ItemGroup > 要素を含む、 \<AppxManifest > 要素。 次の追加\<None > 要素の子として、 \<ItemGroup > 要素。  
  
    ```xml  
    <None Include="project.json" />  
    ```  
  
12. 検索、 \<ItemGroup > 要素を含む logo .png ファイルなど、プロジェクトに追加されるその他の資産 (\<コンテンツ Include="Assets\Logo.scale-100.png"/>)。 次の追加\<Content > 子要素のこの\<ItemGroup > 要素。  
  
     **(C#)。**  
  
    ```xml  
    <Content Include="Properties\default.rd.xml" />  
    ```  
  
     **VB の場合。**  
  
    ```xml  
    <Content Include="My Project\default.rd.xml" />  
    ```  
  
13. 検索、 \<ItemGroup > 要素を含む\<参照 > 子要素を NuGet パッケージ。 プロジェクトを再読み込みした後に、NuGet パッケージ マネージャーで NuGet パッケージをダウンロードする必要があるため、使用する NuGet パッケージに注意してください。 この削除\<ItemGroup > とその子。 たとえば、ある UWP プロジェクトでは次の NuGet パッケージを削除する必要があるかもしれません。  
  
    ```xml  
    <ItemGroup>  
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
      </ItemGroup>  
    ```  
  
14. 変更内容を保存します。  
  
15. .csproj または .vbproj ファイルを閉じます。  
  
16. ソリューション エクスプローラーでプロジェクトを右クリックし、コンテキスト メニューの [プロジェクトの再読み込み] をクリックします。 これで、プロジェクト内のすべてのファイルがソリューション エクスプローラーに表示されます。  
  
17. 前の手順で削除したパッケージを再度追加するには、NuGet マネージャーを使用します。  
  
     次に、Windows ストア 8.1 または Windows Phone 8.1 プロジェクトの [パッケージ マニフェスト ファイルを更新する](#PackageManifest) 手順に従う必要があります。  
  
##  <a name="MigrateCPlusPlus"></a> ユニバーサル Windows プラットフォームを使用する C++ Windows ストア 8.1 または Windows Phone 8.1 アプリを移行します。  
  
#### <a name="migrate-your-c-project-files"></a>C++ プロジェクト ファイルを移行する  
  
1.  インストールされているユニバーサル Windows プラットフォームを見つけるには、次のフォルダーを開きます: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**。 これには、インストールされているユニバーサル Windows プラットフォームごとのフォルダーの一覧が含まれています。 フォルダー名は、インストールされているユニバーサル Windows プラットフォームのバージョンです。 たとえば、この Windows 10 デバイスには、ユニバーサル Windows プラットフォームのバージョン 10.0.10240.0 がインストールされています。  
  
     ![インストールされているバージョンを表示するフォルダーを開く](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     ユニバーサル Windows プラットフォームの複数のバージョンをインストールすることができます。 アプリに対応した最新バージョンを使用することをお勧めします。  
  
2.  Visual Studio で、既存の C++ Windows Store 8.1 アプリまたは Windows Phone 8.1 アプリを含むソリューションを開きます。  
  
     ソリューション エクスプローラーで、既存のプロジェクトを右クリックし、 **[プロジェクトのアンロード]** を選択します。 プロジェクトをアンロードした後、プロジェクト ファイルを再度右クリックして、.vcxproj ファイルの編集を選択します。  
  
     ![右&#45;プロジェクト ファイルをクリックして編集を選択](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")  
  
3.  検索、 \<PropertyGroup > 要素を含む、 \<ApplicationTypeRevision > 8.1 の値を持つ要素。 これは、次の手順を行う\<PropertyGroup > 要素。  
  
    1.  追加、 \<WindowsTargetPlatformVersion > 要素と\<WindowsTargetPlatformMinVersion > 要素をインストールしたユニバーサル Windows プラットフォームのバージョンの値を付けます。  
  
    2.  ApplicationTypeRevision 要素の値を 8.1 から 10.0 に更新します。  
  
    3.  値を変更、 \<MinimumVisualStudioVersion > 要素を: 14 です。  
  
    4.  追加、 \<EnableDotNetNativeCompatibleProfile > 要素その値を設定する: true。  
  
    5.  ユニバーサル Windows アプリの既定のアセット スケールは 200 です。 追加する必要がありますが、プロジェクトには、200 で縮小しないアセットが含まれている場合、 \<UapDefaultAssetScale > この PropertyGroup に資産の小数点以下桁数の値を持つ要素。 詳細については、「 [資産とスケール](http://msdn.microsoft.com/library/jj679352.aspx)」を参照してください。  
  
    6.  Windows Phone のプロジェクトのみの値を変更\<ApplicationType > Windows ストアへの Windows Phone から。  
  
         これで、 \<PropertyGroup > 要素にこの例のようになります。  
  
        ```xml  
        <PropertyGroup>  
            …  
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
             <ApplicationType>Windows Store</ApplicationType>  
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
4.  すべてのインスタンスの変更、 \<PlatformToolset > 要素に値 v140 を設定します。 例えば:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
5.  残りの\<PropertyGroup > 要素で要素が、リリース構成での Condition 属性を確認します。 含まれていない場合、 \<UseDotNetNativeToolchain > 要素、1 つを追加します。 値を設定、 \<UseDotNetNativeToolchain > 要素を次のように、true にします。  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
6.  変更内容を保存します。 その後、プロジェクト ファイルを閉じます。  
  
7.  ソリューション エクスプローラーでプロジェクト ファイルを右クリックし、コンテキスト メニューの [プロジェクトの再読み込み] をクリックします。 これで、プロジェクト内のすべてのファイルがソリューション エクスプローラーに表示されます。  
  
     次に、Windows ストア 8.1 または Windows Phone 8.1 プロジェクトの [パッケージ マニフェスト ファイルを更新する](#PackageManifest) 手順に従う必要があります。  
  
##  <a name="PackageManifest"></a> すべての Windows ストア 8.1 または Windows Phone 8.1 プロジェクトのパッケージ マニフェスト ファイルを更新します。  
 ソリューション内のプロジェクトごとに、パッケージのマニフェスト ファイルを更新する必要があります。  
  
#### <a name="update-your-package-manifest-file"></a>パッケージ マニフェスト ファイルを更新する  
  
1.  プロジェクトの Package.appxmanifest ファイルを開きます。 Windows ストアと Windows Phone のプロジェクトごとに、Package.AppxManifest ファイルを編集する必要があります。  
  
2.  更新する必要がある、\<パッケージ > 既存のプロジェクトの種類に基づいて、新しいスキーマを持つ要素。 最初に、Windows ストアまたは Windows Phone プロジェクトがあるかどうかに基づいて、以下のスキーマを削除します。  
  
     **Windows ストア プロジェクトの古い:** 、\<パッケージ > 要素は次のようになります。  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
        xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">  
  
    ```  
  
     **Windows Phone プロジェクトの古い:** 、\<パッケージ > 要素は次のようになります。  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
    xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"  
    xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"  
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">  
    ```  
  
     **ユニバーサル Windows プラットフォームの新機能:** 以下のスキーマを追加、\<パッケージ > 要素。 削除したスキーマの要素から、関連した名前空間の識別子のプレフィックスを削除します。 IgnorableNamespaces プロパティを uap mp に更新します。 新しい\<パッケージ > 要素がこのような検索する必要があります。  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"  
        xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"  
        xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"  
       IgnorableNamespaces= "uap mp">  
  
    ```  
  
3.  追加、\<依存関係 > 子要素の\<パッケージ > 要素。 追加し、 \<TargetDeviceFamily > 子要素のこの\<依存関係 > Name、MinVersion、および MaxVersionTested 属性を持つ要素。 Name 属性の値に Windows.Universal を指定します。 MinVersion と MaxVersionTested に、インストールしたユニバーサル Windows プラットフォームのバージョンの値を指定します。 この要素は次のようになります。  
  
    ```xml  
    <Dependencies>  
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />  
    </Dependencies>  
    ```  
  
4.  **Windows ストアのみの:** を追加する必要がある、 \<mp:PhoneIdentity > 子要素の\<パッケージ > 要素。 PhoneProductId 属性と PhonePublisherId 属性を追加します。 内の Name 属性として同じ値を持つ PhoneProductId の設定、 \<Identity > 要素。 PhonePublishedId の値を 00000000-0000-0000-0000-000000000000 に設定します。 以下に例を示します。  
  
    ```xml  
    <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />   
    <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>  
    ```  
  
5.  検索、\<の前提条件 > 要素と、この要素と任意の子要素を削除します。  
  
6.  追加、 **uap** 、次の名前空間\<リソース > の要素: DXFeatureLevel、スケールします。 例えば:  
  
    ```xml  
    <Resources>  
      <Resource Language="en-us"/>  
     <Resource uap:Scale="180"/>  
     <Resource uap:DXFeatureLevel="dx11"/>  
    </Resources>  
  
    ```  
  
7.  追加、 **uap** 、次の名前空間\<機能 > 要素: documentsLibrary、picturesLibrary、videosLibrary、musicLibrary、enterpriseAuthentication、sharedUserCertificates、removableStorage、予定、および連絡先。 例えば:  
  
    ```xml  
    <Capabilities>  
      <uap:Capability Name="documentsLibrary"/>  
      <uap:Capability Name="removableStorage"/>  
    </Capabilities>  
  
    ```  
  
8.  追加、 **uap**名前空間を\<VisualElements > 要素とその子要素のいずれか。 例えば:  
  
    ```xml  
    <uap:VisualElements  
        DisplayName="My WWA App"  
        Square150x150Logo="images/150x150.png"  
        Square44x44Logo="images/44x44.png"  
        Description="My WWA App"  
        BackgroundColor="#777777">  
      <uap:SplashScreen Image="images/splash.png"/>  
    </uap:VisualElements>  
  
    ```  
  
     **Windows ストアにのみ適用されます:** タイル サイズの名前が変更されました。 内の属性を変更、 \<VisualElements > 新しいを反映するように要素がタイルのサイズを集約します。 70x70 は 71x71 になり、30x30 は 44x44 になります。  
  
     **OLD:** タイル サイズの名前  
  
    ```xml  
    <m2:VisualElements  
        …  
        Square30x30Logo="Assets\SmallLogo.png"  
        …>  
     <m2:DefaultTile  
          …  
          Square70x70Logo="images/70x70.png">  
    </m2:VisualElements>  
  
    ```  
  
     **NEW:** タイル サイズの名前  
  
    ```xml  
    <uap:VisualElements  
        …  
        Square44x44Logo="Assets\SmallLogo.png"  
        …>  
     <uap:DefaultTile  
          …  
          Square71x71Logo="images/70x70.png">  
    </uap:VisualElements>  
  
    ```  
  
9. 追加、 **uap**名前空間を\<ApplicationContentUriRules > とそのすべての子要素。 例えば:  
  
    ```xml  
    <uap:ApplicationContentUriRules>  
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>  
      <uap:Rule Type="exclude" Match="*.pdf"/>  
    </uap:ApplicationContentUriRules>  
  
    ```  
  
10. 追加、 **uap** 、次の名前空間\<拡張機能 > 要素とそのすべての子要素: windows.accountPictureProvide、windows.alarm、windows.appointmentsProvider windows.autoPlayContent、 windows.autoPlayDevice、windows.cachedFileUpdate、windows.cameraSettings、windows.fileOpenPicker、windows.fileTypeAssociation、windows.fileSavePicke、windows.lockScreenCall、windows.printTaskSettings、windows.protocol、windows.search、windows.shareTarget します。 例えば:  
  
    ```xml  
    <Extensions>  
      <uap:Extension Category="windows.alarm"/>  
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>  
      <uap:Extension Category="windows.protocol">  
        <uap:Protocol Name="mailto" DesiredView="useHalf">  
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>  
        </uap:Protocol>  
      </uap:Extension>  
    </Extensions>  
  
    ```  
  
11. **uap** 名前空間をタイプ chatMessageNotification のバックグラウンド タスクに追加します。 例えば:  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
     <BackgroundTasks ServerName="MyBackgroundTasks">  
        <uap:Task Type="chatMessageNotification"/>  
      </BackgroundTasks>  
    </Extension>  
  
    ```  
  
12. フレームワークの依存関係を変更します。 すべてパブリッシャー名を追加\<PackageDependency > 要素では、指定されていない場合、MinVersion を指定します。  
  
     **旧:** \<PackageDependency > 要素  
  
    ```xml  
    <Dependencies>  
     <PackageDependency Name="Microsoft.VCLibs.120.00" />  
    </Dependencies>  
  
    ```  
  
     **新規:** \<PackageDependency > 要素  
  
    ```xml  
    <Dependencies>  
     <PackageDependency  
          Name="Microsoft.VCLibs.120.00"  
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"  
          MinVersion="12.0.30113.0" />  
    </Dependencies>  
  
    ```  
  
     使用している実際のフレームワークのための適切な Publisher 値と MinVersion 値を使用します。 Windows 10 では、これらの名前が変更される可能性があることに注意してください。  
  
13. gattCharacteristicNotification と rfcommConnection バック グラウンド タイプ タスクを Bluetooth タイプ タスクに置き換えます。 例えば:  
  
     **古い。**  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
                <Task Type="rfcommConnection"/>  
               <Task Type="gattCharacteristicNotification"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
     **NEW:** Bluetooth タイプ タスクを使用します。  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
               <Task Type="bluetooth"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
14. Bluetooth デバイス機能の bluetooth.rfcomm と bluetooth.genericAttributeProfile を汎用の Bluetooth 機能に置き換えます。 例えば:  
  
     **古い。**  
  
    ```xml  
    <Capabilities>  
      <m2:DeviceCapability Name="bluetooth.rfcomm">  
        <m2:Device Id="any">  
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">  
        <m2:Device Id="any">  
         <m2:Function Type="name:heartRate"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
    </Capabilities>  
    ```  
  
     **NEW:** 汎用の Bluetooth 機能に置き換えられています。  
  
    ```xml  
    <Capabilities>  
      <uap:DeviceCapability Name="bluetooth"/>  
    </Capabilities>  
  
    ```  
  
15. 非推奨の要素を削除します。  
  
    1.  これらの属性を\<VisualElements > は非推奨とされ、削除する必要があります。  
  
        -   \<VisualElements > 属性: ForegroundText、ToastCapable  
  
        -   \<DefaultTile > 属性 DefaultSize  
  
        -   \<ApplicationView > 要素  
  
         例えば:  
  
        ```xml  
        <m2:VisualElements  
            …  
            ForegroundText="dark"  
            ToastCapable="true">  
        <m2:DefaultTile DefaultSize="square150x150Logo"/>  
          <m2:ApplicationView MinWidth="width320"/>  
        </m2:VisualElements>  
  
        ```  
  
    2.  Windows.contact と windows.contactPicker 拡張子、およびこれらの拡張子の下のすべての要素を削除します。  
  
16. Package.appxmanifest ファイルを保存します。 その後、Visual Studio を閉じます。  
  
17. ソリューションを再度開く前に、いくつかの隠しファイルを削除する必要があります。  
  
    1.  ファイル エクスプローラーを開き、ツールバーの **[表示]** をクリックして、 **[非表示項目]** と **[ファイル名拡張子]** を選択します。 コンピューターにこのフォルダーを開く:\<のソリューションの場所のパス >\\.vs\\Project Name \v14 します。 .suo ファイル拡張子の付いたファイルがある場合は、それを削除します。  
  
    2.  ここで、ソリューションが存在するフォルダーに戻ります。 ソリューション内に存在するプロジェクトのフォルダーを開きます。 これらのプロジェクト フォルダー内のファイルに csproj.user または vbproj.user 拡張子がある場合、それを削除します。  
  
         これで、Visual Studio でソリューションを再び開くことができます。 ユニバーサル Windows プラットフォームを使用して、アプリをコーディング、ビルド、およびデバッグする準備ができました。  
  
         ユニバーサル Windows プラットフォームの新機能を活用するように [コードを適合させる方法](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) について説明します。  
  
##  <a name="PreviousVersions"></a> Visual Studio 2015 RC で作成された既存のユニバーサル Windows アプリの必要な変更  
 Visual Studio 2015 RC で Windows 10 ユニバーサル アプリを作成した場合は、Visual Studio 2015 の最新版のリリースでインストールされたユニバーサル Windows プラットフォームのバージョンを使用するように、プロジェクトを再ターゲットする必要があります。 以前のバージョンはサポートされていません。 必要な変更は、アプリの作成に使用した言語によって異なります。  
  
-   [C #/vb アプリ](#RCUpdate10CSharp)  
  
-   [C++ アプリ](#RCUpdate10CPlusPlus)  
  
###  <a name="RCUpdate10CSharp"></a> 最新のユニバーサル Windows プラットフォームを使用する C #/vb プロジェクトを更新します。  
 既存のアプリのソリューションを開くと、アプリを更新する必要があることが表示されます。  
  
 ![ソリューション エクスプ ローラーでプロジェクトを表示](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")  
  
 ソリューション エクスプローラーからこのプロジェクトを再読み込みすることを選択する場合は、このダイアログ ボックスが表示されます。  
  
 ![適切な SDK を使用してアプリを再ターゲット](../misc/media/missingsdkforuap.png "MissingSDKforUAP")  
  
 プロジェクトのユニバーサル Windows プラットフォーム SDK は非サポートになりましたので、インストールできません。 単に [OK] をクリックして、以下の手順に従います。  
  
##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>最新のユニバーサル Windows プラットフォームを使用するように、C#/VB のプロジェクトを更新する  
  
1.  インストールされているユニバーサル Windows プラットフォームを見つけるには、次のフォルダーを開きます: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**。 これには、インストールされているユニバーサル Windows プラットフォームごとのフォルダーの一覧が含まれています。 フォルダー名は、インストールされているユニバーサル Windows プラットフォームのバージョンです。 たとえば、この Windows 10 デバイスには、ユニバーサル Windows プラットフォームのバージョン 10.0.10240.0 がインストールされています。  
  
     ![インストールされているバージョンを表示するフォルダーを開く](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     ユニバーサル Windows プラットフォームの複数のバージョンをインストールすることができます。 アプリに対応した最新バージョンを使用することをお勧めします。  
  
2.  ファイル エクスプローラーを使用して、UWP プロジェクトが保存されているフォルダーに移動します。 ファイルの packages.config を削除し、このフォルダーに新しい .json ファイルを作成します。 ファイルの名前を project.json にして、次の内容をこのファイルに追加します。  
  
    ```json  
  
    {  
      "dependencies": {  
        "Microsoft.ApplicationInsights": "1.0.0",  
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
      },  
      "frameworks": {  
        "uap10.0": {}  
      },  
      "runtimes": {  
        "win10-arm": {},  
        "win10-arm-aot": {},  
        "win10-x86": {},  
        "win10-x86-aot": {},  
        "win10-x64": {},  
        "win10-x64-aot": {}  
      }  
    }  
  
    ```  
  
3.  Visual Studio を使用して、C#/VB ユニバーサル Windows アプリを含むソリューションを開きます。 プロジェクト ファイル (.csproj または .vbproj ファイル) を更新する必要があることが分かります。 プロジェクト ファイルを右クリックして、このファイルの編集を選択します。  
  
     ![プロジェクトを右クリックして、編集](../misc/media/uap-editproject.png "UAP_EditProject")  
  
4.  検索、 \<PropertyGroup > 要素を含む、 \<TargetPlatformVersion > と\<TargetPlatformMinVersion > 要素。 既存の値の変更、 \<TargetPlatformVersion > と\<TargetPlatformMinVersion > 要素がインストールされているユニバーサル Windows プラットフォームの同じバージョンであります。  
  
     ユニバーサル Windows アプリの既定のアセット スケールは 200 です。 Visual Studio 2015 RC が含まれる資産を 100 に拡大/縮小で作成したプロジェクトを追加する必要が、 \<UapDefaultAssetScale > この PropertyGroup に 100 の値を持つ要素。 詳細については、「 [資産とスケール](http://msdn.microsoft.com/library/jj679352.aspx)」を参照してください。  
  
5.  UWP 拡張 SDK (例: Windows Mobile SDK) に参照を追加した場合、SDK のバージョンを更新する必要があります。 たとえばこの\<SDKReference > 要素。  
  
    ```xml  
    <SDKReference Include="WindowsMobile, Version=10.0.0.1">  
          <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
    </SDKReference>  
  
    ```  
  
     次のように変更する必要があります。  
  
    ```xml  
    <SDKReference Include="WindowsMobile, Version=10.0.10240.0">  
          <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
    </SDKReference>  
  
    ```  
  
6.  検索、\<ターゲット > 値を含む name 属性を持つ要素: EnsureNuGetPackageBuildImports します。 この要素とそのすべての子要素を削除します。  
  
    ```xml  
    <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">  
        <PropertyGroup>  
          <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>  
        </PropertyGroup>  
        <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />  
        <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />  
    </Target>  
    ```  
  
7.  検索し、削除、\<インポート > Microsoft.Diagnostics.Tracing.EventSource と Microsoft.ApplicationInsights を参照するプロジェクトと条件の属性を持つ要素には、このような。  
  
    ```xml  
    <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />  
    <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />  
  
    ```  
  
8.  検索、 \<ItemGroup > を持つ\<参照 > 子要素を NuGet パッケージ。 この情報は今後のステップに必要なので、参照している NuGet パッケージに注意してください。 Visual Studio 2015 RC と Visual Studio 2015 RTM の間での Windows 10 プロジェクトの形式における 1 つの大きな違いは、RTM の形式では [NuGet](http://docs.nuget.org/) バージョン 3 を使用することです。  
  
     削除、 \<ItemGroup > とそのすべての子。 たとえば、Visual Studio RC で作成された、ある UWP プロジェクトでは次の NuGet パッケージを削除する必要があるかもしれません。  
  
    ```xml  
    <ItemGroup>  
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
      </ItemGroup>  
  
    ```  
  
9. 検索、 \<ItemGroup > 要素を含む、 \<AppxManifest > 要素。 ある場合、 \<None > に設定された Include 属性を持つ要素: packages.config を削除します。 また、追加、 \<None > 要素を含める属性し、その値に設定: project.json。  
  
10. 変更内容を保存します。 その後、プロジェクト ファイルを閉じます。  
  
11. ソリューション エクスプローラーでプロジェクト ファイルを右クリックし、コンテキスト メニューの [プロジェクトの再読み込み] をクリックします。 これで、プロジェクト内のすべてのファイルがソリューション エクスプローラーに表示されます。  
  
12. ソリューション エクスプローラーで、ApplicationInsights.config のファイルを選択し、そのプロパティを開きます。 "ビルド アクション" プロパティを "コンテンツ" に変更し、"出力ディレクトリにコピー" プロパティを "新しい場合はコピーする" に変更します。  
  
13. プロジェクトの Package.appxmanifest ファイルを開きます。  
  
    1.  検索、 \<TargetDeviceFamily > 要素。 MinVersion と MaxVersionTested 属性を変更して、インストールしたユニバーサル Windows プラットフォームのバージョンに対応させます。 以下に例を示します。  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  変更内容を保存します。  
  
14. 前の手順で削除したパッケージを追加するには、NuGet マネージャーを使用します。 Visual Studio 2015 RC と Visual Studio 2015 RTM の間での Windows 10 プロジェクトの形式における 1 つの大きな違いは、RTM の形式では [NuGet](http://docs.nuget.org/) バージョン 3 を使用することです。  
  
 これで、アプリをコーディング、ビルド、およびデバッグすることができます。  
  
 ユニバーサル Windows アプリの単体テスト プロジェクトがある場合は、 [これらの手順](#MigrateUnitTest)も行う必要があります。  
  
###  <a name="RCUpdate10CPlusPlus"></a> 最新のユニバーサル Windows プラットフォームを使用する C++ プロジェクトを更新します。  
  
1.  インストールされているユニバーサル Windows プラットフォームを見つけるには、次のフォルダーを開きます: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**。 これには、インストールされているユニバーサル Windows プラットフォームごとのフォルダーの一覧が含まれています。 フォルダー名は、インストールされているユニバーサル Windows プラットフォームのバージョンです。 たとえば、この Windows 10 デバイスには、ユニバーサル Windows プラットフォームのバージョン 10.0.10240.0 がインストールされています。  
  
     ![インストールされているバージョンを表示するフォルダーを開く](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     ユニバーサル Windows プラットフォームの複数のバージョンをインストールすることができます。 アプリに対応した最新バージョンを使用することをお勧めします。  
  
2.  C++ Windows ユニバーサル アプリを含むソリューションを開きます。 プロジェクト .vcxproj ファイルを右クリックして、プロジェクト ファイルのアンロードを選択します。 プロジェクトをアンロードした後、プロジェクト ファイルを再度右クリックして、その編集を選択します。  
  
     ![プロジェクトをアンロードし、プロジェクト ファイルを編集](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")  
  
3.  見つかった\<PropertyGroup > 要素の Condition 属性が含まれていませんが、実行が含まれている、 \<ApplicationTypeRevision > 要素。 ApplicationTypeRevision の値を 8.2 から 10.0 に更新します。 追加、 \<WindowsTargetPlatformVersion > と\<WindowsTargetPlatformMinVersion > 要素をインストールしたユニバーサル Windows プラットフォームのバージョンの値には、その値を設定するとします。  
  
     追加、 \<EnableDotNetNativeCompatibleProfile > 要素とその値を要素が存在しない場合は true に設定します。  
  
     ユニバーサル Windows アプリの既定のアセット スケールは 200 です。 Visual Studio 2015 RC が含まれる資産を 100 に拡大/縮小で作成したプロジェクトを追加する必要が、 \<UapDefaultAssetScale > この PropertyGroup に 100 の値を持つ要素。 詳細については、「 [資産とスケール](http://msdn.microsoft.com/library/jj679352.aspx)」を参照してください。  
  
     したがって、 \<PropertyGroup > 要素に次のようになります。  
  
    ```xml  
    <PropertyGroup Label="Globals">  
        …  
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>  
        <ApplicationType>Windows Store</ApplicationType>  
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
        <UapDefaultAssetScale>100</UapDefaultAssetScale>  
      </PropertyGroup>  
  
    ```  
  
4.  残りの\<PropertyGroup > 要素で要素が、リリース構成での Condition 属性を確認します。 含まれていない場合、 \<UseDotNetNativeToolchain > 要素、1 つを追加します。 値を設定、 \<UseDotNetNativeToolchain > 要素を次のように、true にします。  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
5.  更新する必要がある、 \<EnableDotNetNativeCompatibleProfile > 要素と\<UseDotNetNativeToolchain > C++ テンプレートでは、.NET ネイティブですが .NET Native を有効にする要素が有効になっていません。  
  
     変更内容を保存します。 その後、プロジェクト ファイルを閉じます。  
  
6.  ソリューション エクスプローラーでプロジェクト ファイルを右クリックし、コンテキスト メニューの [プロジェクトの再読み込み] をクリックします。 これで、プロジェクト内のすべてのファイルがソリューション エクスプローラーに表示されます。  
  
7.  プロジェクトの Package.appxmanifest ファイルを開きます。  
  
    1.  検索、 \<TargetDeviceFamily > 要素。 MinVersion と MaxVersionTested 属性を変更して、インストールしたユニバーサル Windows プラットフォームのバージョンに対応させます。 以下に例を示します。  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  変更内容を保存します。  
  
         これで、アプリをコーディング、ビルド、およびデバッグすることができます。  
  
         ユニバーサル Windows アプリの単体テスト プロジェクトがある場合は、 [これらの手順](#MigrateUnitTest)も行う必要があります。  
  
##  <a name="MigrateUnitTest"></a> Visual Studio 2015 RC で作成されたユニバーサル Windows アプリの単体テスト プロジェクトを既存の必要な変更  
 Visual Studio 2015 RC で Windows 10 ユニバーサル アプリの単体テスト プロジェクトを作成した場合、これらの追加の変更をプロジェクト ファイルに行い、Visual Studio 2015 の最新版のリリースでこれらのテスト プロジェクトを使用するようにしなければなりません。 必要な変更は、アプリの作成に使用した言語によって異なります。  
  
-   [C #/vb アプリ](#UnitTestRCUpdate10CSharp)  
  
-   [C++ アプリ](#UnitTestRCUpdate10CPlusPlus)  
  
###  <a name="UnitTestRCUpdate10CSharp"></a> C #/vb 単体テスト プロジェクトを更新します。  
  
1.  Visual Studio を使用して、C#/VB 単体テスト プロジェクトを含むソリューションを開きます。 値を変更、 \<OuttputType > 要素を: AppContainerExe します。  
  
    ```xml  
  
    <OutputType>AppContainerExe</OutputType>  
  
    ```  
  
2.  この要素を置き換えます\<EnableCoreRuntime > false\</EnableCoreRuntime > 次の要素を使用します。  
  
    ```xml  
  
    <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
  
    ```  
  
3.  次の行を削除します。  
  
    ```xml  
  
    <PropertyGroup>  
        <AppXPackage>True</AppXPackage>  
        <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>  
     </PropertyGroup>  
     <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
     <PlatformTarget>AnyCPU</PlatformTarget>  
     <DebugSymbols>true</DebugSymbols>  
     <DebugType>full</DebugType>  
     <Optimize>false</Optimize>  
     <OutputPath>bin\Debug\</OutputPath>  
     <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
     <ErrorReport>prompt</ErrorReport>  
     <WarningLevel>4</WarningLevel>  
     </PropertyGroup>  
     <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
     </PropertyGroup>  
  
    ```  
  
4.  この要素を追加\<UseDotNetNativeToolchain > true\</UseDotNetNativeToolchain > これらのプロパティ グループに子要素として。  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">  
  
    ```  
  
5.  次の削除\<ItemGroup > 要素。  
  
    ```xml  
  
    <ItemGroup>  
       <Compile Include="Properties\AssemblyInfo.cs" />  
       <Compile Include="UnitTest.cs" />  
    </ItemGroup>  
    <ItemGroup>  
       <AppxManifest Include="Package.appxmanifest">  
          <SubType>Designer</SubType>  
       </AppxManifest>  
       <None Include="packages.config" />  
       <None Include="UnitTestProject1_TemporaryKey.pfx" />  
    </ItemGroup>  
    <ItemGroup>  
       <Content Include="Properties\Default.rd.xml" />  
       <Content Include="Assets\Logo.scale-240.png" />  
       <Content Include="Assets\SmallLogo.scale-240.png" />  
       <Content Include="Assets\SplashScreen.scale-240.png" />  
       <Content Include="Assets\Square71x71Logo.scale-240.png" />  
       <Content Include="Assets\StoreLogo.scale-240.png" />  
       <Content Include="Assets\WideLogo.scale-240.png" />  
    </ItemGroup>  
  
    ```  
  
     これらの要素に置き換えます。  
  
    ```xml  
  
    <ItemGroup>  
       <Compile Include="Properties\AssemblyInfo.cs" />  
       <Compile Include="UnitTestApp.xaml.cs">  
          <DependentUpon>UnitTestApp.xaml</DependentUpon>  
       </Compile>  
       <Compile Include="UnitTest.cs" />  
    </ItemGroup>  
    <ItemGroup>  
       <ApplicationDefinition Include="UnitTestApp.xaml">  
          <Generator>MSBuild:Compile</Generator>  
          <SubType>Designer</SubType>  
       </ApplicationDefinition>  
    </ItemGroup>  
    <ItemGroup>  
       <AppxManifest Include="Package.appxmanifest">  
          <SubType>Designer</SubType>  
       </AppxManifest>  
       <None Include="UnitTestProject1_TemporaryKey.pfx" />  
    </ItemGroup>  
    <ItemGroup>  
       <Content Include="Properties\UnitTestApp.rd.xml" />  
       <Content Include="Assets\LockScreenLogo.scale-200.png" />  
       <Content Include="Assets\SplashScreen.scale-200.png" />  
       <Content Include="Assets\Square150x150Logo.scale-200.png" />  
       <Content Include="Assets\Square44x44Logo.scale-200.png" />  
       <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
       <Content Include="Assets\StoreLogo.png" />  
       <Content Include="Assets\Wide310x150Logo.scale-200.png" />  
    </ItemGroup>  
    ```  
  
6.  新しい単体テスト プロジェクトを作成し、UnitTestApp.xaml と UnitTestApp.xaml.cs ファイルをその新規のプロジェクトから、更新している既存の単体テスト プロジェクトにコピーします。  
  
7.  UnitTestApp.rd.xml ファイルを新しい単体テスト プロジェクトのプロパティ フォルダーから、更新している既存の単体テスト プロジェクトのプロパティ フォルダーにコピーします。  
  
8.  プロジェクトの Package.appxmanifest ファイルを開きます。 次に、これらの要素を以下から削除します。  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"  
             Executable="vstest.executionengine.appcontainer.uap.exe"  
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
          <uap:VisualElements  
             DisplayName="UnitTestProject1"  
             Square150x150Logo="Assets\Logo.png"  
             Square44x44Logo="Assets\SmallLogo.png"  
             Description="UnitTestProject1"  
             BackgroundColor="#464646">  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClientServer" />  
    </Capabilities>  
    ```  
  
     これらの削除された要素を次の要素に置き換えます。 ProjectName の値として、以下の要素の UnitTestProject1 ではなく、プロジェクトの名前に基づく適切な値を使用します。  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"   
             Executable="$targetnametoken$.exe"  
             EntryPoint="UnitTestProject1.App">  
          <uap:VisualElements  
                DisplayName="UnitTestProject1"  
                Square150x150Logo="Assets\Square150x150Logo.png"  
                Square44x44Logo="Assets\Square44x44Logo.png"  
                Description="UnitTestProject1"  
                BackgroundColor="transparent">  
             <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClient" />  
    </Capabilities>  
    ```  
  
 これで単体テストを実行できます。  
  
###  <a name="UnitTestRCUpdate10CPlusPlus"></a> 最新のユニバーサル Windows プラットフォームを使用する C++ プロジェクトを更新します。  
  
1.  Visual Studio を使用して、C++ 単体テスト プロジェクトを含むソリューションを開きます。 次の要素を削除します。  
  
    ```xml  
  
    <TestApplication>true</TestApplication>  
    <AppxPackage>True</AppxPackage>  
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>  
    <EnableCoreRuntime>false</EnableCoreRuntime>  
  
    ```  
  
2.  次の追加\<ProjectConfiguration > 要素がこの要素の下\<ItemGroup Label ="ProjectConfigurations"> されていないこのファイルの場合。  
  
    ```xml  
  
    <ProjectConfiguration Include="Debug|x64">  
       <Configuration>Debug</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|x64">  
       <Configuration>Release</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
  
    ```  
  
3.  この要素のすべての出現箇所を置き換えます。  
  
    ```xml  
  
    <ConfigurationType>DynamicLibrary</ConfigurationType>  
  
    ```  
  
     以下に置き換えます。  
  
    ```xml  
  
    <ConfigurationType>Application</ConfigurationType>  
  
    ```  
  
4.  次の追加\<PropertyGroup > 要素がないファイルの場合。  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>true</UseDebugLibraries>  
       <PlatformToolset>v140</PlatformToolset>  
    </PropertyGroup>  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>false</UseDebugLibraries>  
       <WholeProgramOptimization>true</WholeProgramOptimization>  
       <PlatformToolset>v140</PlatformToolset>  
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
    </PropertyGroup>  
  
    ```  
  
5.  この要素のすべての出現箇所を置き換えます。  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
    ```  
  
     以下に置き換えます。  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
  
    ```  
  
6.  この要素のすべての出現箇所を置き換えます。  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
     以下に置き換えます。  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
7.  次の追加\<ItemDefinitionGroup > 要素が既に含まれているその他のセクションでは\<ItemDefinitionGroup > 要素。  
  
    ```xml  
  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
    <Link>  
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
    </Link>  
    </ItemDefinitionGroup>  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
       <Link>  
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
       </Link>  
    </ItemDefinitionGroup>  
  
    ```  
  
8.  次の削除\<ItemGroup > 要素。  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\Logo.scale-100.png" />  
       <Image Include="Assets\SmallLogo.scale-100.png" />  
       <Image Include="Assets\StoreLogo.scale-100.png" />  
       <Image Include="Assets\SplashScreen.scale-100.png" />  
       <Image Include="Assets\WideLogo.scale-100.png" />  
    </ItemGroup>  
  
    ```  
  
     この置き換えます\<ItemGroup > 要素。  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\LockScreenLogo.scale-200.png" />  
       <Image Include="Assets\SplashScreen.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
       <Image Include="Assets\Square150x150Logo.scale-200.png" />  
       <Image Include="Assets\StoreLogo.png" />  
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />  
    </ItemGroup>  
  
    ```  
  
9. 次の削除\<ItemGroup > 要素。  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
    </ItemGroup>  
    ```  
  
     これら置き換えます\<ItemGroup > 要素。  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
       <ClInclude Include="UnitTestApp.xaml.h">  
          <DependentUpon>UnitTestApp.xaml</DependentUpon>  
       </ClInclude>  
    </ItemGroup>  
    <ItemGroup>  
       <ApplicationDefinition Include="UnitTestApp.xaml">  
          <SubType>Designer</SubType>  
       </ApplicationDefinition>  
    </ItemGroup>  
  
    ```  
  
10. 次の要素を削除します。  
  
    ```xml  
    <ClCompile Include="UnitTest.cpp"/>  
    ```  
  
     これら置き換えます\<CICompile > 要素。  
  
    ```xml  
  
    <ClCompile Include="UnitTestApp.xaml.cpp">  
       <DependentUpon>UnitTestApp.xaml</DependentUpon>  
    </ClCompile>  
    <ClCompile Include="UnitTest.cpp"/>  
  
    ```  
  
11. この要素を追加します。  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />  
    ```  
  
     ファイル内のこの要素の上に追加します。  
  
    ```xml  
  
    <ItemGroup>  
       <Xml Include="UnitTestApp.rd.xml" />  
    </ItemGroup>  
    ```  
  
12. 新しい単体テスト C++ プロジェクトを作成し、そのプロジェクトから更新中の既存の単体テスト プロジェクトに UnitTestApp.xaml、UnitTestApp.xaml.cpp、UnitTestApp.xaml.h、および UnitTestApp.rd.xml ファイルをコピーします。  
  
13. プロジェクトの Package.appxmanifest ファイルを開きます。 次に、これらの要素を以下から削除します。  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"  
             Executable="vstest.executionengine.appcontainer.uap.exe"  
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
          <uap:VisualElements  
             DisplayName="UnitTestProject1"  
             Square150x150Logo="Assets\Logo.png"  
             Square44x44Logo="Assets\SmallLogo.png"  
             Description="UnitTestProject1"  
             BackgroundColor="#464646">  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClientServer" />  
    </Capabilities>  
  
    ```  
  
     これらの削除された要素を次の要素に置き換えます。 ProjectName の値として、以下の要素の UnitTestProject1 ではなく、プロジェクトの名前に基づく適切な値を使用します。  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"   
                Executable="$targetnametoken$.exe"  
                EntryPoint="UnitTestProject1.App">  
          <uap:VisualElements  
                DisplayName="UnitTestProject1"  
                Square150x150Logo="Assets\Square150x150Logo.png"  
                Square44x44Logo="Assets\Square44x44Logo.png"  
                Description="UnitTestProject1"  
                BackgroundColor="transparent">  
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
                <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClient" />  
    </Capabilities>  
  
    ```
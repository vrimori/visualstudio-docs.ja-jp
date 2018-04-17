---
title: プロジェクトの種類を登録する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e6c91f2c92dd121cd135aef4291c7f7983206ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="registering-a-project-type"></a>プロジェクトの種類を登録します。
新しいプロジェクトの種類を作成するときに、有効にするレジストリ エントリを作成する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を認識し、プロジェクトの種類を使用します。 通常、これらのレジストリ エントリは、レジストリ スクリプト (.rgs) ファイルを使用して作成します。  
  
 次の例では、レジストリからステートメントの既定のパスを指定してデータ該当する場合、後の表の各ステートメントに対してレジストリ スクリプトからエントリを含むです。 テーブルは、スクリプトのエントリと、ステートメントに関する追加情報を提供します。  
  
> [!NOTE]
>  次のレジストリ情報は、型の例と記述したことには、プロジェクトの種類を登録するレジストリ スクリプト内のエントリの目的をするものではします。 実際のエントリとその用途は、プロジェクトの種類の特定の要件によって異なる可能性があります。 を開発しているプロジェクトの種類とよく似た検索に使用可能なサンプルを確認し、サンプルでのレジストリ スクリプトを確認する必要があります。  
  
 次の例では、HKEY_CLASSES_ROOT からです。  
  
## <a name="example"></a>例  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|プロジェクトの名前と説明を拡張子 .figp を持つファイルを入力します。|  
|`Content Type`|REG_SZ|`Text/plain`|プロジェクト ファイルのコンテンツ タイプ。|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|既定のアイコンがこの種類のプロジェクトで使用します。 % モジュール % ステートメントは、DLL プロジェクトの種類の既定の場所をレジストリに完了します。|  
|`@`|REG_SZ|`&Open in Visual Studio`|既定のアプリケーションのこの種類のプロジェクトを開きます。|  
|`@`|REG_SZ|`devenv.exe "%1"`|この種類のプロジェクトを開いたときに実行される既定のコマンド。|  
  
 次の例では、HKEY_LOCAL_MACHINE からし、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] の下にあります。  
  
## <a name="example"></a>例  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|`@` (既定値)|REG_SZ|`FigPrj Project VSPackage`|ローカライズ可能な名前では、VSPackage (プロジェクトの種類) を登録します。|  
|`InprocServer32`|REG_SZ|`%MODULE%`|プロジェクトの種類の DLL のパス。 IDE は、この DLL を読み込み、VSPackage CLSID`DllGetClassObject`を取得する<xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory>構築するために、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>オブジェクト。|  
|`CompanyName`|REG_SZ|`Microsoft`|プロジェクトの種類を開発した会社の名前です。|  
|`ProductName`|REG_SZ|`Figure Project Sample`|プロジェクトの種類の名前です。|  
|`ProductVersion`|REG_SZ|`9.0`|プロジェクトの種類のバージョン番号を解放します。|  
|`MinEdition`|REG_SZ|`professional`|登録される VSPackage のエディションです。|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|パッケージは、VSPackage プロジェクトのキーを読み込みます。 環境が開始した後、プロジェクトが読み込まれるときに、キーが検証されます。|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|サテライト DLL を含むプロジェクトの種類のローカライズされたリソースのファイル名。|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|サテライト DLL のパス。|  
|`FigProjectsEvents`|REG_SZ|値のステートメントを参照してください。|このオートメーション イベントに対して返されるテキスト文字列を決定します。|  
|`FigProjectItemsEvents`|REG_SZ|値のステートメントを参照してください。|このオートメーション イベントに対して返されるテキスト文字列を決定します。|  
  
 すべての次の例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] の下にあります。  
  
## <a name="example"></a>例  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|この種類のプロジェクトの既定の名前。|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|パッケージ サテライト DLL から取得する名前のリソース ID が登録されています。|  
|`Package`|REG_SZ|`%CLSID_Package%`|パッケージ、VSPackage のクラス ID が登録されています。|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|プロジェクト テンプレート ファイルの既定のパス。 これらは、ファイルが新しいプロジェクト テンプレートが表示されます。|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|プロジェクト項目テンプレート ファイルの既定のパス。 これらは、ファイルが新しい項目の追加のテンプレートが表示されます。|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|実装するための IDE をできるように、**開く** ダイアログ ボックス。|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|IDE で使用すると、開いているプロジェクトはこのプロジェクトの種類 (プロジェクト ファクトリ) によって処理されるかどうかを決定します。 複数のエントリの形式は、セミコロンで区切られた一覧を示します。 たとえば「vdproj; vdp」です。|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|名前を付けて保存操作の既定のファイル名拡張子として、IDE で使用します。|  
|`Filter Settings`|REG_DWORD|さまざまなには、ステートメントとコメントを次の表を参照してください。|これらの設定は、UI ダイアログ ボックスにファイルを表示するためのさまざまなフィルターの設定に使用されます。|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|項目の追加テンプレートのリソース ID です。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|ダイアログ ボックスに表示されるプロジェクト アイテムのパス、**新しい項目の追加**テンプレート。|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|ツリー ノードに表示されるファイルの並べ替え順序を決定、**新しい項目の追加** ダイアログ ボックス。|  
  
 次の表は、前のコード セグメントで使用できるフィルター オプションを示します。  
  
|フィルター オプション|説明|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|一般的なフィルターのいずれかのフィルターがあることを示します、**ファイル内の検索** ダイアログ ボックス。 一般的なフィルターは、一般的でマークされていないフィルターの前に、フィルター一覧に表示されます。|  
|`CommonOpenFilesFilter`|一般的なフィルターのいずれかのフィルターがあることを示します、**ファイルを開く** ダイアログ ボックス。 一般的なフィルターは、一般的でマークされていないフィルターの前に、フィルター一覧に表示されます。|  
|`FindInFilesFilter`|なることを示します、フィルターのフィルターのいずれか、**ファイル内の検索** ダイアログ ボックスし、一般的なフィルターの後に一覧表示されます。|  
|`NotOpenFileFilter`|にフィルターが使用されませんが、**ファイルを開く** ダイアログ ボックス。|  
|`NotAddExistingItemFilter`|フィルターは使用しないことの追加を示します**既存項目の** ダイアログ ボックス。|  
  
 既定では、フィルターが 1 つまたは複数これらのフラグを設定場合、フィルターを使用で、**既存項目の追加** ダイアログ ボックスおよび**ファイルを開く** ダイアログ ボックスの後に、一般的なフィルターの一覧が表示されます。 フィルターが使用されていない、**ファイル内の検索** ダイアログ ボックス。  
  
 すべての次の例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] の下にあります。  
  
## <a name="example"></a>例  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新しいプロジェクト テンプレートのリソース ID です。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|既定の登録済みのプロジェクトの種類のプロジェクトのパス。|  
|`SortPriority`|REG_DWORD|`41 (x29)`|セットは、新しいプロジェクト ウィザード ダイアログ ボックスに表示されるプロジェクトの順序を並べ替えます。|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 は、この種類のプロジェクトが、[新しいプロジェクト] ダイアログ ボックスでのみ表示されることを示します。|  
  
 すべての次の例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] の下にあります。  
  
## <a name="example"></a>例  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|なし|次のエントリはその他のファイル プロジェクト項目であることを示します。 既定値です。|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|新しい項目の追加のテンプレート ファイルのリソース ID 値です。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|既定で表示される項目のパス、**新しい項目の追加** ダイアログ ボックス。|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|[ツリー ノードに表示するための並べ替え順序を確立、**新しい項目の追加**] ダイアログ ボックス。|  
  
 次の例については、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] の下にあります。  
  
## <a name="example"></a>例  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 メニュー項目は、メニューの情報を取得するために使用するリソースを IDE を指します。 メニュー データベースにこのデータがマージされた、ときに、同じキーがレジストリの MenusMerged セクションに追加されます。 VSPackage 必要があります MenusMerged セクションの下にあるものを直接変更します。 次の表に、データ フィールドでは、次の 3 つコンマ区切りのフィールドがあります。 最初のフィールドには、メニュー リソース ファイルの完全なパスを識別します。  
  
-   最初のフィールドを省略すると、メニュー リソースがサテライト VSPackage GUID によって識別される DLL から読み込まれます。  
  
 2 番目のフィールドには、型 CTMENU のメニュー リソース ID を識別します。  
  
-   リソース ID を指定すると、ファイルのパスは、最初のパラメーターによって指定された場合は、メニュー リソースが完全ファイル パスから読み込まれます。  
  
-   リソース ID が指定されましたが、ファイル パスは、メニュー リソースがサテライト DLL から読み込まれます。  
  
-   ファイルの完全パスを指定すると、リソース ID を省略すると、読み込まれるファイルは CTO ファイルであると想定されます。  
  
 最後のフィールドは、CTMENU のリソースのバージョン番号を識別します。 バージョン番号を変更することで、メニューをもう一度マージできます。  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|CLSID_Package %|REG_SZ|`,1000,1`|メニューの情報を取得するリソース。|  
  
 すべての次の例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] の下にあります。  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|図のプロジェクトの新しいプロジェクト テンプレートのリソース ID 値です。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|新しいプロジェクト ディレクトリの既定のパス。 このディレクトリ内の項目が表示されます、**新しいプロジェクト ウィザード** ダイアログ ボックス。|  
|`SortPriority`|REG_DWORD|`41 (x29)`|プロジェクトがのツリー ノードで表示する順序を確立、**新しいプロジェクト** ダイアログ ボックス。|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|この種類のプロジェクトがのみに表示されている場合は 0、**新しいプロジェクト** ダイアログ ボックス。|  
  
 次の例については、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] の下にあります。  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|登録済みの VSPackage のクラス ID。|  
|`UseInterface`|REG_DWORD|`1`|1 は、UI がこのプロジェクトとの対話に使用されることを示します。 0 は、UI インターフェイスがないことを示します。|  
  
 The.vsz ファイル頻繁に新しいプロジェクトの種類を制御するにはには、RELATIVE_PATH エントリが含まれます。 このパス \ProductDir エントリ、プロジェクトの種類、次のセットアップ キーの下にある指定されたパスに対する相対パスです。  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 たとえば、Enterprise Frameworks プロジェクト テンプレートは、次のレジストリ エントリを追加します。  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir C:\Program files \microsoft Visual Studio\EnterpriseFrameworks\ を =  
  
 かどうか、PROJECT_TYPE を追加することを意味する前に指定した ProductDir ディレクトリにファイルを .vsz 環境検索の .vsz ファイル EF エントリを = です。  
  
## <a name="see-also"></a>関連項目  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)   
 [プロジェクト ファクトリを使用したプロジェクト インスタンスの作成](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
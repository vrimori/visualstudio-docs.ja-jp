---
title: プロジェクトの種類を登録する |Microsoft Docs
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
ms.openlocfilehash: 1839ed51b3bd8b26bd67583054fa142f5853a2de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939685"
---
# <a name="registering-a-project-type"></a>プロジェクト タイプの登録
新しいプロジェクトの種類を作成するときに、有効にするレジストリ エントリを作成する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を認識し、プロジェクトの種類を使用します。 通常、これらのレジストリ エントリは、レジストリ スクリプト (.rgs) ファイルを使用して作成します。  
  
 次の例で、レジストリからステートメントは、既定のパスを提供し、データ該当する場合、後の表の各ステートメントに対してレジストリ スクリプトからエントリを含みます。 テーブルでは、スクリプトのエントリと、ステートメントに関する追加情報を提供します。  
  
> [!NOTE]
>  次のレジストリ情報は、型の例と、プロジェクトの種類を登録する記述したレジストリ スクリプト内のエントリの目的で対象としています。 実際のエントリとその用途は、プロジェクトの種類の特定の要件に基づいて異なる場合があります。 を開発しているプロジェクトの種類に近いものを検索する使用可能なサンプルを確認し、サンプル レジストリ スクリプトを確認し、する必要があります。  
  
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
|`@`|REG_SZ|`FigPrjFile`|プロジェクトの名前と説明を持つ拡張 .figp ファイルを入力します。|  
|`Content Type`|REG_SZ|`Text/plain`|プロジェクト ファイルのコンテンツ タイプ。|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|この種類のプロジェクトに使用される既定のアイコン。 % モジュールの % ステートメントは、レジストリ、DLL プロジェクトの種類の既定の場所に完了します。|  
|`@`|REG_SZ|`&Open in Visual Studio`|既定のアプリケーションがこの種類のプロジェクトを開きます。|  
|`@`|REG_SZ|`devenv.exe "%1"`|この種類のプロジェクトを開いたときに実行される既定のコマンド。|  
  
 次の例では、HKEY_LOCAL_MACHINE からはあり、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] の下にあります。  
  
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
|`InprocServer32`|REG_SZ|`%MODULE%`|プロジェクトの種類の DLL のパス。 IDE は、この DLL を読み込み、VSPackage の CLSID`DllGetClassObject`させる<xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory>を構築する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>オブジェクト。|  
|`CompanyName`|REG_SZ|`Microsoft`|プロジェクトの種類を開発した会社の名前です。|  
|`ProductName`|REG_SZ|`Figure Project Sample`|プロジェクトの種類の名前。|  
|`ProductVersion`|REG_SZ|`9.0`|プロジェクトの種類のバージョン番号を解放します。|  
|`MinEdition`|REG_SZ|`professional`|VSPackage の登録されているのエディションです。|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|パッケージは、VSPackage プロジェクトのキーを読み込みます。 環境が開始した後、プロジェクトが読み込まれるときに、キーが検証されます。|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|サテライト DLL を含むプロジェクトの種類のローカライズされたリソースのファイル名。|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|サテライト DLL のパス。|  
|`FigProjectsEvents`|REG_SZ|値のステートメントを参照してください。|このオートメーション イベントの返されるテキスト文字列を決定します。|  
|`FigProjectItemsEvents`|REG_SZ|値のステートメントを参照してください。|このオートメーション イベントの返されるテキスト文字列を決定します。|  
  
 次のすべての例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] の下に配置されます。  
  
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
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|パッケージ サテライト DLL から取得する名前のリソース ID が登録されます。|  
|`Package`|REG_SZ|`%CLSID_Package%`|パッケージの下、VSPackage のクラス ID が登録されます。|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|プロジェクト テンプレート ファイルの既定のパス。 これらは、新しいプロジェクト テンプレートによって表示されるファイルです。|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|プロジェクト項目テンプレート ファイルの既定のパス。 これらは、新しい項目の追加テンプレートによって表示されるファイルです。|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|実装するための IDE により、**オープン** ダイアログ ボックス。|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|IDE で使用すると、開いているプロジェクトはこのプロジェクトの種類 (プロジェクト ファクトリ) によって処理されるかどうかを決定します。 1 つ以上のエントリの形式は、セミコロンで区切られたリストです。 たとえば「vdproj; vdp」。|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|名前を付けて保存操作の既定のファイル名拡張子として IDE によって使用します。|  
|`Filter Settings`|REG_DWORD|、さまざまなステートメントとコメントを以下の表を参照してください。|これらの設定は、UI のダイアログ ボックスでファイルを表示するためのさまざまなフィルターの設定に使用されます。|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|項目の追加テンプレートのリソース ID。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|ダイアログ ボックスに表示されるプロジェクト項目のパス、**新しい項目の追加**テンプレート。|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|ツリー ノードに表示されるファイルの並べ替え順序を決定、**新しい項目の追加** ダイアログ ボックス。|  
  
 次の表では、前のコード セグメントで使用できるフィルター オプションを示します。  
  
|フィルター オプション|説明|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|フィルターの一般的なフィルターの 1 つあることを示します、**ファイル内の検索** ダイアログ ボックス。 一般的なフィルターは、一般的でマークされていないフィルターの前に、フィルター一覧に表示されます。|  
|`CommonOpenFilesFilter`|フィルターの一般的なフィルターの 1 つあることを示します、**ファイルを開く** ダイアログ ボックス。 一般的なフィルターは、一般的でマークされていないフィルターの前に、フィルター一覧に表示されます。|  
|`FindInFilesFilter`|フィルターには内のフィルターのいずれかを示します、**ファイル内の検索** ダイアログ ボックスし、一般的なフィルターの後に表示されます。|  
|`NotOpenFileFilter`|フィルターで使用されませんが、**ファイルを開く** ダイアログ ボックス。|  
|`NotAddExistingItemFilter`|フィルターを追加で使用されませんが**既存項目の** ダイアログ ボックス。|  
  
 既定では、フィルターに 1 つがないか、これらのフラグを設定場合、フィルターが使用、**既存項目の追加** ダイアログ ボックスおよび**ファイルを開く**一般的なフィルターが表示された後ダイアログ ボックス。 フィルターが使用されていない、**ファイル内の検索** ダイアログ ボックス。  
  
 次のすべての例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] の下に配置されます。  
  
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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新しいプロジェクト テンプレートのリソース ID。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|既定の登録済みのプロジェクトの種類のプロジェクトのパス。|  
|`SortPriority`|REG_DWORD|`41 (x29)`|セットは、新しいプロジェクト ウィザード ダイアログ ボックスに表示されるプロジェクトの順序を並べ替えます。|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 は、新しいプロジェクト ダイアログ ボックスでのみ、この種類のプロジェクトが表示されることを示します。|  
  
 次のすべての例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] の下に配置されます。  
  
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
|`@`|REG_SZ|なし|次のエントリがその他のファイル プロジェクト項目のことを示す既定値。|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|新しい項目の追加のテンプレート ファイルのリソース ID 値です。|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|表示される項目の既定のパス、**新しい項目の追加** ダイアログ ボックス。|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|ツリー ノードに表示するための並べ替え順序を確立、**新しい項目の追加** ダイアログ ボックス。|  
  
 次の例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] の下にあります。  
  
## <a name="example"></a>例  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 メニュー エントリは、メニューの情報を取得するために使用するリソースを IDE を指します。 メニュー データベースにこのデータを結合すると、同じキーがレジストリの MenusMerged セクションに追加されます。 VSPackage は変更しないでください MenusMerged セクションでは何も直接します。 データ フィールドで、次の表には、次の 3 つコンマ区切りのフィールドがあります。 最初のフィールドは、メニュー リソース ファイルの完全なパスを識別します。  
  
- 最初のフィールドを省略すると、メニュー リソースがサテライト VSPackage の GUID で識別される DLL から読み込まれます。  
  
  2 番目のフィールドは、型 CTMENU のメニュー リソース ID を識別します。  
  
- リソース ID を指定すると、ファイルのパスは、最初のパラメーターに指定された場合は、メニュー リソースがファイルの完全パスから読み込まれます。  
  
- リソース ID を指定すると、ファイルのパスでない場合、メニュー リソースがサテライト DLL から読み込まれます。  
  
- ファイルの完全パスを指定し、リソース ID を省略すると場合、読み込まれるファイルは CTO ファイルが必要です。  
  
  最後のフィールドは、CTMENU のリソースのバージョン番号を識別します。 バージョン番号を変更することで、メニューをもう一度マージできます。  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|CLSID_Package %|REG_SZ|`,1000,1`|メニューの情報を取得するリソース。|  
  
 次のすべての例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] の下に配置されます。  
  
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
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|新しいプロジェクトのディレクトリの既定のパス。 このディレクトリ内の項目が表示されます、**新しいプロジェクト ウィザード** ダイアログ ボックス。|  
|`SortPriority`|REG_DWORD|`41 (x29)`|プロジェクトがのツリー ノードに表示する順序を確立、**新しいプロジェクト** ダイアログ ボックス。|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 は、この種類のプロジェクトがでのみ表示されることを示します、**新しいプロジェクト** ダイアログ ボックス。|  
  
 次の例は、レジストリ キー [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] の下にあります。  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|登録済みの VSPackage のクラス ID。|  
|`UseInterface`|REG_DWORD|`1`|1 は、このプロジェクトと対話する UI が使用されることを示します。 0 は、UI インターフェイスがないことを示します。|  
  
 頻繁に新しいプロジェクトの種類を制御する The.vsz ファイルには、RELATIVE_PATH エントリが含まれます。 このパスは、次のセットアップ キーの種類のプロジェクトの \ProductDir エントリで指定したパスに対する相対は。  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 たとえば、Enterprise Frameworks のプロジェクト テンプレートは、次のレジストリ エントリを追加します。  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir C:\Program files \microsoft Visual Studio\EnterpriseFrameworks\ を =  
  
 かどうか、PROJECT_TYPE が含まれます。 つまり、.vsz ファイルの前に指定した ProductDir ディレクトリに環境の検索の .vsz ファイルの EF のエントリを =。  
  
## <a name="see-also"></a>関連項目  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)   
 [プロジェクト ファクトリを使用したプロジェクト インスタンスの作成](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
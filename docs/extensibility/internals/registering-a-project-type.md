---
title: "プロジェクトの種類を登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Visual Studio SDK] の新しいプロジェクトのレジストリ エントリ"
  - "レジストリ、新しいプロジェクトの種類"
  - "登録には、新しいプロジェクトの種類"
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトの種類を登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

新しいプロジェクトを作成するとプロジェクトの種類を認識して使用することを [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を有効にするレジストリ エントリを作成する必要があります。  レジストリ スクリプト \(.rgs\) ファイルを使用してこれらのレジストリ エントリを作成します。  
  
 次の例ではレジストリのステートメントが適用されている各ステートメントのレジストリのエントリを含むテーブルになっている既定のパスとデータを提供します。  テーブルはステートメントのエントリとスクリプトの追加情報を提供します。  
  
> [!NOTE]
>  次のレジストリ情報はプロジェクトの種類を登録するために作成したスクリプトのレジストリ エントリの種類と目的の例を目的としています。  実際のエントリとしてプロジェクトの種類に固有の要件に基づいて異なる場合があります。  使用できる厳密に検索開発しているそのサンプルのレジストリ スクリプトが必要です。プロジェクトの種類に似た 1 を確認するにはサンプルを確認できます。  
  
 次の例ではHKEY\_CLASSES\_ROOT からです。  
  
## 例  
  
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
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|`@`|REG\_SZ|`FigPrjFile`|.figp 拡張子を含むプロジェクト ファイルの名前と説明です。|  
|`Content Type`|REG\_SZ|`Text/plain`|プロジェクト ファイルのコンテンツ タイプ。|  
|`NullFile`|REG\_SZ|`Null`||  
|`@`|REG\_SZ|`%MODULE%,-206`|この種類のプロジェクトに使用する既定のアイコン。  %MODULE% のステートメントはプロジェクト タイプの DLL の既定のレジストリの位置を完了します。|  
|`@`|REG\_SZ|`&Open in Visual Studio`|この種類のプロジェクトを開く既定のアプリケーションです。|  
|`@`|REG\_SZ|`devenv.exe "%1"`|この種類のプロジェクトが開かれたときに実行される既定のコマンド。|  
  
 次の例ではから\[HKEY\_LOCAL\_MACHINE キー HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ \\\] 99.0Exp パッケージの下のレジストリにあります。  
  
## 例  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
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
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|`@`\(既定値\)|REG\_SZ|`FigPrj Project VSPackage`|登録された VSPackage \(\) ローカライズ可能なプロジェクト タイプの名前。|  
|`InprocServer32`|REG\_SZ|`%MODULE%`|プロジェクトを DLL のパス。  IDE ではこの DLL を読み込み`DllGetClassObject` に <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> のオブジェクトを構築するに <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> を取得したりVSPackage の CLSID を渡します。|  
|`CompanyName`|REG\_SZ|`Microsoft`|プロジェクトを開発元の会社名です。|  
|`ProductName`|REG\_SZ|`Figure Project Sample`|プロジェクト タイプの名前。|  
|`ProductVersion`|REG\_SZ|`9.0`|プロジェクトのバージョンのリリース番号。|  
|`MinEdition`|REG\_SZ|`professional`|登録される VSPackage のエディション。|  
|`ID`|REG\_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|VSPackage プロジェクトのパッケージの負荷キー。  キーは環境が開始したらプロジェクトの読み込み時に検証されます。|  
|`DllName`|REG\_SZ|`%RESOURCE_DLL%`|プロジェクトの種類用にローカライズされたリソースを含むサテライト DLL のファイル名。|  
|`Path`|REG\_SZ|`%RESOURCE_PATH%`|サテライト DLL のパス。|  
|`FigProjectsEvents`|REG\_SZ|値についてはステートメントを参照してください。|このオートメーション イベントを返す文字列を指定します。|  
|`FigProjectItemsEvents`|REG\_SZ|値についてはステートメントを参照してください。|このオートメーション イベントを返す文字列を指定します。|  
  
 すべての次の例ではキー \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ \\\] 9.0Exp プロジェクトにレジストリにあります。  
  
## 例  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
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
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|`@`|REG\_SZ|`FigPrj Project`|このプロジェクトで既定の名前型。|  
|`DisplayName`|REG\_SZ|`#%IDS_PROJECT_TYPE%`|サテライト DLL からパッケージの下に取得する名前のリソース id を登録します。|  
|`Package`|REG\_SZ|`%CLSID_Package%`|パッケージの下に登録される VSPackage のクラス ID。|  
|`ProjectTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|プロジェクト テンプレート ファイルの既定のパス。  これらは新しいプロジェクト テンプレートによって表示されるファイルです。|  
|`ItemTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|プロジェクト項目テンプレート ファイルの既定のパス。  これらは\[新しい項目テンプレートによって表示されるファイルです。|  
|`DisplayProjectFileExtensions`|REG\_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|IDE が ENT0ENT \[出力\] ダイアログ ボックスを実装できるようにします。|  
|`PossibleProjectExtensions`|REG\_SZ|`figp`|開くプロジェクトがこのプロジェクトの種類 \(プロジェクト ファクトリ\) で処理されるかどうかを確認するためにIDE によって使用されます。  複数のエントリの形式はセミコロン区切りのリストです。  たとえば vdproj; 「」 vdp。|  
|`DefaultProjectExtension`|REG\_SZ|`.figp`|\[名前を付けて保存操作の既定のファイル名拡張子として IDE によって使用されます。|  
|`Filter Settings`|REG\_DWORD|各テーブルに次のステートメントとコメントを参照してください。|これらの設定はUI のダイアログ ボックスにファイルを表示するためのさまざまなフィルターを設定するために使用されます。|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|追加の項目テンプレートのリソース id。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**新しい項目の追加**  テンプレートのダイアログ ボックスに表示されるプロジェクト項目のパス。|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|\[ENT0ENT\] ダイアログ ボックスに表示されるファイルのツリー ノードの並べ替え順序を決定します。|  
  
 次の表に前のコード例で使用できるフィルター オプションを示します。  
  
|フィルター オプション|Description|  
|-----------------|-----------------|  
|`CommonFindFilesFilter`|フィルターが ENT0ENT \[出力\] ダイアログ ボックスの一般的なフィルターの 1 つがであることを示します。  一般的なフィルターにはとしてマークされていないフィルターの前にフィルターのリストに表示されます。|  
|`CommonOpenFilesFilter`|フィルターが ENT0ENT \[出力\] ダイアログ ボックスの一般的なフィルターの 1 つがであることを示します。  一般的なフィルターにはとしてマークされていないフィルターの前にフィルターのリストに表示されます。|  
|`FindInFilesFilter`|\[フィルター\] ダイアログ ボックスが ENT0ENT フィルターの 1 種類のフィルターで共通の後に挙げることを示します。|  
|`NotOpenFileFilter`|フィルターが ENT1ENT \[出力\] ダイアログ ボックスで使用されていないことを示します。|  
|`NotAddExistingItemFilter`|フィルターには追加の ENT1ENT \[出力\] ダイアログ ボックスで使用されていないことを示します。|  
  
 フィルターにこれらのフラグの一つ以上がない場合既定では\[ENT0ENT\] ダイアログ ボックスと \[ENT1ENT\] ダイアログ ボックスに共通のフィルターがないと使用されます。  フィルターは ENT0ENT \[出力\] ダイアログ ボックスでは使用されません。  
  
 すべての次の例ではキー \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ \\\] 9.0Exp プロジェクトにレジストリにあります。  
  
## 例  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新しいプロジェクト テンプレートのリソース id。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|登録されたプロジェクトの種類のプロジェクトの既定のパス。|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|プロジェクトの新規作成ウィザードのダイアログ ボックスに表示されるプロジェクトの並べ替え順序を設定します。|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 ではこの種類のプロジェクトで新しいプロジェクト\] ダイアログ ボックスだけに表示されていることを示します。|  
  
 すべての次の例ではキー \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ \\\] 9.0Exp プロジェクトにレジストリにあります。  
  
## 例  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|`@`|REG\_SZ|なし|次のエントリが \[そのほかのファイル用であることを示す既定値はエントリがあります。|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|\[新しい項目テンプレート ファイルのリソース id 値。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|\[ENT0ENT\] ダイアログ ボックスに表示される項目の既定のパス。|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|\[入力\] ENT0ENT ダイアログ ボックスのツリー ノードに表示の並べ替え順序を指定します。|  
  
 次の例ではキー \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ \\\] メニュー 9.0Exp にレジストリにあります。  
  
## 例  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 メニューの情報を取得するために使用するリソースに IDE のメニュー エントリ ポイント。  このデータはメニューのデータベースにマージされた場合同じキーはレジストリの MenusMerged のセクションに追加されます。  VSPackage は MenusMerged のセクションではが直接変更しないでください。  次の表のデータ フィールドに3 個のコンマ区切りのフィールドがあります。  一つ目のフィールドはメニュー リソース ファイルの完全パスを指定します :  
  
-   最初のフィールドを省略するとメニュー リソースにはVSPackage の GUID で識別されたサテライト DLL から読み込まれます。  
  
 2 番目のフィールドは型 CTMENU のメニューのリソース id を指定します :  
  
-   リソース id を指定しファイル パスが最初のパラメーターに指定される場合メニュー リソースが完全パスから読み込まれます。  
  
-   リソース id を指定した場合はファイル パスがない場合メニューのリソースはサテライト DLL から読み込まれます。  
  
-   完全パスが提供されリソース id を省略すると読み込むファイルは CTO なファイルであると想定されます。  
  
 最後のフィールドは CTMENU のリソースのバージョン番号を指定します。  バージョン番号を変更してメニューを再度マージできます。  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|%CLSID\_Package%|REG\_SZ|`,1000,1`|メニューの情報を取得するリソース。|  
  
 すべての次の例ではキー \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ \\\] 9.0Exp NewProjectTemplates にレジストリにあります。  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|図のリソース id 値はプロジェクト テンプレートがあります。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|新しいプロジェクトのディレクトリの既定のパス。  このディレクトリ内の項目は ENT0ENT \[出力\] ダイアログ ボックスに表示されます。|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|プロジェクトが ENT1ENT \[出力\] ダイアログ ボックスのツリー ノードに表示される順序を設定します。|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 ではこの種類のプロジェクトを ENT1ENT \[出力\] ダイアログ ボックスだけに表示されていることを示します。|  
  
 次の例ではキー \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ \\\] 9.0Exp InstalledProducts にレジストリにあります。  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|`Package`|REG\_SZ|`%CLSID_Package%`|登録された VSPackage のクラス ID。|  
|`UseInterface`|REG\_DWORD|`1`|1 つが UI をプロジェクトとの対話に使用されることを示します。  0 ではUI のインターフェイスがないことを示します。|  
  
 新しいプロジェクトの種類を制御する The.vsz ファイルはRELATIVE\_PATH のエントリが含まれます。  このパスは次のセットアップ キーの相対的なプロジェクトの種類の指定されたパスの下の \\ ProductDir エントリです :  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ Setup \\ 7.0Exp  
  
 たとえばエンタープライズ フレームワークのプロジェクト テンプレートは次のレジストリ エントリを追加します :  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ 7.0Exp \\ Setup \\ EF ProductDir \= C:\\Program Files\\Microsoft \\ Visual Studio \\ \\ EnterpriseFrameworks  
  
 .vsz ファイルに PROJECT\_TYPE\=EF のエントリを配置すると環境は前に指定された ProductDir ディレクトリの .vsz ファイルを検索します。  
  
## 参照  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)   
 [プロジェクトのファクトリを使用して、プロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
---
title: "プロジェクトおよび項目テンプレートを登録します。 | Microsoft Docs"
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
  - "プロジェクト [Visual Studio SDK] 項目を追加します。"
  - "レジストリ、新しい項目の追加] ダイアログ ボックス"
  - "[新しい項目の追加] ダイアログ ボックス"
  - "新しいプロジェクト] ダイアログ ボックスを追加します。"
  - "レジストリ [新しいプロジェクト] ダイアログ ボックス"
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトおよび項目テンプレートを登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトの種類には、それらのプロジェクトとプロジェクト項目テンプレートが置かれているディレクトリを登録する必要があります。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 表示を決定するようにプロジェクトの種類に関連付けられている登録情報を使用して、 **新しいプロジェクトの追加** と **新しい項目の追加** ダイアログ ボックス。  
  
 テンプレートの詳細については、次を参照してください。 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)します。  
  
## プロジェクトのレジストリ エントリ  
 次の例では、HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ の下にレジストリ エントリを表示する \<*バージョン*\> です。 関連するテーブルでは、例で使用される要素について説明します。  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|名前|種類|説明|  
|--------|--------|--------|  
|@|REG\_SZ|この種類のプロジェクトの既定の名前。|  
|DisplayName|REG\_SZ|\[パッケージ サテライト DLL から取得する名前のリソース ID が登録されます。|  
|パッケージ|REG\_SZ|パッケージの下に登録したパッケージのクラス ID。|  
|ProjectTemplatesDir|REG\_SZ|プロジェクト テンプレート ファイルの既定のパスです。 プロジェクト テンプレート ファイルは表示、 **新しいプロジェクト** テンプレートです。|  
  
### 項目テンプレートを登録します。  
 項目テンプレートを保存するディレクトリを登録する必要があります。  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|名前|種類|説明|  
|--------|--------|--------|  
|@|REG\_SZ|項目の追加テンプレートのリソース ID です。|  
|TemplatesDir|REG\_SZ|ダイアログ ボックスに表示されるプロジェクト項目のパス、 **新しい項目の追加** ウィザード。|  
|TemplatesLocalizedSubDir|REG\_SZ|TemplatesDir のサブディレクトリの名前を示す文字列のリソース ID は、ローカライズされたテンプレートを保持します。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 負荷文字列リソースからサテライト Dll に存在する場合、各サテライト DLL は、別のローカライズされたサブディレクトリの名前を含めることができます。|  
|SortPriority|REG\_DWORD|テンプレートの表示順序を制御する SortPriority の設定、 **新しい項目の追加** \] ダイアログ ボックス。 テンプレートの一覧の前より大きな SortPriority の値が表示されます。|  
  
### ファイル フィルターを登録します。  
 フィルターを登録する必要に応じてを [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ファイル名を要求するときに使用します。 たとえば、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] のフィルター処理、 **ファイルを開く** ダイアログ ボックスは。  
  
 **Visual c\# ファイル \(\*.cs、\*.resx、\*.settings、\*.xsd、\*.wsdl\); \*.cs、\*.resx、\*.settings、\*.xsd、\*.wsdl\)**  
  
 独自のサブキー HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ の下に複数のフィルターの登録をサポートするために各フィルターが登録されている \<*バージョン*\> \\Projects\\ {\<*ProjectGUID*\>} \\Filters\\ \<*サブキー*\> です。 サブキーの名前は任意です。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] サブキーの名前を無視し、その値だけを使用します。  
  
 次の表に示すようにフラグを設定して、フィルターが使用されるコンテキストを制御できます。 フィルターがフラグを設定しない場合の一般的なフィルターの後に表示されます、 **既存項目の追加** \] ダイアログ ボックスおよび **ファイルを開く** ダイアログ ボックスで、それはでは使用しないで、 **ファイル内の検索** \] ダイアログ ボックス。  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|名前|種類|説明|  
|--------|--------|--------|  
|CommonFindFilesFilter|REG\_DWORD|一般的なフィルターのいずれかのフィルターは、 **ファイル内の検索** \] ダイアログ ボックス。 一般的なフィルターは、共通としてマークされていないフィルターの前に、フィルター一覧に表示されます。|  
|CommonOpenFilesFilter|REG\_DWORD|一般的なフィルターのいずれかのフィルターは、 **ファイルを開く** \] ダイアログ ボックス。 一般的なフィルターは、共通としてマークされていないフィルターの前に、フィルター一覧に表示されます。|  
|FindInFilesFilter|REG\_DWORD|一般的なフィルターの後にフィルターを一覧表示、 **ファイル内の検索** \] ダイアログ ボックス。|  
|NotOpenFileFilter|REG\_DWORD|フィルターを使用しないことを示す、 **ファイルを開く** \] ダイアログ ボックス。|  
|NotAddExistingItemFilter|REG\_DWORD|フィルターを使用しないことを示す、 **既存項目の追加** \] ダイアログ ボックス。|  
|SortPriority|REG\_DWORD|フィルターの表示順序を制御する SortPriority を設定します。 フィルター一覧の前、SortPriority のより大きな値が表示されます。|  
  
## ディレクトリ構造  
 VSPackages を置くテンプレート ファイルとフォルダー任意の場所、ローカルまたはリモート ディスク統合開発環境 \(IDE\) を通して、場所を登録している限り、されます。 ただし、組織のため、製品のインストール パスでは、次のディレクトリ構造を勧めします。  
  
 \\Templates  
  
 \\Projects \(プロジェクト テンプレートが含まれています\)  
  
 \\Applications  
  
 \\Components  
  
 \\ ...  
  
 \\ProjectItems \(プロジェクト項目が含まれています\)  
  
 \\Class  
  
 \\Form  
  
 \\Web ページ  
  
 \\HelperFiles \(複数のファイル プロジェクト項目で使用されるファイルが含まれています\)  
  
 \\WizardFiles  
  
## 参照  
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [アプリケーションのローカライズ](../../ide/localizing-applications.md)   
 [通常、プロジェクトの拡張に使用されるオブジェクトの Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
---
title: プロジェクトと項目テンプレートの登録 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85c22d0191d015979dff5a4845c4dda0af96ee60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="registering-project-and-item-templates"></a>プロジェクトと項目テンプレートの登録
プロジェクトの種類は、そのプロジェクトとプロジェクト項目テンプレートが配置されているディレクトリを登録する必要があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 表示するものを決定する、プロジェクトの種類に関連付けられている登録情報を使用して、**新しいプロジェクトの追加**と**新しい項目の追加** ダイアログ ボックス。  
  
 テンプレートの詳細については、次を参照してください。[プロジェクトに追加するとプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)です。  
  
## <a name="registry-entries-for-projects"></a>プロジェクトのレジストリ エントリ  
 次の例では、HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio の下のレジストリ エントリ\\<*バージョン*>。 付随するテーブルでは、例で使用される要素について説明します。  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|@|REG_SZ|この種類のプロジェクトの既定の名前。|  
|DisplayName|REG_SZ|パッケージ サテライト DLL から取得する名前のリソース ID が登録されています。|  
|Package|REG_SZ|パッケージの下に登録パッケージのクラス ID。|  
|ProjectTemplatesDir|REG_SZ|プロジェクト テンプレート ファイルの既定のパス。 プロジェクト テンプレートのファイルが表示されます、**新しいプロジェクト**テンプレート。|  
  
### <a name="registering-item-templates"></a>項目テンプレートの登録  
 項目テンプレートを保存するディレクトリを登録する必要があります。  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|@|REG_SZ|項目の追加テンプレートのリソース ID です。|  
|TemplatesDir|REG_SZ|ダイアログ ボックスに表示されるプロジェクト アイテムのパス、**新しい項目の追加**ウィザード。|  
|TemplatesLocalizedSubDir|REG_SZ|TemplatesDir のサブディレクトリの名前を示す文字列のリソース ID では、ローカライズされたテンプレートを保持します。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]読み込み、文字列リソースをサテライト Dll に存在する場合、各サテライト DLL が別のローカライズされたサブディレクトリ名を含めることができます。|  
|SortPriority|REG_DWORD|テンプレートが表示される順序を制御するために SortPriority の設定、**新しい項目の追加** ダイアログ ボックス。 テンプレートの一覧の前半 SortPriority のより大きな値が表示されます。|  
  
### <a name="registering-file-filters"></a>ファイルのフィルターを登録します。  
 必要に応じて、フィルターを登録することができますを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ファイル名を要求するときに使用します。 たとえば、[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]のフィルター処理、**ファイルを開く** ダイアログ ボックスは。  
  
 **Visual c# ファイル (\*.cs、\*.resx、\*.settings、\*.xsd、\*.wsdl);\*です。cs、\*.resx、\*.settings、\*.xsd、\*.wsdl)**  
  
 独自のサブキー HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio の下で複数のフィルターの登録をサポートする各フィルターが登録されている\\<*バージョン*> \Projects\\{\< *ProjectGUID*>} \Filters\\<*サブキー*>。 サブキーの名前は任意です。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]サブキーの名前を無視され、その値だけを使用します。  
  
 次の表に示すようにフラグを設定して、フィルターを使用しているコンテキストを制御できます。 フィルターでは、フラグを設定することはない場合の一般的なフィルターの後に表示されます、**既存項目の追加** ダイアログ ボックスおよび**ファイルを開く** ダイアログ ボックスがないで使用される、**ファイル内の検索**  ダイアログ ボックス。  
  
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
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|一般的なフィルターのいずれかのフィルターは、**ファイル内の検索** ダイアログ ボックス。 一般的なフィルターは、一般的でマークされていないフィルターの前に、フィルター一覧に表示されます。|  
|CommonOpenFilesFilter|REG_DWORD|一般的なフィルターのいずれかのフィルターは、**ファイルを開く** ダイアログ ボックス。 一般的なフィルターは、一般的でマークされていないフィルターの前に、フィルター一覧に表示されます。|  
|FindInFilesFilter|REG_DWORD|一般的なフィルターの後にフィルターを一覧表示、**ファイル内の検索** ダイアログ ボックス。|  
|NotOpenFileFilter|REG_DWORD|フィルターを使用しないことを示す、**ファイルを開く** ダイアログ ボックス。|  
|NotAddExistingItemFilter|REG_DWORD|フィルターを使用しないことを示す、**既存項目の追加** ダイアログ ボックス。|  
|SortPriority|REG_DWORD|フィルターが表示される順序を制御するために SortPriority を設定します。 フィルター一覧の前、SortPriority のより大きな値が表示されます。|  
  
## <a name="directory-structure"></a>ディレクトリ構造  
 Vspackage に配置できるテンプレート ファイルとフォルダー任意の場所ローカルまたはリモート ディスクでは、統合開発環境 (IDE) を通して、場所を登録している限り、します。 ただし、組織の容易にするため、製品のインストール パスでは、次のディレクトリ構造お勧めします。  
  
 \Templates  
  
 \Projects (プロジェクト テンプレートが含まれています)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (プロジェクト項目が含まれています)  
  
 \Class  
  
 \Form  
  
 \Web ページ  
  
 \HelperFiles (複数のファイル プロジェクト項目で使用されるファイルが含まれています)  
  
 \WizardFiles  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [アプリケーションのローカライズ](../../ide/localizing-applications.md)   
 [プロジェクトの拡張に通常使用されるオブジェクトの CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
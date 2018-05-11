---
title: コンテキスト パラメーター |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb6646e917b4cb94b4cd0534b513d148490cf69d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="context-parameters"></a>コンテキスト パラメーター
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) では、ウィザードを追加することができます、**新しいプロジェクト**、**新しい項目の追加**、または**Sub プロジェクトの追加** ダイアログ ボックス。 追加のウィザードに用意されて、**ファイル**メニューでプロジェクトを右クリックして、または**ソリューション エクスプ ローラー**です。 IDE では、コンテキスト パラメーターをウィザードの実装に渡します。 コンテキスト パラメーターは、IDE は、ウィザードを呼び出すときに、プロジェクトの状態を定義します。  
  
 IDE では、ウィザードを起動するには、<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>フラグを IDE の呼び出しで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>プロジェクトのメソッドです。 設定すると、プロジェクトが発生する必要があります、`IVsExtensibility::RunWizardFile`に登録されているウィザード名または GUID およびその他の IDE が渡されるコンテキスト パラメーターを使用して実行されるメソッド。  
  
## <a name="context-parameters-for-new-project"></a>新しいプロジェクトのコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類を登録 (<xref:EnvDTE.Constants.vsWizardNewProject>) またはウィザードの種類を示す GUID です。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]は {0f90e1d0-4999-11d1-b6d1-00a0c90f2744}、実装では、ウィザードの guid を指定します。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`LocalDirectory`|プロジェクト ファイルの操作のローカルの場所。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールします。|  
|`FExclusive`|プロジェクトが開いているソリューションを閉じる必要がありますを示すブール値フラグです。|  
|`SolutionName`|ディレクトリの部分および .sln 拡張子を含まないソリューション ファイルの名前です。 .Suo ファイルの名前を使用して作成も`SolutionName`します。 この引数が空の文字列でない場合は、ウィザードを使用して<xref:EnvDTE._Solution.Create%2A>を使用してプロジェクトを追加する前に<xref:EnvDTE._Solution.AddFromTemplate%2A>です。 この名前が空の文字列の場合を使用して<xref:EnvDTE._Solution.AddFromTemplate%2A>呼び出さず<xref:EnvDTE._Solution.Create%2A>です。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックしてされた (`TRUE`)。|  
  
## <a name="context-parameters-for-add-new-item"></a>新しい項目の追加のコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類を登録 (<xref:EnvDTE.Constants.vsWizardAddItem>) またはウィザードの種類を示す GUID です。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D1-4999-11D1-B6D1-00A0C90F2744} は、実装では、ウィザードの guid を指定します。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`ProjectItems`|作業用のプロジェクト ファイルを含むローカルの場所。|  
|`ItemName`|追加する項目の名前です。 この名前は既定のファイル名またはファイル名から型のユーザーを**アイテムの追加** ダイアログ ボックス。 名前は、.vsdir ファイルで設定されているフラグに基づきます。 名前は、null 値を指定できます。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールします。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックしてされた (`TRUE`)。|  
  
## <a name="context-parameters-for-add-sub-project"></a>サブ プロジェクトの追加のコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類を登録 (<xref:EnvDTE.Constants.vsWizardAddSubProject>) またはウィザードの種類を示す GUID です。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D2-4999-11D1-B6D1-00A0C90F2744} は、実装では、ウィザードの guid を指定します。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`ProjectItems`|ポインター、`ProjectItems`ウィザードが動作するコレクション。 このポインターは、プロジェクト階層の選択内容に基づいて、ウィザードに渡されます。 ユーザーは通常、項目を保存するフォルダーを選択しを呼び出して、プロジェクトの**項目の追加** ダイアログ ボックス。|  
|`LocalDirectory`|プロジェクト ファイルの操作のローカルの場所。|  
|`ItemName`|追加する項目の名前です。 この名前は既定のファイル名またはファイル名から型のユーザーを**アイテムの追加** ダイアログ ボックス。 名前は、.vsdir ファイルで設定されているフラグに基づきます。 名前は、null 値を指定できます。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールします。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックしてされた (`TRUE`)。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [ウィザード (です。Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [ウィザードを起動するためのコンテキスト パラメーター](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
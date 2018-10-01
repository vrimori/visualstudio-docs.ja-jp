---
title: コンテキスト パラメーター |Microsoft Docs
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
ms.openlocfilehash: 03e95dce70b38a6c2b51e0b610cb8e8bd6379239
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370992"
---
# <a name="context-parameters"></a>コンテキスト パラメーター
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) では、ウィザードを使用を追加することができます、**新しいプロジェクト**、**新しい項目の追加**、または**サブ プロジェクトの追加** ダイアログ ボックス。 追加のウィザードで使用できる、**ファイル**メニューでプロジェクトを右クリックして、または**ソリューション エクスプ ローラー**。 IDE では、ウィザードの実装にコンテキスト パラメーターを渡します。 コンテキスト パラメーターは、IDE は、ウィザードを呼び出すときに、プロジェクトの状態を定義します。  
  
 IDE 設定ウィザードの起動時に、<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>フラグを IDE の呼び出しで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>プロジェクトのメソッド。 設定すると、プロジェクトが発生する必要があります、`IVsExtensibility::RunWizardFile`登録ウィザードの名前または GUID およびその他の IDE が渡されるコンテキスト パラメーターを使用して実行するメソッド。  
  
## <a name="context-parameters-for-new-project"></a>新しいプロジェクトのコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類の登録 (<xref:EnvDTE.Constants.vsWizardNewProject>) またはウィザードの種類を示す GUID。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]実装では、ウィザードの GUID は {0f90e1d0-4999-11d1-b6d1-00a0c90f2744} します。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`LocalDirectory`|プロジェクト ファイルの操作のローカルの場所。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールです。|  
|`FExclusive`|プロジェクトが開いているソリューションを閉じる必要がありますかを示すブール フラグです。|  
|`SolutionName`|ディレクトリの部分のないソリューション ファイルの名前または *.sln*拡張機能。 *.Suo*を使用してファイル名を作成しても`SolutionName`します。 この引数が空の文字列でない場合は、ウィザードを使用して<xref:EnvDTE._Solution.Create%2A>でプロジェクトを追加する前に<xref:EnvDTE._Solution.AddFromTemplate%2A>します。 この名前が空の文字列の場合を使用して、<xref:EnvDTE._Solution.AddFromTemplate%2A>呼び出さず<xref:EnvDTE._Solution.Create%2A>します。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックしてされた (`TRUE`)。|  
  
## <a name="context-parameters-for-add-new-item"></a>新しい項目の追加のコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類の登録 (<xref:EnvDTE.Constants.vsWizardAddItem>) またはウィザードの種類を示す GUID。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]実装、ウィザードの GUID は、{0F90E1D1-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`ProjectItems`|プロジェクトの作業ファイルを格納しているローカルの場所。|  
|`ItemName`|追加する項目の名前。 この名前は既定のファイル名またはファイル名から型のユーザーを**項目の追加** ダイアログ ボックス。 名前に設定されているフラグに基づいて、 *.vsdir*ファイル。 名前は、null 値を指定できます。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールです。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックしてされた (`TRUE`)。|  
  
## <a name="context-parameters-for-add-sub-project"></a>サブ プロジェクトの追加のコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類の登録 (<xref:EnvDTE.Constants.vsWizardAddSubProject>) またはウィザードの種類を示す GUID。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]実装、ウィザードの GUID は、{0F90E1D2-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`ProjectItems`|ポインター、`ProjectItems`ウィザードが動作するコレクション。 このポインターは、プロジェクト階層の選択に基づいてウィザードに渡されます。 ユーザーは、通常、アイテムを配置するフォルダーを選択し、呼び出して、プロジェクトの**項目の追加** ダイアログ ボックス。|  
|`LocalDirectory`|プロジェクト ファイルの操作のローカルの場所。|  
|`ItemName`|追加する項目の名前。 この名前は既定のファイル名またはファイル名から型のユーザーを**項目の追加** ダイアログ ボックス。 名前に設定されているフラグに基づいて、 *.vsdir*ファイル。 名前は、null 値を指定できます。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールします。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックしてされた (`TRUE`)。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [ウィザード (.vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [ウィザードを起動するためのコンテキスト パラメーター](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
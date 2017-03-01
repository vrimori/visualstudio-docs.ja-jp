---
title: "コンテキスト パラメーター |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 143a8738f2eb6517c1642eafd2b9629e0fa8f84d
ms.lasthandoff: 02/22/2017

---
# <a name="context-parameters"></a>コンテキスト パラメーター
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE)、ウィザードを使用してを追加することができます、**新しいプロジェクト**、**新しい項目の追加**、または**Sub プロジェクトの追加**ダイアログ ボックス。 追加のウィザードが 利用可能、**ファイル**メニューまたはでプロジェクトを右クリックして**ソリューション エクスプ ローラー**します。 IDE では、ウィザードの実装にコンテキスト パラメーターを渡します。 コンテキスト パラメーターは、IDE は、ウィザードを呼び出すときに、プロジェクトの状態を定義します。  
  
 IDE では、ウィザードを起動するには、<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>フラグを IDE の呼び出しで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>プロジェクトのメソッドです</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>。 設定すると、プロジェクトが発生する必要があります、`IVsExtensibility::RunWizardFile`登録ウィザードの名前または GUID と、IDE が渡されるその他のコンテキスト パラメーターを使用して実行するメソッドです。  
  
## <a name="context-parameters-for-new-project"></a>新しいプロジェクトのコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類を登録 (<xref:EnvDTE.Constants.vsWizardNewProject>) またはウィザードの種類を示す GUID</xref:EnvDTE.Constants.vsWizardNewProject> 。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]実装では、ウィザードの GUID は {0f90e1d0-4999-11d1-b6d1-00a0c90f2744} です。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`LocalDirectory`|プロジェクト ファイルのローカルの場所。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールします。|  
|`FExclusive`|プロジェクトが開かれているソリューションを閉じることを示すブール フラグです。|  
|`SolutionName`|ディレクトリの部分や .sln 拡張子のないソリューション ファイルの名前です。 .Suo ファイルの名前を使用して作成も`SolutionName`です。 <xref:EnvDTE._Solution.Create%2A> <xref:EnvDTE._Solution.AddFromTemplate%2A>。</xref:EnvDTE._Solution.AddFromTemplate%2A>を使用してプロジェクトを追加する前に</xref:EnvDTE._Solution.Create%2A>ウィザードを使用してこの引数が空の文字列でない場合は、 <xref:EnvDTE._Solution.AddFromTemplate%2A> <xref:EnvDTE._Solution.Create%2A>。</xref:EnvDTE._Solution.Create%2A>を呼び出さずに</xref:EnvDTE._Solution.AddFromTemplate%2A>この名前が空の文字列の場合を使用してください。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックした (`TRUE`)。|  
  
## <a name="context-parameters-for-add-new-item"></a>新しい項目の追加のコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類を登録 (<xref:EnvDTE.Constants.vsWizardAddItem>) またはウィザードの種類を示す GUID</xref:EnvDTE.Constants.vsWizardAddItem> 。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]実装では、ウィザードの GUID は、{0F90E1D1-4999-11D1-B6D1-00A0C90F2744} します。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`ProjectItems`|作業用プロジェクトのファイルを含むローカルの場所。|  
|`ItemName`|追加する項目の名前。 この名前は既定のファイル名またはユーザーから型のファイル名、**アイテムの追加** ダイアログ ボックス。 名前は、.vsdir ファイルで設定されているフラグに基づきます。 名前は、null 値であることができます。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールします。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックした (`TRUE`)。|  
  
## <a name="context-parameters-for-add-sub-project"></a>Sub プロジェクトの追加のコンテキスト パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`WizardType`|ウィザードの種類を登録 (<xref:EnvDTE.Constants.vsWizardAddSubProject>) またはウィザードの種類を示す GUID</xref:EnvDTE.Constants.vsWizardAddSubProject> 。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]実装では、ウィザードの GUID は、{0F90E1D2-4999-11D1-B6D1-00A0C90F2744} します。|  
|`ProjectName`|一意である文字列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトの名前。|  
|`ProjectItems`|ポインター、`ProjectItems`ウィザードが動作するコレクション。 このポインターは、プロジェクト階層の選択に基づいてウィザードに渡されます。 ユーザーが通常、アイテムを配置するフォルダーを選択し、プロジェクトの順に呼び出して**項目の追加** ダイアログ ボックス。|  
|`LocalDirectory`|プロジェクト ファイルのローカルの場所。|  
|`ItemName`|追加する項目の名前。 この名前は既定のファイル名またはユーザーから型のファイル名、**アイテムの追加** ダイアログ ボックス。 名前は、.vsdir ファイルで設定されているフラグに基づきます。 名前は、null 値であることができます。|  
|`InstallationDirectory`|ディレクトリ パス、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストールします。|  
|`Silent`|ウィザードをサイレント モードで実行する必要があるかどうかを示すブール値として**完了**クリックした (`TRUE`)。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [ウィザード (します。Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [ウィザードを起動するためのコンテキスト パラメーター](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)

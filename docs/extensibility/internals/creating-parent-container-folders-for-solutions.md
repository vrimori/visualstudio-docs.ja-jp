---
title: ソリューションの親コンテナーのフォルダーを作成する |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be768f684a495271f06a2a79a71647a9bbaa8552
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498871"
---
# <a name="create-parent-container-folders-for-solutions"></a>親コンテナーのフォルダーのソリューションを作成します。
ソース管理プラグイン API バージョン 1.2、ユーザーは、ソリューション内のすべての web プロジェクトの 1 つのルートのソース コントロール変換先を指定できます。 この単一のルートには、スーパー Unified ルート (サー) が呼び出されます。  
  
 ソース管理プラグイン API バージョン 1.1、ユーザー、ソース管理にマルチ プロジェクト ソリューションを追加する場合、ユーザーが web プロジェクトごとに 1 つのソース コントロールの宛先の指定を求めが。  
  
## <a name="new-capability-flags"></a>新しい機能フラグ  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>新しい関数  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は、ソース管理にソリューションを追加するときに常にほぼサー フォルダーを作成します。 具体的には、これは、次の場合。  
  
-   プロジェクトでは、web プロジェクトのファイル共有です。  
  
-   別のドライブは、プロジェクトとソリューション ファイルがあります。  
  
-   別の共有は、プロジェクトとソリューション ファイルがあります。  
  
-   プロジェクトは、個別に (ソース管理の対象のソリューション) に追加されました。  
  

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、サー フォルダーの名前が、拡張子を除いたソリューション名と同じであることをお勧めします。 次の表では、2 つのバージョンで動作をまとめたものです。  
  
|機能|ソース管理プラグイン API バージョン 1.1|ソース管理プラグイン API バージョン 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|ソース コード管理にソリューションを追加します。|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|ソース管理対象のソリューションにプロジェクトを追加します。|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **注:** Visual Studio では、ソリューションが、SUR. の直接の子であります。|  
  
## <a name="examples"></a>使用例  
 次の表では、2 つの例を示します。 どちらの場合で、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]までソース管理下にあるソリューションの保存先のユーザーの入力を求め、 *user_choice*変換先として指定されます。 User_choice を指定すると、ソース コントロールの変換先のユーザーに確認しないで、ソリューションと 2 つのプロジェクトが追加されます。  
  
|ソリューションが含まれています|ディスク上の場所に|データベースの既定の構造|  
|-----------------------|-----------------------|--------------------------------|  
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/< user_choice >/sln1<br /><br /> $/< user_choice > C/Web1<br /><br /> $/< user_choice >/Web2|  
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/< user_choice >/sln1<br /><br /> $/< user_choice >/D web1<br /><br /> $/< user_choice >/sln1 win1|  
  
 操作がキャンセルはまたはエラーのため失敗したかどうかに関係なく、サー フォルダーとサブフォルダーが作成されます。 キャンセルまたはエラー状態で自動的に削除されません。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] バージョン 1.1 の動作に既定値は、ソース管理プラグインが返されなかった場合`SCC_CAP_CREATESUBPROJECT`と`SCC_CAP_GETPARENTPROJECT`機能フラグ。 さらに、ユーザーの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]バージョン 1.1 の動作に戻すには、次のキーの値を設定することができます*dword:00000001*:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*
  
## <a name="see-also"></a>関連項目  
 [新機能については、ソース管理プラグイン API バージョン 1.2 です。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
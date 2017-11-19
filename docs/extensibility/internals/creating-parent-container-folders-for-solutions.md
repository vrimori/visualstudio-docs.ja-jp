---
title: "ソリューションの親コンテナーのフォルダーを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ea901fe4e380fd867db1c63e44bc1cb6e144feb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="creating-parent-container-folders-for-solutions"></a>ソリューションの親コンテナーのフォルダーを作成します。
API では、ソース管理プラグイン バージョン 1.2、ユーザーは、ソリューション内のすべての Web プロジェクトの 1 つのルート ソース コントロール変換先を指定できます。 この単一のルートには、スーパー Unified ルート (SUR) が呼び出されます。  
  
 ソース管理プラグイン API バージョン 1.1 でユーザー マルチ プロジェクト ソリューションをソース管理に追加する場合、ユーザーするように要求されました Web プロジェクトごとに 1 つのソース コントロールの送信先を指定します。  
  
## <a name="new-capability-flags"></a>新しい機能フラグ  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>新しい関数  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は、ソース管理にソリューションを追加するときにほとんどの場合、SUR フォルダーを作成します。 具体的には、次の場合に。  
  
-   プロジェクトは、ファイル共有の Web プロジェクトです。  
  
-   プロジェクトとソリューション ファイルの別のドライブがありません。  
  
-   他の共有、プロジェクトとソリューション ファイルがあります。  
  
-   プロジェクトは、個別に (ソース管理の対象のソリューション) に追加されました。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] SUR フォルダーの名前が、拡張子のないソリューション名と同じであることをお勧めします。 次の表は、2 つのバージョンの動作をまとめたものです。  
  
|特性|tSource コントロール プラグイン API のバージョン 1.1|ソース管理プラグイン API のバージョン 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|ソリューションを SCC に追加します。|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|ソース管理対象のソリューションにプロジェクトを追加します。|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()**注:** Visual Studio は、ソリューションが、SUR. の直接の子である前提としています。|  
  
## <a name="examples"></a>例  
 次の表は、2 つの例を示します。 どちらの場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]までソース管理下にあるソリューションに、送信先のユーザーの入力を求め、 *user_choice*先として指定します。User_choice を指定すると、ソース コントロールの宛先へのユーザーに確認しないでソリューションと 2 つのプロジェクトが追加されます。  
  
|ソリューションに含まれる|ディスク上の場所に|データベースの既定の構造|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*D/web1<br /><br /> $/*user_choice*sln1/win1|  
  
 かどうか、操作キャンセルまたは失敗がエラーのために関係なく、SUR フォルダーとサブフォルダーが作成されます。 キャンセルまたはエラー条件に自動的に削除されません。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]バージョン 1.1 の動作に既定値は、ソース管理プラグインが返されない場合は`SCC_CAP_CREATESUBPROJECT`と`SCC_CAP_GETPARENTPROJECT`機能フラグ。 さらに、ユーザーの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]バージョン 1.1 の動作に戻すには、次のキーの値を dword:00000001 に設定することもできます。  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword:00000001  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
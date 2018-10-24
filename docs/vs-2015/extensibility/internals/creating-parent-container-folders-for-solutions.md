---
title: ソリューションの親コンテナーのフォルダーを作成する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8bf3de0c558dbda1d1b43e7b5887780f1a1e2b90
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832065"
---
# <a name="creating-parent-container-folders-for-solutions"></a>ソリューションの親コンテナー フォルダーの作成
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース管理プラグイン API バージョン 1.2 では、ユーザーは、ソリューション内のすべての Web プロジェクトの 1 つのルートのソース コントロール変換先を指定できます。 この単一のルートには、スーパー Unified ルート (サー) が呼び出されます。  
  
 ソース管理プラグイン API バージョン 1.1 では、ユーザーは、ソース管理にマルチ プロジェクト ソリューションを追加すると、ユーザーを求め Web プロジェクトごとに 1 つのソース コントロールの先を指定されました。  
  
## <a name="new-capability-flags"></a>新しい機能フラグ  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>新しい関数  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE は、ソース管理にソリューションを追加するときに常にほぼサー フォルダーを作成します。 具体的には、これは、次の場合。  
  
- プロジェクトは、Web プロジェクトのファイル共有です。  
  
- 別のドライブは、プロジェクトとソリューション ファイルがあります。  
  
- 別の共有は、プロジェクトとソリューション ファイルがあります。  
  
- プロジェクトは、個別に (ソース管理の対象のソリューション) に追加されました。  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]サー フォルダーの名前が、拡張子を除いたソリューション名と同じであることをお勧めします。 次の表では、2 つのバージョンで動作をまとめたものです。  
  
|機能|tSource コントロール プラグイン API バージョン 1.1|ソース管理プラグイン API バージョン 1.2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|ソース コード管理にソリューションを追加します。|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|ソース管理対象のソリューションにプロジェクトを追加します。|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()**注:** Visual Studio では、ソリューションが、SUR. の直接の子であります。|  
  
## <a name="examples"></a>使用例  
 次の表では、2 つの例を示します。 どちらの場合で、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]までソース管理下にあるソリューションの保存先のユーザーの入力を求め、 *user_choice*変換先として指定されます。User_choice を指定すると、ソース コントロールの変換先のユーザーに確認しないで、ソリューションと 2 つのプロジェクトが追加されます。  
  
|ソリューションが含まれています|ディスク上の場所に|データベースの既定の構造|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*web1/D<br /><br /> $/*user_choice*  /sln1 win1|  
  
 操作が取り消されたまたはエラーのため失敗にかかわらず、サー フォルダーとサブフォルダーが作成されます。 キャンセルまたはエラー状態で自動的に削除されません。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] バージョン 1.1 の動作に既定値は、ソース管理プラグインが返されなかった場合`SCC_CAP_CREATESUBPROJECT`と`SCC_CAP_GETPARENTPROJECT`機能フラグ。 さらに、ユーザーの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]dword:00000001 に次のキーの値を設定して、バージョン 1.1 の動作に戻すことができます。  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword:00000001  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)


---
title: "ソリューションの親コンテナーのフォルダーを作成します。 | Microsoft Docs"
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
  - "親コンテナーを作成して、ソリューション"
  - "ソース管理プラグインを親コンテナーを作成します。"
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# ソリューションの親コンテナーのフォルダーを作成します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理プラグイン API Version 1.2 ではユーザーはソリューション内のすべての Web プロジェクトで一つのルートのソース管理の出力先を指定できます。  この単一のルートが十分で統合されたルートと \(SUR\) 呼ばれます。  
  
 ソース管理プラグイン API Version 1.1 ではユーザーがソース管理に multiproject のソリューションを追加するとユーザーは Web プロジェクトで 1 種類のソース管理の出力先を指定するメッセージが表示されます。  
  
## 新しい機能のフラグ  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## 新しい関数  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は通常はソリューションをソース管理に追加すると SUR のフォルダーを作成します。  具体的には次の場合 :  
  
-   プロジェクトまたはファイル共有 Web プロジェクトです。  
  
-   プロジェクトとソリューション ファイルごとに別のドライブがあります。  
  
-   プロジェクトとソリューション ファイルごとに異なる共有があります。  
  
-   プロジェクトが他にも追加されます \(ソース管理されたソリューション\)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] で SUR フォルダーの名前に拡張子を付けずソリューション名と同じであることをお勧めします。  次の表は2 種類のバージョンで動作を示します。  
  
|機能|tSource コントロールのプラグイン API Version 1.1|ソース管理プラグイン API Version 1.2|  
|--------|------------------------------------------|--------------------------------|  
|SCC へのソリューションの追加|SccInitialize \(\)<br /><br /> SccGetProjPath \(\)<br /><br /> SccGetProjPath \(\)<br /><br /> SccOpenProject \(\)|SccInitialize \(\)<br /><br /> SccGetProjPath \(\)<br /><br /> SccCreateSubProject \(\)<br /><br /> SccCreateSubProject \(\)<br /><br /> SccOpenProject \(\)|  
|ソース管理されたソリューションに追加するプロジェクト|SccGetProjPath \(\)<br /><br /> OpenProject \(\)|SccGetParentProjectPath \(\)<br /><br /> SccOpenProject \(\) **Note:**  Visual Studio がソリューション SUR がの直接の子であると仮定します。|  
  
## 例  
 次の表は2 種類の例を示します。  いずれの場合も[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のユーザーはソース管理でソリューションの配置先の場所に *user\_choice* 先として指定するまでメッセージが表示されます。user\_choice を指定するとソリューションおよび 2 のプロジェクトがソース管理の対象のユーザーにメッセージを表示せずに追加されます。  
  
|ソリューションに含まれています。|ディスク上の場所|データベースの既定の構造|  
|----------------------|--------------|------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C:\\Solutions\\sln1<br /><br /> C:\\Inetpub\\wwwroot\\Web1<br /><br /> \\ \\ server \\ \\ web2 wwwroot$|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/C\/Web1<br /><br /> $*user\_choice*\/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\\Solutions\\sln1<br /><br /> D:\\Inetpub\\wwwroot\\Web1<br /><br /> C:\\solutions\\sln1\\Win1|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/D\/web1<br /><br /> $*user\_choice*\/sln1\/win1|  
  
 操作を取り消すときまたはエラーが原因で失敗するかどうか SUR のフォルダーとサブフォルダーはに関係なく作成されます。  これらはキャンセルまたはエラー条件に自動的に削除されません。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はバージョン 1.1 の動作とソース管理プラグインが `SCC_CAP_CREATESUBPROJECT` と `SCC_CAP_GETPARENTPROJECT` 機能のフラグを返すなります。  また[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のユーザーはダブル ワードに次のキーの値を設定することによりバージョン 1.1 の動作に戻すに選択できます : : 00000001  
  
 \[HKEY\_CURRENT\_USER \\ Software \\ Microsoft \\ VisualStudio \\ 8.0 \\ SourceControl 入力\] DoNotCreateSolutionRootFolderInSourceControl 「 " \=dword: 00000001  
  
## 参照  
 [ソース管理プラグイン API バージョン 1.2 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
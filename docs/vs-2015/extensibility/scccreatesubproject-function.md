---
title: SccCreateSubProject 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e62e1567559898b198866fe3e67e9b5b53096273
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232090"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、指定した名前で指定された既存の親プロジェクトの下のサブプロジェクトを作成、`lpParentProjPath`引数。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグインのコンテキストのポインター。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力] (最大 SCC_USER_SIZE、NULL 終端文字も含めて) ユーザー名。  
  
 lpParentProjPath  
 [in]親プロジェクトのパスを識別する文字列（NULL終端文字を含むSCC_PRJPATH_SIZEまで）。  
  
 lpSubProjName  
 [in]提案されたサブプロジェクト名（NULL終端文字を含むSCC_PRJPATH_SIZEまで）。  
  
 lpAuxProjPath  
 [入力、出力] (最大 SCC_PRJPATH_SIZE、NULL 終端文字も含めて) プロジェクトを識別する文字列を補助します。  
  
 lpSubProjPath  
 [入力、出力](最大 SCC_PRJPATH_SIZE、NULL 終端文字も含めて) サブプロジェクトのパスを識別する文字列を出力します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|サブプロジェクトを正常に作成されました。|  
|SCC_E_INITIALIZEFAILED|親プロジェクトを初期化できませんでした。|  
|SCC_E_INVALIDUSER|ユーザーは、ソース管理システム ログオンできませんでした。|  
|SCC_E_COULDNOTCREATEPROJECT|サブプロジェクトを作成することはできません。|  
|SCC_E_PROJSYNTAXERR|無効なプロジェクトの構文です。|  
|SCC_E_UNKNOWNPROJECT|親プロジェクトはソース管理プラグインを正常ではありません。|  
|SCC_E_INVALIDFILEPATH|無効であるか使用できないファイルのパス。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_CONNECTIONFAILURE|ソース管理プラグイン接続の問題が発生しました。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 関数がたとえば追加することで、一意の 1 つを作成する既定の名前を変更、名前のサブプロジェクトが既に存在する場合"_\<番号 >"にします。 呼び出し元がへの変更を受け入れる準備をする必要がありますで`lpUser`、 `lpSubProjPath`、および`lpAuxProjPath`します。 `lpSubProjPath`と`lpAuxProjPath`への呼び出しで引数を使用し、 [SccOpenProject](../extensibility/sccopenproject-function.md)します。 戻り時に呼び出し元によって、変更する必要があります。 これらの文字列は、ソース管理プラグインをプロジェクトに関連付けるために必要な情報を追跡するための方法を提供します。 呼び出し元の IDE では、プラグインは表示に適したできない可能性がある書式設定された文字列を使用できるため、これら 2 つのパラメーター、戻り時に表示されません。 関数は、成功または失敗のコードを返し、成功した場合、入力変数`lpSubProjPath`で新しいプロジェクトのプロジェクトの完全パス。  
  
 この機能に似ています、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), 点が 1 つを選択するように求めるのではなく、プロジェクトをサイレント モードで作成します。 ときに、`SccCreateSubProject`関数が呼び出されると、`lpParentProjName`と`lpAuxProjPath`空にならないし、は、有効なプロジェクトに対応します。 以前の呼び出しから IDE がこれらの文字列を受信したは、通常、`SccGetProjPath`関数または[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)します。  
  
 `lpUser`引数は、ユーザーの名前です。 IDE から既に受信していたのと同じユーザー名が渡される`SccGetProjPath`、ソース管理プラグインは、既定値として、名を使用する必要があります。 ユーザーが既にプラグインで開いている接続を使用して、プラグインする必要があります再試行関数はサイレント モードで動作を確認するプロンプトを回避します。 ただし、ログインに失敗した場合、プラグインのメッセージを表示するユーザー ログインと、パスの名前がバックアップの有効なログインを受信すると`lpUser`します。 この文字列は、プラグインの場合に変更する可能性があります、ため、IDE が常のバッファーを割り当てサイズ (SCC_USER_LEN + 1 または SCC_USER_SIZE で、null 終端文字のスペースが含まれています)。 文字列を変更すると、新しい文字列が有効なログイン名が (少なくとも古い文字列有効) にあります。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject と SccGetParentProjectPath テクニカル ノート  
 Visual Studio で、ユーザーは、ソース管理システムでの場所を選択するように求められます回数を最小限にするソリューションとプロジェクトをソース管理に追加を簡素化されています。 ソース管理プラグインは、新しい関数の両方をサポートしている場合、これらの変更が Visual Studio によってアクティブ化される`SccCreateSubProject`と`SccGetParentProjectPath`します。 ただし、次のレジストリ エントリは、これらの変更を無効にして、以前の Visual Studio (ソース管理プラグイン API バージョン 1.1) 動作に戻すには使用できます。  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword:00000001  
  
 Visual Studio が、新しい関数を使用しようとした場合、このレジストリ エントリが存在しないか、dword:00000000 に設定されている、`SccCreateSubProject`と`SccGetParentProjectPath`します。  
  
 レジストリ エントリが dword:00000001 に設定されている場合は、Visual Studio がこれらの新しい関数を使用しないし、Visual Studio の以前のバージョンと同じソース管理に追加する操作の動作します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)


---
title: SccCreateSubProject 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa87be4c9d22aca46814e8fa284fda9d587386a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject 関数
この関数が、指定した名前で指定された既存の親プロジェクトの下にサブプロジェクトを作成、`lpParentProjPath`引数。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力].(最大 SCC_USER_SIZE、NULL 終端文字を含む) のユーザー名。  
  
 lpParentProjPath  
 [in]親プロジェクトのパスを識別する文字列（NULL終端文字を含むSCC_PRJPATH_SIZEまで）。  
  
 lpSubProjName  
 [in]提案されたサブプロジェクト名（NULL終端文字を含むSCC_PRJPATH_SIZEまで）。  
  
 lpAuxProjPath  
 [入力、出力].(最大 SCC_PRJPATH_SIZE、NULL 終端文字を含む) プロジェクトを識別する文字列を補助します。  
  
 lpSubProjPath  
 [入力、出力].出力コンテンツ (SCC_PRJPATH_SIZE、NULL 終端文字を含む) までサブプロジェクトのパスを識別する文字列。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|サブプロジェクトを正常に作成されました。|  
|SCC_E_INITIALIZEFAILED|親プロジェクトを初期化できませんでした。|  
|SCC_E_INVALIDUSER|ユーザーは、ソース管理システム ログオンできませんでした。|  
|SCC_E_COULDNOTCREATEPROJECT|サブプロジェクトを作成することはできません。|  
|SCC_E_PROJSYNTAXERR|無効なプロジェクト構文があります。|  
|SCC_E_UNKNOWNPROJECT|ソース管理プラグインに不明な親プロジェクトです。|  
|SCC_E_INVALIDFILEPATH|無効であるか使用不可のファイルのパス。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_CONNECTIONFAILURE|ソース管理プラグイン接続の問題が発生しました。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 関数がの追加などにより、一意のものを作成する既定の名前を変更できる名前のサブプロジェクトが既に存在する場合"_\<番号 >"にします。 呼び出し元がへの変更を受け入れるように準備する必要があります`lpUser`、 `lpSubProjPath`、および`lpAuxProjPath`です。 `lpSubProjPath`と`lpAuxProjPath`への呼び出しで引数を使用して、 [SccOpenProject](../extensibility/sccopenproject-function.md)です。 関数が戻るとき、呼び出し元がこれらは変更できません。 これらの文字列は、ソース管理プロジェクトに関連付けるに必要な情報を追跡するプラグインの手段を提供します。 呼び出し元は、IDE では、プラグインは表示に適したできない可能性がある書式設定された文字列を使用できるため関数が戻るとき、これら 2 つのパラメーターは表示されません。 成功または失敗のコードを返し、成功した場合、入力変数`lpSubProjPath`を新しいプロジェクトへのプロジェクトの完全パス。  
  
 この関数がに似ていますが、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)をユーザーに 1 つを選択するのではなく、プロジェクトをサイレント モードで作成する点を除いて、します。 ときに、`SccCreateSubProject`関数が呼び出されると、`lpParentProjName`と`lpAuxProjPath`が空になり、有効なプロジェクトに対応します。 以前の呼び出しから IDE でこれらの文字列を受信した通常の`SccGetProjPath`関数または[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)です。  
  
 `lpUser`引数は、ユーザー名。 IDE がから既に受信していたものと同じ名前のユーザーに渡す`SccGetProjPath`と、ソース管理プラグインは、既定値として名前を使用する必要があります。 ユーザーは、プラグインで開いている接続を既に持っている場合、プラグインする必要があります再試行関数がサイレント モードで動作を確認するプロンプトを回避するのにします。 ただし、ログインに失敗した場合、プラグインが求めログインとは、パスの名前がバックアップの有効なログインを受け取ると、ユーザー`lpUser`です。 この文字列は、プラグインの場合に変更することがあります、ため、IDE が常のバッファーを割り当てサイズ (SCC_USER_LEN + 1 または SCC_USER_SIZE で、null 終端文字のスペースが含まれています)。 文字列が変更された場合、新しい文字列は有効なログイン名 (少なくとも古い文字列有効) にする必要があります。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>テクニカル ノート SccCreateSubProject および SccGetParentProjectPath  
 Visual studio ユーザーは、ソース管理システムで場所を選択するように要求する回数を最小限に抑えるにソース管理にソリューションおよびプロジェクトの追加を簡素化されています。 ソース管理プラグインは、新しい関数の両方をサポートしている場合、Visual Studio によってこれらの変更がアクティブ化`SccCreateSubProject`と`SccGetParentProjectPath`です。 ただし、次のレジストリ エントリは、これらの変更を無効にして、Visual Studio (ソース管理プラグイン API のバージョン 1.1) の以前の動作に戻すを使用できます。  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword:00000001  
  
 Visual Studio が、新しい関数を使用しようとした場合、このレジストリ エントリが存在しないか、dword:00000000 に設定されている、`SccCreateSubProject`と`SccGetParentProjectPath`です。  
  
 レジストリ エントリは dword:00000001 に設定されている場合は、Visual Studio はこれらの新しい関数を使用しようとはしませんおよびソース管理に追加の操作 Visual Studio の以前のバージョンで同様に動作します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
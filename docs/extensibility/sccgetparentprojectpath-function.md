---
title: "SccGetParentProjectPath 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetParentProjectPath
helpviewer_keywords: SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8395d73a48d4c8501ba834b2168b5bcbc8019b8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath 関数
この関数は、指定されたプロジェクトの親プロジェクト パスを決定します。 この関数は、ユーザーがソース管理に、Visual Studio プロジェクトを追加するときに呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力].(最大 SCC_USER_SIZE、NULL 終端文字を含む) ユーザー名。  
  
 lpProjPath  
 [in](最大 SCC_PRJPATH_SIZE、NULL 終端文字を含む) プロジェクトのパスを識別する文字列。  
  
 lpAuxProjPath  
 [入力、出力].(最大 SCC_PRJPATH_SIZE、NULL 終端文字を含む) プロジェクトを識別する文字列を補助します。  
  
 lpParentProjPath  
 [入力、出力].出力する、親プロジェクトまでのパス (SCC_PRJPATH_SIZE、NULL 終端文字を含む) を識別する文字列。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|親プロジェクト パスは正常に取得されました。|  
|SCC_E_INITIALIZEFAILED|プロジェクトを初期化できませんでした。|  
|SCC_E_INVALIDUSER|ユーザーは、ソース管理プラグイン ログオンできませんでした。|  
|SCC_E_UNKNOWNPROJECT|ソース管理プラグインに不明なプロジェクトです。|  
|SCC_E_INVALIDFILEPATH|無効であるか使用不可のファイルのパス。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_PROJSYNTAXERR|無効なプロジェクト構文があります。|  
|SCC_E_CONNECTIONFAILURE|接続の問題を格納します。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 この関数は、成功または失敗のコードを返し、成功した場合、入力変数`lpParentProjPath`を指定されたプロジェクトへのプロジェクトの完全パス。  
  
 この関数は、既存のプロジェクトのプロジェクトのパスの親を返します。 ルート プロジェクト関数に渡されたプロジェクト パスを返します (つまり、同じルート プロジェクト パス)。 プロジェクト パスはソース管理プラグインにのみ意味のある文字列であることに注意してください。  
  
 IDE が変更を反映する準備ができた、`lpUser`と`lpAuxProjPath`パラメーターも同様です。 IDE はこれらの文字列を保持しに渡したり、 [SccOpenProject](../extensibility/sccopenproject-function.md)ユーザーが開いた、今後このプロジェクト。 そのため、これらの文字列は、ソース管理プロジェクトに関連付ける必要な情報を追跡するプラグインの方法を提供します。  
  
 この関数がに似ていますが、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)プロジェクトを選択するユーザーに求めないする点を除いて、します。 既存のプロジェクトでのみが、新しいプロジェクトを作成します。  
  
 ときに`SccGetParentProjectPath`が呼び出されると、`lpProjPath`と`lpAuxProjPath`が空になり、有効なプロジェクトに対応します。 以前の呼び出しから IDE でこれらの文字列を受信した通常の`SccGetProjPath`関数。  
  
 `lpUser`引数は、ユーザー名。 IDE がから既に受信していたものと同じ名前のユーザーに渡す、`SccGetProjPath`関数、およびソース管理プラグインは、既定値と名前を使用する必要があります。 ユーザーは、プラグインで開いている接続を既に持っている場合、プラグインする必要があります再試行関数がサイレント モードで動作を確認するプロンプトを回避するのにします。 ただし、ログインに失敗した場合、プラグインが求めログインとは、パスの名前がバックアップの有効なログインを受け取ると、ユーザー`lpUser`です。 この文字列は、プラグインの場合に変更することがあります、ため、IDE が常にサイズのバッファーを割り当てる (`SCC_USER_LEN`+1)。 文字列が変更された場合、新しい文字列は有効なログイン名 (少なくとも古い文字列有効) にする必要があります。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>テクニカル ノート SccCreateSubProject および SccGetParentProjectPath  
 Visual studio ユーザーは、ソース管理システムで場所を選択するように要求する回数を最小限に抑えるにソース管理にソリューションおよびプロジェクトの追加を簡素化されています。 ソース管理プラグインは、新しい関数の両方をサポートしている場合、Visual Studio によってこれらの変更がアクティブ化、 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)と`SccGetParentProjectPath`関数。 ただし、次のレジストリ エントリは、これらの変更を無効にして、Visual Studio (ソース管理プラグイン API のバージョン 1.1) の以前の動作に戻すを使用できます。  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword:00000001  
  
 Visual Studio が、新しい関数を使用しようとした場合、このレジストリ エントリが存在しないか、dword:00000000 に設定されている、`SccCreateSubProject`と`SccGetParentProjectPath`です。  
  
 レジストリ エントリは dword:00000001 に設定されている場合は、Visual Studio はこれらの新しい関数を使用しようとはしませんおよびソース管理に追加の操作 Visual Studio の以前のバージョンで同様に動作します。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
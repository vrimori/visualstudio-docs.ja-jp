---
title: SccGetParentProjectPath 関数 |Microsoft Docs
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
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e75c3e39f2d4f56d40ca546291b2f86bd185f88
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744421"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、指定されたプロジェクトの親プロジェクトのパスを決定します。 この関数は、ユーザーがソース管理に Visual Studio プロジェクトを追加するときに呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]ソース管理プラグインのコンテキストのポインター。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力] (最大 SCC_USER_SIZE、NULL 終端文字も含めて) ユーザー名。  
  
 lpProjPath  
 [in]プロジェクトパスを識別する文字列（NULL終端文字を含むSCC_PRJPATH_SIZEまで）。  
  
 lpAuxProjPath  
 [入力、出力] (最大 SCC_PRJPATH_SIZE、NULL 終端文字も含めて) プロジェクトを識別する文字列を補助します。  
  
 lpParentProjPath  
 [入力、出力]親プロジェクトのパス (最大 SCC_PRJPATH_SIZE、NULL 終端文字を含む) を識別する文字列を出力します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|親プロジェクト パスが正常に取得します。|  
|SCC_E_INITIALIZEFAILED|プロジェクトを初期化できませんでした。|  
|SCC_E_INVALIDUSER|ユーザーは、ソース管理プラグイン ログオンできませんでした。|  
|SCC_E_UNKNOWNPROJECT|プロジェクトはソース管理プラグインを正常ではありません。|  
|SCC_E_INVALIDFILEPATH|無効であるか使用できないファイルのパス。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_PROJSYNTAXERR|無効なプロジェクトの構文です。|  
|SCC_E_CONNECTIONFAILURE|接続の問題を格納します。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、成功または失敗のコードを返すし、成功した場合、入力変数`lpParentProjPath`指定されたプロジェクトにプロジェクトの完全パスを使用します。  
  
 この関数は、既存のプロジェクトのプロジェクトのパスの親を返します。 ルート プロジェクトでは、関数に渡されたプロジェクト パスを返します (つまり、同じルート プロジェクト パス)。 プロジェクトのパスはソース管理プラグインにのみ意味のある文字列であることに注意してください。  
  
 IDE が変更を適用する準備ができた、`lpUser`と`lpAuxProjPath`パラメーターも同様です。 IDE はこれらの文字列を保持しに渡したり、 [SccOpenProject](../extensibility/sccopenproject-function.md)ユーザーが開いた、今後このプロジェクト。 そのため、これらの文字列はソース管理プラグインをプロジェクトに関連付ける必要な情報を追跡する方法を提供します。  
  
 この機能に似ています、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)プロジェクトを選択するユーザーを求めないことを除いて、します。 既存のプロジェクトでのみが、新しいプロジェクトを作成します。  
  
 ときに`SccGetParentProjectPath`が呼び出され、`lpProjPath`と`lpAuxProjPath`空にならないし、は、有効なプロジェクトに対応します。 以前の呼び出しから IDE がこれらの文字列を受信したは、通常、`SccGetProjPath`関数。  
  
 `lpUser`引数は、ユーザーの名前です。 IDE から既に受信していたのと同じユーザー名が渡される、`SccGetProjPath`関数、およびソース管理プラグインは、既定値としての名前を使用する必要があります。 ユーザーが既にプラグインで開いている接続を使用して、プラグインする必要があります再試行関数はサイレント モードで動作を確認するプロンプトを回避します。 ただし、ログインに失敗した場合、プラグインのメッセージを表示するユーザー ログインと、パスの名前がバックアップの有効なログインを受信すると`lpUser`します。 プラグインがこの文字列を変更するため、IDE が常にサイズのバッファーを割り当てる (`SCC_USER_LEN`+1)。 文字列を変更すると、新しい文字列が有効なログイン名が (少なくとも古い文字列有効) にあります。  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject と SccGetParentProjectPath テクニカル ノート  
 Visual Studio で、ユーザーは、ソース管理システムでの場所を選択するように求められます回数を最小限にするソリューションとプロジェクトをソース管理に追加を簡素化されています。 ソース管理プラグインは、新しい関数の両方をサポートしている場合、Visual Studio によってこれらの変更がアクティブ化、 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)と`SccGetParentProjectPath`関数。 ただし、次のレジストリ エントリは、これらの変更を無効にして、以前の Visual Studio (ソース管理プラグイン API バージョン 1.1) 動作に戻すには使用できます。  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl"= dword:00000001  
  
 Visual Studio が、新しい関数を使用しようとした場合、このレジストリ エントリが存在しないか、dword:00000000 に設定されている、`SccCreateSubProject`と`SccGetParentProjectPath`します。  
  
 レジストリ エントリが dword:00000001 に設定されている場合は、Visual Studio がこれらの新しい関数を使用しないし、Visual Studio の以前のバージョンと同じソース管理に追加する操作の動作します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)


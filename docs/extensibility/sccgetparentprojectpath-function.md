---
title: "SccGetParentProjectPath 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetParentProjectPath"
helpviewer_keywords: 
  - "SccGetParentProjectPath 関数"
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccGetParentProjectPath 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、指定したプロジェクトの親プロジェクトのパスを決定します。 ユーザーがソース管理に Visual Studio プロジェクトを追加する場合は、この関数が呼び出されます。  
  
## 構文  
  
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
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグインのコンテキストのポインター。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 \[入力、出力\]\(最大 SCC\_USER\_SIZE、NULL 終端文字も含めて\) ユーザー名。  
  
 lpProjPath  
 \[in\]\(最大 SCC\_PRJPATH\_SIZE、NULL 終端文字も含めて\) プロジェクトのパスを識別する文字列。  
  
 lpAuxProjPath  
 \[入力、出力\]\(最大 SCC\_PRJPATH\_SIZE、NULL 終端文字も含めて\) プロジェクトを識別する文字列を補助します。  
  
 lpParentProjPath  
 \[入力、出力\]\(最大 SCC\_PRJPATH\_SIZE、NULL 終端文字も含めて\)、親プロジェクトのパスを識別する文字列を出力します。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|親プロジェクト パスが正常に取得しました。|  
|SCC\_E\_INITIALIZEFAILED|プロジェクトを初期化できませんでした。|  
|SCC\_E\_INVALIDUSER|ユーザーは、ソース管理プラグイン ログオンできませんでした。|  
|SCC\_E\_UNKNOWNPROJECT|プロジェクトは、ソース管理プラグインには不明です。|  
|SCC\_E\_INVALIDFILEPATH|無効であるか使用不可のファイルのパス。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_PROJSYNTAXERR|無効なプロジェクト構文があります。|  
|SCC\_E\_CONNECTIONFAILURE|接続の問題を格納します。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|不特定のエラーです。|  
  
## 解説  
 この関数は、成功または失敗コードが返され、成功した場合、入力変数 `lpParentProjPath` 指定されたプロジェクトにプロジェクトの完全パスを使用します。  
  
 この関数は、親の既存のプロジェクトのプロジェクトのパスを返します。 ルート プロジェクト関数に渡されたプロジェクト パスを返します \(つまり、同じルート プロジェクト パス\)。 プロジェクト パスは、ソース管理プラグインにとってのみ意味がある文字列であることに注意してください。  
  
 IDE に変更を適用する準備ができて、 `lpUser` と `lpAuxProjPath` パラメーターも同様です。 IDE はこれらの文字列を永続化およびに渡したり、 [SccOpenProject](../extensibility/sccopenproject-function.md) 、ユーザーが開き、\[今後このプロジェクトです。 これらの文字列は、そのため、ソース管理プロジェクトに関連付ける必要な情報を追跡するプラグインの手段を提供します。  
  
 この関数は、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), 点が、プロジェクトを選択するユーザーから求められません。 既存のプロジェクトでのみが、新しいプロジェクトを作成します。  
  
 `SccGetParentProjectPath` が呼び出されると、 `lpProjPath` と `lpAuxProjPath` 空にならないし、は、有効なプロジェクトに対応します。 これらの文字列が前の呼び出しから IDE が受信した通常の `SccGetProjPath` 関数です。  
  
 `lpUser` 引数は、ユーザー名。 IDE はから既に受信していたのと同じユーザー名に適合、 `SccGetProjPath` 関数、およびソース管理プラグインは、既定値と名前を使用する必要があります。 ユーザーは、プラグインで開かれた接続を既に持っている場合、プラグインする必要がありますしようと、関数が何も行わずに動作を確認のプロンプトを行わないようにします。 ただし、ログインに失敗した場合、プラグインでメッセージを表示してユーザーをログインに対して、パスの名前がバックアップの有効なログインを受信すると `lpUser`です。 プラグインがこの文字列を変更するため、IDE が常にサイズのバッファーを割り当てる \(`SCC_USER_LEN`\+1\)。 文字列を変更すると、新しい文字列が有効なログイン名が \(少なくとも、古い文字列有効\) にあります。  
  
## テクニカル ノート SccCreateSubProject および SccGetParentProjectPath  
 ソース管理システムで場所を選択を求める回数を最小限にする Visual Studio でソース管理へのソリューションとプロジェクトの追加を簡素化されています。 ソース管理プラグインでは、新しい関数の両方がサポートする場合、Visual Studio によってこれらの変更がアクティブ化、 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) と `SccGetParentProjectPath` 関数です。 ただし、次のレジストリ エントリは、これらの変更を無効にして、以前の Visual Studio \(ソース管理プラグインの API バージョン 1.1\) 動作に戻すには使用できます。  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\]"DoNotCreateSolutionRootFolderInSourceControl"\= dword:00000001  
  
 Visual Studio が新しい関数を使用しようとした場合、このレジストリ エントリが存在しないか、dword:00000000 に設定されている、 `SccCreateSubProject`と`SccGetParentProjectPath`します。  
  
 レジストリ エントリは、dword:00000001 に設定されている場合は、Visual Studio はこれらの新しい関数を使用しようとはしませんし、ソース管理に追加の操作が Visual Studio の以前のバージョンで同様に動作します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
---
title: "SccCreateSubProject 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCreateSubProject"
helpviewer_keywords: 
  - "SccCreateSubProject 関数"
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# SccCreateSubProject 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数が、指定した名前で指定された既存の親プロジェクトの下にサブプロジェクトを作成、 `lpParentProjPath` 引数。  
  
## 構文  
  
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
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグインのコンテキストのポインター。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 \[入力、出力\]\(最大 SCC\_USER\_SIZE、NULL 終端文字も含めて\) のユーザー名。  
  
 lpParentProjPath  
 \[in\]\(最大 SCC\_PRJPATH\_SIZE、NULL 終端文字も含めて\)、親プロジェクトのパスを識別する文字列。  
  
 lpSubProjName  
 \[in\]\(最大 SCC\_PRJPATH\_SIZE、NULL 終端文字も含めて\) サブプロジェクトの推奨される名前です。  
  
 lpAuxProjPath  
 \[入力、出力\]\(最大 SCC\_PRJPATH\_SIZE、NULL 終端文字も含めて\) プロジェクトを識別する文字列を補助します。  
  
 lpSubProjPath  
 \[入力、出力\]\(最大 SCC\_PRJPATH\_SIZE、NULL 終端文字も含めて\) そのサブプロジェクトのパスを識別する文字列を出力します。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|サブプロジェクトが正常に作成します。|  
|SCC\_E\_INITIALIZEFAILED|親プロジェクトを初期化できませんでした。|  
|SCC\_E\_INVALIDUSER|ユーザーは、ソース管理システム ログオンできませんでした。|  
|SCC\_E\_COULDNOTCREATEPROJECT|サブプロジェクトを作成できません。|  
|SCC\_E\_PROJSYNTAXERR|無効なプロジェクト構文があります。|  
|SCC\_E\_UNKNOWNPROJECT|親プロジェクトは、ソース管理プラグインには不明です。|  
|SCC\_E\_INVALIDFILEPATH|無効であるか使用不可のファイルのパス。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_CONNECTIONFAILURE|ソース コントロールのプラグイン接続の問題が発生しました。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|不特定のエラーです。|  
  
## 解説  
 名前のサブプロジェクトが既に存在する場合、関数は、「\_ \< 番号 \>」の追加などにより、一意の 1 つを作成する既定の名前を変更できます。 呼び出し元への変更を確定する必要があります `lpUser`, 、`lpSubProjPath`, 、および `lpAuxProjPath`です。`lpSubProjPath` と`lpAuxProjPath` への呼び出しで引数を使用して、 [SccOpenProject](../extensibility/sccopenproject-function.md)です。 関数が戻るとき、呼び出し元がない変更する必要があります。 これらの文字列は、ソース管理プロジェクトに関連付けるに必要な情報を追跡するプラグインの手段を提供します。 呼び出し元の IDE では、プラグインは表示に適したできない可能性がある書式設定された文字列を使用できるため関数が戻るとき、これら 2 つのパラメーターは表示されません。 返し、成功または失敗コード、成功した場合、入力変数 `lpSubProjPath` は新しいプロジェクトにプロジェクトの完全パスを使用します。  
  
 この関数は、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), 点が 1 つを選択するユーザー入力を求めるのではなく、プロジェクトを暗黙的に作成します。 ときに、 `SccCreateSubProject` 関数が呼び出されると、 `lpParentProjName` と `lpAuxProjPath` 空にならないし、は、有効なプロジェクトに対応します。 これらの文字列が前の呼び出しから IDE が受信した通常の `SccGetProjPath` 関数または [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)です。  
  
 `lpUser` 引数は、ユーザー名。 IDE はから既に受信していたのと同じユーザー名に適合 `SccGetProjPath`, 、ソース管理プラグインは、既定値として、名を使用する必要があります。 ユーザーは、プラグインで開かれた接続を既に持っている場合、プラグインする必要がありますしようと、関数が何も行わずに動作を確認のプロンプトを行わないようにします。 ただし、ログインに失敗した場合、プラグインでメッセージを表示してユーザーをログインに対して、パスの名前がバックアップの有効なログインを受信すると `lpUser`です。 プラグインがこの文字列を変更するため、IDE が常のバッファーを割り当て \(SCC\_USER\_LEN \+ 1 または SCC\_USER\_SIZE で、null 終端文字のスペースが含まれます\) のサイズを変更します。 文字列を変更すると、新しい文字列が有効なログイン名が \(少なくとも、古い文字列有効\) にあります。  
  
## テクニカル ノート SccCreateSubProject および SccGetParentProjectPath  
 ソース管理システムで場所を選択を求める回数を最小限にする Visual Studio でソース管理へのソリューションとプロジェクトの追加を簡素化されています。 ソース管理プラグインでは、新しい関数の両方がサポートする場合、これらの変更が Visual Studio によってアクティブ化される `SccCreateSubProject` と `SccGetParentProjectPath`です。 ただし、次のレジストリ エントリは、これらの変更を無効にして、以前の Visual Studio \(ソース管理プラグインの API バージョン 1.1\) 動作に戻すには使用できます。  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\]"DoNotCreateSolutionRootFolderInSourceControl"\= dword:00000001  
  
 Visual Studio が新しい関数を使用しようとした場合、このレジストリ エントリが存在しないか、dword:00000000 に設定されている、 `SccCreateSubProject` と `SccGetParentProjectPath`です。  
  
 レジストリ エントリは、dword:00000001 に設定されている場合は、Visual Studio はこれらの新しい関数を使用しようとはしませんし、ソース管理に追加の操作が Visual Studio の以前のバージョンで同様に動作します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
---
title: "SccOpenProject 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccOpenProject"
helpviewer_keywords: 
  - "SccOpenProject 関数"
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# SccOpenProject 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、既存のソース管理プロジェクトを開くか、新しいものを再作成します。  
  
## 構文  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 \[入力、出力\]ユーザー \(not NULL 終端文字も含めて SCC\_USER\_SIZE を超える\) の名前。  
  
 lpProjName  
 \[in\]プロジェクトの名前を識別する文字列。  
  
 lpLocalProjPath  
 \[in\]プロジェクトの作業フォルダーへのパス。  
  
 lpAuxProjPath  
 \[入力、出力\]プロジェクト \(not NULL 終端文字も含めて SCC\_AUXPATH\_SIZE を超える\) を識別する、オプションの補助文字列。  
  
 lpComment  
 \[in\]作成される新しいプロジェクトに対するコメントします。  
  
 lpTextOutProc  
 \[in\]プラグインのソース管理からの出力テキストを表示するオプションのコールバック関数。  
  
 dwFlags  
 \[in\]信号をプロジェクトがソースに不明な場合に作成する新しいプロジェクトが必要かどうかを制御プラグインします。 値の組み合わせを指定できます `SCC_OP_CREATEIFNEW` と `SCC_OP_SILENTOPEN.`  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|プロジェクトを開くときに成功しました。|  
|SCC\_E\_INITIALIZEFAILED|プロジェクトを初期化できませんでした。|  
|SCC\_E\_INVALIDUSER|ユーザーは、ソース管理システム ログオンできませんでした。|  
|SCC\_E\_COULDNOTCREATEPROJECT|呼び出しの前に、プロジェクトがありませんでした `SCC_OPT_CREATEIFNEW` フラグを設定したが、プロジェクトを作成できませんでした。|  
|SCC\_E\_PROJSYNTAXERR|無効なプロジェクト構文があります。|  
|SCC\_E\_UNKNOWNPROJECT|プロジェクトでは、ソース管理プラグイン、未知と `SCC_OPT_CREATEIFNEW` フラグが設定されませんでした。|  
|SCC\_E\_INVALIDFILEPATH|無効であるか使用不可のファイルのパス。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_NONSPECFICERROR|不特定のエラーです。ソース管理システムは初期化されませんでした。|  
  
## 解説  
 IDE がユーザー名を渡すことがあります \(`lpUser`\)、単に空の文字列にポインター パス可能性があります。 ユーザー名がある場合、ソース管理プラグイン使用してください、既定値として。 ただし、名が渡されなかった場合、または指定した名前、ログインに失敗した場合は、プラグインにログインを求める必要がありで有効な名前を返す `lpUser` 有効なログインを受信すると`.` プラグインがユーザー名の文字列を変更するため、IDE が常にサイズのバッファーを割り当てる \(`SCC_USER_LEN`\+1 または SCC\_USER\_SIZE で、null 終端文字用の領域が含まれています\)。  
  
> [!NOTE]
>  実行する必要があります、IDE の最初のアクションへの呼び出しがあります、 `SccOpenProject` 関数または [SccGetProjPath](../extensibility/sccgetprojpath-function.md)です。 このため、これらの両方に同一ある `lpUser` パラメーター。  
  
 `lpAuxProjPath` `lpProjName` ソリューション ファイルから読み取られるへの呼び出しから返された、または、 `SccGetProjPath` 関数です。 これらのパラメーターをソース管理プラグインがプロジェクトに関連付ける文字列を含みプラグインにのみ意味のあります。 ソリューション ファイルにこのような文字列がないと、ユーザーが参照するように要求されていない場合 \(を介して文字列を返すよう、 `SccGetProjPath` 関数\)、IDE は、両方の空の文字列を渡して `lpAuxProjPath` と `lpProjName`, をこの関数が戻るときに、プラグインで更新するこれらの値を期待します。  
  
 `lpTextOutProc` ソース管理プラグインをコマンドの出力結果を表示できるようにするための IDE によって提供されるコールバック関数へのポインターです。 このコールバック関数がで詳しく説明されている [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)します。  
  
> [!NOTE]
>  ソース管理プラグインが活用しようとすると場合、これを設定している必要があります、 `SCC_CAP_TEXTOUT` フラグ、 [SccInitialize](../extensibility/sccinitialize-function.md)です。 このフラグが設定されていない場合、または IDE では、この機能をサポートしていない場合 `lpTextOutProc` は `NULL`です。  
  
 `dwFlags` パラメーターは、開いているプロジェクトが現在存在しないことに、結果を制御します。 構成は次の 2 つのビットフラグ `SCC_OP_CREATEIFNEW` と `SCC_OP_SILENTOPEN`です。 この関数は、既に開いているプロジェクトが存在する場合は、単にプロジェクトが開きますして返します `SCC_OK`します。 プロジェクトが存在しない場合、および場合、 `SCC_OP_CREATEIFNEW` フラグがオン、ソース管理プラグインは、ソース管理システムで、プロジェクトを作成、開くには、および返す `SCC_OK`します。 プロジェクトが存在しない場合、および場合、 `SCC_OP_CREATEIFNEW` フラグがオフ、プラグインし、確認する、 `SCC_OP_SILENTOPEN` フラグ。 フラグがオンでない場合、プラグイン可能性があります、ユーザーに要求、プロジェクトの名前。 フラグがあるかどうか、プラグインする必要があります戻ります `SCC_E_UNKNOWNPROJECT`します。  
  
## 呼び出し順序  
 通常、イベントの [SccInitialize](../extensibility/sccinitialize-function.md) を開くには、ソース コントロール セッションを最初に呼び出すとします。 呼び出しは、セッションで構成される `SccOpenProject`, 、別のソース管理プラグインの API 関数呼び出しの後を呼び出して終了、 [SccCloseProject](../extensibility/scccloseproject-function.md)です。 このようなセッションを前に何度も繰り返すことがあります、 [SccUninitialize](../extensibility/sccuninitialize-function.md) が呼び出されます。  
  
 ソース管理プラグインを設定する場合、 `SCC_CAP_REENTRANT` 内のビット `SccInitialize`, 、上のセッションの順序は、並列で何度も繰り返し可能性があります使用し、します。 異なる `pvContext` 構造体は、各、別のセッションを追跡 `pvContext` は一度に 1 つの開いているプロジェクトに関連付けられています。 に基づいて、`pvContext` パラメーター、プラグインを特定するプロジェクトは、特定の呼び出しで参照されています。 機能ビットする場合 `SCC_CAP_REENTRANT` が設定されていない nonreentrant ソース管理プラグインは、複数のプロジェクトを操作する機能に制限されます。  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT` ビットは、ソース管理プラグインの API のバージョン 1.1 で導入されました。 設定されていないか、バージョン 1.0 では無視され、すべてのバージョン 1.0 ソース管理プラグインは nonreentrant と見なされます。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [文字列長の制限](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
---
title: "SccOpenProject 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccOpenProject
helpviewer_keywords: SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d61b4fade0775c5e017a85fa5364779bc567b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccopenproject-function"></a>SccOpenProject 関数
この関数は、既存のソース管理プロジェクトを開くか、新規に作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力].ユーザー (を超過しない SCC_USER_SIZE、NULL 終端文字を含む) の名前。  
  
 lpProjName  
 [in]プロジェクトの名前を識別する文字列。  
  
 lpLocalProjPath  
 [in]プロジェクトの作業フォルダーへのパス。  
  
 lpAuxProjPath  
 [入力、出力].プロジェクト (を超過しない SCC_AUXPATH_SIZE、NULL 終端文字を含む) を識別する、省略可能なの補助文字列。  
  
 lpComment  
 [in]作成される新しいプロジェクトにコメントします。  
  
 lpTextOutProc  
 [in]ソース管理プラグインからの出力テキストを表示するオプションのコールバック関数。  
  
 dwFlags  
 [in]信号をプロジェクトがソースに不明な場合に作成する新しいプロジェクトが必要かどうかを制御プラグインします。 値の組み合わせを指定できます`SCC_OP_CREATEIFNEW`と`SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|プロジェクトを開くときに成功しました。|  
|SCC_E_INITIALIZEFAILED|プロジェクトを初期化できませんでした。|  
|SCC_E_INVALIDUSER|ユーザーは、ソース管理システム ログオンできませんでした。|  
|SCC_E_COULDNOTCREATEPROJECT|呼び出しの前に、プロジェクトがありませんでした `SCC_OPT_CREATEIFNEW`フラグが設定されましたが、プロジェクトを作成できませんでした。|  
|SCC_E_PROJSYNTAXERR|無効なプロジェクト構文があります。|  
|SCC_E_UNKNOWNPROJECT|プロジェクトがソース管理プラグイン、認識できない、`SCC_OPT_CREATEIFNEW`フラグが設定されていません。|  
|SCC_E_INVALIDFILEPATH|無効であるか使用不可のファイルのパス。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECFICERROR|不特定のエラーです。ソース管理システムは初期化されませんでした。|  
  
## <a name="remarks"></a>コメント  
 IDE は、ユーザー名を渡します (`lpUser`)、またはポインターで空の文字列を渡すことがあります単にします。 ユーザー名がある場合、ソース管理プラグインとして使用してください、既定値です。 ただし、名前が渡されなかった場合、または指定した名前、ログインに失敗した場合は、プラグインにログインするユーザーを要求する必要がありで有効な名前を返す`lpUser`受信すると、有効なログイン`.`プラグインは、ユーザー名の文字列を変更するため、IDE がサイズのバッファーを割り当て、常に (`SCC_USER_LEN`+1 または SCC_USER_SIZE で、null 終端文字のスペースが含まれています)。  
  
> [!NOTE]
>  最初のアクションを実行する必要があります、IDE への呼び出しがあります、`SccOpenProject`関数または[SccGetProjPath](../extensibility/sccgetprojpath-function.md)です。 このため、これらの両方がある同じ`lpUser`パラメーター。  
  
 `lpAuxProjPath`および`lpProjName`ソリューション ファイルから読み取るへの呼び出しから返されるか、`SccGetProjPath`関数。 これらのパラメーターは、ソース管理プラグインをプロジェクトに関連付ける文字列が含まれてし、プラグインにのみ意味があるものです。 ソリューション ファイルでこのような文字列がないと、ユーザーが参照するように要求されていない場合 (と、文字列を返すと、`SccGetProjPath`関数)、IDE は、両方の空の文字列を渡す`lpAuxProjPath`と`lpProjName`、更新するこれらの値が必要ですが、プラグインするときにこの関数を返します。  
  
 `lpTextOutProc`ソース管理コマンドの結果の出力を表示するためにプラグインするための IDE によって提供されるコールバック関数へのポインターです。 このコールバック関数がで詳しく説明されている[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)です。  
  
> [!NOTE]
>  場合は、ソース管理プラグインでは、これを利用しようとして、設定がありますが、`SCC_CAP_TEXTOUT`フラグ、 [SccInitialize](../extensibility/sccinitialize-function.md)です。 このフラグが設定されていない場合、または IDE では、この機能をサポートしていない場合`lpTextOutProc`なります`NULL`です。  
  
 `dwFlags`パラメーターは、開いているプロジェクトが現在存在していないことに結果を制御します。 2 つのビットフラグから成る`SCC_OP_CREATEIFNEW`と`SCC_OP_SILENTOPEN`です。 この関数は、既に開いているプロジェクトが存在する場合は、単にプロジェクトが開きますして返します`SCC_OK`です。 場合と、プロジェクトが存在しない場合、`SCC_OP_CREATEIFNEW`フラグがオン、ソース管理プラグインは、ソース管理システムで、プロジェクトを作成を開くと、および返す`SCC_OK`です。 場合と、プロジェクトが存在しない場合、`SCC_OP_CREATEIFNEW`フラグがオフ、プラグインを確認する、`SCC_OP_SILENTOPEN`フラグ。 そのフラグがオンでない場合、プラグイン要求があります、プロジェクト名のユーザー。 そのフラグがあるかどうか、プラグインは返されるだけ`SCC_E_UNKNOWNPROJECT`です。  
  
## <a name="calling-order"></a>呼び出し順序  
 通常、イベントの中に、 [SccInitialize](../extensibility/sccinitialize-function.md)ソース コントロール セッションを最初に呼び出されるとします。 セッションはへの呼び出しで構成される`SccOpenProject`の別のソース管理プラグイン API 関数呼び出しの後に、呼び出しを終了、 [SccCloseProject](../extensibility/scccloseproject-function.md)です。 このようなセッションは前に何回か繰り返される可能性があります、 [SccUninitialize](../extensibility/sccuninitialize-function.md)と呼びます。  
  
 ソース管理プラグインを設定する場合、`SCC_CAP_REENTRANT`内のビット`SccInitialize`、上のセッション順序可能性がありますが重複する並列します。 異なる`pvContext`構造体で、別々 のセッションを追跡する`pvContext`は一度に 1 つのプロジェクトを開くと関連付けられています。 に基づいて、`pvContext`パラメーター、プラグインを決定できます、特定の呼び出しでどのプロジェクトが参照されています。 場合は、機能のビット`SCC_CAP_REENTRANT`が設定されていない nonreentrant ソース管理プラグインは複数のプロジェクトを操作するには、その機能に制限されます。  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT`ビットは、ソース管理プラグイン API のバージョン 1.1 で導入されました。 設定されていないか、バージョン 1.0 では無視され、すべてのバージョン 1.0 ソース管理プラグインは nonreentrant と見なされます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [文字列の長さの制限](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
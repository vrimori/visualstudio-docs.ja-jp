---
title: SccOpenProject 関数 |Microsoft Docs
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
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0bcb33ee214c11c369e17dc90bce138c0014fc6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768269"
---
# <a name="sccopenproject-function"></a>SccOpenProject 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、既存のソース管理プロジェクトを開きますか、新しいを作成します。  
  
## <a name="syntax"></a>構文  
  
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
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力] (NULL ターミネータを含めた SCC_USER_SIZE を超過しない)、ユーザーの名前。  
  
 lpProjName  
 [in]プロジェクトの名前を識別する文字列。  
  
 lpLocalProjPath  
 [in]プロジェクトの作業フォルダーへのパス。  
  
 lpAuxProjPath  
 [入力、出力]プロジェクト (NULL ターミネータを含めた SCC_AUXPATH_SIZE を超過しない) を識別する、省略可能の補助文字列。  
  
 lpComment  
 [in]作成される新しいプロジェクトにコメントします。  
  
 lpTextOutProc  
 [in]ソース管理プラグインからの出力テキストを表示するオプションのコールバック関数。  
  
 dwFlags  
 [in]信号をプロジェクトがソースに不明の場合に作成する新しいプロジェクトが必要かどうかを制御プラグイン。 値の組み合わせを指定できます`SCC_OP_CREATEIFNEW`と `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|プロジェクトを開くときに成功しました。|  
|SCC_E_INITIALIZEFAILED|プロジェクトを初期化できませんでした。|  
|SCC_E_INVALIDUSER|ユーザーは、ソース管理システム ログオンできませんでした。|  
|SCC_E_COULDNOTCREATEPROJECT|呼び出しの前に、プロジェクトがありませんでした `SCC_OPT_CREATEIFNEW`フラグを設定したが、プロジェクトを作成できませんでした。|  
|SCC_E_PROJSYNTAXERR|無効なプロジェクトの構文です。|  
|SCC_E_UNKNOWNPROJECT|プロジェクトがソース管理プラグインは、認識できない、`SCC_OPT_CREATEIFNEW`フラグが設定されませんでした。|  
|SCC_E_INVALIDFILEPATH|無効であるか使用できないファイルのパス。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NONSPECFICERROR|不特定のエラーです。ソース管理システムは初期化されませんでした。|  
  
## <a name="remarks"></a>Remarks  
 ユーザー名を渡すことが IDE (`lpUser`)、またはポインターで空の文字列に渡すことがありますだけです。 ユーザー名がある場合、ソース管理プラグインとして使用してください、既定値。 ただし、名前が渡されなかった場合、または指定した名前、ログインに失敗した場合は、プラグイン ログインするユーザーにメッセージを表示してで有効な名前を返す`lpUser`有効なログインを受信すると`.`プラグインは、ユーザー名文字列を変更可能性がありますので、、IDE は常にサイズのバッファーを割り当てます (`SCC_USER_LEN`+1 または SCC_USER_SIZE で、null 終端文字のスペースが含まれています)。  
  
> [!NOTE]
>  最初のアクションを実行する必要があります、IDE への呼び出しがあります、`SccOpenProject`関数または[SccGetProjPath](../extensibility/sccgetprojpath-function.md)します。 このため、これらの両方に同一ある`lpUser`パラメーター。  
  
 `lpAuxProjPath` `lpProjName` 、ソリューション ファイルから読み取られますへの呼び出しから返された、または、`SccGetProjPath`関数。 これらのパラメーターは、ソース管理プラグインをプロジェクトに関連付ける文字列を含むし、プラグインにのみ意味があります。 ソリューション ファイルにこのような文字列がないと、ユーザーが参照するように要求されていない場合 (は、文字列を返しますが、`SccGetProjPath`関数)、IDE は、両方の空の文字列を渡す`lpAuxProjPath`と`lpProjName`とでこれらの値を更新する必要がありますプラグインのときにこの関数を返します。  
  
 `lpTextOutProc` ソース管理プラグイン コマンドの結果の出力を表示できるようにするための IDE によって提供されるコールバック関数へのポインターです。 このコールバック関数がで詳しく説明されている[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)します。  
  
> [!NOTE]
>  設定する必要がありますが、ソース管理プラグインでは、この利用しようとして場合、`SCC_CAP_TEXTOUT`フラグ、 [SccInitialize](../extensibility/sccinitialize-function.md)します。 フラグが設定されていない場合、または IDE では、この機能をサポートしていない場合`lpTextOutProc`なります`NULL`します。  
  
 `dwFlags`パラメーターは、開いているプロジェクトが現在存在していないことに、結果を制御します。 2 つのビットフラグから成る`SCC_OP_CREATEIFNEW`と`SCC_OP_SILENTOPEN`します。 関数は、既に開いているプロジェクトが存在する場合は、単にプロジェクトが開きますを返します`SCC_OK`します。 プロジェクトが存在しない場合、`SCC_OP_CREATEIFNEW`フラグがオンで、ソース管理プラグインは、ソース管理システムで、プロジェクトを作成、それを開いて、および返す`SCC_OK`します。 場合と、プロジェクトが存在しない場合、`SCC_OP_CREATEIFNEW`フラグがオフ、プラグインする必要がありますし、確認、`SCC_OP_SILENTOPEN`フラグ。 フラグがオンがない場合、プラグイン求めることができます、プロジェクト名のユーザー。 フラグがであるかどうか、プラグインを返すだけ`SCC_E_UNKNOWNPROJECT`です。  
  
## <a name="calling-order"></a>呼び出し順序  
 イベントの通常のコースでは、 [SccInitialize](../extensibility/sccinitialize-function.md)ソース コントロール セッションを最初に呼び出されるとします。 セッションはへの呼び出しで構成される`SccOpenProject`、その他のソース管理プラグイン API 関数呼び出しの後におよびへの呼び出しが中止、 [SccCloseProject](../extensibility/scccloseproject-function.md)します。 このようなセッションは、前に何度も繰り返すことが、 [SccUninitialize](../extensibility/sccuninitialize-function.md)が呼び出されます。  
  
 ソース管理プラグインのセットがある場合、`SCC_CAP_REENTRANT`ビット`SccInitialize`、上のセッションの順序は、並列で何度も繰り返し可能性があります使用し、します。 異なる`pvContext`構造体で、異なるセッションを追跡する`pvContext`は一度に 1 つ開いているプロジェクトに関連付けられています。 に基づいて、`pvContext`パラメーター、プラグインを調べるどのプロジェクトが、特定の呼び出しで参照されています。 場合は、機能のビット`SCC_CAP_REENTRANT`が設定されていない nonreentrant ソース管理プラグインは、複数のプロジェクトを操作する機能に制限されます。  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT`ビットは、ソース管理プラグイン API のバージョン 1.1 で導入されました。 設定されていないか、バージョン 1.0 では無視され、すべてのバージョン 1.0 ソース管理プラグインは nonreentrant と見なされます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [文字列長の制限](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)


---
title: SccGetProjPath 関数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da39a5216f313371753a1b52e411aba093419e0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935801"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 関数
この関数は、ソース管理プラグインにのみ意味のある文字列であるプロジェクトのパスをユーザーに求めます。 これには、ユーザーの場合は呼び出されます。  
  
-   新しいプロジェクトを作成します。  
  
-   バージョン管理への既存のプロジェクトの追加  
  
-   既存のバージョン コントロール プロジェクトを検索しようとしています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力]ユーザー名 (NULL ターミネータを含めた SCC_USER_SIZE を超過しない)  
  
 lpProjName  
 [入力、出力]IDE プロジェクト、プロジェクトのワークスペースまたはメイクファイル (NULL ターミネータを含めた SCC_PRJPATH_SIZE を超過しない) の名前。  
  
 lpLocalPath  
 [入力、出力]プロジェクトの作業用のパス。 場合`bAllowChangePath`は`TRUE`、ソース管理プラグインは、この文字列 (null ターミネータを含めた _MAX_PATH を超過しない) を変更できます。  
  
 lpAuxProjPath  
 [入力、出力]返されるプロジェクトのパス (NULL ターミネータを含めた SCC_PRJPATH_SIZE を超過しない) のバッファー。  
  
 bAllowChangePath  
 [in]この場合`TRUE`、ソース管理プラグインを要求したり変更したり、`lpLocalPath`文字列。  
  
 pbNew  
 [入力、出力]導入される値では、新しいプロジェクトを作成するかどうかを示します。 返される値は、プロジェクトの作成の成功を表します。  
  
|着信|解釈|  
|--------------|--------------------|  
|true|ユーザーは、新しいプロジェクトを作成可能性があります。|  
|false|ユーザーは、新しいプロジェクトを作成できません。|  
  
|発信|解釈|  
|--------------|--------------------|  
|true|新しいプロジェクトが作成されました。|  
|false|既存のプロジェクトが選択されました。|  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|プロジェクトは正常に作成または取得します。|  
|SCC_I_OPERATIONCANCELED|操作が取り消されました。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。|  
|SCC_E_CONNECTIONFAILURE|ソース管理システムに接続しようとしています。 問題が発生しました。|  
|SCC_E_NONSPECIFICERROR|未指定のエラーが発生しました。|  
  
## <a name="remarks"></a>Remarks  
 この関数の目的は、パラメーターを取得するための IDE の`lpProjName`と`lpAuxProjPath`します。 ソース管理プラグインは、この情報を求める後、は、IDE にこれら 2 つの文字列を渡します。 IDE のソリューション ファイルには、文字列が解決しないし、コマンドを渡し、 [SccOpenProject](../extensibility/sccopenproject-function.md)たびに、ユーザーがこのプロジェクトを開きます。 これらの文字列には、プロジェクトに関連付けられた情報を追跡するには、プラグインが有効にします。  
  
 関数が最初に呼び出されると、`lpAuxProjPath`が空の文字列に設定します。 `lProjName` 空である可能性のあるソース管理プラグインを使用して、無視、IDE プロジェクト名を含めることができますか。 関数が正常に返されるときに、プラグインを返します 2 つの対応する文字列。 IDE はによりこれらの文字列の前提条件、使用するには、およびそれらを変更するユーザーはできません。 ユーザー設定を変更する場合は、IDE が呼び出す`SccGetProjPath`、もう一度、前の時間を受信と同じ値で渡す必要があります。 これで、これら 2 つの文字列プラグイン、完全な制御ができます。  
  
 `lpUser`IDE を渡すことがユーザー名、またはポインターで空の文字列に渡すことがありますだけです。 ユーザー名がある場合、ソース管理プラグインとして使用してください、既定値。 ただし、名前が渡されなかった場合、または指定した名前、ログインに失敗した場合は、プラグイン、メッセージを表示するユーザー ログインと、名前をパス`lpUser`有効なログインを受信するとします。 プラグインがこの文字列を変更するため、IDE が常にサイズのバッファーを割り当てる (`SCC_USER_LEN`+1)。  
  
> [!NOTE]
>  いずれかへの呼び出しを IDE を実行する最初のアクションがあります、`SccOpenProject`関数または`SccGetProjPath`関数。 そのため、両方のある、同じ`lpUser`パラメーターで、ソース管理プラグインでユーザーのいずれかの時点でログインできるようにします。 関数からの戻り値には、エラーが示されている場合でもプラグイン入力してこの文字列には、有効なログイン名。  
  
 `lpLocalPath` ユーザーが、プロジェクトを保持するディレクトリです。 空の文字列がある可能性があります。 (ソース管理システムからプロジェクトをダウンロードしようとしていますユーザー) 場合には、現在定義されているディレクトリが存在しない場合、`bAllowChangePath`は`TRUE`、ソース管理プラグインがユーザー入力を要求または配置するその他の方法を使用して、。文字列を所有`lpLocalPath`します。 場合`bAllowChangePath`は`FALSE`、プラグインが変わらないようにする、文字列、ユーザーが指定されたディレクトリに既に作業しているためです。  
  
 ユーザーは、ソース管理下に新しいプロジェクトを作成する場合、ソース管理プラグイン可能性があります実際に作成されませんが、ソース管理システムで時に`SccGetProjPath`が呼び出されます。 と共に、0 以外の値の文字列を渡しますが代わりに、 `pbNew`、ソース管理システムで、プロジェクトが作成されることを示します。  
  
 たとえば、ユーザーの場合、**新しいプロジェクト**Visual Studio でウィザードでは、自分のプロジェクトをソース管理に追加、Visual Studio は、この関数を呼び出して、およびソース管理システムで新しいプロジェクトを作成できるかどうかは、プラグインを決定しますVisual Studio プロジェクトが含まれます。 ユーザーがクリックした場合**キャンセル**ウィザードが完了する前に、プロジェクトは作成されません。 ユーザーがクリックした場合 **[ok]**、Visual Studio は呼び出して`SccOpenProject`で渡し`SCC_OPT_CREATEIFNEW`、され、その時点でソース管理プロジェクトを作成します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
---
title: SccGetProjPath 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ef5041b483e85e0806827f7d1188d432b476c5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142342"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 関数
この関数には、ユーザーは、ソース管理プラグインにのみ意味のある文字列であるプロジェクト パスにメッセージが表示されます。 ユーザーがときに呼び出されます。  
  
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
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力].ユーザー名 (を超過しない SCC_USER_SIZE、NULL 終端文字を含む)  
  
 lpProjName  
 [入力、出力].IDE のプロジェクト、プロジェクト ワークスペースまたはメイクファイル (を超過しない SCC_PRJPATH_SIZE、NULL 終端文字を含む) の名前。  
  
 lpLocalPath  
 [入力、出力].プロジェクトの有効なパスです。 場合`bAllowChangePath`は`TRUE`、ソース管理プラグインは、この文字列 (を超過しない _MAX_PATH、null 終端文字を含む) を変更できます。  
  
 lpAuxProjPath  
 [入力、出力].返されるプロジェクトのパス (を超過しない SCC_PRJPATH_SIZE、NULL 終端文字を含む) のバッファーです。  
  
 bAllowChangePath  
 [in]これは、する場合`TRUE`、ソース管理プラグインの入力を求めるしたり変更したり、`lpLocalPath`文字列。  
  
 pbNew  
 [入力、出力].受け取った値では、新しいプロジェクトを作成するかどうかを示します。 返される値は、プロジェクトの作成の成功を表します。  
  
|受信|解釈|  
|--------------|--------------------|  
|true|ユーザーでは、新しいプロジェクトを作成します。|  
|false|ユーザーは、新しいプロジェクトを作成しない場合があります。|  
  
|発信|解釈|  
|--------------|--------------------|  
|true|新しいプロジェクトが作成されました。|  
|false|既存のプロジェクトが選択されました。|  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|プロジェクトを作成または取得に成功しました。|  
|SCC_I_OPERATIONCANCELED|操作が取り消されました。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。|  
|SCC_E_CONNECTIONFAILURE|ソース管理システムに接続しようとしています。 問題が発生しました。|  
|SCC_E_NONSPECIFICERROR|未指定のエラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 この関数の目的は、パラメーターを取得するための IDE`lpProjName`と`lpAuxProjPath`です。 ソース管理プラグインは、この情報はユーザーを要求、後に、IDE にこれら 2 つの文字列を渡します。 IDE がそのソリューション ファイルには、文字列が引き続き発生して、コマンドを渡し、 [SccOpenProject](../extensibility/sccopenproject-function.md)されるたびに、ユーザーがこのプロジェクトを開きます。 これらの文字列をプロジェクトに関連付けられている情報を追跡するプラグインを有効にします。  
  
 関数が最初に呼び出されたときに`lpAuxProjPath`が空の文字列に設定します。 `lProjName` 空であることがあり、ソース管理プラグインを使用して無視 IDE、プロジェクト名を含めることがありますか。 関数が正常に返されるときに、プラグインを返します 2 つの対応する文字列。 IDE は、これらの文字列に関する仮定は行われません、使用するには、変更をユーザーができません。 IDE が呼び出す場合は、ユーザーの設定を変更する場合、`SccGetProjPath`ここでも、同じ値で渡すことが受信前の時間。 これにより、これら 2 つの文字列プラグイン、完全な制御。  
  
 `lpUser`IDE を渡すことがユーザー名、またはポインターで空の文字列を渡すことがあります単にします。 ユーザー名がある場合、ソース管理プラグインとして使用してください、既定値です。 ただし、名前が渡されなかった場合、または指定した名前、ログインに失敗した場合は、プラグインする必要がありますユーザー入力を求める、ログイン名とパスの名前を再び`lpUser`有効なログインを受信するとします。 この文字列は、プラグインの場合に変更することがあります、ため、IDE が常にサイズのバッファーを割り当てる (`SCC_USER_LEN`+1)。  
  
> [!NOTE]
>  IDE を実行する最初のアクションのいずれかへの呼び出し可能性があります、`SccOpenProject`関数または`SccGetProjPath`関数。 そのため、これらの両方のある同じ`lpUser`パラメーターで、ソース管理プラグインのいずれかの時にユーザーをログインできるようにします。 関数の戻り値には、エラーが示されている場合でも、プラグイン入力この文字列には、有効なログイン名ください。  
  
 `lpLocalPath` ユーザーが、プロジェクトを保持するディレクトリです。 空の文字列がある可能性があります。 (とユーザーの場合は、ソース管理システムからプロジェクトをダウンロードしようとしています) に現在定義されているディレクトリが存在しない場合、`bAllowChangePath`は`TRUE`、ソース管理プラグインが入力するプロンプトが表示または配置するその他の方法を使用して、文字列を所有`lpLocalPath`です。 場合`bAllowChangePath`は`FALSE`、プラグインが変わらないようにする、文字列、ユーザーが指定されたディレクトリで機能しているためです。  
  
 ユーザーは、ソース管理下に新しいプロジェクトを作成する場合、ソース管理プラグイン可能性があります実際に作成していないソース管理システムの時点で`SccGetProjPath`と呼びます。 代わりに、その渡すに沿って文字列以外の値を`pbNew`、ソース管理システムで、プロジェクトが作成されることを示すです。  
  
 たとえば、ユーザーがの場合、**新しいプロジェクト**Visual Studio のウィザードで自分のプロジェクトをソース管理に追加する、Visual Studio は、この関数を呼び出してを使用するソース管理システムで新しいプロジェクトを作成できるかどうかは、プラグインを決定Visual Studio プロジェクトが含まれてください。 ユーザーがクリックした場合**キャンセル**ウィザードを完了する前に、プロジェクトは作成されません。 ユーザーがクリックした場合**OK**、Visual Studio によって呼び出さ`SccOpenProject`を渡して、 `SCC_OPT_CREATEIFNEW`、され、その時点で、ソース管理されているプロジェクトを作成します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
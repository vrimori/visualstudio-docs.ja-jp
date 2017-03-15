---
title: "SccGetProjPath 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 551fe26fe20da62d6892a8c7e807cf6c22600fc8
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 関数
この関数は、ソース管理プラグインにとってのみ意味がある文字列であるプロジェクトのパスはユーザーを要求します。 ユーザーがときに呼び出されます。  
  
-   新しいプロジェクトを作成します。  
  
-   既存のプロジェクトをバージョン管理に追加します。  
  
-   既存のバージョン管理のプロジェクトを検索しようとしています。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
 hwnd の分離  
 [in]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpUser  
 [入力、出力]ユーザー名 (not NULL 終端文字も含めて SCC_USER_SIZE を超える)  
  
 lpProjName  
 [入力、出力]IDE のプロジェクト、プロジェクトのワークスペースまたはメイクファイル (not NULL 終端文字も含めて SCC_PRJPATH_SIZE を超える) の名前。  
  
 lpLocalPath  
 [入力、出力]プロジェクトの有効なパスです。 場合`bAllowChangePath`は`TRUE`、ソース管理プラグインがこの文字列 (not null 終端文字を含む _MAX_PATH を超える) を変更できます。  
  
 lpAuxProjPath  
 [入力、出力]返されたプロジェクトのパス (not NULL 終端文字も含めて SCC_PRJPATH_SIZE を超える) のバッファー。  
  
 bAllowChangePath  
 [in]この場合`TRUE`、ソース管理プラグインのダイアログを表示したり変更したり、`lpLocalPath`文字列。  
  
 pbNew  
 [入力、出力]の値では、新しいプロジェクトを作成するかどうかを示します。 返される値は、プロジェクトの作成の成功を表します。  
  
|着信|解釈|  
|--------------|--------------------|  
|TRUE|ユーザーは、新しいプロジェクトを作成します。|  
|FALSE|ユーザーは、新しいプロジェクトを作成しない場合があります。|  
  
|発信|解釈|  
|--------------|--------------------|  
|TRUE|新しいプロジェクトが作成されました。|  
|FALSE|既存のプロジェクトが選択されました。|  
  
## <a name="return-value"></a>戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|プロジェクトを作成または取得に成功しました。|  
|SCC_I_OPERATIONCANCELED|操作は取り消されました。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。|  
|SCC_E_CONNECTIONFAILURE|ソース管理システムに接続しようとしています。 問題が発生しました。|  
|SCC_E_NONSPECIFICERROR|未指定のエラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 この関数の目的は、パラメーターを取得するための IDE`lpProjName`と`lpAuxProjPath`です。 ソース管理プラグインでは、この情報はユーザーを要求後、は、IDE に戻るこれら&2; つの文字列を渡します。 IDE は、ソリューション ファイルには、文字列が引き続き発生して、コマンドを渡し、 [SccOpenProject](../extensibility/sccopenproject-function.md)するたびに、ユーザーがこのプロジェクトを開きます。 これらの文字列には、プロジェクトに関連付けられている情報を追跡するには、プラグインが有効にします。  
  
 最初に、関数が呼び出されたときに`lpAuxProjPath`が空の文字列に設定します。 `lProjName`空でもあることがあり、ソース管理プラグインを使用して無視する IDE、プロジェクト名を含めることがありますか。 関数が正常に返されるときに、プラグインを返します&2; つの対応する文字列。 IDE でこれらの文字列に関する仮定は行われませんを使用するには、変更をユーザーができなくなります。 IDE が呼び出す場合は、ユーザーの設定を変更する場合、`SccGetProjPath`ここでも、同じ値で渡すことが前の起動時に受信します。 こうと、これら&2; つの文字列をプラグイン、完全に制御できます。  
  
 `lpUser`IDE がユーザー名を渡すことが、またはポインターに空の文字列に渡すことがありますだけです。 ユーザー名がある場合、ソース管理プラグイン使用してください、既定値として。 ただし、名が渡されなかった場合、または指定した名前、ログインに失敗した場合は、プラグインでメッセージを表示、ユーザー ログイン名とパスの名前がバックアップに`lpUser`有効なログインを受信するとします。 プラグインがこの文字列を変更するため、IDE が常にサイズのバッファーを割り当てる (`SCC_USER_LEN`+1)。  
  
> [!NOTE]
>  いずれかへの呼び出しを IDE を実行する最初のアクションがあります、`SccOpenProject`関数または`SccGetProjPath`関数です。 そのため、これらの両方のあるに同一`lpUser`パラメーターで、ソース管理時にユーザーをログインにプラグインを使用します。 関数からの戻り値には、エラーが示されている場合でも、プラグイン入力してこの文字列には、有効なログイン名ください。  
  
 `lpLocalPath`ユーザーが、プロジェクトがどのように保持する場所のディレクトリです。 空の文字列がある可能性があります。 (ソース管理システムからプロジェクトをダウンロードしようとしています。 ユーザー) 場合、現在定義されているディレクトリが存在しない場合、`bAllowChangePath`は`TRUE`、ソース管理プラグインがユーザーに入力を求めるまたはに独自の文字列を配置するその他の方法を使用して`lpLocalPath`します。 場合`bAllowChangePath`は`FALSE`、プラグインが変わらないようにする、文字列、ユーザーが指定されたディレクトリで機能しているためです。  
  
 ユーザーは、ソース管理下に新しいプロジェクトを作成する場合、ソース管理プラグイン可能性があります実際に作成していないソース管理システムの時点で`SccGetProjPath`が呼び出されます。 以外の値を持つに沿って文字列を渡しますが代わりに、 `pbNew`、ソース管理システムで、プロジェクトが作成されることを示します。  
  
 たとえば、ユーザーが、**新しいプロジェクト**Visual Studio のウィザードでは、自分のプロジェクトをソース管理に追加、Visual Studio はこの関数を呼び出して、およびプラグインかどうかを Visual Studio プロジェクトを格納するソース管理システムで新しいプロジェクトを作成します。 ユーザーがクリックすると**キャンセル**ウィザードを完了する前に、プロジェクトは作成されません。 ユーザーがクリックした場合**OK**、Visual Studio によって呼び出さ`SccOpenProject`を渡すことで`SCC_OPT_CREATEIFNEW`、され、その時点で、ソース管理プロジェクトを作成します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)

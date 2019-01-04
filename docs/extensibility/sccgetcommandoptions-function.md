---
title: SccGetCommandOptions 関数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4237b967e63e89890bba5bed157ff98e7898a115
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823501"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions 関数
この関数は、指定されたコマンドの詳細設定オプションのユーザーに求めます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 iCommand  
 [in]高度なオプションを要求する対象のコマンド (を参照してください[コマンド コード](../extensibility/command-code-enumerator.md)使用可能な値)。  
  
 ppvOptions  
 [in]オプションの構造 (することもできます`NULL`)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_I_ADV_SUPPORT|ソース管理プラグインでは、コマンドの高度なオプションをサポートしています。|  
|SCC_I_OPERATIONCANCELED|ユーザーは、ソース管理プラグインのキャンセル**オプション** ダイアログ ボックス。|  
|SCC_E_OPTNOTSUPPORTED|ソース管理プラグインは、この操作をサポートしません。|  
|SCC_E_ISCHECKEDOUT|現在チェック アウトされているファイルでこの操作を実行することはできません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 IDE では、この関数を呼び出すと初めて`ppvOptions` = `NULL`をソース管理プラグインが、指定したコマンドのオプションの高度な機能をサポートしているかを判断します。 場合は、プラグインはそのコマンドのサポートの機能、IDE この関数を呼び出すもう一度、ユーザーは、高度なオプションを要求したときに (通常として実装、 **詳細設定**  ダイアログ ボックスのボタン) とのNULL以外のポインターを提供`ppvOptions`を指す、`NULL`ポインター。 プラグインはプライベート構造内のユーザーによって指定された高度なオプションを格納してには、その構造体へのポインターを返します`ppvOptions`します。 この構造体は後続の呼び出しを含む、について知っておく必要があるその他のすべてのソース管理プラグイン API 関数に渡されます、`SccGetCommandOptions`関数。  
  
 例は、このような状況をわかりやすく可能性があります。  
  
 ユーザーが選択、**取得**コマンドと、IDE が表示されます、**取得** ダイアログ ボックス。 IDE の呼び出し、`SccGetCommandOptions`関数と`iCommand`に設定`SCC_COMMAND_GET`と`ppvOptions`設定`NULL`します。 これは、質問としてプラグインのソース コントロールによって解釈されますが、"このコマンドの任意の高度なオプションでしょうか。" プラグインを返す場合`SCC_I_ADV_SUPPORT`、IDE が表示されます、 **詳細設定**ボタンその**取得** ダイアログ ボックス。  
  
 初めてクリックすると、ユーザー、**詳細**ボタン、IDE をもう一度呼び出します、`SccGetCommandOptions`関数は、この時点ではない`NULL``ppvOptions`を指す、`NULL`ポインター。 プラグインの表示、独自**オプションを取得** ダイアログ ボックスについては、ユーザー要求情報、独自の構造に保存されます。 とでその構造体へのポインターを返します`ppvOptions`します。  
  
 ユーザーがクリックした場合 **[詳細設定]** もう一度、同じダイアログ ボックスで、IDE 呼び出し、`SccGetCommandOptions`関数を変更せずにもう一度`ppvOptions`構造がプラグインに渡されるように、します。 これにより、ユーザーが以前に設定する値に、ダイアログ ボックスを再初期化するには、プラグインできます。 プラグインを返す前に、構造を変更します。  
  
 最後に、ユーザーがクリックすると**OK** ide の**取得**ダイアログ ボックスで、IDE の呼び出し、 [SccGet](../extensibility/sccget-function.md)で返される構造体を渡すこと`ppvOptions`を格納している、高度なオプションです。  
  
> [!NOTE]
>  コマンドは、 `SCC_COMMAND_OPTIONS` IDE が表示されるときに使用する**オプション** ダイアログ ボックスをユーザー設定を行う場合、統合のしくみを制御します。 表示できる場合は、ソース管理プラグインは、独自の環境設定 ダイアログ ボックスを指定する必要がある、 **詳細設定** IDE の基本設定 ダイアログ ボックスでボタンをクリックします。 プラグインが責任を負うものを取得して、この情報を永続化IDE は、それを使用してまたは変更はありません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [コマンド コード](../extensibility/command-code-enumerator.md)
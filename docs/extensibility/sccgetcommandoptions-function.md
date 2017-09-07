---
title: "SccGetCommandOptions 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 14
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: df497de98463d728b5cd040415924a40fb6717b8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

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
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 iCommand  
 [in]高度なオプションを要求する対象のコマンド (を参照してください[コマンド コード](../extensibility/command-code-enumerator.md)使用可能な値)。  
  
 ppvOptions  
 [in]オプションの構造 (することもできます`NULL`)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_I_ADV_SUPPORT|ソース管理プラグインは、コマンドの詳細設定オプションをサポートします。|  
|SCC_I_OPERATIONCANCELED|ソース管理プラグインでは、ユーザーによって取り消されました**オプション** ダイアログ ボックス。|  
|SCC_E_OPTNOTSUPPORTED|ソース管理プラグインは、この操作をサポートしません。|  
|SCC_E_ISCHECKEDOUT|現在チェック アウトされているファイルでこの操作を実行できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 IDE で最初にこの関数が呼び出さ`ppvOptions` = `NULL`をソース管理プラグインが、指定されたコマンドのオプションの高度な機能をサポートしているかどうかを判断します。 ならば、プラグインが機能をサポート、そのコマンドの IDE によってこの関数もう一度、ユーザーは、高度なオプションを要求したときに (通常として実装、**詳細** ダイアログ ボックスのボタン)のNULL以外のポインターを提供し、`ppvOptions`を指す、`NULL`ポインター。 プライベート構造内のユーザーによって指定された高度なオプションを格納し、でその構造体へのポインターを返します、プラグイン`ppvOptions`です。 この構造体が後続の呼び出しなど、それについて認識する必要があるその他のすべてのソース管理プラグイン API 関数に渡され、`SccGetCommandOptions`関数。  
  
 例ではこのような状況を明確に役立ちます。  
  
 ユーザーが選択、**取得**コマンドと、IDE を表示、**取得** ダイアログ ボックス。 IDE の呼び出し、`SccGetCommandOptions`で機能`iCommand`に設定`SCC_COMMAND_GET`と`ppvOptions`'éý'`NULL`です。 これは、ソース管理プラグイン質問としてによって解釈されますが、"このコマンドの詳細設定オプションですか?" プラグインを返す場合`SCC_I_ADV_SUPPORT`、IDE を表示、 **詳細設定**ボタンをクリックして、**取得** ダイアログ ボックス。  
  
 初めてユーザーがクリックして、 **[詳細設定]**ボタン、IDE をもう一度呼び出す、`SccGetCommandOptions`関数は、この時点ではない`NULL``ppvOptions`を指す、`NULL`ポインター。 プラグインの表示、独自**オプションを取得** ダイアログ ボックスについては、ユーザー要求、独自の構造体には、その情報を格納およびでその構造体へのポインターを返します`ppvOptions`です。  
  
 ユーザーがクリックした場合**[詳細設定]**もう一度同じダイアログ ボックスでは、IDE によって呼び出さ、`SccGetCommandOptions`関数を変更せずにもう一度`ppvOptions`、構造体がプラグインに渡されるようにします。 これにより、ユーザーが以前に設定する値には、そのダイアログ ボックスを再初期化するようにプラグインできます。 プラグインを返す前に、配置内の構造を変更します。  
  
 最後に、ユーザーがクリックしたとき**OK**で IDE の**取得**ダイアログ ボックスで、IDE の呼び出し、 [SccGet](../extensibility/sccget-function.md)で返される構造体を渡すこと`ppvOptions`を格納している、高度なオプションです。  
  
> [!NOTE]
>  コマンドは、 `SCC_COMMAND_OPTIONS` IDE が表示されたときに使用、**オプション**統合の動作を制御 ダイアログ ボックス ユーザーを設定します。 表示できる、ソース管理プラグインは、独自の設定 ダイアログ ボックスを指定する必要がある場合、**詳細**IDE の基本設定 ダイアログ ボックスにボタンをクリックします。 取得し、この情報を保持する責任は、プラグインIDE や使用しないことを変更します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [コマンドのコード](../extensibility/command-code-enumerator.md)

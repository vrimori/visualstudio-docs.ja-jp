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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 86f8b896581d4238e1328bd0fe086987145c9fb5
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions 関数
この関数は、指定されたコマンドの詳細設定オプションのユーザーに求めます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
 hwnd の分離  
 [in]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 iCommand  
 [in]高度なオプションを要求する対象のコマンド (を参照してください[コマンド コード](../extensibility/command-code-enumerator.md)指定できる値について)。  
  
 ppvOptions  
 [in]オプションの構造 (することもできます`NULL`)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_I_ADV_SUPPORT|ソース管理プラグインでは、コマンドの詳細オプションをサポートしています。|  
|SCC_I_OPERATIONCANCELED|ユーザーは、ソース管理プラグインのキャンセル**オプション** ダイアログ ボックス。|  
|SCC_E_OPTNOTSUPPORTED|ソース管理プラグインでは、この操作はサポートしません。|  
|SCC_E_ISCHECKEDOUT|現在チェック アウトされているファイルでこの操作を実行できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 IDE で最初にこの関数が呼び出さ`ppvOptions` = `NULL`ソース管理プラグインが指定されたコマンドでのオプションの高度な機能をサポートしているかどうか。 ならばプラグイン機能をサポートして、そのコマンドの IDE によってこの関数もう一度、ユーザーは、高度なオプションを要求すると (通常として実装、**詳細** ダイアログ ボックスのボタン) の NULL 以外のポインターを提供し、`ppvOptions`を指す、`NULL`ポインター。 プラグインにプライベート構造体でユーザーが指定されている高度なオプションを格納し、その構造体へのポインターを返します`ppvOptions`します。 この構造体への後続の呼び出しなど、それについて認識する必要がある他のすべてのソース管理プラグインの API 関数に渡されます、`SccGetCommandOptions`関数です。  
  
 例を使用してこのような状況を明確にします。  
  
 ユーザーが選択、**取得**コマンドと、IDE を表示、**取得** ダイアログ ボックス。 IDE の呼び出し、`SccGetCommandOptions`関数を`iCommand`に設定`SCC_COMMAND_GET`と`ppvOptions`に設定`NULL`します。 これは、質問とプラグインのソース管理によって解釈されますが、"このコマンドの高度なオプションですか?" プラグインを返した場合`SCC_I_ADV_SUPPORT`、IDE が表示されます、 **[詳細設定**ボタンをクリックして、**取得**] ダイアログ ボックス。  
  
 はじめて、ユーザーがクリックすると、 **詳細設定**ボタン、IDE をもう一度呼び出す、`SccGetCommandOptions`機能しますが、この時点ではない`NULL``ppvOptions`を指す、`NULL`ポインター。 プラグインの表示、独自**取得オプション** ダイアログ ボックスについては、ユーザー要求独自の構造体には、その情報を格納し、その構造体へのポインターを返します`ppvOptions`します。  
  
 ユーザーがクリックした場合**[詳細設定**再び同じ] ダイアログ ボックスで、IDE を呼び出します、`SccGetCommandOptions`関数を変更せずにもう一度`ppvOptions`、構造体がプラグインに渡されるようにします。 これにより、以前に設定した値には、そのダイアログ ボックスを再初期化するには、プラグインできます。 プラグインを返す前に、配置内の構造を変更します。  
  
 最後に、ユーザーがクリックすると**OK** 、IDE で**取得**ダイアログ ボックスで、IDE の呼び出し、 [SccGet](../extensibility/sccget-function.md)で返される構造体を渡すこと`ppvOptions`高度なオプションを含みます。  
  
> [!NOTE]
>  コマンドは、 `SCC_COMMAND_OPTIONS` IDE が表示されたときに使用される、**オプション**ダイアログ ボックスを表示、ユーザーは、統合のしくみを制御する基本設定を設定します。 表示できる、ソース管理プラグインは、独自の基本設定 ダイアログ ボックスを指定する必要がある場合、**詳細**IDE の基本設定 ダイアログ ボックスでボタンをクリックします。 プラグインを取得し、この情報を永続化する責任を負うものIDE や使用しないことを変更します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [コマンドのコード](../extensibility/command-code-enumerator.md)

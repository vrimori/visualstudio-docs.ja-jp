---
title: SccSetOption 関数 |Microsoft Docs
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
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4a6c746ca1c824738c0c8cf7df23e78b0d94d7d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748794"
---
# <a name="sccsetoption-function"></a>SccSetOption 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ソース管理プラグインの動作を制御するオプションを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 nOption  
 [in]このオプションが設定されています。  
  
 dwVal  
 [in]オプションの設定。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|オプションが正常に設定します。|  
|SCC_I_SHARESUBPROJOK|場合に返される`nOption`が`SCC_OPT_SHARESUBPROJ`ソース管理プラグインにより、IDE をコピー先のフォルダーを設定するとします。|  
|SCC_E_OPNOTSUPPORTED|オプションが設定されていないに依存する必要があります。|  
  
## <a name="remarks"></a>Remarks  
 IDE では、ソース管理プラグインの動作を制御するには、この関数を呼び出します。 最初のパラメーターでは、 `nOption`、2 番目の中に、設定する値を指定`dwVal`、その値を使って対処方法を示します。 プラグインに関連付けられている情報を保存、`pvContext``,`呼び出した後、IDE がこの関数を呼び出す必要がありますので、 [SccInitialize](../extensibility/sccinitialize-function.md) (が各呼び出しの後に必ずしも、 [SccOpenProject](../extensibility/sccopenproject-function.md))。  
  
 オプションとその値の概要:  
  
|`nOption`|`dwValue`|説明|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|イベント キュー バック グラウンドの有効/無効にします。|  
|`SCC_OPT_USERDATA`|任意の値|渡されるユーザー値を指定します、 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)コールバック関数。|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE 現在がサポートするか、操作の取り消しを示します。|  
|`SCC_OPT_NAMECHANGEPFN`|ポインター、 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)コールバック関数|名前変更のコールバック関数へのポインターを設定します。|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE では、手動で (ソース管理のユーザー インターフェイス) 経由でそのファイルのチェック アウトまたはかどうかがチェック アウト ソース管理プラグインを介してのみかどうかを示します。|  
|`SCC_OPT_SHARESUBPROJ`|N/A|ソース管理プラグインは、ローカルのプロジェクト フォルダーを指定するための IDE を許可している場合、プラグインを返します`SCC_I_SHARESUBPROJOK`します。|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 場合`nOption`は`SCC_OPT_EVENTQUEUE`IDE が無効にすると (または再度有効にする) バック グラウンド処理します。 たとえば、コンパイル時に IDE は、任意の種類のアイドル処理を停止するプラグインのソース管理を教えることがあります。 コンパイルした後は、プラグのイベント キューを最新に保つためにバック グラウンド処理を再度有効になります。 対応する、 `SCC_OPT_EVENTQUEUE` @property`nOption`の 2 つの値がある`dwVal`、つまり、`SCC_OPT_EQ_ENABLE`と`SCC_OPT_EQ_DISABLE`します。  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 場合の値は、`nOption`は`SCC_OPT_HASCANCELMODE`IDE では、ユーザーを長時間操作をキャンセルします。 設定`dwVal`に`SCC_OPT_HCM_NO`(既定値) では、IDE にキャンセル モードがないことを示します。 ソース管理プラグインは、ユーザーを取り消すことがある必要がある場合、独自の [キャンセル] ボタンを提供する必要があります。 `SCC_OPT_HCM_YES` IDE がプラグイン、SCC は、独自の [キャンセル] ボタンを表示する必要はありませんので、操作をキャンセルする機能を提供することを示します。 IDE が設定されている場合`dwVal`に`SCC_OPT_HCM_YES`に対応する準備ができた`SCC_MSG_STATUS`と`DOCANCEL`に送信されたメッセージ、`lpTextOutProc`コールバック関数 (を参照してください[LPTEXTOUTPROC](../extensibility/lptextoutproc.md))。 IDE でこの変数が設定されていない場合、プラグインを送信できませんこれら 2 つのメッセージ。  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 NOption に設定されている場合`SCC_OPT_NAMECHANGEPFN`と、両方のソース管理プラグインと、IDE を許可することで、プラグイン実際に名前を変更したり、ソース管理操作中にファイルを移動します。 `dwVal`型の関数ポインターに設定されます[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)します。 ソース管理の操作中に、プラグインのこの関数を呼び出す、3 つのパラメーターを渡します。 これらは、IDE との関連性のある情報へのポインターや、そのファイルの新しい名前 (完全修飾パス) で、ファイルの古い名前 (完全修飾パス) にします。 IDE を呼び出すことによってこの最後のポインターで送信`SccSetOption`で`nOption`に設定`SCC_OPT_USERDATA`で`dwVal`のデータを指します。 この関数のサポートは、省略可能です。 VSSCI プラグ-を使用してこの機能する必要があります、関数ポインターとユーザー データ変数を初期化`NULL`が与えられた 1 つしない限り、名前の変更関数を呼び出すことが必要がありますいないとします。 渡された値を保持する、または新しい呼び出しに応答を変更するにも準備する`SccSetOption`します。 これは、ソース管理コマンドの操作の途中では行われませんが、コマンド間で可能性があります。  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 NOption に設定されている場合`SCC_OPT_SCCCHECKOUTONLY`IDE は、現在開いているプロジェクト内のファイルしないチェック アウトするか手動でソース管理システムのユーザー インターフェイスを使用を示すです。 代わりに、ファイルは、IDE の管理下にあるプラグインのソース管理からのみチェック_アウトする必要があります。 場合`dwValue`に設定されている`SCC_OPT_SCO_NO`ファイルがプラグインによって通常どおりに扱う必要があるあり、UI のソース管理からチェック アウトできるになります。 場合`dwValue`に設定されている`SCC_OPT_SCO_YES`しプラグインのみが許可されたファイルをチェック アウト、および、ソース管理システムの UI を起動しません。 これは、IDE が IDE を介してのみをチェック アウトすることに意味"擬似 files"を必要がありますに適しています。  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 場合`nOption`に設定されている`SCC_OPT_SHARESUBPROJ`IDE、ソース管理からファイルを追加すると、ソース管理プラグインは、指定したローカル フォルダーを使用できるかどうかをテストします。 値、`dwVal`パラメーターはここでは関係ありません。 プラグインでは、IDE ソースからファイルを追加、ローカルのコピー先フォルダーを指定する場合が制御、 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)と呼ばれる場合は、プラグインを返す必要がありますし、`SCC_I_SHARESUBPROJOK`ときに、`SccSetOption`関数と呼ばれる。 IDE を使用し、`lplpFileNames`のパラメーター、`SccAddFromScc`関数に渡す先のフォルダーにします。 プラグインは、ソース管理から追加されたファイルを配置するのに先のフォルダーを使用します。 場合は、プラグインは返されません`SCC_I_SHARESUBPROJOK`ときに、`SCC_OPT_SHARESUBPROJ`オプションが設定されている、IDE では、プラグインの項目が現在のローカル フォルダーにのみファイルを追加することを前提としています。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)


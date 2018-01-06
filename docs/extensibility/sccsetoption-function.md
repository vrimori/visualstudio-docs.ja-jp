---
title: "SccSetOption 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccSetOption
helpviewer_keywords: SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70fe624984adce58191ee7d354185eac0bb527ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccsetoption-function"></a>SccSetOption 関数
この関数は、ソース管理プラグインの動作を制御するオプションを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in]設定されているオプションです。  
  
 dwVal  
 [in]オプションの設定。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|オプションが正常に設定します。|  
|SCC_I_SHARESUBPROJOK|場合に返される`nOption`が`SCC_OPT_SHARESUBPROJ`ソース管理プラグインは、移行先のフォルダーを設定するための IDE とします。|  
|SCC_E_OPNOTSUPPORTED|オプションが設定されていないには依存しない必要があります。|  
  
## <a name="remarks"></a>コメント  
 IDE では、ソース管理プラグインの動作を制御するには、この関数を呼び出します。 最初のパラメーターでは、 `nOption`、2 番目の中に、設定した値を示します`dwVal`、その値を持つの対処方法を示します。 プラグインに関連付けられている情報の保存、 `pvContext``,` IDE はこの関数を呼び出した後に呼び出す必要がありますので、 [SccInitialize](../extensibility/sccinitialize-function.md) (への各呼び出しの後に必ずしもですが、 [SccOpenProject](../extensibility/sccopenproject-function.md))。  
  
 オプションとその値の概要:  
  
|`nOption`|`dwValue`|説明|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|有効/無効には、イベント キューをバック グラウンドします。|  
|`SCC_OPT_USERDATA`|任意の値|渡されるユーザー値を指定します、 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)コールバック関数。|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE 現在がサポートするか、操作の取り消しを示します。|  
|`SCC_OPT_NAMECHANGEPFN`|ポインター、 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)コールバック関数|名前変更のコールバック関数へのポインターを設定します。|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE では、そのファイルから手動で (ソース制御ユーザー インターフェイス) のチェック アウトまたはかどうかがチェック アウト ソース管理プラグインを介してのみかどうかを示します。|  
|`SCC_OPT_SHARESUBPROJ`|N/A|ソース管理プラグインは、ローカルのプロジェクト フォルダーを指定するための IDE を許可している場合、プラグインを返します`SCC_I_SHARESUBPROJOK`です。|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 場合`nOption`は`SCC_OPT_EVENTQUEUE`IDE が無効にすると (または再度有効にする) のバック グラウンド処理します。 インスタンス、コンパイル時に IDE がソース管理プラグインを任意の種類の アイドル処理を停止するを教えることがあります。 コンパイルした後は、プラグインのイベント キューを常に最新の状態に保つにバック グラウンド処理を再度有効になります。 対応する、`SCC_OPT_EVENTQUEUE`の値`nOption`、2 つの可能な値がある`dwVal`、つまり、`SCC_OPT_EQ_ENABLE`と`SCC_OPT_EQ_DISABLE`です。  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 場合の値は、`nOption`は`SCC_OPT_HASCANCELMODE`IDE では、ユーザーを長時間操作をキャンセルします。 設定`dwVal`に`SCC_OPT_HCM_NO`(既定) では、IDE に [キャンセル] モードが含まれていないことを示します。 ユーザーにキャンセルできる必要がある場合、ソース管理プラグインは独自の [キャンセル] ボタンを提供しなければなりません。 `SCC_OPT_HCM_YES`IDE に、SCC プラグインは独自の [キャンセル] ボタンを表示する必要はありませんので、操作をキャンセルする機能が提供されていることを示します。 場合は、IDE 設定`dwVal`に`SCC_OPT_HCM_YES`に応答する準備ができた`SCC_MSG_STATUS`と`DOCANCEL`に送信されたメッセージ、`lpTextOutProc`コールバック関数 (を参照してください[LPTEXTOUTPROC](../extensibility/lptextoutproc.md))。 IDE でこの変数が設定されていない場合、プラグインを送信できませんこれら 2 つのメッセージ。  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 NOption に設定されている場合`SCC_OPT_NAMECHANGEPFN`、および両方のソース管理プラグインと、IDE を使用することで、プラグイン実際に名前を変更したりソース管理操作中にファイルを移動します。 `dwVal`型の関数ポインターに設定されます[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)です。 ソース管理操作中にプラグインこの関数を呼び出す、3 つのパラメーターに渡します。 これらは、ファイル、そのファイルと、IDE との関連性のある情報へのポインターの (完全修飾パス) の新しい名前の (完全修飾パス) の古い名前です。 IDE を呼び出すことによってこの最後のポインターで送信`SccSetOption`で`nOption`'éý'`SCC_OPT_USERDATA`で`dwVal`のデータを指すです。 この関数のサポートはオプションです。 VSSCI プラグ-を使用してこの機能する必要があります、関数ポインターとユーザー データ変数を初期化`NULL`に与えられたいずれかの場合を除き、rename 関数を呼び出す必要がありますいないこととします。 これをも準備に指定された値を保持するかに新しい呼び出しに対する応答で変更`SccSetOption`です。 これは、ソース管理コマンドの操作の途中では行われませんが、コマンド間でその可能性があります。  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 NOption に設定されている場合`SCC_OPT_SCCCHECKOUTONLY`IDE では、こと現在開いているプロジェクト内のファイルしないでチェック アウトするか手動でソース管理システムのユーザー インターフェイスを通じてを示すです。 代わりに、ファイルは、IDE の管理下にあるプラグイン ソース管理を通してのみチェック_アウトする必要があります。 場合`dwValue`に設定されている`SCC_OPT_SCO_NO`、こと示し、ファイル、プラグインで通常扱う必要があります UI ソース管理からチェック アウトできます。 場合`dwValue`に設定されている`SCC_OPT_SCO_YES`し、プラグインのみが許可されたファイルをチェック アウト、およびソース管理システムの UI を起動する必要があります。 これは、状況、IDE が、IDE を介してのみをチェック アウトする意味をなします"疑似 files"を持つ可能性があります。  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 場合`nOption`に設定されている`SCC_OPT_SHARESUBPROJ`IDE はソース管理からファイルを追加すると、ソース管理プラグインは、指定したローカル フォルダーを使用できるかどうかをテストします。 値、`dwVal`パラメーターはここでは関係ありません。 プラグインでは、IDE でソースからのファイルの追加、ローカルのコピー先フォルダーを指定する場合は、タイミングを制御、 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)が呼び出されたが、プラグインを返す必要があります、`SCC_I_SHARESUBPROJOK`ときに、`SccSetOption`関数は、と呼ばれる。 IDE を使用し、`lplpFileNames`のパラメーター、`SccAddFromScc`関数を対象フォルダーに渡します。 プラグインは、ソース管理から追加されたファイルの配置先のフォルダーを使用します。 プラグインを返さない場合`SCC_I_SHARESUBPROJOK`ときに、`SCC_OPT_SHARESUBPROJ`オプションの設定と、IDE がプラグインの項目が現在のローカル フォルダーでのみファイルを追加できることを想定しています。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
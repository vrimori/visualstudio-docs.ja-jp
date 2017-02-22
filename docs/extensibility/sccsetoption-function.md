---
title: "SccSetOption 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccSetOption"
helpviewer_keywords: 
  - "SccSetOption 関数"
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccSetOption 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理プラグインの動作を制御するオプションを設定します。  
  
## 構文  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 nOption  
 \[in\]このオプションが設定されています。  
  
 dwVal  
 \[in\]オプションの設定です。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|オプションが正常に設定します。|  
|SCC\_I\_SHARESUBPROJOK|返された場合 `nOption` が `SCC_OPT_SHARESUBPROJ` 、ソース管理プラグインでは、IDE をコピー先のフォルダーを設定するとします。|  
|SCC\_E\_OPNOTSUPPORTED|オプションは設定されていませんでしたし、時に依存しないします。|  
  
## 解説  
 IDE では、ソース管理プラグインの動作を制御するには、この関数を呼び出します。 最初のパラメーター `nOption`, 、2 番目のしたときに、設定値を示す `dwVal`, 、その値を持つ処理方法を示します。 プラグインに関連付けられている情報の保存、 `pvContext``,` IDE が呼び出した後にこの関数を呼び出す必要がありますので、 [SccInitialize](../extensibility/sccinitialize-function.md) \(への各呼び出しの後に必ずしも、 [SccOpenProject](../extensibility/sccopenproject-function.md)\)。  
  
 オプションとその値の概要:  
  
|`nOption`|`dwValue`|説明|  
|---------------|---------------|--------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|背景イベント キューの有効\/無効にします。|  
|`SCC_OPT_USERDATA`|任意の値|渡されるユーザー値を示す、 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) コールバック関数。|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE 現在がサポートするか、操作の取り消しを示します。|  
|`SCC_OPT_NAMECHANGEPFN`|ポインター、 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) コールバック関数|名前の変更のコールバック関数へのポインターを設定します。|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE では、そのファイルから手動で \(ソース管理のユーザー インターフェイス\) のチェック アウトまたはかどうか、チェック アウト ソース管理プラグインを通じてのみかどうかを示します。|  
|`SCC_OPT_SHARESUBPROJ`|N\/A|ソース管理プラグインでは、ローカルのプロジェクト フォルダーを指定するための IDE を許可している場合、プラグインを返します `SCC_I_SHARESUBPROJOK`します。|  
  
## SCC\_OPT\_EVENTQUEUE  
 場合 `nOption` は `SCC_OPT_EVENTQUEUE`, 、IDE が無効にすると \(または再度有効にする\) バック グラウンドで処理します。 たとえば、コンパイル時に、IDE は、任意の種類の \[アイドル処理を停止するプラグインのソース管理を教えることがあります。 コンパイル後に、イベント キュー、プラグインの最新の状態を保持するバック グラウンド処理を再度有効には。 対応する、 `SCC_OPT_EVENTQUEUE` の値 `nOption`, 、2 つの可能な値がある `dwVal`, 、つまり、 `SCC_OPT_EQ_ENABLE` と `SCC_OPT_EQ_DISABLE`です。  
  
## SCC\_OPT\_HASCANCELMODE  
 場合に値 `nOption` は `SCC_OPT_HASCANCELMODE`, 、IDE では、ユーザーを長時間操作をキャンセルします。 設定 `dwVal` に `SCC_OPT_HCM_NO` \(既定値\) では、IDE にキャンセル モードが含まれていないことを示します。 ユーザーがキャンセルできる必要がある場合、ソース管理プラグインでは、それぞれの \[キャンセル\] ボタンを提供しなければなりません。`SCC_OPT_HCM_YES` IDE は、SCC プラグインは独自の \[キャンセル\] ボタンを表示する必要はありませんので、操作をキャンセルする機能を提供することを示します。 IDE を設定する場合 `dwVal` に `SCC_OPT_HCM_YES`, に対応する準備ができた `SCC_MSG_STATUS` と `DOCANCEL` に送信されたメッセージ、 `lpTextOutProc` コールバック関数 \(を参照してください [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)\)。 IDE でこの変数が設定されていない場合、プラグインを送信しないでこれら 2 つのメッセージ。  
  
## SCC\_OPT\_NAMECHANGEPFN  
 NOption に設定されている場合 `SCC_OPT_NAMECHANGEPFN`, 、および両方のソース管理プラグインと、IDE を使用することで、プラグイン実際に名前を変更したり、ソース管理操作中にファイルを移動します。`dwVal` 型の関数ポインターに設定されます [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)します。 ソース管理の操作中に、プラグイン関数を呼び出すこの、3 つのパラメーターを渡します。 これらは、IDE との関連性のある情報へのポインターや、そのファイルの新しい名前 \(完全修飾パス\) で、ファイルのパスを持つ完全修飾の古い名前です。 IDE を呼び出すことによってこの最後のポインターで送信 `SccSetOption` と `nOption` に設定 `SCC_OPT_USERDATA`, と `dwVal` のデータを指します。 この関数のサポートはオプションです。 VSSCI プラグ\-を使用してこの機能必要があります、関数ポインターとユーザー データ変数を初期化 `NULL`, に与えられたいずれかの場合を除き、名前の変更関数を呼び出して、必要がありますいません。 指定された値を保持するか、新しい呼び出しへの応答で変更するにも準備する `SccSetOption`です。 これは、ソース管理コマンドの操作の途中では行われませんが、コマンドの間があります。  
  
## SCC\_OPT\_SCCCHECKOUTONLY  
 NOption に設定されている場合は、 `SCC_OPT_SCCCHECKOUTONLY`, 、IDE は、現在開いているプロジェクト内のファイル決してチェック アウトするか手動でソース管理システムのユーザー インターフェイスを使用ことを示します。 代わりに、ファイルは、IDE の制御下にあるプラグインのソース管理からのみチェック\_アウトする必要があります。 場合 `dwValue` に設定されている `SCC_OPT_SCO_NO`, 、ことを示し、ファイル、プラグインで通常使用をソース管理 UI をチェック アウトすることができます。 場合 `dwValue` に設定されている `SCC_OPT_SCO_YES`, し、プラグインのみが許可されたファイルをチェック アウト、およびソース管理システムの UI を起動する必要があります。 これは、IDE によってのみをチェック アウトすることに意味「擬似ファイル」を IDE がある場合に適しています。  
  
## SCC\_OPT\_SHARESUBPROJ  
 場合`nOption` に設定されている `SCC_OPT_SHARESUBPROJ`, 、IDE は、ソース管理プラグインはソース管理からファイルを追加するときに指定したローカル フォルダーを使用できるかどうかをテストします。 値、 `dwVal` パラメーターはここでは関係ありません。 プラグインでは、IDE のソースからファイルを追加、ローカルの格納先フォルダーを指定する場合は、タイミングを制御、 [SccAddFromScc](../extensibility/sccaddfromscc-function.md) を呼び出すと、プラグインを返す必要があります `SCC_I_SHARESUBPROJOK` ときに、 `SccSetOption` 関数が呼び出されます。 IDE を使用し、 `lplpFileNames` のパラメーター、 `SccAddFromScc` コピー先のフォルダーを指定する関数。 プラグインは、ソース管理から追加されたファイルを配置するのに先のフォルダーを使用します。 プラグインを返さない場合 `SCC_I_SHARESUBPROJOK` ときに、 `SCC_OPT_SHARESUBPROJ` オプションの設定と、IDE は、プラグインの項目が現在のローカル フォルダーにのみファイルを追加できることを想定しています。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
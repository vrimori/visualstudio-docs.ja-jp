---
title: LPTEXTOUTPROC |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 235d98ba6a5ca665857b8a18db5ca823ecc0c7c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
ユーザーは、統合開発環境 (IDE) 内からソース管理操作を実行するとき、ソース管理プラグインすることも、操作に関連するエラーまたはステータス メッセージの伝達します。 プラグインを表示できます、独自のメッセージ ボックスこの目的のため。 ただし、複数のシームレスな統合をプラグインできますで文字列を渡す、IDE では、ステータス情報を表示するがネイティブの方法で表示されます。 このメカニズムは、`LPTEXTOUTPROC`関数ポインター。 IDE では、エラーと状態を表示する (詳細については、以下で説明) この関数を実装します。  
  
 IDE をソース管理プラグインこの関数への関数ポインターとして渡す、`lpTextOutProc`パラメーターを呼び出すときに、 [SccOpenProject](../extensibility/sccopenproject-function.md)です。 例についてへの呼び出しの途中で、SCC 操作中に、 [SccGet](../extensibility/sccget-function.md)多数のファイルを含む、プラグイン呼び出すことができます、`LPTEXTOUTPROC`関数を定期的に表示する文字列。 IDE では、ステータス バー、または必要に応じての個別のメッセージ ボックスに、出力ウィンドウにこれらの文字列を表示できます。 必要に応じて、IDE がで特定のメッセージを表示することができます、**キャンセル**ボタンをクリックします。 これにより、ユーザーは、操作をキャンセルして、プラグインにこの情報を渡せるように IDE になります。  
  
## <a name="signature"></a>署名  
 IDE には、関数には、シグネチャは次の出力します。  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 display_string  
 表示するテキスト文字列。 この文字列は、キャリッジ リターン、ライン フィードで終了しない必要があります。  
  
 mesg_type  
 メッセージの種類。 次の表は、このパラメーターのサポートされている値を一覧表示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|メッセージは、情報、警告、またはエラーと見なされます。|  
|`SCC_MSG_STATUS`|メッセージは状態が表示され、ステータス バーに表示されることができます。|  
|`SCC_MSG_DOCANCEL`|メッセージ文字列がありませんと共に送信されます。|  
|`SCC_MSG_STARTCANCEL`|表示の開始、**キャンセル**ボタンをクリックします。|  
|`SCC_MSG_STOPCANCEL`|表示を停止、**キャンセル**ボタンをクリックします。|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|バック グラウンド操作をキャンセルできるが IDE を要求する: IDE を返します`SCC_MSG_RTN_CANCEL`操作が取り消されました。 場合を返しますそれ以外の場合、`SCC_MSG_RTN_OK`です。 `display_string`パラメーターとしてキャスト、 [SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled)構造で、ソース管理プラグインで指定します。|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|バージョン コントロールから取得される前に、ファイルは、IDE に指示します。 `display_string`パラメーターとしてキャスト、 [SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile)構造で、ソース管理プラグインで指定します。|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|バージョン管理から取得された後、ファイルに関する IDE に指示します。 `display_string`パラメーターとしてキャスト、 [SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)構造で、ソース管理プラグインで指定します。|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|バック グラウンド操作の現在の状態の IDE に指示します。 `display_string`パラメーターとしてキャスト、 [SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)構造で、ソース管理プラグインで指定します。|  
  
## <a name="return-value"></a>戻り値  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|文字列が表示されるか、操作が正常に完了しました。|  
|SCC_MSG_RTN_CANCEL|ユーザーが操作をキャンセルしようとするとします。|  
  
## <a name="example"></a>例  
 たとえば、IDE の呼び出し、 [SccGet](../extensibility/sccget-function.md) 20 個のファイル名を持つ。 ソース管理プラグイン ファイルの取得の途中で操作を取り消すようにしたいです。 呼び出しの各ファイルを取得した後`lpTextOutProc`、ファイルごとにステータス情報を渡すと、送信、`SCC_MSG_DOCANCEL`メッセージの状態レポートに設定されていない場合。 かどうかはいつでもプラグイン、戻り値の値を受け取る`SCC_MSG_RTN_CANCEL`IDE から操作をキャンセル、get、すぐにこれ以上ファイルを取得できるようにします。  
  
## <a name="structures"></a>構造体  
  
###  <a name="LinkSccMsgDataIsCancelled"></a> SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 この構造体に送信される、`SCC_MSG_BACKGROUND_IS_CANCELLED`メッセージ。 取り消された、バック グラウンド操作の ID を通信するために使用されます。  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a> SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 この構造体に送信される、`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`メッセージ。 取得しようとするファイルの名前と、取得を行っているバック グラウンド操作の ID を通信するために使用されます。  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a> SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 この構造体に送信される、`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`メッセージ。 指定したファイルだけでなく、取得すると、バック グラウンド操作の ID を取得する操作の結果を通信するために使用されます。 戻り値を参照してください、 [SccGet](../extensibility/sccget-function.md)にどのような結果に与えることができます。  
  
###  <a name="LinkSccMsgDataOnMessage"></a> SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 この構造体に送信される、`SCC_MSG_BACKGROUND_ON_MESSAGE`メッセージ。 バック グラウンド操作の現在の状態を通信するために使用されます。 状態は、IDE に表示する文字列として表されますと`bIsError`メッセージの重大度を示します (`TRUE`にエラー メッセージです。`FALSE`警告または情報メッセージ)。 ステータスを送信するバック グラウンド操作の ID も示されます。  
  
## <a name="code-example"></a>コード例  
 呼び出す簡単な例を次に示します`LPTEXTOUTPROC`を送信する、`SCC_MSG_BACKGROUND_ON_MESSAGE`の呼び出しの構造をキャストする方法を示すメッセージ。  
  
```cpp  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDE によって実装されているコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)